---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Object
ms.openlocfilehash: 11aedd0f5249153e01382132c9eeb95f0717cda3
ms.sourcegitcommit: f9ae48d026d65833b9c8ca881058dda0bbd067b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/25/2020
ms.locfileid: "93269589"
---
# Select-Object

## SAMMANFATTNING
Markerar objekt eller objekt egenskaper.

## SYNTAX

### DefaultParameter (standard)

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-Last <Int32>] [-First <Int32>] [-Skip <Int32>] [-Wait]
 [<CommonParameters>]
```

### SkipLastParameter

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-SkipLast <Int32>] [<CommonParameters>]
```

### IndexParameter

```
Select-Object [-InputObject <PSObject>] [-Unique] [-Wait] [-Index <Int32[]>] [<CommonParameters>]
```

### SkipIndexParameter

```
Select-Object [-InputObject <PSObject>] [-Unique] [-SkipIndex <Int32[]>] [<CommonParameters>]
```

## BESKRIVNING

`Select-Object`Cmdleten väljer angivna egenskaper för ett objekt eller en uppsättning objekt. Det kan också välja unika objekt, ett angivet antal objekt eller objekt på en angiven position i en matris.

Om du vill välja objekt från en samling använder du parametrarna **First** , **Last** , **Unique** , **Skip** och **index** . Om du vill välja objekt egenskaper använder du **egenskaps** parametern. När du väljer Egenskaper `Select-Object` returnerar nya objekt som bara har de angivna egenskaperna.

Från och med Windows PowerShell 3,0 `Select-Object` innehåller en optimerings funktion som förhindrar att kommandon skapar och bearbetar objekt som inte används.

När du inkluderar ett `Select-Object` kommando med de **första** parametrarna eller **index** parametrarna i en kommando pipeline, stoppar PowerShell kommandot som genererar objekten så snart det valda antalet objekt genereras, även när kommandot som genererar objekten visas före `Select-Object` kommandot i pipelinen. Om du vill inaktivera optimerings beteendet använder du parametern **wait** .

## EXEMPEL

### Exempel 1: Välj objekt efter egenskap

I det här exemplet skapas objekt som har egenskaper för **namn** , **ID** och arbets minne ( **WS** ) för process objekt.

```powershell
Get-Process | Select-Object -Property ProcessName, Id, WS
```

### Exempel 2: Välj objekt efter egenskap och formatera resultaten

I det här exemplet får du information om de moduler som används av processerna på datorn. Den använder `Get-Process` cmdleten för att hämta processen på datorn.

Den använder `Select-Object` cmdleten för att mata ut en matris med `[System.Diagnostics.ProcessModule]` instanser som finns i egenskapen **modules** för varje `System.Diagnostics.Process` instans som matas ut av `Get-Process` .

**Egenskaps** parametern för `Select-Object` cmdleten väljer process namnen. Detta lägger till en `ProcessName` **NoteProperty** till varje `[System.Diagnostics.ProcessModule]` instans och fyller den med värdet för den aktuella processens **processname** -egenskap.

Slutligen `Format-List` används cmdleten för att visa namn och moduler för varje process i en lista.

```powershell
Get-Process Explorer | Select-Object -Property ProcessName -ExpandProperty Modules | Format-List
```

```Output
ProcessName       : explorer
ModuleName        : explorer.exe
FileName          : C:\WINDOWS\explorer.exe
BaseAddress       : 140697278152704
ModuleMemorySize  : 3919872
EntryPointAddress : 140697278841168
FileVersionInfo   : File:             C:\WINDOWS\explorer.exe
                    InternalName:     explorer
                    OriginalFilename: EXPLORER.EXE.MUI
                    FileVersion:      10.0.17134.1 (WinBuild.160101.0800)
                    FileDescription:  Windows Explorer
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.17134.1
...
```

### Exempel 3: Välj processer som använder mest minne

Det här exemplet hämtar de fem processerna som använder mest minne. `Get-Process`Cmdleten hämtar processerna på datorn. `Sort-Object`Cmdleten sorterar processerna efter minnes användning (arbets minne) och- `Select-Object` cmdleten väljer bara de sista fem medlemmarna i den resulterande matrisen med objekt.

