---
description: Läs mer om versions historiken för det önskade tillägget för tillstånds konfiguration (DSC) i Azure.
ms.date: 06/21/2018
keywords: DSC, PowerShell, Azure, tillägg
title: Versions historik för Azure DSC-tillägg
ms.openlocfilehash: 7a89037d62cb2c8580141d2b177fdded5db654eb
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417293"
---
# <a name="azure-desired-state-configuration-extension-version-history"></a>Versions historik för det önskade tillstånds konfigurations tillägget i Azure

Det virtuella Azure-tillägget för önskad tillstånds konfiguration (DSC) uppdateras som-nödvändigt för att stödja förbättringar och nya funktioner som levereras av Azure, Windows Server och Windows Management Framework (WMF) som innehåller Windows PowerShell.

Den här artikeln innehåller information om varje version av Azure DSC VM-tillägget, vilka miljöer som stöds och kommentarer och kommentarer om nya funktioner eller ändringar.

## <a name="latest-version"></a>Senaste version

### <a name="version-276"></a>Version 2,76

- **Utgivnings datum:**
  - 9 maj 2018 (Azure) | 21 juni 2018 (Azure Kina, Azure Government)
- **OS-support:**
  - Windows Server 2016
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
  - Windows-klient 7/8.1/10
  - Nano Server
- **WMF-support:**
  - WMF 5.1
  - WMF 5,0 RTM
  - WMF 4,0-uppdatering
  - WMF 4,0
- **Miljö**
  - Azure
  - Azure Kina
  - Azure Government
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativ system installerar den [Windows Management Framework 5,1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installation av WMF kräver en omstart). För Nano Server installeras DSC-rollen på den virtuella datorn.
- **Nya funktioner:**
  - Förbättringar i tilläggets metadata för under status och andra mindre fel korrigeringar.

## <a name="supported-versions"></a>Versioner som stöds

