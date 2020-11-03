---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-table?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Table
ms.openlocfilehash: dc406be942cce50fea7d39cae705834353ff6941
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "93269061"
---
# Format-Table

## SAMMANFATTNING
Formaterar utdata som en tabell.

## SYNTAX

### Alla

```
Format-Table [-AutoSize] [-RepeatHeader] [-HideTableHeaders] [-Wrap] [[-Property] <Object[]>]
 [-GroupBy <Object>] [-View <String>] [-ShowError] [-DisplayError] [-Force] [-Expand <String>]
 [-InputObject <PSObject>] [<CommonParameters>]
```

## BESKRIVNING

`Format-Table`Cmdleten formaterar utdata från ett kommando som en tabell med de valda egenskaperna för objektet i varje kolumn. Objekt typen bestämmer standardlayouten och egenskaperna som visas i varje kolumn. Du kan använda **egenskaps** parametern för att välja de egenskaper som du vill visa.

PowerShell använder standardformat för att definiera hur objekt typer visas. Du kan använda `.ps1xml` filer för att skapa anpassade vyer som visar en utgående tabell med angivna egenskaper. När en anpassad vy har skapats använder du parametern **View** för att visa tabellen med din anpassade vy. Mer information om vyer finns i [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).

Du kan använda en hash-tabell för att lägga till beräknade egenskaper till ett objekt innan du visar det och för att ange kolumn rubrikerna i tabellen. Använd **egenskapen** eller **groupby** -parametern om du vill lägga till en beräknad egenskap. Mer information om hash-tabeller finns i [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).

## EXEMPEL

### Exempel 1: formatera PowerShell-värd

I det här exemplet visas information om värd programmet för PowerShell i en tabell.

```powershell
Get-Host | Format-Table -AutoSize
```

`Get-Host`Cmdleten hämtar **system. Management. Automation. Internal. Host. InternalHost** -objekt som representerar värden. Objekten skickas ned pipelinen till `Format-Table` och visas i en tabell. Parametern **AutoSize** justerar kolumn bredderna för att minimera trunkering.

### Exempel 2: formatera processer efter BasePriority

I det här exemplet visas processer i grupper som har samma **BasePriority** -egenskap.

```powershell
Get-Process | Sort-Object -Property BasePriority | Format-Table -GroupBy BasePriority -Wrap
```

`Get-Process`Cmdleten hämtar objekt som representerar varje process på datorn och skickar dem nedåt i pipeline till `Sort-Object` . Objekten sorteras i ordningen för deras **BasePriority** -egenskap.

De sorterade objekten skickas ned pipelinen till `Format-Table` . Parametern **groupby** ordnar process data i grupper baserat på deras värde för egenskapen **BasePriority** . **Wrap** -parametern ser till att data inte trunkeras.

### Exempel 3: formatera processer efter start datum

I det här exemplet visas information om processerna som körs på datorn. Objekten sorteras och `Format-Table` använder en vy för att gruppera objekten efter deras start datum.

```powershell
Get-Process | Sort-Object StartTime | Format-Table -View StartTime
```

`Get-Process` hämtar de **system. Diagnostics. process** -objekt som representerar processerna som körs på datorn. Objekten skickas ned till pipelinen till `Sort-Object` och sorteras baserat på egenskapen **StartTime** .

De sorterade objekten skickas ned pipelinen till `Format-Table` . Parametern **View** anger den **StartTime** -vy som definieras i PowerShell- `DotNetTypes.format.ps1xml` filen för **system. Diagnostics. process** -objekt. Vyn **StartTime** konverterar varje processs start tid till ett kort datum och grupperar sedan processerna efter start datum.

`DotNetTypes.format.ps1xml`Filen innehåller en **prioritets** vy för processer. Du kan skapa egna `format.ps1xml` filer med anpassade vyer.

### Exempel 4: Använd en anpassad vy för tabellens utdata

I det här exemplet visar en anpassad vy katalogens innehåll. Den anpassade vyn lägger till kolumnen **CreationTime** i tabellen utdata för **system. io. DirectoryInfo** och **system. io. fileinfo** objekt som skapats av `Get-ChildItem` .

Den anpassade vyn i det här exemplet skapades från vyn som definierats i PowerShell-källkod. Mer information om vyer och koden som används för att skapa det här exemplets vy finns i [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view).

```powershell
Get-ChildItem  -Path C:\Test | Format-Table -View mygciview
```