Parametern **wait** krävs inte i kommandon som innehåller `Sort-Object` cmdleten eftersom `Sort-Object` bearbetar alla objekt och returnerar sedan en samling. `Select-Object`Optimeringen är endast tillgänglig för kommandon som returnerar objekt individuellt när de bearbetas.

```powershell
Get-Process | Sort-Object -Property WS | Select-Object -Last 5
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VS(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
2866     320       33432      45764   203   222.41   1292 svchost
577      17        23676      50516   265    50.58   4388 WINWORD
826      11        75448      76712   188    19.77   3780 Ps
1367     14        73152      88736   216    61.69    676 Ps
1612     44        66080      92780   380   900.59   6132 INFOPATH
```

### Exempel 4: Välj unika tecken från en matris

I det här exemplet används den **unika** parametern för `Select-Object` för att hämta unika tecken från en matris med tecken.

```powershell
"a","b","c","a","a","a" | Select-Object -Unique
```

```Output
a
b
c
```

### Exempel 5: Välj nyaste och äldsta händelser i händelse loggen

Det här exemplet hämtar de första (nyaste) och senaste (äldsta) händelserna i Windows PowerShell-händelseloggen.

`Get-EventLog` hämtar alla händelser i Windows PowerShell-loggen och sparar dem i `$a` variabeln.
Sedan `$a` är skickas till `Select-Object` cmdleten. `Select-Object`Kommandot använder parametern **index** för att välja händelser från händelsens matris i `$a` variabeln. Indexet för den första händelsen är 0. Indexet för den sista händelsen är antalet objekt i `$a` minus 1.

```powershell
$a = Get-EventLog -LogName "Windows PowerShell"
$a | Select-Object -Index 0, ($A.count - 1)
```

### Exempel 6: Markera alla utom det första objektet

I det här exemplet skapas en ny PSSession på var och en av de datorer som anges i Servers.txt-filer, förutom den första.

`Select-Object` markerar alla utom den första datorn i en lista över dator namn. Den resulterande listan med datorer anges som värde för parametern **computername** för `New-PSSession` cmdleten.

```powershell
New-PSSession -ComputerName (Get-Content Servers.txt | Select-Object -Skip 1)
```

### Exempel 7: Byt namn på filer och välj flera för att granska

I det här exemplet läggs ett "-ro"-suffix till i grundnamnen på textfiler som har det skrivskyddade attributet och sedan visas de första fem filerna så att användaren kan se ett exempel på resultatet.

`Get-ChildItem` använder den **skrivskyddade** dynamiska parametern för att hämta skrivskyddade filer. De resulterande filerna är skickas till `Rename-Item` cmdleten, som byter namn på filen. Den använder parametern **Passthru** för `Rename-Item` för att skicka de omdöpta filerna till `Select-Object` cmdleten, som väljer de första 5 för visning.

Parametern **wait** i `Select-Object` förhindrar att PowerShell stoppar `Get-ChildItem` cmdleten när den får de första fem skrivskyddade textfilerna. Utan den här parametern får bara de fem första skrivskyddade filerna namnet.

```powershell
Get-ChildItem *.txt -ReadOnly |
    Rename-Item -NewName {$_.BaseName + "-ro.txt"} -PassThru |
    Select-Object -First 5 -Wait
```

### Exempel 8: demonstrera erna för parametern-ExpandProperty

Det här exemplet demonstrerar erna för parametern **ExpandProperty** .

Observera att de utdata som genereras var en matris med `[System.Int32]` instanser. Instanserna följer standardformateringsregler i **vyn utdata**. Detta gäller för alla *utökade* egenskaper. Om det finns ett standardformat för objekten i listan kanske den utökade egenskapen inte visas.

```powershell
# Create a custom object to use for the Select-Object example.
$object = [pscustomobject]@{Name="CustomObject";Expand=@(1,2,3,4,5)}
# Use the ExpandProperty parameter to Expand the property.
$object | Select-Object -ExpandProperty Expand -Property Name
```

```Output
1
2
3
4
5
```

