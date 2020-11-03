---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Where-Object
ms.openlocfilehash: b5f4a64cceffa1f4f9884bb4de3211e129871ba7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267758"
---
# Where-Object

## SAMMANFATTNING
Väljer objekt från en samling baserat på deras egenskaps värden.

## SYNTAX

### EqualSet (standard)

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-EQ]
 [<CommonParameters>]
```

### ScriptBlockSet

```
Where-Object [-InputObject <PSObject>] [-FilterScript] <ScriptBlock> [<CommonParameters>]
```

### MatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Match
 [<CommonParameters>]
```

### CaseSensitiveEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CEQ
 [<CommonParameters>]
```

### NotEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NE
 [<CommonParameters>]
```

### CaseSensitiveNotEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNE
 [<CommonParameters>]
```

### GreaterThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GT
 [<CommonParameters>]
```

### CaseSensitiveGreaterThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGT
 [<CommonParameters>]
```

### LessThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LT
 [<CommonParameters>]
```

### CaseSensitiveLessThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLT
 [<CommonParameters>]
```

### GreaterOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GE
 [<CommonParameters>]
```

### CaseSensitiveGreaterOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGE
 [<CommonParameters>]
```

### LessOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LE
 [<CommonParameters>]
```

### CaseSensitiveLessOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLE
 [<CommonParameters>]
```

### LikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Like
 [<CommonParameters>]
```

### CaseSensitiveLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLike
 [<CommonParameters>]
```

### NotLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotLike
 [<CommonParameters>]
```

### CaseSensitiveNotLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotLike
 [<CommonParameters>]
```

### CaseSensitiveMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CMatch
 [<CommonParameters>]
```

### NotMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotMatch
 [<CommonParameters>]
```

### CaseSensitiveNotMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotMatch
 [<CommonParameters>]
```

### ContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Contains
 [<CommonParameters>]
```

### CaseSensitiveContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CContains
 [<CommonParameters>]
```

### NotContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotContains
 [<CommonParameters>]
```

### CaseSensitiveNotContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotContains
 [<CommonParameters>]
```

### Luta

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -In
 [<CommonParameters>]
```

### CaseSensitiveInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CIn
 [<CommonParameters>]
```

### NotInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotIn
 [<CommonParameters>]
```

### CaseSensitiveNotInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotIn
 [<CommonParameters>]
```

### IsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Is
 [<CommonParameters>]
```

### IsNotSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -IsNot
 [<CommonParameters>]
```

### Inte

```
Where-Object [-InputObject <PSObject>] [-Property] <String> -Not [<CommonParameters>]
```

## BESKRIVNING

`Where-Object`Cmdleten väljer objekt som har särskilda egenskaps värden från objekt samlingen som skickas till den. Du kan till exempel använda `Where-Object` cmdleten för att välja filer som har skapats efter ett visst datum, händelser med ett visst ID eller datorer som använder en viss version av Windows.

Från och med Windows PowerShell 3,0 finns det två olika sätt att skapa ett `Where-Object` kommando.

- **Skript block**. Du kan använda ett-skript block för att ange egenskaps namn, en jämförelse operator och ett egenskaps värde. `Where-Object` returnerar alla objekt som skript block instruktionen är sann för.

  Följande kommando hämtar till exempel processer i normal prioritets klass, det vill säga processer där värdet för egenskapen **priorityClass** är lika med normal.

  `Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}`

  Alla PowerShell-jämförelse operatorer är giltiga i skript block formatet. Mer information om jämförelse operatorer finns [about_Comparison_Operators](./About/about_Comparison_Operators.md).

- **Jämförelse uttryck**. Du kan också skriva en jämförelse instruktion, som är mycket mer likt naturligt språk. Jämförelse uttryck introducerades i Windows PowerShell 3,0.

  Följande kommandon får till exempel också processer som har prioritets klassen normal. Dessa kommandon är likvärdiga och kan användas utbytbart.

  `Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"`

  `Get-Process | Where-Object PriorityClass -eq "Normal"`

  Från och med Windows PowerShell 3,0 `Where-Object` lägger till jämförelse operatorer som parametrar i ett `Where-Object` kommando. Om inget annat anges är alla operatorer Skift läges känsliga. Före Windows PowerShell 3,0 kan jämförelse operatorerna i PowerShell-språket endast användas i skript block.