```Output
    Directory: C:\Test

Mode                LastWriteTime              CreationTime         Length Name
----                -------------              ------------         ------ ----
d-----        11/4/2019     15:54       9/24/2019     15:54                Archives
d-----        8/27/2019     14:22       8/27/2019     14:22                Drawings
d-----       10/23/2019     09:38       2/25/2019     09:38                Files
-a----        11/7/2019     11:07       11/7/2019     11:07          11345 Alias.txt
-a----        2/27/2019     15:15       2/27/2019     15:15            258 alias_out.txt
-a----        2/27/2019     15:16       2/27/2019     15:16            258 alias_out2.txt
```

`Get-ChildItem` hämtar innehållet i den aktuella katalogen `C:\Test` . **System. io. DirectoryInfo** och **system. io. fileinfo** -objekten skickas nedåt i pipelinen.
`Format-Table` använder parametern **View** för att ange den anpassade vyn **mygciview** som innehåller kolumnen **CreationTime** .

Standardutdata `Format-Table` för `Get-ChildItem` inkluderar inte kolumnen **CreationTime** .

### Exempel 5: Använd egenskaper för tabellens utdata

I det här exemplet används **egenskaps** parametern för att visa alla dator tjänster i en tabell med två kolumner som visar egenskaperna **Name** och **DependentServices**.

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

`Get-Service` hämtar alla tjänster på datorn och skickar **system. ServiceProcess. ServiceController** -objekten nedåt i pipelinen. `Format-Table` använder **egenskaps** parametern för att ange att egenskaperna **namn** och **DependentServices** ska visas i tabellen.

**Namn** -och **DependentServices** är två av objekt typens egenskaper. Så här visar du alla egenskaper: `Get-Service | Get-Member -MemberType Properties` .

### Exempel 6: formatera en process och beräkna dess kör tid

I det här exemplet visas en tabell med process namnet och den totala körnings tiden för den lokala datorns **anteckningar** -processer. Den totala körnings tiden beräknas genom att subtrahera start tiden för varje process från den aktuella tiden.

```powershell
Get-Process notepad |
  Format-Table ProcessName, @{Label="TotalRunningTime"; Expression={(Get-Date) - $_.StartTime}}
```

```Output
ProcessName TotalRunningTime
----------- ----------------
notepad     03:20:00.2751767
notepad     00:00:16.7710520
```

`Get-Process` hämtar alla **anteckningar** från den lokala datorn och skickar dem nedåt i pipelinen. `Format-Table` visar en tabell med två kolumner: **processname** , en `Get-Process` egenskap och **TotalRunningTime** , en beräknad egenskap.

Egenskapen **TotalRunningTime** anges av en hash-tabell med två nycklar, **etikett** och **uttryck**. **Etikett** nyckeln anger egenskaps namnet. **Uttrycks** nyckeln anger beräkningen. Uttrycket hämtar egenskapen **StartTime** för varje process objekt och subtraherar den från resultatet av ett `Get-Date` kommando, som hämtar aktuellt datum och aktuell tid.

### Exempel 7: formatera anteckningar-processer

I det här exemplet används för `Get-CimInstance` att hämta körnings tiden för alla **anteckningar** -processer på den lokala datorn. Du kan använda `Get-CimInstance` med parametern **computername** för att hämta information från fjärrdatorer.

```powershell
$Processes = Get-CimInstance -Class win32_process -Filter "name='notepad.exe'"
$Processes | Format-Table ProcessName, @{ Label = "Total Running Time"; Expression={(Get-Date) - $_.CreationDate}}
```

```Output
ProcessName Total Running Time
----------- ------------------
notepad.exe 03:39:39.6260693
notepad.exe 00:19:56.1376922
```

`Get-CimInstance` hämtar instanser av WMI- **Win32_Process** -klassen som beskriver alla de lokala dator processerna som heter **notepad.exe**. Process objekt lagras i `$Processes` variabeln.

Process objekt i `$Processes` variabeln skickas ned till pipelinen till `Format-Table` , som visar egenskapen **processname** och en ny beräknad egenskap, **sammanlagd kör tid**.

Kommandot tilldelar namnet på den nya beräknade egenskapen, den **totala körnings tiden** , till **etikett** nyckeln. **Uttrycks** nyckelns skript block beräknar hur lång tid processen har körts genom att subtrahera processernas skapande datum från det aktuella datumet. `Get-Date`Cmdleten hämtar det aktuella datumet. Skapande datumet subtraheras från det aktuella datumet. Resultatet är värdet av den **totala kör tiden**.

### Exempel 8: fel sökning av format fel

I följande exempel visas resultatet av att lägga till **DisplayError** -eller **ShowError** -parametrarna med ett uttryck.

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -DisplayError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday #ERR
```

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -ShowError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday

InvalidArgument: Failed to evaluate expression " $_ / $null ".
```

## PARAMETRAR

### -AutoSize

Anger att cmdleten justerar kolumn storleken och antalet kolumner baserat på data bredden. Som standard bestäms kolumn storleken och antalet av vyn.

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

