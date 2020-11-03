---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: 551646fba0523a03954295eb42380e7245ec319b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267105"
---
# Export-Csv

## SAMMANFATTNING
Konverterar objekt till en serie med kommaavgränsade värde strängar (CSV) och sparar strängarna i en fil.

## SYNTAX

### Avgränsare (standard)

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### UseCulture

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Export-CSV`Cmdleten skapar en CSV-fil med de objekt som du skickar. Varje objekt är en rad som innehåller en kommaavgränsad lista med objektets egenskaps värden. Du kan använda `Export-CSV` cmdleten för att skapa kalkyl blad och dela data med program som accepterar CSV-filer som indata.

Formatera inte objekt innan du skickar dem till- `Export-CSV` cmdleten. Om `Export-CSV` tar emot formaterade objekt, innehåller CSV-filen format egenskaper i stället för objekt egenskaperna. Om du bara vill exportera markerade egenskaper för ett objekt använder du `Select-Object` cmdleten.

## EXEMPEL

### Exempel 1: Exportera process egenskaper till en CSV-fil

I det här exemplet väljs **bearbeta** objekt med vissa egenskaper, och objekten exporteras till en CSV-fil.

```powershell
Get-Process -Name WmiPrvSE | Select-Object -Property BasePriority,Id,SessionId,WorkingSet |
  Export-Csv -Path .\WmiData.csv -NoTypeInformation
Import-Csv -Path .\WmiData.csv
```

```Output
BasePriority Id    SessionId WorkingSet
------------ --    --------- ----------
8            976   0         20267008
8            2292  0         36786176
8            3816  0         30351360
8            8604  0         15011840
8            10008 0         8830976
8            11764 0         14237696
8            54632 0         9502720
```

`Get-Process`Cmdlet: en hämtar **process** objekt. Parametern **Name** filtrerar utdata så att endast process objekt för Wmiprvse tas med. Process objekt skickas ned pipelinen till `Select-Object` cmdleten. `Select-Object` använder **egenskaps** parametern för att välja en delmängd av process objekt egenskaperna. Process objekt skickas ned pipelinen till `Export-Csv` cmdleten. `Export-Csv` konverterar process objekt till en serie med CSV-strängar. Parametern **Path** anger att WmiData.csv-filen sparas i den aktuella katalogen. Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6. `Import-Csv`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.

### Exempel 2: exportera processer till en kommaavgränsad fil

Det här exemplet **hämtar objekt och exporterar objekten till** en CSV-fil.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

`Get-Process`Cmdleten **bearbetar** objekt. Process objekt skickas ned pipelinen till `Export-Csv` cmdleten. `Export-Csv` konverterar process objekt till en serie med CSV-strängar.
Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen. Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6. `Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.

### Exempel 3: exportera processer till en semikolonavgränsad fil

Det här exemplet **hämtar objekt och exporterar objekten till** en fil med semikolon avgränsare.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

`Get-Process`Cmdleten **bearbetar** objekt. Process objekt skickas ned pipelinen till `Export-Csv` cmdleten. `Export-Csv` konverterar process objekt till en serie med CSV-strängar.
Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen. Parametern **delimiter** anger ett semikolon för att avgränsa sträng värden. Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6. `Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.

### Exempel 4: exportera processer med nuvarande kulturs List avgränsare

Det här exemplet **hämtar objekt och exporterar objekten till** en fil. Avgränsaren är den aktuella kulturen List avgränsare.

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

`Get-Culture`Cmdleten använder de kapslade egenskaperna **Textinfo** och **ListSeparator** och visar den aktuella kulturen som är standard för List avgränsare. `Get-Process`Cmdleten **bearbetar** objekt.
Process objekt skickas ned pipelinen till `Export-Csv` cmdleten. `Export-Csv` konverterar process objekt till en serie med CSV-strängar. Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen. Parametern **UseCulture** använder aktuell kulturs standard List avgränsare som avgränsare. Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6. `Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.

### Exempel 5: exportera processer med typ information

Det här exemplet förklarar hur du inkluderar **#TYPE** rubrik information i en CSV-fil. **#TYPEs** huvudet är standardvärdet i tidigare versioner än PowerShell 6,0.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -IncludeTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

`Get-Process`Cmdleten **bearbetar** objekt. Process objekt skickas ned pipelinen till `Export-Csv` cmdleten. `Export-Csv` konverterar process objekt till en serie med CSV-strängar.
Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen. **IncludeTypeInformation** innehåller **#TYPE** informations rubriken i CSV-utdata. `Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.

