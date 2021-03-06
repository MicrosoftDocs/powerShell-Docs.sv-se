---
title: Nyheter i PowerShell Core 6,0
description: Nya funktioner och ändringar som lanseras i PowerShell Core 6,0
ms.date: 08/06/2018
ms.openlocfilehash: 18650733117d81e3b8d714960b95b4921122ed32
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96840154"
---
# <a name="whats-new-in-powershell-core-60"></a>Nyheter i PowerShell Core 6,0

[PowerShell Core 6,0][github] är en ny version av PowerShell som är plattforms oberoende (Windows, MacOS och Linux), öppen källkod och byggd för heterogena miljöer och hybrid molnet.

## <a name="moved-from-net-framework-to-net-core"></a>Flyttad från .NET Framework till .NET Core

PowerShell Core använder [.net core 2,0][] som dess körnings miljö. .NET Core 2,0 gör det möjligt för PowerShell Core att arbeta på flera plattformar (Windows, macOS och Linux). PowerShell-kärnan exponerar även den API-uppsättning som erbjuds av .NET Core 2,0 som ska användas i PowerShell-cmdlets och skript.

Windows PowerShell använde .NET Framework runtime som värd för PowerShell-motorn. Det innebär att Windows PowerShell exponerar den API-uppsättning som erbjuds av .NET Framework.

De API: er som delas mellan .NET Core och .NET Framework definieras som en del av [.net standard][].

Mer information om hur detta påverkar kompatibilitet mellan moduler och skript mellan PowerShell Core och Windows PowerShell finns i [bakåtkompatibla kompatibilitet med Windows PowerShell](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>Stöd för macOS och Linux

PowerShell stöder nu officiellt macOS och Linux, inklusive:

- Windows 7, 8,1 och 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Windows Server Semi-Annual-kanal][semi-annual]
- Ubuntu 14,04, 16,04 och 17,04
- Debian 8,7 + och 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42,2
- Fedora 25, 26
- macOS 10.12 +

Vår community har också bidragit med paket för följande plattformar, men de stöds inte officiellt:

- Båge Linux
- Kali Linux
- AppImage (fungerar på flera Linux-plattformar)

Vi har även stöd för experimentella utgåvor för följande plattformar:

- Windows på ARM32/ARM64
- Raspbian (sträck ut)

Ett antal ändringar gjordes i PowerShell Core 6,0 för att det ska fungera bättre på andra system än Windows. Några av dessa är ändringar som också påverkar Windows. Andra är endast närvarande eller tillämpliga i icke-Windows-installationer av PowerShell Core.

