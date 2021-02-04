---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 97576832ea851f01b463f63948fbd80028c9a6fb
ms.sourcegitcommit: fa1a84c81e15f1ffac962110b0b4c850c1b173a0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2021
ms.locfileid: "99495850"
---
# Get-Random

## SAMMANFATTNING
Hämtar ett slumpmässigt tal eller väljer objekt slumpmässigt från en samling.

## SYNTAX

### RandomNumberParameterSet (standard)

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [<CommonParameters>]
```

### RandomListItemParameterSet

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

## BESKRIVNING

`Get-Random`Cmdleten hämtar ett slumpmässigt valt nummer. Om du skickar en samling objekt till `Get-Random` hämtas ett eller flera slumpmässigt valda objekt från samlingen.

Utan parametrar eller Indatatyp `Get-Random` returnerar ett kommando ett slumpmässigt valt 32-bitars heltal utan tecken mellan 0 (noll) och **Int32. MaxValue** ( `0x7FFFFFFF` , `2,147,483,647` ).

Som standard `Get-Random` genererar kryptografiskt säker slumpmässig het med klassen [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) .

Du kan använda parametrarna för `Get-Random` för att ange lägsta och högsta värden, antalet objekt som returneras från en samling eller ett start nummer.

> [!CAUTION]
> Att ställa in startvärdet för ett avsiktligt resultat i icke-slumpmässig, repeterbar funktion. Den bör endast användas när du försöker återskapa beteende, till exempel vid fel sökning eller analys av ett skript som innehåller `Get-Random` kommandon.
>
> Det här dirigering svärdet används för det aktuella kommandot och för alla efterföljande `Get-Random` kommandon i den aktuella sessionen tills du använder **SetSeed** igen eller stänger sessionen. Du kan inte återställa startvärdet till dess standardvärde.

## EXEMPEL

### Exempel 1: Hämta ett slumpmässigt heltal

Det här kommandot hämtar ett slumpmässigt heltal mellan 0 (noll) och **Int32. MaxValue**.

```powershell
Get-Random
```

```Output
3951433
```

### Exempel 2: Hämta ett slumpmässigt heltal mellan 0 och 99

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### Exempel 3: Hämta ett slumpmässigt heltal mellan-100 och 99

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### Exempel 4: Hämta ett slumpmässigt flytt ALS nummer

Det här kommandot hämtar ett slumpmässigt flytt ALS nummer som är större än eller lika med 10,7 och mindre än 20,92.

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### Exempel 5: Hämta ett slumpmässigt heltal från en matris

Det här kommandot hämtar ett slumpmässigt valt nummer från den angivna matrisen.

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### Exempel 6: få flera slumpmässiga heltal från en matris

Det här kommandot hämtar tre slumpmässigt markerade siffror i slumpmässig ordning från en matris.

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### Exempel 7: Slumpa en hel samling

Det här kommandot returnerar hela samlingen i slumpmässig ordning.

Värdet för **Count** -parametern är egenskapen **MaxValue** static för heltal.

Om du vill returnera en hel samling i slumpmässig ordning anger du ett tal som är större än eller lika med antalet objekt i samlingen.

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count ([int]::MaxValue)
```

```Output
2
3
5
1
8
13
```

### Exempel 8: Hämta ett slumpmässigt icke-numeriskt värde

Det här kommandot returnerar ett slumpmässigt värde från en icke-numerisk samling.

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### Exempel 9: Använd parametern SetSeed

I det här exemplet visas effekterna av att använda parametern **SetSeed** .

Eftersom **SetSeed** genererar icke-slumpmässiga beteenden används vanligt vis endast för att återge resultat, till exempel vid fel sökning eller analys av ett skript.

```powershell
# Commands with the default seed are pseudorandom
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

```powershell
# Commands with the same seed are not random
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
```

```Output
74
74
74
```

```powershell
# SetSeed results in a repeatable series
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

### Exempel 10: Hämta slumpmässiga filer

Dessa kommandon får ett slumpmässigt valt exempel på 50 filer från den `C:` lokala datorns enhet.

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### Exempel 11: sammanfatta verkliga tärningar

Det här exemplet rullar en rättvis Die 1200 gånger och räknar resultatet. Det första kommandot `ForEach-Object` upprepar anropet till `Get-Random` från skickas i siffror (1-6). Resultaten grupperas efter deras värde med `Group-Object` och formaterats som en tabell med `Select-Object` .

