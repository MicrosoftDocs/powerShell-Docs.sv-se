---
title: Nyheter i PowerShell Core 6.0
description: Nya funktioner och ändringar som introducerades i PowerShell Core 6.0
ms.date: 08/06/2018
ms.openlocfilehash: 83c104d838db9d86fe1d485e92245a9c8f2d2057
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62059023"
---
# <a name="whats-new-in-powershell-core-60"></a>Nyheter i PowerShell Core 6.0

[PowerShell Core 6.0] [ github] är en ny version av PowerShell som är plattformsoberoende (Windows, macOS och Linux), öppen källkod och byggd för heterogena miljöer och hybridmoln.

## <a name="moved-from-net-framework-to-net-core"></a>Flyttas från .NET Framework till .NET Core

PowerShell Core använder [.NET Core 2.0][] som dess runtime.
.NET core 2.0 gör det möjligt för PowerShell Core ska fungera på flera plattformar (Windows, macOS och Linux).
PowerShell Core exponerar även API-uppsättning som erbjuds av .NET Core 2.0 som ska användas i PowerShell-cmdlets och skript.

Windows PowerShell används .NET Framework-körning som värd för PowerShell-motorn.
Det innebär att Windows PowerShell exponerar API-uppsättning som erbjuds av .NET Framework.

API: er som delas mellan .NET Core och .NET Framework har definierats som en del av [.NET-standard][].

Mer information om hur detta påverkar modulen/skript-kompatibilitet mellan PowerShell Core och Windows PowerShell finns i [Backwards kompatibilitet med Windows PowerShell](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>Stöd för macOS och Linux

PowerShell officiellt stöder nu macOS och Linux, inklusive:

- Windows 7, 8.1 och 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Windows Server Halvårskanal][semi-annual]
- Ubuntu 14.04, 16.04 och nr 17.04 från
- Debian 8.7 + och 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25, 26
- macOS 10.12+

Paket för följande plattformar också har bidragit med vår community, men de officiellt stöds inte:

- Arch Linux
- Kali Linux
- AppImage (fungerar på flera Linux-plattformar)

Vi har också experimentella (som inte stöds) versioner för följande plattformar:

- Windows på ARM32/ARM64
- Raspbian (Stretch)

Många ändringar gjordes i PowerShell Core 6.0 så att den fungerar bättre för icke-Windows-datorer.
Vissa av dessa större ändringar som påverkar också Windows.
Andra är endast finns eller så är tillämpligt i icke-Windows-installationer av PowerShell Core.

