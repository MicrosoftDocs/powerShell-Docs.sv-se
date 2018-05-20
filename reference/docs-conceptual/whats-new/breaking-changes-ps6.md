---
ms.date: 05/17/2018
keywords: PowerShell, kärnor
title: Gör ändringar för PowerShell 6.0
ms.openlocfilehash: 60ce7a1676403bb08b57bf852ba725acde86a30c
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2018
---
# <a name="breaking-changes-for-powershell-60"></a>Gör ändringar för PowerShell 6.0

## <a name="features-no-longer-available-in-powershell-core"></a>Funktioner som inte längre är tillgängliga i PowerShell Core

### <a name="powershell-workflow"></a>PowerShell-arbetsflöde

[PowerShell-arbetsflöde] [ workflow] är en funktion i Windows PowerShell som bygger ovanpå [Windows Workflow Foundation (WF)] [ workflow-foundation] som kan skapa robust runbooks för tidskrävande eller paralleliserad uppgifter.

På grund av bristande stöd för Windows Workflow Foundation i .NET Core fortsätter vi inte att stödja PowerShell-arbetsflöde i PowerShell Core.

I framtiden kommer vill vi aktivera native parallellitet/parallellkörning i PowerShell-språk utan att behöva PowerShell-arbetsflöde.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Anpassade snapin-moduler

[PowerShell-snapin-moduler] [ snapin] är en föregångare till PowerShell-moduler som inte har omfattande införande i PowerShell-community.

På grund av svårigheterna stödja snapin-moduler och deras bristande användning i gemenskapen stöder vi inte längre anpassade snapin-moduler i PowerShell Core.

Idag är det bryts det `ActiveDirectory` och `DnsClient` moduler i Windows och Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>WMI-v1-cmdlets

På grund av svårigheterna stödja två uppsättningar av WMI-baserade moduler vi tagit bort WMI-v1-cmdlets från PowerShell Core:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

I stället bör du använda CIM (aka WMI v2)-cmdletar som ger samma funktionalitet med nya funktioner och förbättrade syntax:

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

Användning av stöds inte API: er, `Microsoft.PowerShell.LocalAccounts` har tagits bort från PowerShell Core tills en bättre lösning hittas.

### <a name="-counter-cmdlets"></a>`*-Counter`-cmdletar

Användning av stöds inte API: er i `*-Counter` har tagits bort från PowerShell Core tills en bättre lösning hittas.

## <a name="enginelanguage-changes"></a>Ändringar av motorn/språk

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Byt namn på `powershell.exe` till `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

För att ge användarna en deterministisk sätt att anropa PowerShell Core för Windows (i stället för Windows PowerShell), PowerShell Core binärfilen har ändrats till `pwsh.exe` i Windows och `pwsh` på Windows-plattformar.

En förkortning stämmer med namngivning av tankar på Windows-plattformar.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Infoga inte radbrytningar till utdata (förutom tabeller) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Tidigare utdata har justerats till konsolen bredd och radbrytningar har lagts till på slutbredden i konsolen, vilket innebär att inte hämta omformateras utdata som väntat om terminalen har ändrats. Den här ändringen har inte tillämpats på tabeller, som behövs för att hålla kolumnerna justerad radbrytningar.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Hoppa över kontrollen null-element för samlingar med en värdetyp elementtyp [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

För den `Mandatory` parameter och `ValidateNotNull` och `ValidateNotNullOrEmpty` attribut, hoppa över kontrollen av null-element om samlingstyp element är värdetyp.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Ändra `$OutputEncoding` att använda `UTF-8 NoBOM` kodningen i stället för ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

Den tidigare kodning, ASCII (7-bitars) skulle leda till felaktig ändring av utdata i vissa fall. Den här ändringen är att göra `UTF-8 NoBOM` standard, vilket bevarar Unicode-utdata med kodning stöds av de flesta verktyg och operativsystem.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Ta bort `AllScope` från de flesta standardalias [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Påskynda scope skapa `AllScope` har tagits bort från de flesta standardalias. `AllScope` lämnades för några vanliga alias där sökningen var snabbare.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` och `-Debug` längre åsidosätter `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Tidigare, om `-Verbose` eller `-Debug` angavs, det overrode beteendet för `$ErrorActionPreference`. Med den här ändringen `-Verbose` och `-Debug` längre påverkar `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Cmdlet-ändringar

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Anropa RestMethod returnerar inte praktisk information när inga data returneras. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

