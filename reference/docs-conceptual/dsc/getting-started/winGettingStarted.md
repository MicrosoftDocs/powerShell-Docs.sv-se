---
ms.date: 08/15/2019
keywords: dsc,powershell,configuration,setup
title: Get started with Desired State Configuration (DSC) for Windows
ms.openlocfilehash: a9346b96693acdbad9bacbd4b6ca85971e17a3d1
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417761"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a>Get started with Desired State Configuration (DSC) for Windows

This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.
For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).

## <a name="supported-windows-operation-system-versions"></a>Supported Windows operation system versions

The following versions are supported:

- Windows Server 2019
- Windows Server 2016
- Windows Server 2012R2
- Windows Server 2012
- Windows Server 2008 R2 SP1
- Windows 10
- Windows 8.1
- Windows 7

The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku does not contain an implementation of Desired State Configuraion so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.

## <a name="installing-dsc"></a>Installing DSC

PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.
The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).

> [!NOTE]
> You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.
> That feature is only needed when building a Windows Pull Server instance.

## <a name="using-dsc-for-windows"></a>Using DSC for Windows

The following sections explain how to create and run DSC configurations on Windows computers.

### <a name="creating-a-configuration-mof-document"></a>Creating a configuration MOF document

The Windows PowerShell Configuration keyword is used to create a configuration.
The following steps describe the creation of a configuration document using Windows PowerShell.

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a>Define a configuration and generate the configuration document:

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
#### <a name="install-a-module-containing-dsc-resources"></a>Install a module containing DSC resources

Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.
You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a>Apply the configuration to the machine

Configuration documents (MOF files) can be applied to the machine using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a>Get the current state of the configuration

The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.

`Get-DscConfiguration`

The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a>Remove the current configuration from a machine

The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a>Configure settings in Local Configuration Manager

Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.
Requires the path to the Meta Configuration MOF.

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a>Windows PowerShell Desired State Configuration log files

Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.
Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).
