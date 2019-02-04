---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Kom igång med PowerShell-galleriet
ms.openlocfilehash: c8beba3009e462ce52cdecd34fc0313d9234f289
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688849"
---
# <a name="getting-started-with-the-powershell-gallery"></a>Komma igång med PowerShell-galleriet

PowerShell-galleriet är en paketdatabas som innehåller skript, moduler och du kan hämta och använda DSC-resurser. Du använder cmdlets i den [PowerShellGet](/powershell/module/powershellget) modul för att installera paket från PowerShell-galleriet. Du behöver inte logga in att ladda ned objekt från PowerShell-galleriet.

> [!NOTE]
> Det är möjligt att ladda ned ett paket från PowerShell-galleriet direkt, men detta är inte en rekommenderad metod.
> Mer information finns i [manuell paketet hämta](/powershell/gallery/how-to/working-with-packages/manual-download).

## <a name="discovering-packages-from-the-powershell-gallery"></a>Identifiering av paket från PowerShell-galleriet

Du kan hitta paket i PowerShell-galleriet med hjälp av den **Search** kontrollen i PowerShell-galleriet [startsida](https://www.powershellgallery.com), eller genom att gå igenom de moduler och skript från den [paket sidan ](https://www.powershellgallery.com/packages). Du kan också hitta paket från PowerShell-galleriet genom att köra den [Find-Module][], [Find-DscResource], och [Find-Script][] cmdlet: ar, beroende på typen package med `-Repository PSGallery`.

Du kan filtrera resultaten från galleriet med hjälp av följande parametrar:

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

Om du bara vill identifiera specifika DSC-resurser i galleriet, du kan köra den [Find-DscResource] cmdlet. Sök-DscResource returnerar data på DSC-resurser som ingår i galleriet.
Eftersom DSC-resurser levereras alltid som en del av en modul, du fortfarande behöver köra [Install-Module][] att installera dessa DSC-resurser.

## <a name="learning-about-packages-in-the-powershell-gallery"></a>Lära dig mer om paketen i PowerShell-galleriet

När du har identifierat ett paket som du är intresserad av kan du lära dig mer om den. Du kan göra detta genom att undersöka det paketet specifik sida i galleriet. På sidan, kommer du att kunna se alla metadata som har överförts med paketet. Dessa metadata kommer från paketets författare och verifieras inte av Microsoft. Ägaren av paketet är alltså tätt kopplade till kontot galleriet som används för att publicera paketet och är mer tillförlitlig än fältet Författare.

Om du upptäcker ett paket som du anser inte har publicerats i god tro klickar du på **Rapportera missbruk** på sidan för det paketet.

Om du kör [Find-Module][] eller [Find-Script][], du kan visa dessa data i det returnerade PSGetModuleInfo-objektet. Till exempel köra `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
Returnerar data i modulen PSReadLine i galleriet.

## <a name="downloading-packages-from-the-powershell-gallery"></a>Ladda ned paket från PowerShell-galleriet

Vi rekommenderar följande process när du laddar ned paket från PowerShell-galleriet:

### <a name="inspect"></a>Granska

Om du vill ladda ned ett paket från galleriet för granskning, kör du antingen den [Save-Module][] eller [Save-Script][] cmdlet, beroende på typen av paketet. På så sätt kan du spara paketet lokalt utan att installera den och granska paketinnehållet. Kom ihåg att ta bort det sparade paketet manuellt.

Vissa av dessa paket skapats av Microsoft och andra skapats av PowerShell-communityn.
Microsoft rekommenderar att du läser igenom innehållet och koden för paket på det här galleriet före installationen.

Om du upptäcker ett paket som du anser inte har publicerats i god tro klickar du på **Rapportera missbruk** på sidan för det paketet.

### <a name="install"></a>Installera

Om du vill installera ett paket från galleriet för användning, kör du antingen den [Install-Module][] eller [Install-Script][] cmdlet, beroende på typen av paketet.

[Install-Module][] installerar modulen till `$env:ProgramFiles\WindowsPowerShell\Modules` som standard.
Detta kräver ett administratörskonto. Om du lägger till den `-Scope CurrentUser` parametern modulen installeras på `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Install-Script][] installerar skriptet till `$env:ProgramFiles\WindowsPowerShell\Scripts` som standard.
Detta kräver ett administratörskonto. Om du lägger till den `-Scope CurrentUser` parametern skriptet installeras på `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Som standard [Install-Module][] och [Install-Script][] installerar den senaste versionen av ett paket.
Installera en äldre version av paketet lägger till den `-RequiredVersion` parametern.

### <a name="deploy"></a>Distribuera

Om du vill distribuera ett paket från PowerShell-galleriet i Azure Automation, klickar du på **Azure Automation**, klicka sedan på **distribuera till Azure Automation** på sidan med paketet. Du omdirigeras till Azure-hanteringsportalen där du loggar in med dina autentiseringsuppgifter för Azure-konto. Observera att distribuera paket med beroenden distribuerar alla beroenden till Azure Automation. Knappen ”distribuera till Azure Automation-kan inaktiveras genom att lägga till den **AzureAutomationNotSupported** tagg till din paketmetadata.

Läs mer om Azure Automation i den [Azure Automation](/azure/automation) dokumentation.

## <a name="updating-packages-from-the-powershell-gallery"></a>Uppdaterar paket från PowerShell-galleriet

Om du vill uppdatera paket som installeras från PowerShell-galleriet, kör du antingen [Update-Module] [-] eller [Uppdateringsskriptet] [] cmdlet. När du kör utan ytterligare parametrar, [Update-Module] [] försöker uppdatera alla moduler som har installerats genom att köra [Install-Module][]. För att selektivt uppdatera moduler, lägger du till den `-Name` parametern. 

På samma sätt när kör utan ytterligare parametrar, [Uppdateringsskriptet] [-] också försöker uppdatera alla skript som har installerats genom att köra [Install-Script][]. För att selektivt uppdatera skript, lägger du till den `-Name` parametern.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>Lista över paket som du har installerat från PowerShell-galleriet

Om du vill ta reda på vilka moduler som du har installerat från PowerShell-galleriet kan du köra den [Get-InstalledModule][] cmdlet. Det här kommandot visar alla moduler som du har på datorn som har installerats direkt från PowerShell-galleriet.

På samma sätt för att ta reda på vilka skript som du har installerat från PowerShell-galleriet kan köra den [Get-InstalledScript][] cmdlet. Det här kommandot visar alla skript som du har på datorn som har installerats direkt från PowerShell-galleriet.

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
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
