---
ms.date: 07/10/2019
keywords: Jea, PowerShell, säkerhet
title: Registrerar JEA-konfigurationer
description: När du registrerar JEA-slutpunkten med systemet blir slut punkten tillgänglig för användning av användare och automatiserings motorer.
ms.openlocfilehash: 6e7f8cdc1e7a666bddaa42034d70fcbcf55c1972
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92499917"
---
# <a name="registering-jea-configurations"></a>Registrerar JEA-konfigurationer

När du har skapat dina [roll funktioner](role-capabilities.md) och [konfigurations filen för sessionen](session-configurations.md) är det sista steget att registrera Jea-slutpunkten. När du registrerar JEA-slutpunkten med systemet blir slut punkten tillgänglig för användning av användare och automatiserings motorer.

## <a name="single-machine-configuration"></a>Konfiguration för enskild dator

För små miljöer kan du distribuera JEA genom att registrera sessionens konfigurations fil med hjälp av cmdleten [register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) .

Innan du börjar bör du kontrol lera att följande krav är uppfyllda:

- En eller flera roller har skapats och placerats i mappen **RoleCapabilities** i en PowerShell-modul.
- En konfigurations fil för sessionen har skapats och testats.
- Användaren som registrerar JEA-konfigurationen har administratörs behörighet på systemet.
- Du har valt ett namn för din JEA-slutpunkt.

Namnet på JEA-slutpunkten krävs när användare ansluter till systemet med hjälp av JEA. Cmdlet: en [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) visar namnen på slut punkterna i ett system. Slut punkter som börjar med `microsoft` levereras vanligt vis med Windows. `microsoft.powershell`Slut punkten är standard slut punkten som används vid anslutning till en fjärran sluten PowerShell-slutpunkt.

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

Kör följande kommando för att registrera slut punkten.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Föregående kommando startar om WinRM-tjänsten på systemet. Detta avslutar alla PowerShell-fjärrsessioner och pågående DSC-konfigurationer. Vi rekommenderar att du tar produktions datorer offline innan du kör kommandot för att undvika avbrott i affärs åtgärder.

Efter registreringen är du redo att [använda Jea](using-jea.md). Du kan när som helst ta bort sessionens konfigurations fil. Konfigurations filen används inte efter att slut punkten har registrerats.

## <a name="multi-machine-configuration-with-dsc"></a>Konfiguration av flera datorer med DSC

När du distribuerar JEA på flera datorer använder den enklaste distributions modellen JEA [-resursen (Desired State Configuration)](../../../dsc/overview/overview.md) för att snabbt och konsekvent distribuera Jea på varje dator.

För att distribuera JEA med DSC kontrollerar du att följande krav är uppfyllda:

- En eller flera roll funktioner har skapats och lagts till i en PowerShell-modul.
- PowerShell-modulen som innehåller rollerna lagras på en (skrivskyddad) fil resurs som är tillgänglig för varje dator.
- Inställningarna för konfigurationen av sessionen har fastställts. Du behöver inte skapa en konfigurations fil för sessionen när du använder JEA DSC-resursen.
- Du har autentiseringsuppgifter som tillåter administrativa åtgärder på varje dator eller åtkomst till DSC-pull-servern som används för att hantera datorerna.
- Du har laddat ned [Jea DSC-resursen](https://github.com/powershell/JEA/tree/master/DSC%20Resource).

Skapa en DSC-konfiguration för din JEA-slutpunkt på en måldator eller hämtnings Server. I den här konfigurationen definierar **JustEnoughAdministration** DSC-resursen sessionens konfigurations fil och **fil** resursen kopierar roll funktionerna från fil resursen.

Följande egenskaper kan konfigureras med hjälp av DSC-resursen:

- Rolldefinitioner
- Virtuella konto grupper
- Grupphanterat tjänst konto namn
- Avskrifts katalog
- Användar enhet
- Regler för villkorlig åtkomst
- Start skript för JEA-sessionen

Syntaxen för var och en av dessa egenskaper i en DSC-konfiguration är konsekvent med konfigurations filen för PowerShell-sessionen.

Nedan visas en exempel-DSC-konfiguration för en generell server underhålls modul. Det förutsätter att en giltig PowerShell-modul som innehåller roll funktioner finns på `\\myfileshare\JEA` fil resursen.

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

Därefter tillämpas konfigurationen på ett system genom att direkt anropa den [lokala Configuration Manager](/powershell/scripting/dsc/managing-nodes/metaConfig) eller uppdatera konfigurationen för pull- [servern](/powershell/scripting/dsc/pull-server/pullServer).

DSC-resursen låter dig också ersätta standard slut punkten för **Microsoft. PowerShell** . När den ersätts registrerar resursen automatiskt en säkerhets kopierings slut punkt med namnet **Microsoft. PowerShell. restricted**. Slut punkten för säkerhets kopieringen har standard-WinRM ACL som tillåter att fjärrhanterings användare och lokala administratörer kan komma åt den.

## <a name="unregistering-jea-configurations"></a>JEA-konfigurationer avregistreras

[Unregister-PSSessionConfiguration-](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet: en tar bort en Jea-slutpunkt. När du avregistrerar en JEA-slutpunkt hindras nya användare från att skapa nya JEA-sessioner i systemet. Du kan också uppdatera en JEA-konfiguration genom att registrera en uppdaterad sessions konfigurations fil på nytt med samma slut punkts namn.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> När du avregistrerar en JEA-slutpunkt startar WinRM-tjänsten om. Detta avbryter de flesta pågående hanterings åtgärder, inklusive andra PowerShell-sessioner, WMI-anrop och vissa hanterings verktyg. Avregistrera bara PowerShell-slutpunkter under planerat underhålls fönster.

## <a name="next-steps"></a>Nästa steg

[Testa JEA-slutpunkten](using-jea.md)
