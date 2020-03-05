---
title: Nyheter i PowerShell 7,0
description: Nya funktioner och ändringar som lanseras i PowerShell 7,0
ms.date: 03/04/2020
ms.openlocfilehash: 3e83fbe9d863a5e29acbcc1e88b58c88501922ae
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78280314"
---
# <a name="whats-new-in-powershell-70"></a>Nyheter i PowerShell 7,0

PowerShell 7,0 är en utgåva med öppen källkod, plattforms oberoende plattform (Windows, macOS och Linux) av PowerShell, som är byggd för att hantera heterogena miljöer och hybrid moln.

I den här versionen har vi introducerat ett antal nya funktioner, bland annat:

- Pipeline-parallellisering med `ForEach-Object -Parallel`
- Nya operatorer:
  - Ternär operator: `a ? b : c`
  - Operatorer för pipeline-kedjan: `||` och `&&`
  - Null-villkorliga operatorer: `??` och `??=`
- En förenklad och dynamisk felvy och `Get-Error` cmdlet för enklare undersökning av fel
- Ett kompatibilitetsläge som gör det möjligt för användare att importera moduler i en implicit Windows PowerShell-session
- Automatiska nya versions meddelanden
- Möjligheten att anropa DSC-resurser direkt från PowerShell 7 (experimentell)

Om du vill se en fullständig lista över funktioner och korrigeringar går du till [ChangeLogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).

## <a name="where-can-i-install-powershell"></a>Var kan jag installera PowerShell?

PowerShell 7 har för närvarande stöd för följande operativ system på x64, inklusive:

- Windows 8,1 och 10
- Windows Server 2012, 2012 R2, 2016 och 2019
- macOS 10.13 +
- Red Hat Enterprise Linux (RHEL)/CentOS 7
- Fedora 30 +
- Debian 9
- Ubuntu LTS 16.04 +
- Alpine Linux 3.8 +

Dessutom stöder PowerShell 7,0 ARM32 och ARM64 varianter för Debian, Ubuntu och ARM64 Alpine Linux.