### – DisplayError

Anger att cmdleten visar fel på kommando raden. Den här parametern kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-Table` kommando och behöver felsöka uttrycken.

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

### – Expandera

Anger formatet för samlings objekt och objekt i samlingen. Den här parametern är utformad för att formatera objekt som har stöd för [ICollection](/dotnet/api/system.collections.icollection) -gränssnittet ([system. Collection](/dotnet/api/system.collections)). Standardvärdet är **EnumOnly**.
De acceptabla värdena för den här parametern är följande:

- **EnumOnly** : visar egenskaperna för objekten i samlingen.
- **CoreOnly** : visar egenskaperna för objektet samling.
- **Båda** : visar egenskaperna för Collection-objektet och egenskaperna för objekt i samlingen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Anger att cmdleten dirigerar cmdleten för att visa all fel information. Används med parametern **DisplayError** eller **ShowError** . Som standard visas endast en del fel information när ett fel objekt skrivs till fel-eller visnings strömmar.

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

### – GroupBy

Anger sorterade utdata i separata tabeller baserat på ett egenskaps värde. Du kan till exempel använda **groupby** för att visa en lista över tjänster i separata tabeller baserat på deras status.

Ange ett uttryck eller en egenskap. Parametern **groupby** förväntar sig att objekten sorteras.
Använd `Sort-Object` cmdleten innan `Format-Table` du använder för att gruppera objekten.

Värdet för **groupby** -parametern kan vara en ny beräknad egenskap. Den beräknade egenskapen kan vara ett skript block eller en hash-tabell. Giltiga nyckel/värde-par är:

- Namn (eller etikett)- `<string>`
- Uttryck- `<string>` eller `<script block>`
- FormatString `<string>`

Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HideTableHeaders

Utelämnar kolumn rubrikerna från tabellen.

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

### – InputObject

Anger de objekt som ska formateras. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

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

### – Egenskap

Anger objekt egenskaperna som visas i visningen och i vilken ordning de visas. Ange ett eller flera egenskaps namn, avgränsade med kommatecken eller Använd en hash-tabell för att visa en beräknad egenskap. Jokertecken är tillåtna.

Om du utelämnar den här parametern beror egenskaperna som visas i vyn på det första objektets egenskaper. Om det första objektet till exempel har **egenskapen** in och **PropertyB** men efterföljande objekt har **egenskapen** in, **PropertyB** och **PropertyC** , visas bara rubrikerna **propertya** och **PropertyB** .

**Egenskaps** parametern är valfri. Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.

Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap. Den beräknade egenskapen kan vara ett skript block eller en hash-tabell. Giltiga nyckel/värde-par är:

- Namn (eller etikett) `<string>`
- Uttryck- `<string>` eller `<script block>`
- FormatString `<string>`
- Width- `<int32>` -måste vara större än `0`
- Justering-värdet kan vara `Left` , `Center` eller `Right`

Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -RepeatHeader

Upprepar visar rubriken för en tabell när varje skärm är full. Den upprepade rubriken är användbar när utdata är skickas till en pager som `less` eller `more` eller sid indelning med en skärm läsare.

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

### – ShowError

Den här parametern skickar fel via pipelinen. Den här parametern kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-Table` kommando och behöver felsöka uttrycken.

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

### – Visa

Från och med PowerShell 6 definieras standardvyerna i PowerShell- `C#` källkod. `*.format.ps1xml`Filerna från powershell 5,1 och tidigare versioner finns inte i PowerShell 6 och senare versioner.

Med parametern **Visa** kan du ange ett alternativt format eller en anpassad vy för tabellen. Du kan använda standard-PowerShell-vyer eller skapa anpassade vyer. Mer information om hur du skapar en anpassad vy finns i [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).

De alternativa och anpassade vyerna för parametern **View** måste använda tabell formatet, annars `Format-Table` Miss lyckas. Om den alternativa vyn är en lista använder du `Format-List` cmdleten. Om den alternativa vyn inte är en lista eller en tabell använder du `Format-Custom` cmdleten.

Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.

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

### – Radbryt

Visar text som överskrider kolumn bredden på nästa rad. Som standard är text som överskrider kolumn bredden trunkerad.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka valfritt objekt nedåt i pipeline till `Format-Table` .

## UTDATA

### Microsoft. PowerShell. commands. Internal. format

`Format-Table` Returnerar format objekt som representerar tabellen.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[Exportera – FormatData](Export-FormatData.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Wide](Format-Wide.md)

[Get-FormatData](Get-FormatData.md)

[Hämta medlem](Get-Member.md)

[Get-CimInstance](../CimCmdlets/Get-CimInstance.md)

[Uppdatera – FormatData](Update-FormatData.md)