> [!WARNING]
> Version 2,4 till 2,13 Använd WMF 5,0 offentlig för hands version vars signerings certifikat upphör att gälla i augusti 2016.  Mer information om det här problemet finns i [blogg inlägg](https://blogs.msdn.microsoft.com/powershell/2016/05/24/azure-dsc-extension-versions-2-4-up-to-2-13-will-retire-in-august/).

### <a name="version-275"></a>Version 2.75

- **Utgivnings datum:** 5 mars 2018
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows-klient 7/8.1/10, Nano Server
- **WMF-support:** WMF 5,1, WMF 5,0 RTM, WMF 4,0 Update, WMF 4,0
- **Miljö:** Azure
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativ system installerar den [Windows Management Framework 5,1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installation av WMF kräver en omstart). För Nano Server installeras DSC-rollen på den virtuella datorn.
- **Nya funktioner:**
  - När GitHub senaste flytt till TLS 1,2 kan du inte publicera en virtuell dator till Azure Automation DSC med hjälp av gör det själv Resource Manager-mallar som är tillgängliga på Azure Marketplace eller använda DSC-tillägget för att hämta alla konfigurationer som finns på GitHub. Ett fel som liknar följande visas vid distribution av tillägget:

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

  - I den nya tilläggs versionen tillämpas nu TLS 1,2. När du distribuerar tillägget om du redan hade aktiverat autoupgrademinorversion = true i Resource Manager-mallen, kommer tillägget att uppdateras automatiskt till 2,75. För manuella uppdateringar anger du `TypeHandlerVersion = 2.75` i din Resource Manager-mall.

### <a name="version-270---272"></a>Version 2,70-2,72

- **Utgivnings datum:** 13 november 2017
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows-klient 7/8.1/10, Nano Server
- **WMF-support:** WMF 5,1, WMF 5,0 RTM, WMF 4,0 Update, WMF 4,0
- **Miljö:** Azure
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativ system installerar den [Windows Management Framework 5,1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installation av WMF kräver en omstart). För Nano Server installeras DSC-rollen på den virtuella datorn.
- **Nya funktioner:**
  - Fel korrigeringar & förbättringar som fören klar användningen av DSC-Azure Automation via användar gränssnittet för portalen samt Resource Manager-mall.  Mer information finns i [standard konfigurations skript](/azure/virtual-machines/extensions/dsc-overview) i dokumentationen för DSC-tillägget.

### <a name="version-226"></a>Version 2.26

- **Utgivnings datum:** 9 juni 2017
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows-klient 7/8.1/10, Nano Server
- **WMF-support:** WMF 5,1, WMF 5,0 RTM, WMF 4,0 Update, WMF 4,0
- **Miljö:** Azure
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativ system installerar den [Windows Management Framework 5,1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installation av WMF kräver en omstart). För Nano Server installeras DSC-rollen på den virtuella datorn.
- **Nya funktioner:**
  - Förbättringar av telemetri.

### <a name="version-225"></a>Version 2.25

- **Utgivnings datum:** 2 juni 2017
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows-klient 7/8.1/10, Nano Server
- **WMF-support:** WMF 5,1, WMF 5,0 RTM, WMF 4,0 Update, WMF 4,0
- **Miljö:** Azure
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativ system installerar den [Windows Management Framework 5,1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installation av WMF kräver en omstart). För Nano Server installeras DSC-rollen på den virtuella datorn.
- **Nya funktioner:**
  - Flera fel korrigeringar och andra mindre förbättringar har lagts till.

### <a name="version-224"></a>Version 2.24

- **Utgivnings datum:** 13 april 2017
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF-support:** WMF 5,1, WMF 5,0 RTM, WMF 4,0 Update, WMF 4,0
- **Miljö:** Azure
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativ system installerar den [Windows Management Framework 5,1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installation av WMF kräver en omstart). För Nano Server installeras DSC-rollen på den virtuella datorn.
- **Nya funktioner:**
  - Exponerar VM-UUID & DSC-agent-ID som tilläggs-metadata. Andra mindre förbättringar har lagts till.

### <a name="version-223"></a>Version 2.23

- **Utgivnings datum:** 15 mars 2017
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF-support:** WMF 5,1, WMF 5,0 RTM, WMF 4,0 Update, WMF 4,0
- **Miljö:** Azure
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativ system installerar den [Windows Management Framework 5,1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installation av WMF kräver en omstart). För Nano Server installeras DSC-rollen på den virtuella datorn.
- **Nya funktioner:**
  - Många fel korrigeringar och andra förbättringar har lagts till.

### <a name="version-222"></a>Version 2.22

- **Utgivnings datum:** 8 februari 2017
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF-support:** WMF 5,1, WMF 5,0 RTM, WMF 4,0 Update, WMF 4,0
- **Miljö:** Azure
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativ system installerar den [Windows Management Framework 5,1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installation av WMF kräver en omstart). För Nano Server installeras DSC-rollen på den virtuella datorn.
- **Nya funktioner:**
  - DSC-tillägget har nu stöd för WMF 5,1.
  - Mindre andra förbättringar har lagts till.

### <a name="version-221"></a>Version 2.21

- **Utgivnings datum:** 2 december 2016
- **OS-support:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF-support:** WMF 5,1 Preview, WMF 5,0 RTM, WMF 4,0 Update, WMF 4,0
- **Miljö:** Azure
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016; för andra Windows-operativ system installeras [Windows Management Framework 5,0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installation av WMF kräver en omstart). För Nano Server installeras DSC-rollen på den virtuella datorn.
- **Nya funktioner:**
  - DSC-tillägget är nu tillgängligt på Nano Server. Den här versionen innehåller främst kod ändringar för att köra tillägget på Nano Server.
  - Mindre andra förbättringar har lagts till.

### <a name="version-220"></a>Version 2.20

- **Utgivnings datum:** 2 augusti 2016
- **OS-support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF-support:** WMF 5,1 Preview, WMF 5,0 RTM, WMF 4,0 Update, WMF 4,0
- **Miljö:** Azure
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativ system installeras [Windows Management Framework 5,0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installation av WMF kräver en omstart).
- **Nya funktioner:**
  - Stöd för för hands versionen av WMF 5,1. Vid den första publiceringen var den här versionen en valfri uppgradering och du måste ange Wmfversion = ' 5,1 PP ' i Resource Manager-mallar för att installera WMF 5,1 Preview. Wmfversion = "senaste" installerar fortfarande [WMF 5,0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/). Mer information om för hands versionen av WMF 5,1 finns i [den här bloggen](https://blogs.msdn.microsoft.com/powershell/2016/07/16/announcing-windows-management-framework-wmf-5-1-preview/).
  - Mindre andra korrigeringar och förbättringar har lagts till.

### <a name="version--219"></a>Version 2,19

- **Utgivnings datum:** 3 juni 2016
- **OS-support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF-support:** WMF 5,0 RTM, WMF 4,0 uppdatering, WMF 4,0
- **Miljö:** Azure, Azure Kina, Azure Government
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativ system installeras [Windows Management Framework 5,0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installation av WMF kräver en omstart).
- **Nya funktioner:**
  - DSC-tillägget har nu publicerats till Azure Kina. Den här versionen innehåller främst korrigeringar för att köra tillägget på Azure Kina.

### <a name="version-218"></a>Version 2.18

- **Utgivnings datum:** 3 juni 2016
- **OS-support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF-support:** WMF 5,0 RTM, WMF 4,0 uppdatering, WMF 4,0
- **Miljö:** Azure
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativ system installeras [Windows Management Framework 5,0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installation av WMF kräver en omstart).
- **Nya funktioner:**
  - Gör telemetri icke-blockerande om ett fel inträffar under hämtningen av snabb korrigering för telemetri (känt Azure DNS problem) eller under installationen.
  - Åtgärda det tillfälliga problemet när tillägget slutar att bearbeta konfigurationen efter en omstart. Detta gjorde att DSC-tillägget är kvar i läget "över gång".
  - Mindre andra korrigeringar och förbättringar har lagts till.

### <a name="version-217"></a>Version 2.17

- **Utgivnings datum:** 26 april 2016
- **OS-support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF-support:** WMF 5,0 RTM, WMF 4,0 uppdatering, WMF 4,0
- **Miljö:** Azure
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativ system installeras [Windows Management Framework 5,0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installation av WMF kräver en omstart).
- **Nya funktioner:**
  - Stöd för WMF 4,0-uppdatering. Mer information om WMF 4,0-uppdateringen finns i [den här bloggen](https://blogs.msdn.microsoft.com/powershell/2016/01/19/windows-management-framework-wmf-4-0-update-now-available-for-windows-server-2012-windows-server-2008-r2-sp1-and-windows-7-sp1/).
  - Försök att använda logiken på fel som inträffar under DSC-tillägget installera eller tillämpa en installation av DSC-konfiguration efter tillägg. Som en del av den här ändringen kommer tillägget att försöka installera igen om en tidigare installation misslyckades eller att införa en ny DSC-konfiguration som tidigare har misslyckats, under högst tre gånger tills den når slut för ande tillstånd (lyckades/fel) eller om en ny begäran kommer. Om tillägget Miss lyckas på grund av ogiltiga användar inställningar/användarindata, görs inget nytt försök. I det här fallet måste tillägget anropas igen med en ny begäran och rätt användar inställningar. Obs! DSC-tillägget är beroende av Azure VM-agenten för nya försök. Azure VM-agenten anropar tillägget med den senaste misslyckade begäran tills den når ett lyckat eller fel tillstånd.

### <a name="version-216"></a>Version 2.16

- **Utgivnings datum:** 21 april 2016
- **OS-support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF-support:** WMF 5,0 RTM, WMF 4,0
- **Miljö:** Azure
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativ system installeras [Windows Management Framework 5,0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installation av WMF kräver en omstart).
- **Nya funktioner:**
  - Förbättring av fel hantering och andra mindre fel korrigeringar.
  - Ny egenskap i inställningar för DSC-tillägg. "ForcePullAndApply" i AdvancedOptions läggs till för att aktivera DSC-tillägget implementera DSC-konfigurationer när uppdaterings läget är pull (till skillnad från standard push-läget). Mer information finns i [den här bloggen](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/) för att få mer information om DSC-tilläggets inställningar.

### <a name="version-215"></a>Version 2.15

- **Utgivnings datum:** 14 mars 2016
- **OS-support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF-support:** WMF 5,0 RTM, WMF 4,0
- **Miljö:** Azure
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativ system installeras [Windows Management Framework 5,0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installation av WMF kräver en omstart).
- **Nya funktioner:**
  - I tillägg version 2,14 inkluderades ändringar i installationen av WMF RTM. När du uppgraderar från tilläggets version 2.13.2.0 till 2.14.0.0, kan det hända att vissa DSC-cmdlets Miss lyckas eller att konfigurationen Miss lyckas med ett fel – "ingen instans hittades med de tilldelade egenskapsvärdena". Mer information finns i viktig information om [DSC](/powershell/scripting/wmf/known-issues/known-issues-dsc). Lösningarna för de här problemen har lagts till i 2,15-versionen.
  - Om du redan har installerat version 2,14 och körs i något av ovanstående två problem, måste du utföra dessa steg manuellt.  I en upphöjd PowerShell-session:
    - `Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof`
    - `mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof`

### <a name="version-214"></a>Version 2.14

- **Utgivnings datum:** 25 februari 2016
- **OS-support:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF-support:** WMF 5,0 RTM, WMF 4,0
- **Miljö:** Azure
- **Anmärkningar:** Den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativ system installeras [Windows Management Framework 5,0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installation av WMF kräver en omstart).
- **Nya funktioner:**
  - Använder WMF RTM.
  - Möjliggör insamling av data för att förbättra kvaliteten på DSC-tillägget. Mer information finns i [bloggen](https://blogs.msdn.microsoft.com/powershell/2016/02/02/azure-dsc-extension-data-collection-2/).
  - Innehåller ett uppdaterat inställnings format för tillägget i en Resource Manager-mall. Mer information finns i [bloggen](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/).
  - Fel korrigeringar och andra förbättringar.

## <a name="next-steps"></a>Nästa steg

- Mer information om PowerShell DSC finns i [PowerShell-dokumentations centret](../overview/overview.md).
- Granska [Resource Manager-mallen för DSC-tillägget](/azure/virtual-machines/extensions/dsc-template).
- Om du vill ha fler funktioner som du kan hantera med hjälp av PowerShell DSC kan du bläddra i [PowerShell-galleriet](https://www.powershellgallery.com/packages?q=DscResource&x=0&y=0)för fler DSC-resurser.
- Mer information om hur du skickar känsliga parametrar till konfigurationer finns i [Hantera autentiseringsuppgifter säkert med DSC-tilläggs hanteraren](/azure/virtual-machines/extensions/dsc-credentials).
