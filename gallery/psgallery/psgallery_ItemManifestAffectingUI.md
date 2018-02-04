# <a name="item-manifest-values-that-impact-the-powershell-gallery-ui"></a>Objektet manifestet värden som påverkar Gränssnittet PowerShell-galleriet

Det här avsnittet innehåller utgivare med översiktlig information om hur du ändrar manifest för sina PowerShell-galleriet publikationer så att funktionerna i PowerShellGet-cmdlets och PowerShell-galleriet Användargränssnittet kommer att påverkas. Det här innehållet är ordnad efter där ändringen ska visas, från och med avsnittet i mitten och sedan navigeringsområdet till vänster. Det finns en informationsavsnittet omfattar taggar, som identifierar viktiga taggar, samt några av de vanligaste taggar. Det finns två avsnitt som innehåller manifestet exempel: 

* Moduler, se [uppdatering modulen Manifest](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/psget_update-modulemanifest)
* Skript, se [skapa skriptfil med Metadata](https://docs.microsoft.com/en-us/powershell/gallery/psget/script/psget_new-scriptfileinfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>PowerShell-galleriet funktionselement styrs av manifestet

Tabellen nedan visar elementen i PowerShell-galleriet objektet sidan användargränssnitt som styrs av utgivaren.
Varje post anger om den kan styras av manifestet modul eller skript.

| UI-Element | Beskrivning | Modul | Skript | 
| --- | --- | --- | --- |
| **Rubrik** | Det här är namnet på det objekt som har publicerats i galleriet  | Nej | Nej |
| **Version** | Den version som visas är Versionsträngen i metadata och en förhandsversion om har angetts. Den primära delen av version i ett modulmanifest är ModuleVersion. Det har identifierats som ett skript. VERSION. Om en förhandsversion sträng anges ska det läggas till ModuleVersion för moduler, eller anges som del av. VERSION för skript. Det finns dokumentation för att ange förhandsversionen strängar i [moduler](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/prereleasemodule), och i [skript](https://docs.microsoft.com/en-us/powershell/gallery/psget/script/prereleasescript) | Ja | Ja |
| **Beskrivning** | Detta är beskrivningen i modulmanifestet och det är i ett skript filen manifest. BESKRIVNING | Ja | Ja |
| **Kräv godkännande av licens** | En modul kan kräva att användaren godkänner en licens genom att ändra modulmanifestet med RequireLicenseAcceptance = $true tillhandahåller en LicenseURI och ge en filen license.txt i roten av mappen modulen. Mer information finns i den [kräver godkännande av licens](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_requires_license_acceptance) avsnittet. | Ja | Nej |
| **Versionsanmärkningar** | Den här informationen hämtas från avsnittet ReleaseNotes under PSData\PrivateData för moduler. I skriptet manifest är det den. RELEASENOTES element. | Ja | Ja |
| **Ägare** | Ägare är en lista över användare i PowerShell-galleriet som kan uppdatera ett objekt. Listan över ägare ingår inte i manifestet för objektet. Ytterligare dokumentation beskriver hur du [hantera objekt ägare](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners). | Nej | Nej |
| **Författare** | Detta ingår i modulmanifestet som författare och i ett skript-manifest som. FÖRFATTARE. Fältet Författare används ofta för att ange ett företag eller organisation som är associerad med ett objekt. | Ja | Ja |
| **Copyright** | Detta är det Copyright i modulmanifestet, och. COPYRIGHT i ett skript manifest. | Ja | Ja |
| **FileList** | I listan över ritas från paketet när den publiceras i PowerShell-galleriet. Det går inte att styra av manifestet information. Obs: det finns en ytterligare .nuspec-fil som visas i listan med varje objekt i PowerShell-galleriet som inte finns när du har installerat objektet på ett system. Detta är Nuget-paketet manifest för objektet och kan ignoreras. | Nej | Nej |
| **Taggar** | För moduler ingår taggar under PSData\PrivateData. Avsnittet är märkt för skript. TAGGAR. Observera att taggar inte får innehålla blanksteg, även när de är inom citattecken. Taggar har ytterligare krav och innebörd som beskrivs senare i det här avsnittet i avsnittet taggen information. | Ja | Ja |
| **Cmdletar** | Detta tillhandahålls i modulmanifestet med CmdletsToExport. Observera att det bästa sättet är att ange en lista med objekt, snarare än att använda jokertecknet ”*”, enligt som förbättrar prestanda läsa in modulen för användare. | Ja | Nej |
| **Funktioner** | Detta tillhandahålls i modulmanifestet med FunctionsToExport. Observera att det bästa sättet är att ange en lista med objekt, snarare än att använda jokertecknet ”*”, enligt som förbättrar prestanda läsa in modulen för användare. | Ja | Nej |
| **DSC-resurser** | Detta har angetts i manifestet DscResourcesToExport för moduler som ska användas på PowerShell version 5.0 och senare. Om modulen ska användas i PowerShell 4, bör DSCResourcesToExport inte användas eftersom den inte är en stöds manifestet nyckel. (DSC var inte tillgänglig innan PowerShell 4.) | Ja | Nej |
| **Arbetsflöden** | Arbetsflöden är publicerade i PowerShell-galleriet som skript och identifieras som arbetsflöden (se [Anslut AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) ett exempel) i koden. Detta är inte styrs av manifestet. | Nej | Nej |
| **Rollen funktioner** | Detta visas när modulen som publicerats till PowerShell-galleriet innehåller minst en roll (.psrc) funktionsfiler, som används av JEA. I JEA dokumentationen för mer information finns på [roll funktioner](https://docs.microsoft.com/en-us/powershell/jea/role-capabilities). | Ja | Nej |
| **PowerShell-versioner** | Detta har angetts i ett skript eller modulen manifest. För moduler som är avsedd att användas med PowerShell 5.0 och under denna kontrolleras med hjälp av taggar. Använd taggen PSEdition_Desktop för skrivbordet, och Använd taggen PSEdition_Core för kärnor. För moduler som används endast på PowerShell 5.1 och ovan, finns en CompatiblePSEditions nyckel i huvudsakliga manifestet. Granska ytterligare information om funktionen PS Edition i [PowerShell Get-dokumentationen](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/modulewithpseditionsupport). | Ja | Ja |
| **Beroenden** | Beroenden är modulerna i PowerShell-galleriet som deklareras i modulen som RequiredModules eller i manifestet skript som #Requires-modul (namn). | Ja | Ja |
| **Lägsta version av Powershell** | Det kan anges i en modulmanifest som PowerShellVersion | Ja | Nej |
| **Versionshistorik** | Tidigare versioner visar uppdateringar som görs till en modul i PowerShell-galleriet. Om en version av ett objekt med hjälp av funktionen Ta bort visas det inte i tidigare versioner utom till objektet ägare. | Nej | Nej |
| **Project-webbplats** | Projektwebbplatsen har angetts för moduler i avsnittet Privatedata\PSData i modulmanifestet genom att ange en ProjectURI. I manifestet skript styrs genom att ange. PROJECTURI. | Ja | Ja |
| **Licens** | En licens-länk har angetts för moduler i avsnittet Privatedata\PSData i modulmanifestet genom att ange en LicenseURI. I manifestet skript styrs genom att ange. LICENSEURI. Det är viktigt att Observera att om en licens har angetts via LicenseURI eller i en modul, villkor för användning av PowerShell-galleriet ange villkor för användning av objektet. Se villkoren för användning av information. | Ja | Ja |

## <a name="editing-item-details"></a>Redigera detaljer om objektet

Sidan Redigera PowerShell-galleriet artikel kan utgivare ändra flera av de fält som visas för ett objekt, speciellt:

* Titel
* Beskrivning
* Sammanfattning
* Ikon-URL
* URL för startsidan
* Författare
* Copyright
* Taggar
* Versionskommentarer
* Kräv licens

Den här metoden allmänhet rekommenderas inte, utom när behövs för att korrigera det som visas för en äldre version av en modul. Användarna som skaffar modulen visas metadata inte matchar det som visas i PowerShell-galleriet, vilket ökar om objektet. Detta resulterar ofta i frågor som ska objektet ägare att bekräfta ändringen. Det rekommenderas starkt att den här metoden används när en ny version av objektet ska publiceras med samma ändringar. 

## <a name="tag-details"></a>Taggen information

Taggar är enkla strängar konsumenter används för att hitta objekt. Taggar är mest värdefullt när de används konsekvent över många objekt som är relaterade till samma ämnet. Med hjälp av flera varianter av samma innehåller word (till exempel databasen och databaser, eller test och testa) vanligtvis lite förmånen. Taggar är skiftlägeskänsliga strängar för enstaka ord och får inte innehålla blanksteg. Om det finns en fras som du tror att användarna ska söka efter, lägga till som beskrivning av artikeln och kommer att hittas i sökresultaten. Använd Pascal skiftläge, bindestreck, understreck eller perioden om du vill förbättra läsbarhet. Var försiktig om hur du skapar långa komplex och onormal taggar som de är ofta felstavade. 

Taggar som är viktigt att notera, PowerShell-galleriet och PowerShellGet cmdlets behandla dem unikt. PSEdition_Desktop PSEdition_Core är specifika exempel och beskrivs ovan. 

Som nämnts ovan, ange taggar största möjliga värde när de är specifika och använda konsekvent över många objekt. Som en utgivare försöker hitta bästa taggarna du använder, är det enklaste sättet att söka PowerShell-galleriet för taggar som du överväger. Vi rekommenderar finns många objekt som returneras och artikelbeskrivningarna överensstämmer med din användning av den nyckelord. 

Här följer vissa vanligaste taggar från och med 12/14/2017 referens. I vissa fall finns liknande men kanske mindre perfekt alternativ som visas bredvid taggen.
Det är bäst att använda önskade-tagg som som kommer att resultera i mindre brus och bättre sökresultat för konsumenterna. 


| **Önskad tagg** | **Alternativ och anteckningar** |
| --- | --- |
| **Azure** |  |
| **DSC** | DesiredStateConfiguration är mindre önskvärt, den är för lång |
| **ResourceManager** | ARM-används för att beskriva grupp processorer och ska inte användas för Azure Resource Manager | **DSCResourceKit** |  |
| **SQL** |  |
| **AWS** |  |
| **DSCResource** |  |
| **Automation** |  |
| **REST** |  |
| **ActiveDirectory** | AD används inte för närvarande ensamt  |
| **SQLServer** |  |
| **DBA** |  |
| **Säkerhet** | Skyddet är mindre exakt |
| **Databasen** | Databaser (pluralformen) är mindre önskvärt |
| **DevOps** |  |
| **Windows** |  |
| **Skapa** |  |
| **Distribution** | Distribuera används mindre ofta |
| **Molntjänster** |  |
| **GIT** |  |
| **Test** | Testning är mindre önskvärt |
| **VersionControl** | Versionen är mindre exakt, även om används mer sällan  |
| **Loggning** | Önskad användning av loggning som en åtgärd |
| **Logg** | Prioriterade användningen av loggen som en sak |
| **Backup** |  |
| **IaaS** |  |
| **Linux** |  |
| **IIS** |  |
| **AzureAutomation** |  |
| **Storage** |  |
| **GitHub** |  |
| **Json** |  |
| **Exchange** |  |
| **Nätverk** | Nätverk är liknande används mindre ofta |
| **SharePoint** |  |
| **Rapportering** | Reporting är en åtgärd, rapporten är en sak |
| **Rapporten** | Rapporten är en sak |
| **WinRM** |  |
| **Övervakning** |  |
| **VSTS** |  |
| **Excel** |  |
| **Google** |  |
| **Färg** |  |
| **DNS** |  |
| **Office365** | Det är bättre att stavning av Office. O365 används mindre ofta, men kortare | **Gitlab** |  |
| **Pester** |  |
| **AzureAD** |  |
| **HTML** |  |
| **Hyper-V** | Hyper-v är mindre vanliga som en etikett |
| **Konfiguration** |  |
| **ChatOps** |  |
| **PackageManagement** |  |
| **WMI** |  |
| **Brandväggen** |  |
| **Docker** |  |
| **Appveyor** |  |
| **AzureRm** | Används främst för AzureRM-moduler |
| **Zip** |  |
| **MSI** |  |
| **Mac** |  |
| **PoshBot** |  |


