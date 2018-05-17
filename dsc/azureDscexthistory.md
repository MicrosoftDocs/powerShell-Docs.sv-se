---
description: Mer information om tidigare versioner för önskad tillstånd Configuration DSC ()-tillägget i Azure.
ms.date: 05/09/2018
keywords: DSC, powershell, azure, tillägg
title: Versionshistorik för Azure DSC-tillägg
ms.openlocfilehash: 81dfcf81bd8f8685a0c8c81cd07bc5447e1abf94
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="azure-desired-state-configuration-extension-version-history"></a>Versionshistorik för Azure önskade tillstånd Configuration-tillägg

VM-tillägget Azure önskad tillstånd Configuration (DSC) uppdateras som krävs för stöd av förbättringar och nya funktioner som levereras av Azure, Windows Server och i Windows Management Framework (WMF) som innehåller Windows PowerShell.

Den här artikeln innehåller information om varje version av VM-tillägget Azure DSC vilka miljöer som har stöd för, och kommentarer och anmärkningar om nya funktioner och ändringar.

## <a name="latest-versions"></a>Senaste version

### <a name="version-276"></a>Version 2.76

- **Utgivningsdatum:**
  - 9 kan 2018
- **OS-stöd:**
  - Windows Server 2016
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
  - Klienten för Windows 8.1/7/10
  - Nano Server
- **WMF stöd:**
  - WMF 5.1
  - WMF 5.0 RTM
  - WMF 4.0 uppdatera
  - WMF 4.0
- **Miljö:**
  - Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016, för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). För Nano Server är DSC-rollen installerad på den virtuella datorn.
- **Nya funktioner:**
  - Förbättring i tillägget metadata för understatus och andra mindre felkorrigeringar.

### <a name="version-219"></a>Version 2.19

- **Utgivningsdatum:**
  - 3 juni 2016
- **OS-stöd:**
  - Windows Server 2016 Technical Preview
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
- **WMF stöd:**
  - WMF 5.0 RTM
  - WMF 4.0 uppdatera
  - WMF 4.0
- **Miljö:**
  - Azure
  - Azure Kina
  - Azure Government
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview, för andra operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - DSC-tillägg är nu på avgränsad till Azure Kina. Den här versionen innehåller i första hand korrigeringar för att köra tillägget på Azure Kina.

## <a name="supported-versions"></a>Versioner som stöds

> [!WARNING]
> Versioner 2.4 2.13 använder WMF 5.0 Public Preview vars signering av certifikat som upphört att gälla i augusti 2016.  Mer information om det här problemet finns [blogginlägget](https://blogs.msdn.microsoft.com/powershell/2016/05/24/azure-dsc-extension-versions-2-4-up-to-2-13-will-retire-in-august/).

### <a name="version-275"></a>Version 2.75

- **Utgivningsdatum:** 5 mars 2018
- **OS-stöd:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF stöd:** WMF 5.1, WMF 5.0 RTM, WMF 4.0-uppdateringen, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016, för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). För Nano Server är DSC-rollen installerad på den virtuella datorn.
- **Nya funktioner:**
  - Efter Githubs senaste flytta TLS 1.2, det går inte att publicera en virtuell dator till Azure Automation DSC med själv Resource Manager-mallar som är tillgängliga på Azure Marketplace eller använda DSC-tillägg för att få alla config finns på GitHub. Ett fel som liknar följande vid distribution av tillägget visas:

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

  - TLS 1.2 har nu verkställts i den nya tilläggsversionen. Vid distribution av tillägget om du redan hade AutoUpgradeMinorVersion = true i Resource Manager-mall och sedan tillägget får autoupgraded till 2,75. Manuella uppdateringar ange `TypeHandlerVersion = 2.75` i Resource Manager-mall.

### <a name="version-270---272"></a>Version 2.70 2.72

- **Utgivningsdatum:** 13 November 2017
- **OS-stöd:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF stöd:** WMF 5.1, WMF 5.0 RTM, WMF 4.0-uppdateringen, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016, för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). För Nano Server är DSC-rollen installerad på den virtuella datorn.
- **Nya funktioner:**
  - Programfel korrigeringar och förbättringar som gör det enklare att använda DSC Azure Automation via portalen Användargränssnittet, samt Resource Manager-mall.  Mer information finns i [standard konfigurationsskript](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/extensions-dsc-overview#default-configuration-script) i DSC-tillägg-dokumentationen.

### <a name="version-226"></a>Version 2.26

- **Utgivningsdatum:** den 9 juni 2017
- **OS-stöd:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF stöd:** WMF 5.1, WMF 5.0 RTM, WMF 4.0-uppdateringen, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016, för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). För Nano Server är DSC-rollen installerad på den virtuella datorn.
- **Nya funktioner:**
  - Telemetri förbättringar.

