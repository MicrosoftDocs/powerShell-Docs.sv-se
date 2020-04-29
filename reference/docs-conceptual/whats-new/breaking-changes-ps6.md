---
ms.date: 02/03/2020
keywords: PowerShell, Core
title: Bryta ändringar för PowerShell 6,0
ms.openlocfilehash: 47ed14cceed86e4dd04a8e0079af00f6a98988ea
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "76995452"
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

[workflow]: /powershell/scripting/components/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Anpassade snapin-moduler

[PowerShell-snapin-moduler][snapin] är en föregående aktivitet till PowerShell-moduler som inte har omfattande antagande i PowerShell-communityn.

På grund av komplexiteten vid stöd för snapin-moduler och deras brist på användning i communityn stöder vi inte längre anpassade snapin-moduler i PowerShell Core.

Idag tar detta upp `ActiveDirectory` och `DnsClient` moduler i Windows och Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

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

På grund av användning av API: er som inte `Microsoft.PowerShell.LocalAccounts` stöds, har tagits bort från PowerShell Core tills en bättre lösning har hittats.

### <a name="new-webserviceproxy-cmdlet-removed"></a>`New-WebServiceProxy`cmdlet borttagen

.NET Core har inte stöd för Windows Communication Framework, som tillhandahåller tjänster för att använda SOAP-protokollet. Den här cmdleten togs bort eftersom den kräver SOAP.

### <a name="-transaction-cmdlets-removed"></a>`*-Transaction`cmdletar har tagits bort

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

### <a name="-counter-cmdlets"></a>`*-Counter`cmdletar

På grund av användning av API: er som inte stöds `*-Counter` , har tagits bort från PowerShell Core tills en bättre lösning har hittats.

### <a name="-eventlog-cmdlets"></a>`*-EventLog`cmdletar

På grund av användning av API: er som inte stöds `*-EventLog` , har tagits bort från PowerShell-kärnan. tills en bättre lösning har hittats. `Get-WinEvent`och `Create-WinEvent` är tillgängliga för att hämta och skapa händelser i Windows.

### <a name="cmdlets-that-use-wpf-removed"></a>Cmdletar som använder WPF borttagna

Windows Presentation Framework stöds inte på CoreCLR. Följande cmdletar påverkas:

- `Show-Command`
- `Out-GridView`
- Parametern **ShowWindow** för`Get-Help`

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

### <a name="rename-powershellexe-to-pwshexe-5101"></a>Byt `powershell.exe` namn `pwsh.exe` till [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

För att ge användarna ett deterministiskt sätt att anropa PowerShell Core på Windows (till skillnad från Windows PowerShell) ändrades binärfilen för PowerShell-kärnan till `pwsh.exe` i Windows och `pwsh` på andra plattformar än Windows-plattformar.

