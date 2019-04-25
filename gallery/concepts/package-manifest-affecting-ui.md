---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Paketet manifest värden som påverkar PowerShell galleriets gränssnitt
ms.openlocfilehash: cedf81df8de29c54ef559a800d654305029491ec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084716"
---
# <a name="package-manifest-values-that-impact-the-powershell-gallery-ui"></a>Paketet manifest värden som påverkar PowerShell galleriets gränssnitt

Det här avsnittet innehåller utgivare med översiktlig information om hur du ändrar manifest för publikationer sina PowerShell-galleriet så att funktionerna i PowerShellGet-cmdletar och PowerShell-galleriet Användargränssnittet kommer att påverkas. Det här innehållet är ordnad efter där ändringen tillämpas, från med mitt i navigeringsområdet till vänster. Det finns en informationsavsnittet täckande taggar, som identifierar viktiga taggar, samt några av de vanligaste taggar. Det finns två avsnitt som innehåller manifestet exempel:

- Moduler, se [uppdatera modulen Manifest](/powershell/module/powershellget/Update-ModuleManifest)
- Skript, se [skapa skriptfil med Metadata](/powershell/module/powershellget/New-ScriptFileInfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>PowerShell-galleriet funktionselement som styrs av manifestet

Tabellen nedan visar elementen på sidan för PowerShell-galleriet paketet Användargränssnittet som styrs av utgivaren. Varje objekt innebär att om den kan styras av manifestet modulen eller skript.

| UI Element | Beskrivning | Modul | Skript |
| --- | --- | --- | --- |
| **Rubrik** | Det här är namnet på det paket som har publicerats i galleriet  | Nej | Nej |
| **Version** | Den version som visas är Versionsträngen i metadata och ett förhandsversioner om har angetts. Den primära delen av versionen i ett modulmanifest är ModuleVersion. För ett skript identifieras som. VERSION. Om en förhandsversion sträng anges ska det läggas till för ModuleVersion för moduler, eller angetts som en del av. VERSIONEN för skript. Det finns dokumentation för att ange förhandsversioner strängar i [moduler](module-prerelease-support.md), och i [skript](script-prerelease-support.md) | Ja | Ja |
| **Beskrivning** | Detta är beskrivningen i modulmanifestet och det är i ett manifest för skript-fil. BESKRIVNING | Ja | Ja |
| **Kräv godkännande av licensen** | En modul kan kräva att användaren måste godkänna en licens genom att ändra modulmanifestet med RequireLicenseAcceptance = $true, tillhandahåller en LicenseURI och ge en license.txt-filen i roten av modulmappen. Mer information finns i den [kräver godkännande av licensen](../how-to/working-with-packages/packages-that-require-license-acceptance.md) avsnittet. | Ja | Nej |
| **Versionsanmärkningar** | För moduler hämtas den här informationen från avsnittet ReleaseNotes under PSData\PrivateData. I skriptet manifest, är det den. RELEASENOTES element. | Ja | Ja |
| **Ägare** | Ägare är en lista över användare i PowerShell-galleriet som kan uppdatera ett paket. Listan ägare ingår inte i Paketmanifestet. Ytterligare dokumentation som beskriver hur du [hantera objektägare](../how-to/publishing-packages/managing-package-owners.md). | Nej | Nej |
| **Författare** | Det här är inkluderade i modulmanifestet som författare och i ett skript-manifest som. FÖRFATTARE. Fältet Författare används ofta för att ange ett företag eller organisation som är associerad med ett paket. | Ja | Ja |
| **Copyright** | Detta är Copyright-fält i modulmanifestet, och. COPYRIGHT i ett skript-manifest. | Ja | Ja |
| **FileList** | Fillistan ritas från paketet när den publiceras i PowerShell-galleriet. Det går inte att styra av manifest information. Obs: det finns en ytterligare .nuspec-fil som visas i listan med varje paket i PowerShell-galleriet som inte finns när du har installerat paketet på ett system. Detta är Paketmanifestet Nuget-paketet och kan ignoreras. | Nej | Nej |
| **Taggar** | För moduler ingår taggar under PSData\PrivateData. Avsnittet är märkt för skript. MED TAGGAR. Observera att taggar får inte innehålla blanksteg, även när de är inom citattecken. Taggar har ytterligare krav och betydelser som beskrivs senare i det här avsnittet i avsnittet tagginformation. | Ja | Ja |
| **Cmdletar** | Detta tillhandahålls i modulmanifestet med CmdletsToExport. Observera att den bästa metoden är att uttryckligen listobjekt i stället för med jokertecknet ”*”, enligt som förbättrar prestanda load-modulen för användare. | Ja | Nej |
| **Funktioner** | Detta tillhandahålls i modulmanifestet med FunctionsToExport. Observera att den bästa metoden är att uttryckligen listobjekt i stället för med jokertecknet ”*”, enligt som förbättrar prestanda load-modulen för användare. | Ja | Nej |
| **DSC-resurser** | Detta har angetts i manifestet DscResourcesToExport för moduler som ska användas på PowerShell-version 5.0 och senare. Om modulen är som ska användas i PowerShell 4, bör DSCResourcesToExport inte användas eftersom den inte är en stöds manifest nyckel. (DSC var inte tillgänglig före PowerShell 4.) | Ja | Nej |
| **Arbetsflöden** | Arbetsflöden är publiceras i PowerShell-galleriet som skript och identifieras som arbetsflöden (se [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) ett exempel) i koden. Detta styrs inte av manifestet. | Nej | Nej |
| **Rollfunktioner** | Detta visas när modulen som publicerats i PowerShell-galleriet innehåller en eller flera roll funktionen (.psrc) filer som används av JEA. Finns i JEA-dokumentationen för mer information om [rollfunktioner](/powershell/jea/role-capabilities). | Ja | Nej |
| **PowerShell-utgåvor** | Detta har angetts i ett skript eller modulen manifest. För moduler som är avsedd att användas med PowerShell 5.0 och under detta styrs med hjälp av taggar. Använd taggen PSEdition_Desktop för skrivbordet, och Använd taggen PSEdition_Core för kärna. Moduler som används bara på PowerShell 5.1 och senare, har en CompatiblePSEditions-nyckel i huvudsakliga manifestet. Mer information om, granska funktionen PS-versionen i [i PowerShell-Get-dokumentationen](module-psedition-support.md). | Ja | Ja |
| **Beroenden** | Beroenden är moduler i PowerShell-galleriet som deklareras i modulen som RequiredModules eller i skript-manifest som #Requires – modul (namn). | Ja | Ja |
| **Lägsta version av PowerShell** | Det kan anges i ett modulmanifest som PowerShellVersion | Ja | Nej |
| **Versionshistorik** | Versionshistoriken visar uppdateringar för en modul i PowerShell-galleriet. Om en version av ett paket är dold med hjälp av funktionen Ta bort visas den inte i tidigare versioner utom för paket-ägare. | Nej | Nej |
| **Project-webbplats** | Projektwebbplatsen har angetts för moduler i avsnittet Privatedata\PSData i modulmanifestet genom att ange en ProjectURI. I skriptet-manifestet styrs genom att ange. PROJECTURI. | Ja | Ja |
| **Licens** | En licens länk för moduler i avsnittet Privatedata\PSData i modulmanifestet genom att ange en LicenseURI. I skriptet-manifestet styrs genom att ange. LICENSEURI. Det är viktigt att Observera att om en licens har angetts via LicenseURI eller i en modul, villkor för användning av PowerShell-galleriet ange villkor för användning av paketet. Se villkor för användning av information. | Ja | Ja |
| **Ikonen** | En ikon kan anges för alla paket i PowerShell-galleriet genom att ange flaggan IconURI i skriptet manifestet och i avsnittet Privatedata PSData i modulmanifestet. IconURI måste peka på en 32 x 32-avbildning med transparens bakgrund. URI: N **måste** vara en direkt bild-URL och **får inte** går du till en webbsida som innehåller avbildningen eller en fil i PowerShell-galleriet paketet. | Ja | Ja |


## <a name="editing-package-details"></a>Redigera Paketinformation

Sidan Redigera PowerShell-galleriet package kan utgivare att ändra flera av de fält som visas för ett paket, särskilt:

- Titel
- Beskrivning
- Sammanfattning
- Ikon-URL
- URL för Project-startsida
- Författare
- Copyright
- Taggar
- Versionskommentarer
- Licens

Den här metoden Allmänt rekommenderas inte, utom när behövs för att korrigera vad som visas för en äldre version av en modul. Användare som skaffar modulen ser metadata som inte matchar det som visas i PowerShell-galleriet, vilket ökar om paketet. Detta leder ofta förfrågningar som kommer att paketet ägare att bekräfta ändringen. Vi rekommenderar starkt att som helst som den här metoden används en ny version av paketet måste publiceras med samma ändringar.

## <a name="tag-details"></a>Tagginformation

Taggar är enkla strängar konsumenter använder för att hitta paket. Taggar är mest värdefullt när de används konsekvent över många paket som är relaterade till samma avsnitt. Flera varianter av samma ger ord (till exempel databasen och databaser, eller test och testning) vanligtvis lite förmånen. Taggar är ett ords-skiftlägeskänsliga strängar och får inte innehålla tomma värden. Om det finns en fras som du tror att användare söker efter, lägga till som paketbeskrivningen och att den visas i sökresultaten. Använd Pascal gemener och versaler, bindestreck, understreck eller punkt om du vill göra dem mer läsbara.
Var försiktig om hur du skapar långa, komplexa och ovanliga taggar, eftersom de ofta är felstavat.

Det finns taggar som är viktigt att notera, som PowerShell-galleriet och PowerShellGet cmdletar behandla dem unikt. PSEdition_Desktop PSEdition_Core är de specifika exemplen och beskrivs ovan.

Enligt vad som anges ovan, ange taggar ut mest värde när de är specifika och används konsekvent över många paket. Som en utgivare försök att hitta de bästa taggarna du använder, är det enklaste sättet att söka i PowerShell-galleriet för taggar du funderar på att. Vi rekommenderar det blir många paket som returneras och beskrivningar för paketet anpassas med din användning av nyckeln ordet.

Referens följer vissa vanligaste taggar från och med 12/14/2017. I vissa fall finns liknande men kanske mindre perfekt alternativ som visas bredvid taggen. Det är en bra idé att använda den önskade taggen som som kommer att leda till mindre bruset och bättre sökresultat för konsumenter.

| Önskade taggen | Alternativ och anteckningar |
| --- | --- |
| Azure |  |
| DSC | DesiredStateConfiguration är mindre önskvärda, det är för långt |
| ResourceManager | ARM används för att beskriva grupp med processorer och ska inte användas för Azure Resource Manager |
| DSCResourceKit |  |
| SQL |  |
| AWS |  |
| DSCResource |  |
| Automatisering |  |
| REST |  |
| ActiveDirectory | AD används inte för närvarande ensamt  |
| SQLServer |  |
| DBA |  |
| Säkerhet | Defense är mindre exakt |
| Databas | Databaser (plural) är mindre önskvärda |
| DevOps |  |
| Windows |  |
| Utveckla |  |
| Distribution | Distribuera används mindre ofta |
| Molnet |  |
| GIT |  |
| Testa | Testningen är mindre önskvärda |
| VersionControl | Versionen är mindre exakt, även om används oftare  |
| Loggning | Önskad användning av loggning som en åtgärd |
| log | Prioriterade användningen av loggen som en sak |
| Säkerhetskopiering |  |
| IaaS |  |
| Linux |  |
| IIS |  |
| AzureAutomation |  |
| Lagring |  |
| GitHub |  |
| Json |  |
| Exchange |  |
| Nätverk | Nätverk är liknande, används mindre ofta |
| SharePoint |  |
| Rapporter | Rapportering är en åtgärd, rapporten är en sak |
| Rapport | Rapporten är en sak |
| WinRM |  |
| Övervakning |  |
| VSTS |  |
| Excel |  |
| Google |  |
| Färg |  |
| DNS |  |
| Office365 | Stavning ut Office är att föredra. O365 används mer sällan, även om det är kortare |
| Gitlab |  |
| Lära |  |
| AzureAD |  |
| HTML |  |
| Hyper-V | Hyper-v är mindre vanligt som en etikett |
| Konfiguration |  |
| ChatOps |  |
| PackageManagement |  |
| WMI |  |
| Brandvägg |  |
| Docker |  |
| Appveyor |  |
| AzureRm | Används främst för AzureRM-moduler |
| ZIP |  |
| MSI |  |
| MacOS |  |
| PoshBot |  |