När du anger en enskild **egenskap** till `Where-Object` , behandlas värdet för egenskapen som ett booleskt uttryck. Om värdet för **längd** inte är noll utvärderas uttrycket till **Sant**. Exempelvis: `('hi', '', 'there') | Where-Object Length`

Det tidigare exemplet fungerar som en motsvarighet till:

- `('hi', '', 'there') | Where-Object Length -GT 0`
- `('hi', '', 'there') | Where-Object {$_.Length -gt 0}`

## EXEMPEL

### Exempel 1: Hämta stoppade tjänster

De här kommandona hämtar en lista över alla tjänster som för närvarande är stoppade. Den `$_` automatiska variabeln representerar varje objekt som skickas till `Where-Object` cmdleten.

Det första kommandot använder skript block formatet, det andra kommandot använder jämförelse uttryck formatet. Kommandona är likvärdiga och kan användas utbytbara.

```powershell
Get-Service | Where-Object {$_.Status -eq "Stopped"}
Get-Service | where Status -eq "Stopped"
```

### Exempel 2: Hämta processer baserat på arbets minnet

Kommandona visar en lista över processer som har en arbets mängd som är större än 250 megabyte (KB). Syntaxen för script block och-satsen är likvärdig och kan användas utbytbart.

```powershell
Get-Process | Where-Object {$_.WorkingSet -GT 250MB}
Get-Process | Where-Object WorkingSet -GT (250MB)
```

### Exempel 3: Hämta processer baserat på process namn

De här kommandona hämtar de processer som har ett värde för egenskapen **processname** som börjar med bokstaven `p` . Med operatorn **match** kan du använda reguljära uttryck matchningar.

Syntaxen för script block och-satsen är likvärdig och kan användas utbytbart.

```powershell
Get-Process | Where-Object {$_.ProcessName -Match "^p.*"}
Get-Process | Where-Object ProcessName -Match "^p.*"
```

### Exempel 4: Använd formatet jämförelse uttryck

Det här exemplet visar hur du använder det nya jämförelse instruktions formatet för `Where-Object` cmdleten.

Det första kommandot använder jämförelse instruktions formatet.
I det här kommandot används inga alias och alla parametrar inkluderar parameter namnet.

Det andra kommandot är den mer naturliga användningen av jämförelse kommando formatet. `where`Aliaset ersätts med cmdlet- `Where-Object` namnet och alla valfria parameter namn utelämnas.

```powershell
Get-Process | Where-Object -Property Handles -GE -Value 1000
Get-Process | where Handles -GE 1000
```

### Exempel 5: Hämta kommandon baserat på egenskaper

Det här exemplet visar hur du skriver kommandon som returnerar objekt som är true eller false eller som har ett värde för en angiven egenskap. I varje exempel visas formatet skript block och jämförelse uttryck för kommandot.

```powershell
# Use Where-Object to get commands that have any value for the OutputType property of the command.
# This omits commands that do not have an OutputType property and those that have an OutputType property, but no property value.
Get-Command | where OutputType
Get-Command | where {$_.OutputType}
```

```powershell
# Use Where-Object to get objects that are containers.
# This gets objects that have the **PSIsContainer** property with a value of $True and excludes all others.
Get-ChildItem | where PSIsContainer
Get-ChildItem | where {$_.PSIsContainer}
```

```powershell
# Finally, use the Not operator (!) to get objects that are not containers.
# This gets objects that do have the **PSIsContainer** property and those that have a value of $False for the **PSIsContainer** property.
Get-ChildItem | where {!$_.PSIsContainer}
# You cannot use the Not operator (!) in the comparison statement format of the command.
Get-ChildItem | where PSIsContainer -eq $False
```

