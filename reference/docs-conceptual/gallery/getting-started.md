---
ms.date: 06/12/2017
title: Kom igång med PowerShell-galleriet
description: Den här artikeln förklarar hur du kommer igång med PowerShell-galleriet och PowerShellGet-cmdletar
ms.openlocfilehash: a5045e4ecee2eb8bc9aa373a6b8ec3a940b4de33
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913293"
---
# <a name="getting-started-with-the-powershell-gallery"></a>Komma igång med PowerShell-galleriet

PowerShell-galleriet är en paket lagrings plats som innehåller skript, moduler och DSC-resurser som du kan hämta och utnyttja. Du kan använda cmdletarna i [PowerShellGet](/powershell/module/powershellget) -modulen för att installera paket från PowerShell-galleriet. Du behöver inte logga in för att ladda ned objekt från PowerShell-galleriet.

> [!NOTE]
> Det går att ladda ned ett paket från PowerShell-galleriet direkt, men detta är inte en rekommenderad metod. Mer information finns i [manuell paket hämtning](how-to/working-with-packages/manual-download.md).

## <a name="discovering-packages-from-the-powershell-gallery"></a>Identifiera paket från PowerShell-galleriet

Du kan hitta paket i PowerShell-galleriet med hjälp av **Sök** kontrollen på [start sidan](https://www.powershellgallery.com)för PowerShell-galleriet eller genom att bläddra bland modulerna och skripten på [sidan paket](https://www.powershellgallery.com/packages). Du kan också hitta paket från PowerShell-galleriet genom att köra cmdletarna [find-module][], [find-dscresource Keyword Supports]och [find-script][] , beroende på paket typen, med `-Repository PSGallery` .

Du kan filtrera resultat från galleriet med hjälp av följande parametrar:

- Namn
- AllVersions
- MinimumVersion
- RequiredVersion
- Tagga
- Inkluderar
- Dscresource Keyword Supports
- RoleCapability
- Kommando
- Filtrera

Om du bara är intresse rad av att identifiera vissa DSC-resurser i galleriet kan du köra cmdleten [find-dscresource Keyword Supports][] . Find-DscResource returnerar data på DSC-resurser som finns i galleriet. Eftersom DSC-resurser alltid levereras som en del av en modul, behöver du fortfarande köra [install-module][] för att installera dessa DSC-resurser.

## <a name="learning-about-packages-in-the-powershell-gallery"></a>Lär dig om paket i PowerShell-galleriet

När du har identifierat ett paket som du är intresse rad av kanske du vill veta mer om det. Det kan du göra genom att undersöka Paketets aktuella sida i galleriet. På den sidan kan du se alla metadata som har laddats upp med paketet. Dessa metadata tillhandahålls av paketets författare och verifieras inte av Microsoft. Paketets ägare är starkt bunden till Galleri kontot som används för att publicera paketet och är mer tillförlitligt än fältet författare.

Om du upptäcker ett paket som du tycker att du inte har publicerat i en godkänd tro klickar du på **rapportera missbruk** på paketets sida.

Om du kör [find-module][] eller [find-script][]kan du visa dessa data i det returnerade PSGetModuleInfo-objektet. Att köra returnerar till exempel `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` data i PSReadLine-modulen i galleriet.

## <a name="downloading-packages-from-the-powershell-gallery"></a>Hämta paket från PowerShell-galleriet

Vi uppmuntrar följande process när du laddar ned paket från PowerShell-galleriet:

### <a name="inspect"></a>Allmänt

Om du vill ladda ned ett paket från galleriet för granskning kör du antingen cmdleten [Save-module][] eller [Save-script][] , beroende på paket typen. På så sätt kan du spara paketet lokalt utan att installera det och granska paket innehållet. Kom ihåg att ta bort det sparade paketet manuellt.

Några av de här paketen har skapats av Microsoft och andra har skapats av PowerShell-communityn. Microsoft rekommenderar att du granskar innehållet och koden i paketen i det här galleriet före installationen.

Om du upptäcker ett paket som du tycker att du inte har publicerat i en godkänd tro klickar du på **rapportera missbruk** på paketets sida.

### <a name="install"></a>Installera

Om du vill installera ett paket från galleriet för användning kör du antingen cmdleten [install-module][] eller [install-script][] , beroende på typ av paket.

[Installera-modulen][] installerar modulen som `$env:ProgramFiles\WindowsPowerShell\Modules` standard.
Detta kräver ett administratörs konto. Om du lägger till `-Scope CurrentUser` parametern installeras modulen till `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Install-script][] installerar skriptet till `$env:ProgramFiles\WindowsPowerShell\Scripts` som standard.
Detta kräver ett administratörs konto. Om du lägger till `-Scope CurrentUser` parametern installeras skriptet till `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Som standard installerar [install-module][] och [install-script][] den senaste versionen av ett paket. Lägg till parametern om du vill installera en äldre version av paketet `-RequiredVersion` .

### <a name="deploy"></a>Distribuera

Om du vill distribuera ett paket från PowerShell-galleriet till Azure Automation klickar du på **Azure Automation** och klickar sedan på **distribuera till Azure Automation** på paket informations sidan. Du omdirigeras till Azure-Hanteringsportal där du loggar in med dina autentiseringsuppgifter för Azure-kontot. Observera att distribution av paket med beroenden distribuerar alla beroenden till Azure Automation. Knappen distribuera till Azure Automation kan inaktive ras genom att **AzureAutomationNotSupported** -taggen läggs till i paketets metadata.

Mer information om Azure Automation finns i [Azure Automation](/azure/automation) -dokumentationen.

## <a name="updating-packages-from-the-powershell-gallery"></a>Uppdaterar paket från PowerShell-galleriet

Om du vill uppdatera paket som är installerade från PowerShell-galleriet kör du antingen cmdleten [Update-module][] eller [Update-script][] . Om du kör utan ytterligare parametrar försöker [Update-module][] uppdatera alla moduler som installerats genom att köra [install-module][]. Om du vill uppdatera moduler selektivt lägger du till `-Name` parametern.

Vid körning utan ytterligare parametrar försöker [Update-script][] också uppdatera alla skript som installeras genom att köra [install-script][]. Om du vill uppdatera skript selektivt lägger du till `-Name` parametern.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>List paket som du har installerat från PowerShell-galleriet

Om du vill ta reda på vilka moduler som du har installerat från PowerShell-galleriet kör du cmdleten [Get-InstalledModule][] . Detta kommando visar alla moduler som finns på ditt system som har installerats direkt från PowerShell-galleriet.

Om du vill ta reda på vilka skript som du har installerat från PowerShell-galleriet kör du cmdleten [Get-InstalledScript][] . Det här kommandot visar alla skript som finns på ditt system som installerades direkt från PowerShell-galleriet.

## <a name="network-access-to-the-powershell-gallery"></a>Nätverks åtkomst till PowerShell-galleriet

PowerShell-galleriet använder följande värdnamn.

- `psg-prod-eastus.azureedge.net` -CDN-värdnamn
- `az818661.vo.msecnd.net` -CDN-värdnamn
- `devopsgallerystorage.blob.core.windows.net` -lagrings kontots värdnamn
- `*.powershellgallery.com` – webbplats
- `go.microsoft.com` – omdirigerings tjänst

Dessa värdnamn ska läggas till i listan över tillåtna som styr åtkomst från nätverket.

[!INCLUDE [TLS 1.2 Requirement](../../includes/tls-gallery.md)]

[Find-Dscresource Keyword Supports]: /powershell/module/powershellget/Find-DscResource
[Sök-modul]: /powershell/module/powershellget/Find-Module
[Sök – skript]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Installera-modul]: /powershell/module/powershellget/Install-Module
[Installera – skript]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Spara-modul]: /powershell/module/powershellget/Save-Module
[Spara – skript]: /powershell/module/powershellget/Save-Script
[Update-modul]: /powershell/module/powershellget/Update-Module
[Uppdatera skript]: /powershell/module/powershellget/Update-Script
