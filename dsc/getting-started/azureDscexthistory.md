---
description: Läs mer om versionshistoriken för tillägget Desired State Configuration (DSC) i Azure.
ms.date: 06/21/2018
keywords: dsc, powershell, azure, extension
title: Versionshistorik för Azure DSC-tillägg
ms.openlocfilehash: 2c076e3beccc15e99af2327820916d7a4d28da68
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079752"
---
# <a name="azure-desired-state-configuration-extension-version-history"></a>Versionshistorik för Azure Desired State Configuration-tillägg

VM-tillägget Azure Desired State Configuration (DSC) uppdateras efter behov för förbättringar och nya funktioner som levereras av Azure, Windows Server och i Windows Management Framework (WMF) som innehåller Windows PowerShell.

Den här artikeln innehåller information om varje version av VM-tillägget Azure DSC vilka miljöer som har stöd för, och kommentarer och anmärkning med nya funktioner och ändringar.

## <a name="latest-version"></a>Senaste versionen

### <a name="version-276"></a>Version 2.76

- **Utgivningsdatum:**
  - 9 maj 2018 (Azure) | 21 juni 2018 (Azure Kina, Azure Government)
- **OS-support:**
  - Windows Server 2016
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
  - Windows Client 7/8.1/10
  - Nano Server
- **WMF stöd:**
  - WMF 5.1
  - WMF 5.0 RTM
  - WMF 4.0 uppdatera
  - WMF 4.0
- **Miljö:**
  - Azure
  - Azure Kina
  - Azure Government
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). DSC-rollen är installerad på den virtuella datorn för Nano Server.
- **Nya funktioner:**
  - Förbättring i metadata för tilläggen för understatus och andra mindre felkorrigeringar.

## <a name="supported-versions"></a>Versioner som stöds

> [!WARNING]
> Versioner 2.4 2.13 använder WMF 5.0 Public Preview vars certifikat för tokensignering har upphört att gälla i augusti 2016.  Mer information om det här problemet finns i [blogginlägget](https://blogs.msdn.microsoft.com/powershell/2016/05/24/azure-dsc-extension-versions-2-4-up-to-2-13-will-retire-in-august/).

### <a name="version-275"></a>Version 2.75

- **Utgivningsdatum:** 5 mars 2018
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF stöd:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update-, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). DSC-rollen är installerad på den virtuella datorn för Nano Server.
- **Nya funktioner:**
  - Efter Githubs senaste övergång till TLS 1.2, det går inte att publicera en virtuell dator till Azure Automation DSC med gör det själv Resource Manager-mallar som är tillgängliga på Azure Marketplace eller använda DSC-tillägget för att få någon config finns på GitHub. Ett fel som liknar följande när du distribuerar tillägget visas:

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

  - I den nya versionen av tillägget tillämpas nu TLS 1.2. När du distribuerar tillägget om du redan hade AutoUpgradeMinorVersion = true i Resource Manager-mall och sedan tillägget får autoupgraded till 2,75. Manuella uppdateringar ange `TypeHandlerVersion = 2.75` i Resource Manager-mallen.

### <a name="version-270---272"></a>Version 2.70 - 2.72

- **Utgivningsdatum:** Den 13 november 2017
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF stöd:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update-, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). DSC-rollen är installerad på den virtuella datorn för Nano Server.
- **Nya funktioner:**
  - Bugg korrigeringar och förbättringar som förenklar med hjälp av DSC Azure Automation via portalens användargränssnitt samt Resource Manager-mall.  Mer information finns i [standard konfigurationsskript](/azure/virtual-machines/extensions/dsc-overview) i DSC-tillägg-dokumentationen.

### <a name="version-226"></a>Version 2.26

- **Utgivningsdatum:** Den 9 juni 2017
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF stöd:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update-, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). DSC-rollen är installerad på den virtuella datorn för Nano Server.
- **Nya funktioner:**
  - Förbättringar av telemetri.

### <a name="version-225"></a>Version 2.25