### Exempel 6: Använd flera villkor

```powershell
Get-Module -ListAvailable | where {($_.Name -notlike "Microsoft*" -and $_.Name -notlike "PS*") -and $_.HelpInfoUri}
```

Det här exemplet visar hur du skapar ett `Where-Object` kommando med flera villkor.

Det här kommandot hämtar moduler som inte är kärnan och som har stöd för den uppdaterbara hjälp funktionen. Kommandot använder **ListAvailable** -parametern för `Get-Module` cmdleten för att hämta alla moduler på datorn. En pipeline-operator ( `|` ) skickar modulerna till `Where-Object` cmdleten, som hämtar moduler vars namn inte börjar med Microsoft eller PS, och har ett värde för egenskapen **HelpInfoURI** , som talar om för PowerShell var du hittar uppdaterade hjälpfiler för modulen. Jämförelse instruktionerna är anslutna med operatorn **och** den logiska operatorn.

I exemplet används skript blockets kommando format. Logiska operatorer, till **And** exempel och **och, är** bara giltiga i skript block. Du kan inte använda dem i jämförelse instruktions formatet för ett `Where-Object` kommando.

- Mer information om logiska PowerShell-operatörer finns [about_Logical_Operators](./About/about_logical_operators.md).
- Mer information om den uppdaterbara hjälp funktionen finns [about_Updatable_Help](./About/about_Updatable_Help.md).

## PARAMETRAR

### -CContains

Anger att denna cmdlet hämtar objekt från en samling om objektets egenskaps värde är en exakt matchning för det angivna värdet. Den här åtgärden är Skift läges känslig.

Exempelvis: `Get-Process | where ProcessName -CContains "svchost"`

**CContains** refererar till en samling värden och är true om samlingen innehåller ett objekt som är en exakt matchning för det angivna värdet. Om indatatypen är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CEQ

Anger att denna cmdlet hämtar objekt om egenskap svärdet är samma som det angivna värdet.
Den här åtgärden är Skift läges känslig.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CGE

Anger att denna cmdlet hämtar objekt om egenskapens värde är större än eller lika med det angivna värdet. Den här åtgärden är Skift läges känslig.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CGT

Anger att denna cmdlet hämtar objekt om egenskapens värde är större än det angivna värdet.
Den här åtgärden är Skift läges känslig.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CIn

Anger att denna cmdlet hämtar objekt om egenskap svärdet innehåller det angivna värdet. Den här åtgärden är Skift läges känslig.

Exempelvis: `Get-Process | where -Value "svchost" -CIn ProcessName`

**CIn** liknar **CContains** , förutom att egenskaps-och värde positionerna är omvända. Följande uttryck är till exempel båda sanna.

`"abc", "def" -CContains "abc"`

`"abc" -CIn "abc", "def"`

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLE

Anger att denna cmdlet hämtar objekt om egenskapens värde är mindre än eller lika med det angivna värdet. Den här åtgärden är Skift läges känslig.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLike

Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar ett värde som innehåller jokertecken. Den här åtgärden är Skift läges känslig.

Exempelvis: `Get-Process | where ProcessName -CLike "*host"`

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLT

Anger att denna cmdlet hämtar objekt om egenskapens värde är mindre än det angivna värdet. Den här åtgärden är Skift läges känslig.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CMatch

Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar det angivna reguljära uttrycket. Den här åtgärden är Skift läges känslig. När indatatypen är skalär, sparas det matchande värdet i den `$Matches` automatiska variabeln.

Exempelvis: `Get-Process | where ProcessName -CMatch "Shell"`

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNE

Anger att denna cmdlet hämtar objekt om egenskap svärdet skiljer sig från det angivna värdet.
Den här åtgärden är Skift läges känslig.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotContains

Anger att denna cmdlet hämtar objekt om objektets egenskaps värde inte är en exakt matchning för det angivna värdet. Den här åtgärden är Skift läges känslig.

Exempelvis: `Get-Process | where ProcessName -CNotContains "svchost"`