### Exempel 6: exportera och lägga till objekt i en CSV-fil

Det här exemplet beskriver hur du exporterar objekt till en CSV-fil och använder parametern **APPEND** för att lägga till objekt i en befintlig fil.

```powershell
$AppService = (Get-Service -DisplayName *Application* | Select-Object -Property DisplayName, Status)
$AppService | Export-Csv -Path .\Services.Csv -NoTypeInformation
Get-Content -Path .\Services.Csv
$WinService = (Get-Service -DisplayName *Windows* | Select-Object -Property DisplayName, Status)
$WinService | Export-Csv -Path ./Services.csv -NoTypeInformation -Append
Get-Content -Path .\Services.Csv
```

```Output
"DisplayName","Status"
"Application Layer Gateway Service","Stopped"
"Application Identity","Running"
"Windows Audio Endpoint Builder","Running"
"Windows Audio","Running"
"Windows Event Log","Running"
```

`Get-Service`Cmdlet: en hämtar tjänst objekt. Parametern **DisplayName** returnerar tjänster som innehåller Word-programmet. Tjänst objekt skickas ned pipelinen till `Select-Object` cmdleten. `Select-Object` använder **egenskaps** parametern för att ange egenskaperna **DisplayName** och **status** . `$AppService`Variabeln lagrar objekten.

`$AppService`Objekten skickas ned pipelinen till `Export-Csv` cmdleten. `Export-Csv` konverterar tjänst objekt till en serie CSV-strängar. Parametern **Path** anger att Services.csv-filen sparas i den aktuella katalogen. Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6. `Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.

`Get-Service` `Select-Object` Cmdletarna och upprepas för tjänster som innehåller ordet Windows. `$WinService`Variabeln lagrar tjänst objekt. `Export-Csv`Cmdleten använder parametern **APPEND** för att ange att `$WinService` objekten läggs till i den befintliga Services.csvs filen. `Get-Content`Cmdleten upprepas för att visa den uppdaterade filen som innehåller de data som lagts till.

### Exempel 7: format-cmdleten i en pipeline skapar oväntade resultat

Det här exemplet visar varför det är viktigt att inte använda en format-cmdlet i en pipeline. Felsök pipeline-syntaxen när oväntade utdata tas emot.

```powershell
Get-Date | Select-Object -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\DateTime.csv -NoTypeInformation
Get-Content -Path .\DateTime.csv
```

```Output
"DateTime","Day","DayOfWeek","DayOfYear"
"Wednesday, January 2, 2019 14:59:34","2","Wednesday","2"
```

```powershell
Get-Date | Format-Table -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\FTDateTime.csv -NoTypeInformation
Get-Content -Path .\FTDateTime.csv
```

```Output
"ClassId2e4f51ef21dd47e99d3c952918aff9cd","pageHeaderEntry","pageFooterEntry","autosizeInfo", ...
"033ecb2bc07a4d43b5ef94ed5a35d280",,,,"Microsoft.PowerShell.Commands.Internal.Format. ...
"9e210fe47d09416682b841769c78b8a3",,,,,
"27c87ef9bbda4f709f6b4002fa4af63c",,,,,
"4ec4f0187cb04f4cb6973460dfe252df",,,,,
"cf522b78d86c486691226b40aa69e95c",,,,,
```

`Get-Date`Cmdlet: en hämtar **datetime** -objektet. Objektet skickas ned pipelinen till `Select-Object` cmdleten. `Select-Object` använder **egenskaps** parametern för att välja en delmängd av objekt egenskaperna. Objektet skickas ned pipelinen till `Export-Csv` cmdleten. `Export-Csv` konverterar objektet till ett CSV-format. Parametern **Path** anger att DateTime.csv-filen sparas i den aktuella katalogen. Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6. `Get-Content`Cmdleten använder parametern **Path** för att Visa CSV-filen som finns i den aktuella katalogen.

När `Format-Table` cmdleten används i pipelinen för att välja egenskaper tas oväntade resultat emot. `Format-Table` skickar tabell formats objekt ned pipelinen till `Export-Csv` cmdleten i stället för **datetime** -objektet. `Export-Csv` konverterar tabell formats objekt till en serie CSV-strängar. `Get-Content`Cmdleten visar CSV-filen som innehåller tabell formats objekt.

### Exempel 8: använda Force-parametern för att skriva över skrivskyddade filer

Det här exemplet skapar en tom skrivskyddad fil och använder **Force** -parametern för att uppdatera filen.

```powershell
New-Item -Path .\ReadOnly.csv -ItemType File
Set-ItemProperty -Path .\ReadOnly.csv -Name IsReadOnly -Value $true
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
```

```Output
Export-Csv : Access to the path 'C:\ReadOnly.csv' is denied.
At line:1 char:15
+ Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
+               ~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (:) [Export-Csv], UnauthorizedAccessException
+ FullyQualifiedErrorId : FileOpenFailure,Microsoft.PowerShell.Commands.ExportCsvCommand
```

```powershell
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation -Force
Get-Content -Path .\ReadOnly.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

