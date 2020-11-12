---
title: Nyheter i PowerShell 7,1
description: Nya funktioner och ändringar som lanseras i PowerShell 7,1
ms.date: 11/11/2020
ms.openlocfilehash: 9ad552a8105b16d1f01ddacbdee1a43663ef3fd1
ms.sourcegitcommit: 28831acbb09d3edbaa6bd9fc62491603d64d3849
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94553275"
---
# <a name="whats-new-in-powershell-71"></a>Nyheter i PowerShell 7,1

PowerShell 7,1 är en utgåva med öppen källkod, plattforms oberoende plattform (Windows, macOS och Linux) av PowerShell, som är byggd för att hantera heterogena miljöer och hybrid moln.

Vi bygger på stiftelsen som etablerats i PowerShell 7,0, våra ansträngningar fokuserar på community-problem och inkluderar ett antal förbättringar och korrigeringar. Vi strävar efter att se till att PowerShell är en stabil och genomförd plattform.

## <a name="where-can-i-install-powershell"></a>Var kan jag installera PowerShell?

PowerShell 7,1 har för närvarande stöd för följande operativ system på x64, inklusive:

- Windows 8.1/10 (inklusive ARM64)
- Windows Server 2012 R2, 2016, 2019 och Semi-Annual-kanal (SAC)
- Ubuntu 16.04/18.04/20.04 (inklusive ARM64)
- Ubuntu 19,10 (via Snap-paket)
- Debian 9/10
- CentOS och RHEL 7/8
- Fedora 30
- Alpine 3.11 + (inklusive ARM64)
- macOS 10.13 +

Vi har också community-support för:

- Båge Linux
- Raspbian Linux
- Kali Linux

Mer uppdaterad information om operativ system och support livs cykel som stöds finns i [PowerShell-Supportens livs cykel](/powershell/scripting/powershell-support-lifecycle)

PowerShell 7,1 har publicerats till Microsoft Store. Du hittar PowerShell-versionen på [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) webbplats eller i Store-programmet i Windows.

Fördelar med Microsoft Store-paketet:

- Automatiska uppdateringar har skapats direkt i Windows 10
- Integreras med andra mekanismer för program varu distribution som Intune och SCCM

> [!NOTE]
> Eventuella konfigurations inställningar på system nivå som lagras i `$PSHOME` kan inte ändras. Detta inkluderar WSMAN-konfigurationen. Detta förhindrar att fjärrsessioner ansluter till Store-baserade installationer av PowerShell. Konfigurationer på användar nivå och SSH-fjärrkommunikation stöds.

Kontrol lera installations anvisningarna för det önskade operativ systemet:

- [Windows](/powershell/scripting/install/installing-powershell-core-on-windows)
- [macOS](/powershell/scripting/install/installing-powershell-core-on-macos)
- [Linux](/powershell/scripting/install/installing-powershell-core-on-linux)

Dessutom stöder PowerShell 7,1 ARM32 och ARM64 varianter för Debian, Ubuntu och ARM64 Alpine Linux.

