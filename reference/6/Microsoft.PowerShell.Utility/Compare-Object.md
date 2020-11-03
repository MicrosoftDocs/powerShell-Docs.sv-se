---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/compare-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compare-Object
ms.openlocfilehash: c72cde8e626993726ae1a52206c88e20c3a7c588
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "93273411"
---
# Compare-Object

## Sammanfattning
Jämför två objekt uppsättningar.

## Syntax

```
Compare-Object [-ReferenceObject] <PSObject[]> [-DifferenceObject] <PSObject[]>
 [-SyncWindow <Int32>] [-Property <Object[]>] [-ExcludeDifferent] [-IncludeEqual] [-PassThru]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## Beskrivning

`Compare-Object`Cmdleten jämför två uppsättningar objekt. En uppsättning objekt är **referensen** och den andra uppsättningen objekt är **skillnaden**.

`Compare-Object` söker efter tillgängliga metoder för att jämföra ett helt objekt. Om det inte går att hitta en lämplig metod anropar den **toString ()** -metoderna för objekten och jämför sträng resultatet. Du kan ange en eller flera egenskaper som ska användas för jämförelse. När egenskaper anges jämför cmdleten bara värdena för dessa egenskaper.

Resultatet av jämförelsen anger om ett egenskaps värde endast visas i **referens** -objektet ( `<=` ) eller endast i **Differens** -objektet ( `=>` ). Om parametern **IncludeEqual** används, `==` anger () att värdet finns i båda objekten.

Om **referensen** eller **Differens** -objekten är null ( `$null` ) `Compare-Object` genererar ett avslutande fel.

Några exempel använder ihopbuntning för att minska rad längden för kod exemplen. Mer information finns i [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).

## Exempel

### Exempel 1 – Jämför innehållet i två textfiler

I det här exemplet jämförs innehållet i två textfiler. Exemplet använder följande två textfiler, med varje värde på en separat rad.

- `Testfile1.txt` innehåller värdena: hund, Squirrel och fågel.
- `Testfile2.txt` innehåller värdena: Cat, fågel och racoon.

Utdata visar bara de rader som skiljer sig åt mellan filerna. `Testfile1.txt` är **referens** objekt ( `<=` ) och `Testfile2.txt` är **Differens** -objektet ( `=>` ). Rader med innehåll som visas i båda filerna visas inte.

```powershell
Compare-Object -ReferenceObject (Get-Content -Path C:\Test\Testfile1.txt) -DifferenceObject (Get-Content -Path C:\Test\Testfile2.txt)
```

```Output
InputObject SideIndicator
----------- -------------
cat         =>
racoon      =>
dog         <=
squirrel    <=
```

### Exempel 2 – jämför varje rad med innehåll och exkluderar skillnaderna

I det här exemplet används parametrarna **IncludeEqual** och **ExcludeDifferent** för att jämföra varje innehålls rad i två textfiler.

Eftersom kommandot använder parametern **ExcludeDifferent** innehåller utdata bara rader i båda filerna, som visas i **SideIndicator** ( `==` ).

```powershell
$objects = @{
  ReferenceObject = (Get-Content -Path C:\Test\Testfile1.txt)
  DifferenceObject = (Get-Content -Path C:\Test\Testfile2.txt)
}
Compare-Object @objects -IncludeEqual -ExcludeDifferent
```

```Output
InputObject SideIndicator
----------- -------------
bird        ==
```

<a id="ex3" />

### Exempel 3 – Visa skillnaden när du använder parametern PassThru

Normalt `Compare-Object` returnerar en **PSCustomObject** -typ med följande egenskaper:

- **InputObject** som jämförs
- Egenskapen **SideIndicator** visar vilket indata-objekt som utdata tillhör

När du använder parametern **Passthru** ändras inte objekt **typen** , men instansen för det returnerade objektet har en tillagd **NoteProperty** som heter **SideIndicator**. **SideIndicator** visar vilket indata-objekt som utdata tillhör.

I följande exempel visas olika typer av utdata.

```powershell
$a = $True
Compare-Object -IncludeEqual $a $a
(Compare-Object -IncludeEqual $a $a) | Get-Member
```

```Output
InputObject SideIndicator
----------- -------------
       True ==

   TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