### <a name="version-225"></a>Version 2.25

- **Utgivningsdatum:** 2 juni 2017
- **OS-stöd:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **WMF stöd:** WMF 5.1, WMF 5.0 RTM, WMF 4.0-uppdateringen, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016, för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). För Nano Server är DSC-rollen installerad på den virtuella datorn.
- **Nya funktioner:**
  - Flera felkorrigeringar och andra mindre förbättringar har lagts till.

### <a name="version-224"></a>Version 2.24

- **Utgivningsdatum:** 13 April 2017
- **OS-stöd:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1 Nano Server
- **WMF stöd:** WMF 5.1, WMF 5.0 RTM, WMF 4.0-uppdateringen, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016, för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). För Nano Server är DSC-rollen installerad på den virtuella datorn.
- **Nya funktioner:**
  - Visar VM UUID & DSC Agent-ID som tillägget metadata. Andra mindre förbättringar har lagts till.

### <a name="version-223"></a>Version 2.23

- **Utgivningsdatum:** 15 mars 2017
- **OS-stöd:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1 Nano Server
- **WMF stöd:** WMF 5.1, WMF 5.0 RTM, WMF 4.0-uppdateringen, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016, för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). För Nano Server är DSC-rollen installerad på den virtuella datorn.
- **Nya funktioner:**
  - Många felkorrigeringar och andra förbättringar har lagts till.

### <a name="version-222"></a>Version 2.22

- **Utgivningsdatum:** 8 februari 2017
- **OS-stöd:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1 Nano Server
- **WMF stöd:** WMF 5.1, WMF 5.0 RTM, WMF 4.0-uppdateringen, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016, för andra Windows-operativsystem installeras den [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (installera WMF kräver en omstart). För Nano Server är DSC-rollen installerad på den virtuella datorn.
- **Nya funktioner:**
  - DSC-tillägg har nu stöd för WMF 5.1.
  - Lägre andra förbättringar har lagts till.

### <a name="version-221"></a>Version 2.21

- **Utgivningsdatum:** 2 December 2016
- **OS-stöd:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1 Nano Server
- **WMF stöd:** WMF 5.1 Preview, WMF 5.0 RTM, WMF 4.0-uppdateringen, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016, för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart). För Nano Server är DSC-rollen installerad på den virtuella datorn.
- **Nya funktioner:**
  - DSC-tillägg finns nu på Nano Server. Den här versionen innehåller i första hand kodändringar för att köra tillägget på Nano Server.
  - Lägre andra förbättringar har lagts till.

### <a name="version-220"></a>Version 2.20

