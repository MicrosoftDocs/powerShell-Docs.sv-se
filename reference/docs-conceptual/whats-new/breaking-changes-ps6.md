---
ms.date: 05/17/2018
keywords: PowerShell, Core
title: Bryta ändringar för PowerShell 6,0
ms.openlocfilehash: df716fc3ad48d640ddefcfd87da445eaf104cfbe
ms.sourcegitcommit: e1027805385081c2e6f9250f9cd1167a45f035b0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561265"
---
# <a name="breaking-changes-for-powershell-60"></a>Bryta ändringar för PowerShell 6,0

## <a name="features-no-longer-available-in-powershell-core"></a>Funktioner som inte längre är tillgängliga i PowerShell Core

### <a name="powershell-workflow"></a>PowerShell-arbetsflöde

[PowerShell-arbetsflöde][workflow] är en funktion i Windows PowerShell som bygger ovanpå [Windows Workflow Foundation (WF)][workflow-foundation] som gör det möjligt att skapa robusta Runbooks för långvariga eller parallella uppgifter.

På grund av brist på stöd för Windows Workflow Foundation i .NET Core kommer vi inte att fortsätta att stödja PowerShell-arbetsflöde i PowerShell Core.

I framtiden skulle vi vilja aktivera inbyggd parallellitet/samtidighet i PowerShell-språket utan att behöva använda PowerShell-arbetsflöde.

Om du behöver använda kontroll punkter för att återuppta ett skript efter det att operativ systemet har startats om, rekommenderar vi att du använder Schemaläggaren för att köra ett skript på Start av operativ systemet, men skriptet måste ha ett eget tillstånd (som att spara det i en fil).

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Anpassade snapin-moduler

[PowerShell-snapin-moduler][snapin] är en föregående aktivitet till PowerShell-moduler som inte har omfattande antagande i PowerShell-communityn.

På grund av komplexiteten vid stöd för snapin-moduler och deras brist på användning i communityn stöder vi inte längre anpassade snapin-moduler i PowerShell Core.

Idag tar detta upp `ActiveDirectory` och `DnsClient` modulerna i Windows och Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>WMI v1-cmdletar

På grund av komplexiteten med stöd för två uppsättningar WMI-baserade moduler tog vi bort WMI v1-cmdletar från PowerShell Core:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

I stället rekommenderar vi att du använder CIM-cmdletarna (aka WMI v2) som tillhandahåller samma funktioner med nya funktioner och en omdesignad syntax:

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

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft. PowerShell. LocalAccounts

På grund av användning av API: er som inte stöds har `Microsoft.PowerShell.LocalAccounts` tagits bort från PowerShell Core tills en bättre lösning har hittats.

### <a name="-computer-cmdlets"></a>`*-Computer`-cmdletar

På grund av användning av API: er som inte stöds har följande cmdlets tagits bort från PowerShell Core tills en bättre lösning har hittats.

- Lägg till dator
- Checkpoint-Computer
- Ta bort dator
- Återställa-dator

### <a name="-counter-cmdlets"></a>`*-Counter`-cmdletar

På grund av användning av API: er som inte stöds har `*-Counter` tagits bort från PowerShell Core tills en bättre lösning har hittats.

### <a name="-eventlog-cmdlets"></a>`*-EventLog`-cmdletar

På grund av användning av API: er som inte stöds har `*-EventLog` tagits bort från PowerShell-kärnan. tills en bättre lösning har hittats. `Get-WinEvent` och `Create-WinEvent` är tillgängliga för att hämta och skapa händelser i Windows.