InputObject   NoteProperty System.Boolean InputObject=True
SideIndicator NoteProperty string SideIndicator===
```

```powershell
Compare-Object -IncludeEqual $a $a -PassThru
(Compare-Object -IncludeEqual $a $a -PassThru) | Get-Member
```

```Output
True

   TypeName: System.Boolean
Name          MemberType   Definition
----          ----------   ----------
CompareTo     Method       int CompareTo(System.Object obj), int CompareTo(bool value), int IComparable.CompareTo(Syst
Equals        Method       bool Equals(System.Object obj), bool Equals(bool obj), bool IEquatable[bool].Equals(bool ot
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
GetTypeCode   Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean     Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte        Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar        Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime    Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal     Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble      Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16       Method       short IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32       Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64       Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte       Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle      Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString      Method       string ToString(), string ToString(System.IFormatProvider provider), string IConvertible.To
ToType        Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16      Method       ushort IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32      Method       uint IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64      Method       ulong IConvertible.ToUInt64(System.IFormatProvider provider)
TryFormat     Method       bool TryFormat(System.Span[char] destination, [ref] int charsWritten)
SideIndicator NoteProperty string SideIndicator===
```

När du använder **Passthru** returneras den ursprungliga objekt typen ( **system. Boolean** ). Observera hur utdata som visas i standardformatet för **system. Boolean** -objekt visar inte egenskapen **SideIndicator** . Men det returnerade **system. Boolean** -objektet har den tillagda **NoteProperty**.

### Exempel 4 – jämför två enkla objekt med hjälp av egenskaper

I det här exemplet jämför vi två olika strängar som har samma längd.

```powershell
Compare-Object -ReferenceObject 'abc' -DifferenceObject 'xyz' -Property Length -IncludeEqual
```

```Output
Length SideIndicator
------ -------------
     3 ==
```

### Exempel 5 – jämföra komplexa objekt med egenskaper

Det här exemplet visar beteendet vid jämförelse av komplexa objekt. I det här exemplet lagrar vi två olika process objekt för olika instanser av PowerShell. Båda variablerna innehåller process objekt med samma namn. När objekten jämförs utan att ange **egenskaps** parametern, betraktar cmdleten objekten som ska vara lika. Observera att värdet för **InputObject** är detsamma som resultatet av metoden **toString ()** . Eftersom klassen **system. Diagnostics. process** inte har gränssnittet **IComparable** , konverterar cmdleten objekten till strängarna och jämför sedan resultaten.

```powershell
PS> Get-Process pwsh

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    101   123.32     139.10      35.81   11168   1 pwsh
     89   107.55      66.97      11.44   17600   1 pwsh

PS> $a = Get-Process -Id 11168
PS> $b = Get-Process -Id 17600
PS> $a.ToString()
System.Diagnostics.Process (pwsh)
PS> $b.ToString()
System.Diagnostics.Process (pwsh)
PS> Compare-Object $a $b -IncludeEqual

InputObject                       SideIndicator
-----------                       -------------
System.Diagnostics.Process (pwsh) ==

PS> Compare-Object $a $b -Property ProcessName, Id, CPU

ProcessName    Id       CPU SideIndicator
-----------    --       --- -------------
pwsh        17600   11.4375 =>
pwsh        11168 36.203125 <=
```

När du anger vilka egenskaper som ska jämföras, visar cmdleten skillnaderna.

### Exempel 6 – jämföra komplexa objekt som implementerar IComparable

Om objektet implementerar **IComparable** söker cmdleten efter sätt att jämföra objekten. Om objekten är olika typer, konverteras **Differens** -objektet till **ReferenceObject** typ och jämförs sedan.

I det här exemplet jämför vi en sträng med ett **TimeSpan** -objekt. I det första fallet konverteras strängen till ett **TimeSpan** så att objekten är lika.

```powershell
Compare-Object ([TimeSpan]"0:0:1") "0:0:1" -IncludeEqual
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    ==
```

```powershell
Compare-Object "0:0:1" ([TimeSpan]"0:0:1")
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    =>
0:0:1       <=
```

I det andra fallet konverteras **TimeSpan** till en sträng så att objektet skiljer sig åt.

## Parametrar

### -CaseSensitive

Anger att jämförelser ska vara Skift läges känslig.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Kultur

Anger kulturen som ska användas för jämförelser.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DifferenceObject

Anger de objekt som jämförs med **referens** objekt.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ExcludeDifferent

Anger att denna cmdlet endast visar egenskaperna för jämförda objekt som är lika. Skillnaderna mellan objekten ignoreras.

Använd **ExcludeDifferent** med **IncludeEqual** för att visa endast de rader som matchar mellan **referens** -och **skillnads** objekt.

Om **ExcludeDifferent** anges utan **IncludeEqual** , finns det inga utdata.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeEqual

**IncludeEqual** visar matchningarna mellan **referens** -och **skillnads** objekt.

Som standard innehåller utdata även skillnaderna mellan **referens** -och **skillnads** objekt.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru

När du använder parametern **Passthru** `Compare-Object` utelämnar **PSCustomObject** -omslutningen runt de jämförda objekten och returnerar olika objekt, oförändrade.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Egenskap

Anger en matris med egenskaper för **referens** -och **skillnads** objekt som ska jämföras.

Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap. Den beräknade egenskapen kan vara ett skript block eller en hash-tabell. Giltiga nyckel/värde-par är:

- Uttryck- `<string>` eller `<script block>`

Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferenceObject

Anger en matris med objekt som används som referens för jämförelse.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SyncWindow

Anger antalet intilliggande objekt som `Compare-Object` inspecar och söker efter en matchning i en objekt samling. `Compare-Object` granskar intilliggande objekt när det inte går att hitta objektet på samma plats i en samling. Standardvärdet är `[Int32]::MaxValue` , vilket innebär att `Compare-Object` hela objekt samlingen genomsöks.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: [Int32]::MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Indata

### System. Management. Automation. PSObject

Du kan skicka ett objekt nedåt i pipelinen till **DifferenceObject** -parametern.

## Utdata

### Inget

Om **referens** -och **Differens** -objektet är samma, finns det inga utdata, om du inte använder parametern **IncludeEqual** .

### System. Management. Automation. PSCustomObject

Om objekten skiljer `Compare-Object` sig från varandra radbryts de olika objekten i en omslutning `PSCustomObject` med en **SideIndicator** -egenskap som refererar till skillnaderna.

När du använder parametern **Passthru** ändras inte objekt **typen** , men instansen för det returnerade objektet har en tillagd **NoteProperty** som heter **SideIndicator**. **SideIndicator** visar vilket indata-objekt som utdata tillhör.

## Kommentarer

När du använder parametern **Passthru** får inte de utdata som visas i-konsolen innehålla egenskapen **SideIndicator** . Standardvyn av för objekt typen utdata av innehåller `Compare-Object` inte egenskapen **SideIndicator** . Mer information finns i [exempel 3](#ex3) i den här artikeln.

## Relaterade länkar

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[-Objekt](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Gruppera objekt](Group-Object.md)

[Mått – objekt](Measure-Object.md)

[Nytt – objekt](New-Object.md)

[Select-Object](Select-Object.md)

[Sortera objekt](Sort-Object.md)

[Tee – objekt](Tee-Object.md)

[Where-objekt](../Microsoft.PowerShell.Core/Where-Object.md)

[Hämta process](../Microsoft.PowerShell.Management/Get-Process.md)
