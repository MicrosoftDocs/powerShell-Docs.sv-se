---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: c54efeb79f4129b55e078a1ccf9d46afc2e754ab
ms.sourcegitcommit: fb9bafd041e3615b9dc9fb77c9245581b705cd02
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725178"
---
# ForEach-Object

## Sammanfattning
Utför en åtgärd mot varje objekt i en samling inobjekt.

## Syntax

### ScriptBlockSet (standard)

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PropertyAndMethodSet

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ParallelParameterSet

```
ForEach-Object [-InputObject <PSObject>] -Parallel <ScriptBlock> [-ThrottleLimit <Int32>]
 [-TimeoutSeconds <Int32>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

`ForEach-Object`Cmdleten utför en åtgärd på varje objekt i en samling inobjekt. Objekten kan skickas till cmdleten eller anges med parametern **InputObject** .

Från och med Windows PowerShell 3,0 finns det två olika sätt att skapa ett `ForEach-Object` kommando.

- **Skript block**. Du kan använda ett-skript block för att ange åtgärden. I-skript blocket använder du `$_` variabeln för att representera det aktuella objektet. Skript blocket är värdet för **process** parametern. Skript blocket kan innehålla alla PowerShell-skript.

  Till exempel hämtar följande kommando värdet för egenskapen **processname** för varje process på datorn.

  `Get-Process | ForEach-Object {$_.ProcessName}`

  `ForEach-Object` stöder `begin` -, `process` -och- `end` blocken enligt beskrivningen i [about_Functions](about/about_functions.md#piping-objects-to-functions).

  > [!NOTE]
  > Skript blocken körs i anroparens omfång. Därför har blocken åtkomst till variabler i det omfånget och kan skapa nya variabler som finns kvar i det omfånget när cmdleten har slutförts.

- **Åtgärds uttryck**. Du kan också skriva en åtgärds instruktion, som är mycket mer likt naturligt språk. Du kan använda instruktionen operation för att ange ett egenskaps värde eller anropa en metod. Åtgärds instruktioner introducerades i Windows PowerShell 3,0.

  Följande kommando hämtar till exempel också värdet för egenskapen **processname** för varje process på datorn.

  `Get-Process | ForEach-Object ProcessName`

- **Parallellt skript block som körs**. Från och med PowerShell 7,0 är en tredje parameter uppsättning tillgänglig som kör varje skript block parallellt. Parametern **ThrottleLimit** begränsar antalet parallella skript som körs i taget. Som tidigare använder du `$_` variabeln för att representera det aktuella inobjektet i skript blocket. Använd `$using:` nyckelordet för att skicka variabel referenser till skriptet som körs.

  I PowerShell 7 skapas en ny körnings utrymme för varje upprepnings slinga för att säkerställa maximal isolering.
  Detta kan vara en stor prestanda-och resurs träff om det arbete du gör är litet jämfört med att skapa nya körnings utrymmen eller om det finns många iterationer som utför betydande arbete.

  Som standard använder parallell scriptblocks den aktuella arbets katalogen för den anropare som startade parallell aktiviteterna.

  Icke-avslutande fel skrivs till cmdlet: en fel ström när de inträffar parallellt med scriptblocks. Eftersom parallell script block inte kan fastställas, är ordningen i vilken fel visas i fel strömmen. På samma sätt skrivs meddelanden som skrivs till andra data strömmar som varning, utförligt eller information till dessa data strömmar i en obestämd ordning.

  Om du avslutar fel, till exempel undantag, avslutar du den enskilda parallella instansen av scriptblocks där de förekommer. Ett avslutande fel i en scriptblocks kan inte leda till att `Foreach-Object` cmdleten avslutas. De andra scriptblocks, som körs parallellt, fortsätter att köras om de inte också påträffar ett avslutande fel. Det avslutande felet skrivs till fel data strömmen som en **ErrorRecord** med **FullyQualifiedErrorId** `PSTaskException` .
  Avslutande fel kan konverteras till icke-avslutande fel med hjälp av PowerShell-try/catch-eller trap-block.

## Exempel

### Exempel 1: dividera heltal i en matris

Det här exemplet tar en matris med tre heltal och dividerar var och en av dem med 1024.

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### Exempel 2: Hämta längden på alla filer i en katalog

I det här exemplet behandlas filerna och katalogerna i installations katalogen för PowerShell `$PSHOME` .

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

Om objektet inte är en katalog får skript blocket namnet på filen, dividerar värdet för egenskapen **length** med 1024 och lägger till ett blank steg ("") för att skilja det från nästa post. Cmdleten använder egenskapen **PSISContainer** för att avgöra om ett objekt är en katalog.

### Exempel 3: arbeta med de senaste system händelserna

Det här exemplet skriver de senaste 1000 händelserna från systemets händelse logg till en textfil. Aktuell tid visas före och efter bearbetning av händelser.

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

`Get-EventLog` hämtar de senaste 1000 händelserna från system händelse loggen och lagrar dem i `$Events` variabeln. `$Events` skickas sedan till `ForEach-Object` cmdleten. Parametern **BEGIN** visar aktuellt datum och tid. Därefter använder **process** -parametern `Out-File` cmdleten för att skapa en textfil med namnet events.txt och lagrar meddelande egenskapen för varje händelse i filen. Sist används parametern **End** för att visa datum och tid när all bearbetning har slutförts.

### Exempel 4: ändra värdet för en register nyckel

Det här exemplet ändrar värdet för register posten **remotePath** i alla under nycklar under `HKCU:\Network` nyckeln till versal text.

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

Du kan använda det här formatet för att ändra formuläret eller innehållet i ett register post värde.

Varje under nyckel i **nätverks** nyckeln representerar en mappad nätverks enhet som återansluter vid inloggning. **RemotePath** -posten innehåller UNC-sökvägen till den anslutna enheten. Om du till exempel mappar E: enheten till `\\Server\Share` skapas en **E** -postnyckel i `HKCU:\Network` med register värde för **remotePath** inställt på `\\Server\Share` .

Kommandot använder `Get-ItemProperty` cmdleten för att hämta alla under nycklar för **nätverks** nyckeln och `Set-ItemProperty` cmdleten för att ändra värdet för register posten **remotePath** i varje nyckel.
I `Set-ItemProperty` kommandot är sökvägen värdet för egenskapen **PSPath** i register nyckeln. Detta är en egenskap för det Microsoft .NET Framework-objekt som representerar register nyckeln, inte en register post. Kommandot använder metoden **ToUpper ()** i **remotePath** -värdet, som är en sträng (REG_SZ).

Eftersom `Set-ItemProperty` ändrar egenskapen för varje nyckel, `ForEach-Object` krävs cmdleten för att komma åt egenskapen.

### Exempel 5: Använd den automatiska variabeln $Null

I det här exemplet visas en funktion för att skicka den `$Null` automatiska variabeln till `ForEach-Object` cmdleten.

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

Eftersom PowerShell behandlar null som en explicit plats hållare, `ForEach-Object` genererar cmdleten ett värde för `$Null` , precis som för andra objekt som du skickar till den.

### Exempel 6: Hämta egenskaps värden

I det här exemplet hämtas värdet för egenskapen **sökväg** för alla installerade PowerShell-moduler med hjälp av parametern **MemberName** för `ForEach-Object` cmdleten.

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

Det andra kommandot motsvarar det första. Det använder `Foreach` aliaset för `ForEach-Object` cmdleten och utelämnar namnet på parametern **MemberName** , som är valfritt.

`ForEach-Object`Cmdleten är användbar för att hämta egenskaps värden, eftersom den hämtar värdet utan att ändra typen, till skillnad från **format** -cmdletar eller `Select-Object` cmdleten, som ändrar värde typen för egenskapen.

### Exempel 7: dela Modulnamn i namn på komponenter

Det här exemplet visar tre sätt att dela två punktavgränsade modulnamn till sina komponent namn.

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

Kommandona anropar **delnings** metoden för strängar. De tre kommandona använder olika syntax, men de är likvärdiga och utbytbara.

Det första kommandot använder den traditionella syntaxen, som innehåller ett skript block och den aktuella objekt operatorn `$_` . Den använder punktsyntax för att ange den metod och den parentes som ska omges av argumentet avgränsnings uttryck.

Det andra kommandot använder parametern **MemberName** för att ange metoden **Split** och parametern **ArgumentName** för att identifiera punkten (".") som uppdelnings avgränsare.

Det tredje kommandot använder **förgrunds** Ali Aset för `ForEach-Object` cmdleten och utelämnar Namnen på parametrarna **MemberName** och **argument List** , som är valfria.

### Exempel 8: använda ForEach-Object med två skript block

I det här exemplet skickar vi två skript block i position. Alla skript block binder till **process** parametern. De behandlas dock som om de hade skickats till parametrarna **BEGIN** och **process** .

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### Exempel 9: använda ForEach-Object med fler än två skript block

I det här exemplet skickar vi två skript block i position. Alla skript block binder till **process** parametern. De behandlas dock som om de hade skickats till parametrarna **BEGIN**, **process** och **End** .

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> Det första skript blocket mappas alltid till `begin` blocket, det sista blocket mappas till `end` blocket och blocken mellan är alla mappade till `process` blocket.

### Exempel 10: kör flera skript block för varje pipeline-objekt

Som du ser i det föregående exemplet har flera skript block som skickas med **process** parametern mappats till **Start** -och **slut** parametrarna. För att undvika den här mappningen måste du ange explicita värden för **Start** -och **slut** parametrarna.

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

### Exempel 11: kör långsamt skript i parallella batchar

I det här exemplet körs ett enkelt skript block som utvärderar en sträng och vilo läge för en sekund.

```powershell
$Message = "Output:"