Även om den inte stöds officiellt har communityn även tillhandahållit paket för [båge](https://aur.archlinux.org/packages/powershell/) och Kali Linux.

> [!NOTE]
> Debian 10 +, CentOS 8 +, Ubuntu 20,04, alpina och arm stöder för närvarande inte WinRM-fjärrkommunikation. Mer information om hur du konfigurerar SSH-baserad fjärr kommunikation finns i [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

## <a name="running-powershell-71"></a>Köra PowerShell 7,1

PowerShell 7,1 installeras i en ny katalog och körs sida vid sida med Windows PowerShell 5,1.
PowerShell 7,1 är en uppgradering på plats som ersätter PowerShell 6. x. eller PowerShell 7,0.

- PowerShell 7,1 är installerat på `%programfiles%\PowerShell\7`
- `%programfiles%\PowerShell\7`Mappen läggs till`$env:PATH`

PowerShell 7,1-installations paketet uppgraderar tidigare versioner av PowerShell Core 6. x:

- PowerShell Core 6. x i Windows: `%programfiles%\PowerShell\6` ersätts av `%programfiles%\PowerShell\7`
- Linux: `/opt/microsoft/powershell/6` ersätts av `/opt/microsoft/powershell/7`
- macOS: `/usr/local/microsoft/powershell/6` ersätts av `/usr/local/microsoft/powershell/7`

> [!NOTE]
> I Windows PowerShell heter den körbara filen för att starta PowerShell `powershell.exe` . I version 6 och senare ändras den körbara filen så att den stöder sida-vid-sida-körning. Den nya körbara filen för att starta PowerShell 7,1 är `pwsh.exe` . För hands versioner kommer att finnas kvar på plats som i `pwsh-preview` stället för i `pwsh` den 7-för hands versions katalogen.

## <a name="breaking-changes-and-improvements"></a>Bryta ändringar och förbättringar

Den senaste informationen om ändringar och förbättringar finns i [ändringsloggen](https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG) i GitHub-lagringsplatsen.

### <a name="breaking-changes"></a>Icke-bakåtkompatibla ändringar

<!-- TODO: Add descriptions for each breaking change  -->

- Korrigera `$?` till inte `$false` när det interna kommandot skriver till `stderr` (#13395)
- Byt namn `-FromUnixTime` till `-UnixTimeSeconds` på för `Get-Date` att tillåta UNIX-tidsinformation (#13084) (tack @aetos382 !)
- `$ErrorActionPreference`Påverkar inte `stderr` utdata från interna kommandon (#13361)
- Tillåt explicit angiven namngiven parameter att ersätta samma med en hash-ihopbuntning (#13162)
- Gör att växel parametern `-Qualifier` inte placeras för `Split-Path` (#12960) (tack @yecril71pl !)
- Matcha arbets katalogen som en litteral sökväg för `Start-Process` när den inte har angetts (#11946) (tack @NoMoreFood !)
- Skapa `-OutFile` en parameter i webb-cmdlets som fungerar som `-LiteralPath` (#11701) (tack @iSazonov !)
- Korrigera sträng parameter bindning för `BigInteger` numeriska literaler (#11634) (tack @vexx32 !)
- I Windows `Start-Process` skapar en process miljö med alla miljövariabler från den aktuella sessionen, med `-UseNewEnvironment` en ny standard process miljö (#10830) (tack @iSazonov !)
- Bryt inte retur resultat till `PSObject` när du konverterar script block till delegaten (#10619)
- Använd invariant kultur sträng konvertering för `-replace` operatör (#10954) (tack @iSazonov !)

### <a name="experimental-features"></a>Experimentella funktioner

<!-- TODO: note which features are now mainstream  -->

- Lägg till `-Runspace` parameter till alla `*-PSBreakpoint` cmdletar (#10492) (tack @KirkMunro !)
- Stöd `PSPath` för att skicka till interna kommandon (#12386)
- Använd invariant kultur sträng konvertering för `-replace` operatör (#10954) (tack @iSazonov !)

### <a name="general-cmdlet-updates-and-fixes"></a>Allmänna cmdlet-uppdateringar och korrigeringar

- Genererar varning om `ConvertTo-Json` överskrider `-Depth` värdet (#13692)
- Korrigera fall där undantags meddelandet bara innehåller ``"`n"`` Windows (#13684)
- Identifiera `CONOUT$` och `CONIN$` som reserverade enhets namn (#13508) (tack @davidreis97 !)
- Korrigering `ConciseView` för interaktiv avancerad funktion vid skrivfel (#13623)
- Lägg till stöd för `TLS` 1,3 i Web-cmdlets (#13409) (tack @iSazonov !)
- Lägg till null-kontroll för `args` i `CommandLineParser` (#13451) (tack @iSazonov !)
- Behandla referens punkter för Microsoft Store program (#13481) (tack @iSazonov !)
- Flytta `PSNullConditionalOperators` funktion från experiment (#13529)
- Flytta `PSNativePSPathResolution` funktion från experiment (#13522)
- Använd fältet om egenskapen inte finns för `ObRoot` när du använder PowerShell Direct to container (#13375) (tack @hemisphera !)
- Ignorera `UTF-7` föråldrade varningar (#13484)
- Undvik flera uppräkningar av en `IEnumerable<Expression>` instans i `Compiler.cs` (#13491)
- Ändra `Add-Type -OutputType` till inte stöd `ConsoleApplication` och `WindowsApplication` (#13440)
- Skapa varningar när `UTF-7` anges som en kodning (#13430)
- Åtgärda fel meddelandet från en ny symbolisk länk saknar mål (#13085) (tack @yecril71pl !)
- Gör så att parametern `args` inte kan ha värdet null i offentliga `ConsoleHost` API: er (#13429)
- Lägg till saknad dispose `CancellationTokenSource` (#13420) (tack @Youssef1313 !)
- Korrigeringen `Get-Help` visas inte korrekt om parametern stöder jokertecken (#13353) (tack @ThomasNieto !)
- Uppdatera `pwsh` Hjälp för `-InputFormat` parameter (#13355) (tack @sethvs !)
- Deklarera MIT-licens för filer som har kopierats från Roslyn (#13305) (tack @xtqqczze !)
- Förbättra `BigInteger` inbytes beteenden (#12629) (tack @vexx32 !)
- Korrigera `Get-Acl -LiteralPath "HKLM:Software\Classes\*"` beteende (#13107) (tack @Shriram0908 !)
- Lägg till `DefaultVisit` metod i besökarnas gränssnitt och klass (#13258)
- Åtgärda konflikt vid kort SKRIFTS växling `-s` (sta) för `pwsh` (#13262) (tack @iSazonov !)
- Ändra `Read-Host -MaskInput` till Använd befintlig `SecureString` sökväg, men returnera som oformaterad text (#13256)
- Ta bort `ComEnumerator` as COM-objekt med `IEnumerator` stöds nu i .net 5,0 (#13259)
- Använd tillfällig personlig sökväg vid körnings utrymme start när miljövariabeln "hem" inte har definierats (#13239)
- Korrigera `Invoke-Command` för att identifiera rekursivt anrop av samma historik post (#13197)
- Ändra `pwsh` `-inputformat` prefixet för körbara växlar `-in` till `-inp` för att åtgärda konflikten med `-interactive` (#13205) (tack @iSazonov !)
- Hantera WSL-filsystem-sökväg vid analys av säkerhets zon för en fil (#13120)
- Gör andra växlar obligatoriska i `Split-Path` (#13150) (tack @kvprasoon !)
- Ny Fluent-design ikon för PowerShell 7 (#13100) (tack @sarthakmalik !)
- Korrigera `Move-Item` för att ge stöd för att flytta över monteringen på UNIX (#13044)
- Korrigera `NullReferenceException` i `CommandSearcher.GetNextCmdlet` (#12659) (tack @powercode !)
- Förhindra `NullReferenceException` i UNIX-dator-cmdletar med aktiva test-hookar (#12651) (tack @vexx32 !)
- Åtgärda problem i `Select-Object` där `Hashtable` medlemmar (t. ex. `Keys` ) inte kan användas med `-Property` eller `-ExpandProperty` (#11097) (tack @vexx32 !)
- Åtgärda ändring av stenografisk växel `-w` för pwsh (#12945)
- Byt namn på `CimCmdlet` resurs filen (#12955) (tack @iSazonov !)
- Ta bort användning av `Test-Path` i `ConciseView` (#12778)
- Flagga `default` satsen satsen switch sats condition som nyckelord (#10487) (tack @msftrncs !)
- Lägg till parameter `SchemaFile` till `Test-Json` cmdlet (#11934) (tack @beatcracker !)
- Ta tillbaka parametrar för certifikat leverantörer (#10622) (tack @iSazonov !)
- Korrigera `New-Item` för att skapa en symbolisk länk till målet för relativa sökvägar (#12797) (tack @iSazonov !)
- Lägg till `CommandLine` egenskap till process (#12288) (tack @iSazonov !)
- Lägger till `-MaskInput` parametern till `Read-Host` (#10908) (tack @davinci26 !)
- Ändra `CimCmdlets` att använda `AliasAttribute` (#12617) (tack @thlac !)
- Korrigera felaktigt index i format sträng i ParameterBinderBase (#12630) (tack @powercode !)
- Kopiera `CommandInfo` egenskapen i `Command.Clone()` (#12301) (tack @TylerLeonhardt !)
- Använd `-IncludeEqual` i `Compare-Object` när `-ExcludeDifferent` har angetts (#12317) (tack @davidseibel !)
- Ändra `Get-FileHash` till Stäng fil handtag innan du skriver utdata (#12474) (tack @HumanEquivalentUnit !)
- Åtgärda inkonsekvent undantags meddelande i `-replace` operatorn (#12388) (tack @jackdcasey !)
- Åtgärda `WinCompat` inläsning av modul för att hantera PowerShell 7-moduler med högre prioritet (#12269)
- Implementera `ForEach-Object -Parallel` körnings utrymme åter användning (#12122)
- Korrigera `Get-Service` till att inte ändra samling vid uppräkning av den (#11851) (tack @NextTurn !)
- Rensa IPC med namnet pipe på PowerShell-avsluta (#12187)
- Korrigera `<img />` identifierings-regex i webbcmdlets (#12099) (tack @vexx32 !)
- Tillåt kortare signerade hex-litteraler med lämpliga typ suffix (#11844) (tack @vexx32 !)
- Uppdatera `UseNewEnvironment` parameter beteende för `Start-Process` cmdleten i Windows (#10830) (tack @iSazonov !)
- Lägg till `-Shuffle` Växla till `Get-Random` kommando (#11093) (tack @eugenesmlv !)
- Gör `GetWindowsPowerShellModulePath` kompatibel med flera PS-installationer (#12280)
- Korrigera `Start-Job` för att fungera på system som inte har Windows PowerShell registrerat som standard gränssnitt (#12296)
- Ange ett alias och `-Syntax` för att `Get-Command` returnera syntaxen för aliased-kommandon (#10784) (tack @ChrisLGardner !)
- Gör CSV-cmdletar fungerar när du använder `-AsNeeded` och det finns en ofullständig rad (#12281) (tack @iSazonov !)
- I lokala anrop behöver du inte göra något `-PowerShellVersion 5.1` för `Get-FormatData` att se alla format data. (#11270) (Tack @mklement0 !)
- Stöd har lagts till för big endian `UTF-32` (#11947) (tack @NoMoreFood !)
- Åtgärda möjligt ras som läcker PowerShell-objekt i `ForEach-Object -Parallel` (#12227)
- Lägg till i `-FromUnixTime` `Get-Date` för att tillåta Unix-Time-inmatare (#12179) (tack @jackdcasey !)
- Ändra standard förloppet för förloppet och bakgrunds färgerna för att ge bättre kontrast (#11455) (tack @rkeithhill !)
- Åtgärda `foreach -parallel` när den aktuella enheten inte är tillgänglig (#12197)
- Bryt inte retur resultat till `PSObject` vid konvertering `ScriptBlock` till `delegate` (#10619)
- Skriv inte fel vid DNS-matchning på `Test-Connection -Quiet` (#12204) (tack @vexx32 !)
- Använd dedikerade trådar för att läsa de omdirigerade utdata och fel strömmar från den underordnade processen för jobb som är utanför proc (#11713)
- Åtgärda ett problem med en operatörs prioritetsordning i binder-kod (#12075) (tack @DamirAinullin !)
- Korrigera `NullReferenceException` vid bindning av gemensamma parametrar av typen `ActionPreference` (#12124)
- Korrigera standardformatering för avserialiserad `MatchInfo` (#11728) (tack @iSazonov !)
- Använd asynkrona strömmar i `Invoke-RestMethod` (#11095) (tack @iSazonov !)
- Address UTF-8-identifiering i `Get-Content -Tail` (#11899) (tack @NoMoreFood !)
- Hantera `IOException` i `Get-FileHash` (#11944) (tack @iSazonov !)
- Ändra `PowerShell Core` till `PowerShell` i en resurs sträng (#11928) (tack @alexandair !)
- Ta dig `MainWindowTitle` tillbaka `PSHostProcessInfo` (#11885) (tack @iSazonov !)
- Diverse mindre uppdateringar av Windows-kompatibilitet (#11980)
- Korrigera `ConciseView` till delning `PositionMessage` med `[Environment]::NewLine` (#12010)
- Ta bort nätverks hopp begränsning för interaktiva sessioner (#11920)
- Korrigera `NullReferenceException` i `SuspendStoppingPipeline()` och `RestoreStoppingPipeline()` (#11870) (tack @iSazonov !)
- Generera GUID för `FormatViewDefinition` `InstanceId` om det inte anges (#11896)
- Åtgärda `ConciseView` var fel meddelande är bredare än fönster bredd och inte innehåller blank steg (#11880)
- Tillåt `CAPI-compatible` fjärran sluten nyckel utbyte mellan plattformar (#11185) (tack @silijon !)
- Åtgärda fel meddelande (#11862) (tack @NextTurn !)
- Korrigera `ConciseView` för att hantera fall där det inte finns en-konsol för att hämta bredden (#11784)
- Uppdatera `CmsCommands` för att använda Store vs Certificate Provider (#11643) (tack @mikeTWC1984 !)
- Aktivera `pwsh` för att arbeta med Windows-system där `mpr.dll` och sta inte är tillgängligt (#11748)
- Återanvändare och implementera `Restart-Computer` för `Un*x` och macOS (#11319)
- Lägg till en implementering av `Stop-Computer` för Linux och MacOS (#11151)
- `help`Funktionen Fix för att kontrol lera om den `less` är tillgänglig innan du använder (#11737)
- Uppdatera `PSPath` i `certificate_format_ps1.xml` (#11603) (tack @xtqqczze !)
- Ändra reguljärt uttryck för att matcha Relations typer utan citat tecken i länk huvudet (#11711) (tack @Marusyk !)
- Åtgärda fel meddelandet under borttagning av den symboliska länken (#11331)
- Lägg endast till anpassad `Selected.*` typ `PSCustomObject` i `Select-Object` endast en gång (#11548) (tack @iSazonov !)
- Lägg till `-AsUTC` i `Get-Date` cmdleten (#11611)
- Åtgärda grupp beteende med booleska värden i `Format-Hex` (#11587) (tack @vexx32 !)
- `Test-Connection`Använd alltid standard kontext för synkronisering för att skicka ping-begäranden (#11517)
- Rätta till Start fel meddelanden (#11473) (tack @iSazonov !)
- Ignorera huvuden med null-värden i webbcmdlets (#11424) (tack @iSazonov !)
- Lägg till kontrollen igen för att ta `Invoke-Command` bort jobb. (#11388)
- Återställ "uppdatera Formatter till Skriv newlines om innehållet är tomt (#11193)" (#11342) (tack @iSazonov !)
- Tillåt `CompleteInput` att resultat returneras från `ArgumentCompleter` när `AST` eller skript har matchande funktions definition (#10574) (tack @M1kep !)
- Uppdatera formateringen så att den inte skriver nya rader om innehållet är tomt (#11193)

<!-- TODO: add more general contributor thank you listing -->
