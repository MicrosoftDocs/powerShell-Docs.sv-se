---
ms.date: 07/10/2019
keywords: jea, powershell, säkerhet
title: Registrera JEA-konfigurationer
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726624"
---
# <a name="registering-jea-configurations"></a>Registrera JEA-konfigurationer

När du har din [rollfunktioner](role-capabilities.md) och [session konfigurationsfilen](session-configurations.md) skapas, det sista steget är att registrera JEA-slutpunkt. Registrera JEA-slutpunkt med systemet gör slutpunkten som är tillgängliga för användning av användare och automation-motorer.

## <a name="single-machine-configuration"></a>Konfiguration av enkel dator

För små miljöer kan du distribuera JEA genom att registrera session configuration filen med den [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.

Innan du börjar måste du kontrollera att följande krav är uppfyllda:

- En eller flera roller har skapats och placeras i den **RoleCapabilities** mapp på en PowerShell-modulen.
- En konfigurationsfil för sessionen har skapats och testats.
- Den användare som registrerar JEA-konfigurationen har administratörsbehörighet på systemet.
- Du har valt ett namn för din JEA-slutpunkt.

Namnet på JEA-slutpunkt krävs när användarna ansluter till systemet med JEA. Den [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet visar en lista över slutpunkter på ett system. Slutpunkter som börjar med `microsoft` vanligtvis medföljer Windows. Den `microsoft.powershell` slutpunkten är standardslutpunkten användas vid anslutning till en PowerShell-fjärrslutpunkten.

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Kör följande kommando för att registrera slutpunkten.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Föregående kommando startar om WinRM-tjänsten i systemet. Detta avslutar alla PowerShell-fjärrkommunikation sessioner och alla pågående DSC-konfigurationer. Vi rekommenderar att du vidta produktion datorerna offline innan du kör kommandot för att undvika störningar verksamheten.

Efter registreringen är du redo att [använda JEA](using-jea.md). Du kan ta bort konfigurationsfilen sessionen när som helst. Konfigurationsfilen används inte efter registreringen av slutpunkten.

## <a name="multi-machine-configuration-with-dsc"></a>Konfiguration för flera datorer med DSC

När du distribuerar du JEA på flera datorer, den enklaste distributionsmodellen använder JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) resursen för att snabbt och enhetligt distribuera JEA på varje dator.

Om du vill distribuera JEA med DSC, kontrollerar du att följande förutsättningar uppfylls:

- En eller flera rollfunktioner har skapats och lagts till i en PowerShell-modul.
- PowerShell-modulen som innehåller rollerna som lagras på en (skrivskyddad)-filresursen som är tillgängliga med varje dator.
- Inställningar för sessionskonfigurationen har visats. Du behöver inte skapa en konfigurationsfil för sessionen när du använder JEA DSC-resurs.
- Du har autentiseringsuppgifter som tillåter administrativa åtgärder på varje dator eller åtkomst till DSC-hämtningsserver som används för att hantera datorerna.
- Du har hämtat den [JEA DSC-resurs](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).

Skapa en DSC-konfiguration för JEA-slutpunkt på en målserver för dator- eller pull. I den här konfigurationen, den **JustEnoughAdministration** DSC-resursen definierar konfigurationsfilen sessionen och **filen** resursen kopierar rollfunktioner från filresursen.

Följande egenskaper kan konfigureras med hjälp av DSC-resurs:

- Rolldefinitioner
- Virtuellt kontogrupper
- Grupp-hanterade tjänstkontonamn
- Avskriften directory
- Enheten
- Regler för villkorlig åtkomst
- Startskript för JEA-sessionen

Syntaxen för var och en av de här egenskaperna i en DSC-konfiguration är konsekvent med PowerShell-session konfigurationsfil.

Nedan visas en exempelkonfiguration DSC för en modul för underhåll av allmänna. Det förutsätts att en giltig PowerShell-modul som innehåller rollfunktioner finns på den `\\myfileshare\JEA` filresurs.

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

Sedan konfigurationen används på ett system genom att aktivera direkt i [lokal konfigurationshanterare](/powershell/dsc/managing-nodes/metaConfig) eller uppdatera den [pull-serverkonfiguration](/powershell/dsc/pull-server/pullServer).

DSC-resurs kan du ersätta standard **Microsoft.PowerShell** slutpunkt. När den ersätts, registrerar resursen automatiskt en säkerhetskopiering slutpunkt med namnet **Microsoft.PowerShell.Restricted**. Säkerhetskopiering slutpunkten har standard WinRM ACL som tillåter Fjärrhanteringsanvändare och lokala administratörer gruppmedlemmar att komma åt den.

## <a name="unregistering-jea-configurations"></a>Avregistrerar JEA-konfigurationer

Den [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet tar bort en JEA-slutpunkt. Avregistrera en JEA-slutpunkt förhindrar att nya användare skapa nya JEA-sessioner på systemet. Du kan också uppdatera en JEA-konfiguration genom att registrera en konfigurationsfil för uppdaterade session med samma slutpunktnamn.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Avregistrera en JEA gör endpoint att WinRM-tjänsten startas om. Detta avbryter yttersta hanteringsåtgärder pågår, inklusive andra PowerShell-sessioner, WMI-anrop och vissa hanteringsverktyg. Avregistrera endast PowerShell slutpunkter under planerat underhållsfönster.

## <a name="next-steps"></a>Nästa steg

[Testa JEA-slutpunkt](using-jea.md)