1..8 | ForEach-Object -Parallel {
    "$using:Message $_"
    Start-Sleep 1
} -ThrottleLimit 4
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
```

Värdet för parametern **ThrottleLimit** anges till 4 så att indatamängden bearbetas i batchar med fyra.
`$using:`Nyckelordet används för att skicka `$Message` variabeln till varje parallellt skript block.

### Exempel 12: Hämta logg poster parallellt

I det här exemplet hämtas logg poster 50 000 från 5 system loggar på en lokal Windows-dator.

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count
```

```Output
50000
```

Den **parallella** parametern anger det skript block som körs parallellt för varje logg namn. Parametern **ThrottleLimit** säkerställer att alla fem skript block körs samtidigt.

### Exempel 13: kör parallellt som ett jobb

I det här exemplet körs ett enkelt skript block parallellt, vilket skapar två bakgrunds jobb i taget.

```powershell
$job = 1..10 | ForEach-Object -Parallel {
    "Output: $_"
    Start-Sleep 1
} -ThrottleLimit 2 -AsJob

$job | Receive-Job -Wait
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
Output: 9
Output: 10
```

`$job`variabeln tar emot jobbobjektet som samlar in utmatnings data och övervakar körnings tillstånd.
Jobbobjektet är skickas till `Receive-Job` med parametern **väntande** switch. Och detta strömmar utdata till-konsolen, precis som om `ForEach-Object -Parallel` kördes utan **AsJob**.

