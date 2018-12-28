---
ms.date: 05/17/2018
keywords: PowerShell, core
title: Större ändringar för PowerShell 6.0
ms.openlocfilehash: d477a9b27e8d5df6653ee40f8b606879b60a80c7
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655454"
---
# <a name="breaking-changes-for-powershell-60"></a>Större ändringar för PowerShell 6.0

## <a name="features-no-longer-available-in-powershell-core"></a>Funktioner som inte längre tillgängliga i PowerShell Core

### <a name="powershell-workflow"></a>PowerShell-arbetsflöde

[PowerShell-arbetsflöde] [ workflow] är en funktion i Windows PowerShell som bygger på [Windows Workflow Foundation (WF)] [ workflow-foundation] som gör möljligt robust runbooks för tidskrävande eller parallelliserad uppgifter.

På grund av bristen på stöd för Windows Workflow Foundation i .NET Core, vi kommer inte att fortsätta att stödja PowerShell-arbetsflöden i PowerShell Core.

I framtiden kommer vill vi aktivera inbyggda parallellitet/samtidighet i PowerShell-språket utan behov av PowerShell-arbetsflöde.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Anpassade snapin-moduler

[PowerShell-snapin-moduler] [ snapin] är en föregångare till PowerShell-moduler som inte har införandet i PowerShell-communityn.

På grund av komplexiteten med stöd för snapin-moduler och deras bristande användning i communityn, stöder vi inte längre anpassade snapin-moduler i PowerShell Core.

Idag är det bryter den `ActiveDirectory` och `DnsClient` moduler i Windows och Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>WMI v1-cmdletar

På grund av komplexiteten med stöd för två uppsättningar med WMI-baserade moduler, vi har tagit bort WMI-v1 cmdlets från PowerShell Core:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

I stället rekommenderar vi att du kan använda CIM (även kallat WMI v2)-cmdletar som ger samma funktioner med nya funktioner och en omarbetad syntax:

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

På grund av användningen av stöds inte API: er, `Microsoft.PowerShell.LocalAccounts` har tagits bort från PowerShell Core tills en bättre lösning hittas.

### <a name="-counter-cmdlets"></a>`*-Counter`-cmdletar

På grund av användningen av stöds inte API: er, den `*-Counter` har tagits bort från PowerShell Core tills en bättre lösning hittas.

## <a name="enginelanguage-changes"></a>Ändringar av motorn/språk

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Byt namn på `powershell.exe` till `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

För att ge användarna ett deterministiskt sätt att anropa PowerShell Core i Windows (i stället för Windows PowerShell), PowerShell Core-binärfilen har ändrats till `pwsh.exe` på Windows och `pwsh` på icke-Windows-plattformar.

Förkortat namn är också konsekvent med namngivning av gränssnitt på icke-Windows-plattformar.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Infoga inte radbrytningar att mata ut (förutom för tabeller) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Tidigare utdata har justerats till bredd i konsolen och radbrytningar har lagts till på slutbredden i konsolen, vilket innebär att utdata inte hämta omformaterades som väntat om terminalen har ändrats. Den här ändringen har inte tillämpats på tabeller, som krävs för att hålla kolumnerna justerad radbrytningar.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Hoppa över kontrollen av null-element för samlingar med en värdetyp elementtypen [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

För den `Mandatory` parametern och `ValidateNotNull` och `ValidateNotNullOrEmpty` attribut, hoppa över kontrollen null-element om samlingens elementtypen är värdetyp.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Ändra `$OutputEncoding` att använda `UTF-8 NoBOM` kodning i stället för ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

Den föregående kodning, ASCII (7-bitars) skulle resultera i felaktiga ändring av utdata i vissa fall. Den här ändringen är att göra `UTF-8 NoBOM` standard, vilket bevarar Unicode-utdata med en kodning som stöds av de flesta verktyg och operativsystem.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Ta bort `AllScope` från de flesta standardalias [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Påskynda omfång skapa `AllScope` har tagits bort från de flesta standardalias. `AllScope` lämnades för några vanliga alias där sökningen var snabbare.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` och `-Debug` inte längre åsidosätter `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Tidigare, om `-Verbose` eller `-Debug` angavs, den overrode beteendet för `$ErrorActionPreference`. Med den här ändringen `-Verbose` och `-Debug` inte längre att påverka beteendet för `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Ändrade cmdletar

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Anropa RestMethod returnerar inte användbar information när inga data returneras. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

