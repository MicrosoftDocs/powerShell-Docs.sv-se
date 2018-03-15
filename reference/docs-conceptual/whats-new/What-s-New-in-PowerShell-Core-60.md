# <a name="whats-new-in-powershell-core-60"></a>Vad är nytt i PowerShell Core 6.0

[PowerShell Core 6.0] [ github] är en ny version av PowerShell som har flera plattformar (Windows, Linux och macOS), öppen källkod och byggda för heterogena miljöer och i hybridmoln.

## <a name="moved-from-net-framework-to-net-core"></a>Flyttas från .NET Framework till .NET Core

PowerShell Core använder [.NET Core 2.0][] som dess runtime.
.NET core 2.0 aktiverar PowerShell Core ska fungera på flera plattformar (Windows, Linux och macOS).
PowerShell Core visar också API-uppsättningen som erbjuds av .NET Core 2.0 som ska användas i PowerShell-cmdlets och skript.

Windows PowerShell används .NET Framework-körning som värd för PowerShell-motorn.
Detta innebär att Windows PowerShell visar API-uppsättningen som erbjuds av .NET Framework.

API: er som delas mellan .NET Core och .NET Framework har definierats som en del av [.NET Standard][].

Mer information om hur detta påverkar skriptet och module kompatibilitet mellan PowerShell Core- och Windows PowerShell finns [Backwards kompatibilitet med Windows PowerShell](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>Stöd för macOS- och Linux

PowerShell officiellt stöder nu macOS- och Linux, inklusive:

- Windows 7, 8.1 och 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Windows Server semikolon mellan årligt kanal][semi-annual]
- Ubuntu 14.04 16.04 och nr 17.04 från
- Debian 8.7 + och 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25, 26
- macOS 10.12+

Gruppen har också bidragit paket för följande plattformar, men de officiellt stöds inte:

- Arkitektur Linux
- Kali Linux
- AppImage (fungerar på flera plattformar för Linux)

Vi har också experiment (som inte stöds) versioner för följande plattformar:

- Windows på ARM32/ARM64
- Raspbian (Stretch)

Många ändringar gjordes i PowerShell Core 6.0 så att det fungerar bättre för icke-Windows-datorer.
Vissa av dessa bryter ändringar som påverkar också Windows.
Andra är bara finns eller så är tillämpligt i icke-Windows-installationer av PowerShell Core.