- Stöd har lagts till för globbing för inbyggda kommandon på UNIX-plattformar.
- `more`Funktionerna respekterar Linux `$PAGER` och standardvärdet `less` . Det innebär att du nu kan använda jokertecken med interna binärfiler/kommandon (till exempel `ls *.txt` ). (#3463)
- Avslutande omvänt snedstreck undantas automatiskt vid hantering av interna kommando argument. (#4965)
- Ignorera `-ExecutionPolicy` växeln när du kör PowerShell på plattformar som inte är Windows-plattformar eftersom skript signering inte stöds för närvarande. (#3481)
- Fast ConsoleHost för att respektera `NoEcho` UNIX-plattformar. (#3801)
- Åtgärdat `Get-Help` till support Skift läges okänslig mönster matchning på UNIX-plattformar. (#3852)
- `powershell` man – sidan har lagts till i paketet

### <a name="logging"></a>Loggning

I macOS använder PowerShell inbyggda `os_log` API: er för att logga in på Apples [enhetlig loggnings system][os_log]. I Linux använder PowerShell [syslog][], en lösning för allmänt förekommande-loggning.

### <a name="filesystem"></a>Filsystem

Ett antal ändringar har gjorts på macOS och Linux för att stödja fil namns tecken som inte traditionellt stöds i Windows:

- Sökvägar som ges till cmdlets är nu snedstreck-oberoende (både/och \ fungerar som katalog avgränsare)
- XDG-bas katalog specifikationen respekteras nu och används som standard:
  - Profil Sök vägen för Linux/macOS finns på `~/.config/powershell/profile.ps1`
  - Historikens sparade sökväg finns på `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - Sökvägen till användar modulen finns på `~/.local/share/powershell/Modules`
- Stöd för fil-och mappnamn som innehåller kolon-tecknet i UNIX. (#4959)
- Stöd för skript namn eller fullständiga sökvägar som innehåller kommatecken. (#4136) (Tack till [@TimCurwick](https://github.com/TimCurwick) !)
- Identifiera när `-LiteralPath` används för att utelämna expansion av jokertecken för navigerings-cmdletar. (#5038)
- Uppdaterat `Get-ChildItem` för att fungera mer som * nix `ls -R` och inbyggda Windows- `DIR /S` kommandon. `Get-ChildItem` returnerar nu de symboliska länkar som påträffades under en rekursiv sökning och söker inte igenom de kataloger som dessa länkar riktar sig mot. (#3780)

### <a name="case-sensitivity"></a>Skift läges känslighet

Linux och macOS tenderar att vara Skift läges känsliga medan Windows är Skift läges känsligt och bevarar Skift läge.
I allmänhet är PowerShell Skift läges okänsligt.

Miljövariabler är till exempel Skift läges känsliga på macOS och Linux, vilket innebär att `PSModulePath` miljövariabeln inte har standardiserats. (#3255) `Import-Module` är Skift läges okänslig när den använder en fil Sök väg för att fastställa modulens namn. (#5097)

## <a name="support-for-side-by-side-installations"></a>Stöd för installation sida vid sida

PowerShell Core installeras, konfigureras och körs separat från Windows PowerShell.
PowerShell-kärnan har ett "Portable" ZIP-paket. Med ZIP-paketet kan du installera valfritt antal versioner var som helst på disken, inklusive lokalt till ett program som använder PowerShell som ett beroende.
Vid sida-vid-sida-installation blir det enklare att testa nya versioner av PowerShell och migrera befintliga skript över tid. Sida-vid-sida aktiverar också bakåtkompatibilitet som skript kan fästas på vissa versioner som de behöver.

> [!NOTE]
> Som standard installerar MSI-baserade installations program på Windows en uppdatering på plats.

## <a name="renamed-powershellexe-to-pwshexe"></a>`powershell(.exe)` har bytt namn till `pwsh(.exe)`

Det binära namnet för PowerShell Core har ändrats från `powershell(.exe)` till `pwsh(.exe)` . Den här ändringen är ett deterministiskt sätt för användarna att köra PowerShell Core på datorer för att stödja Windows PowerShell-och PowerShell-installationer sida vid sida. `pwsh` är också mycket kortare och enklare att skriva.

Ytterligare ändringar av `pwsh(.exe)` från `powershell.exe` :

- Den första positions parametern har ändrats från `-Command` till `-File` . Den här ändringen åtgärdar användningen av `#!` (aka som en Shebang) i PowerShell-skript som körs från icke-PowerShell-gränssnitt på andra plattformar än Windows-plattformar. Det innebär också att du kan köra kommandon som `pwsh foo.ps1` eller `pwsh fooScript` utan att ange `-File` . Den här ändringen kräver dock att du uttryckligen anger `-c` eller `-Command` när du försöker köra kommandon som `pwsh.exe -Command Get-Command` .
  (#4019)
- PowerShell-kärnan godkänner `-i` (eller `-Interactive` ) växeln för att ange ett interaktivt gränssnitt.
  (#3558) Detta gör att PowerShell kan användas som standard gränssnitt på UNIX-plattformar.
- Parametrar och från har tagits bort `-importsystemmodules` `-psconsoleFile` `pwsh.exe` . (#4995)
- Ändrad `pwsh -version` och inbyggd hjälp för `pwsh.exe` att justera med andra inbyggda verktyg. (#4958 & #4931) (Tack [@iSazonov](https://github.com/iSazonov) )
- Ogiltiga argument fel meddelanden för `-File` och `-Command` och avsluta koder som är konsekventa med UNIX-standarder (#4573)
- Parametern har lagts till `-WindowStyle` i Windows. (#4573) På samma sätt är paketbaserade installationer som inte är Windows-plattformar uppdateringar på plats.

## <a name="backwards-compatibility-with-windows-powershell"></a>Bakåtkompatibilitet med Windows PowerShell

Målet med PowerShell Core är att vara så kompatibelt som möjligt med Windows PowerShell.
PowerShell Core använder [.net Standard][] 2,0 för att ge binär kompatibilitet med befintliga .net-sammansättningar. Många PowerShell-moduler är beroende av dessa sammansättningar (ofta gånger DLL-filer), så .NET standard gör det möjligt för dem att fortsätta arbeta med .NET Core. PowerShell Core innehåller också en tumregel för att titta på välkända mappar, t. ex. när den globala sammansättningscachen vanligt vis finns på disk-för att hitta .NET Framework DLL-beroenden.

Du kan lära dig mer om .NET-standarden i [.net-bloggen][], i den här [YouTube][] -videon och via dessa [vanliga frågor och svar][] om GitHub.

Bästa ansträngningar har gjorts för att säkerställa att PowerShell-språket och "inbyggda" moduler (t. ex `Microsoft.PowerShell.Management` `Microsoft.PowerShell.Utility` ., osv.) fungerar på samma sätt som i Windows PowerShell. I många fall har vi lagt till nya funktioner och fel korrigeringar för dessa cmdlets med hjälp av communityn. I vissa fall, på grund av ett saknat beroende i underliggande .NET-lager, har funktionen tagits bort eller är inte tillgänglig.

De flesta moduler som levereras som en del av Windows (t. ex.,,, `DnsClient` `Hyper-V` `NetTCPIP` `Storage` osv.) och andra Microsoft-produkter, inklusive Azure och Office, har inte *uttryckligen* tilldelats .net Core än. PowerShell-teamet arbetar med dessa produkt grupper och team för att validera och Porta sina befintliga moduler till PowerShell Core. Med .NET standard och [cdxlm][], verkar många av dessa traditionella Windows PowerShell-moduler fungera i PowerShell Core, men de har inte formellt verifierats och de har inte formellt stöd.

Genom att installera [`WindowsPSModulePath`][windowspsmodulepath] modulen kan du använda Windows PowerShell-moduler genom att lägga till Windows PowerShell `PSModulePath` i PowerShell-kärnan `PSModulePath` .

Installera först `WindowsPSModulePath` modulen från PowerShell-galleriet:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

När du har installerat den här modulen kör du `Add-WindowsPSModulePath` cmdleten för att lägga till Windows PowerShell `PSModulePath` till PowerShell-kärnan:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Docker-stöd

PowerShell Core lägger till stöd för Docker-behållare för alla större plattformar som vi stöder (inklusive flera Linux-distributioner, Windows Server Core och Nano Server).

För en fullständig lista, se taggarna på [ `microsoft/powershell` Docker Hub][docker-hub]. Mer information om Docker-och PowerShell-kärnan finns i [Docker][] på GitHub.

## <a name="ssh-based-powershell-remoting"></a>SSH-baserad PowerShell-fjärrkommunikation

PowerShell Remoting-protokollet (PSRP) fungerar nu med SSH-protokollet (Secure Shell) förutom den traditionella WinRM-baserade PSRP.

Det innebär att du kan använda cmdletar som `Enter-PSSession` och `New-PSSession` och AUTENTISERA med SSH. Allt du behöver göra är att registrera PowerShell som ett under system med en OpenSSH-baserad SSH-server och du kan använda dina befintliga SSH-baserade autentiserande mekanismer (t. ex. lösen ord eller privata nycklar) med traditionella `PSSession` semantik.

Mer information om hur du konfigurerar och använder SSH-baserad fjärr kommunikation finns i [PowerShell-fjärrkommunikation via SSH][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom-except-for-new-modulemanifest"></a>Standard kodning är UTF-8 utan en BOM förutom för New-ModuleManifest

Tidigare var Windows PowerShell-cmdletar som `Get-Content` , som `Set-Content` använder olika kodningar, t. ex. ASCII och UTF-16. Var Ian sen i kodnings standardvärden skapade problem när du blandar cmdletar utan att ange en kodning.

Plattformar som inte är Windows-plattformar använder traditionellt UTF-8 utan ett byte ordnings tecken (BOM) som standard kodning för textfiler. Fler Windows-program och-verktyg flyttas bort från UTF-16 och mot BOM-mindre UTF-8-kodning. PowerShell Core ändrar standard kodningen så att den överensstämmer med de bredare eko systemen.

Det innebär att alla inbyggda cmdlets som använder `-Encoding` parametern använder `UTF8NoBOM` värdet som standard. Följande cmdletar påverkas av den här uppdateringen:

- Add-Content
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- Out-File
- Select-String
- Send-MailMessage
- Set-Content

Dessa cmdletar har också uppdaterats så att `-Encoding` parametern kan accepteras universellt `System.Text.Encoding` .

Standardvärdet för `$OutputEncoding` har också ändrats till UTF-8.

Som bästa praxis bör du uttryckligen ställa in kodningar i skript med hjälp av `-Encoding` parametern för att skapa deterministiska beteenden på olika plattformar.

`New-ModuleManifest` cmdleten har ingen **encoding** -parameter. Kodningen för modul manifest filen (. psd1) som skapats med `New-ModuleManifest` cmdleten är beroende av miljön: om den är PowerShell Core som körs på Linux är kodningen UTF-8 (ingen BOM), annars är kodningen UTF-16 (med struktur). (#3940)

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Stöd för pipelines med et-tecken ( `&` ) (#3360)

Om du lägger till `&` slutet av en pipeline körs pipelinen som ett PowerShell-jobb. När en pipeline har ett bakgrunds objekt returneras ett jobb objekt. När pipelinen körs som ett jobb kan alla standard- `*-Job` cmdlets användas för att hantera jobbet. Variabler (ignorerar verksamhetsspecifika variabler) som används i pipelinen kopieras automatiskt till jobbet så att `Copy-Item $foo $bar &` bara fungerar. Jobbet körs också i den aktuella katalogen i stället för användarens Hem Katalog. Mer information om PowerShell-jobb finns [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).

## <a name="semantic-versioning"></a>Semantisk versionshantering

- Är `SemanticVersion` kompatibel med `SemVer 2.0` . (#5037) (Tack [@iSazonov](https://github.com/iSazonov) !)
- Standardvärdet `ModuleVersion` har ändrats i `New-ModuleManifest` så att det `0.0.1` överensstämmer med SemVer. (#4842) (Tack [@LDSpits](https://github.com/LDSpits) )
- Tillagt `semver` som typ Accelerator för `System.Management.Automation.SemanticVersion` . (#4142) (Tack till [@oising](https://github.com/oising) !)
- Aktive rad jämförelse mellan en `SemanticVersion` instans och en `Version` instans som endast är konstruerad med `Major` och `Minor` versions värden.

## <a name="language-updates"></a>Språk uppdateringar

- Implementera tolkning av Unicode-Escape så att användarna kan använda Unicode-tecken som argument, strängar eller variabel namn. (#3958) (Tack till [@rkeithhill](https://github.com/rkeithhill) !)
- Nytt escape-tecken har lagts till för ESC: `` `e``
- Stöd har lagts till för konvertering av uppräkningar till sträng (#4318) (tack [@KirkMunro](https://github.com/KirkMunro) )
- Fast data mat ris med en generisk samling. (#3170)
- Tecken intervallets överbelastning till `..` operatorn har lagts till, så `'a'..'z'` returnerar tecken från "a" till "ö". (#5026) (Tack [@IISResetMe](https://github.com/IISResetMe) !)
- Fast variabel tilldelning har inte Skriv över skrivskyddade variabler
- Push-överför lokala variabler för automatiska variabler till "DottedScopes" när du pekar på punkter för skript-cmdletar (#4709)
- Aktivera användning av alternativet "Singleline, Multiline" i Split-operatorn (#4721) (tack [@iSazonov](https://github.com/iSazonov) )

## <a name="engine-updates"></a>Motor uppdateringar

- `$PSVersionTable` har fyra nya egenskaper:
  - `PSEdition`: Detta är inställt `Core` på på PowerShell Core och `Desktop` i Windows PowerShell
  - `GitCommitId`: Det här är git-inchecknings-ID: t för git-grenen eller-taggen där PowerShell byggdes.
    På publicerade versioner är det troligt att det är detsamma som `PSVersion` .
  - `OS`: Det här är en OS-version som returneras av `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: Detta returneras av `[System.Environment]::OSVersion.Platform` det är inställt `Win32NT` på på Windows, `Unix` MacOS och `Unix` Linux.
- Egenskapen har tagits bort `BuildVersion` från `$PSVersionTable` . Den här egenskapen är starkt knuten till Windows build-versionen. I stället rekommenderar vi att du använder `GitCommitId` för att hämta den exakta versionen av PowerShell Core. (#3877) (Tack till [@iSazonov](https://github.com/iSazonov) !)
- Ta bort `ClrVersion` egenskap från `$PSVersionTable` . Den här egenskapen är irrelevant för .NET Core och bevarades bara i .NET Core för speciella äldre syfte som inte är tillgängliga för PowerShell.
- Tre nya automatiska variabler har lagts till för att avgöra om PowerShell körs i ett angivet operativ system: `$IsWindows` , `$IsMacOs` och `$IsLinux` .
- Lägg till `GitCommitId` i PowerShell Core-banderoll. Nu behöver du inte köra `$PSVersionTable` så snart du startar PowerShell för att hämta versionen! (#3916) (Tack till [@iSazonov](https://github.com/iSazonov) !)
- Lägg till en JSON-konfigurationsfil som kallas `powershell.config.json` i `$PSHome` för att lagra vissa inställningar som krävs före start tiden (t. ex. `ExecutionPolicy` ).
- Blockera inte pipelinen när Windows EXE körs
- Uppräkning av COM-samlingar har Aktiver ATS. (#4553)

## <a name="cmdlet-updates"></a>Cmdlet-uppdateringar

### <a name="new-cmdlets"></a>Nya cmdletar

- Lägg till `Get-Uptime` i `Microsoft.PowerShell.Utility` .
- Lägg till `Remove-Alias` kommando. (#5143) (Tack [@PowershellNinja](https://github.com/PowershellNinja) !)
- Lägg till `Remove-Service` i Management-modulen. (#4858) (Tack [@joandrsn](https://github.com/joandrsn) !)

### <a name="web-cmdlets"></a>Webb-cmdletar

- Lägg till stöd för certifikatautentisering för webb-cmdletar. (#4646) (Tack [@markekraus](https://github.com/markekraus) )
- Lägg till stöd för innehålls rubriker i webb-cmdletar. (#4494 & #4640) (Tack [@markekraus](https://github.com/markekraus) )
- Lägg till stöd för flera länkar till Web-cmdletar. (#5265) (Tack [@markekraus](https://github.com/markekraus) !)
- Stöd för länk huvuds sid brytning i webb-cmdlets (#3828)
  - För `Invoke-WebRequest` , när svaret innehåller ett länk huvud, skapar vi en RelationLink-egenskap som en ord lista som representerar URL: er och `rel` attribut och ser till att URL: erna är absoluta för att det ska bli lättare för utvecklaren att använda.
  - För `Invoke-RestMethod` , när svaret innehåller ett länk huvud, visar vi en `-FollowRelLink` växel för att automatiskt följa `next` `rel` länkar tills de inte längre finns eller när vi har nått det valfria `-MaximumFollowRelLink` parameter värdet.
- Lägg till `-CustomMethod` parametern till webb-cmdletar för att tillåta verb som inte är standard. (#3142) (Tack till @Lee303 !)
- Lägg till `SslProtocol` stöd för webb-cmdletar. (#5329) (Tack [@markekraus](https://github.com/markekraus) !)
- Lägg till multipart-stöd för Web-cmdletar. (#4782) (Tack [@markekraus](https://github.com/markekraus) )
- Lägg till `-NoProxy` i webb-cmdlets så att de ignorerar den systemomfattande proxyinställningarna. (#3447) (Tack till [@TheFlyingCorpse](https://github.com/TheFlyingCorpse) !)
- Användar agenten för Web-cmdlets rapporterar nu operativ system plattformen (#4937) (tack [@LDSpits](https://github.com/LDSpits) )
- Lägg till `-SkipHeaderValidation` switch till Web-cmdletar för att stödja tillägg av huvuden utan att verifiera Huvudvärdet. (#4085)
- Aktivera webb-cmdletar för att inte verifiera HTTPS-certifikatet för servern om det behövs.
- Lägg till autentiseringsmetoder till webb-cmdletar. (#5052) (Tack [@markekraus](https://github.com/markekraus) )
  - Lägg till `-Authentication` som innehåller tre alternativ: Basic, OAuth och Bearer.
  - Lägg till `-Token` för att hämta Bearer-token för OAuth-och Bearer-alternativ.
  - Lägg till `-AllowUnencryptedAuthentication` i kringgå autentisering som har angetts för något annat transport schema än https.
- Lägg till i `-ResponseHeadersVariable` `Invoke-RestMethod` för att aktivera insamlingen av svars rubriker.
  (#4888) (Tack [@markekraus](https://github.com/markekraus) )
- Korrigera webb-cmdletar för att inkludera HTTP-svaret i undantaget när svars status koden inte är slutförd. (#3201)
- Ändra webb-cmdletar `UserAgent` från `WindowsPowerShell` till `PowerShell` . (#4914) (Tack [@markekraus](https://github.com/markekraus) )
- Lägg till explicit `ContentType` identifiering till `Invoke-RestMethod` (#4692)
- Korrigera webb-cmdletar `-SkipHeaderValidation` så att de fungerar med User-Agent-huvuden som inte är standard. (#4479 &
  #<a name="4512-thanks-markekraus"></a>4512) (tack [@markekraus](https://github.com/markekraus) )

### <a name="json-cmdlets"></a>JSON-cmdletar

- Lägg till för `-AsHashtable` `ConvertFrom-Json` att returnera en `Hashtable` i stället. (#5043) (Tack [@bergmeister](https://github.com/bergmeister) !)
- Använd prettier-Formatter med `ConvertTo-Json` utdata. (#2787) (Tack till @kittholland !)
- Lägg till `Jobject` stöd för serialisering i `ConvertTo-Json` . (#5141)
- Korrigera `ConvertFrom-Json` för att deserialisera en sträng mat ris från pipelinen som tillsammans skapar en fullständig JSON-sträng. Detta åtgärdar vissa fall där newlines skulle bryta JSON-parsning.
  (#3823)
- Ta bort den `AliasProperty "Count"` definierade för `System.Array` . Detta tar bort den främmande `Count` egenskapen för vissa `ConvertFrom-Json` utdata. (#3231) (Tack till [@PetSerAl](https://github.com/PetSerAl) !)

### <a name="csv-cmdlets"></a>CSV-cmdletar

- `Import-Csv` stöder nu utökat logg fils format för W3C (#2482) (tack [@iSazonov](https://github.com/iSazonov) !)
- Lägg till `PSTypeName` stöd för `Import-Csv` och `ConvertFrom-Csv` . (#5389) (Tack [@markekraus](https://github.com/markekraus) !)
- Gör `Import-Csv` support `CR` , `LF` och `CRLF` som rad avgränsare. (#5363) (Tack [@iSazonov](https://github.com/iSazonov) !)
- Gör `-NoTypeInformation` standardinställningen på `Export-Csv` och `ConvertTo-Csv` . (#5164) (Tack [@markekraus](https://github.com/markekraus) !)

### <a name="service-cmdlets"></a>Tjänst-cmdletar

- Lägg till egenskaper,,, `UserName` `Description` `DelayedAutoStart` `BinaryPathName` och `StartupType` till de `ServiceController` objekt som returnerades av `Get-Service` . (#4907) (Tack [@joandrsn](https://github.com/joandrsn) )
- Lägg till funktioner för att ange autentiseringsuppgifter för `Set-Service` kommandot. (#4844) (Tack [@joandrsn](https://github.com/joandrsn) )

### <a name="other-cmdlets"></a>Andra cmdletar

- Lägg till en parameter till `Get-ChildItem` anropad `-FollowSymlink` som passerar symlinks på begäran, med kontroller för länk slingor. (#4020)
- Uppdatera `Add-Type` till stöd `CSharpVersion7` . (#3933) (Tack till [@iSazonov](https://github.com/iSazonov) )
- Ta bort `Microsoft.PowerShell.LocalAccounts` modulen på grund av användning av API: er som inte stöds förrän en bättre lösning har påträffats. (#4302)
- Ta bort `*-Counter` cmdletarna i `Microsoft.PowerShell.Diagnostics` på grund av användning av API: er som inte stöds förrän en bättre lösning har hittats. (#4303)
- Lägg till stöd för `Invoke-Item -Path <folder>` . (#4262)
- Lägg till `-Extension` och `-LeafBase` växlar till `Split-Path` så att du kan dela upp sökvägar mellan fil namns tillägget och resten av fil namnet. (#2721) (Tack till [@powercode](https://github.com/powercode) !)
- Lägg till parametrar `-Top` och `-Bottom` för den `Sort-Object` översta/understa N-sorteringen
- Exponera en process överordnade process genom att lägga till `CodeProperty "Parent"` i `System.Diagnostics.Process` . (#2850) (Tack till [@powercode](https://github.com/powercode) !)
- Använd MB i stället för KB för minnes kolumner i `Get-Process`
- Lägg till `-NoNewLine` växel för `Out-String` . (#5056) (Tack [@raghav710](https://github.com/raghav710) )
- `Move-Item` cmdleten följer `-Include` `-Exclude` parametrarna, och `-Filter` . (#3878)
- Tillåt `*` användning i register Sök vägen för `Remove-Item` . (#4866)
- Lägg till `-Title` i `Get-Credential` och förena prompten på olika plattformar.
- Lägg till `-TimeOut` parametern i `Test-Connection` . (#2492)
- `Get-AuthenticodeSignature` cmdlets kan nu hämta tidstämpel för filsignaturen. (#4061)
- Ta bort växeln som inte stöds `-ShowWindow` från `Get-Help` . (#4903)
- Korrigera `Get-Content -Delimiter` till inkludera inte avgränsaren i de mat ris element som returneras (#3706) (tack [@mklement0](https://github.com/mklement0) )
- Lägg till `Meta` , `Charset` och `Transitional` parametrar för `ConvertTo-HTML` (#4184) (tack [@ergo3114](https://github.com/ergo3114) )
- Lägg till `WindowsUBR` och `WindowsVersion` egenskaper som ska `Get-ComputerInfo` skapas
- Lägg till `-Group` parameter i `Get-Verb`
- Lägg till `ShouldProcess` stöd i `New-FileCatalog` och `Test-FileCatalog` (korrigeringar `-WhatIf` och `-Confirm` ). (#3074) (Tack till [@iSazonov](https://github.com/iSazonov) !)
- Lägg till `-WhatIf` Växla till `Start-Process` cmdlet (#4735) (tack [@sarithsutha](https://github.com/sarithsutha) )
- Lägg till `ValidateNotNullOrEmpty` för många befintliga parametrar.

## <a name="tab-completion"></a>Slut för ande flik

- Utökad typ av härledning i ifyllning baserat på variabel värden för körning. (#2744) (Tack till [@powercode](https://github.com/powercode) !) Detta möjliggör avslutning av tabb i situationer som:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Fliken för att lägga till en hash- `-Property` mängd för `Select-Object` . (#3625) (Tack till [@powercode](https://github.com/powercode) )
- Aktivera Autoavsluta av argument för `-ExcludeProperty` och `-ExpandProperty` `Select-Object` .
  (#3443) (Tack till [@iSazonov](https://github.com/iSazonov) !)
- Åtgärda ett fel i slut för ande av flikar för att `native.exe --<tab>` ringa till den interna slutföraren. (#3633) (Tack till [@powercode](https://github.com/powercode) !)

## <a name="breaking-changes"></a>Icke-bakåtkompatibla ändringar

Vi har introducerat ett antal överbrytande ändringar i PowerShell Core 6,0.
Läs mer om dem i detalj i avsnittet om att [dela upp ändringar i PowerShell Core 6,0][breaking-changes].

## <a name="debugging"></a>Felsökning

- Stöd för stegvis fel sökning för `Invoke-Command -ComputerName` . (#3015)
- Aktivera fel söknings loggning för binder i PowerShell Core

## <a name="filesystem-updates"></a>Fil Systems uppdateringar

- Aktivera användning av fil Systems leverantören från en UNC-sökväg. ($4998)
- `Split-Path` fungerar nu med UNC-rötter
- `cd` utan argument fungerar nu som `cd ~`
- Fast PowerShell Core för att tillåta användning av sökvägar som är längre än 260 tecken. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Fel korrigeringar och prestanda förbättringar

Vi har gjort *många* förbättringar av prestanda i PowerShell, inklusive i start tid, olika inbyggda cmdlets och interaktion med interna binärfiler.

Vi har också åtgärdat ett antal buggar i PowerShell Core. En fullständig lista över korrigeringar och ändringar finns i vår [ändringsloggen][] på GitHub.

## <a name="telemetry"></a>Telemetri

- PowerShell Core 6,0 lade till telemetri till konsol värden för att rapportera två värden (#3620):
  - OS-plattformen ( `$PSVersionTable.OSDescription` )
  - den exakta versionen av PowerShell ( `$PSVersionTable.GitCommitId` )

Om du vill välja bort den här Telemetrin skapar du bara `POWERSHELL_TELEMETRY_OPTOUT` miljövariabler med något av följande värden: `true` , `1` eller `yes` . När du skapar variabeln kringgås all telemetri även före den första körningen av PowerShell. Vi planerar också att exponera dessa telemetridata och de insikter vi få från Telemetrin i [Community-instrumentpanelen][community-dashboard]. Du hittar mer information om hur vi använder dessa data i det här [blogg inlägget][telemetry-blog].

[.NET-blogg]: https://devblogs.microsoft.com/dotnet/introducing-net-standard/
[.NET Core 2.0]: /dotnet/core/
[.NET Standard]: /dotnet/standard/net-standard
[breaking-changes]: breaking-changes-ps6.md
[CDXLM]: /previous-versions/windows/desktop/wmi_v2/getting-started-with-cdxml
[ändringsloggen]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[Docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[Vanliga frågor och svar]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[github]: https://github.com/PowerShell/PowerShell
[os_log]: https://developer.apple.com/documentation/os/logging
[semi-annual]: /windows-server/get-started/semi-annual-channel-overview
[ssh-remoting]: /powershell/scripting/learn/remoting/SSH-Remoting-in-PowerShell-Core
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[telemetry-blog]: https://devblogs.microsoft.com/powershell/powershell-open-source-community-dashboard/
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