`New-Item`Cmdleten använder parametrarna **Path** och **ItemType** för att skapa ReadOnly.csv-filen i den aktuella katalogen. `Set-ItemProperty`Cmdleten använder **namn** -och **värde** parametrarna för att ändra filens **IsReadOnly** -egenskap till true. `Get-Process`Cmdleten **bearbetar** objekt. Process objekt skickas ned pipelinen till `Export-Csv` cmdleten. `Export-Csv` konverterar process objekt till en serie med CSV-strängar. Parametern **Path** anger att ReadOnly.csv-filen sparas i den aktuella katalogen. Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6. Utdata visar att filen inte har skrivits eftersom åtkomst nekas.

Parametern **Force** läggs till i `Export-Csv` cmdleten för att tvinga exporten att skriva till filen. `Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.

### Exempel 9: använda Force-parametern med append

I det här exemplet visas hur du använder **Force** -och **APPEND** -parametrarna. När dessa parametrar kombineras, kan avvikande objekt egenskaper skrivas till en CSV-fil.

```powershell
$Content = [PSCustomObject]@{Name = 'PowerShell Core'; Version = '6.0'}
$Content | Export-Csv -Path .\ParmFile.csv -NoTypeInformation
$AdditionalContent = [PSCustomObject]@{Name = 'Windows PowerShell'; Edition = 'Desktop'}
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
```

```Output
Export-Csv : Cannot append CSV content to the following file: ParmFile.csv.
The appended object does not have a property that corresponds to the following column:
Version. To continue with mismatched properties, add the -Force parameter, and then retry
 the command.