```powershell
1..1200 | ForEach-Object {
    1..6 | Get-Random
} | Group-Object | Select-Object Name,Count
```

```Output
Name Count
---- -----
1      206
2      199
3      196
4      226
5      185
6      188
```

## PARAMETRAR

### -Antal

Anger antalet slumpmässiga objekt eller tal som ska returneras. Standard är 1.

`InputObject`Om värdet för **Count** överskrider antalet objekt i samlingen `Get-Random` returneras alla objekt i slumpmässig ordning när det används med.

```yaml
Type: System.Int32
Parameter Sets: RandomListItemParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger en samling objekt. `Get-Random` hämtar slumpmässigt valda objekt i slumpmässig ordning från samlingen upp till det antal som anges i **Count**. Ange objekten, en variabel som innehåller objekten, eller ett kommando eller uttryck som hämtar objekten. Du kan också skicka en samling objekt till `Get-Random` .

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Maximalt

Anger ett max värde för det slumpmässiga talet. `Get-Random` Returnerar ett värde som är mindre än det maximala värdet (inte lika med). Ange ett heltal, ett flyttal med dubbel precision eller ett objekt som kan konverteras till ett heltal eller dubbelt, till exempel en numerisk sträng ("100").

Värdet för **maximum** måste vara större än (lika med) som **minimivärdet**. Om värdet för **maximum** eller **minimum** är ett flytt ALS nummer `Get-Random` returnerar ett slumpmässigt valt flyttal.

På en 64-bitars dator, om värdet för **minimum** är ett 32-bitars heltal **, är** standardvärdet **Int32. MaxValue**.

Om **minimivärdet är ett** Double-värde (ett flytt ALS nummer) är standardvärdet **Max** **Double. MaxValue**. Annars är standardvärdet **Int32. MaxValue**.

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minst

Anger ett minimivärde för det slumpmässiga talet. Ange ett heltal, ett flyttal med dubbel precision eller ett objekt som kan konverteras till ett heltal eller dubbelt, till exempel en numerisk sträng ("100"). Standardvärdet är 0 (noll).

**Minimivärdet måste vara** mindre än (lika med) som **Max** värde. Om värdet för **maximum** eller **minimum** är ett flytt ALS nummer `Get-Random` returnerar ett slumpmässigt valt flyttal.

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SetSeed

Anger ett Seed-värde för slump tals generatorn. När du använder **SetSeed** använder cmdlet: en [system. Random](/dotnet/api/system.random) -metod för att generera pseudorandom-nummer som inte är kryptografiskt säkra.

> [!CAUTION]
> Inställning av Dirigerings resultat i icke-slumpmässiga beteenden. Den bör endast användas när du försöker återskapa beteende, till exempel vid fel sökning eller analys av ett skript som innehåller `Get-Random` kommandon.
>
> Det här dirigering svärdet används för det aktuella kommandot och för alla efterföljande `Get-Random` kommandon i den aktuella sessionen tills du använder **SetSeed** igen eller stänger sessionen. Du kan inte återställa startvärdet till dess standardvärde.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Object

Du kan skicka ett eller flera objekt. `Get-Random` väljer värden slumpmässigt från skickas-objekten.

## UTDATA

### System. Int32, system. Int64, system. Double

`Get-Random` Returnerar ett heltals-eller flytt ALS nummer, eller ett objekt som marker ATS slumpvis från en skickad samling.

## ANTECKNINGAR

Som standard `Get-Random` genererar kryptografiskt säker slumpmässig het med klassen [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) .

`Get-Random` returnerar inte alltid samma datatyp som indatavärdet. I följande tabell visas utdatatypen för var och en av de numeriska inmatnings typerna.

| Indatatyp | Utdatatyp |
| :--------: | :---------: |
|   SByte    |   Double    |
|    Byte    |   Double    |
|   Int16    |   Double    |
|   UInt16   |   Double    |
|   Int32    |    Int32    |
|   UInt32   |   Double    |
|   Int64    |    Int64    |
|   UInt64   |   Double    |
|   Double   |   Double    |
|   Enkel   |   Double    |

Från och med Windows PowerShell 3,0 `Get-Random` stöder 64-bitars heltal. I Windows PowerShell 2,0 omvandlas alla värden till **system. Int32**.

## RELATERADE LÄNKAR

[System. Security. Cryptography. RandomNumberGenerator ()](/dotnet/api/system.security.cryptography.randomnumbergenerator)

[System, slumpmässig](/dotnet/api/system.random)