- **Utgivningsdatum:** Den 2 juni 2017
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF stöd:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update-, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). DSC-rollen är installerad på den virtuella datorn för Nano Server.
- **Nya funktioner:**
  - Flera felkorrigeringar och andra mindre förbättringar har lagts till.

### <a name="version-224"></a>Version 2.24

- **Utgivningsdatum:** Den 13 april 2017
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF stöd:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update-, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). DSC-rollen är installerad på den virtuella datorn för Nano Server.
- **Nya funktioner:**
  - Visar VM UUID- & ID för DSC-agenten som metadata för tilläggen. Andra mindre förbättringar har lagts till.

### <a name="version-223"></a>Version 2.23

- **Utgivningsdatum:** Den 15 mars 2017
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF stöd:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update-, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). DSC-rollen är installerad på den virtuella datorn för Nano Server.
- **Nya funktioner:**
  - Många felkorrigeringar och andra förbättringar har lagts till.

### <a name="version-222"></a>Version 2.22

- **Utgivningsdatum:** Den 8 februari 2017
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF stöd:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update-, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). DSC-rollen är installerad på den virtuella datorn för Nano Server.
- **Nya funktioner:**
  - DSC-tillägget har nu stöd för WMF 5.1.
  - Mindre andra förbättringar har lagts till.

### <a name="version-221"></a>Version 2.21

- **Utgivningsdatum:** Den 2 december 2016
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF stöd:** WMF 5.1 förhandsversion, WMF 5.0 RTM, WMF 4.0 uppdaterar, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart). DSC-rollen är installerad på den virtuella datorn för Nano Server.
- **Nya funktioner:**
  - DSC-tillägget är nu tillgängligt på Nano Server. Den här versionen innehåller främst ändringar i koden för att köra tillägget på Nano Server.
  - Mindre andra förbättringar har lagts till.

### <a name="version-220"></a>Version 2.20