När ett API returnerar bara `null`, Invoke-RestMethod serialisering av detta som strängen `"null"` i stället för `$null`. Den här ändringen åtgärdar logiken i `Invoke-RestMethod` att korrekt serialisera ett giltigt enskilt value JSON `null` literal som `$null`.

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Ta bort `-ComputerName` från `*-Computer` cmdletar [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

På grund av problem med RPC-fjärrkommunikation i CoreFX (särskilt på icke-Windows-plattformar) och att säkerställa en konsekvent fjärrkommunikationsupplevelse i PowerShell, den `-ComputerName` parametern har tagits bort från den `\*-Computer` cmdletar. Använd `Invoke-Command` istället för som ett sätt att köra cmdlet: ar via en fjärranslutning.

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Ta bort `-ComputerName` från `*-Service` cmdletar [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

För att uppmuntra konsekvent användning av PSRP, den `-ComputerName` parametern har tagits bort från `*-Service` cmdletar.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Åtgärda `Get-Item -LiteralPath a*b` om `a*b` faktiskt inte finns för att returnera fel [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Tidigare `-LiteralPath` angivna jokertecken skulle behandlar det samma som `-Path` och om det finns inga filer jokertecknet den tyst skulle avsluta. Rätt beteende ska vara den `-LiteralPath` är en teckenliteral så att om filen inte finns, den borde fel. Ändringen är att behandla jokertecken användas med `-Literal` som literal.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` ska gälla `PSTypeNames` vid importen när anger du följande information finns i CSV-filen [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Tidigare objekt exporteras med `Export-CSV` med `TypeInformation` importeras med `ConvertFrom-Csv` inte behålla informationen. Den här ändringen lägger till informationen om att `PSTypeNames` medlem om det är tillgängligt från CSV-filen.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` bör vara standard på `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Den här ändringen gjordes på adressen synpunkter på standardbeteendet för `Export-CSV` med av typinformation.

Cmdlet: en skulle tidigare utdata en kommentar som den första raden som innehåller namnet på objektet. Ändringen är att förhindra detta som standard eftersom den inte kan tolkas i de flesta verktygen. Använd `-IncludeTypeInformation` att behålla den tidigare funktionen.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Web-cmdletar ska Varna när `-Credential` skickas via okrypterade anslutningar [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

När du använder HTTP, skickas innehåll, inklusive lösenord som klartext. Den här ändringen är att inte tillåta detta som standard och returnerar ett fel om autentiseringsuppgifter skickas på ett säkert sätt. Användarna kan kringgå detta med hjälp av den `-AllowUnencryptedAuthentication` växla.

## <a name="api-changes"></a>API-ändringar

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Ta bort `AddTypeCommandBase` klass [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

Den `AddTypeCommandBase` klassen har tagits bort från `Add-Type` att förbättra prestanda. Den här klassen används endast av cmdleten Add-Type och bör inte påverkar användarna.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Skapa en enhetlig cmdlets med parametern `-Encoding` är av typen `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

Den `-Encoding` värdet `Byte` har tagits bort från filsystemet provider-cmdlet: ar. En ny parameter `-AsByteStream`, nu för att ange att det krävs en byte-dataström som indata eller att utdata är en dataström med byte.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Lägg till bättre felmeddelande visas för tom och null `-UFormat` parametern [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Tidigare när du skicka en tom format sträng till `-UFormat`, en exempelbild felmeddelande visas. Ett mer beskrivande fel har lagts till.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Rensa konsolen kod [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Följande funktioner har tagits bort eftersom de inte stöds i PowerShell Core och det finns inga planer på att lägga till stöd som de finns äldre skäl för Windows PowerShell: `-psconsolefile` växeln och kod, `-importsystemmodules` växel och kod och teckensnitt ändra kod.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Ta bort `RunspaceConfiguration` stöder [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

Tidigare, när du skapar ett PowerShell-körningsutrymme programmässigt med hjälp av API du kan använda en äldre [ `RunspaceConfiguration` ] [ runspaceconfig] eller det nyare [ `InitialSessionState` ] [ iss]. Den här ändringen inte längre stöd för `RunspaceConfiguration` och stöder endast `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` binda argument till `$input` i stället för `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

En felaktig placering av en parameter resulterade i argument angavs som indata i stället för som argument.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Ta bort stöds inte `-showwindow` växla från `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` förlitar sig på WPF, vilket inte stöds på CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>Tillåt * som ska användas i registersökväg för `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Tidigare `-LiteralPath` angivna jokertecken skulle behandlar det samma som `-Path` och om det finns inga filer jokertecknet den tyst skulle avsluta. Rätt beteende ska vara den `-LiteralPath` är en teckenliteral så att om filen inte finns, den borde fel. Ändringen är att behandla jokertecken användas med `-Literal` som literal.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Åtgärda `Set-Service` misslyckas testet [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Tidigare, om `New-Service -StartupType foo` har använts, `foo` ignorerades och tjänsten har skapats med vissa standard starttyp. Den här ändringen är att skapa egna ett fel för en ogiltig starttyp.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Byt namn på `$IsOSX` till `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

Namnge i PowerShell ska stämma överens med våra namngivning och följa Apples användning av macOS i stället för OSX. Men för läsbarhet och konsekvent vi vistas med Pascal gemener och versaler.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Gör fel meddelandet konsekvent när ogiltigt skript skickas till - fil, bättre fel när tvetydig argumentet [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Ändra slutkoder av `pwsh.exe` för att anpassas till Unix-conventions

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Borttagning av `LocalAccount` och cmdlet: ar från `Diagnostics` moduler. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

På grund av stöds inte API: er, den `LocalAccounts` modulen och `Counter` cmdletar i den `Diagnostics` modulen har tagits bort tills en bättre lösning hittas.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>Kör powershell-skript med bool parametern fungerar inte [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Tidigare med hjälp av powershell.exe (nu `pwsh.exe`) att köra ett PowerShell-skript med `-File` tillhandahålls inget sätt att skicka $true/$false som parametervärden. Stöd för $true/$false som parsade värden till parametrar har lagts till. Värden stöds också som för närvarande dokumenterade syntax inte fungerar.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Ta bort `ClrVersion` egenskap från `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

Den `ClrVersion` egenskapen för `$PSVersionTable` är inte användbart med CoreCLR slutanvändare bör inte använda detta värde för att fastställa kompatibiliteten.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Ändra namngivna parametern för `powershell.exe` från `-Command` till `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Aktivera shebang användningen av PowerShell på icke-Windows-plattformar. Det innebär på Unix-baserat system, du kan göra en skriptet körbar fil som skulle anropar PowerShell automatiskt i stället för att explicit anropa `pwsh`. Det innebär också att du kan nu göra saker som `powershell foo.ps1` eller `powershell fooScript` utan att ange `-File`. Den här ändringen nu kräver dock att du uttryckligen anger `-c` eller `-Command` vid försök att till exempel `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Implementera Unicode-escape-parsning [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u#### `` eller `` `u{####} `` konverteras till motsvarande Unicode-tecken. Att mata ut en literal `` `u ``, hoppa över backtick: ``` ``u ```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Ändra `New-ModuleManifest` kodning till `UTF8NoBOM` på icke-Windows-plattformar [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Tidigare `New-ModuleManifest` skapar psd1 manifesten i UTF-16 med BOM, skapar ett problem för Linux-verktyg. Den här stor förändring ändras kodning av `New-ModuleManifest` kan UTF (utan BOM) på icke-Windows-plattformar.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Förhindra `Get-ChildItem` från recursing till symlinks (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Den här ändringen ger `Get-ChildItem` mer i linje med Unix `ls -r` och Windows `dir /s` inbyggda kommandon. Precis som kommandona nämnda cmdlet visar symboliska länkar till kataloger hittades under rekursion, men recurse inte i dessa.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Åtgärda `Get-Content -Delimiter` att inte inkludera avgränsaren i de returnerade raderna [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Tidigare utdata när du använder `Get-Content -Delimiter` var inkonsekvent och olämplig eftersom det krävs ytterligare bearbetning av data och ta bort avgränsaren. Den här ändringen tar bort avgränsaren i returnerade rader.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Implementera Format hexadecimalt i C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

Den `-Raw` parametern är nu en ”no-op” (eftersom den inte gör något). Vi rekommenderar att alla utdata visas med tal som innehåller alla byte för dess typ representerar (vad den `-Raw` parametern kallades tidigare gjorde före ändringen).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>PowerShell som en standard-gränssnittet fungerar inte med skriptkommandot [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

För Unix är det en konvention för tankar att acceptera `-i` för ett interaktivt gränssnitt och många verktyg förväntar du dig det här beteendet (`script` exempelvis och när du ställer in PowerShell som standardgränssnittet) och anropar shell med den `-i` växla. Den här ändringen är större i som `-i` tidigare kunde användas som kort tillsammans för att matcha `-inputformat`, som nu måste vara `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Åtgärda stavfel i Get-ComputerInfo egenskapsnamnet [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` var felstavad som `BiosSeralNumber` och har ändrats till rätt stavning.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Lägg till `Get-StringHash` och `Get-FileHash` cmdletar [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Den här ändringen är att vissa hash-algoritmer stöds inte av CoreFX, de är därför inte längre tillgängliga:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Lägga till verifiering på `Get-*` cmdletar där skicka $null returnerar alla objekt i stället för fel [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Skicka `$null` till någon av de följande nu returnerar ett fel:

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Lägg till stöd för W3C utökat loggfilsformat i `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Tidigare den `Import-Csv` cmdlet kan inte användas till att direktimportera loggfiler i W3C utökat loggfilsformat och ytterligare åtgärd skulle krävas. Med den här ändringen stöds utökade W3C-loggformatet.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Problem med parameter-bindning med `ValueFromRemainingArguments` i PS funktioner [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` Nu returnerar värdena som en matris i stället för ett enda värde som i sin tur är en matris.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion` tas bort från `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Ta bort den `BuildVersion` egenskap från `$PSVersionTable`. Den här egenskapen är kopplad till build-version för Windows. I stället rekommenderar vi att du använder `GitCommitId` att hämta exakta build-versionen av PowerShell Core.

### <a name="changes-to-web-cmdlets"></a>Ändringar i webb-cmdletar

Underliggande .NET API för webb-cmdletar har ändrats till `System.Net.Http.HttpClient`. Den här ändringen ger många fördelar. Men den här ändringen tillsammans med brist på samverkan med Internet Explorer har resulterat i flera ändringar i `Invoke-WebRequest` och `Invoke-RestMethod`.

- `Invoke-WebRequest` har nu stöd för grundläggande HTML-parsning endast. `Invoke-WebRequest` returnerar alltid en `BasicHtmlWebResponseObject` objekt. Den `ParsedHtml` och `Forms` egenskaper har tagits bort.
- `BasicHtmlWebResponseObject.Headers` värden är nu `String[]` i stället för `String`.
- `BasicHtmlWebResponseObject.BaseResponse` är nu en `System.Net.Http.HttpResponseMessage` objekt.
- Den `Response` egenskapen på Web Cmdlet undantag är nu en `System.Net.Http.HttpResponseMessage` objekt.
- Strikt RFC-huvud och parsning nu är standard för den `-Headers` och `-UserAgent` parametern. Detta kan kringgås med `-SkipHeaderValidation`.
- `file://` och `ftp://` URI-scheman stöds inte längre.
- `System.Net.ServicePointManager` inställningar för respekteras inte längre.
- Det finns för närvarande inga certifikatbaserad autentisering på macOS.
- Användning av `-Credential` över en `http://` URI resulterar i ett fel. Använd en `https://` URI eller ange den `-AllowUnencryptedAuthentication` parametern för att ignorera felet.
- `-MaximumRedirection` skapar nu ett avslutande fel när omdirigering försök att överskrida den angivna istället för att returnera resultatet av den senaste omdirigeringen.