**NotContains** och **CNotContains** refererar till en samling värden och är sanna när samlingen inte innehåller några objekt som är en exakt matchning för det angivna värdet. Om indatatypen är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotIn

Anger att denna cmdlet hämtar objekt om egenskap svärdet inte är en exakt matchning för det angivna värdet. Den här åtgärden är Skift läges känslig.

Exempelvis: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`

**NotIn** -och **CNotIn** -operatörer liknar **NotContains** och **CNotContains** , förutom att egenskaps-och värde positionerna är omvända. Följande påståenden är till exempel sanna.

`"abc", "def" -CNotContains "Abc"`

`"abc" -CNotIn "Abc", "def"`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotLike

Anger att denna cmdlet hämtar objekt om egenskap svärdet inte matchar ett värde som innehåller jokertecken. Den här åtgärden är Skift läges känslig.

Exempelvis: `Get-Process | where ProcessName -CNotLike "*host"`

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotMatch

Anger att denna cmdlet hämtar objekt om egenskap svärdet inte matchar det angivna reguljära uttrycket. Den här åtgärden är Skift läges känslig. När indatatypen är skalär, sparas det matchande värdet i den `$Matches` automatiska variabeln.

Exempelvis: `Get-Process | where ProcessName -CNotMatch "Shell"`

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Innehåller

Anger att denna cmdlet hämtar objekt om något objekt i objektets egenskaps värde är en exakt matchning för det angivna värdet.

Exempelvis: `Get-Process | where ProcessName -Contains "Svchost"`

Om egenskap svärdet innehåller ett enda objekt konverterar PowerShell det till en samling med ett objekt.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainsSet
Aliases: IContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EQ

Anger att denna cmdlet hämtar objekt om egenskap svärdet är samma som det angivna värdet.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: EqualSet
Aliases: IEQ

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterScript

Anger det skript block som används för att filtrera objekten. Omge skript blocket med klammerparenteser ( `{}` ).

Parameter namnet, **FilterScript** , är valfritt.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GE

Anger att denna cmdlet hämtar objekt om egenskapens värde är större än eller lika med det angivna värdet.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterOrEqualSet
Aliases: IGE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GT

Anger att denna cmdlet hämtar objekt om egenskapens värde är större än det angivna värdet.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterThanSet
Aliases: IGT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – In

Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar något av de angivna värdena.
Ett exempel:

`Get-Process | where -Property ProcessName -in -Value "Svchost", "TaskHost", "WsmProvHost"`

Om värdet för **Value** -parametern är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.

Om egenskap svärdet för ett objekt är en matris använder PowerShell referens likhet för att fastställa en matchning. `Where-Object` returnerar objektet endast om värdet för **egenskaps** parametern och **värdet för värdet är samma** instans av ett objekt.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InSet
Aliases: IIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger de objekt som ska filtreras. Du kan också skicka objekt till `Where-Object` .

När du använder parametern **InputObject** i `Where-Object` , i stället för Skicka kommando resultat till `Where-Object` , behandlas **InputObject** -värdet som ett enskilt objekt. Detta gäller även om värdet är en samling som är resultatet av ett kommando, till exempel `-InputObject (Get-Process)` . Eftersom **InputObject** inte kan returnera enskilda egenskaper från en matris eller samling objekt, rekommenderar vi att om du använder `Where-Object` för att filtrera en samling objekt för de objekt som har specifika värden i definierade egenskaper, använder du `Where-Object` i pipelinen, som du ser i exemplen i det här avsnittet.

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

### -Är

Anger att denna cmdlet hämtar objekt om egenskap svärdet är en instans av den angivna .NET-typen. Sätt typnamn i hakparenteser.

Till exempel `Get-Process | where StartTime -Is [DateTime]`

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – IsNot

Anger att denna cmdlet hämtar objekt om egenskap svärdet inte är en instans av den angivna .NET-typen.

Till exempel `Get-Process | where StartTime -IsNot [DateTime]`

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsNotSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LE

Anger att denna cmdlet hämtar objekt om egenskapens värde är mindre än eller lika med det angivna värdet.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessOrEqualSet
Aliases: ILE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Som

Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar ett värde som innehåller jokertecken.

Exempelvis: `Get-Process | where ProcessName -Like "*host"`

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LikeSet
Aliases: ILike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LT

Anger att denna cmdlet hämtar objekt om egenskapens värde är mindre än det angivna värdet.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessThanSet
Aliases: ILT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Matcha

Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar det angivna reguljära uttrycket. När indatatypen är skalär, sparas det matchande värdet i den `$Matches` automatiska variabeln.

Exempelvis: `Get-Process | where ProcessName -Match "shell"`

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MatchSet
Aliases: IMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NE

Anger att denna cmdlet hämtar objekt om egenskap svärdet skiljer sig från det angivna värdet.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotEqualSet
Aliases: INE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Inte

Anger att denna cmdlet hämtar objekt om egenskapen inte finns eller har värdet null eller false.

Exempelvis: `Get-Service | where -Not "DependentServices"`

Den här parametern introducerades i Windows PowerShell 6,1.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Not
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotContains

Anger att denna cmdlet hämtar objekt om inget av objekten i egenskap svärdet är en exakt matchning för det angivna värdet.

Exempelvis: `Get-Process | where ProcessName -NotContains "Svchost"`

**NotContains** refererar till en samling värden och är true om samlingen inte innehåller några objekt som är en exakt matchning för det angivna värdet. Om indatatypen är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotContainsSet
Aliases: INotContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotIn

Anger att denna cmdlet hämtar objekt om egenskap svärdet inte är en exakt matchning för något av de angivna värdena.

Exempelvis: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`

