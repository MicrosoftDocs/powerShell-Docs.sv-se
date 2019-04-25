---
title: Nyheter i PowerShell Core 6.2
description: Nya funktioner och ändringar som introducerades i PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 6a0da8a410e602ae3963e0bc7bace745317d7d4b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058105"
---
# <a name="whats-new-in-powershell-core-62"></a>Nyheter i PowerShell Core 6.2

PowerShell Core 6.2-versionen fokuserar på prestandaförbättringar, felkorrigeringar och mindre förbättringar för cmdlet och språk som förbättrar kvaliteten. Om du vill se en fullständig lista över förbättringar, Kolla in vår detaljerad [changelogs](https://github.com/PowerShell/PowerShell/releases) på GitHub.

## <a name="experimental-features"></a>Experimentella funktioner

Tidigare var vi aktiverat stöd för [experimentella funktioner][]. Vi har fyra experimentella funktioner för att testa i 6.2-utgåvan. Ge feedback så att vi kan göra förbättringar och bestämma om funktionen är värt att uppgradera till vanlig status.

Använd `Get-ExperimentalFeature` att hämta en lista över tillgängliga experimentella funktioner. Du kan aktivera eller inaktivera dessa funktioner via `Enable-ExperimentalFeature` och `Disable-ExperimentalFeature`.

### <a name="command-not-found-suggestions"></a>Kommandot hittades inte förslag

Den här funktionen använder partiell matchning för att få förslag på kommandon eller cmdlet: ar som kanske har du angett.

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a>Exempel

I det här exemplet är felstavade cmdlet-namn fuzzy matchas mot flera förslag från mest sannolikt minst sannolikt.

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

### <a name="implicit-remoting-batching"></a>Implicit fjärrkommunikation batchbearbetning

När du använder [implicit fjärrkommunikation](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) i en pipeline PowerShell behandlar varje kommando i pipelinen oberoende av varandra. Objekt flera gånger serialiseras och `de-serialized` mellan klienten och fjärrdatorn under körningen av pipelinen.

Med den här funktionen analyserar PowerShell pipeline för att avgöra om kommandot är säkert att köra och den finns på målsystemet. Om värdet är true PowerShell körs hela pipelinen via en fjärranslutning och endast Serialiserar och `de-serializes` resultaten tillbaka till klienten.

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

Ett verkligt test av `Get-Process | Sort-Object` över localhost sjunker från 10 – 15 sekunder till 20 – 30 **millisekunder**. Funktionen behöver bara vara aktiverad på klienten. Det krävs inga ändringar på servern.

### <a name="temp-drive"></a>Temp Drive

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

Om du använder PowerShell Core på olika operativsystem, kommer du att upptäcka att miljövariabeln för att hitta den tillfälliga katalogen är olika i Windows, macOS och Linux! Med den här funktionen kan du få en [PSDrive][] kallas `Temp:` som mappas automatiskt till den tillfälliga mappen för operativsystemet som du använder.

#### <a name="example"></a>Exempel

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> `Get-Content` Temp:/hello.txt
Hello World!
```

Tänk på de interna kommandona (som `ls` på Linux) är inte medvetna om PSDrives och ser inte detta `Temp:` enhet.

### <a name="abbreviation-expansion"></a>Förkortning Expansion

PowerShell-cmdletar som förväntas ha beskrivande substantiv. Detta resulterar i långa namn som är svårare att skriva. Den här funktionen kan du bara ange versaler för cmdlet: ar och Använd tabbifyllning för att hitta en matchning.

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a>Exempel

```powershell
PS> i-arsavsf
```

Om du trycker på fliken och har Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) installerat modulen, kommer det att Komplettera automatiskt till:

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> Den här funktionen är avsedd att användas interaktivt. Förkortade former av cmdlet: ar kan inte utföras.
> Den här funktionen är inte en ersättning för alias.

## <a name="breaking-changes"></a>Icke-bakåtkompatibla ändringar

- Åtgärda `-NoEnumerate` beteende i `Write-Output` för att överensstämma med Windows PowerShell. (#9069)
- Kontrollera `Join-String -InputObject 1,2,3` resultera lika `1,2,3 | Join-String` resultera (#8611) (tack @sethvs!)
- Lägg till `-Stable` till `Sort-Object` och relaterade tester (#7862) (tack @KirkMunro!)
- Förbättra `Start-Sleep` cmdlet för att acceptera fraktionell (#8537) (tack @Prototyyppi!)
- Ändra hash-tabell att använda OrdinalIgnoreCase för att vara `case-insensitive` i alla kulturer (#8566)
- Åtgärda **LiteralPath** i `Import-Csv` att binda till `Get-ChildItem` utdata (#8277) (tack @iSazonov!)
- Hoppar över en kolumn utan namn inte längre om dubbelt citattecken avgränsare används i `Import-Csv` (#7899) (tack @Topping!)
- `Get-ExperimentalFeature` har inte längre `-ListAvailable` växla (#8318)
- Felsöka nu parameteruppsättningar `$DebugPreference` till **Fortsätt** i stället för **Inquire** (#8195) (tack @KirkMunro!)
- Kontrollera `-OutputFormat` om anges i icke-interaktivt, omdirigerade, kodade kommando som används med pwsh (#8115)
- Läsa in sammansättningen från modulen rotsökväg innan du försöker läsa in från den globala Sammansättningscachen (#8073)
- Ta bort tilde från Linux förhandsversion paket (#8244)
- Flytta bearbetning av `-WorkingDirectory` innan bearbetningen av profiler (#8079)
- Lägg inte till `PATHEXT` miljövariabeln på Unix (#7697) (tack @iSazonov!)

## <a name="known-issues"></a>Kända problem

- Fjärrkommunikation för plattformar som Windows IOT ARM har ett problem vid inläsning av moduler. Se (#8053)

## <a name="general-updates-and-fixes"></a>Allmänna uppdateringar och korrigeringar

- Aktivera skiftlägeskänsliga tabbifyllning för filer och mappar i skiftlägeskänsliga filsystem (#8128)
- Gör PSVersionInfo.PSVersion och PSVersionInfo.PSEdition offentlig (#8054) (tack @KirkMunro!)
- Lägg till typen Inferens för `$_`  /  `$PSItem` i `catch{ }` blockerar (#8020) (tack @vexx32!)
- Åtgärda statisk metod anrop typ inferens (#8018) (tack @SeeminglyScience!)
- Skapa antydda för `Select-Object`, `Group-Object`, **PSObject** och **hash-tabell** (#7231) (tack @powercode!)
- Stöd för anropa metoden med `ByRef-like` Skriv parametrar (#7721)
- Hantera Windows PowerShell-modulens sökväg redan används i den miljön PSModulePath (#7727)
- Aktivera `SecureString` -cmdletar för Windows genom att lagra den oformaterade texten (#9199)
- Förbättra felmeddelande vid icke-Windows när du importerar clixml med securestring (#7997)
- Att lägga till parametern ReplyTo till `Send-MailMessage` (#8727) (tack @replicaJunction!)
- Lägg till föråldrat meddelande till `Send-MailMessage` (#9178)
- Åtgärda `Restart-Computer` att arbeta med `localhost` när WinRM är inte finns (#9160)
- Kontrollera `Start-Job` throw avslutande fel när PowerShell värd (#9128)
- Lägg till C# style typ acceleratorer och suffix för ushort, uint, ulong och korta litteraler (#7813) (tack @vexx32!)
- Har lagts till nytt suffix för numeriska literaler – Se [about_Numeric_Literals][] (#7901) (tack @vexx32!)
- Korrekt rapportering effektnivå när SupportsShouldProcess inte är inställd på 'true' (#8209) (tack @vexx32!)
- Åtgärda teckenuppsättningen problem i Web-Cmdlets (#8742) (tack @markekraus!)
- Åtgärda Expect `100-continue` problem med Web-cmdletar (#8679) (tack @markekraus!)
- Åtgärda blockeringsproblem för filen med web-cmdletar (#7676) (tack @Claustn!)
- Åtgärda teckentabellen parsning problem i `Invoke-RestMethod` (#8694) (tack @markekraus!)
- Omstrukturera `ConvertTo-Json` att exponera JsonObject.ConvertToJson som inget offentligt API (#8682)
- Lägg till konfigurerbara maximala djupet i `ConvertFrom-Json` med - djup (#8199) (tack @louistio!)
- Lägg till EscapeHandling parameter i `ConvertTo-Json` cmdlet (#7775) (tack @iSazonov!)
- Lägg till `-CustomPipeName` till pwsh och `Enter-PSHostProcess` (#8889)
- Aktivera skapa relativa symboliska länkar på Windows med `New-Item` (#8783)
- Tillåt Windows-användare i utvecklare för att skapa symlinks utan höjning (#8534)
- Aktivera `Write-Information` att acceptera `$null` (#8774)
- Åtgärda `Get-Help` för avancerade funktioner med MAML hjälpinnehåll (#8353)
- Åtgärda `Get-Help` PSTypeName problem med - parametern när bara en parametern deklareras (#8754) (tack @pougetat!)
- Token beräkning korrigering för `Get-Help` körs på ScriptBlock kommentar hjälp. (#8238) (Tack @hubuk!)
- Ändra `Get-Help` cmdlet-parametern-parametern så att den accepterar sträng matriser (#8454) (tack @sethvs!)
- Lösa PERSONSÖKARE om sökvägen innehåller blanksteg (#8571) (tack @pougetat!)
- Lägg till fråga i användningen av `less` i Hjälp om du till ber användaren att avsluta (#7998)-funktionen
- Lägga till stöd för uppräkning och char typer i `Format-Hex` cmdlet (#8191) (tack @iSazonov!)
- Ta bort ShouldProcess från `Format-Hex` (#8178)
- Lägg till nya förskjutning och antal parametrar till `Format-Hex` och omstrukturera cmdleten (#7877) (tack @iSazonov!)
- Tillåt 'name' som ett alias-nyckel för 'etiketten' i `ConvertTo-Html`, Tillåt 'bredd-posten ska vara ett heltal (#8426) (tack @mklement0!)
- Kontrollera scriptblock baseras beräknade egenskaper fungerar igen i `ConvertTo-Html` (#8427) (tack @mklement0!)
- Lägg till cmdlet `Join-String` för att skapa text från pipelinen indata (#7660) (tack @powercode!)
- Åtgärda `Join-String` cmdlet FormatString parametern logic (#8449) (tack @sethvs!)
- Ändra `Clear-Host` till att använda `$RAWUI` och avmarkera om du vill arbeta med fjärrkommunikation (#8609)
- Ändra `Clear-Host` till kallas bara `[console]::clear` och ta bort rensa alias från Unix (#8603)
- Åtgärda LiteralPath i `Import-Csv` att binda till `Get-ChildItem` utdata (#8277) (tack @iSazonov!)
- hjälpfunktionen bör inte använda personsökare för AliasHelpInfo (#8552)
- Lägg till `-UseMinimalHeader` till `Start-Transcript` att minimera avskrift rubrik (#8402) (tack @lukexjeremy!)
- Lägg till `Enable-ExperimentalFeature` och `Disable-ExperimentalFeature` cmdletar (#8318)
- Exponera alla cmdletar från **PSDiagnostics** om logman.exe är tillgängliga (#8366)
- Ta bort **spara** parametern från `New-PSDrive` på `non-Windows` plattform (#8291) (tack @lukexjeremy!)
- Lägg till stöd för `cd +` (#7206) (tack @bergmeister!)
- Aktivera `Set-Location -LiteralPath` att arbeta med mappar med följande namn - och + (#8089)
- `Test-Path` Returnerar `$false` när en tom eller `$null` sökväg värde (#8080) (tack @vexx32!)
- Tillåt dynamisk parameter som ska returneras även om sökvägen inte matchar någon leverantör (#7957)
- Stöd för `Get-PSHostProcessInfo` och `Enter-PSHostProcess` på Unix-plattformar (#8232)
- Minska allokeringar i `Get-Content` cmdlet (#8103) (tack @iSazonov!)
- Aktivera `Add-Content` delar läsbehörighet med andra verktyg vid skrivning till innehåll (#8091)
- `Get/Add-Content` genererar förbättrad fel när måldatorn är en behållare (#7823) (tack @kvprasoon!)
- Lägg till `-Name`, `-NoUserOverrides` och `-ListAvailable` parametrar för att `Get-Culture` cmdlet (#7702) (tack @iSazonov!)
- Lägg till enhetlig attribut för slutförande för **Encoding** parametern. (#7732) (Tack @ThreeFive-O!)
- Tillåt numeriska ID: N och namnet på registrerade teckentabeller i **Encoding** parametrar (#7636) (tack @iSazonov!)
- Åtgärda `Rename-Item -Path` med jokertecken char (#7398) (tack @kwkam!)
- När du använder `Start-Transcript` och filen finns, tom fil snarare än att tas bort (#8131) (tack @paalbra!)
- Kontrollera `Add-Type` öppna källfiler med **FileAccess.Read** och **FileShare.Read** uttryckligen (#7915) (tack @IISResetMe!)
- Åtgärda `Enter-PSSession -ContainerId` för den senaste Windows (#7883)
- Se till att **NestedModules** egenskapen fylls med `Test-ModuleManifest` (#7859)
- Lägg till `%F` fallet till `Get-Date` - UFormat (#7630) (tack @britishben!)
- Åtgärda `Set-Service -Status Stopped` stoppa tjänsterna med beroenden (#5525) (tack @zhenggu!)

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Experimentella funktioner]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