- **Utgivningsdatum:** Den 2 augusti 2016
- **OS-support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF stöd:** WMF 5.1 förhandsversion, WMF 5.0 RTM, WMF 4.0 uppdaterar, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - Förhandsversionen av stödet för WMF 5.1. När det publiceras för första gången, den här versionen har en valfri uppgradering och var du tvungen att ange Wmfversion = ' 5.1PP' i Resource Manager-mallar för att installera WMF 5.1-förhandsversion. Wmfversion = ”senaste” fortfarande installerar den [WMF 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/). Läs mer i förhandsversionen av WMF 5.1 [den här bloggen]( https://blogs.msdn.microsoft.com/powershell/2016/07/16/announcing-windows-management-framework-wmf-5-1-preview/).
  - Mindre korrigeringar och förbättringar har lagts till.

### <a name="version--219"></a>Version  2.19

- **Utgivningsdatum:** 3 juni 2016
- **OS-support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF stöd:** WMF 5.0 RTM, WMF 4.0 uppdaterar, WMF 4.0
- **Miljö:** Azure, Azure China, Azure Government
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - DSC-tillägget har nu publicerats i Azure i Kina. Den här versionen innehåller främst korrigeringar för att köra tillägget på Azure Kina.

### <a name="version-218"></a>Version 2.18

- **Utgivningsdatum:** 3 juni 2016
- **OS-support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF stöd:** WMF 5.0 RTM, WMF 4.0 uppdaterar, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - Se telemetri icke-blockerande när ett fel uppstår under snabbkorrigeringen för telemetri (känt problem med Azure DNS) eller under installationen.
  - Korrigering för tillfälligt fel där tillägget stoppar bearbetning av konfigurationen efter en omstart. Detta orsakades DSC-tillägget ska behållas i övergår tillståndet.
  - Mindre korrigeringar och förbättringar har lagts till.

### <a name="version-217"></a>Version 2.17

- **Utgivningsdatum:** 26 april 2016
- **OS-support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF stöd:** WMF 5.0 RTM, WMF 4.0 uppdaterar, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - Stöd för WMF 4.0 Update. Mer information om WMF 4.0-uppdateringen finns i [den här bloggen](https://blogs.msdn.microsoft.com/powershell/2016/01/19/windows-management-framework-wmf-4-0-update-now-available-for-windows-server-2012-windows-server-2008-r2-sp1-and-windows-7-sp1/).
  - Logik för omprövning av på fel som uppstår under installationen DSC-tillägget eller när en DSC-konfiguration efter tillägg installera. Som en del av den här ändringen kommer tillägget försök installera igen om en tidigare installation misslyckades eller nytt tillämpar en DSC-konfiguration som tidigare misslyckats, för högst tre gånger tills den når uppgiftens status (lyckades/fel) eller om en ny begäran kommer. Om tillägget misslyckas på grund av ogiltig användare inställningar/användarindata, det gör inget nytt försök. I det här fallet måste tillägget anropas igen med en ny begäran och korrigera användarinställningarna för. Anm DSC-tillägget är beroende av Azure VM-agenten för nya försök. Virtuella Azure-datoragenten anropar tillägget med den senaste misslyckade begäranden tills den når tillståndet – slutförd eller misslyckades.

### <a name="version-216"></a>Version 2.16

- **Utgivningsdatum:** Den 21 april 2016
- **OS-support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF stöd:** WMF 5.0 RTM WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - Förbättring av felhantering och andra mindre felkorrigeringar.
  - Ny egenskap i inställningarna för DSC-tillägget. ForcePullAndApply om du i AdvancedOptions har lagts till för att aktivera DSC-tillägget tillämpar DSC-konfigurationer när uppdatering-läget är Pull (i stället för standard Push-läge). Mer information finns i [den här bloggen](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/) vill ha mer information om inställningar för DSC-tillägget.

### <a name="version-215"></a>Version 2.15

- **Utgivningsdatum:** Den 14 mars 2016
- **OS-support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF stöd:** WMF 5.0 RTM WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - Ändringar för att installera WMF RTM ingick i tilläggsversion punkt 2.14. När du uppgraderar från tilläggsversion 2.13.2.0 2.14.0.0, kanske du märker att vissa DSC-cmdletar misslyckas eller konfigurationen misslyckas med ett fel – ”Nej instans hittades med angivna värden”. Mer information finns i den [DSC viktig](https://msdn.microsoft.com/en-us/powershell/wmf/limitation_dsc). Lösningar för dessa problem har lagts till i 2.15 version.
  - Om du redan har installerat version punkt 2.14 och körs i en av dessa två frågor, behöver du tyvärr att utföra dessa steg manuellt.  I en upphöjd PowerShell-session:
    - `Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof`
    - `mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof`

### <a name="version-214"></a>Version 2.14

- **Utgivningsdatum:** Den 25 februari 2016
- **OS-support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF stöd:** WMF 5.0 RTM WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** Den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - Använder WMF RTM.
  - Aktiverar datainsamling för att förbättra kvaliteten på DSC-tillägget. Mer information finns i [bloggen](https://blogs.msdn.microsoft.com/powershell/2016/02/02/azure-dsc-extension-data-collection-2/).
  - Tillhandahåller ett format för uppdaterade inställningarna för tillägget i Resource Manager-mall. Mer information finns i [bloggen](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/).
  - Felkorrigeringar och andra förbättringar.

## <a name="next-steps"></a>Nästa steg

- Mer information om PowerShell DSC, går du till den [PowerShell dokumentationscentret](../overview/overview.md).
- Granska den [Resource Manager-mall för DSC-tillägget](/azure/virtual-machines/extensions/dsc-template).
- Fler funktioner som du kan hantera med hjälp av PowerShell DSC, samt mer DSC-resurser, bläddra i [PowerShell-galleriet](https://www.powershellgallery.com/packages?q=DscResource&x=0&y=0).
- Mer information om att skicka känslig parametrar i konfigurationer finns i [hantera autentiseringsuppgifter på ett säkert sätt med DSC-tilläggshanterare](/azure/virtual-machines/extensions/dsc-credentials).