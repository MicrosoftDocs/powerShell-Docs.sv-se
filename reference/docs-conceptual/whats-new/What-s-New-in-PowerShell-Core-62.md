---
title: Nyheter i PowerShell Core 6,2
description: Nya funktioner och ändringar som lanseras i PowerShell Core 6,2
ms.date: 03/28/2019
ms.openlocfilehash: 98dd97b064e11509bf97e68e0a312e6b34b5d2bc
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96840147"
---
# <a name="whats-new-in-powershell-core-62"></a>Nyheter i PowerShell Core 6,2

PowerShell Core 6,2-versionen fokuserar på prestanda förbättringar, fel korrigeringar och mindre cmdlet-och språk förbättringar som förbättrar kvaliteten. Om du vill se en fullständig lista över förbättringar kan du kolla in vår detaljerade [ChangeLogs](https://github.com/PowerShell/PowerShell/releases) på GitHub.

## <a name="experimental-features"></a>Experimentella funktioner

Tidigare aktiverade vi stöd för [experimentella funktioner][]. I 6,2-versionen har vi fyra experimentella funktioner för att testa. Ge feedback så att vi kan göra förbättringar och avgöra om funktionen är värd för att marknadsföra till en vanlig status.

Använd `Get-ExperimentalFeature` för att hämta en lista över tillgängliga experimentella funktioner. Du kan aktivera eller inaktivera dessa funktioner med `Enable-ExperimentalFeature` och `Disable-ExperimentalFeature` .

### <a name="command-not-found-suggestions"></a>Kommandot hittade inte förslag

Den här funktionen använder fuzzy-matchning för att hitta förslag på kommandon eller cmdletar som du kan ha felskrivit.

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a>Exempel

I det här exemplet är det felstavade cmdlet-namnet suddigt matchat med flera förslag från de mest sannolika.

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a>Implicit fjärran batchbearbetning

När du använder [implicit fjärr kommunikation](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) i en pipeline behandlar PowerShell varje kommando i pipelinen separat. Objekten serialiseras upprepade gånger och `de-serialized` mellan klienten och fjärrsystemet under körningen av pipelinen.

Med den här funktionen analyserar PowerShell pipelinen för att avgöra om kommandot är säkert att köra och finns på mål systemet. När värdet är true, kör PowerShell hela pipelinen via en fjärr anslutning och bara serialiserar och `de-serializes` tillbaka resultatet till klienten.

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

Ett verkligt globalt test av `Get-Process | Sort-Object` över localhost minskar från 10-15 sekunder till 20-30 **millisekunder**. Funktionen behöver bara aktive ras på klienten. Inga ändringar krävs på servern.

### <a name="temp-drive"></a>Tillfällig enhet

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

Om du använder PowerShell Core på olika operativ system kommer du att upptäcka att miljövariabeln för att hitta den temporära katalogen är annorlunda på Windows, macOS och Linux! Med den här funktionen får du en [PSDrive][] `Temp:` som kallas att automatiskt mappas till den temporära mappen för det operativ system som du använder.

#### <a name="example"></a>Exempel

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

Tänk på att interna fil kommandon (som `ls` i Linux) inte är medvetna om PSDrives och inte ser den här `Temp:` enheten.

### <a name="abbreviation-expansion"></a>Utökning av förkortning

PowerShell-cmdletar förväntas ha beskrivande substantiv. Detta resulterar i långa namn som är svårare att skriva. Med den här funktionen kan du bara skriva versaler i cmdleten och använda TABB-slutförande för att hitta en matchning.

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a>Exempel

```powershell
PS> i-arsavsf
```

Om du trycker på tabbtangenten och har modulen Azure PowerShell [AZ](https://www.powershellgallery.com/packages/Az) installerad, kommer den att kompletteras med:

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> Den här funktionen är avsedd att användas interaktivt. Det går inte att köra förkortade former av cmdletar.
> Den här funktionen ersätter inte alias.

## <a name="breaking-changes"></a>Icke-bakåtkompatibla ändringar

- Åtgärda `-NoEnumerate` beteendet i `Write-Output` för att vara konsekvent med Windows PowerShell. (#9069)
- Gör `Join-String -InputObject 1,2,3` resultatet lika med `1,2,3 | Join-String` resultatet (#8611) (tack @sethvs !)
- Lägg till `-Stable` i `Sort-Object` och relaterade tester (#7862) (tack @KirkMunro !)
- Förbättra `Start-Sleep` cmdleten för att ta emot bråktal i sekunder (#8537) (tack @Prototyyppi !)
- Ändra hash-OrdinalIgnoreCase så att den använder `case-insensitive` alla kulturer (#8566)
- Åtgärda **LiteralPath** i `Import-Csv` för att binda till `Get-ChildItem` utdata (#8277) (tack @iSazonov !)
- Hoppar inte längre över en kolumn utan namn om dubbel quote-avgränsare används i `Import-Csv` (#7899) (tack @Topping !)
- `Get-ExperimentalFeature` har inte längre någon `-ListAvailable` växel (#8318)
- Felsök-parametern har nu ställts in `$DebugPreference` för att **fortsätta** i stället för **fråga** (#8195) (tack @KirkMunro !)
- `-OutputFormat`Använd om det är angivet i icke-interaktivt, omdirigerade, kodade kommando som används med pwsh (#8115)
- Läs in sammansättning från modulens bas Sök väg innan du försöker läsa in från GAC (#8073)
- Ta bort Tilde från Linux Preview-paket (#8244)
- Flytta bearbetning av `-WorkingDirectory` före bearbetning av profiler (#8079)
- Lägg inte till `PATHEXT` miljövariabeln på UNIX (#7697) (tack @iSazonov !)

## <a name="known-issues"></a>Kända problem

- Det finns ett problem med att läsa in moduler för fjärr kommunikation på Windows IOT ARM-plattformar. Se (#8053)

## <a name="general-updates-and-fixes"></a>Allmänna uppdateringar och korrigeringar

- Aktivera ifyllnad av Skift läges okänsligt för filer och mappar på SKIFT läges känsligt fil system (#8128)
- Gör PSVersionInfo. PSVersion och PSVersionInfo. PSEdition Public (#8054) (tack @KirkMunro !)
- Lägg till typ härledning för `$_`  /  `$PSItem` i `catch{ }` block (#8020) (tack @vexx32 !)
- Korrigera statisk metod typ härledning (#8018) (tack @SeeminglyScience !)
- Skapa härledda typer för `Select-Object` , `Group-Object` , **PSObject** och **hash** (#7231) (tack @powercode !)
- Stöd för anrop av metod med `ByRef-like` typ parametrar (#7721)
- Hantera det fall där sökvägen till Windows PowerShell-modulen redan finns i miljöns PSModulePath (#7727)
- Aktivera `SecureString` cmdletar för icke-Windows genom att lagra den oformaterade texten (#9199)
- Förbättra fel meddelandet på icke-Windows när du importerar CliXml med SecureString (#7997)
- Lägger till parametern ReplyTo till `Send-MailMessage` (#8727) (tack @replicaJunction !)
- Lägg till föråldrat meddelande i `Send-MailMessage` (#9178)
- Korrigera `Restart-Computer` för att fungera på `localhost` när WinRM inte finns (#9160)
- Gör `Start-Job` Throw-avslutande fel när PowerShell håller på att nås (#9128)
- Lägg till acceleratorer med C#-typ och suffix för ushort, uint, ulong och korta litteraler (#7813) (tack @vexx32 !)
- Nya suffix har lagts till för numeriska literaler – se [about_Numeric_Literals][] (#7901) (tack @vexx32 !)
- Korrekt rapport effekt nivå när SupportsShouldProcess inte är inställt på True (#8209) (tack @vexx32 !)
- Korrigera charset-problem i webb-cmdlets (#8742) (tack @markekraus !)
- Åtgärda förväntat `100-continue` problem med Web-cmdletar (#8679) (tack @markekraus !)
- Åtgärda problem med fil blockering med Web-cmdletar (#7676) (tack @Claustn !)
- Åtgärda problem med tolkning av tecken tabell i `Invoke-RestMethod` (#8694) (tack @markekraus !)
- Refaktum `ConvertTo-Json` för att exponera JsonObject. ConvertToJson som ett offentligt API (#8682)
- Lägg till konfigurerbart maximalt djup i `ConvertFrom-Json` med-djup (#8199) (tack @louistio !)
- Lägg till EscapeHandling-parametern i `ConvertTo-Json` cmdleten (#7775) (tack @iSazonov !)
- Lägg till `-CustomPipeName` i pwsh och `Enter-PSHostProcess` (#8889)
- Aktivera skapande av relativa symboliska länkar i Windows med `New-Item` (#8783)
- Tillåt Windows-användare i utvecklarläge att skapa symlinks utan utökade privilegier (#8534)
- Tillåt `Write-Information` att accepterar `$null` (#8774)
- Korrigera `Get-Help` för avancerade funktioner med MAML-hjälp innehåll (#8353)
- Åtgärda `Get-Help` PSTypeName-problem med-parameter när endast en parameter deklareras (#8754) (tack @pougetat !)
- Korrigering av token-beräkning för `Get-Help` körning på script block för kommentars hjälpen. (#8238) (Tack @hubuk !)
- Ändra `Get-Help` cmdlet – parameter parameter så att den accepterar sträng mat ris (#8454) (tack @sethvs !)
- Lös PAGER om sökvägen innehåller blank steg (#8571) (tack @pougetat !)
- Lägg till en prompt till användningen av `less` i funktionen Help för att instruera användaren att avsluta (#7998)
- Lägg till stöd för uppräknings-och tecken typer i `Format-Hex` cmdlet (#8191) (tack @iSazonov !)
- Ta bort ShouldProcess från `Format-Hex` (#8178)
- Lägg till nya förskjutnings-och Count-parametrar till och omstrukturering `Format-Hex` av cmdleten (#7877) (tack @iSazonov !)
- Tillåt ' name ' som en aliasnamn för ' Label ' i `ConvertTo-Html` , Tillåt att ' width '-posten är ett heltal (#8426) (tack @mklement0 !)
- Gör script block-baserade beräknade egenskaper fungerar igen om `ConvertTo-Html` (#8427) (tack @mklement0 !)
- Lägg till cmdlet `Join-String` för att skapa text från pipeline-ininformation (#7660) (tack @powercode !)
- Åtgärda `Join-String` cmdlet FormatString parameter Logic (#8449) (tack @sethvs !)
- Ändra `Clear-Host` tillbaka till Använd `$RAWUI` och rensa för att arbeta via fjärr kommunikation (#8609)
- Ändra `Clear-Host` till att bara anropa `[console]::clear` och ta bort radera alias från Unix (#8603)
- Åtgärda LiteralPath i `Import-Csv` för att binda till `Get-ChildItem` utdata (#8277) (tack @iSazonov !)
- Hjälp funktionen ska inte använda pager för AliasHelpInfo (#8552)
- Lägg till `-UseMinimalHeader` i `Start-Transcript` för att minimera avskrifts huvudet (#8402) (tack @lukexjeremy !)
- Lägg till `Enable-ExperimentalFeature` och `Disable-ExperimentalFeature` cmdlets (#8318)
- Visa alla cmdletar från **PSDiagnostics** om logman.exe är tillgängligt (#8366)
- Ta bort **bevara** parameter från `New-PSDrive` på `non-Windows` plattformen (#8291) (tack @lukexjeremy !)
- Lägg till stöd för `cd +` (#7206) (tack @bergmeister !)
- Aktivera `Set-Location -LiteralPath` för att arbeta med mappar med namnet-och + (#8089)
- `Test-Path` Returnerar `$false` när angivet värde för tom eller `$null` sökväg (#8080) (tack @vexx32 !)
- Tillåt att dynamisk parameter returneras även om sökvägen inte matchar någon Provider (#7957)
- Support- `Get-PSHostProcessInfo` och `Enter-PSHostProcess` UNIX-plattformar (#8232)
- Minska allokeringarna i en `Get-Content` cmdlet (#8103) (tack @iSazonov !)
- Aktivera `Add-Content` för att dela Läs behörighet med andra verktyg när du skriver innehåll (#8091)
- `Get/Add-Content` genererar förbättrat fel vid mål för en behållare (#7823) (tack @kvprasoon !)
- Lägg `-Name` till `-NoUserOverrides` och `-ListAvailable` parametrar till `Get-Culture` cmdlet (#7702) (tack @iSazonov !)
- Lägg till enhetligt attribut för att slutföra **kodnings** parametern. (#7732) (Tack @ThreeFive-O !)
- Tillåt numeriska ID: n och namnet på registrerade tecken sidor i **encoding** -parametrar (#7636) (tack @iSazonov !)
- Korrigera `Rename-Item -Path` med jokertecken (#7398) (tack @kwkam !)
- När `Start-Transcript` du använder och filen finns, tom fil i stället för att ta bort (#8131) (tack @paalbra !)
- Gör `Add-Type` filer med öppen källkod med **fileaccess. Read** och **fileshare. Read** explicit (#7915) (tack @IISResetMe !)
- Korrigera `Enter-PSSession -ContainerId` den senaste versionen av Windows (#7883)
- Se till att egenskapen **NestedModules** är ifylld med `Test-ModuleManifest` (#7859)
- Lägg till `%F` Case to `Get-Date` -UFormat (#7630) (tack @britishben !)
- Korrigera `Set-Service -Status Stopped` för att stoppa tjänster med beroenden (#5525) (tack @zhenggu !)

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Experimentella funktioner]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