### Exempel 14: använda tråd säkra variabel referenser

I det här exemplet anropas skript block parallellt för att samla in unika namngivna process objekt.

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
Get-Process | ForEach-Object -Parallel {
    $dict = $using:threadSafeDictionary
    $dict.TryAdd($_.ProcessName, $_)
}

$threadSafeDictionary["pwsh"]
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     82    82.87     130.85      15.55    2808   2 pwsh
```

En enda instans av ett **ConcurrentDictionary** -objekt skickas till varje skript block för att samla in objekten. Eftersom **ConcurrentDictionary** är tråd säker, är det säkert att modifieras av varje parallellt skript. Ett icke-tråd säkert objekt, t. ex **. system. Collections. Generic. Dictionary**, är inte säkert att använda här.

> [!NOTE]
> Det här exemplet är en mycket ineffektiv användning av **parallell** parameter. Skriptet lägger bara till inobjektet i ett objekt i en samtidig ord lista. Det är enkelt och inte värt omkostnaderna för att anropa varje skript i en separat tråd. `ForEach-Object`Att köras normalt utan att den **parallella** växeln är mycket effektivare och snabbare. Det här exemplet är endast avsett för att visa hur du använder tråd säkra variabler.

### Exempel 15: skrivfel med parallell körning

Det här exemplet skriver till fel strömmen parallellt, där ordningen på skrivna fel är slumpmässig.

```powershell
1..3 | ForEach-Object -Parallel {
    Write-Error "Error: $_"
}
```

```Output
Write-Error: Error: 1
Write-Error: Error: 3
Write-Error: Error: 2
```

### Exempel 16: avbryta fel vid parallell körning

Det här exemplet visar ett avslutande fel i en parallell script block.

```powershell
1..5 | ForEach-Object -Parallel {
    if ($_ -eq 3)
    {
        throw "Terminating Error: $_"
    }

    Write-Output "Output: $_"
}
```

```Output
Exception: Terminating Error: 3
Output: 1
Output: 4
Output: 2
Output: 5
```

`Output: 3` skrivs aldrig eftersom parallellt script block för den iterationen avbröts.

## Parametrar

### – Argument List

Anger en matris med argument till ett metod anrop. Mer information om beteendet för **argument List** finns [about_Splatting](about/about_Splatting.md#splatting-with-arrays).

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Börja

Anger ett skript block som körs innan denna cmdlet bearbetar eventuella inobjekt. Det här skript blocket körs bara en gång för hela pipelinen. Mer information om `begin` blocket finns [about_Functions](about/about_functions.md#piping-objects-to-functions).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Slut

Anger ett skript block som körs när denna cmdlet bearbetar alla inobjekt. Det här skript blocket körs bara en gång för hela pipelinen. Mer information om `end` blocket finns [about_Functions](about/about_functions.md#piping-objects-to-functions).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger ingående objekt. `ForEach-Object` Kör skript blocket eller instruktions satsen för varje indatamängds objekt. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

När du använder parametern **InputObject** i `ForEach-Object` , i stället för Skicka kommando resultat till `ForEach-Object` , behandlas **InputObject** -värdet som ett enskilt objekt. Detta gäller även om värdet är en samling som är resultatet av ett kommando, till exempel `-InputObject (Get-Process)` .
Eftersom **InputObject** inte kan returnera enskilda egenskaper från en matris eller samling objekt, rekommenderar vi att om du använder `ForEach-Object` för att utföra åtgärder på en samling objekt för de objekt som har specifika värden i definierade egenskaper, använder du `ForEach-Object` i pipelinen, som du ser i exemplen i det här avsnittet.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – MemberName

Anger den egenskap som ska hämtas eller metoden som ska anropas.

Jokertecken är tillåtna men fungerar bara om den resulterande strängen matchar ett unikt värde.
Om du t. ex. kör `Get-Process | ForEach -MemberName *Name` , matchar jokertecken fler än en medlem som orsakar att kommandot kraschar.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### – Process

Anger den åtgärd som ska utföras för varje indatamängds objekt. Det här skript blocket körs för varje objekt i pipelinen. Mer information om `process` blocket finns [about_Functions](about/about_functions.md#piping-objects-to-functions).

När du anger flera skript block till **process** parametern, mappas det första skript blocket alltid till `begin` blocket. Om det bara finns två skript block mappas det andra blocket till `process` blocket. Om det finns tre eller fler skript block mappas det första skript blocket alltid till `begin` blocket, det sista blocket mappas till `end` blocket och blocken mellan är alla mappade till `process` blocket.

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemainingScripts

Anger alla skript block som inte tas av **process** parametern.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Parallell

Anger det skript block som ska användas för parallell bearbetning av indata-objekt. Ange ett skript block som beskriver åtgärden.

Den här parametern introducerades i PowerShell 7,0.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ParallelParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Anger antalet skript block parallellt. Inmatade objekt blockeras tills det antal som körs är under **ThrottleLimit**. Standardvärdet är `5`.

Den här parametern introducerades i PowerShell 7,0.

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeoutSeconds

Anger antalet sekunder som ska förflyta för att alla inloggade inloggade ska bearbetas parallellt. När tids gränsen har angetts stoppas alla skript som körs. Och eventuella kvarvarande inobjekt som ska bearbetas ignoreras. Standardvärdet `0` inaktiverar tids gränsen och `ForEach-Object -Parallel` kan köras på obestämd tid. Om du skriver <kbd>CTRL</kbd> + <kbd>C</kbd> på kommando raden stoppas ett kommando som körs `ForEach-Object -Parallel` . Den här parametern kan inte användas tillsammans med parametern **AsJob** .

Den här parametern introducerades i PowerShell 7,0.

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### – AsJob

Orsakar parallell anrop att köras som ett PowerShell-jobb. Ett enskilt jobb objekt returneras i stället för utdata från skript blocken som körs. Jobbobjektet innehåller underordnade jobb för varje parallellt skript block som körs. Jobbobjektet kan användas av alla PowerShell-jobb-cmdletar för att övervaka körnings tillstånd och hämta data.

Den här parametern introducerades i PowerShell 7,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Indata

### System. Management. Automation. PSObject

Du kan skicka alla objekt till denna cmdlet.

## Utdata

### System. Management. Automation. PSObject

Denna cmdlet returnerar objekt som bestäms av indatamängden.

## Kommentarer

- `ForEach-Object`Cmdleten fungerar ungefär som en **förgrunds** instruktion, förutom att du inte kan skicka vidare indatamängdar till en **förgrunds** deklaration. Mer information om den **förgrunds** instruktionen finns [about_Foreach](./About/about_Foreach.md).

- Med början i PowerShell 4,0 `Where` och `ForEach` metoder har lagts till för användning med samlingar. Du kan läsa mer om de här nya metoderna här [about_arrays](./About/about_Arrays.md)

- `ForEach-Object -Parallel`Parameter uppsättningen använder PowerShell: s interna API för att köra varje skript block. Detta är betydligt mer arbete än att köra `ForEach-Object` normalt med sekventiell bearbetning. Det är viktigt att använda **parallellt** där behovet av att köra parallellt är litet jämfört med det arbete som skript blocket utför. Exempel:

  - Beräknings intensiva skript på datorer med flera kärnor
  - Skript som tillbringar tid i väntan på resultat eller utför fil åtgärder

  Om du använder den **parallella** parametern kan skript köras mycket långsammare än normalt. Särskilt om de parallella skripten är enkla. Experimentera med **parallellt** för att upptäcka var det kan vara bra.

  > [!IMPORTANT]
  > `ForEach-Object -Parallel`Parameter uppsättningen kör skript block parallellt på separata process trådar. Med `$using:` nyckelordet kan du skicka variabel referenser från cmdlet anrops tråden till varje skript block tråd som körs. Eftersom skript block körs i olika trådar måste de objektvariabler som skickas av referensen användas på ett säkert sätt. Vanligt vis är det säkert att läsa från refererade objekt som inte ändras. Men om objektets status ändras måste du använda tråd säkra objekt, till exempel .net **system. Collection.** desamma typer (se exempel 11).

## Relaterade länkar

[Jämför objekt](../Microsoft.PowerShell.Utility/Compare-Object.md)

[Where-objekt](Where-Object.md)

[Gruppera objekt](../Microsoft.PowerShell.Utility/Group-Object.md)

[Mått – objekt](../Microsoft.PowerShell.Utility/Measure-Object.md)

[Nytt – objekt](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sortera objekt](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Tee – objekt](../Microsoft.PowerShell.Utility/Tee-Object.md)
