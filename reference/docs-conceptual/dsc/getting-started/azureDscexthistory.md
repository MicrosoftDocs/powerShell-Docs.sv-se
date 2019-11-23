---
description: Learn about the version history for the Desired State Configuration (DSC) extension in Azure.
ms.date: 06/21/2018
keywords: dsc, powershell, azure, extension
title: Azure DSC Extension Version History
ms.openlocfilehash: 7a89037d62cb2c8580141d2b177fdded5db654eb
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417293"
---
# <a name="azure-desired-state-configuration-extension-version-history"></a>Azure Desired State Configuration extension version history

The Azure Desired State Configuration (DSC) VM Extension is updated as-needed to support enhancements and new capabilities delivered by Azure, Windows Server, and the Windows Management Framework (WMF) that includes Windows PowerShell.

This article will provide information about each version of the Azure DSC VM Extension, what environments it supports, and comments and remarks on new features or changes.

## <a name="latest-version"></a>Latest Version

### <a name="version-276"></a>Version 2.76

- **Release date:**
  - May 9, 2018 (Azure) | June 21, 2018 (Azure China, Azure Government)
- **OS support:**
  - Windows Server 2016
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
  - Windows Client 7/8.1/10
  - Nano Server
- **WMF support:**
  - WMF 5.1
  - WMF 5.0 RTM
  - WMF 4.0 Update
  - WMF 4.0
- **Environment:**
  - Azure
  - Azure China
  - Azure Government
- **Remarks:** This version uses DSC as included in Windows Server 2016; for other Windows OSes, it installs the [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installing WMF requires a reboot). For Nano Server, DSC role is installed on the VM.
- **Nya funktioner:**
  - Improvement in extension metadata for substatus and other minor bug fixes.

## <a name="supported-versions"></a>Supported Versions

