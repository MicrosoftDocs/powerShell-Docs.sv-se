---
ms.date: 02/03/2020
keywords: PowerShell, Core
title: Bryta ändringar för PowerShell 6,0
description: Den här artikeln sammanfattar skillnaderna mellan Windows PowerShell 5,1 och PowerShell 6,0.
ms.openlocfilehash: b53365ee72e6a6e85faa56125a8aa7961d3ecc7f
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96840139"
---
# <a name="breaking-changes-for-powershell-6x"></a>Bryta ändringar för PowerShell 6. x

## <a name="features-no-longer-available-in-powershell-core"></a>Funktioner som inte längre är tillgängliga i PowerShell Core

### <a name="modules-not-shipped-for-powershell-6x"></a>Moduler som inte levererats för PowerShell 6. x

För olika kompatibilitetsproblem ingår inte följande moduler i PowerShell 6.

- ISE
- Microsoft. PowerShell. LocalAccounts
- Microsoft. PowerShell. ODataUtils
- Microsoft. PowerShell. operation. Validation
- PSScheduledJob
- PSWorkflow
- PSWorkflowUtility

### <a name="powershell-workflow"></a>PowerShell-arbetsflöde

[PowerShell-arbetsflöde][workflow] är en funktion i Windows PowerShell som bygger ovanpå [Windows Workflow Foundation (WF)][workflow-foundation] som gör det möjligt att skapa robusta Runbooks för långvariga eller parallella uppgifter.

På grund av brist på stöd för Windows Workflow Foundation i .NET Core stöder vi inte PowerShell-arbetsflöde i PowerShell Core.

I framtiden skulle vi vilja aktivera inbyggd parallellitet/samtidighet i PowerShell-språket utan att behöva använda PowerShell-arbetsflöde.

Om du behöver använda kontroll punkter för att återuppta ett skript efter det att operativ systemet har startats om, rekommenderar vi att du använder Schemaläggaren för att köra ett skript på Start av operativ systemet, men skriptet måste ha ett eget tillstånd (som att spara det i en fil).

[workflow]: /previous-versions/powershell/scripting/components/workflows-guide
[workflow-foundation]: /dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Anpassade snapin-moduler

[PowerShell-snapin-moduler][snapin] är en föregående aktivitet till PowerShell-moduler som inte har omfattande antagande i PowerShell-communityn.

På grund av komplexiteten vid stöd för snapin-moduler och deras brist på användning i communityn stöder vi inte längre anpassade snapin-moduler i PowerShell Core.

Idag tar detta upp `ActiveDirectory` och `DnsClient` moduler i Windows och Windows Server.

[snapin]: /powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>WMI v1-cmdletar

På grund av komplexiteten med stöd för två uppsättningar WMI-baserade moduler tog vi bort WMI v1-cmdletar från PowerShell Core:

- `Register-WmiEvent`
- `Set-WmiInstance`
- `Invoke-WmiMethod`
- `Get-WmiObject`
- `Remove-WmiObject`

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

På grund av användning av API: er som inte stöds, `Microsoft.PowerShell.LocalAccounts` har tagits bort från PowerShell Core tills en bättre lösning har hittats.

### <a name="new-webserviceproxy-cmdlet-removed"></a>`New-WebServiceProxy` cmdlet borttagen

.NET Core har inte stöd för Windows Communication Framework, som tillhandahåller tjänster för att använda SOAP-protokollet. Den här cmdleten togs bort eftersom den kräver SOAP.

### <a name="-transaction-cmdlets-removed"></a>`*-Transaction` cmdletar har tagits bort

Dessa cmdletar hade mycket begränsad användning. Beslutet har fattats för att avbryta stödet för dem.

- `Complete-Transaction`
- `Get-Transaction`
- `Start-Transaction`
- `Undo-Transaction`
- `Use-Transaction`

### <a name="security-cmdlets-not-available-on-non-windows-platforms"></a>Säkerhets-cmdletar är inte tillgängliga på plattformar som inte är Windows-plattformar

- `Get-Acl`
- `Set-Acl`
- `Get-AuthenticodeSignature`
- `Set-AuthenticodeSignature`
- `Get-CmsMessage`
- `Protect-CmsMessage`
- `Unprotect-CmsMessage`
- `New-FileCatalog`
- `Test-FileCatalog`

### <a name="-computerand-other-windows-specific-cmdlets"></a>`*-Computer`och andra Windows-Specific-cmdletar

På grund av användning av API: er som inte stöds har följande cmdlets tagits bort från PowerShell Core tills en bättre lösning har hittats.