Kontrol lera installations anvisningarna för det önskade operativ systemet [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [MacOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7)eller [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).

Även om den inte stöds officiellt har communityn även tillhandahållit paket för [båge](https://aur.archlinux.org/packages/powershell/) och Kali Linux.

> [!NOTE]
> Debian 10 och CentOS 8 stöder för närvarande inte WinRM-fjärrkommunikation. Mer information om hur du konfigurerar SSH-baserad fjärr kommunikation finns i [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).

Mer uppdaterad information om operativ system och support livs cykel som stöds finns i [PowerShell-Supportens livs cykel](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).

## <a name="running-powershell-7"></a>Kör PowerShell 7

PowerShell 7 installeras i en ny katalog och körs sida vid sida med Windows PowerShell 5,1. För PowerShell Core 6. x är PowerShell 7 en uppgradering på plats som tar bort PowerShell Core 6. x.

- PowerShell 7 installeras för att `%programfiles%\PowerShell\7`
- Mappen `%programfiles%\PowerShell\7` läggs till i `$env:PATH`

PowerShell 7 installations paket uppgraderar tidigare versioner av PowerShell Core 6. x:

- PowerShell Core 6. x i Windows: `%programfiles%\PowerShell\6` ersätts av `%programfiles%\PowerShell\7`
- Linux: `/opt/microsoft/powershell/6` ersätts av `/opt/microsoft/powershell/7`
- macOS: `/usr/local/microsoft/powershell/6` ersätts av `/usr/local/microsoft/powershell/7`

> [!NOTE]
> I Windows PowerShell heter den körbara filen för att starta PowerShell `powershell.exe`. I version 6 och senare ändras den körbara filen så att den stöder sida-vid-sida-körning. Den nya körbara filen för att starta PowerShell 7 är `pwsh.exe`. För hands versioner kommer att finnas kvar på plats som `pwsh-preview` i stället för `pwsh` under 7-Preview-katalogen.

## <a name="improved-backwards-compatibility-with-windows-powershell"></a>Förbättrad bakåtkompatibilitet med Windows PowerShell

PowerShell 7,0 markerar en flytta en till .NET Core 3,1, vilket möjliggör betydligt mer bakåtkompatibilitet med befintliga Windows PowerShell-moduler. Detta inkluderar många moduler i Windows som kräver GUI-funktioner som `Out-GridView` och `Show-Command`, samt många roll hanterings moduler som levereras som en del av Windows.

För Windows läggs en ny växel parameter **UseWindowsPowerShell** till `Import-Module`. Den här växeln skapar en proxy-modul i PowerShell 7 som använder en lokal Windows PowerShell-process för att implicit köra alla cmdletar som finns i modulen. Mer information om [import-module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).

Mer information om vilka Microsoft-moduler som fungerar med PowerShell 7,0 finns i [tabellen](https://aka.ms/PSModuleCompat)för kompatibilitetsmodulen.

## <a name="parallel-execution-added-to-foreach-object"></a>Parallell körning har lagts till i Körningsbegäran – objekt

`ForEach-Object`-cmdleten, som itererar objekt i en samling, har nu inbyggd parallellitet med den nya **parallella** parametern.

Som standard använder parallella skript block den aktuella arbets katalogen för den anropare som startade parallell aktiviteterna.

I det här exemplet hämtas logg poster 50 000 från 5 system loggar på en lokal Windows-dator:

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

Den **parallella** parametern anger det skript block som körs parallellt för varje logg namn.

Den nya **ThrottleLimit** -parametern begränsar antalet skript block som körs parallellt vid en specifik tidpunkt. Standardvärdet är 5.

Använd variabeln `$_` för att representera det aktuella indatamängdet i-skript blocket. Använd `$using:`s omfång för att skicka variabel referenser till skript blocket som körs.

Mer information om [solobjekt](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).

## <a name="ternary-operator"></a>Ternär operator

PowerShell 7,0 introducerar en ternär operator som beter sig som ett förenklat `if-else`-uttryck.
PowerShell: s ternära operator modelleras noggrant från C# ternär operatörs syntax:

```
<condition> ? <if-true> : <if-false>
```

Villkors uttrycket utvärderas alltid och dess resultats mat som konverteras till ett **booleskt värde** för att avgöra vilken gren som utvärderas härnäst:

- `<if-true>` uttryck körs om `<condition>`s uttrycket är sant
- `<if-false>`-uttrycket körs om `<condition>`-uttrycket är falskt

Exempel:

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

I det här exemplet visas **sökvägen** , om sökvägen finns. Om sökvägen inte finns visas **inte sökvägen** .

För mer information [om](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).

## <a name="pipeline-chain-operators"></a>Operatorer för pipeline-kedjan

PowerShell 7 implementerar `&&` och `||`-operatörer för att villkorligt kedja pipelines. Dessa operatörer är kända i PowerShell som "pipelines kedje operatorer", och liknar och, eller listor i gränssnitt som **bash** och **zsh**, samt villkorsstyrda bearbetnings symboler i Windows Command Shell (**cmd. exe**).

`&&` operatören kör den högra pipelinen om den vänstra pipelinen lyckades. I motsatt fall kör `||`-operatören den högra pipelinen om den vänstra pipelinen misslyckades.

> [!NOTE]
> Dessa operatörer använder `$?` och `$LASTEXITCODE` variabler för att avgöra om en pipeline misslyckades. På så sätt kan du använda dem med inbyggda kommandon och inte bara med cmdlets eller functions.

Här är det första kommandot som slutförs och det andra kommandot körs:

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

Det första kommandot Miss lyckas, det andra körs inte:

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

Det första kommandot slutförs, det andra kommandot utförs inte:

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

Det första kommandot Miss lyckas, så det andra kommandot körs:

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

Mer information [om operatorer för pipeline-kedjan](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).

## <a name="null-coalescing-assignment-and-conditional-operators"></a>Null-sammanslagning, tilldelning och villkorliga operatorer

PowerShell 7 innehåller null-sammanslagnings operator `??`, null villkorlig tilldelning `??=`och null-operatörer för villkorliga medlemmar `?.` och `?[]`.

### <a name="null-coalescing-operator-"></a>Null-sammanslagnings operator??

Operatorn null-sammanslagning `??` returnerar värdet för den vänstra operanden om den inte är null.
Annars utvärderar den högra operanden och returnerar resultatet. `??` operatorn utvärderar inte sin högra operand om den vänstra operanden utvärderas till icke-null.

```powershell
$x = $null
$x ?? 100
100
```

I följande exempel kommer den högra operanden inte att utvärderas:

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a>Null villkorlig tilldelnings operator? =

Operatorn null för villkorlig tilldelning `??=` tilldelar värdet för dess högra operand till sin vänstra operand endast om den vänstra operanden utvärderar till null. `??=` operatorn utvärderar inte sin högra operand om den vänstra operanden utvärderas till icke-null.

```powershell
$x = $null
$x ??= 100
$x
100
```

I följande exempel kommer den högra operanden inte att utvärderas:

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a>Null villkorliga medlemmars åtkomst operatörer?. särskilt? [] (Experimentell)

> [!NOTE]
> Det här är en experimentell funktion som heter **PSNullConditionalOperators**. Om du vill veta mer [om experimentella funktioner](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).

En villkorlig operator för null tillåter åtkomst till medlemmar, `?.`eller element, `?[]`, till operanden endast om denna operand utvärderar till icke-null. annars returnerar den null.

> [!NOTE]
> Eftersom PowerShell tillåter `?` att ingå i variabel namnet, krävs formell specifikation av variabel namnet för att använda dessa operatorer. Därför måste du använda `{}` runt variabel namnen som `${a}` eller när `?` är en del av variabeln Name `${a?}`.

I följande exempel returneras värdet för medlems egenskaps **status** :

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

Följande exempel kommer att returnera Null, utan att försöka komma åt medlems namnets **status**:

```powershell
$service = $Null
${Service}?.status
```

På samma sätt returneras värdet för elementet när du använder `?[]`:

```powershell
$a = 1..10
${a}?[0]
1
```

När operanden är null returneras inte elementet och null returneras:

```powershell
$a = $null
${a}?[0]
```

Mer information [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7).

## <a name="new-view-conciseview-and-cmdlet-get-error"></a>New View ConciseView och cmdlet Get-Error

Visningen av fel meddelanden har förbättrats för att förbättra läsbarheten för interaktiva och skript fel med en ny standardvy **ConciseView**. Vyerna är användare som kan väljas via variabeln Preference `$ErrorView`.

Om ett fel inte är från ett skript eller ett parsningsfel i **ConciseView**, är det ett enda rad fel meddelande:

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

Om felet inträffar under skript körningen eller är ett parsningsfel returnerar PowerShell ett fel meddelande i flera rader som innehåller felet, en pekare och ett fel meddelande som visar var felet finns på raden. Om terminalen inte har stöd för ANSI-färgs escape-sekvenser (VT100) visas inte färger.

![Fel vid visning från ett skript](./media/What-s-New-in-PowerShell-70/myscript-error.png)

Standardvyn i PowerShell 7 är **ConciseView**. Den tidigare **NormalView** är användare valbara genom att ställa in variabeln Preference `$ErrorView`.

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> En ny egenskaps- **ErrorAccentColor** läggs till i `$Host.PrivateData` för att stödja ändring av tilläggs färgen för fel meddelandet.

En ny cmdlet `Get-Error` ger fullständig detaljerad vy över det fullständigt kvalificerade felet när du vill.
Som standard visar cmdleten fullständig information, inklusive inre undantag, av det senaste felet som inträffat.

![Visa från get-Error](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

`Get-Error`-cmdleten stöder inmatade från pipelinen med hjälp av den inbyggda variabeln `$Error`.
`Get-Error` visar alla skickas-fel.

```powershell
$Error | Get-Error
```

`Get-Error`-cmdleten stöder den **senaste** parametern, så att du kan ange hur många fel från den aktuella sessionen som du vill visa.

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

För ytterligare information om [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).

## <a name="new-version-notification"></a>Nytt versions meddelande

PowerShell 7 använder uppdaterings meddelanden för att varna användarna om att det finns uppdateringar till PowerShell.
En gång per dag frågar PowerShell en online tjänst för att avgöra om det finns en nyare version.

> [!NOTE]
> Uppdaterings kontrollen sker under den första sessionen under en viss 24-timmarsperiod. Av prestanda skäl börjar uppdaterings kontrollen 3 sekunder efter att sessionen har börjat. Meddelandet visas bara i början av efterföljande sessioner.

Som standard prenumererar PowerShell på en av två olika meddelande kanaler, beroende på dess version/gren. Allmänt tillgängliga (GA) versioner av PowerShell returnerar endast aviseringar för uppdaterade GA-versioner. För hands versions-och Release Candidate (RC)-versioner meddelar uppdateringar om uppdateringar för Preview-, RC-och GA-versioner.

Du kan ändra beteendet för uppdaterings aviseringar med hjälp av `$Env:POWERSHELL_UPDATECHECK`-miljövariabeln. Följande värden stöds:

- **Standardvärdet** är detsamma som att definiera `$Env:POWERSHELL_UPDATECHECK`
  - GA-versioner meddelar uppdateringar till GA-versioner
  - Preview/RC-versioner meddelar uppdateringar för GA och för hands versioner
- **Off** inaktiverar funktionen för uppdaterings avisering
- **LTS** meddelar bara uppdateringar till GA-versioner för långsiktig betjäning (LTS)

> [!NOTE]
> Miljövariabeln `$Env:POWERSHELL_UPDATECHECK` finns inte förrän den har ställts in för första gången.

Så här anger du versions meddelandet endast för `LTS`-versioner:

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

Så här ställer du in versions meddelandet till `Default` beteendet:

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

Mer information [om uppdaterings meddelanden](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a>Nytt stöd för DSC-resurser med Invoke-Dscresource Keyword Supports (experimentell)

> [!NOTE]
> Det här är en experimentell funktion med namnet **PSDesiredStateConfiguration. InvokeDscResource**. Om du vill veta mer [om experimentella funktioner](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).

`Invoke-DscResource`-cmdleten kör en metod för en angiven DSC-resurs (Desired State Configuration) för PowerShell.

Den här cmdleten anropar en DSC-resurs direkt utan att skapa ett konfigurations dokument. Med den här cmdleten kan konfigurations hanterings produkter hantera Windows eller Linux med hjälp av DSC-resurser. Den här cmdleten aktiverar även fel sökning av resurser när DSC-motorn körs med fel sökning aktiverat.

Det här kommandot anropar **set** -metoden för en resurs med namnet log och anger en **meddelande** egenskap.

```powershell
Invoke-DscResource -Name Log -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Message = 'Hello World'
}
```

Mer information om [Invoke-dscresource Keyword Supports](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).

## <a name="breaking-changes-and-improvements"></a>Bryta ändringar och förbättringar

### <a name="breaking-changes"></a>Icke-bakåtkompatibla ändringar

- Gör uppdaterings aviseringar stöd för LTS och standard kanaler (#11132)
- Uppdatera test-anslutningen så att den fungerar som den som är i Windows PowerShell (#10697) (tack @vexx32!)
- Behåll $? för ParenExpression, under uttryck och ArrayExpression (#11040)
- Ange arbets katalog till den aktuella katalogen i Start-Job (#10920) (tack @iSazonov!)
- Se till att $PSCulture konsekvent reflekterar ändringar i kulturen (#10138) (tack @iSazonov!)

### <a name="engine-updates-and-fixes"></a>Uppdateringar och korrigeringar för motorn

- Förbättringar i Bryt punkts-API: er för fjärrscenarier (#11312)
- Korrigera definitions läckor i PowerShell-klassen i en annan körnings utrymme (#11273)
- Åtgärda en regression i formatering som orsakas av FirstOrDefault-primitiven som lagts till i 7.0.0-preview1 (#11258)
- Ytterligare Microsoft-moduler för att spåra i PS7 telemetri (#10751)
- Gör godkända funktioner icke-experimentella (#11303)
- Uppdatera ConciseView för att använda TargetObject om det är tillämpligt (#11075)
- Åtgärda NullReferenceException i CompletionCompleters offentliga metoder (#11274)
- Korrigera status kontroll för fristående trådar på plattformar som inte kommer från Windows (#11301)
- Uppdatera inställnings PSModulePath för att sammanfoga variablerna för processen och maskin miljön (#11276)
- Stöta på .NET Core till 3.1.0 (#11260)
- Korrigera identifiering av $PSHOME framför $env:P ÖKVÄG (#11141)
- Tillåt att pwsh ärver $env:P SModulePath och gör så att PowerShell. exe startar korrekt (#11057)
- Flytta till .NET Core 3,1 Preview 1 (#10798)
- Kontroll av referens tag gen omstrukturering i fil system leverantören (#10431) (tack @iSazonov!)
- Ersätt CR och New-raden med ett 0x23CE-tecken i skript loggning (#10616)
- Åtgärda en resurs läcka genom att avregistrera händelse hanteraren från AppDomain. CurrentDomain. ProcessExit (#10626)
- Lägg till stöd i Åtgärdsinställning. Break för att bryta till fel sökning när fel sökning, fel, information, förlopp, utförliga eller varnings meddelanden genereras (#8205) (tack @KirkMunro!)
- Aktivera start av kontroll panels tillägg i PowerShell Core utan att ange. CPL-tillägg. (#9828)

### <a name="general-cmdlet-updates-and-fixes"></a>Allmänna cmdlet-uppdateringar och korrigeringar

- Korrigering för problem på Raspbian för att ange datum för fil ändringar i UnixStat experimentell funktion (#11313)
- Lägg till oformaterad text i ConvertFrom – SecureString (#11142)
- WindowsPS-versions kontroll har lagts till för WinCompat (#11148)
- Åtgärda fel – rapportering i vissa WinCompat-scenarier (#11259)
- Lägg till inbyggd binär matchare (#11032) (tack @iSazonov!)
- Uppdatera beräkningen av tecken bredden för att respektera CJK-tecken korrekt (#11262)
- Lägg till avblockering – fil för macOS (#11137)
- Fix regression i get-PSCallStack (#11210) (tack @iSazonov!)
- Ta bort automatisk inläsning av ScheduledJob-modulen när du använder jobb-cmdletar (#11194)
- Lägg till OutputType i get-Error-cmdleten och bevara de ursprungliga TypeName (#10856)
- Korrigera null-referens i egenskapen SupportsVirtualTerminal (#11105)
- Lägg till gräns kontroll i get-WinEvent (#10648) (tack @iSazonov!)
- Åtgärda kommando körningen så att StopUpstreamCommandsException inte fylls i ErrorVariable (#10840)
- Ställ in output-kodningen på [Console]:: OutputEncoding för interna kommandon (#10824)
- Stöd för kod block med flera rader i exempel (#10776) (tack @Greg-Smulko!)
- Lägg till en kultur parameter i SELECT-String-cmdleten (#10943) (tack @iSazonov!)
- Åtgärda start jobbets arbets katalog Sök väg med avslutande omvänt snedstreck (#11041)
- ConvertFrom-JSON: unwrap Collections som standard (#10861) (tack @danstur!)
- Använd Skift läges känslig hash för Group-Object-cmdlet med-CaseSensitive och-AsHashtable växlar (#11030) (tack @vexx32!)
- Hantera undantag om det inte går att räkna upp filer när sökvägen återskapas för att ha rätt Skift läge (#11014)
- Åtgärda ConciseView för att visa aktivitet i stället för kommandot mina (#11007)
- Tillåt att webb-cmdlet: ar ignorerar HTTP-felstatuser (#10466) (tack @vdamewood!)
- Korrigera överdragningen av fler än en CommandInfo till Get-Command (#10929)
- Lägg till cmdleten Get-Counter för Windows (#10933)
- Gör ConvertTo-JSON-behandling [AutomationNull]:: värde och [NullString]:: värde som $null (#10957)
- Ta bort hakparenteser från IPv6-adressen för SSH-fjärrkommunikation (#10968)
- Åtgärda krasch om kommandot som skickas till pwsh är bara blank steg (#10977)
- Tillägg mellan plattformar get-Urklipp och set-Clipboard (#10340)
- Korrigera inställning av ursprunglig sökväg för fil Systems objekt till att inte ha ett extra avslutande snedstreck (#10959)
- Stöd $null för ConvertTo-JSON (#10947)
- Lägg till kommandot back ut – skrivare i Windows (#10906)
- Åtgärda start-Job-WorkingDirectory med blank steg (#10951)
- Returnera standardvärdet när null hämtas för en inställning i PSConfiguration.cs (#10963) (tack @iSazonov!)
- Hantera IO-undantag som icke-avslutande (#10950)
- Lägg till GraphicalHost-sammansättning för att aktivera out-GridView, show-Command och Get-Help-ShowWindow (#10899)
- Ta dator namn via pipeline i get-HotFix (#10852) (tack @kvprasoon!)
- Korrigera att fliken har slutförts för parametrar så att den visar vanliga parametrar som tillgängliga (#10850)
- Korrigera GetCorrectCasedPath () för att först kontrol lera om några system fil poster returneras innan du anropar First () (#10930)
- Ange arbets katalog till den aktuella katalogen i Start-Job (#10920) (tack @iSazonov!)
- Ändra TabExpansion2 till att inte kräva-CursorColumn och behandla som $InputScript. length (#10849)
- Hantera fall där värden inte kan returnera rader eller kolumner på skärmen (#10938)
- Korrigera användningen av dekor färger för värdar som inte stöder dem (#10937)
- Lägg till föregående uppdatering-List kommando (#10922)
- Uppdatera FWLink-ID för Clear-RecycleBin (#10925)
- Hoppa över fil vid slut för ande av filer om det inte går att läsa filattribut (#10910)
- Lägg till Clear-RecycleBin för Windows (#10909)
- Lägg till `$env:__SuppressAnsiEscapeSequences` för att kontrol lera om VT-escape-sekvens i utdata (#10814)
- Lägg till nobetonar parameter för att färga Select-String-utdata (#8963) (tack @derek-xia!)
- Lägg till snabb korrigerings-cmdlet för hämtning (#10740)
- Gör användbara tillägg i program som är värdar för PowerShell (#10587)
- Använd en mer effektiv utvärderings ordning i LanguagePrimitives. IsNullLike () (#10781) (tack @vexx32!)
- Förbättra hanteringen av skickas-indata och skickas strömmar med blandat indata i format-hex (#8674) (tack @vexx32!)
- Använd typ konvertering i SSHConnection hash när värdet inte matchar förväntad typ (#10720) (tack @SeeminglyScience!)
- Korrigera get-Content-ReadCount 0-beteende när-TotalCount har angetts (#10749) (tack @eugenesmlv!)
- Ett fel meddelande om att Word-åtkomst nekades i get-WinEvent (#10639) (tack @iSazonov!)
- Aktivera slut för ande av TABB för variabel tilldelning som är Enum eller typ begränsad (#10646)
- Ta bort den oanvända SourceLength-egenskapen som orsakar problem med formateringen (#10765)
- Parametern Add-delimiter till ConvertFrom-StringData (#10665) (tack @steviecoaster!)
- Lägg till positions parametern för script block när du använder Invoke-Command med SSH (#10721) (tack @machgo!)
- Visa information om linje kontext om flera rader men inte skript namn för ConciseView (#10746)
- Lägg till stöd för \\Wsl $ \ sökvägar till fil system leverantören (#10674)
- Lägg till den token-text som saknas för TokenKind. QuestionMark i parser (#10706)
- Ange aktuell arbets katalog för varje förgrunds-objekt – parallellt kör skript till samma plats som det anropande skriptet. (#10672)
- Ersätt API-ms-win-core-File-L1-2 -2. dll med Kernell32. dll för FindFirstStreamW och FindNextStreamW-API: er (#10680) (tack @iSazonov!)
- Ändra skript för hjälp formatering så att det blir mer StrictMode-tolerant (#10563)
- Add-SecurityDescriptorSDDL-parameter till New-service (#10483) (tack @kvprasoon!)
- Ta bort informations utdata, konsolidera ping-användning i Test-Connection (#10478) (tack @vexx32!)
- Läs särskilda referens punkter utan att komma åt dem (#10662) (tack @iSazonov!)
- Direkt rensa värden till terminalen (#10681) (tack @iSazonov!)
- Lägg till bakgrunds rad för gruppering med format – tabell och-egenskap (#10653)
- Ta bort [ValidateNotNullOrEmpty] från-InputObject på Get-slump för att tillåta en tom sträng (#10644)
- Gör ett skift läges okänsligt läge för system sträng avstånds okänslighet (#10549) (tack @iSazonov!)
- Åtgärda null-referens undantag i framliggande objekt-parallell bearbetning av indata (#10577)
- Lägg till PowerShell-definitioner för grup principer (#10468)
- Uppdatera konsol värden så att den stöder XTPUSHSGR/XTPOPSGR VT-kontroller som används i sammanställnings scenarier. (#10208)
- Lägg till parametern WorkingDirectory till Start-Job (#10324) (tack @davinci26!)
- Ta bort händelse hanteraren som orsakade Bryt punkts ändringar som inte skulle replikeras felaktigt till värd körnings utrymme fel sökning (#10503) (tack @KirkMunro!)
- Ersätt API-ms-win-core-Job-12-1 -0. dll med Kernell32. dll i Microsoft. PowerShell. commands. NativeMethods P/Invoke API (#10417) (tack @iSazonov!)
- Åtgärda fel utdata för New-service i variabel tilldelning och-avvariabel (#10444) (tack @kvprasoon!)
- Åtgärda problem med globala verktyg runt avslutnings kod, kommando rads parametrar och sökväg med blank steg (#10461)
- Åtgärda rekursion i OneDrive-Change FindFirstFileEx () för att använda SafeFindHandle-typ (#10405)
- Hoppa över automatisk inläsning av PSReadLine i Windows om NVDA skärm läsaren är aktiv (#10385)
- Öka de inbyggda-med-PowerShell-modulens versioner till 7.0.0.0 (#10356)
- Lägg till utlöses ett fel i tilläggs typen om det redan finns en typ med samma namn (#9609) (tack @iSazonov!)

### <a name="performance"></a>Prestanda

- Undvik att använda avslutning i parser. SaveError (#11006)
- Förbättra cachelagringen när du skapar nya regex-instanser (#10657) (tack @iSazonov!)
- Förbättra bearbetningen av inbyggda PowerShell-Datadata från types. ps1xml, typesV3. ps1xml och GetEvent. types. ps1xml (#10898)
- Uppdatera PSConfiguration. ReadValueFromFile för att göra det snabbare och mer minne effektivt (#10839)
- Lägg till mindre prestanda förbättringar för körnings utrymme-initiering (#10569) (tack @iSazonov!)
- Gör en förvarsin-objekt snabbare för de scenarier som används ofta (#10454) och åtgärda de stegvisa prestanda problemen för objekt parallellt med många körnings utrymmen (#10455)

### <a name="code-cleanup"></a>Rensa kod

- Ändra kommentar och element text för att uppfylla Microsofts standarder (#11304)
- Problem med att rensa format i Compiler.cs (#10368) (tack @iSazonov!)
- Ta bort den oanvända typ konverteraren för CommaDelimitedStringCollection (#11000) (tack @iSazonov!)
- Rensnings format i InitialSessionState.cs (#10865) (tack @iSazonov!)
- Rensa kod för PSSession-klass (#11001)
- Ta bort körnings funktionen kör uppdatering – hjälp från Get-Help när funktionen Get-Help körs för första gången (#10974)
- Åtgärda problem med formatmall (#10998) (tack @iSazonov!)
- Rensning: Använd det inbyggda aliaset (#10882) (tack @iSazonov!)
- Ta bort den oanvända inställnings nyckeln ConsolePrompting och Undvik att skapa onödig sträng när du ställer frågor till ExecutionPolicy-inställningen (#10985)
- Inaktivera kontroll av uppdaterings meddelande för dagliga builds (#10903) (tack @bergmeister!)
- Återställa fel söknings-API förlorat i #10338 (#10808)
- Ta bort WorkflowJobSourceAdapter-referens som inte längre används (#10326) (tack @KirkMunro!)
- Rensa COM-gränssnitt i snabb List kod genom att åtgärda PreserveSig-attribut (#9899) (tack @weltkante!)
- Lägg till en kommentar som beskriver varför-IA inte är alias för InformationAction common parameter (#10703) (tack @KirkMunro!)
- Byt namn på InvokeCommandCmdlet.cs till InvokeExpressionCommand.cs (#10659) (tack @kilasuit!)
- Lägg till smärre kod rensningar relaterade till uppdaterings meddelanden (#10698)
- Ta bort föråldrad arbets flödes logik från konfigurations skripten för fjärr kommunikation (#10320) (tack @KirkMunro!)
- Uppdatera Hjälp formatet så att det använder rätt Skift läge (#10678) (tack @tnieto88!)
- Rensa CodeFactor-formatmallar som kommer att utföras under den senaste månaden (#10591) (tack @iSazonov!)
- Korrigera skrivfel i beskrivningen av PSTernaryOperator-experimentell funktion (#10586) (tack @bergmeister!)
- Konvertera Åtgärdsinställning. Suspend-uppräkning svärdet till en icke-kompatibel, reserverad status och ta bort begränsningen för att använda Åtgärdsinställning. IGNORE i Preferences-variabler (#10317) (tack @KirkMunro!)
- Ersätt ArrayList med list<T> för att få mer läsbar och tillförlitlig kod utan att ändra funktionerna (#10333) (tack @iSazonov!)
- Gör kod formats korrigeringar till TestConnectionCommand (#10439) (tack @vexx32!)
- Rensa AutomationEngine och ta bort extra SetSessionStateDrive-metod anrop (#10416) (tack @iSazonov!)
- Byt namn på standard ParameterSetName tillbaka till avgränsare för ConvertTo-CSV och ConvertFrom-CSV (#10425)

### <a name="tools"></a>Verktyg

- Lägg till standardinställningen för egenskapen SDKToUse så att den skapas i VS (#11085)
- Install-Powershell. ps1: Lägg till parameter för att använda MSI-installation (#10921) (tack @MJECloud!)
- Lägg till grundläggande exempel för install-PowerShell. ps1 (#10914) (tack @kilasuit!)
- Gör Install-PowerShellRemoting. ps1 för att hantera en tom sträng i PowerShellHome-parametern (#10526) (tack @Orca88!)
- Växla från/etc/lsb-release till/etc/OS-release i install-powershell.sh (#10773) (tack @Himura2la!)
- Kontrol lera pwsh. exe och pwsh i den dagliga versionen av Windows (#10738) (tack @centreboard!)
- Ta bort onödiga tryck i installpsh-osx.sh (#10752)
- Uppdatera install-PowerShell. ps1 för att söka efter redan installerad daglig build (#10489)

### <a name="tests"></a>Resultaten

- Gör ett tillförlitligt DSC-test väntar (#11131)
- Åtgärda stringdata-testet för att verifiera nycklar för hash (#10810)
- Ta bort testmoduler (#11061) (tack @iSazonov!)
- Öka tiden mellan nya test-URL: er (#11015)
- Uppdatera testerna för att korrekt beskriva test åtgärder. (#10928) (Tack @romero126!)
- Tillfälligt hoppa över flaky test TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)
- Gör så att händelse hanteraren läcker testet stabilt (#10790)
- Synkronisera Skift läge i CI YAML (#10767) (tack @RDIL!)
- Lägg till test för korrigering av händelse hanterare som läcker (#10768)
- Lägg till get-ChildItem-test (#10507) (tack @iSazonov!)
- Ersätt tvetydigt språk för test från växla till parameter för noggrannhet (#10666) (tack @romero126!)
- Lägg till experimentell kontroll i förgrunden – objekt parallella tester (#10354) (tack @KirkMunro!)
- Uppdatera tester för Alpine-validering (#10428)

### <a name="build-and-package-improvements"></a>Förbättringar av build och paket

- Åtgärda NuGet-paketets signering för koordinerade paket byggen (#11316)
- Uppdatera beroenden från PowerShell-galleriet och NuGet (#11323)
- Ojämnhet Microsoft. ApplicationInsights från 2.11.0 till 2.12.0 (#11305)
- Ojämnhet Microsoft. CodeAnalysis. CSharp från 3.3.1 till 3.4.0 (#11265)
- Uppdaterings paket för Debian 10 och 11 (#11236)
- Aktivera endast experimentella funktioner före RC (#11162)
- Uppdatera lägsta macOS-version (#11163)
- Ojämnhets NJsonSchema från 10.0.27 till 10.0.28 (#11170)
- Uppdaterar länkar i README.md och metadata. JSON för för hands versionen. 5 (#10854)
- Välj filer för testning av efterlevnad som ägs av PowerShell (#10837)
- Tillåt att win7x86 msix-paketet skapas. (Internt 10515)
- Tillåt att semantiska versioner skickas till NormalizeVersion-funktionen (#11087)
- Stöter på .NET Core Framework till 3,1 – för hands version. 3 (#11079)
- Ojämnhet PSReadLine från 2.0.0-beta5 till 2.0.0-beta6 i/src/Modules (#11078)
- Ojämnhet Newtonsoft. JSON från 12.0.2 till 12.0.3 (#11037) (#11038)
- Lägg till Debian 10, 11 och CentOS 8-paket (#11028)
- Ladda upp JSON-filen för build-info med ReleaseDate-fältet (#10986)
- Stöter på .NET Core Framework till 3,1 – för hands version. 2 (#10993)
- Aktivera build av x86 MSIX-paket (#10934)
- Uppdatera URL: en för installations skriptet för dotNET SDK i build. psm1 (#10927)
- Ojämnhet Markdig. signerat från 0.17.1 till 0.18.0 (#10887)
- Ojämnhets ThreadJob från 2.0.1 till 2.0.2 (#10886)
- Uppdatera AppX-manifest och paketera modul så att de överensstämmer med kraven för MS Store (#10878)
- Uppdatera paket referens för PowerShell SDK för för hands version. 5 (internt 10295)
- Uppdatera ThirdPartyNotices. txt (#10834)
- Ojämnhet Microsoft. PowerShell. Native to 7.0.0 – för hands version. 3 (#10826)
- Ojämnhet Microsoft. ApplicationInsights från 2.10.0 till 2.11.0 (#10608)
- Ojämnhets NJsonSchema från 10.0.24 till 10.0.27 (#10756)
- Lägg till MacPorts-stöd för build-systemet (#10736) (tack @Lucius-Q-User!)
- Ojämnhets PackageManagement från 1.4.4 till 1.4.5 (#10728)
- Ojämnhets NJsonSchema från 10.0.23 till 10.0.24 (#10635)
- Lägg till en miljö variabel för att skilja klient/server-telemetri i MSI (#10612)
- Ojämnhets PSDesiredStateConfiguration från 2.0.3 till 2.0.4 (#10603)
- Ojämnhet Microsoft. CodeAnalysis. CSharp från 3.2.1 till 3.3.1 (#10607)
- Uppdatera till .net Core 3,0 RTM (#10604) (tack @bergmeister!)
- Uppdatera MSIX-paket så att versions kraven för Windows Store (#10588)
- Ojämnhet PowerShellGet-version från 2,2 till 2.2.1 (#10382)
- Ojämnhet PackageManagement-version från 1.4.3 till 1.4.4 (#10383)
- Uppdatera README.md och metadata. JSON för 7.0.0-Preview. 4 (internt 10011)
- Uppgradera .net Core 3,0-versionen från Preview 9 till RC1 (#10552) (tack @bergmeister!)
- Åtgärda genereringen av ExperimentalFeature-listor (internt 9996)
- Ojämnhet PSReadLine-version från 2.0.0-beta4 till 2.0.0-beta5 (#10536)
- Korrigera release build-skript för att ange versions tag gen
- Uppdatera versionen av Microsoft. PowerShell. Native till 7.0.0 – för hands version. 2 (#10519)
- Uppgradera till Netcoreapp 3.0 preview9 (#10484) (tack @bergmeister!)
- Se till att den dagliga samordnade versionen vet att det är en daglig version (#10464)
- Uppdatera den kombinerade paket versionen för att frigöra de dagliga build-versionerna (#10449)
- Ta bort AppVeyor-referens (#10445) (tack @RDIL!)
- Ojämnhet NJsonSchema-version från 10.0.22 till 10.0.23 (#10421)
- Ta bort borttagningen av linux-x64-installationsmappen eftersom vissa beroenden för Alpine behöver den (#10407)

### <a name="documentation-and-help-content"></a>Dokumentation och hjälp innehåll

- Ändrings loggar i en logg per utgåva (#11165)
- Åtgärda FWLinks för PowerShell 7 direkt hjälp dokument (#11071)
- Uppdatera CONTRIBUTING.md (#11096) (tack @mklement0!)
- Åtgärda installations dokument länkar i README.md (#11083)
- Lägger till exempel i Install-PowerShell. ps1-skriptet (#11024) (tack @kilasuit!)
- Korrigera för Select-String betoning och import-Dscresource Keyword Supports i CHANGELOG.md (#10890)
- Ta bort den inaktuella länken från powershell-beginners-guide.md (#10926)
- Sammanfoga stabila och underhålls ändrings loggar (#10527)
- Uppdatera använda .NET-versionen i build-dokument (#10775) (tack @Greg-Smulko!)
- Ersätt länkar från MSDN till docs.microsoft.com i powershell-beginners-guide.md (#10778) (tack @iSazonov!)
- Korrigera bruten DSC översikts länk (#10702)
- Uppdatera Support_Question. MD för att länka till Stack Overflow som en annan grupp resurs (#10638) (tack @mklement0!)
- Lägg till processor arkitektur i mallen för distributions förfrågningen (#10661)
- Lägg till en ny PowerShell-MoL-bok i Learning PowerShell-dokument (#10602)
- Uppdatera README.md och metadata för v 6.1.6 och v 6.2.3-versioner (#10523)
- Åtgärda ett stavfel i README.md (#10465) (tack @vedhasp!)
- Lägg till en referens till PSKoans-modulen i Learning Resources-dokumentationen (#10369) (tack @vexx32!)
- Uppdatera README.md och metadata. JSON för 7.0.0-Preview. 3 (#10393)