> [!WARNING]
> Versions 2.4 through 2.13 use WMF 5.0 Public Preview whose signing certificates expired in August 2016.  For more information about this issue, see [blog post](https://blogs.msdn.microsoft.com/powershell/2016/05/24/azure-dsc-extension-versions-2-4-up-to-2-13-will-retire-in-august/).

### <a name="version-275"></a>Version 2.75

- **Release date:** March 5, 2018
- **OS support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF support:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Environment:** Azure
- **Remarks:** This version uses DSC as included in Windows Server 2016; for other Windows OSes, it installs the [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installing WMF requires a reboot). For Nano Server, DSC role is installed on the VM.
- **Nya funktioner:**
  - After GitHub's recent move to TLS 1.2, you can't onboard a VM to Azure Automation DSC using DIY Resource Manager templates available on Azure Marketplace or use DSC extension to get any config hosted on GitHub. You will see an error similar to the following while deploying the extension:

    ```json
    {
        "code": "DeploymentFailed",
        "message": "At least one resource deployment operation failed. Please list deployment operations for details. Please see https://aka.ms/arm-debug for usage details.",
        "details": [{
            "code": "Conflict",
            "message": "{
                \"status\": \"Failed\",
                \"error\": {
                    \"code\": \"ResourceDeploymentFailure\",
                    \"message\": \"The resource operation completed with terminal provisioning state 'Failed'.\",
                    \"details\": [ {
                        \"code\": \"VMExtensionProvisioningError\",
                        \"message\": \"VM has reported a failure when processing extension 'Microsoft.Powershell.DSC'.
                        Error message: \\\"The DSC Extension failed to execute: Error downloading
                        https://github.com/Azure/azure-quickstart-templates/raw/master/dsc-extension-azure-automation-pullserver/UpdateLCMforAAPull.zip
                        after 29 attempts: The request was aborted: Could not create SSL/TLS secure channel..\\nMore information about the failure can
                        be found in the logs located under 'C:\\\\WindowsAzure\\\\Logs\\\\Plugins\\\\Microsoft.Powershell.DSC\\\\2.74.0.0' on the VM.\\\".\"
                    } ]
                }
            }"
        }]
    }
    ```

  - In the new extension version, TLS 1.2 is now enforced. While deploying the extension if you already had the AutoUpgradeMinorVersion = true in the Resource Manager template, then the extension will get autoupgraded to 2.75. For manual updates, specify `TypeHandlerVersion = 2.75` in your Resource Manager template.

### <a name="version-270---272"></a>Version 2.70 - 2.72

- **Release date:** November 13, 2017
- **OS support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF support:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Environment:** Azure
- **Remarks:** This version uses DSC as included in Windows Server 2016; for other Windows OSes, it installs the [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installing WMF requires a reboot). For Nano Server, DSC role is installed on the VM.
- **Nya funktioner:**
  - Bug fixes & improvements that simplifies using DSC Azure Automation through the portal UI as well as Resource Manager template.  For more information, see [Default Configuration Script](/azure/virtual-machines/extensions/dsc-overview) in the DSC Extension documentation.

### <a name="version-226"></a>Version 2.26

- **Release date:** June 9, 2017
- **OS support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF support:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Environment:** Azure
- **Remarks:** This version uses DSC as included in Windows Server 2016; for other Windows OSes, it installs the [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installing WMF requires a reboot). For Nano Server, DSC role is installed on the VM.
- **Nya funktioner:**
  - Telemetry improvements.

### <a name="version-225"></a>Version 2.25

- **Release date:** June 2, 2017
- **OS support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF support:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Environment:** Azure
- **Remarks:** This version uses DSC as included in Windows Server 2016; for other Windows OSes, it installs the [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installing WMF requires a reboot). For Nano Server, DSC role is installed on the VM.
- **Nya funktioner:**
  - Several bug fixes and other minor improvements were added.

### <a name="version-224"></a>Version 2.24

- **Release date:** April 13, 2017
- **OS support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF support:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Environment:** Azure
- **Remarks:** This version uses DSC as included in Windows Server 2016; for other Windows OSes, it installs the [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installing WMF requires a reboot). For Nano Server, DSC role is installed on the VM.
- **Nya funktioner:**
  - Exposes VM UUID & DSC Agent ID as extension metadata. Other minor improvements were added.

### <a name="version-223"></a>Version 2.23

- **Release date:** March 15, 2017
- **OS support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF support:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Environment:** Azure
- **Remarks:** This version uses DSC as included in Windows Server 2016; for other Windows OSes, it installs the [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installing WMF requires a reboot). For Nano Server, DSC role is installed on the VM.
- **Nya funktioner:**
  - Lots of bug fixes and other improvements were added.

### <a name="version-222"></a>Version 2.22

- **Release date:** February 8, 2017
- **OS support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF support:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Environment:** Azure
- **Remarks:** This version uses DSC as included in Windows Server 2016; for other Windows OSes, it installs the [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installing WMF requires a reboot). For Nano Server, DSC role is installed on the VM.
- **Nya funktioner:**
  - The DSC Extension now has support for WMF 5.1.
  - Minor other improvements were added.

### <a name="version-221"></a>Version 2.21

- **Release date:** December 2, 2016
- **OS support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF support:** WMF 5.1 Preview, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Environment:** Azure
- **Remarks:** This version uses DSC as included in Windows Server 2016; for other Windows OSes, it installs the [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installing WMF requires a reboot). For Nano Server, DSC role is installed on the VM.
- **Nya funktioner:**
  - The DSC Extension is now available on Nano Server. This version primarily contains code changes for running the Extension on Nano Server.
  - Minor other improvements were added.

### <a name="version-220"></a>Version 2.20

- **Release date:** August 2, 2016
- **OS support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF support:** WMF 5.1 Preview, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Environment:** Azure
- **Remarks:** This version uses DSC as included in Windows Server 2016 Technical Preview; for other Windows OSes, it installs the [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installing WMF requires a reboot).
- **Nya funktioner:**
  - Support for WMF 5.1 Preview. When first published, this version was an optional upgrade and you had to specify Wmfversion = '5.1PP' in Resource Manager templates to install WMF 5.1 preview. Wmfversion = 'latest' still installs the [WMF 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/). For more information on WMF 5.1 preview, see [this blog](https://blogs.msdn.microsoft.com/powershell/2016/07/16/announcing-windows-management-framework-wmf-5-1-preview/).
  - Minor other fixes and improvements were added.

### <a name="version--219"></a>Version  2.19

- **Release date:** June 3, 2016
- **OS support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF support:** WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Environment:** Azure, Azure China, Azure Government
- **Remarks:** This version uses DSC as included in Windows Server 2016 Technical Preview; for other Windows OSes, it installs the [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installing WMF requires a reboot).
- **Nya funktioner:**
  - The DSC Extension is now onboarded to Azure China. This version primarily contains fixes for running the Extension on Azure China.

### <a name="version-218"></a>Version 2.18

- **Release date:** June 3, 2016
- **OS support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF support:** WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Environment:** Azure
- **Remarks:** This version uses DSC as included in Windows Server 2016 Technical Preview; for other Windows OSes, it installs the [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installing WMF requires a reboot).
- **Nya funktioner:**
  - Make telemetry non-blocking when an error occurs during telemetry hotfix download (known Azure DNS issue) or during install.
  - Fix for the intermittent issue where extension stops processing configuration after a reboot. This was causing the DSC Extension to remain in 'transitioning' state.
  - Minor other fixes and improvements were added.

### <a name="version-217"></a>Version 2.17

- **Release date:** April 26, 2016
- **OS support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF support:** WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Environment:** Azure
- **Remarks:** This version uses DSC as included in Windows Server 2016 Technical Preview; for other Windows OSes, it installs the [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installing WMF requires a reboot).
- **Nya funktioner:**
  - Support for WMF 4.0 Update. For more information on WMF 4.0 Update, see [this blog](https://blogs.msdn.microsoft.com/powershell/2016/01/19/windows-management-framework-wmf-4-0-update-now-available-for-windows-server-2012-windows-server-2008-r2-sp1-and-windows-7-sp1/).
  - Retry logic on errors that occur during the DSC Extension install or while applying a DSC configuration post extension install. As a part of this change, the extension will retry the installation if a previous install failed or re-enact a DSC configuration that had previously failed, for a maximum three times until it reaches the completion state (Success/Error) or if a new request comes. If the extension fails due to invalid user settings/user input, it does not retry. In this case, the extension needs to be invoked again with a new request and correct user settings. Note: The DSC Extension is dependent on the Azure VM agent for the retries. Azure VM agent invokes the extension with the last failed request until it reaches a success or error state.

### <a name="version-216"></a>Version 2.16

- **Release date:** April 21, 2016
- **OS support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF support:** WMF 5.0 RTM, WMF 4.0
- **Environment:** Azure
- **Remarks:** This version uses DSC as included in Windows Server 2016 Technical Preview; for other Windows OSes, it installs the [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installing WMF requires a reboot).
- **Nya funktioner:**
  - Improvement in error handling and other minor bug fixes.
  - New property in DSC Extension settings. 'ForcePullAndApply' in AdvancedOptions is added to enable the DSC Extension enact DSC configurations when the refresh mode is Pull (as opposed to the default Push mode). For more information, please refer to [this blog](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/) to get more information on the DSC Extension settings.

### <a name="version-215"></a>Version 2.15

- **Release date:** March 14, 2016
- **OS support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF support:** WMF 5.0 RTM, WMF 4.0
- **Environment:** Azure
- **Remarks:** This version uses DSC as included in Windows Server 2016 Technical Preview; for other Windows OSes, it installs the [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installing WMF requires a reboot).
- **Nya funktioner:**
  - In extension version 2.14, changes to install WMF RTM were included. While upgrading from extension version 2.13.2.0 to 2.14.0.0, you may notice that some DSC cmdlets fail or your configuration fails with an error – 'No Instance found with given property values'. For more information, see the [DSC release notes](/powershell/scripting/wmf/known-issues/known-issues-dsc). The workarounds for these issues have been added in 2.15 version.
  - Unfortunately, if you have already installed version 2.14 and are running into one of the above two issues, you will need to perform these steps manually.  In an elevated PowerShell session:
    - `Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof`
    - `mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof`

### <a name="version-214"></a>Version 2.14

- **Release date:** February 25, 2016
- **OS support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF support:** WMF 5.0 RTM, WMF 4.0
- **Environment:** Azure
- **Remarks:** This version uses DSC as included in Windows Server 2016 Technical Preview; for other Windows OSes, it installs the [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installing WMF requires a reboot).
- **Nya funktioner:**
  - Uses WMF RTM.
  - Enables data collection in order to improve the quality of the DSC Extension. For more information, see [the blog](https://blogs.msdn.microsoft.com/powershell/2016/02/02/azure-dsc-extension-data-collection-2/).
  - Provides an updated settings format for the extension in a Resource Manager template. For more information, see [the blog](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/).
  - Bug fixes and other enhancements.

## <a name="next-steps"></a>Nästa steg

- For more information about PowerShell DSC, go to the [PowerShell documentation center](../overview/overview.md).
- Examine the [Resource Manager template for the DSC extension](/azure/virtual-machines/extensions/dsc-template).
- For more functionality that you can manage by using PowerShell DSC, and for more DSC resources, browse the [PowerShell gallery](https://www.powershellgallery.com/packages?q=DscResource&x=0&y=0).
- For details about passing sensitive parameters into configurations, see [Manage credentials securely with the DSC extension handler](/azure/virtual-machines/extensions/dsc-credentials).