- `Get-Clipboard`
- `Set-Clipboard`
- `Add-Computer`
- `Checkpoint-Computer`
- `Remove-Computer`
- `Restore-Computer`
- `Reset-ComputerMachinePassword`
- `Disable-ComputerRestore`
- `Enable-ComputerRestore`
- `Get-ComputerRestorePoint`
- `Test-ComputerSecureChannel`
- `Get-ControlPanelItem`
- `Show-ControlPanelItem`
- `Get-HotFix`
- `Clear-RecycleBin`
- `Update-List`
- `Out-Printer`
- `ConvertFrom-String`
- `Convert-String`

### <a name="-counter-cmdlets"></a>`*-Counter` cmdletar

På grund av användning av API: er som inte stöds, `*-Counter` har tagits bort från PowerShell Core tills en bättre lösning har hittats.

### <a name="-eventlog-cmdlets"></a>`*-EventLog` cmdletar

På grund av användning av API: er som inte stöds, `*-EventLog` har tagits bort från PowerShell-kärnan. tills en bättre lösning har hittats. `Get-WinEvent` och `New-WinEvent` är tillgängliga för att hämta och skapa händelser i Windows.

### <a name="cmdlets-that-use-wpf-removed"></a>Cmdletar som använder WPF borttagna

Windows Presentation Framework stöds inte på CoreCLR. Följande cmdletar påverkas:

- `Show-Command`
- `Out-GridView`
- Parametern **ShowWindow** för `Get-Help`

### <a name="some-dsc-cmdlets-removed"></a>Vissa DSC-cmdletar har tagits bort

- `Get-DscConfiguration`
- `Publish-DscConfiguration`
- `Restore-DscConfiguration`
- `Start-DscConfiguration`
- `Stop-DscConfiguration`
- `Test-DscConfiguration`
- `Update-DscConfiguration`
- `Remove-DscConfigurationDocument`
- `Get-DscConfigurationStatus`
- `Disable-DscDebug`
- `Enable-DscDebug`
- `Get-DscLocalConfigurationManager`
- `Set-DscLocalConfigurationManager`
- `Invoke-DscResource`

## <a name="enginelanguage-changes"></a>Motor/språk ändringar

### <a name="rename-powershellexe-to-pwshexe-5101"></a>Byt namn `powershell.exe` till `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

För att ge användarna ett deterministiskt sätt att anropa PowerShell Core på Windows (till skillnad från Windows PowerShell) ändrades binärfilen för PowerShell-kärnan till `pwsh.exe` i Windows och `pwsh` på andra plattformar än Windows-plattformar.

