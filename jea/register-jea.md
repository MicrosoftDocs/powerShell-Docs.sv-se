---
ms.date: 06/12/2017
keywords: jea, powershell, säkerhet
title: Registrera JEA-konfigurationer
ms.openlocfilehash: 6fa0ce434c8e70eb718545e99417bfe034cda6bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084835"
---
# <a name="registering-jea-configurations"></a>Registrera JEA-konfigurationer

> Gäller för: Windows PowerShell 5.0

När du har din [rollfunktioner](role-capabilities.md) och [session konfigurationsfilen](session-configurations.md) skapas, det sista steget innan du kan använda JEA är att registrera JEA-slutpunkt.
Registrera JEA-slutpunkt med systemet gör slutpunkten som är tillgängliga för användning av användare och automation-motorer.

## <a name="single-machine-configuration"></a>Konfiguration av enkel dator

För små miljöer kan du distribuera JEA genom att registrera session configuration filen med den [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.

Innan du börjar måste du kontrollera att följande krav är uppfyllda:
- En eller flera roller har skapats och placeras i mappen ”RoleCapabilities” av en giltig PowerShell-modulen.
- En konfigurationsfil för sessionen har skapats och testats.
- Den användare som registrerar JEA-konfigurationen har administratörsbehörighet på systemen.

Du måste också välja ett namn för din JEA-slutpunkt.
Namnet på JEA-slutpunkt krävs när du vill ansluta till systemet med JEA.
Du kan använda den [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet för att kontrollera namnen på befintliga slutpunkter i systemet.
Slutpunkter som börjar med 'microsoft' vanligtvis medföljer Windows.
'Microsoft.powershell'-slutpunkten är standardslutpunkten användas vid anslutning till en PowerShell-fjärrslutpunkten.

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

När du har bestämt ett lämpligt namn för din JEA-slutpunkt, kör du följande kommando för att registrera slutpunkten.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Ovanstående kommando startar om WinRM-tjänsten i systemet.
> Detta avslutar alla PowerShell-fjärrkommunikation sessioner, samt eventuella pågående DSC-konfigurationer.
> Vi rekommenderar att du ägnar några produktion datorer offline innan du kör kommandot för att undvika störningar verksamheten.

Om registreringen lyckas du är redo att [använda JEA](using-jea.md).
Du kan ta bort konfigurationsfilen som sessionen när som helst; den används inte när registrering av slutpunkten.

## <a name="multi-machine-configuration-with-dsc"></a>Konfiguration för flera datorer med DSC

Om du distribuerar JEA på flera datorer, den enklaste modellen är att använda JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resursen för att snabbt och enhetligt distribuera JEA på varje dator.

Om du vill distribuera JEA med DSC, måste du se till att följande krav är uppfyllda:
- En eller flera rollfunktioner har skapats och lagts till i en giltig PowerShell-modul.
- PowerShell-modulen som innehåller rollerna som lagras på en (skrivskyddad)-filresursen som är tillgängliga med varje dator.
- Inställningar för sessionskonfigurationen har visats. Du behöver inte skapa en konfigurationsfil för sessionen när du använder JEA DSC-resurs.
- Du har autentiseringsuppgifter så att du kan utföra administrativa åtgärder på varje dator eller har åtkomst till en DSC-hämtningsserver som används för att hantera datorerna.
- Du har hämtat den [JEA DSC-resurs](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

Skapa en DSC-konfiguration för JEA-slutpunkt på ett mål dator (eller pull-servern, om du använder en).
I den här konfigurationen använder du JustEnoughAdministration DSC-resurs du ställer in konfigurationsfilen sessionen och File-resursen ska kopieras över rollfunktioner från filresursen.

Följande egenskaper kan konfigureras med hjälp av DSC-resurs:
- Rolldefinitioner
- Virtuella kontogrupper
- Gruppnamn för Hanterat tjänstkonto
- Avskriften directory
- Enheten
- Regler för villkorlig åtkomst
- Startskript för JEA-sessionen

Syntaxen för var och en av de här egenskaperna i en DSC-konfiguration är konsekvent med PowerShell-session konfigurationsfil.

Nedan visas en exempelkonfiguration DSC för en modul för underhåll av allmänna.

Det förutsätts att en giltig PowerShell-modul som innehåller rollfunktioner i en undermapp som ”RoleCapabilities” finns på den '\\\\myfileshare\\JEA-filresurs.


```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

Den här konfigurationen kan sedan tillämpas på ett system av [direkt anropar den lokala Konfigurationshanteraren](https://msdn.microsoft.com/powershell/dsc/metaconfig) eller uppdatera den [pull-serverkonfiguration](https://msdn.microsoft.com/powershell/dsc/pullserver).

DSC-resurs kan du ersätta standardslutpunkten Microsoft.PowerShell fjärrkommunikation.
Om du gör det, registrerar resursen automatiskt en säkerhetskopiering obegränsad slutpunkt med namnet ”Microsoft.PowerShell.Restricted” som har standard WinRM ACL (som tillåter Fjärrhanteringsanvändare och lokala administratörer gruppmedlemmar att komma åt den).

## <a name="unregistering-jea-configurations"></a>Avregistrerar JEA-konfigurationer

Ta bort en JEA-slutpunkt på ett system med den [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.
Avregistrera en JEA-slutpunkt förhindrar att nya användare skapa nya JEA-sessioner på systemet.
Du kan också uppdatera en JEA-konfiguration genom att registrera en konfigurationsfil för uppdaterade session med samma slutpunktnamn.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Avregistrera en JEA gör endpoint att WinRM-tjänsten startas om.
> Detta avbryter yttersta hanteringsåtgärder pågår, inklusive andra PowerShell-sessioner, WMI-anrop och vissa hanteringsverktyg.
> Avregistrera endast PowerShell slutpunkter under planerat underhållsfönster.

## <a name="next-steps"></a>Nästa steg

- [Testa JEA-slutpunkt](using-jea.md)