Om värdet för **värde** är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.

Om egenskap svärdet för ett objekt är en matris använder PowerShell referens likhet för att fastställa en matchning. `Where-Object` returnerar objektet endast om värdet för **egenskapen** och värdet **för värdet inte är samma** instans av ett objekt.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotInSet
Aliases: INotIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotLike

Anger att denna cmdlet hämtar objekt om egenskap svärdet inte matchar ett värde som innehåller jokertecken.

Exempelvis: `Get-Process | where ProcessName -NotLike "*host"`

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotLikeSet
Aliases: INotLike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotMatch

Anger att denna cmdlet hämtar objekt när egenskap svärdet inte matchar det angivna reguljära uttrycket. När indatatypen är skalär, sparas det matchande värdet i den `$Matches` automatiska variabeln.

Exempelvis: `Get-Process | where ProcessName -NotMatch "PowerShell"`

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotMatchSet
Aliases: INotMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Egenskap

Anger namnet på en objekt egenskap. Parameter namnet, **Property** , är valfritt.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: EqualSet, LessOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet, Not
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Värde

Anger ett egenskaps värde. Parameter namn, **värde** , är valfritt. Den här parametern accepterar jokertecken när de används med följande jämförelse parametrar:

- **CLike**
- **CNotLike**
- **Likadan**
- **NotLike**

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Object
Parameter Sets: EqualSet, LessOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka vidare objekt till denna cmdlet.

## UTDATA

### Objekt

Den här cmdleten returnerar valda objekt från den angivna insamlings objekt uppsättningen.

## ANTECKNINGAR

Startar i Windows PowerShell 4,0 `Where` och `ForEach` metoder lades till för användning med samlingar.

Du kan läsa mer om de här nya metoderna här [about_arrays](./About/about_Arrays.md)

## RELATERADE LÄNKAR

[Jämför objekt](../Microsoft.PowerShell.Utility/Compare-Object.md)

[-Objekt](ForEach-Object.md)

[Gruppera objekt](../Microsoft.PowerShell.Utility/Group-Object.md)

[Mått – objekt](../Microsoft.PowerShell.Utility/Measure-Object.md)

[Nytt – objekt](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sortera objekt](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Tee – objekt](../Microsoft.PowerShell.Utility/Tee-Object.md)

