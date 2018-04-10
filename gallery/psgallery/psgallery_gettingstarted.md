---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: 599b148e141ba4205a7c774581e737a5d54bfae1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="get-started-with-the-powershell-gallery"></a>Kom igång med PowerShell-galleriet

## <a name="what-is-the-powershell-gallery"></a>Vad är PowerShell-galleriet?

PowerShell-galleriet är en central lagringsplats för PowerShell-innehåll.
I den hittar du användbar PowerShell-moduler som innehåller PowerShell-kommandon och önskade tillstånd Configuration DSC ()-resurser. Du kan också hitta PowerShell-skript, vilket kan innehålla PowerShell-arbetsflöden och som beskriver en uppsättning uppgifter och ange ordningsföljd för dessa aktiviteter.
Vissa av dessa element skapats av Microsoft och andra skapats av PowerShell-communityn.

## <a name="requirements"></a>Krav

Hämtar objekt från PowerShell-galleriet till systemet kräver den [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) modul. Modulen PowerShellGet hittar du i något av följande. Du behöver inte logga in kan du hämta från PowerShell-galleriet.

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [MSI Installer (för PowerShell 3 och 4)](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

PowerShellGet kräver också den [NuGet provider](http://go.microsoft.com/fwlink/?LinkId=722208) att arbeta med PowerShell-galleriet. Du uppmanas att installera NuGet-providern automatiskt vid första användning av PowerShellGet om NuGet-providern inte är i något av följande platser:

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

Du kan köra `Install-PackageProvider -Name NuGet -Force` att automatisera hämtning och installation av NuGet-providern.


Om du har en version som är äldre än 2.8.5.201 av NuGet måste anropa följande PowerShell-cmdlets för att installera och växla till den senaste versionen av NuGet.

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  Ta bort den äldre versionen av NuGet från ovan installationsplats.

Mer information finns i <http://oneget.org/> .


Obs: På grund av ändringar i paketering format rekommenderar vi du uppdaterar till den senaste versionen av PowerShellGet och PackageManagement för att installera objekt som nyligen har uppdaterats. PowerShellGet ingår i Windows 10 som du kan lära dig mer om [här](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409).
PowerShellGet är också en del av de Windows Management Framework (WMF) 5.0, som du kan hämta [här](http://go.microsoft.com/fwlink/?LinkId=398175).

## <a name="discovering-items-from-the-powershell-gallery"></a>Identifiering av objekt från PowerShell-galleriet

Du hittar objekt i PowerShell-galleriet med hjälp av den **Sök** kontroll på den här webbplatsen, eller genom att gå igenom sidorna moduler och skript. Du kan också hitta objekt från PowerShell-galleriet genom att köra den [hitta modulen](https://go.microsoft.com/fwlink/?LinkId=821658) och [hitta skriptet](https://go.microsoft.com/fwlink/?LinkId=822322) cmdlets, beroende på vilken objektet med `-Repository PSGallery`.

Filtrerar resultaten från galleriet kan göras med hjälp av följande parametrar för [hitta modulen](https://go.microsoft.com/fwlink/?LinkId=821658) och [Sök-skript](https://go.microsoft.com/fwlink/?LinkId=822322)

- Namn
- AllVersions
- MinimumVersion
- RequiredVersion
- Tagg
- Innehåller
- DscResource
- RoleCapability
- Kommando
- Filter

Om du bara är intresserad av att identifiera specifika DSC-resurser i galleriet, kan du köra den [hitta DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) cmdlet.
[Hitta DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) returnerar data på DSC-resurser som ingår i galleriet. Eftersom DSC resurser levereras alltid som en del av en modul, du fortfarande behöver köra [installera modulen](https://go.microsoft.com/fwlink/?LinkId=821663) att installera de DSC-resurserna.

## <a name="learning-about-items-in-the-powershell-gallery"></a>Lär dig hur objekten i PowerShell-galleriet

När du har hittat ett objekt som du är intresserad kan du vill veta mer om den. Du kan göra detta genom att undersöka artikelns viss sida i galleriet. På sidan, kommer du att kunna se alla metadata tillsammans med objektet. Dessa metadata för en artikel tillhandahålls av objektets författare och verifieras inte av Microsoft. Ägaren av det kopplat starkt till Gallery-kontot som används för att publicera artikeln och är mer tillförlitlig än fältet Författare.

Om du upptäcker ett objekt som du inte har publicerats i god tro klickar du på **Rapportera missbruk** på sidan för att objektet.

Om du kör [hitta modulen](https://go.microsoft.com/fwlink/?LinkId=821658) eller [hitta skriptet](https://go.microsoft.com/fwlink/?LinkId=822322), du kan visa informationen i det returnerade PSGetModuleInfo-objektet.
Till exempel köra `Find-Module -Name PSReadLine -Repository PSGallery | Get-Member` returnerar data i modulen PSReadLine i galleriet.

## <a name="downloading-items-from-the-powershell-gallery"></a>Ladda ned objekt från PowerShell-galleriet

Vi rekommenderar följande process när du hämtar objekt från PowerShell-galleriet:

### <a name="inspect"></a>Inspektera

Om du vill ladda ned ett objekt från galleriet för inspektion, kör du antingen den [spara modulen](https://go.microsoft.com/fwlink/?LinkId=821669) eller [spara skriptet](https://go.microsoft.com/fwlink/?LinkId=822334) cmdlet, beroende på vilken typ av objekt. På så sätt kan du spara objektet lokalt utan att installera den och kontrollerar du innehållet för objektet. Kom ihåg att ta bort det sparade objektet manuellt.

Vissa av dessa element skapats av Microsoft och andra skapats av PowerShell-communityn. Microsoft rekommenderar att du läser innehåll och kod för artiklar i det här galleriet före installationen.

Om du upptäcker ett objekt som du inte har publicerats i god tro klickar du på **Rapportera missbruk** på sidan för att objektet.

### <a name="install"></a>Installera

Installera ett objekt från galleriet för att köra antingen den [installera modulen](https://go.microsoft.com/fwlink/?LinkId=821663) eller [installationsskriptet](https://go.microsoft.com/fwlink/?LinkId=822327) cmdlet, beroende på vilken typ av objekt.

[Installera modulen](https://go.microsoft.com/fwlink/?LinkId=821663) installerar modulen `$env:ProgramFiles\WindowsPowerShell\Modules` som standard. Detta kräver att ett administratörskonto. Om du lägger till den `-Scope
CurrentUser` parametern modulen är installerad så att `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Installationsskriptet](https://go.microsoft.com/fwlink/?LinkId=822327) installerar skriptet till `$env:ProgramFiles\WindowsPowerShell\Scripts` som standard. Detta kräver att ett administratörskonto. Om du lägger till den `-Scope
CurrentUser` parametern skriptet installeras på `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Som standard [installera modulen](https://go.microsoft.com/fwlink/?LinkId=821663) och [installationsskriptet](https://go.microsoft.com/fwlink/?LinkId=822327) installerar den senaste versionen av ett objekt. Installera en äldre version av objektet genom att lägga till den `-RequiredVersion` parameter.

### <a name="deploy"></a>Distribuera

Om du vill distribuera ett objekt från PowerShell-galleriet till Azure Automation klickar du på **till Azure Automation** på informationssidan för objektet. Du omdirigeras till Azure-hanteringsportalen där du loggar in med dina Azure-autentiseringsuppgifter. Observera att distribuera objekt med beroenden distribuerar alla beroenden till Azure Automation. Knappen ”distribuera till Azure Automation-kan inaktiveras genom att lägga till den **AzureAutomationNotSupported** så att dina objektmetadata.

Läs mer om Azure Automation i den [Azure Automation-webbplatsen](http://azure.microsoft.com/services/automation/).

## <a name="updating-items-from-the-powershell-gallery"></a>Uppdaterar objekt från PowerShell-galleriet

Uppdatera objekt från PowerShell-galleriet genom att köra något av [uppdatering modulen](https://go.microsoft.com/fwlink/?LinkID=398576) eller [skript för uppdatering](http://go.microsoft.com/fwlink/?LinkId=619787) cmdlet. När kör utan ytterligare parametrar, [uppdatering modulen](https://go.microsoft.com/fwlink/?LinkID=398576) försöker uppdatera varje modul som har installerats genom att köra [installera modulen](https://go.microsoft.com/fwlink/?LinkId=821663).
Uppdatera selektivt moduler genom att lägga till den `-Name` parameter.

På liknande sätt när kör utan ytterligare parametrar, [skript för uppdatering](http://go.microsoft.com/fwlink/?LinkId=619787) också försöker uppdatera varje skript installerat genom att köra [installationsskriptet](https://go.microsoft.com/fwlink/?LinkId=822327).
Uppdatera selektivt skript genom att lägga till den `-Name` parameter.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Lista över artiklar som du har installerat från PowerShell-galleriet

Om du vill ta reda på vilka moduler som du har installerat från PowerShell-galleriet kan köra den [Get-InstalledModule](https://go.microsoft.com/fwlink/?LinkId=526863) cmdlet. Det här kommandot visar alla moduler som du har i systemet som har installerats direkt från PowerShell-galleriet.

På samma sätt för att ta reda på vilka skript som du har installerat från PowerShell-galleriet kan köra den [Get-InstalledScript](https://go.microsoft.com/fwlink/?LinkId=619790) cmdlet. Det här kommandot listar alla skript som du har i systemet som har installerats direkt från PowerShell-galleriet.