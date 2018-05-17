---
ms.date: 06/12/2017
keywords: jea powershell säkerhet
title: Registrera JEA konfigurationer
ms.openlocfilehash: cda899b20378b0183a3d88ecfd593aaf7356e967
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="registering-jea-configurations"></a>Registrera JEA konfigurationer

> Gäller för: Windows PowerShell 5.0

Det sista steget innan du kan använda JEA när du har din [roll funktioner](role-capabilities.md) och [session konfigurationsfilen](session-configurations.md) skapades är att registrera slutpunkten JEA.
Den här processen gäller sessionsinformation konfigurationen systemet och tillgängliggör slutpunkten för användning av användare och automation motorer.

## <a name="single-machine-configuration"></a>Konfiguration av enskild dator

För små miljöer kan du distribuera JEA genom att registrera session configuration filen med den [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.

Innan du börjar bör du kontrollera att följande krav är uppfyllda:
- En eller flera roller har skapats och placeras i mappen 'RoleCapabilities' av en giltig PowerShell-modulen.
- En konfigurationsfil för sessionen har skapats och testas.
- Användare som registrerar JEA konfigurationen har administratörsbehörighet på det eller.

Du måste också markera ett namn för din JEA slutpunkt.
Namnet på slutpunkten JEA måste utföras när du vill ansluta till systemet med JEA.
Du kan använda den [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) för att kontrollera namnen på befintliga slutpunkter i systemet.
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

När du har bestämt ett lämpligt namn för slutpunkten JEA, kör du följande kommando för att registrera slutpunkten.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Ovanstående kommando startar om WinRM-tjänsten i systemet.
> Detta avslutas alla sessioner med PowerShell-fjärrkommunikation samt alla pågående DSC-konfigurationer.
> Vi rekommenderar att du ägnar några maskiner offline innan du kör kommandot för att undvika störningar verksamheten.

Om registreringen har lyckats, är du redo att [använder JEA](using-jea.md).
Du kan ta bort sessionen konfigurationsfilen när som helst; den används inte efter registreringen.

## <a name="multi-machine-configuration-with-dsc"></a>Flera datorer med DSC-konfiguration

Om du distribuerar JEA på flera datorer, den enklaste distributionsmodellen är att använda JEA [Desired State Configuration](https://msdn.microsoft.com/en-us/powershell/dsc/overview) resurs för att snabbt och konsekvent distribuera JEA på varje dator.

Om du vill distribuera JEA med DSC, måste du se till att följande krav är uppfyllda:
- En eller flera funktioner för rollen har skapats och lägga till en giltig PowerShell-modul.
- PowerShell-modulen som innehåller rollerna som lagras på en (skrivskyddad) filresurs tillgänglig av varje dator.
- Inställningar för sessionskonfigurationen har visats. Du behöver inte skapa en konfigurationsfil för session när du använder JEA DSC-resursen.
- Du har autentiseringsuppgifter som ska tillåta dig att utföra administrativa åtgärder på varje dator eller har åtkomst till en DSC pull-server som används för att hantera datorerna.
- Du har hämtat den [JEA DSC-resurs](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

Skapa en DSC-konfigurationen för slutpunkten JEA på en mål-dator (eller pull-servern, om du använder en).
I den här konfigurationen använder du JustEnoughAdministration DSC-resursen att ställa in konfigurationsfilen sessionen och filresurs för att kopiera över rollen funktioner från filresursen.

Följande egenskaper kan konfigureras med hjälp av DSC-resurs:
- Rolldefinitioner
- Virtuella kontogrupper
- Gruppnamn för Hanterat tjänstkonto
- Betyg directory
- Enheten
- Regler för villkorlig åtkomst
- Startskript för JEA-sessionen

Syntaxen för var och en av de här egenskaperna i ett DSC-konfigurationen är konsekvent med PowerShell-session konfigurationsfilen.

Nedan visas exempel DSC-konfigurationen för en allmän server Underhåll modul.

Det förutsätts att en giltig PowerShell-modul som innehåller funktioner för rollen i en undermapp 'RoleCapabilities' finns på den '\\\\myfileshare\\JEA' filresurs.


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

Den här konfigurationen kan sedan användas på ett system med [direkt anropar den lokala Configuration Manager](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) eller uppdatera den [pull-serverkonfigurationen](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).

DSC-resursen kan du ersätta standardslutpunkten Microsoft.PowerShell fjärrkommunikation.
Om du gör detta registrera resursen automatiskt en säkerhetskopiering unconstrainted slutpunkt med namnet ”Microsoft.PowerShell.Restricted” som har standard WinRM ACL (vilket innebär att Fjärrhanteringsanvändare och lokala administratörer gruppmedlemmar att komma åt den).

## <a name="unregistering-jea-configurations"></a>Avregistrerar JEA konfigurationer

Ta bort en JEA slutpunkt på ett system med den [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.
Avregistrerar en slutpunkt för JEA förhindrar att nya användare skapar nya JEA sessioner i systemet.
Du kan också uppdatera en JEA konfiguration genom att registrera en uppdaterad session konfigurationsfil med samma slutpunktnamn.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Avregistrerar en JEA kommer endpoint WinRM-tjänsten startas om.
> Detta kommer att avbryta yttersta hanteringsåtgärder pågår, inklusive andra PowerShell-sessioner, WMI-anrop och vissa hanteringsverktyg.
> Bara avregistrera PowerShell slutpunkter under planerat underhåll.

## <a name="next-steps"></a>Nästa steg

- [Testa JEA slutpunkten](using-jea.md)