- Tillagt stöd för inbyggda kommandot globbing på Unix-plattformar.
- Den `more` funktioner respekterar Linux `$PAGER` och som standard `less`.
  Det innebär att du kan nu använda jokertecken med inbyggda binärfiler-kommandon (till exempel `ls *.txt`). (#3463)
- Avslutande omvänt snedstreck hoppas automatiskt när du hanterar interna kommandoargumenten. (#4965)
- Ignorera den `-ExecutionPolicy` växla när du kör PowerShell på plattformar som inte är Windows eftersom skriptet signering inte stöds för närvarande. (#3481)
- Fast ConsoleHost ta hänsyn till medägarens `NoEcho` på Unix-plattformar. (#3801)
- Fast `Get-Help` för skiftlägeskänslig matchning på Unix-plattformar. (#3852)
- `powershell` man sida har lagts till i paket

### <a name="logging"></a>Loggning

I macOS, PowerShell använder inbyggt `os_log` API: er för att logga in till Apples [unified loggning system][os_log].
På Linux, PowerShell använder [Syslog][], en lösning för allt vanligare loggning.

### <a name="filesystem"></a>Filsystem

Ett antal ändringar har gjorts på macOS och Linux för att stödja filnamnstecken inte traditionellt stöds på Windows:

- Sökvägar som anges i cmdletar är nu snedstreck-oberoende (både / och \ arbets som katalogavgränsare)
- XDG Base Directory specifikationen är nu respekteras och används som standard:
  - Sökväg till Linux/Mac OS-profilen finns i `~/.config/powershell/profile.ps1`
  - Historiken spara sökväg finns i `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - Modulsökväg användare finns i `~/.local/share/powershell/Modules`
- Stöd för fil- och namn som innehåller tecknet kolon på Unix. (#4959)
- Stöd för Skriptnamn eller kompletta sökvägar som har kommatecken. (#4136) (Tack vare [ @TimCurwick ](https://github.com/TimCurwick)!)
- Identifiera när `-LiteralPath` används för att ignorera jokertecken expansion för navigering cmdletar. (#5038)
- Uppdatera `Get-ChildItem` att arbeta mer liknande den * nix `ls -R` och Windows `DIR /S` inbyggda kommandon.
  `Get-ChildItem` Nu returnerar de symboliska länkarna under rekursiv sökning och inte i katalogerna som dessa länkar mål. (#3780)

### <a name="case-sensitivity"></a>Skiftlägeskänslighet

Linux och macOS brukar vara skiftlägeskänsliga när Windows är skiftlägeskänsliga och behålla fallet.
I allmänhet är PowerShell inte skiftlägeskänsligt.

Till exempel miljövariabler är skiftlägeskänsliga på macOS och Linux, så den skiftläge för den `PSModulePath` miljövariabeln har standardiserats. (#3255) `Import-Module` är skiftlägesokänsligt när den använder en filsökväg för att fastställa modulens namn. (#5097)

## <a name="support-for-side-by-side-installations"></a>Stöd för sida-vid-sida-installationer

PowerShell Core är installerad, konfigurerad och körs separat från Windows PowerShell.
PowerShell Core har ett ”portabla” ZIP-paket.
I ZIP-paketet kan installera du obegränsat antal versioner av var som helst på disk, inklusive lokala till ett program som använder PowerShell som ett beroende.
Installation sida vid sida gör det lättare att testa nya versioner av PowerShell och migrera befintliga skript över tid.
Sida-vid-sida kan också bakåtkompatibilitet kompatibilitet som skript kan fästas på specifika versioner som de behöver.

> [!NOTE]
> Som standard sker MSI-baserade installationsprogrammet på Windows en uppdatering på plats-installation.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>Byta namn på `powershell(.exe)` till `pwsh(.exe)`

Det binära namnet för PowerShell Core har ändrats från `powershell(.exe)` till `pwsh(.exe)`.
Den här ändringen ger ett deterministiskt sätt för användare att köra PowerShell Core på datorer för sida-vid-sida Windows PowerShell och PowerShell Core-installationer.
`pwsh` är också mycket kortare och lättare att ange.

Ytterligare ändringar av `pwsh(.exe)` från `powershell.exe`:

- Första namngivna parametern från ändrats `-Command` till `-File`.
  Den här ändringen åtgärdar användningen av `#!` (även kallat som en shebang) i PowerShell-skript som körs från icke-PowerShell-gränssnitt på icke-Windows-plattformar.
  Det innebär också att du kan köra kommandon som `pwsh foo.ps1` eller `pwsh fooScript` utan att ange `-File`.
  Den här ändringen kräver dock att du uttryckligen anger `-c` eller `-Command` vid försök att köra kommandon som `pwsh.exe -Command Get-Command`. (#4019)
- PowerShell Core accepterar den `-i` (eller `-Interactive`) växel för att ange ett interaktivt gränssnitt. (#3558) Detta gör att PowerShell som ska användas som ett standardgränssnitt på Unix-plattformar.
- Ta bort parametrar `-importsystemmodules` och `-psconsoleFile` från `pwsh.exe`. (#4995)
- Ändra `pwsh -version` och inbyggd hjälp för `pwsh.exe` för att anpassas med andra inbyggda verktyg. (#4958 & #4931) (Tack [ @iSazonov ](https://github.com/iSazonov))
- Ogiltigt argument felmeddelanden för `-File` och `-Command` och slutkoder konsekvent med Unix-standarder (#4573)
- Lagt till `-WindowStyle` parametern på Windows. (#4573) Paket-baserade installationer uppdateringar på icke-Windows-plattformar är på samma sätt kan uppdateringar på plats.

## <a name="backwards-compatibility-with-windows-powershell"></a>Bakåtkompatibilitet kompatibilitet med Windows PowerShell

Målet med PowerShell Core är att förbli som kompatibel som möjligt med Windows PowerShell.
PowerShell Core använder [.NET-standard][] 2.0 och binär kompatibilitet med befintliga .NET-sammansättningar.
Många PowerShell-moduler är beroende av dessa sammansättningar (ofta tider DLL: er), så att .NET Standard gör att de kan fortsätta att arbeta med .NET Core.
PowerShell Core innehåller också en tumregel att leta i kända mappar, t.ex. där den globala sammansättningscachen vanligtvis finns på disken – för att hitta beroenden i .NET Framework-DLL.

Du kan lära dig mer om .NET Standard på den [.NET-bloggen][], i det här [YouTube][] video- och via detta [vanliga frågor och svar][] på GitHub.

Bästa arbete har gjorts för att se till att PowerShell-moduler för språk och ”inbyggd” (t.ex. `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`och så vidare) fungerar på samma sätt som i Windows PowerShell.
I många fall med hjälp av gruppen, har vi lagt till nya funktioner och felkorrigeringar dessa cmdlets.
I vissa fall, på grund av ett saknat beroende i den underliggande .NET lager funktioner har tagits bort eller är inte tillgänglig.

De flesta av de moduler som levereras som en del av Windows (till exempel `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`och så vidare) och andra Microsoft-produkter inklusive Azure och Office har inte varit *uttryckligen* portas till. NET Core ännu.
PowerShell-teamet arbetar med dessa grupper och team att validera och porten deras befintliga moduler PowerShell Core.
Med .NET Standard och [CDXML][], många av dessa traditionella Windows PowerShell-moduler verkar fungera i PowerShell Core, men de har inte formellt verifierats och formellt stöds inte.

Genom att installera den [ `WindowsPSModulePath` ] [ windowspsmodulepath] modulen, kan du använda Windows PowerShell-moduler genom att lägga till Windows PowerShell `PSModulePath` till PowerShell Core `PSModulePath`.

Installera först den `WindowsPSModulePath` modul från PowerShell-galleriet:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

När du har installerat den här modulen, kör den `Add-WindowsPSModulePath` cmdlet för att lägga till Windows PowerShell `PSModulePath` till PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Docker-stöd

PowerShell Core lägger till stöd för Docker-behållare för alla större plattformar som stöds (inklusive flera Linux-distributioner, Windows Server Core och Nano Server).

En fullständig lista finns i taggarna på [ `microsoft/powershell` på Docker Hub][docker-hub].
Läs mer om Docker och PowerShell Core [Docker][] på GitHub.

## <a name="ssh-based-powershell-remoting"></a>SSH-baserad PowerShell-fjärrkommunikation

PowerShell fjärrkommunikation Protocol (PSRP) fungerar nu med protokollet Secure Shell (SSH) utöver traditionella WinRM-baserade PSRP.

Detta innebär att du kan använda cmdlet: ar som `Enter-PSSession` och `New-PSSession` och autentisera med hjälp av SSH.
Allt du behöver göra är att registrera PowerShell som ett undersystem med en OpenSSH-baserade SSH-server och du kan använda din befintliga SSH-baserad autentisera mekanismer (t.ex. lösenord eller privata nycklar) med den traditionella `PSSession` semantik.

Läs mer om att konfigurera och använda SSH-baserad fjärrkommunikation [PowerShell fjärrkommunikation via SSH][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom-except-for-new-modulemanifest"></a>Standardkodning är UTF-8 utan att en BOM förutom New-ModuleManifest

I tidigare Windows PowerShell-cmdlets som `Get-Content`, `Set-Content` används olika kodningar, till exempel ASCII och UTF-16.
Avvikelse i används som standard skapas problem när blanda cmdlets utan att ange kodning.

Icke-Windows-plattformar använder traditionellt UTF-8 utan en Byte (BOM Order Mark) som standardkodning för textfiler.
Flera Windows-program och verktyg du befordras från UTF-16 och mot BOM utan UTF-8-kodning.
PowerShell Core ändras den standardkodning som överensstämmer med bredare ekosystem.

Det innebär att alla inbyggda cmdletar som använder den `-Encoding` parametern används den `UTF8NoBOM` värdet som standard.
Följande cmdletar påverkas av den här ändringen:

- Add-Content
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- Out-File
- Välj-sträng
- Send-MailMessage
- Set-Content

Dessa cmdletar har också uppdaterats så att den `-Encoding` parametern accepterar universellt `System.Text.Encoding`.

Standardvärdet för `$OutputEncoding` har också ändrats till UTF-8.

Som bästa praxis bör du uttryckligen ange kodningar i skript med hjälp av den `-Encoding` parametern för att producera deterministisk beteendet mellan plattformar.

`New-ModuleManifest` cmdlet: en har inte **Encoding** parametern. Kodning av manifestfilen (.psd1)-filen för modulen skapas med `New-ModuleManifest` cmdlet beror på miljön: om det är PowerShell Core som körs på Linux sedan kodning är UTF-8 (utan BOM); annars kodning är UTF-16 (med BOM). (#3940)

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Stöd för backgrounding av pipelines med et-tecken (`&`) (#3360)

Placera `&` orsakar pipelinen ska köras som ett PowerShell-jobb i slutet av en pipeline.
När en pipeline är backgrounded returneras ett jobbobjekt.
När pipelinen körs som ett jobb, alla standardprogram `*-Job` cmdletar kan användas för att hantera jobbet.
Variabler (ignorera processpecifika variabler) som används i pipelinen kopieras automatiskt till jobbet så `Copy-Item $foo $bar &` bara fungerar.
Jobbet körs också i den aktuella katalogen i stället för i användarens arbetskatalog.
Mer information om PowerShell-jobb finns i [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).

## <a name="semantic-versioning"></a>Semantisk versionshantering

- Gjort `SemanticVersion` kompatibel med `SemVer 2.0`. (#5037) (Tack [ @iSazonov ](https://github.com/iSazonov)!)
- Ändra standard `ModuleVersion` i `New-ModuleManifest` till `0.0.1` för att anpassas till SemVer. (#4842) (Tack [ @LDSpits ](https://github.com/LDSpits))
- Lagt till `semver` som en typ accelerator för `System.Management.Automation.SemanticVersion`. (#4142) (Tack vare [ @oising ](https://github.com/oising)!)
- Aktiverad jämförelse mellan en `SemanticVersion` instans och en `Version` -instans som har konstruerats med endast `Major` och `Minor` Versionsvärden.

## <a name="language-updates"></a>Språkuppdateringar

- Implementera Unicode-escape-parsning så att användarna kan använda Unicode-tecken som argument, strängar eller variabelnamn. (#3958) (Tack vare [ @rkeithhill ](https://github.com/rkeithhill)!)
- Har lagts till nya escape-tecknet för ESC: `` `e``
- Stöd för att konvertera uppräkningar för att sträng (#4318) har lagts till (tack [ @KirkMunro ](https://github.com/KirkMunro))
- Fast omvandling enstaka element-matris till en allmän samling. (#3170)
- Har lagts till tecknet intervallet överlagring för den `..` operator, så `'a'..'z'` Returnerar tecknen från ”a” till ”z”. (#5026) (Tack [ @IISResetMe ](https://github.com/IISResetMe)!)
- Fast variabeltilldelning inte skriva över skrivskyddade variabler
- Skicka lokala variabler över automatiska variabler till 'DottedScopes' när över hela skript-cmdlets (#4709)
- Aktivera 'Singleline, Multiline' alternativet i delningsoperatorn (#4721) (tack [ @iSazonov ](https://github.com/iSazonov))

## <a name="engine-updates"></a>Uppdateringar till

- `$PSVersionTable` har fyra nya egenskaper:
  - `PSEdition`: Detta är inställt på `Core` på PowerShell Core och `Desktop` på Windows PowerShell
  - `GitCommitId`: Detta är ID: T för Git-incheckning för Git-gren eller tagg där PowerShell har skapats.
    På utgivna versioner kommer det sannolikt att samma som `PSVersion`.
  - `OS`: Detta är en sträng för OS-version som returneras av `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: Detta returneras av `[System.Environment]::OSVersion.Platform` anges till `Win32NT` på Windows, `Unix` på macOS, och `Unix` i Linux.
- Ta bort den `BuildVersion` egenskap från `$PSVersionTable`.
  Den här egenskapen har alltså tätt kopplade till build-version för Windows.
  I stället rekommenderar vi att du använder `GitCommitId` att hämta exakta build-versionen av PowerShell Core. (#3877) (Tack vare [ @iSazonov ](https://github.com/iSazonov)!)
- Ta bort `ClrVersion` egenskap från `$PSVersionTable`.
  Den här egenskapen är inte relevant för .NET Core och endast har bevarats i .NET Core för specifika äldre syften kan inte tillämpas till PowerShell.
- Lagt till tre nya automatiska variabler för att avgöra om PowerShell körs i en viss OS: `$IsWindows`, `$IsMacOs`, och `$IsLinux`.
- Lägg till `GitCommitId` till PowerShell Core banderoll.
  Nu du inte behöver köra `$PSVersionTable` när du startar PowerShell för att hämta versionen! (#3916) (Tack vare [ @iSazonov ](https://github.com/iSazonov)!)
- Lägg till en JSON-konfigurationsfil som kallas `powershell.config.json` i `$PSHome` att lagra vissa inställningar som krävs innan starttiden (t.ex. `ExecutionPolicy`).
- Blockera inte pipeline när du kör Windows EXE
- Aktiverade uppräkning av COM-samlingar. (#4553)

## <a name="cmdlet-updates"></a>Cmdlet-uppdateringar

### <a name="new-cmdlets"></a>Nya cmdletar

- Lägg till `Get-Uptime` till `Microsoft.PowerShell.Utility`.
- Lägg till `Remove-Alias` kommando. (#5143) (Tack [ @PowershellNinja ](https://github.com/PowershellNinja)!)
- Lägg till `Remove-Service` till Management-modulen. (#4858) (Tack [ @joandrsn ](https://github.com/joandrsn)!)

### <a name="web-cmdlets"></a>Web-cmdletar

- Lägg till certifikatstöd för autentisering för web-cmdletar. (#4646) (Tack [ @markekraus ](https://github.com/markekraus))
- Lägg till stöd för content-huvuden i web-cmdletar. (#4494 & #4640) (Tack [ @markekraus ](https://github.com/markekraus))
- Lägg till stöd för flera länk-huvud i Web-cmdletar. (#5265) (Tack [ @markekraus ](https://github.com/markekraus)!)
- Stöd för länken rubrik sidbrytning i web-cmdlets (#3828)
  - För `Invoke-WebRequest`, när svaret innehåller en länk-rubrik som vi skapar en RelationLink-egenskap som en ordlista som representerar de URL: er och `rel` attribut och se till att webbadresserna är absolut att göra det enklare för utvecklare att använda.
  - För `Invoke-RestMethod`, när svaret innehåller en länk-rubrik som vi Exponerar en `-FollowRelLink` växel automatiskt följa `next` `rel` länkar förrän de inte längre finns eller en gång vi når det valfria `-MaximumFollowRelLink` parametervärde.
- Lägg till `-CustomMethod` parameter i web-cmdletar för standardmässiga metoden verb. (#3142) (Tack vare [ @Lee303 ](https://github.com/Lee303)!)
- Lägg till `SslProtocol` stöd för Web-cmdletar. (#5329) (Tack [ @markekraus ](https://github.com/markekraus)!)
- Lägg till Multipart stöd i web-cmdletar. (#4782) (Tack [ @markekraus ](https://github.com/markekraus))
- Lägg till `-NoProxy` i web-cmdletar så att de ignorerar systemomfattande proxyinställning. (#3447) (Tack vare [ @TheFlyingCorpse ](https://github.com/TheFlyingCorpse)!)
- Användaren Agent för webb-cmdletar nu rapporterar OS-plattform (#4937) (tack [ @LDSpits ](https://github.com/LDSpits))
- Lägg till `-SkipHeaderValidation` växla till webb-cmdletar för att lägga till rubriker utan att verifiera huvudets värde. (#4085)
- Aktivera web-cmdletar för att verifiera inte HTTPS-certifikat på servern om det behövs.
- Lägg till autentiseringsparametrar i webb-cmdletar. (#5052) (Tack [ @markekraus ](https://github.com/markekraus))
  - Lägg till `-Authentication` som tillhandahåller tre alternativ: Basic, OAuth och Ägarautentisering.
  - Lägg till `-Token` att hämta ägar-token för OAuth och ägar-alternativ.
  - Lägg till `-AllowUnencryptedAuthentication` kringgå authentication som har angetts för alla transportschema än HTTPS.
- Lägg till `-ResponseHeadersVariable` till `Invoke-RestMethod` vill aktivera avbildningsfunktionen för svarshuvuden. (#4888) (Tack [ @markekraus ](https://github.com/markekraus))
- Åtgärda web-cmdletar för att inkludera ett HTTP-svar i undantaget när Svarets statuskod inte lyckades. (#3201)
- Ändra web cmdletar `UserAgent` från `WindowsPowerShell` till `PowerShell`. (#4914) (Tack [ @markekraus ](https://github.com/markekraus))
- Lägg till explicita `ContentType` identifiering till `Invoke-RestMethod` (#4692)
- Åtgärda web cmdletar `-SkipHeaderValidation` att arbeta med inte är standard användaragent-rubriker. (#4479 & #4512) (Tack [ @markekraus ](https://github.com/markekraus))

### <a name="json-cmdlets"></a>JSON-cmdletar

- Lägg till `-AsHashtable` till `ConvertFrom-Json` att returnera en `Hashtable` i stället. (#5043) (Tack [ @bergmeister ](https://github.com/bergmeister)!)
- Använd prettier Formateraren med `ConvertTo-Json` utdata. (#2787) (Tack vare @kittholland!)
- Lägg till `Jobject` serialisering stöd till `ConvertTo-Json`. (#5141)
- Åtgärda `ConvertFrom-Json` att deserialisera en matris med strängar från pipelinen som tillsammans skapar en fullständig JSON-sträng.
  Det löser tillfällen där nya rader skulle skapa JSON-parsning. (#3823)
- Ta bort den `AliasProperty "Count"` definierats för `System.Array`.
  Detta tar bort den överflödig `Count` egenskapen på vissa `ConvertFrom-Json` utdata. (#3231) (Tack vare [ @PetSerAl ](https://github.com/PetSerAl)!)

### <a name="csv-cmdlets"></a>CSV-cmdletar

- Lägg till `PSTypeName` stöd för `Import-Csv` och `ConvertFrom-Csv`. (#5389) (Tack [ @markekraus ](https://github.com/markekraus)!)
- Kontrollera `Import-Csv` stöder `CR`, `LF`, och `CRLF` som rad avgränsare. (#5363) (Tack [ @iSazonov ](https://github.com/iSazonov)!)
- Kontrollera `-NoTypeInformation` standard på `Export-Csv` och `ConvertTo-Csv`. (#5164) (Tack [ @markekraus ](https://github.com/markekraus))

### <a name="service-cmdlets"></a>Cmdlet: ar

- Lägg till egenskaper `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName`, och `StartupType` till den `ServiceController` objekten som returneras av `Get-Service`. (#4907) (Tack [ @joandrsn ](https://github.com/joandrsn))
- Lägg till funktioner för att ange autentiseringsuppgifter på `Set-Service` kommando. (#4844) (Tack [ @joandrsn ](https://github.com/joandrsn))

### <a name="other-cmdlets"></a>Andra cmdlet: ar

- Lägg till en parameter till `Get-ChildItem` kallas `-FollowSymlink` som passerar symlinks på begäran med söker efter länk slingor. (#4020)
- Uppdatera `Add-Type` för `CSharpVersion7`. (#3933) (Tack vare [ @iSazonov ](https://github.com/iSazonov))
- Ta bort den `Microsoft.PowerShell.LocalAccounts` modulen på grund av användningen av stöds inte API: er tills en bättre lösning hittas. (#4302)
- Ta bort den `*-Counter` cmdlets i `Microsoft.PowerShell.Diagnostics` på grund av användningen av stöds inte API: er tills en bättre lösning hittas. (#4303)
- Lägg till stöd för `Invoke-Item -Path <folder>`. (#4262)
- Lägg till `-Extension` och `-LeafBase` växlar till `Split-Path` så att du kan dela upp sökvägar mellan filnamnstillägget och resten av filnamnet. (#2721) (Tack vare [ @powercode ](https://github.com/powercode)!)
- Lägg till parametrar `-Top` och `-Bottom` till `Sort-Object` för högsta/lägsta N sortera
- Exponera en process överordnade processen genom att lägga till den `CodeProperty "Parent"` till `System.Diagnostics.Process`. (#2850) (Tack vare [ @powercode ](https://github.com/powercode)!)
- Använda MB i stället för KB för minne kolumner i `Get-Process`
- Lägg till `-NoNewLine` växla för `Out-String`. (#5056) (Tack [ @raghav710 ](https://github.com/raghav710))
- `Move-Item` cmdlet godkänner `-Include`, `-Exclude`, och `-Filter` parametrar. (#3878)
- Tillåt `*` som ska användas i registersökväg för `Remove-Item`. (#4866)
- Lägg till `-Title` till `Get-Credential` och skapa en enhetlig fråga upplevelse mellan plattformar.
- Lägg till den `-TimeOut` parameter `Test-Connection`. (#2492)
- `Get-AuthenticodeSignature` cmdlet: ar kan nu få signatur-filtidsstämpel. (#4061)
- Ta bort stöds inte `-ShowWindow` växla från `Get-Help`. (#4903)
- Åtgärda `Get-Content -Delimiter` returnerade (#3706) att inte inkludera avgränsaren i matriselement (tack [ @mklement0 ](https://github.com/mklement0))
- Lägg till `Meta`, `Charset`, och `Transitional` parametrar för att `ConvertTo-HTML` (#4184) (tack [ @ergo3114 ](https://github.com/ergo3114))
- Lägg till `WindowsUBR` och `WindowsVersion` egenskaper så att `Get-ComputerInfo` resultat
- Lägg till `-Group` parameter `Get-Verb`
- Lägg till `ShouldProcess` stöd till `New-FileCatalog` och `Test-FileCatalog` (åtgärdar `-WhatIf` och `-Confirm`). (#3074) (Tack vare [ @iSazonov ](https://github.com/iSazonov)!)
- Lägg till `-WhatIf` växla till `Start-Process` cmdlet (#4735) (tack [ @sarithsutha ](https://github.com/sarithsutha))
- Lägg till `ValidateNotNullOrEmpty` för många befintliga parametrar.

## <a name="tab-completion"></a>Tabbifyllning

- Förbättrad typ inferens i tabbifyllning utifrån variabelvärden för körning. (#2744) (Tack vare [ @powercode ](https://github.com/powercode)!) På så sätt kan tabbifyllning i situationer som:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Lägg till hash-tabell tabbifyllning för `-Property` av `Select-Object`. (#3625) (Tack vare [ @powercode ](https://github.com/powercode))
- Aktivera argumentet automatisk komplettering för `-ExcludeProperty` och `-ExpandProperty` av `Select-Object`. (#3443) (Tack vare [ @iSazonov ](https://github.com/iSazonov)!)
- Åtgärda en bugg i tabbifyllning att göra `native.exe --<tab>` anropar ursprungliga komplettering. (#3633) (Tack vare [ @powercode ](https://github.com/powercode)!)

## <a name="breaking-changes"></a>Icke-bakåtkompatibla ändringar

Vi har lanserat ett antal icke-bakåtkompatibla ändringar i PowerShell Core 6.0.
Mer information om dem i detalj, finns i [icke-bakåtkompatibla ändringar i PowerShell Core 6.0][breaking-changes].

## <a name="debugging"></a>Felsökning

- Stöd för step-in fjärrfelsökning för `Invoke-Command -ComputerName`. (#3015)
- Aktivera binder felsökningsloggning i PowerShell Core

## <a name="filesystem-updates"></a>Filsystem-uppdateringar

- Aktivera användning av filsystem-provider från en UNC-sökväg. ($4998)
- `Split-Path` fungerar nu med UNC-rötter
- `cd` inga argument fungerar nu som `cd ~`
- Fast PowerShell Core som tillåter användning av sökvägarna som är mer än 260 tecken långt. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Felkorrigeringar och prestandaförbättringar

Vi har gjort *många* förbättringar av prestanda i PowerShell, inklusive i starttiden för olika inbyggda cmdletar och interaktion med inbyggda binärfiler.

Vi har också åtgärdat ett antal buggar i PowerShell Core.
En fullständig lista över korrigeringar och ändringar, Kolla in vår [ändringsloggen][] på GitHub.

## <a name="telemetry"></a>Telemetri

- PowerShell Core 6.0 har lagts till telemetri till konsolvärden rapporten två värden (#3620):
  - OS-plattform (`$PSVersionTable.OSDescription`)
  - den exakta versionen av PowerShell (`$PSVersionTable.GitCommitId`)

Om du vill välja bort den här telemetrin skapar bara `POWERSHELL_TELEMETRY_OPTOUT` miljövariabel med något av följande värden: `true`, `1` eller `yes`.
Skapa variabeln kringgår all telemetri och med före den första körningen av PowerShell.
Vi har även planer på att exponera informationen telemetri och de insikter vi få djupare förståelse från från telemetri i den [community instrumentpanelen][community-dashboard].
Du hittar mer information om hur vi använder informationen i det här [blogginlägget][telemetry-blog].

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/dotnet/core/
[.NET-standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: breaking-changes-ps6.md
[ändringsloggen]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET-standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET-bloggen]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[VANLIGA FRÅGOR OCH SVAR]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