- Tillagt stöd för inbyggda kommandot globbing på Unix-plattformar.
- Den `more` funktioner respekterar Linux `$PAGER` och som standard `less`.
  Det innebär att du kan nu använda jokertecken med interna binärfiler-kommandon (till exempel `ls *.txt`). (#3463)
- Avslutande omvänt hoppas automatiskt när du hanterar interna kommandoargumenten. (#4965)
- Ignorera den `-ExecutionPolicy` växeln när du kör PowerShell på Windows-plattformar eftersom skriptet signering inte stöds för närvarande. (#3481)
- Fast ConsoleHost ta hänsyn till `NoEcho` på Unix-plattformar. (#3801)
- Fast `Get-Help` att stödja skiftlägesokänslig matchning på Unix-plattformar. (#3852)
- `powershell` man-sidan som lagts till i paketet

### <a name="logging"></a>Loggning

I macOS, PowerShell använder ursprungligt `os_log` API: er för att logga på Apples [unified loggning system][os_log].
På Linux, PowerShell använder [Syslog][], en vanlig loggning lösning.

### <a name="filesystem"></a>Filsystem

Flera ändringar har gjorts i macOS och Linux att stödja filnamnstecken traditionellt inte stöds i Windows:

- Sökvägar till cmdlets är nu snedstreck-oberoende (både / och \ fungerar som katalogavgränsare)
- XDG Base Directory specifikation är nu respekteras och används som standard:
  - Linux/macOS profilsökvägen finns i `~/.config/powershell/profile.ps1`
  - Historik spara sökvägen finns i `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - Modul-sökväg användare finns i `~/.local/share/powershell/Modules`
- Stöd för fil- och namn som innehåller kolon på Unix. (#4959)
- Stöd för Skriptnamn eller fullständiga sökvägar med kommatecken. (#4136) (Tack till @TimCurwick!)
- Identifiera när `-LiteralPath` används för att undertrycka jokertecken expansion för navigering-cmdlets. (#5038)
- Uppdatera `Get-ChildItem` ska fungera flera liknande det * nix `ls -R` och Windows `DIR /S` inbyggda kommandon.
  `Get-ChildItem` Returnerar nu symboliska länkar påträffades under en rekursiv sökning och inte i katalogerna som mål för dessa länkar. (#3780)

### <a name="case-sensitivity"></a>Skiftlägeskänslighet

Linux- och macOS brukar vara skiftlägeskänsliga när Windows är skiftlägeskänsliga och behålla skiftläge.
I allmänhet är PowerShell inte skiftlägeskänsligt.

Till exempel miljövariabler är skiftlägeskänsliga i macOS och Linux, därför skiftläge för den `PSModulePath` miljövariabeln har standardiserats. (#3255) `Import-Module` är skiftlägeskänsligt när den använder en sökväg till filen för att fastställa modulens namn. (#5097)

## <a name="support-for-side-by-side-installations"></a>Stöd för sida vid sida-installationer

PowerShell Core installeras, konfigureras och körs separat från Windows PowerShell.
PowerShell Core har en ”bärbar” ZIP-paketet.
I ZIP-paketet kan installera du valfritt antal versioner var som helst på disken, inklusive lokal till ett program som använder PowerShell som ett beroende.
Sida-vid-sida-installation gör det enklare att testa nya versioner av PowerShell och migrera befintliga skript över tid.
Sida-vid-sida kan också bakåtkompatibilitet kompatibilitet som kan vara Fäst skript på specifika versioner som de kräver.

> [!NOTE]
> Som standard har MSI-baserade installationsprogrammet för Windows installera en uppdatering på plats.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>Byta namn på `powershell(.exe)` till `pwsh(.exe)`

Det binära namnet för PowerShell Core har ändrats från `powershell(.exe)` till `pwsh(.exe)`.
Den här ändringen kan deterministiska för användare att köra PowerShell Core på datorer som stöder sida-vid-sida Windows PowerShell och PowerShell Core-installationer.
`pwsh` är också mycket kortare och enklare att skriva.

Ytterligare ändringar `pwsh(.exe)` från `powershell.exe`:

- Ändra den första namngivna parametern från `-Command` till `-File`.
  Den här ändringen åtgärdas användningen av `#!` (aka som shebang) i PowerShell-skript som körs från icke-PowerShell-gränssnitt på Windows-plattformar.
  Det innebär också att du kan köra kommandon som `pwsh foo.ps1` eller `pwsh fooScript` utan att ange `-File`.
  Den här ändringen kräver dock att du anger explicit `-c` eller `-Command` vid försök att köra kommandon som `pwsh.exe -Command Get-Command`. (#4019)
- PowerShell Core accepterar den `-i` (eller `-Interactive`) växel för att indikera en interaktiv shell. (#3558) Detta gör att PowerShell som ska användas som ett standardgränssnitt på Unix-plattformar.
- Ta bort parametrar `-importsystemmodules` och `-psconsoleFile` från `pwsh.exe`. (#4995)
- Ändra `pwsh -version` och inbyggd hjälp för `pwsh.exe` ska justeras med andra inbyggda verktyg. (#4958 & #4931) (Tack @iSazonov)
- Ogiltigt argument felmeddelanden för `-File` och `-Command` och slutkoder som är förenligt med Unix-standarder (#4573)
- Lägga till `-WindowStyle` parameter i Windows. (#4573) Paket-baserade installationer uppdateringar på Windows-plattformar är på samma sätt in-place Update.

## <a name="backwards-compatibility-with-windows-powershell"></a>Bakåtkompatibilitet kompatibilitet med Windows PowerShell

Målet med PowerShell Core är förblir som kompatibel som möjligt med Windows PowerShell.
PowerShell Core använder [.NET Standard][] 2.0 för att ge binära kompatibilitet med befintliga .NET-sammansättningar.
Många PowerShell-moduler är beroende av dessa paket (ofta tider DLL-filer), så .NET Standard innebär att de kan fortsätta att arbeta med .NET Core.
PowerShell Core innehåller också en tumregel ska sökas i välkända mappar--som där den globala sammansättningscachen normalt finns på disken--för att hitta DLL-filen för .NET Framework-beroenden.

Du kan lära dig mer om .NET Standard på den [.NET-bloggen][], i det här [YouTube][] video- och via detta [vanliga frågor och svar][] på GitHub.

Ansträngningar har gjorts för att säkerställa att PowerShell-moduler för språk och ”inbyggd” (t.ex. `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`osv) fungerar på samma sätt som i Windows PowerShell.
I många fall med hjälp av gemenskapen, vi har lagt till nya funktionerna och korrigeringarna till dessa cmdletar.
I vissa fall på grund av ett saknat beroende i den underliggande .NET lager funktioner har tagits bort eller inte tillgänglig.

De flesta av de moduler som levereras som en del av Windows (till exempel `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`osv) och andra Microsoft-produkter inklusive Azure och Office har inte varit *explicit* portar till. NET Core ännu.
PowerShell-teamet arbetar med dessa grupper och grupper för att validera och porten sina befintliga PowerShell Core-moduler.
Med .NET Standard och [CDXML][]många av dessa traditionella Windows PowerShell-moduler verkar fungerar i PowerShell Core, men de har formellt verifierats och de formellt stöds inte.

Genom att installera den [ `WindowsPSModulePath` ] [ windowspsmodulepath] modulen, kan du använda Windows PowerShell-moduler genom att lägga till Windows PowerShell `PSModulePath` till PowerShell-kärna `PSModulePath`.

Installera först den `WindowsPSModulePath` modul från PowerShell-galleriet:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin 
Install-Module WindowsPSModulePath -Force
```

När du installerar den här modulen, kör du den `Add-WindowsPSModulePath` för att lägga till Windows PowerShell `PSModulePath` till PowerShell kärnor:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Docker-support

PowerShell Core lägger till stöd för Docker-behållare för alla större plattformar som stöder vi (inklusive flera Linux-distributioner, Windows Server Core och Nano Server).

En fullständig lista över kolla taggar på [ `microsoft/powershell` Docker NAV][docker-hub].
Mer information om Docker och PowerShell Core finns [Docker][] på GitHub.

## <a name="ssh-based-powershell-remoting"></a>SSH-baserad PowerShell-fjärrkommunikation

PowerShell fjärrkommunikation Protocol (PSRP) fungerar nu med protokollet SSH (Secure Shell) utöver traditionella WinRM-baserade PSRP.

Det innebär att du kan använda cmdlets som `Enter-PSSession` och `New-PSSession` och autentisera med hjälp av SSH.
Allt du behöver göra är att registrera PowerShell som ett delsystem med en OpenSSH-baserade SSH-server och du kan använda din befintliga SSH-baserad autentisering mekanismer (till exempel lösenord eller privata nycklar) med de traditionella `PSSession` semantik.

Mer information om hur du konfigurerar och använder SSH-baserad fjärrkommunikation finns [PowerShell-fjärrkommunikation via SSH][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom"></a>Standardkodning är UTF-8 utan en struktur

I tidigare Windows PowerShell-cmdlets som `Get-Content`, `Set-Content` används olika kodningar, till exempel ASCII- och UTF-16.
Variationen i används som standard skapas problem när blanda cmdlets utan att ange en kodning.

Icke-Windows-plattformar använder traditionellt UTF-8 utan en Byte ordning markering (BOM) som standardkodning för textfiler.
Flera Windows-program och verktyg är glidande från UTF-16 och mot BOM mindre UTF-8-kodning.
PowerShell Core ändras den standardkodning som överensstämmer med bredare ekosystem.

Detta innebär att alla inbyggda cmdlet: ar som använder den `-Encoding` parametern används den `UTF8NoBOM` värde som standard.
Följande cmdlets som påverkas av den här ändringen:

- Add-Content
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- Ny ModuleManifest
- Out-File
- Välj sträng
- Skicka MailMessage
- Set-Content

Dessa cmdletar har också uppdaterats så att den `-Encoding` parametern accepterar universellt `System.Text.Encoding`.

Standardvärdet för `$OutputEncoding` har också ändrats till UTF-8.

Som bästa praxis bör du uttryckligen ange kodningar i skript med hjälp av den `-Encoding` parametern för att skapa deterministiska beteende mellan olika plattformar.

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Stöd för backgrounding för pipelines med et-tecken (`&`) (#3360)

Placera `&` i slutet av en pipeline orsakar pipelinen ska köras som ett PowerShell-jobb.
När en pipeline backgrounded, returneras ett jobbobjekt.
När pipelinen körs som ett jobb, alla standardprogram `*-Job` cmdlets kan användas för att hantera jobbet.
Variabler (ignoreras processpecifika variabler) används i pipeline kopieras automatiskt till jobbet så `Copy-Item $foo $bar &` helt enkelt fungerar.
Jobbet körs också i den aktuella katalogen i stället för användarens hemkatalog.
Mer information om PowerShell jobb finns [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).

## <a name="semantic-versioning"></a>Semantiska versionshantering

- Gjorts `SemanticVersion` kompatibel med `SemVer 2.0`. (#5037) (Tack @iSazonov!)
- Ändra standard `ModuleVersion` i `New-ModuleManifest` till `0.0.1` att justera SemVer. (#4842) (Tack @LDSpits)
- Lägga till `semver` som en typ snabbtangenten för `System.Management.Automation.SemanticVersion`. (#4142) (Tack till @oising!)
- Aktiverad jämförelse mellan en `SemanticVersion` instans och en `Version` -instans som har skapats med `Major` och `Minor` Versionsvärden.

## <a name="language-updates"></a>Språkuppdateringar

- Implementera Unicode-escape-parsning så att användarna kan använda Unicode-tecken som argument, strängar eller variabelnamn. (#3958) (Tack till @rkeithhill!)
- Tillagda nya escape-tecknet för ESC: `` `e``
- Tillagt stöd för konvertering av uppräkningar att sträng (#4318) (tack @KirkMunro)
- Fast omvandling enstaka element matris till en allmän samling. (#3170)
- Tillagda tecknet område överlagring för den `..` operator, så `'a'..'z'` returnerar tecken från ”a” till ”z”. (#5026) (Tack @IISResetMe!)
- Fast variabeltilldelning inte skriva över skrivskyddade variabler
- Push-lokala över automatiska variabler till 'DottedScopes' när över hela skriptet cmdlets (#4709)
- Aktivera 'Singleline, lambda-alternativet i delningsoperatorn (#4721) (tack @iSazonov)

## <a name="engine-updates"></a>Uppdateringar

- `$PSVersionTable` har fyra nya egenskaper:
  - `PSEdition`: Det här värdet `Core` på PowerShell Core och `Desktop` på Windows PowerShell
  - `GitCommitId`: Det är Git commit-ID på Git branch eller taggen där PowerShell har skapats.
    På utgivna versioner, sannolikt blir samma som `PSVersion`.
  - `OS`: Det är en sträng för OS-version som returneras av `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: Det har returnerats av `[System.Environment]::OSVersion.Platform` anges till `Win32NT` i Windows, `MacOSX` på macOS, och `Unix` på Linux.
- Ta bort den `BuildVersion` egenskap från `$PSVersionTable`.
  Den här egenskapen har starkt knutna till Windows-versionen.
  I stället rekommenderar vi att du använder `GitCommitId` att hämta PowerShell Core exakta versionen. (#3877) (Tack till @iSazonov!)
- Ta bort `ClrVersion` egenskap från `$PSVersionTable`.
  Den här egenskapen är inte relevant för .NET Core och har endast bevaras i .NET Core för specifika äldre ändamål som är inte tillämpligt för PowerShell.
- Lägga till tre nya automatiska variabler för att avgöra om PowerShell körs i en given OS: `$IsWindows`, `$IsMacOs`, och `$IsLinux`.
- Lägg till `GitCommitId` för PowerShell Core.
  Nu slipper du kör `$PSVersionTable` när du startar PowerShell för att få version! (#3916) (Tack till @iSazonov!)
- Lägg till en JSON-konfigurationsfil som kallas `powershell.config.json` i `$PSHome` att lagra vissa inställningar som krävs innan starten (t.ex. `ExecutionPolicy`).
- Blockera inte pipeline när du kör Windows EXE
- Aktiverade uppräkning av COM-samlingar. (#4553)

## <a name="cmdlet-updates"></a>Cmdlet-uppdateringar

### <a name="new-cmdlets"></a>Nya cmdlet: ar

- Lägg till `Get-Uptime` till `Microsoft.PowerShell.Utility`.
- Lägg till `Remove-Alias` kommando. (#5143) (Tack @PowershellNinja!)
- Lägg till `Remove-Service` till Management-modulen. (#4858) (Tack @joandrsn!)

### <a name="web-cmdlets"></a>-Cmdletar

- Lägga till stöd för autentisering av certifikat för web-cmdletar. (#4646) (Tack @markekraus)
- Lägga till stöd för innehållshuvuden-cmdletar. (#4494 & #4640) (Tack @markekraus)
- Lägga till stöd för flera länken huvud-cmdletar. (#5265) (Tack @markekraus!)
- Stöder länk sidhuvud sidbrytning i web-cmdletar (#3828)
  - För `Invoke-WebRequest`när svaret innehåller ett huvud för länken som vi skapa en RelationLink-egenskap som en ordlista som representerar URL: er och `rel` attribut och kontrollera URL: er är absolut att göra det enklare för utvecklare att använda.
  - För `Invoke-RestMethod`när svaret innehåller ett huvud för länken som vi exponera en `-FollowRelLink` växla till automatiskt `next` `rel` länkar tills de inte längre finns eller en gång vi nådde den valfria `-MaximumFollowRelLink` parametervärdet.
- Lägg till `-CustomMethod` parameter för-cmdletar för att tillåta för icke-standard metoden verb. (#3142) (Tack till @Lee303!)
- Lägg till `SslProtocol` stöd till Web-cmdletar. (#5329) (Tack @markekraus!)
- Lägg till Multipart-cmdletar-supporten. (#4782) (Tack @markekraus)
- Lägg till `-NoProxy` till web-cmdletar så att de ignorerar hela systemets proxyinställningar. (#3447) (Tack till @TheFlyingCorpse!)
- Användaren Agent-cmdletar rapporterar nu OS-plattform (#4937) (tack @LDSpits)
- Lägg till `-SkipHeaderValidation` växla till web-cmdlets med stöd för att lägga till huvuden utan att verifiera huvudets värde. (#4085)
- Aktivera web cmdletar inte kan validera HTTPS-certifikat på servern om det behövs.
- Lägg till autentiseringsparametrar-cmdletar. (#5052) (Tack @markekraus)
  - Lägg till `-Authentication` som tillhandahåller tre alternativ: Basic, OAuth och innehavaren.
  - Lägg till `-Token` att hämta innehavaren token för OAuth och ägar-alternativ.
  - Lägg till `-AllowUnencryptedAuthentication` kringgå autentisering som tillhandahålls för eventuella transportschema än HTTPS.
- Lägg till `-ResponseHeadersVariable` till `Invoke-RestMethod` att infångandet av svarshuvuden. (#4888) (Tack @markekraus)
- Åtgärda-cmdletar för att inkludera HTTP-svaret i undantaget när Svarets statuskod inte lyckades. (#3201)
- Ändra-cmdletar för `UserAgent` från `WindowsPowerShell` till `PowerShell`. (#4914) (Tack @markekraus)
- Lägg till explicita `ContentType` identifiering för `Invoke-RestMethod` (#4692)
- Åtgärda-cmdletar för `-SkipHeaderValidation` att arbeta med standardmässiga användaragent huvuden. (#4479 & #4512) (Tack @markekraus)

### <a name="json-cmdlets"></a>JSON-cmdlets

- Lägg till `-AsHashtable` till `ConvertFrom-Json` att returnera en `Hashtable` i stället. (#5043) (Tack @bergmeister!)
- Använd prettier formaterare med `ConvertTo-Json` utdata. (#2787) (Tack till @kittholland!)
- Lägg till `Jobject` serialisering stöd till `ConvertTo-Json`. (#5141)
- Åtgärda `ConvertFrom-Json` att deserialisera en matris med strängar som tillsammans skapar en fullständig JSON-sträng från pipeline.
  Det löser tillfällen där radmatningar bäddas skulle bryta JSON-parsning. (#3823)
- Ta bort den `AliasProperty "Count"` har definierats för `System.Array`.
  Detta tar bort de extra `Count` egenskapen på vissa `ConvertFrom-Json` utdata. (#3231) (Tack till @PetSerAl!)

### <a name="csv-cmdlets"></a>CSV-cmdlets

- Lägg till `PSTypeName` stöd för `Import-Csv` och `ConvertFrom-Csv`. (#5389) (Tack @markekraus!)
- Se `Import-Csv` stöder `CR`, `LF`, och `CRLF` som rad avgränsare. (#5363) (Tack @iSazonov!)
- Se `-NoTypeInformation` standard på `Export-Csv` och `ConvertTo-Csv`. (#5164) (Tack @markekraus)

### <a name="service-cmdlets"></a>Cmdlet: ar

- Lägga till egenskaper `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName`, och `StartupType` till den `ServiceController` objekt som returnerats av `Get-Service`. (#4907) (Tack @joandrsn)
- Lägg till funktioner för att ange autentiseringsuppgifter på `Set-Service` kommando. (#4844) (Tack @joandrsn)

### <a name="other-cmdlets"></a>Andra cmdlet: ar

- Lägg till en parameter till `Get-ChildItem` kallas `-FollowSymlink` som passerar symlinks på begäran med kontroller för länken slingor. (#4020)
- Uppdatera `Add-Type` att stödja `CSharpVersion7`. (#3933) (Tack till @iSazonov)
- Ta bort den `Microsoft.PowerShell.LocalAccounts` modulen följd av användningen av stöds inte API: er tills en bättre lösning hittas. (#4302)
- Ta bort den `*-Counter` cmdlets i `Microsoft.PowerShell.Diagnostics` följd av användningen av stöds inte API: er tills en bättre lösning hittas. (#4303)
- Lägga till stöd för `Invoke-Item -Path <folder>`. (#4262)
- Lägg till `-Extension` och `-LeafBase` växlar till `Split-Path` så att du kan dela sökvägar mellan filnamnstillägget och resten av filnamnet. (#2721) (Tack till @powercode!)
- Lägg till parametrar `-Top` och `-Bottom` till `Sort-Object` för översta/nedersta N sortera
- Exponera en process överordnade processen genom att lägga till den `CodeProperty "Parent"` till `System.Diagnostics.Process`. (#2850) (Tack till @powercode!)
- Använda MB i stället KB för minne kolumner i `Get-Process`
- Lägg till `-NoNewLine` växla för `Out-String`. (#5056) (Tack @raghav710)
- `Move-Item` cmdlet godkänner `-Include`, `-Exclude`, och `-Filter` parametrar. (#3878)
- Tillåt `*` som ska användas i registersökvägen för `Remove-Item`. (#4866)
- Lägg till `-Title` till `Get-Credential` och enhetlig fråga upplevelsen olika plattformar.
- Lägg till den `-TimeOut` parameter till `Test-Connection`. (#2492)
- `Get-AuthenticodeSignature` cmdlets kan nu hämta signatur-filtidsstämpel. (#4061)
- Ta bort stöds inte `-ShowWindow` växla från `Get-Help`. (#4903)
- Åtgärda `Get-Content -Delimiter` att inte inkludera avgränsaren i matriselementen returnerade (#3706) (tack @mklement0)
- Lägg till `Meta`, `Charset`, och `Transitional` parametrar för att `ConvertTo-HTML` (#4184) (tack @ergo3114)
- Lägg till `WindowsUBR` och `WindowsVersion` egenskaper till `Get-ComputerInfo` resultat
- Lägg till `-Group` parameter till `Get-Verb`
- Lägg till `ShouldProcess` stöd till `New-FileCatalog` och `Test-FileCatalog` (åtgärdas `-WhatIf` och `-Confirm`). (#3074) (Tack till @iSazonov!)
- Lägg till `-WhatIf` växla till `Start-Process` cmdlet (#4735) (tack @sarithsutha)
- Lägg till `ValidateNotNullOrEmpty` för många befintliga parametrar.

## <a name="tab-completion"></a>Flikavslutande

- Förbättrad typhärledning i flikavslutande baserat på variabelvärden för körning. (#2744) (Tack till @powercode!) Detta gör att flikavslutande i situationer som:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Lägg till Hashtable flikavslutande för `-Property` av `Select-Object`. (#3625) (Tack till @powercode)
- Aktivera argumentet automatisk komplettering för `-ExcludeProperty` och `-ExpandProperty` av `Select-Object`. (#3443) (Tack till @iSazonov!)
- Åtgärda ett programfel i flikavslutande att göra `native.exe --<tab>` anropar intern slutföra. (#3633) (Tack till @powercode!)

## <a name="breaking-changes"></a>Gör ändringar

Vi har introducerat ett antal viktiga förändringar i PowerShell Core 6.0.
Du kan läsa mer om dem i detalj, se [gör ändringar i PowerShell Core 6.0][breaking-changes].

## <a name="debugging"></a>Felsökning

- Stöd för step-in fjärrfelsökning för `Invoke-Command -ComputerName`. (#3015)
- Aktivera binder felsökningsloggning i PowerShell Core

## <a name="filesystem-updates"></a>Filsystem-uppdateringar

- Aktivera användning av filsystem-provider från en UNC-sökväg. ($4998)
- `Split-Path` nu fungerar med UNC-rötter
- `cd` utan argument nu fungerar som `cd ~`
- Fast PowerShell Core som tillåter användning av sökvägar som är mer än 260 tecken långt. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Felkorrigeringar och kapacitetsförbättringar

Vi har gjort *många* förbättringar av prestanda i PowerShell, bland annat i starten, olika inbyggda cmdlet: ar och interaktion med interna binärfiler.

Vi har också ett antal åtgärdade buggar i PowerShell Core.
En fullständig lista över korrigeringar och ändringar kolla vår [changelog][] på GitHub.

## <a name="telemetry"></a>Telemetri

- PowerShell Core 6.0 läggs telemetri till konsolen värden till rapporten två värden (#3620):
  - OS-plattform (`$PSVersionTable.OSDescription`)
  - exakt vilken version av PowerShell (`$PSVersionTable.GitCommitId`)

Om du vill välja bort den här telemetri bara ta bort `$PSHome\DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` eller skapa `POWERSHELL_TELEMETRY_OPTOUT` miljövariabel med något av följande värden: `true`, `1` eller `yes`.
Ta bort den här filen eller variabeln kringgår all telemetri även före första gången du kör PowerShell.
Vi planerar också på att exponera informationen telemetri och insikter som vi glean från telemetri i den [community instrumentpanelen][community-dashboard].
Du hittar mer information om hur vi kan använda informationen i det här [blogginlägget][telemetry-blog].

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/en-us/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: https://github.com/PowerShell/PowerShell/tree/master/docs/BREAKINGCHANGES.md
[changelog]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[Standard för .NET]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET-bloggen]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[vanliga frågor och svar]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