Det förkortade namnet är också konsekvent med namngivning av gränssnitt på andra plattformar än Windows-plattformar.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193"></a>Infoga inte rad brytningar i utdata (förutom tabeller) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Tidigare var utdata justerade till bredden på konsolen och rad brytningarna lades till i konsolens slut punkt, vilket innebär att resultatet inte blev omformaterat som förväntat om terminalfönstret ändrades. Den här ändringen tillämpades inte i tabeller eftersom rad brytningar krävs för att hålla kolumnerna justerade.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432"></a>Hoppa över null-Elements kontroll för samlingar med en värde typs element typ [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

Hoppa över `Mandatory` null- `ValidateNotNull` elementet `ValidateNotNullOrEmpty` för parametern och attributen om samlingens element typ är värdetyp.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369"></a>Ändra `$OutputEncoding` till att `UTF-8 NoBOM` använda ENCODING i stället för ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

Föregående kodning, ASCII (7-bitars), resulterar i en felaktig ändring av utdata i vissa fall. Den här ändringen är att `UTF-8 NoBOM` göra standardvärdet, vilket bevarar Unicode-utdata med en kodning som stöds av de flesta verktyg och operativ system.

### <a name="remove-allscope-from-most-default-aliases-5268"></a>Ta `AllScope` bort från de flesta standardalias [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

För att påskynda skapandet av omfattningar `AllScope` , har tagits bort från de flesta Standardalias. `AllScope`har lämnats för några ofta använda alias där sökningen var snabbare.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113"></a>`-Verbose`och `-Debug` åsidosätter `$ErrorActionPreference` inte längre [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Tidigare, om `-Verbose` eller `-Debug` har angetts, overrode beteendet `$ErrorActionPreference`. Med den här ändringen `-Verbose` och `-Debug` påverkar inte längre beteendet för `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Cmdlet-ändringar

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320"></a>Invoke-RestMethod returnerar inte värdefull information när inga data returneras. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

När ett API returnerar bara `null`, serialiserar Invoke-RestMethod detta som strängen `"null"` i stället för. `$null` Den här ändringen korrigerar logiken i `Invoke-RestMethod` för korrekt serialisering av ett giltigt JSON `null` -värde `$null`för enkel värde som.

### <a name="remove--protocol-from--computer-cmdlets-5277"></a>Ta `-Protocol` bort `*-Computer` från cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

På grund av problem med RPC-fjärrkommunikation i CoreFX (särskilt på plattformar som inte är Windows) och säkerställer en konsekvent fjärrhantering `-Protocol` i PowerShell, har parametern `\*-Computer` tagits bort från cmdletarna. DCOM stöds inte längre för fjärr kommunikation. Följande cmdletar stöder bara WSMAN-fjärr kommunikation:

- Byt namn – dator
- Starta om datorn
- Stoppa – dator

### <a name="remove--computername-from--service-cmdlets-5090"></a>Ta `-ComputerName` bort `*-Service` från cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

`-ComputerName` Parametern har tagits bort från `*-Service` cmdlets för att uppmuntra en konsekvent användning av PSRP.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197"></a>Korrigera `Get-Item -LiteralPath a*b` om `a*b` den inte redan finns för att returnera fel [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

`-LiteralPath` Tidigare skulle ett jokertecken behandla det på samma sätt som `-Path` och om jokertecken inte hittade några filer, stängs det tyst. Rätt beteende bör vara det `-LiteralPath` exakta värdet, så om filen inte finns, bör den innehålla fel. Ändra är att hantera jokertecken som används `-Literal` med literal.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134"></a>`Import-Csv`bör gälla `PSTypeNames` vid import när typ information finns i CSV- [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Tidigare bevarade objekt `Export-CSV` som `TypeInformation` exporter ATS `ConvertFrom-Csv` med med importerad med inte typ informationen. Den här ändringen lägger till typ informationen `PSTypeNames` till medlemmen om den är tillgänglig från CSV-filen.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131"></a>`-NoTypeInformation`ska vara standard `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Den här ändringen gjordes för att lösa kundfeedback om standard beteendet `Export-CSV` för att inkludera typ information.

Tidigare skulle cmdleten skriva en kommentar som den första raden som innehåller objektets typnamn. Ändringen är att ignorera detta som standard eftersom det inte tolkas av de flesta verktyg. Används `-IncludeTypeInformation` för att behålla det tidigare beteendet.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112"></a>Webb-cmdlets bör varna `-Credential` när skickas via okrypterade anslutningar [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

När du använder HTTP skickas innehåll inklusive lösen ord som klartext. Den här ändringen är att inte tillåta detta som standard och returnera ett fel om autentiseringsuppgifterna skickas på ett osäkert sätt. Användare kan kringgå detta genom att `-AllowUnencryptedAuthentication` använda växeln.

## <a name="api-changes"></a>API-ändringar

### <a name="remove-addtypecommandbase-class-5407"></a>Ta `AddTypeCommandBase` bort klass [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

`AddTypeCommandBase` Klassen har tagits bort från `Add-Type` för att förbättra prestandan. Den här klassen används endast av cmdleten Add-Type och bör inte påverka användare.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080"></a>Förena cmdletar med parametern `-Encoding` som typ `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

`-Encoding` Värdet `Byte` har tagits bort från cmdletarna för fil Systems Provider. En ny parameter `-AsByteStream`används nu för att ange att en byte-dataström krävs som indata eller att utdata är en data ström i byte.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055"></a>Lägg till bättre fel meddelande för Tom och `-UFormat` null-parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Tidigare visas ett fel meddelande om att en tom `-UFormat`format sträng skickades till. Ett mer beskrivande fel har lagts till.

### <a name="clean-up-console-code-4995"></a>Rensa konsol kod [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Följande funktioner har tagits bort eftersom de inte stöds i PowerShell Core, och det finns inga planer på att lägga till stöd som de finns för äldre skäl för Windows PowerShell `-psconsolefile` : switch och kod `-importsystemmodules` , växel och kod och kod för ändring av teckensnitt.

### <a name="removed-runspaceconfiguration-support-4942"></a>Stöd `RunspaceConfiguration` [#4942](https://github.com/PowerShell/PowerShell/issues/4942) har tagits bort

När du tidigare skapade en PowerShell-körnings utrymme via programmering med hjälp av API: et kan du [`RunspaceConfiguration`][runspaceconfig] använda det äldre [`InitialSessionState`][iss]eller senare. Den här ändringen har tagit `RunspaceConfiguration` bort stöd för `InitialSessionState`och stöder bara.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923"></a>`CommandInvocationIntrinsics.InvokeScript`bind argument till `$input` i stället `$args` för [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

En felaktig position av en parameter resulterade i argumenten som angavs som indatamängd i stället för som argument.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903"></a>Ta bort `-showwindow` växeln som inte stöds `Get-Help` från [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow`är beroende av WPF, vilket inte stöds på CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866"></a>Tillåt att * används i register Sök vägen för `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

`-LiteralPath` Tidigare skulle ett jokertecken behandla det på samma sätt som `-Path` och om jokertecken inte hittade några filer, stängs det tyst. Rätt beteende bör vara det `-LiteralPath` exakta värdet, så om filen inte finns, bör den innehålla fel. Ändra är att hantera jokertecken som används `-Literal` med literal.

### <a name="fix-set-service-failing-test-4802"></a>Korrigera `Set-Service` misslyckad test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Om `New-Service -StartupType foo` `foo` användes tidigare ignorerades och tjänsten skapades med en typ av standard starttyp. Den här ändringen är att explicit utlösa ett fel för en ogiltig starttyp.

### <a name="rename-isosx-to-ismacos-4700"></a>Byt `$IsOSX` namn `$IsMacOS` till [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

Namngivningen i PowerShell bör vara konsekvent med vår namn och överensstämmer med Apples användning av macOS i stället för OSX. Men för att kunna läsa och ständigt kan vi hålla sig till Pascal-höljet.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573"></a>Gör fel meddelandet konsekvent när ogiltigt skript skickas till fil, vilket är ett bättre fel när ett tvetydigt argument har skickats [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Ändra avslutnings koderna `pwsh.exe` för att anpassas efter UNIX-konventioner

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302-4303"></a>Borttagning av `LocalAccount` och cmdlets från `Diagnostics` moduler. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

På grund av API: er som inte `LocalAccounts` stöds har modulen `Counter` och cmdletarna i `Diagnostics` modulen tagits bort tills en bättre lösning har hittats.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036"></a>Det går inte att köra PowerShell-skriptet med bool-parametern [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Tidigare använde **PowerShell. exe** (nu **pwsh. exe**) för att köra ett PowerShell-skript `-File` med det tillhandahållna inget `$true` / `$false` sätt att skicka som parameter värden. Stöd för `$true` / `$false` som parsade värden till parametrar har lagts till. Växlings värden stöds också som för närvarande dokumenterad syntax fungerar inte.

### <a name="remove-clrversion-property-from-psversiontable-4027"></a>Ta `ClrVersion` bort egenskap `$PSVersionTable` från [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

`ClrVersion` Egenskapen i `$PSVersionTable` är inte användbar med CoreCLR, slutanvändare ska inte använda det värdet för att fastställa kompatibiliteten.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019"></a>Ändra positions parameter för `powershell.exe` från `-Command` till `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Aktivera Shebang användning av PowerShell på andra plattformar än Windows-plattformar. Det innebär att du kan skapa en skript-körbar fil som anropar PowerShell automatiskt i stället för att uttryckligen anropa `pwsh`det på UNIX-baserade system. Det innebär också att du nu kan göra saker som `powershell foo.ps1` eller `powershell fooScript` utan att `-File`ange. Den här ändringen kräver dock att du uttryckligen anger `-c` eller `-Command` när du försöker göra saker som. `powershell.exe Get-Command`

### <a name="implement-unicode-escape-parsing-3958"></a>Implementera tolkning av Unicode-Escape [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u####``eller `` `u{####}`` konverteras till motsvarande Unicode-tecken. Om du vill mata `` `u``ut en litteral kan du undanta ``` ``u```bakticket:.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940"></a>Ändra `New-ModuleManifest` kodningen `UTF8NoBOM` till på andra plattformar än Windows-plattformar [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Tidigare `New-ModuleManifest` skapade psd1-manifest i UTF-16 med BOM och skapar ett problem för Linux-verktyg. Den här avbrytande ändringen ändrar `New-ModuleManifest` kodningen till UTF (ingen BOM) på andra plattformar än Windows-plattformar.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780"></a>Förhindra `Get-ChildItem` att återkommer till symlinks (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Den här ändringen `Get-ChildItem` ger mer i rad med UNIX `ls -r` -och inbyggda `dir /s` Windows-kommandon. Precis som de nämnda kommandona visar cmdleten symboliska länkar till kataloger som hittades under rekursion, men rekursivt inte in dem.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706"></a>Korrigera `Get-Content -Delimiter` för att inte inkludera avgränsaren i de returnerade raderna [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Tidigare `Get-Content -Delimiter` var de utdata som användes inkonsekventa och olämpliga eftersom det krävde ytterligare bearbetning av data för att ta bort avgränsaren. Den här ändringen tar bort avgränsaren i returnerade rader.

### <a name="implement-format-hex-in-c-3320"></a>Implementera format – hex i C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

`-Raw` Parametern är nu en "No-OP" (där det inte gör något). Om du fortsätter kommer alla utdata att visas med en sann representation av siffror som innehåller alla byte för dess typ (vad den `-Raw` här ändringen hade innan ändringen).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319"></a>PowerShell som standard gränssnitt fungerar inte med skript kommandot [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

I UNIX är det en konvention för gränssnitt att acceptera `-i` för ett interaktivt gränssnitt och många verktyg förväntar sig`script` detta beteende (till exempel och när du ställer in PowerShell som standard gränssnitt) och anropar `-i` gränssnittet med växeln. Den här ändringen är Sparad i `-i` som tidigare kunde användas som kort för att matcha `-inputformat`, vilket nu måste vara `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167"></a>Skriv åtgärd i get-ComputerInfo egenskaps namn [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber`är felstavat `BiosSeralNumber` och har ändrats till rätt stavning.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024"></a>Lägg `Get-StringHash` till `Get-FileHash` och cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Den här ändringen är att vissa hash-algoritmer inte stöds av CoreFX, vilket innebär att de inte längre är tillgängliga:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672"></a>Lägg till verifiering `Get-*` på cmdletar där överföring av $null returnerar alla objekt i stället för fel [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Att `$null` skicka till något av följande genererar nu ett fel:

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

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482"></a>Lägg till stöd för utökat logg fils `Import-Csv` format för W3C i [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Tidigare kan `Import-Csv` cmdleten inte användas för att importera loggfilerna direkt i utökat logg format för W3C och ytterligare åtgärder krävs. Med den här ändringen stöds W3C Extended Log-formatet.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035"></a>Parameter bindnings problem `ValueFromRemainingArguments` med i PS functions [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments`returnerar nu värdena som en matris i stället för ett enda värde som är en matris.

### <a name="buildversion-is-removed-from-psversiontable-1415"></a>`BuildVersion`har tagits bort `$PSVersionTable` från [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Ta bort `BuildVersion` egenskapen från `$PSVersionTable`. Den här egenskapen är kopplad till Windows build-versionen. I stället rekommenderar vi att du använder `GitCommitId` för att hämta den exakta versionen av PowerShell Core.

### <a name="changes-to-web-cmdlets"></a>Ändringar av webb-cmdletar

De underliggande .NET API: erna för webb-cmdletarna har ändrats `System.Net.Http.HttpClient`till. Den här ändringen ger många fördelar. Men den här ändringen tillsammans med en brist på interoperabilitet med Internet Explorer har resulterat i flera större ändringar `Invoke-WebRequest` i `Invoke-RestMethod`och.

- `Invoke-WebRequest`stöder nu bara grundläggande HTML-parsning. `Invoke-WebRequest`returnerar alltid ett `BasicHtmlWebResponseObject` objekt. Egenskaperna `ParsedHtml` och `Forms` har tagits bort.
- `BasicHtmlWebResponseObject.Headers`värdena är nu `String[]` i stället `String`för.
- `BasicHtmlWebResponseObject.BaseResponse`är nu ett `System.Net.Http.HttpResponseMessage` objekt.
- `Response` Egenskapen för webb-cmdlet-undantag är nu `System.Net.Http.HttpResponseMessage` ett objekt.
- Strikt rubrik tolkning för RFC är nu standard för parametern `-Headers` och `-UserAgent` . Detta kan kringgås med `-SkipHeaderValidation`.
- `file://`och `ftp://` URI-scheman stöds inte längre.
- `System.Net.ServicePointManager`inställningarna stöds inte längre.
- Det finns för närvarande ingen certifikatbaserad autentisering tillgänglig på macOS.
- Om `-Credential` du använder över `http://` en URI kommer det att resultera i ett fel. Använd en `https://` URI eller ange `-AllowUnencryptedAuthentication` parametern för att ignorera felet.
- `-MaximumRedirection`genererar nu ett avslutande fel när omdirigerings försök överskrider den angivna gränsen i stället för att returnera resultaten av den senaste omdirigeringen.
- I PowerShell 6,2 gjordes en ändring som standard till UTF-8-kodning för JSON-svar. Om ingen teckenuppsättning anges för ett JSON-svar ska standard kodningen vara UTF-8 per RFC 8259.