```powershell
# The output did not contain the Name property, but it was added successfully.
# Use Get-Member to confirm the Name property was added and populated.
$object | Select-Object -ExpandProperty Expand -Property Name | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType   Definition
----        ----------   ----------
CompareTo   Method       int CompareTo(System.Object value), int CompareTo(int value), int IComparable.CompareTo(System.Object obj)...
Equals      Method       bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int].Equals(int other)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
GetTypeCode Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar      Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime  Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal   Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble    Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16     Method       int16 IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32     Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64     Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte     Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle    Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString    Method       string ToString(), string ToString(string format), string ToString(System.IFormatProvider provider)...
ToType      Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16    Method       uint16 IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32    Method       uint32 IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64    Method       uint64 IConvertible.ToUInt64(System.IFormatProvider provider)
Name        NoteProperty string Name=CustomObject
```

### Exempel 9: skapa anpassade egenskaper för objekt

I följande exempel visas hur `Select-Object` du lägger till en anpassad egenskap i alla objekt.
När du anger ett egenskaps namn som inte finns `Select-Object` skapar den egenskapen som en **NoteProperty** för varje objekt som skickas.

```powershell
$customObject = 1 | Select-Object -Property MyCustomProperty
$customObject.MyCustomProperty = "New Custom Property"
$customObject
```

```Output
MyCustomProperty
----------------
New Custom Property
```

### Exempel 10: skapa beräknade egenskaper för varje InputObject

I det här exemplet visas hur `Select-Object` du lägger till beräknade egenskaper i dina inaktuella inaktuella. Genom att skicka en **script block** till **egenskaps** parametern kan du `Select-Object` utvärdera uttrycket för varje objekt som skickas och lägga till resultaten i utdata. I **script block** kan du använda `$_` variabeln för att referera till det aktuella objektet i pipelinen.

Som standard `Select-Object` använder **script block** -strängen som namn på egenskapen. Med hjälp av en **hash-hash** kan du märka utdata från din **script block** som en anpassad egenskap som har lagts till i varje objekt. Du kan lägga till flera beräknade egenskaper för varje objekt som skickas till `Select-Object` .

```powershell
# Create a calculated property called $_.StartTime.DayOfWeek
Get-Process | Select-Object -Property ProcessName,{$_.StartTime.DayOfWeek}
```

```Output
ProcessName  $_.StartTime.DayOfWeek
----         ----------------------
alg                       Wednesday
ati2evxx                  Wednesday
ati2evxx                   Thursday
...
```

```powershell
# Add a custom property to calculate the size in KiloBytes of each FileInfo object you pass in.
# Use the pipeline variable to divide each file's length by 1 KiloBytes
$size = @{label="Size(KB)";expression={$_.length/1KB}}
# Create an additional calculated property with the number of Days since the file was last accessed.
# You can also shorten the key names to be 'l', and 'e', or use Name instead of Label.
$days = @{l="Days";e={((Get-Date) - $_.LastAccessTime).Days}}
# You can also shorten the name of your label key to 'l' and your expression key to 'e'.
Get-ChildItem $PSHOME -File | Select-Object Name, $size, $days
```

```Output
Name                        Size(KB)        Days
----                        --------        ----
Certificate.format.ps1xml   12.5244140625   223
Diagnostics.Format.ps1xml   4.955078125     223
DotNetTypes.format.ps1xml   134.9833984375  223
```

## PARAMETRAR

### -ExcludeProperty

Anger egenskaperna som denna cmdlet exkluderar från åtgärden. Jokertecken är tillåtna.

Från och med PowerShell 6 behöver du inte längre inkludera **egenskaps** parametern för att **ExcludeProperty** ska fungera.

```yaml
Type: System.String[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### – ExpandProperty

Anger en egenskap som ska väljas och indikerar att ett försök ska göras för att expandera den egenskapen.

- Om den angivna egenskapen är en matris ingår varje mat ris värde i utdata.
- Om den angivna egenskapen är ett objekt expanderas objekt egenskaperna för varje **InputObject**

I båda fallen matchar **typen** av objekt utdata den **typ** av utökad egenskap som visas.

Om **egenskaps** parametern har angetts `Select-Object` försöker att lägga till varje vald egenskap som **NoteProperty** till varje utgivna objekt.

> [!WARNING]
> Om du får felet: SELECT: egenskapen kan inte bearbetas eftersom egenskapen `<PropertyName>` redan finns, Tänk på följande.
> Observera att när `-ExpandProperty` du använder, `Select-Object` inte kan ersätta en befintlig egenskap.
> Det innebär att du måste:
>
> - Om det utökade objektet har en egenskap med samma namn, uppstår ett fel.
> - Om det *valda* objektet har en egenskap med samma namn som en *utökad* objekt egenskap uppstår ett fel.

```yaml
Type: System.String
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Första

