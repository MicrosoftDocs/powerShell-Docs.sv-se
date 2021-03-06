---
ms.date: 08/15/2019
keywords: DSC, PowerShell, konfiguration, installation
title: Kom igång med önskad tillstånds konfiguration (DSC) för Windows
description: I det här avsnittet beskrivs hur du kommer igång med PowerShell (Desired State Configuration) för Windows.
ms.openlocfilehash: 2b9ddba2023a3933e3ad70d7bfee798ff07f0484
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662820"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a>Kom igång med önskad tillstånds konfiguration (DSC) för Windows

I det här avsnittet beskrivs hur du kommer igång med PowerShell (Desired State Configuration) för Windows. Allmän information om DSC finns i [Kom igång med önskad tillstånds konfiguration i Windows PowerShell](../overview/overview.md).

## <a name="supported-windows-operation-system-versions"></a>Operativ system versioner som stöds i Windows

Följande versioner stöds:

- Windows Server 2019
- Windows Server 2016
- Windows Server-2012R2
- Windows Server 2012
- Windows Server 2008 R2 SP1
- Windows 10
- Windows 8,1
- Windows 7

Den fristående produkt-SKU: n för [Microsoft Hyper-V server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) innehåller ingen implementering av önskad tillstånds konfiguration så att den inte kan hanteras av PowerShell DSC eller Azure Automation tillstånds konfiguration.

## <a name="installing-dsc"></a>Installerar DSC

PowerShell Desired State Configuration ingår i Windows och uppdateras via Windows Management Framework. Den senaste versionen är [Windows Management Framework 5,1](https://www.microsoft.com/download/details.aspx?id=54616).

> [!NOTE]
> Du behöver inte aktivera Windows Server-funktionen "DSC-service" för att kunna hantera en dator med DSC.
> Funktionen behövs bara när du skapar en Windows pull Server-instans.

## <a name="using-dsc-for-windows"></a>Använda DSC för Windows

I följande avsnitt beskrivs hur du skapar och kör DSC-konfigurationer på Windows-datorer.

### <a name="creating-a-configuration-mof-document"></a>Skapa ett MOF-dokument för konfiguration

Windows PowerShell- `Configuration` nyckelordet används för att skapa en konfiguration.
Följande steg beskriver hur du skapar ett konfigurations dokument med hjälp av Windows PowerShell.

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a>Definiera en konfiguration och generera konfigurations dokumentet:

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```

#### <a name="install-a-module-containing-dsc-resources"></a>Installera en modul som innehåller DSC-resurser

Windows PowerShell Desired State Configuration inkluderar inbyggda moduler som innehåller DSC-resurser.
Du kan också läsa in moduler från externa källor som PowerShell-galleriet med hjälp av PowerShellGet-cmdletar.

```PowerShell
Install-Module 'PSDscResources' -Verbose
```

#### <a name="apply-the-configuration-to-the-machine"></a>Tillämpa konfigurationen på datorn

> [!NOTE]
> För att DSC ska kunna köras måste Windows konfigureras för att ta emot PowerShell-fjärrkommandon även när du kör en `localhost` konfiguration. För att enkelt konfigurera din miljö på rätt sätt kan du bara köra `Set-WsManQuickConfig -Force` i en upphöjd PowerShell-Terminal.

Konfigurations dokument (MOF-filer) kan tillämpas på machineusing [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) -cmdlet.

```powershell
Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose
```

#### <a name="get-the-current-state-of-the-configuration"></a>Hämta konfigurationens aktuella tillstånd

Cmdlet [: en get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) frågar efter datorns aktuella status och returnerar de aktuella värdena för konfigurationen.

```powershell
Get-DscConfiguration
```

Cmdlet: en [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) returnerar den aktuella meta-konfigurationen som tillämpas på datorn.

```powershell
Get-DscLocalConfigurationManager
```

#### <a name="remove-the-current-configuration-from-a-machine"></a>Ta bort den aktuella konfigurationen från en dator

[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)

```powershell
Remove-DscConfigurationDocument -Stage Current -Verbose
```

#### <a name="configure-settings-in-local-configuration-manager"></a>Konfigurera inställningar i lokala Configuration Manager

Använd en MOF-fil för meta-konfiguration på datorn med cmdleten [set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) . Kräver sökvägen till MOF för meta-konfiguration.

```powershell
Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose
```

## <a name="windows-powershell-desired-state-configuration-log-files"></a>Loggfiler för önskad tillstånds konfiguration i Windows PowerShell

Loggar för DSC skrivs till händelse loggen i Windows i sökvägen `Microsoft-Windows-Dsc/Operational` .
Ytterligare loggar för fel sökning kan aktive ras enligt stegen i [var DSC-händelseloggar](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).