## <a name="enginelanguage-changes"></a>Motor/språk ändringar

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Byt namn på `powershell.exe` till `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

För att ge användarna ett deterministiskt sätt att anropa PowerShell Core på Windows (till skillnad från Windows PowerShell) ändrades binärfilen för PowerShell-kärnan till `pwsh.exe` i Windows och `pwsh` på andra plattformar än Windows-plattformar.

Det förkortade namnet är också konsekvent med namngivning av gränssnitt på andra plattformar än Windows-plattformar.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Infoga inte rad brytningar i utdata (förutom tabeller) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Tidigare var utdata justerade till bredden på konsolen och rad brytningarna lades till i konsolens slut punkt, vilket innebär att resultatet inte blev omformaterat som förväntat om terminalfönstret ändrades. Den här ändringen tillämpades inte i tabeller eftersom rad brytningar krävs för att hålla kolumnerna justerade.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Hoppa över null-Elements kontroll för samlingar med en värde typs element typ [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

För parametern `Mandatory` och `ValidateNotNull` och `ValidateNotNullOrEmpty` attribut, hoppar du över värdet null-element om samlingens element typ är värdetyp.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Ändra `$OutputEncoding` att använda `UTF-8 NoBOM` encoding i stället för ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

Föregående kodning, ASCII (7-bitars), resulterar i en felaktig ändring av utdata i vissa fall. Den här ändringen är att göra `UTF-8 NoBOM` standard, vilket bevarar Unicode-utdata med en kodning som stöds av de flesta verktyg och operativ system.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Ta bort `AllScope` från de flesta Standardalias [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

För att påskynda skapandet av ett område, har `AllScope` tagits bort från de flesta Standardalias. `AllScope` lämnades för några vanliga alias där sökningen var snabbare.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` och `-Debug` inte längre åsidosätter `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Tidigare, om `-Verbose` eller `-Debug` har angetts, overrode funktionen för `$ErrorActionPreference`. Med den här ändringen påverkar `-Verbose` och `-Debug` inte längre `$ErrorActionPreference`ens beteende.

## <a name="cmdlet-changes"></a>Cmdlet-ändringar

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Invoke-RestMethod returnerar inte värdefull information när inga data returneras. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

När ett API returnerar bara `null`, serialiserade Invoke-RestMethod detta som strängen `"null"` i stället för `$null`. Med den här ändringen åtgärdas logiken i `Invoke-RestMethod` för korrekt serialisering av ett giltigt JSON-`null` literalt värde som `$null`.

### <a name="remove--protocol-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Ta bort `-Protocol` från `*-Computer`-cmdletar [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

På grund av problem med RPC-fjärrkommunikation i CoreFX (särskilt på plattformar som inte är Windows) och säkerställer en konsekvent fjärrhantering i PowerShell, har parametern `-Protocol` tagits bort från `\*-Computer`-cmdlet: arna. DCOM stöds inte längre för fjärr kommunikation. Följande cmdletar stöder bara WSMAN-fjärr kommunikation:

- Byt namn – dator
- Starta om datorn
- Stoppa – dator

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Ta bort `-ComputerName` från `*-Service`-cmdletar [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

För att uppmuntra en konsekvent användning av PSRP har parametern `-ComputerName` tagits bort från `*-Service`-cmdletar.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Korrigera `Get-Item -LiteralPath a*b` om `a*b` faktiskt inte finns för att returnera fel [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Tidigare skulle `-LiteralPath` med ett jokertecken behandla det på samma sätt som `-Path` och om jokertecken inte hittas skulle det leda till tyst slut. Korrekt beteende bör vara att `-LiteralPath` är Literal så om filen inte finns, bör den innehålla fel. Ändra är att hantera jokertecken som används med `-Literal` som literal.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` bör gälla `PSTypeNames` vid import när typ information finns i CSV- [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Tidigare har objekt som exporter ATS med `Export-CSV` med `TypeInformation` som importer ATS med `ConvertFrom-Csv` inte bevaras av typ informationen. Den här ändringen lägger till typ informationen till `PSTypeNames` medlem om den är tillgänglig från CSV-filen.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` ska vara standard på `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Den här ändringen gjordes för att lösa kundfeedback om standard beteendet för `Export-CSV` att inkludera typ information.

Tidigare skulle cmdleten skriva en kommentar som den första raden som innehåller objektets typnamn. Ändringen är att ignorera detta som standard eftersom det inte tolkas av de flesta verktyg. Använd `-IncludeTypeInformation` för att behålla det tidigare beteendet.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Webb-cmdletar ska varna när `-Credential` skickas via okrypterade anslutningar [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

När du använder HTTP skickas innehåll inklusive lösen ord som klartext. Den här ändringen är att inte tillåta detta som standard och returnera ett fel om autentiseringsuppgifterna skickas på ett osäkert sätt. Användare kan kringgå detta genom att använda `-AllowUnencryptedAuthentication` växeln.

## <a name="api-changes"></a>API-ändringar

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Ta bort `AddTypeCommandBase` klass [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

@No__t_0-klassen togs bort från `Add-Type` för att förbättra prestandan. Den här klassen används endast av cmdleten Add-Type och bör inte påverka användare.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Förena cmdlets med parameter `-Encoding` att vara av typen `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

@No__t_0 värde `Byte` har tagits bort från cmdletarna för fil Systems Provider. En ny parameter, `-AsByteStream`, används nu för att ange att en byte-dataström krävs som indata eller att utdata är en data ström i byte.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Lägg till bättre fel meddelande för Tom och null `-UFormat` parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

När en tom format sträng skulle skickas till `-UFormat` visas ett fel meddelande om att ett fel meddelande visas. Ett mer beskrivande fel har lagts till.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Rensa konsol kod [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Följande funktioner har tagits bort eftersom de inte stöds i PowerShell Core, och det finns inga planer på att lägga till stöd som de finns för äldre skäl för Windows PowerShell: `-psconsolefile` växel och kod, `-importsystemmodules` växlar och kod och kod för teckensnitts ändring.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Har tagits bort `RunspaceConfiguration`-support [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

När du tidigare skapade en PowerShell-körnings utrymme via programmering med hjälp av API: et kan du använda den äldre [`RunspaceConfiguration`][runspaceconfig] eller den nyare [`InitialSessionState`][iss]. Den här ändringen tog bort stöd för `RunspaceConfiguration` och stöder bara `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` binda argument till `$input` i stället för `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

En felaktig position av en parameter resulterade i argumenten som angavs som indatamängd i stället för som argument.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Ta bort `-showwindow` växel från `Get-Help` som inte stöds [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` är beroende av WPF, vilket inte stöds på CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>Tillåt att * används i register Sök väg för `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Tidigare skulle `-LiteralPath` med ett jokertecken behandla det på samma sätt som `-Path` och om jokertecken inte hittas skulle det leda till tyst slut. Korrekt beteende bör vara att `-LiteralPath` är Literal så om filen inte finns, bör den innehålla fel. Ändra är att hantera jokertecken som används med `-Literal` som literal.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Korrigera `Set-Service` att testet inte fungerar [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Tidigare, om `New-Service -StartupType foo` användes, ignorerades `foo` och tjänsten skapades med en typ av standard starttyp. Den här ändringen är att explicit utlösa ett fel för en ogiltig starttyp.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Byt namn på `$IsOSX` till `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

Namngivningen i PowerShell bör vara konsekvent med vår namn och överensstämmer med Apples användning av macOS i stället för OSX. Men för att kunna läsa och ständigt kan vi hålla sig till Pascal-höljet.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Gör fel meddelandet konsekvent när ogiltigt skript skickas till fil, vilket är ett bättre fel när ett tvetydigt argument har skickats [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Ändra avslutnings koderna för `pwsh.exe` så att de överensstämmer med UNIX-konventioner

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Borttagning av `LocalAccount` och cmdlets från `Diagnostics` moduler. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

På grund av API: er som inte stöds har `LocalAccounts`-modulen och `Counter`-cmdletar i modulen `Diagnostics` tagits bort tills en bättre lösning har hittats.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>Det går inte att köra PowerShell-skriptet med bool-parametern [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Tidigare använde **PowerShell. exe** (nu **pwsh. exe**) för att köra ett powershell-skript med `-File` angav inget sätt att skicka `$true` / `$false` som parameter värden. Stöd för `$true` / `$false` som parsade värden till parametrar har lagts till. Växlings värden stöds också som för närvarande dokumenterad syntax fungerar inte.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Ta bort `ClrVersion` egenskap från `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

Egenskapen `ClrVersion` för `$PSVersionTable` är inte användbar med CoreCLR, slutanvändare ska inte använda det värdet för att fastställa kompatibiliteten.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Ändra positions parameter för `powershell.exe` från `-Command` till `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Aktivera Shebang användning av PowerShell på andra plattformar än Windows-plattformar. Det innebär att du kan göra en körbar skript fil som anropar PowerShell automatiskt i stället för att explicit anropa `pwsh` när du använder UNIX-baserade system. Det innebär också att du nu kan göra saker som `powershell foo.ps1` eller `powershell fooScript` utan att ange `-File`. Den här ändringen kräver dock att du uttryckligen anger `-c` eller `-Command` när du försöker göra saker som `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Implementera tolkning av Unicode-Escape [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u####`` eller `` `u{####}`` konverteras till motsvarande Unicode-tecken. Om du vill mata ut en literal `` `u`` kan du undanta bakticket: ``` ``u```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Ändra `New-ModuleManifest` encoding till `UTF8NoBOM` på andra plattformar än Windows-plattformar [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Tidigare skapade `New-ModuleManifest` psd1-manifest i UTF-16 med BOM, vilket skapar ett problem för Linux-verktyg. Den här avbrytande ändringen ändrar kodningen för `New-ModuleManifest` till UTF (ingen BOM) på andra plattformar än Windows-plattformar.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Förhindra att `Get-ChildItem` återkommer till symlinks (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Den här ändringen ger `Get-ChildItem` mer i rad med UNIX-`ls -r` och inbyggda Windows `dir /s`-kommandon. Precis som de nämnda kommandona visar cmdleten symboliska länkar till kataloger som hittades under rekursion, men rekursivt inte in dem.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Korrigera `Get-Content -Delimiter` att inte inkludera avgränsaren i de returnerade raderna [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Tidigare var de utdata som användes när du använde `Get-Content -Delimiter` inkonsekventa och praktiska eftersom det krävde ytterligare bearbetning av data för att ta bort avgränsaren. Den här ändringen tar bort avgränsaren i returnerade rader.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Implementera format-hex i C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

Parametern `-Raw` är nu "No-OP" (i så fall inget). Om du fortsätter kommer alla utdata att visas med en sann representation av siffror som innehåller alla byte för dess typ (vilken `-Raw` parameter utfördes innan ändringen).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>PowerShell som standard gränssnitt fungerar inte med skript kommandot [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

I UNIX är det en konvention för gränssnitt att acceptera `-i` för ett interaktivt gränssnitt och många verktyg förväntar sig detta beteende (`script` till exempel och när du ställer in PowerShell som standard gränssnitt) och anropar gränssnittet med `-i`-växeln. Den här ändringen delas upp i `-i` tidigare kunde användas som kort hand för att matcha `-inputformat` som nu måste vara `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Skriv åtgärd i get-ComputerInfo egenskaps namn [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` skrevs felstavat som `BiosSeralNumber` och har ändrats till rätt stavning.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Lägg till `Get-StringHash`-och `Get-FileHash`-cmdletar [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Den här ändringen är att vissa hash-algoritmer inte stöds av CoreFX, vilket innebär att de inte längre är tillgängliga:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Lägg till verifiering på `Get-*`-cmdletar där skicka $null returnerar alla objekt i stället för fel [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Att skicka `$null` till något av följande genererar nu ett fel:

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

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Lägg till stöd för utökat logg fils format för W3C i `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Tidigare kan `Import-Csv`-cmdleten inte användas för att importera loggfilerna direkt i utökat logg format för W3C och ytterligare åtgärder krävs. Med den här ändringen stöds W3C Extended Log-formatet.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Parameter bindnings problem med `ValueFromRemainingArguments` i PS-funktioner [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` returnerar nu värdena som en matris i stället för ett enda värde som är en matris.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion` tas bort från `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Ta bort egenskapen `BuildVersion` från `$PSVersionTable`. Den här egenskapen är kopplad till Windows build-versionen. I stället rekommenderar vi att du använder `GitCommitId` för att hämta den exakta versionen av PowerShell Core.

### <a name="changes-to-web-cmdlets"></a>Ändringar av webb-cmdletar

De underliggande .NET API: erna för webb-cmdletar har ändrats till `System.Net.Http.HttpClient`. Den här ändringen ger många fördelar. Men den här ändringen tillsammans med en brist på interoperabilitet med Internet Explorer har resulterat i flera större ändringar i `Invoke-WebRequest` och `Invoke-RestMethod`.

- `Invoke-WebRequest` stöder nu endast grundläggande HTML-parsning. `Invoke-WebRequest` returnerar alltid ett `BasicHtmlWebResponseObject`-objekt. Egenskaperna för `ParsedHtml` och `Forms` har tagits bort.
- `BasicHtmlWebResponseObject.Headers` värden är nu `String[]` i stället för `String`.
- `BasicHtmlWebResponseObject.BaseResponse` är nu ett `System.Net.Http.HttpResponseMessage`-objekt.
- Egenskapen `Response` i Web cmdlet-undantag är nu ett `System.Net.Http.HttpResponseMessage` objekt.
- Strikt rubrik tolkning för RFC är nu standard för `-Headers` och `-UserAgent` parameter. Detta kan kringgås med `-SkipHeaderValidation`.
- `file://`-och `ftp://`-URI-scheman stöds inte längre.
- `System.Net.ServicePointManager` inställningar inte längre används.
- Det finns för närvarande ingen certifikatbaserad autentisering tillgänglig på macOS.
- Om du använder `-Credential` över en `http://` URI resulterar det i ett fel. Använd en `https://`-URI eller ange parametern `-AllowUnencryptedAuthentication` för att ignorera felet.
- `-MaximumRedirection` skapar nu ett avslutande fel när omdirigerings försöken överskrider den angivna gränsen i stället för att returnera resultatet av den senaste omdirigeringen.