At line:1 char:22
+ $AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (Version:String) [Export-Csv], InvalidOperationException
+ FullyQualifiedErrorId : CannotAppendCsvWithMismatchedPropertyNames,Microsoft.PowerShell. ...
```

```powershell
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append -Force
Import-Csv -Path .\ParmFile.csv
```

```Output
Name               Version
----               -------
PowerShell Core    6.0
Windows PowerShell
```

Ett uttryck skapar **PSCustomObject** med **namn** och **versions** egenskaper. Värdena lagras i `$Content` variabeln. `$Content`Variabeln skickas ned pipelinen till `Export-Csv` cmdleten. `Export-Csv` använder parametern **Path** och sparar ParmFile.csv-filen i den aktuella katalogen. Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.

Ett annat uttryck skapar en **PSCustomObject** med egenskaperna **namn** och **utgåva** . Värdena lagras i `$AdditionalContent` variabeln. `$AdditionalContent`Variabeln skickas ned pipelinen till `Export-Csv` cmdleten. Parametern **APPEND** används för att lägga till data i filen. Det går inte att lägga till eftersom det finns ett matchnings fel för egenskaps namn mellan **version** och **utgåva**.

`Export-Csv`Parametern cmdlet **Force** används för att tvinga exporten att skriva till filen. Egenskapen **Edition** ignoreras. `Import-Csv`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.

## PARAMETRAR

### -Lägg till

Använd den här parametern för att `Export-CSV` lägga till CSV-utdata i slutet av den angivna filen. Utan den här parametern `Export-CSV` ersätter filens innehåll utan varning.

Den här parametern introducerades i Windows PowerShell 3,0.

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

### -Avgränsare

Anger en avgränsare för att avgränsa egenskaps värden. Standardvärdet är ett kommatecken ( `,` ). Ange ett tecken, till exempel ett kolon ( `:` ). Om du vill ange ett semikolon ( `;` ), omger du det med citat tecken.

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Anger kodningen för den exporterade CSV-filen. Standardvärdet är `utf8NoBOM`.

De acceptabla värdena för den här parametern är följande:

- `ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).
- `bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.
- `oem`: Använder standard kodning för MS-DOS-och-konsol program.
- `unicode`: Kodar i UTF-16-format med lite-endian-dataordning.
- `utf7`: Kodar i UTF-7-format.
- `utf8`: Kodar i UTF-8-format.
- `utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)
- `utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)
- `utf32`: Kodar i UTF-32-format.

Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ). Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Med den här parametern kan `Export-Csv` du skriva över filer med **skrivskyddat** attribut.

När **tvinga** -och **tilläggs** parametrar kombineras, kan objekt som innehåller felmatchade egenskaper SKRIVAs till en CSV-fil. Endast egenskaper som matchar skrivs till filen. De egenskaper som matchar ignoreras.

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

### -IncludeTypeInformation

När den här parametern används, innehåller den första raden i CSV-utdata **#TYPE** följt av objekt typens fullständigt kvalificerade namn. Till exempel **#TYPE system. Diagnostics. process**.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger de objekt som ska exporteras som CSV-strängar. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten. Du kan också skicka pipe-objekt till `Export-CSV` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Anger sökvägen till CSV-utdatafilen. Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken använder du enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

Använd den här parametern så att `Export-CSV` ingen befintlig fil skrivs över. Om filen finns på den angivna sökvägen `Export-CSV` skrivs filen som standard utan varning.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoTypeInformation

Tar bort **#TYPE** informations huvud från utdata. Den här parametern blev standard i PowerShell 6,0 och ingår för bakåtkompatibilitet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

En obligatorisk parameter som anger den plats där du vill spara CSV-utdatafilen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

Använder list avgränsaren för den aktuella kulturen som objekt avgränsare. Använd följande kommando för att hitta List avgränsaren för en kultur: `(Get-Culture).TextInfo.ListSeparator` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
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

Förhindrar att cmdleten bearbetas eller gör ändringar. Utdata visar vad som händer om cmdleten kördes.

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

Du kan skicka ett objekt med ett ETS-kort (Extended Type System) till `Export-CSV` .

## UTDATA

### System. String

CSV-listan skickas till den fil som anges i parametern Path.

## ANTECKNINGAR

`Export-CSV`Cmdleten konverterar de objekt som du skickar till en serie med CSV-strängar och sparar dem i den angivna text filen. Du kan använda `Export-CSV -IncludeTypeInformation` för att spara objekt i en CSV-fil och sedan använda `Import-Csv` cmdleten för att skapa objekt från texten i CSV-filen.

I CSV-filen representeras varje objekt av en kommaavgränsad lista med objektets egenskaps värden. Egenskaps värden konverteras till strängar med hjälp av metoden **toString ()** . Strängarna representeras av egenskaps värde namnet. `Export-CSV -IncludeTypeInformation` exporterar inte objektets metoder.

CSV-strängarna matas ut enligt följande:

- Om **IncludeTypeInformation** används, innehåller den första strängen **#TYPE** informations huvud följt av objekt typens fullständigt kvalificerade namn.
  Till exempel **#TYPE system. Diagnostics. process**.
- Om **IncludeTypeInformation** inte används, innehåller den första strängen kolumn rubrikerna. Rubrikerna innehåller det första objektets egenskaps namn som en kommaavgränsad lista.
- De återstående strängarna innehåller kommaavgränsade listor över varje objekts egenskaps värden.

Från och med PowerShell 6,0 är standard beteendet för `Export-CSV` att inte inkludera **#TYPE** information i CSV-och **NoTypeInformation** är underförstådd. **IncludeTypeInformation** kan användas för att inkludera **#TYPE** information och emulera standard beteendet för `Export-CSV` före PowerShell 6,0.

När du skickar flera objekt till `Export-CSV` `Export-CSV` ordnas filen baserat på egenskaperna för det första objektet som du skickar. Om de återstående objekten inte har en av de angivna egenskaperna, är egenskap svärdet för objektet null, som representeras av två kommatecken i följd. Om de återstående objekten har ytterligare egenskaper inkluderas inte dessa egenskaps värden i filen.

Du kan använda `Import-Csv` cmdleten för att återskapa objekt från CSV-strängarna i filerna. De resulterande objekten är CSV-versioner av de ursprungliga objekten som består av sträng representationer av egenskapsvärdena och inga metoder.

`ConvertTo-Csv` `ConvertFrom-Csv` Cmdletarna och konverterar objekt till CSV-strängar och från CSV-strängar. `Export-CSV` är detsamma som `ConvertTo-CSV` , förutom att det sparar CSV-strängarna i en fil.

## RELATERADE LÄNKAR

[ConvertFrom-CSV](ConvertFrom-Csv.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Format-Table](Format-Table.md)

[Import-Csv](Import-Csv.md)

[Select-Object](Select-Object.md)