Det förkortade namnet är också konsekvent med namngivning av gränssnitt på andra plattformar än Windows-plattformar.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193"></a>Infoga inte rad brytningar i utdata (förutom tabeller) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Tidigare var utdata justerade till bredden på konsolen och rad brytningarna lades till i konsolens slut punkt, vilket innebär att resultatet inte blev omformaterat som förväntat om terminalfönstret ändrades. Den här ändringen tillämpades inte i tabeller eftersom rad brytningar krävs för att hålla kolumnerna justerade.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432"></a>Hoppa över null-Elements kontroll för samlingar med en värde typs element typ [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

`Mandatory` `ValidateNotNull` `ValidateNotNullOrEmpty` Hoppa över null-elementet för parametern och attributen om samlingens element typ är värdetyp.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369"></a>Ändra `$OutputEncoding` till att använda `UTF-8 NoBOM` encoding i stället för ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

Föregående kodning, ASCII (7-bitars), resulterar i en felaktig ändring av utdata i vissa fall. Den här ändringen är att göra `UTF-8 NoBOM` standardvärdet, vilket bevarar Unicode-utdata med en kodning som stöds av de flesta verktyg och operativ system.

### <a name="remove-allscope-from-most-default-aliases-5268"></a>Ta bort `AllScope` från de flesta Standardalias [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

För att påskynda skapandet av omfattningar, `AllScope` har tagits bort från de flesta Standardalias. `AllScope` har lämnats för några ofta använda alias där sökningen var snabbare.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113"></a>`-Verbose` och `-Debug` åsidosätter inte längre `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Tidigare, om `-Verbose` eller `-Debug` har angetts, overrode beteendet `$ErrorActionPreference` . Med den här ändringen `-Verbose` och `-Debug` påverkar inte längre beteendet för `$ErrorActionPreference` .

## <a name="cmdlet-changes"></a>Cmdlet-ändringar

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320"></a>Invoke-RestMethod returnerar inte värdefull information när inga data returneras. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

När ett API returnerar bara `null` , serialiserade Invoke-RestMethod detta som sträng i `"null"` stället för `$null` . Den här ändringen korrigerar logiken i `Invoke-RestMethod` för korrekt serialisering av ett giltigt JSON-värde för enkel värde `null` som `$null` .

### <a name="remove--protocol-from--computer-cmdlets-5277"></a>Ta bort `-Protocol` från `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

På grund av problem med RPC-fjärrkommunikation i CoreFX (särskilt på plattformar som inte är Windows) och säkerställer en konsekvent fjärrhantering i PowerShell, `-Protocol` har parametern tagits bort från `\*-Computer` cmdletarna. DCOM stöds inte längre för fjärr kommunikation. Följande cmdletar stöder bara WSMAN-fjärr kommunikation:

- Rename-Computer
- Restart-Computer
- Stop-Computer

### <a name="remove--computername-from--service-cmdlets-5090"></a>Ta bort `-ComputerName` från `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

`-ComputerName`Parametern har tagits bort från cmdlets för att uppmuntra en konsekvent användning av PSRP `*-Service` .

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197"></a>Korrigera `Get-Item -LiteralPath a*b` om den `a*b` inte redan finns för att returnera fel [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Tidigare `-LiteralPath` skulle ett jokertecken behandla det på samma sätt som `-Path` och om jokertecken inte hittade några filer, stängs det tyst. Rätt beteende bör vara det `-LiteralPath` exakta värdet, så om filen inte finns, bör den innehålla fel. Ändra är att hantera jokertecken som används med `-Literal` literal.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134"></a>`Import-Csv` bör gälla `PSTypeNames` vid import när typ information finns i CSV- [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Tidigare bevarade objekt som exporter ATS med `Export-CSV` med `TypeInformation` importerad med `ConvertFrom-Csv` inte typ informationen. Den här ändringen lägger till typ informationen till `PSTypeNames` medlemmen om den är tillgänglig från CSV-filen.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131"></a>`-NoTypeInformation` ska vara standard `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Den här ändringen gjordes för att lösa kundfeedback om standard beteendet för `Export-CSV` att inkludera typ information.

Tidigare skulle cmdleten skriva en kommentar som den första raden som innehåller objektets typnamn. Ändringen är att ignorera detta som standard eftersom det inte tolkas av de flesta verktyg. Används `-IncludeTypeInformation` för att behålla det tidigare beteendet.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112"></a>Webb-cmdlets bör varna när `-Credential` skickas via okrypterade anslutningar [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

När du använder HTTP skickas innehåll inklusive lösen ord som klartext. Den här ändringen är att inte tillåta detta som standard och returnera ett fel om autentiseringsuppgifterna skickas på ett osäkert sätt. Användare kan kringgå detta genom att använda `-AllowUnencryptedAuthentication` växeln.

## <a name="api-changes"></a>API-ändringar

### <a name="remove-addtypecommandbase-class-5407"></a>Ta bort `AddTypeCommandBase` klass [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

`AddTypeCommandBase`Klassen har tagits bort från `Add-Type` för att förbättra prestandan. Den här klassen används endast av Add-Type-cmdleten och bör inte påverka användare.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080"></a>Förena cmdletar med parametern `-Encoding` som typ `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

`-Encoding`Värdet `Byte` har tagits bort från cmdletarna för fil Systems Provider. En ny parameter `-AsByteStream` används nu för att ange att en byte-dataström krävs som indata eller att utdata är en data ström i byte.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055"></a>Lägg till bättre fel meddelande för Tom och null- `-UFormat` parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Tidigare visas ett fel meddelande om att en tom format sträng skickades till `-UFormat` . Ett mer beskrivande fel har lagts till.

### <a name="clean-up-console-code-4995"></a>Rensa konsol kod [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Följande funktioner har tagits bort eftersom de inte stöds i PowerShell Core, och det finns inga planer på att lägga till stöd som de finns för äldre skäl för Windows PowerShell: `-psconsolefile` switch och kod, `-importsystemmodules` växel och kod och kod för ändring av teckensnitt.

### <a name="removed-runspaceconfiguration-support-4942"></a>`RunspaceConfiguration`Stöd [#4942](https://github.com/PowerShell/PowerShell/issues/4942) har tagits bort

När du tidigare skapade en PowerShell-körnings utrymme via programmering med hjälp av API: et kan du använda det äldre [`RunspaceConfiguration`][runspaceconfig] eller senare [`InitialSessionState`][iss] . Den här ändringen har tagit bort stöd för `RunspaceConfiguration` och stöder bara `InitialSessionState` .

[runspaceconfig]: /dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: /dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923"></a>`CommandInvocationIntrinsics.InvokeScript` bind argument till `$input` i stället för `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

En felaktig position av en parameter resulterade i argumenten som angavs som indatamängd i stället för som argument.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903"></a>Ta bort växeln som inte stöds `-showwindow` från `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` är beroende av WPF, vilket inte stöds på CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866"></a>Tillåt att * används i register Sök vägen för `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Tidigare `-LiteralPath` skulle ett jokertecken behandla det på samma sätt som `-Path` och om jokertecken inte hittade några filer, stängs det tyst. Rätt beteende bör vara det `-LiteralPath` exakta värdet, så om filen inte finns, bör den innehålla fel. Ändra är att hantera jokertecken som används med `-Literal` literal.

### <a name="fix-set-service-failing-test-4802"></a>Korrigera `Set-Service` misslyckad test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Om användes tidigare `New-Service -StartupType foo` `foo` ignorerades och tjänsten skapades med en typ av standard starttyp. Den här ändringen är att explicit utlösa ett fel för en ogiltig starttyp.

### <a name="rename-isosx-to-ismacos-4700"></a>Byt namn `$IsOSX` till `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

Namngivningen i PowerShell bör vara konsekvent med vår namn och överensstämmer med Apples användning av macOS i stället för OSX. Men för att kunna läsa och ständigt kan vi hålla sig till Pascal-höljet.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573"></a>Gör fel meddelandet konsekvent när ogiltigt skript skickas till fil, vilket är ett bättre fel när ett tvetydigt argument har skickats [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Ändra avslutnings koderna för `pwsh.exe` att anpassas efter UNIX-konventioner

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302-4303"></a>Borttagning av `LocalAccount` och cmdlets från  `Diagnostics` moduler. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

På grund av API: er som inte stöds `LocalAccounts` har modulen och `Counter` cmdletarna i `Diagnostics` modulen tagits bort tills en bättre lösning har hittats.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036"></a>Det går inte att köra PowerShell-skriptet med bool-parametern [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Tidigare använde **powershell.exe** (nu **pwsh.exe**) för att köra ett PowerShell-skript som `-File` inte har tillhandahållit något sätt att skicka `$true` / `$false` som parameter värden. Stöd för `$true` / `$false` som parsade värden till parametrar har lagts till. Växlings värden stöds också som för närvarande dokumenterad syntax fungerar inte.

### <a name="remove-clrversion-property-from-psversiontable-4027"></a>Ta bort `ClrVersion` egenskap från `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

`ClrVersion`Egenskapen i `$PSVersionTable` är inte användbar med CoreCLR, slutanvändare ska inte använda det värdet för att fastställa kompatibiliteten.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019"></a>Ändra positions parameter för `powershell.exe` från `-Command` till `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Aktivera Shebang användning av PowerShell på andra plattformar än Windows-plattformar. Det innebär att du kan skapa en skript-körbar fil som anropar PowerShell automatiskt i stället för att uttryckligen anropa det på UNIX-baserade system `pwsh` . Det innebär också att du nu kan göra saker som `powershell foo.ps1` eller `powershell fooScript` utan att ange `-File` . Den här ändringen kräver dock att du uttryckligen anger `-c` eller `-Command` när du försöker göra saker som `powershell.exe Get-Command` .

### <a name="implement-unicode-escape-parsing-3958"></a>Implementera tolkning av Unicode-Escape [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u####`` eller `` `u{####}`` konverteras till motsvarande Unicode-tecken. Om du vill mata ut en litteral `` `u`` kan du undanta bakticket: ``` ``u``` .

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940"></a>Ändra `New-ModuleManifest` kodningen till `UTF8NoBOM` på andra plattformar än Windows-plattformar [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Tidigare `New-ModuleManifest` skapade psd1-manifest i UTF-16 med BOM och skapar ett problem för Linux-verktyg. Den här avbrytande ändringen ändrar kodningen `New-ModuleManifest` till UTF (ingen BOM) på andra plattformar än Windows-plattformar.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780"></a>Förhindra att `Get-ChildItem` återkommer till symlinks (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Den här ändringen ger `Get-ChildItem` mer i rad med UNIX- `ls -r` och inbyggda Windows- `dir /s` kommandon. Precis som de nämnda kommandona visar cmdleten symboliska länkar till kataloger som hittades under rekursion, men rekursivt inte in dem.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706"></a>Korrigera `Get-Content -Delimiter` för att inte inkludera avgränsaren i de returnerade raderna [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Tidigare var de utdata `Get-Content -Delimiter` som användes inkonsekventa och olämpliga eftersom det krävde ytterligare bearbetning av data för att ta bort avgränsaren. Den här ändringen tar bort avgränsaren i returnerade rader.

### <a name="implement-format-hex-in-c-3320"></a>Implementera Format-Hex i C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

`-Raw`Parametern är nu en "No-OP" (där det inte gör något). Om du fortsätter kommer alla utdata att visas med en sann representation av siffror som innehåller alla byte för dess typ (vad den `-Raw` här ändringen hade innan ändringen).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319"></a>PowerShell som standard gränssnitt fungerar inte med skript kommandot [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

I UNIX är det en konvention för gränssnitt att acceptera `-i` för ett interaktivt gränssnitt och många verktyg förväntar sig detta beteende ( `script` till exempel och när du ställer in PowerShell som standard gränssnitt) och anropar gränssnittet med `-i` växeln. Den här ändringen är Sparad i som `-i` tidigare kunde användas som kort för att matcha `-inputformat` , vilket nu måste vara `-in` .

### <a name="typo-fix-in-get-computerinfo-property-name-3167"></a>Korrigera skrivfel i Get-ComputerInfo egenskaps namn [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` är felstavat `BiosSeralNumber` och har ändrats till rätt stavning.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024"></a>Lägg till `Get-StringHash` och `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Den här ändringen är att vissa hash-algoritmer inte stöds av CoreFX, vilket innebär att de inte längre är tillgängliga:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672"></a>Lägg till verifiering på `Get-*` cmdletar där överföring av $null returnerar alla objekt i stället för fel [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

`$null`Att skicka till något av följande genererar nu ett fel:

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

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482"></a>Lägg till stöd för utökat logg fils format för W3C i `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Tidigare `Import-Csv` kan cmdleten inte användas för att importera loggfilerna direkt i utökat logg format för W3C och ytterligare åtgärder krävs. Med den här ändringen stöds W3C Extended Log-formatet.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035"></a>Parameter bindnings problem med `ValueFromRemainingArguments` i PS functions [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` returnerar nu värdena som en matris i stället för ett enda värde som är en matris.

### <a name="buildversion-is-removed-from-psversiontable-1415"></a>`BuildVersion` har tagits bort från `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Ta bort `BuildVersion` egenskapen från `$PSVersionTable` . Den här egenskapen är kopplad till Windows build-versionen. I stället rekommenderar vi att du använder `GitCommitId` för att hämta den exakta versionen av PowerShell Core.

### <a name="changes-to-web-cmdlets"></a>Ändringar av webb-cmdletar

De underliggande .NET API: erna för webb-cmdletarna har ändrats till `System.Net.Http.HttpClient` . Den här ändringen ger många fördelar. Men den här ändringen tillsammans med en brist på interoperabilitet med Internet Explorer har resulterat i flera större ändringar i `Invoke-WebRequest` och `Invoke-RestMethod` .

- `Invoke-WebRequest` stöder nu bara grundläggande HTML-parsning. `Invoke-WebRequest` returnerar alltid ett `BasicHtmlWebResponseObject` objekt. `ParsedHtml`Egenskaperna och `Forms` har tagits bort.
- `BasicHtmlWebResponseObject.Headers` värdena är nu i `String[]` stället för `String` .
- `BasicHtmlWebResponseObject.BaseResponse` är nu ett `System.Net.Http.HttpResponseMessage` objekt.
- `Response`Egenskapen för webb-cmdlet-undantag är nu ett `System.Net.Http.HttpResponseMessage` objekt.
- Strikt rubrik tolkning för RFC är nu standard för `-Headers` parametern och `-UserAgent` . Detta kan kringgås med `-SkipHeaderValidation` .
- `file://` och `ftp://` URI-scheman stöds inte längre.
- `System.Net.ServicePointManager` inställningarna stöds inte längre.
- Det finns för närvarande ingen certifikatbaserad autentisering tillgänglig på macOS.
- Om du använder `-Credential` över en `http://` URI kommer det att resultera i ett fel. Använd en `https://` URI eller ange `-AllowUnencryptedAuthentication` parametern för att ignorera felet.
- `-MaximumRedirection` genererar nu ett avslutande fel när omdirigerings försök överskrider den angivna gränsen i stället för att returnera resultaten av den senaste omdirigeringen.
- I PowerShell 6,2 gjordes en ändring som standard till UTF-8-kodning för JSON-svar. Om ingen teckenuppsättning anges för ett JSON-svar ska standard kodningen vara UTF-8 per RFC 8259.
