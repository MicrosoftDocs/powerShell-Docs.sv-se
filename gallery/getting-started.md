---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Kom igång med PowerShell-galleriet
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523067"
---
# <a name="get-started-with-the-powershell-gallery"></a>Kom igång med PowerShell-galleriet

Det korrekta sättet att installera objekt från PowerShell-galleriet är att använda cmdletarna i den [PowerShellGet](/powershell/module/powershellget) modulen. Du behöver inte logga in att ladda ned objekt från PowerShell-galleriet.

> [!NOTE]
> Det är möjligt att ladda ned ett paket från PowerShell-galleriet direkt, men detta är inte en rekommenderad metod. Mer information finns i [manuell paketet hämta](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).  


## <a name="discovering-items-from-the-powershell-gallery"></a>Identifierar objekt från PowerShell-galleriet

Du kan hitta dem i PowerShell-galleriet med hjälp av den **Search** kontroll på den här webbplatsen, eller genom att bläddra igenom sidorna moduler och skript. Du kan också hitta objekt från PowerShell-galleriet genom att köra den [Find-Module][] och [Find-Script][] cmdlet: ar, beroende på vilken objekt med `-Repository PSGallery`.

Filtrerar resultaten från galleriet kan du göra detta med hjälp av följande parametrar:

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

Om du bara vill identifiera specifika DSC-resurser i galleriet, du kan köra den [Sök-DscResource] cmdlet. Sök-DscResource returnerar data på DSC-resurser som ingår i galleriet.
Eftersom DSC-resurser levereras alltid som en del av en modul, du fortfarande behöver köra [Install-Module][] att installera dessa DSC-resurser.

## <a name="learning-about-items-in-the-powershell-gallery"></a>Lära dig mer om objekten i PowerShell-galleriet

När du har identifierat ett objekt som du är intresserad av kan du lära dig mer om den. Du kan göra detta genom att undersöka det objektet specifik sida i galleriet. På sidan, kommer du att kunna se alla metadata som har överförts med objektet. Dessa metadata om ett objekt som tillhandahålls av objektets författare och verifieras inte av Microsoft. Ägaren av objektet tätt kopplade alltså till galleriet-kontot som används för att publicera objektet och är mer tillförlitlig än fältet Författare.

Om du upptäcker ett objekt som du anser inte har publicerats i god tro klickar du på **Rapportera missbruk** på sidan för det objektet.

Om du kör [Find-Module][] eller [Find-Script][], du kan visa dessa data i det returnerade PSGetModuleInfo-objektet. Till exempel köra `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
Returnerar data i modulen PSReadLine i galleriet.

## <a name="downloading-items-from-the-powershell-gallery"></a>Ladda ned objekt från PowerShell-galleriet

Vi rekommenderar följande process när du hämtar objekt från PowerShell-galleriet:

### <a name="inspect"></a>Granska

För att hämta ett objekt från galleriet för granskning, kör du antingen den [Save-Module][] eller [Save-Script][] cmdlet, beroende på vilken typ av objekt. På så sätt kan du spara objektet lokalt utan att installera den och kontrollerar du innehållet i objektet. Kom ihåg att ta bort det sparade objektet manuellt.

Några av de här objekten har skapats av Microsoft och andra skapats av PowerShell-communityn.
Microsoft rekommenderar att du läser igenom innehållet och koden för objekt i det här galleriet före installationen.

Om du upptäcker ett objekt som du anser inte har publicerats i god tro klickar du på **Rapportera missbruk** på sidan för det objektet.

### <a name="install"></a>Installera

Om du vill installera ett objekt från galleriet för användning, kör du antingen den [Install-Module][] eller [Install-Script][] cmdlet, beroende på vilken typ av objekt.

[Install-Module][] installerar modulen till `$env:ProgramFiles\WindowsPowerShell\Modules` som standard.
Detta kräver ett administratörskonto. Om du lägger till den `-Scope CurrentUser` parametern modulen installeras på `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Install-Script][] installerar skriptet till `$env:ProgramFiles\WindowsPowerShell\Scripts` som standard.
Detta kräver ett administratörskonto. Om du lägger till den `-Scope CurrentUser` parametern skriptet installeras på `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Som standard [Install-Module][] och [Install-Script][] installerar den senaste versionen av ett objekt.
Installera en äldre version av objektet lägger till den `-RequiredVersion` parametern.

### <a name="deploy"></a>Distribuera

Om du vill distribuera ett objekt från PowerShell-galleriet i Azure Automation, klickar du på **distribuera till Azure Automation** på informationssidan för objektet. Du omdirigeras till Azure-hanteringsportalen där du loggar in med dina autentiseringsuppgifter för Azure-konto. Observera att distribuera objekt med beroenden distribuerar alla beroenden till Azure Automation. Knappen ”distribuera till Azure Automation-kan inaktiveras genom att lägga till den **AzureAutomationNotSupported** tagg till din objektmetadata.

Läs mer om Azure Automation i den [Azure Automation](/azure/automation) dokumentation.

## <a name="updating-items-from-the-powershell-gallery"></a>Uppdaterar objekt från PowerShell-galleriet

Kör den [Update-Module] [-] eller [Uppdateringsskriptet] [] cmdlet för att uppdatera objekt som installeras från PowerShell-galleriet. När du kör utan ytterligare parametrar, [Update-Module] [] försöker uppdatera varje modul som har installerats genom att köra [Install-Module][]. För att selektivt uppdatera moduler, lägger du till den `-Name` parametern.

På samma sätt när kör utan ytterligare parametrar, [Uppdateringsskriptet] [-] också försöker uppdatera varje skript som har installerats genom att köra [Install-Script][]. För att selektivt uppdatera skript, lägger du till den `-Name` parametern.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Listobjekt som du har installerat från PowerShell-galleriet

Om du vill ta reda på vilka moduler som du har installerat från PowerShell-galleriet kan du köra den [Get-InstalledModule][] cmdlet. Det här kommandot visar alla moduler som du har på datorn som har installerats direkt från PowerShell-galleriet.

På samma sätt för att ta reda på vilka skript som du har installerat från PowerShell-galleriet kan köra den [Get-InstalledScript][] cmdlet. Det här kommandot visar alla skript som du har på datorn som har installerats direkt från PowerShell-galleriet.

[Sök-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script