När en API returnerar bara `null`, Invoke-RestMethod serialisering detta som sträng `"null"` i stället för `$null`. Den här ändringen åtgärdas logiken i `Invoke-RestMethod` att serialisera ett giltigt enskilt value JSON korrekt `null` literal som `$null`.

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Ta bort `-ComputerName` från `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

På grund av problem med RPC-fjärrkommunikation i CoreFX (särskilt på Windows-plattformar) och säkerställa en konsekvent fjärrkommunikationsupplevelse i PowerShell den `-ComputerName` parametern har tagits bort från den `\*-Computer` cmdlets. Använd `Invoke-Command` i stället för att köra cmdlet: ar från en fjärrdator.

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Ta bort `-ComputerName` från `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

För att uppmuntra konsekvent användningen av PSRP, den `-ComputerName` parametern har tagits bort från `*-Service` cmdlets.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Åtgärda `Get-Item -LiteralPath a*b` om `a*b` inte finns för att returnera fel [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Tidigare `-LiteralPath` angivna jokertecken kan behandla det samma som `-Path` och om inga filer hittades i jokertecknet den tyst skulle avslutas. Korrekt beteende ska vara som `-LiteralPath` är literal så om filen inte finns, bör det fel. Ändringen är att behandla jokertecken som används med `-Literal` som literal.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` gäller `PSTypeNames` vid importen när typinformation finns i CSV-filen [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Tidigare objekt exporteras med `Export-CSV` med `TypeInformation` importeras med `ConvertFrom-Csv` inte behåller informationen. Den här ändringen läggs informationen till `PSTypeNames` medlem om de är tillgängliga från CSV-filen.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` bör vara standard på `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Den här ändringen gjordes på adressen kundfeedback på standardbeteendet för `Export-CSV` med typen information.

Tidigare skulle cmdlet utdata en kommentar som den första raden som innehåller namnet på objektet. Ändringen är att förhindra detta som standard eftersom den inte kan tolkas i de flesta verktygen. Använd `-IncludeTypeInformation` att behålla den tidigare funktionen.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>-Cmdletar för bör varna när `-Credential` skickas över okrypterade anslutningar [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

När du använder HTTP, skickas innehåll inklusive lösenord som klartext. Den här ändringen är att inte tillåta detta som standard och ett fel returneras om autentiseringsuppgifter skickas på ett säkert sätt. Användare kan åsidosätta detta genom att använda den `-AllowUnencryptedAuthentication` växla.

## <a name="api-changes"></a>API-ändringar

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Ta bort `AddTypeCommandBase` klassen [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

Den `AddTypeCommandBase` klass har tagits bort från `Add-Type` att förbättra prestanda. Den här klassen används endast av cmdlet Add-typ och bör inte påverkar användare.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Förena cmdlets med parametern `-Encoding` måste vara av typen `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

Den `-Encoding` värdet `Byte` har tagits bort från filsystemet provider-cmdlets. En ny parameter `-AsByteStream`, nu används för att ange att det krävs en byte-dataström som indata eller att utdata är en dataström med byte.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Lägg till bättre felmeddelandet tom och null `-UFormat` parametern [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Tidigare, när du skickar ett tomt format sträng till `-UFormat`, visas ett felmeddelande om unhelpful. Ett mer beskrivande fel har lagts till.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Rensa konsolen kod [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Följande funktioner har tagits bort eftersom de inte stöds i PowerShell Core och det finns inga planer på att lägga till stöd för eftersom de finns äldre skäl för Windows PowerShell: `-psconsolefile` växeln och kod, `-importsystemmodules` växel och koden och teckensnitt ändra koden.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Ta bort `RunspaceConfiguration` stöder [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

Tidigare, när du skapar ett PowerShell-körningsutrymme programmässigt med hjälp av API kunde du använda en äldre [ `RunspaceConfiguration` ] [ runspaceconfig] eller den senare [ `InitialSessionState` ] [ iss]. Den här ändringen inte längre stöd för `RunspaceConfiguration` och stöder endast `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` binda argument till `$input` i stället för `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

En felaktig placering av en parameter resulterade i argument angavs som indata i stället för som argument.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Ta bort stöds inte `-showwindow` växla från `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` förlitar sig på WPF, vilket inte stöds i CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>Tillåt * som ska användas i registersökvägen för `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Tidigare `-LiteralPath` angivna jokertecken kan behandla det samma som `-Path` och om inga filer hittades i jokertecknet den tyst skulle avslutas. Korrekt beteende ska vara som `-LiteralPath` är literal så om filen inte finns, bör det fel. Ändringen är att behandla jokertecken som används med `-Literal` som literal.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Åtgärda `Set-Service` misslyckas test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Tidigare, om `New-Service -StartupType foo` användes, `foo` ignorerades och tjänsten har skapats med vissa standard starttyp. Den här ändringen är att skapa egna ett fel för en ogiltig starttyp.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Byt namn på `$IsOSX` till `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

Namnge i PowerShell ska stämma överens med vår namngivning och följa Apples användning av macOS i stället för OS x. Men för att läsa och konsekvent vi håller dig till Pascal skiftläge.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Gör fel meddelande konsekvent när skriptet är ogiltigt och skickas till - fil, bättre fel när de skickas tvetydig argumentet [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Ändra slutkoder av `pwsh.exe` att justera Unix konventioner

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Borttagning av `LocalAccount` och cmdlet: ar från `Diagnostics` moduler. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

På grund av stöds inte API: er, den `LocalAccounts` modulen och `Counter` cmdletar i den `Diagnostics` module togs bort tills en bättre lösning hittas.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>Kör powershell-skript med boolesk parameter fungerar inte [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Tidigare med hjälp av powershell.exe (nu `pwsh.exe`) att köra ett PowerShell-skript med `-File` som inte går att skicka $true/$false som parametervärden. Stöd för $true/$false som parsade värden för parametrar har lagts till. Växeln-värden stöds också som för närvarande dokumenterade syntax inte fungerar.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Ta bort `ClrVersion` egenskap från `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

Den `ClrVersion` -egenskapen för `$PSVersionTable` är inte användbart med CoreCLR slutanvändare bör inte använda värdet för att fastställa kompatibilitet.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Ändra namngivna parametern för `powershell.exe` från `-Command` till `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Aktivera shebang användningen av PowerShell på Windows-plattformar. Detta innebär på Unix-baserade system du ett skript körbar fil som kan anropa PowerShell automatiskt i stället för explicit anropar `pwsh`. Detta betyder också att du kan nu göra sådant som `powershell foo.ps1` eller `powershell fooScript` utan att ange `-File`. Den här ändringen nu kräver dock att du anger explicit `-c` eller `-Command` när du försöker göra sådant som `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Implementera Unicode-escape-parsning [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u#### `` eller `` `u{####} `` konverteras till motsvarande Unicode-tecken. Ta en literal `` `u ``, undanta backtick: ``` ``u ```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Ändra `New-ModuleManifest` kodning till `UTF8NoBOM` på Windows-plattformar [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Tidigare `New-ModuleManifest` skapar psd1 manifesten i UTF-16 med struktur, skapar problem för Linux-verktyg. Senaste ändringen ändras kodning av `New-ModuleManifest` vara UTF (utan BOM) i Windows-plattformar.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Förhindra `Get-ChildItem` från recursing till symlinks (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Den här ändringen ger `Get-ChildItem` mer i enlighet med Unix `ls -r` och Windows `dir /s` inbyggda kommandon. Precis som kommandona nämnda cmdlet visar symboliska länkar till kataloger under rekursion hittades, men recurse inte i dem.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Åtgärda `Get-Content -Delimiter` att inte inkludera avgränsaren i returnerade rader [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Tidigare utdata när du använder `Get-Content -Delimiter` har inkonsekventa och olämplig eftersom det krävs ytterligare bearbetning av data att ta bort avgränsaren. Den här ändringen tar bort avgränsaren i returnerade rader.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Implementera hexadecimalt Format i C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

Den `-Raw` parameter är nu en ”no-op” (att den inte gör något). Framöver alla utdata visas med en exakt representation av siffror som omfattar alla byte för dess typ (vad den `-Raw` parametern gjorde formellt innan den här ändringen).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>PowerShell som ett standardgränssnitt fungerar inte med skriptkommandot [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

För Unix är det en konvention för tankar att acceptera `-i` för många verktyg och en interaktiv shell räknar problemet (`script` till exempel och när du anger PowerShell som standardgränssnittet) och anropar shell med den `-i` växla. Den här ändringen bryter som `-i` tidigare kan användas som kort manuellt så att den matchar `-inputformat`, som nu måste vara `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Korrigera skrivfel i Get-ComputerInfo egenskapsnamn [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` var felstavat som `BiosSeralNumber` och har ändrats till rätt stavning.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Lägg till `Get-StringHash` och `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Den här ändringen är att vissa hash-algoritmer stöds inte av CoreFX, de är därför inte längre tillgängliga:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Lägga till verifiering på `Get-*` cmdletar där skicka $null returnerar alla objekt i stället för felet [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

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

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Lägga till stöd för W3C utökat loggfilsformat i `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Tidigare var det `Import-Csv` cmdlet kan inte användas direkt Importera loggfiler i utökat loggfilsformat för W3C och ytterligare åtgärder skulle krävas. Utökat loggfilsformat för W3C stöds med den här ändringen.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Parametern bindningsproblem med `ValueFromRemainingArguments` i PS-funktioner [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` Nu returnerar värdena som en matris i stället för ett enda värde som i sin tur är en matris.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion` tas bort från `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Ta bort den `BuildVersion` egenskap från `$PSVersionTable`. Den här egenskapen har kopplat till Windows-versionen. I stället rekommenderar vi att du använder `GitCommitId` att hämta PowerShell Core exakta versionen.

### <a name="changes-to-web-cmdlets"></a>Ändringar av Web-cmdletar

Underliggande .NET API-cmdletar har ändrats till `System.Net.Http.HttpClient`. Den här ändringen ger många fördelar. Men den här ändringen tillsammans med bristande samverkan med Internet Explorer har resulterat i flera viktiga förändringar inom `Invoke-WebRequest` och `Invoke-RestMethod`.

- `Invoke-WebRequest` stöder nu grundläggande HTML parsning endast. `Invoke-WebRequest` returnerar alltid en `BasicHtmlWebResponseObject` objekt. Den `ParsedHtml` och `Forms` egenskaper har tagits bort.
- `BasicHtmlWebResponseObject.Headers` värden är nu `String[]` i stället för `String`.
- `BasicHtmlWebResponseObject.BaseResponse` är nu en `System.Net.Http.HttpResponseMessage` objekt.
- Den `Response` egenskapen på webben Cmdlet undantag är nu en `System.Net.Http.HttpResponseMessage` objekt.
- Strikt RFC sidhuvud parsning nu är standard för den `-Headers` och `-UserAgent` parameter. Detta kan kringgås med `-SkipHeaderValidation`.
- `file://` och `ftp://` URI-scheman stöds inte längre.
- `System.Net.ServicePointManager` inställningarna gäller inte längre.
- Det finns för närvarande inga certifikatbaserad autentisering på macOS.
- Användning av `-Credential` över en `http://` URI resulterar i ett fel. Använd en `https://` URI eller lämna den `-AllowUnencryptedAuthentication` parametern för att ignorera felet.
