---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Paket manifest värden som påverkar PowerShell-galleriet gränssnittet
ms.openlocfilehash: d5e0b85a635c4090f8ccb814277a1a6dd6a951e2
ms.sourcegitcommit: 1695df0d241c0390cac71a7401e61198fc6ff756
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/06/2020
ms.locfileid: "91772311"
---
# <a name="package-manifest-values-that-impact-the-powershell-gallery-ui"></a>Paket manifest värden som påverkar PowerShell-galleriet gränssnittet

Det här avsnittet innehåller information om hur du ändrar manifestet för sina PowerShell-galleriets publikationer så att funktionerna i PowerShellGet-cmdletar och PowerShell-galleriet användar gränssnittet påverkas. Det här innehållet är ordnat efter var ändringen visas, från och med mitten och sedan navigerings området till vänster. Det finns ett informations avsnitt som täcker taggar, som identifierar viktiga taggar, samt några av de ofta använda taggarna. Det finns två avsnitt som innehåller exempel på manifest:

- För moduler, se [manifest för uppdaterings modul](/powershell/module/powershellget/Update-ModuleManifest)
- För skript, se [skapa skript fil med metadata](/powershell/module/powershellget/New-ScriptFileInfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>PowerShell-galleriet funktions element som styrs av manifestet

Tabellen nedan visar elementen i gränssnittet för PowerShell-galleriet paket sidan som styrs av utgivaren. Varje objekt anger om det kan styras av modulen eller skript manifestet.

| UI-element | Beskrivning | Modul | Skript |
| --- | --- | --- | --- |
| **Rubrik** | Detta är namnet på det paket som har publicerats i galleriet  | Inga | Inga |
| **Version** | Den version som visas är versions strängen i metadata och en för hands version om har angetts. Den primära delen av versionen i ett modul manifest är ModuleVersion. För ett skript identifieras det som. 2.0.1. Om en för hands versions sträng anges läggs den till i ModuleVersion för moduler eller anges som en del av. VERSION för skript. Det finns dokumentation för att ange för hands versions strängar i [moduler](module-prerelease-support.md)och i [skript](script-prerelease-support.md) | Ja | Ja |
| **Beskrivning** | Detta är beskrivningen i modulens manifest och i en skript fil manifestet. BETECKNING | Ja | Ja |
| **Kräv godkännande av licens** | En modul kan kräva att användaren accepterar en licens genom att ändra modul manifestet med RequireLicenseAcceptance = $true, tillhandahålla en LicenseURI och tillhandahålla en license.txt fil i roten i mappen module. Ytterligare information finns i avsnittet [Kräv godkännande av licens](../how-to/working-with-packages/packages-that-require-license-acceptance.md) . | Ja | Inga |
| **Versionsanmärkningar** | För moduler hämtas den här informationen från avsnittet ReleaseNotes under PSData\PrivateData. I skript manifest är det. RELEASENOTES-element. | Ja | Ja |
| **Ägare** | Ägare är en lista över användare i PowerShell-galleriet som kan uppdatera ett paket. Ägar listan ingår inte i paket manifestet. I ytterligare dokumentation beskrivs hur du [hanterar objekt ägare](../how-to/publishing-packages/managing-package-owners.md). | Inga | Inga |
| **Författare** | Detta ingår i modulen manifest som författare och i ett skript manifest som. Skriver. Författar fältet används ofta för att ange ett företag eller en organisation som är associerad med ett paket. | Ja | Ja |
| **Material** | Detta är upphovs rätts fältet i manifestet för modulen och. COPYRIGHT i ett skript manifest. | Ja | Ja |
| **FileList** | Fil listan hämtas från paketet när den publiceras till PowerShell-galleriet. Det går inte att kontrol lera manifest informationen. Obs! det finns en ytterligare. nuspec-fil som listas med varje paket i PowerShell-galleriet som inte finns när du har installerat paketet på ett system. Det här är manifestet för NuGet-paketet för paketet och kan ignoreras. | Inga | Inga |
| **Taggar** | För moduler ingår Taggar under PSData\PrivateData. Avsnittet är märkt för skript. Taggen. Observera att Taggar inte får innehålla blank steg, även om de är inom citat tecken. Taggar har ytterligare krav och betydelser, som beskrivs senare i det här avsnittet i avsnittet märkes information. | Ja | Ja |
| **Cmdletar** | Detta finns i modulen manifest med hjälp av CmdletsToExport. Observera att det bästa tillvägagångs sättet är att uttryckligen lista objekten i stället för att använda jokertecknet "*", eftersom det förbättrar belastnings-modulens prestanda för användare. | Ja | Inga |
| **Funktioner** | Detta finns i modulen manifest med hjälp av FunctionsToExport. Observera att det bästa tillvägagångs sättet är att uttryckligen lista objekten i stället för att använda jokertecknet "*", eftersom det förbättrar belastnings-modulens prestanda för användare. | Ja | Inga |
| **DSC-resurser** | För moduler som ska användas i PowerShell version 5,0 och senare finns detta i manifestet med hjälp av DscResourcesToExport. Om modulen ska användas i PowerShell 4 ska DSCResourcesToExport inte användas eftersom den inte är en manifest nyckel som stöds. (DSC var inte tillgängligt före PowerShell 4.) | Ja | Inga |
| **Arbetsflöden** | Arbets flöden publiceras till PowerShell-galleriet som skript och identifieras som arbets flöden (se [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) för ett exempel) i koden. Detta styrs inte av manifestet. | Inga | Inga |
| **Roll funktioner** | Detta visas när modulen som publiceras i PowerShell-galleriet innehåller en eller flera roll kapacitets-filer (. psrc) som används av JEA. Mer information om [roll funktioner](/powershell/scripting/learn/remoting/jea/role-capabilities)finns i Jea-dokumentationen. | Ja | Inga |
| **PowerShell-utgåvor** | Detta anges i ett skript eller modul manifest. För moduler som har utformats för att användas med PowerShell 5,0 och tidigare styrs detta med hjälp av taggar. För skriv bord använder du taggen PSEdition_Desktop och för kärna använder du taggen PSEdition_Core. För moduler som endast ska användas på PowerShell 5,1 och senare finns det en CompatiblePSEditions nyckel i huvud manifestet. Mer information finns i PS Edition-funktionen i [Hämta dokumentation för PowerShell](module-psedition-support.md). | Ja | Ja |
| **Beroenden** | Beroenden är moduler i PowerShell-galleriet som har deklarerats i modulen som RequiredModules eller i skript manifestet som #Requires – modul (namn). | Ja | Ja |
| **Lägsta PowerShell-version** | Detta kan anges i ett modul manifest som PowerShellVersion | Ja | Inga |
| **Versions historik** | Versions historiken visar de uppdateringar som gjorts i en modul i PowerShell-galleriet. Om en version av ett paket är dold med funktionen Ta bort kommer den inte att visas i versions historiken, förutom paketets ägare. | Inga | Inga |
| **Projekt webbplats** | Projekt webbplatsen tillhandahålls för moduler i avsnittet Privatedata\PSData i modulen manifest genom att ange en ProjectURI. I skript manifestet styrs det genom att ange. PROJECTURI. | Ja | Ja |
| **Licens** | En licens länk tillhandahålls för moduler i avsnittet Privatedata\PSData i modulen manifest genom att ange en LicenseURI. I skript manifestet styrs det genom att ange. LICENSEURI. Det är viktigt att Observera att om en licens inte tillhandahålls via LicenseURI, eller i en modul, anger användnings villkoren för det PowerShell-galleriet anger användnings villkoren för paketet. Se användnings villkoren för mer information. | Ja | Ja |
| **Ikon** | En ikon kan anges för alla paket i PowerShell-galleriet genom att tillhandahålla flaggan IconURI i skript manifestet eller i avsnittet Privatedata-PSData i modulen manifest. IconURI ska peka på en 85x85-bild med genomskinlig bakgrund. URI: n **måste** vara en URL för direkt avbildning och **får inte** gå till en webb sida som innehåller bilden, eller en fil i PowerShell-galleriet paketet. | Ja | Ja |

## <a name="editing-package-details"></a>Redigera paket information

På sidan PowerShell-galleriet redigera paket kan utgivare ändra flera av de fält som visas för ett paket, särskilt:

- Rubrik
- Beskrivning
- Sammanfattning
- Ikon-URL
- URL för projektets start sida
- Författare
- Copyright
- Taggar
- Viktig information
- Kräv licens

Den här metoden rekommenderas vanligt vis inte, förutom vid behov för att korrigera vad som visas för en äldre version av en modul. Användare som hämtar modulen kommer att se att metadata inte stämmer överens med vad som visas i PowerShell-galleriet, vilket leder till problem med paketet. Detta leder ofta till att förfrågningar skickas till paketets ägare för att bekräfta ändringen. Vi rekommenderar starkt att varje gång den här metoden används, så bör en ny version av paketet publiceras med samma ändringar.

## <a name="tag-details"></a>Märkes information

Taggar är enkla strängar som användare använder för att hitta paket. Taggar är mest värdefulla när de används konsekvent över många paket som är relaterade till samma ämne. Att använda flera varianter av samma ord (till exempel databas och databaser eller test och testning) ger vanligt vis lite nytta. Taggar är Skift läges känsliga strängar med enstaka ord och får inte innehålla blank steg. Om det finns en fras som du tror att användarna kommer att söka efter, lägger du till den i paket beskrivningen och den kommer att finnas i Sök resultaten. Använd Pascal-höljen, bindestreck, under streck eller punkt om du försöker förbättra läsbarheten.
Var försiktig med att skapa långa, komplexa och ovanliga Taggar eftersom de ofta är felstavade.

Det finns taggar som är viktiga att notera, eftersom PowerShell-galleriet-och PowerShellGet-cmdletarna behandlar dem unikt. PSEdition_Desktop och PSEdition_Core är de olika exemplen och beskrivs ovan.

Som anges ovan ger Taggar det mest aktuella värdet när de är speciella och används konsekvent över många paket. Som utgivare försöker hitta de bästa taggarna som ska användas är den enklaste metoden att söka i PowerShell-galleriet efter taggar som du överväger. Vi rekommenderar att det finns många paket som returneras och att paket beskrivningarna anpassas efter din användning av nyckel ordet.

Här följer några av de vanligaste taggarna från 12/14/2017 för referens. I vissa fall finns det liknande men kanske mindre idealiska alternativ som visas bredvid taggen. Det är bäst att använda den önskade taggen, eftersom det leder till mindre brus och bättre Sök Resultat för konsumenterna.

| Önskad tagg | Alternativ och anteckningar |
| --- | --- |
| Azure |  |
| DSC | DesiredStateConfiguration är mindre önskvärt, den är för lång |
| ResourceManager | ARM används för att beskriva en grupp processorer och ska inte användas för Azure Resource Manager |
| DSCResourceKit |  |
| SQL |  |
| AWS |  |
| Dscresource Keyword Supports |  |
| Automation |  |
| REST |  |
| ActiveDirectory | AD används för närvarande inte av sig själv  |
| SQLServer |  |
| DBA |  |
| Säkerhet | Försvaret är mindre exakt |
| Databas | Databaserna (plural) är mindre önskvärda |
| DevOps |  |
| Windows |  |
| Skapa |  |
| Distribution | Distributionen används något mindre ofta |
| Moln |  |
| GIT |  |
| Testa | Testning är mindre önskvärt |
| VersionControl | Versionen är mindre exakt, även om den används oftare  |
| Loggning | Prioriterad användning av loggning som åtgärd |
| Logga | Prioriterad användning av loggen som en sak |
| Backup |  |
| IaaS |  |
| Linux |  |
| IIS |  |
| AzureAutomation |  |
| Storage |  |
| GitHub |  |
| Json |  |
| Exchange |  |
| Nätverk | Nätverk liknar varandra, används mindre ofta |
| SharePoint |  |
| Rapportering | Rapportering är en åtgärd, men rapporten är en sak |
| Rapport | Rapporten är en sak |
| WinRM |  |
| Övervakning |  |
| VSTS |  |
| Excel |  |
| Google |  |
| Färg |  |
| DNS |  |
| Office365 | Stavnings kontroll av Office är bättre. O365 används mindre ofta, även om det är kortare |
| Gitlab |  |
| Pester |  |
| AzureAD |  |
| HTML |  |
| Hyper-V | HyperV är mindre vanligt som en tagg |
| Konfiguration |  |
| ChatOps |  |
| PackageManagement |  |
| WMI |  |
| Brandvägg |  |
| Docker |  |
| Appveyor |  |
| AzureRm | Används främst för AzureRM-moduler |
| Zip |  |
| MSI |  |
| MacOS |  |
| PoshBot |  |