- **Utgivningsdatum:** 2 augusti 2016
- **OS-stöd:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF stöd:** WMF 5.1 Preview, WMF 5.0 RTM, WMF 4.0-uppdateringen, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - Stöd för WMF 5.1 Preview. Första gången de publiceras, den här versionen har en valfri uppgradering och var du tvungen att ange Wmfversion = ' 5.1PP' i Resource Manager-mallar för att installera WMF 5.1 preview. Wmfversion = ”senaste” fortfarande installerar den [WMF 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/). Läs mer på WMF 5.1 preview [bloggen]( https://blogs.msdn.microsoft.com/powershell/2016/07/16/announcing-windows-management-framework-wmf-5-1-preview/).
  - Lägre korrigeringar och förbättringar har lagts till.

### <a name="version--219"></a>Version 2.19

- **Utgivningsdatum:** 3 juni 2016
- **OS-stöd:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF stöd:** WMF 5.0 RTM, WMF 4.0-uppdateringen, WMF 4.0
- **Miljö:** Azure, Azure Kina Azure Government
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - DSC-tillägg är nu publicerats så att Azure Kina. Den här versionen innehåller i första hand korrigeringar för att köra tillägget på Azure Kina.

### <a name="version-218"></a>Version 2.18

- **Utgivningsdatum:** 3 juni 2016
- **OS-stöd:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF stöd:** WMF 5.0 RTM, WMF 4.0-uppdateringen, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - Se telemetri inte blockerar när ett fel uppstår under telemetri snabbkorrigering (känt Azure DNS-problem) eller under installationen.
  - Åtgärda för tillfälligt fel där tillägget stoppar bearbetning av konfigurationen efter en omstart. Detta orsakades DSC-tillägg finns kvar i övergång tillstånd.
  - Lägre korrigeringar och förbättringar har lagts till.

### <a name="version-217"></a>Version 2.17

- **Utgivningsdatum:** 26 April 2016
- **OS-stöd:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF stöd:** WMF 5.0 RTM, WMF 4.0-uppdateringen, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - Stöd för WMF 4.0-uppdateringen. Mer information om WMF 4.0-uppdateringen finns [bloggen](https://blogs.msdn.microsoft.com/powershell/2016/01/19/windows-management-framework-wmf-4-0-update-now-available-for-windows-server-2012-windows-server-2008-r2-sp1-and-windows-7-sp1/).
  - Installera logik på fel som uppstår under installationen DSC-tillägg eller efter tillägg när DSC-konfigurationen. Som en del av den här ändringen tillägget försök installera igen om en tidigare installation misslyckades eller nytt tillämpar en DSC-konfiguration som tidigare inte hade, maximalt tre gånger tills slutförandetillstånd (lyckade/fel) eller om en ny begäran kommer. Om tillägget misslyckas på grund av ogiltiga inställningar/användare användarindata, det gör inget nytt försök. I det här fallet måste tillägget anropas igen med en ny begäran och korrigera användarinställningar. Obs: DSC-tillägg är beroende av Virtuella Azure-agenten för försök. Azure VM-agenten anropar tillägget med den senaste misslyckade begäranden tills ett slutfört eller fel tillstånd.

### <a name="version-216"></a>Version 2.16

- **Utgivningsdatum:** 21 April 2016
- **OS-stöd:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF stöd:** WMF 5.0 RTM, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - Förbättring i felhantering och andra mindre felkorrigeringar.
  - Ny egenskap i inställningarna för DSC-tillägg. ForcePullAndApply om du i AdvancedOptions har lagts till för att aktivera DSC-tillägg tillämpar DSC-konfigurationer när uppdateringen-läget är Pull (i stället för standard Push-läge). Mer information finns i [bloggen](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/) för mer information om inställningar för DSC-tillägg.

### <a name="version-215"></a>Version 2.15

- **Utgivningsdatum:** 14 mars 2016
- **OS-stöd:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF stöd:** WMF 5.0 RTM, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - Ändringar i installera WMF RTM ingick i tilläggsversionen punkt 2.14. Det kan hända att vissa DSC-cmdletar misslyckas eller konfigurationen misslyckas med felmeddelandet – 'Nej instansen hittades med angivna egenskapsvärden' vid uppgradering från version tillägg 2.13.2.0 2.14.0.0. Mer information finns i [DSC viktig information](https://msdn.microsoft.com/en-us/powershell/wmf/limitation_dsc). Lösningar på problemen har lagts till i 2.15 version.
  - Tyvärr om du redan har installerat version punkt 2.14 och kör i något av dessa två frågor, måste du utföra dessa steg manuellt.  I en upphöjd PowerShell-session:
    - `Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof`
    - `mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof`

### <a name="version-214"></a>Version 2.14

- **Utgivningsdatum:** 25 februari 2016
- **OS-stöd:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF stöd:** WMF 5.0 RTM, WMF 4.0
- **Miljö:** Azure
- **Anmärkning:** den här versionen använder DSC som ingår i Windows Server 2016 Technical Preview; för andra Windows-operativsystem installeras den [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (installera WMF kräver en omstart).
- **Nya funktioner:**
  - Använder WMF RTM.
  - Aktiverar datainsamling för att förbättra kvaliteten på DSC-tillägg. Mer information finns i [bloggen](https://blogs.msdn.microsoft.com/powershell/2016/02/02/azure-dsc-extension-data-collection-2/).
  - Innehåller ett format med uppdaterade inställningar för tillägget i en Resource Manager-mall. Mer information finns i [bloggen](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/).
  - Felkorrigeringar och andra förbättringar.

## <a name="next-steps"></a>Nästa steg

- Mer information om PowerShell DSC går du till den [PowerShell Dokumentationscenter](overview.md).
- Granska de [Resource Manager-mall för DSC-tillägg](/azure/virtual-machines/windows/extensions-dsc-template).
- Fler funktioner som du kan hantera med hjälp av PowerShell DSC, samt mer DSC-resurser, bläddra i [PowerShell-galleriet](https://www.powershellgallery.com/packages?q=DscResource&x=0&y=0).
- Mer information om att skicka känslig parametrar i konfigurationer finns [hantera autentiseringsuppgifter på ett säkert sätt med hanteraren för DSC-tillägg](/azure/virtual-machines/windows/extensions-dsc-credentials).