Anger antalet objekt som ska väljas från början av en matris med inobjekt.

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Index

Väljer objekt från en matris baserat på deras index värden. Ange indexen i en kommaavgränsad lista. Index i en matris börjar med 0, där 0 representerar det första värdet och (n-1) representerar det sista värdet.

```yaml
Type: System.Int32[]
Parameter Sets: IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger objekt som ska skickas till cmdleten via pipelinen. Med den här parametern kan du skicka pipe-objekt till `Select-Object` .

När du skickar objekt till parametern **InputObject** , i stället för att använda pipelinen, `Select-Object` behandlar **InputObject** som ett enskilt objekt, även om värdet är en samling. Vi rekommenderar att du använder pipelinen när du skickar samlingar till `Select-Object` .

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

### -Senaste

Anger antalet objekt som ska väljas från slutet av en matris med inobjekt.

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Egenskap

Anger de egenskaper som ska väljas. De här egenskaperna läggs till som **NoteProperty** -medlemmar i objekten. Jokertecken är tillåtna.

Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap. Om du vill skapa en beräknad egenskap använder du en hash-tabell.

Giltiga nycklar är:

- Namn (eller etikett)- `<string>`
- Uttryck- `<string>` eller `<script block>`

Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Hoppa över

Hoppar över (väljer inte) det angivna antalet objekt. Som standard räknas **Skip** -parametern från början av matrisen eller listan över objekt, men om kommandot använder den **sista** parametern räknas det från slutet av listan eller matrisen.

Till skillnad från parametern **index** , som börjar räkna vid 0, börjar **Skip** -parametern vid 1.

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipLast

Hoppar över (väljer inte) det angivna antalet objekt från slutet av listan eller matrisen. Fungerar på samma sätt som att använda **Skip** tillsammans med den **sista** parametern.

Till skillnad från parametern **index** , som börjar räkna med 0, börjar **SkipLast** -parametern på 1.

```yaml
Type: System.Int32
Parameter Sets: SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Unik

Anger att om en delmängd av inobjekten har identiska egenskaper och värden, väljs bara en enskild medlem i del mängden.

Den här parametern är Skift läges känslig. Det innebär att strängar som bara skiljer sig i gemener och versaler anses vara unika.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Vänta

Anger att-cmdleten inaktiverar optimering. PowerShell kör kommandon i den ordning som de visas i kommandot pipeliner och låter dem generera alla objekt. Om du inkluderar ett `Select-Object` kommando med de **första** eller **index** parametrarna i en kommando pipeline, stoppar PowerShell som standard kommandot som genererar objekten så fort det valda antalet objekt genereras.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultParameter, IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipIndex

```yaml
Type: System.Int32[]
Parameter Sets: SkipIndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka vidare alla objekt till `Select-Object` .

## UTDATA

### System. Management. Automation. PSObject

## ANTECKNINGAR

- Du kan också referera till `Select-Object` cmdleten med dess inbyggda alias `select` . Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

- Optimerings funktionen i `Select-Object` är bara tillgänglig för kommandon som skriver objekt till pipelinen när de bearbetas. Den har ingen påverkan på kommandon som buffrar bearbetade objekt och skriver dem som en samling. Att skriva objekt direkt är en bästa praxis för cmdlet-design. Mer information finns i _skriva enstaka poster till pipelinen i den_ [starkt uppmuntrande utvecklings rikt linjerna](/powershell/scripting/developer/windows-powershell).

## RELATERADE LÄNKAR

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Gruppera objekt](Group-Object.md)

[Sortera objekt](Sort-Object.md)

[Where-objekt](../Microsoft.PowerShell.Core/Where-Object.md)
