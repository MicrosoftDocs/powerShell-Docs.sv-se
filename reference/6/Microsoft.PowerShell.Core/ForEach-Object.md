---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 5a1a53c2b312ef36c80ecfb2a771d2fee2ebea7f
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/10/2020
ms.locfileid: "93269451"
---
# ForEach-Object

## SAMMANFATTNING
Utför en åtgärd mot varje objekt i en samling inobjekt.

## SYNTAX

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

## BESKRIVNING

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

## EXEMPEL

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

I det här exemplet skriver du de senaste 1000 händelserna från systemets händelse logg till en textfil. Aktuell tid visas före och efter bearbetning av händelser.

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

Varje under nyckel i **nätverks** nyckeln representerar en mappad nätverks enhet som kommer att återansluta vid inloggning.
**RemotePath** -posten innehåller UNC-sökvägen till den anslutna enheten. Om du till exempel mappar E: enheten till `\\Server\Share` , kommer det att finnas en **E** -under nyckel `HKCU:\Network` och värdet för register posten **remotePath** i **E** -undernyckeln är `\\Server\Share` .

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

`ForEach-Object`Cmdleten är mycket användbar för att hämta egenskaps värden, eftersom den hämtar värdet utan att ändra typen, till skillnad från **format** -cmdlet: ar eller `Select-Object` cmdleten, som ändrar egenskaps värde typen.

### Exempel 7: dela Modulnamn i namn på komponenter

I det här exemplet visas tre sätt att dela två punktavgränsade modulnamn till sina komponent namn.

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

I det här exemplet skickar vi två skript block i position. Alla skript block binder till **process** parametern. De behandlas dock som om de hade skickats till parametrarna **BEGIN** , **process** och **End** .

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

## PARAMETRAR

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
Om du till exempel kör `Get-Process | ForEach -MemberName *Name` och fler än en medlem finns med ett namn som innehåller sträng namnet, t. ex. egenskaperna **processname** och **Name** , Miss lyckas kommandot.

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

## INDATA

### System. Management. Automation. PSObject

Du kan skicka alla objekt till denna cmdlet.

## UTDATA

### System. Management. Automation. PSObject

Denna cmdlet returnerar objekt som bestäms av indatamängden.

## ANTECKNINGAR

- `ForEach-Object`Cmdleten fungerar ungefär som en **förgrunds** instruktion, förutom att du inte kan skicka vidare indatamängdar till en **förgrunds** deklaration. Mer information om den **förgrunds** instruktionen finns [about_Foreach](./About/about_Foreach.md).

- Med början i PowerShell 4,0 `Where` och `ForEach` metoder har lagts till för användning med samlingar. Du kan läsa mer om de här nya metoderna här [about_arrays](./About/about_Arrays.md)

## RELATERADE LÄNKAR

[Jämför objekt](../Microsoft.PowerShell.Utility/Compare-Object.md)

[Where-objekt](Where-Object.md)

[Gruppera objekt](../Microsoft.PowerShell.Utility/Group-Object.md)

[Mått – objekt](../Microsoft.PowerShell.Utility/Measure-Object.md)

[Nytt – objekt](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sortera objekt](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Tee – objekt](../Microsoft.PowerShell.Utility/Tee-Object.md)
