---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Kom igång med PowerShell-galleriet
ms.openlocfilehash: 83974698152e75efac66ea725a9c220486676d6f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190170"
---
# <a name="get-started-with-the-powershell-gallery"></a>Kom igång med PowerShell-galleriet

Hämtar objekt från PowerShell-galleriet till systemet kräver den [PowerShellGet](/powershell/module/powershellget) modul. Modulen PowerShellGet hittar du i något av följande. Du behöver inte logga in kan du hämta från PowerShell-galleriet.

## <a name="discovering-items-from-the-powershell-gallery"></a>Identifiering av objekt från PowerShell-galleriet

Du hittar objekt i PowerShell-galleriet med hjälp av den **Sök** kontroll på den här webbplatsen, eller genom att gå igenom sidorna moduler och skript. Du kan också hitta objekt från PowerShell-galleriet genom att köra den [hitta modulen][] och [hitta skriptet][] cmdlets, beroende på vilken objektet med `-Repository PSGallery`.

Filtrerar resultaten från galleriet kan göras med hjälp av följande parametrar:

- Namn
- Allaversioner
- MinimumVersion
- RequiredVersion
- Tagg
- Innehåller
- DscResource
- RoleCapability
- Kommando
- Filter

Om du bara är intresserad av att identifiera specifika DSC-resurser i galleriet, kan du köra den [hitta DscResource] cmdlet. Hitta DscResource returnerar data på DSC-resurser som ingår i galleriet.
Eftersom DSC resurser levereras alltid som en del av en modul, du fortfarande behöver köra [installera modulen][] att installera de DSC-resurserna.

## <a name="learning-about-items-in-the-powershell-gallery"></a>Lär dig hur objekten i PowerShell-galleriet

När du har hittat ett objekt som du är intresserad kan du vill veta mer om den. Du kan göra detta genom att undersöka artikelns viss sida i galleriet. På sidan, kommer du att kunna se alla metadata tillsammans med objektet. Dessa metadata för en artikel tillhandahålls av objektets författare och verifieras inte av Microsoft. Ägaren av det kopplat starkt till Gallery-kontot som används för att publicera artikeln och är mer tillförlitlig än fältet Författare.

Om du upptäcker ett objekt som du inte har publicerats i god tro klickar du på **Rapportera missbruk** på sidan för att objektet.

Om du kör [hitta modulen][] eller [hitta skriptet][], du kan visa informationen i det returnerade PSGetModuleInfo-objektet. Till exempel köra `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` returnerar data i modulen PSReadLine i galleriet.

## <a name="downloading-items-from-the-powershell-gallery"></a>Ladda ned objekt från PowerShell-galleriet

Vi rekommenderar följande process när du hämtar objekt från PowerShell-galleriet:

### <a name="inspect"></a>Inspektera

Om du vill ladda ned ett objekt från galleriet för inspektion, kör du antingen den [spara modulen][] eller [spara skriptet][] cmdlet, beroende på vilken typ av objekt. På så sätt kan du spara objektet lokalt utan att installera den och kontrollerar du innehållet för objektet. Kom ihåg att ta bort det sparade objektet manuellt.

Vissa av dessa element skapats av Microsoft och andra skapats av PowerShell-communityn.
Microsoft rekommenderar att du läser innehåll och kod för artiklar i det här galleriet före installationen.

Om du upptäcker ett objekt som du inte har publicerats i god tro klickar du på **Rapportera missbruk** på sidan för att objektet.

### <a name="install"></a>Installera

Installera ett objekt från galleriet för att köra antingen den [installera modulen][] eller [installationsskriptet][] cmdlet, beroende på vilken typ av objekt.

[installera modulen][] installerar modulen `$env:ProgramFiles\WindowsPowerShell\Modules` som standard.
Detta kräver att ett administratörskonto. Om du lägger till den `-Scope CurrentUser` parametern modulen är installerad så att `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[installationsskriptet][] installerar skriptet till `$env:ProgramFiles\WindowsPowerShell\Scripts` som standard.
Detta kräver att ett administratörskonto. Om du lägger till den `-Scope CurrentUser` parametern skriptet installeras på `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Som standard [installera modulen][] och [installationsskriptet][] installerar den senaste versionen av ett objekt.
Installera en äldre version av objektet genom att lägga till den `-RequiredVersion` parameter.

### <a name="deploy"></a>Distribuera

Om du vill distribuera ett objekt från PowerShell-galleriet till Azure Automation klickar du på **till Azure Automation** på informationssidan för objektet. Du omdirigeras till Azure-hanteringsportalen där du loggar in med dina Azure-autentiseringsuppgifter. Observera att distribuera objekt med beroenden distribuerar alla beroenden till Azure Automation. Knappen ”distribuera till Azure Automation-kan inaktiveras genom att lägga till den **AzureAutomationNotSupported** så att dina objektmetadata.

Läs mer om Azure Automation i den [Azure Automation](/azure/automation) dokumentation.

## <a name="updating-items-from-the-powershell-gallery"></a>Uppdaterar objekt från PowerShell-galleriet

Kör den [uppdatering modul] [] eller [Uppdateringsskriptet] [] cmdlet för att uppdatera objekt från PowerShell-galleriet. När du kör utan ytterligare parametrar [uppdatering modul] [] försöker uppdatera varje modul som har installerats genom att köra [installera modulen][]. Uppdatera selektivt moduler genom att lägga till den `-Name` parameter.

På liknande sätt, när du kör utan ytterligare parametrar [Uppdateringsskriptet] [] också försöker uppdatera varje skript installerat genom att köra [installationsskriptet][]. Uppdatera selektivt skript genom att lägga till den `-Name` parameter.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Lista över artiklar som du har installerat från PowerShell-galleriet

Om du vill ta reda på vilka moduler som du har installerat från PowerShell-galleriet kan köra den [Get-InstalledModule][] cmdlet. Det här kommandot visar alla moduler som du har i systemet som har installerats direkt från PowerShell-galleriet.

På samma sätt för att ta reda på vilka skript som du har installerat från PowerShell-galleriet kan köra den [Get-InstalledScript][] cmdlet. Det här kommandot listar alla skript som du har i systemet som har installerats direkt från PowerShell-galleriet.

[hitta DscResource]: /powershell/module/powershellget/Find-DscResource
[hitta modulen]: /powershell/module/powershellget/Find-Module
[hitta skriptet]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[installera modulen]: /powershell/module/powershellget/Install-Module
[installationsskriptet]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[spara modulen]: /powershell/module/powershellget/Save-Module
[spara skriptet]: /powershell/module/powershellget/Save-Script