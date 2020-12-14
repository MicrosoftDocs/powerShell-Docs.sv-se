---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-csv?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Csv
ms.openlocfilehash: 819591c6004d6185958376ac8f84c42b9bfbf460
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708623"
---
# Import-Csv

## SAMMANFATTNING
Skapar tabeller som liknar anpassade objekt från objekten i en fil med kommaavgränsade värden (CSV).

## SYNTAX

### DelimiterPath (standard)

```
Import-Csv [[-Delimiter] <Char>] [-Path] <String[]> [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### DelimiterLiteralPath

```
Import-Csv [[-Delimiter] <Char>] -LiteralPath <String[]> [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### CulturePath

```
Import-Csv [-Path] <String[]> -UseCulture [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### CultureLiteralPath

```
Import-Csv -LiteralPath <String[]> -UseCulture [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en `Import-Csv` skapar tabeller som liknar anpassade objekt från objekten i CSV-filer. Varje kolumn i CSV-filen blir en egenskap för det anpassade objektet och objekten i rader blir egenskaps värden. `Import-Csv` fungerar på alla CSV-filer, inklusive filer som genereras av `Export-Csv` cmdleten.

Du kan använda parametrarna för `Import-Csv` cmdleten för att ange kolumn rubrik raden och objekt avgränsaren, eller direkt `Import-Csv` för att använda List avgränsaren för den aktuella kulturen som objekt avgränsare.

Du kan också använda `ConvertTo-Csv` `ConvertFrom-Csv` cmdletarna och för att konvertera objekt till CSV-strängar (och tillbaka). Dessa cmdletar är desamma som `Export-CSV` -och `Import-Csv` -cmdletarna, förutom att de inte behandlar filer.

Om en rubrik rad post i en CSV-fil innehåller ett tomt värde eller null-värde, infogar PowerShell ett standard rubrik rads namn och visar ett varnings meddelande.

Från och med PowerShell 6,0 `Import-Csv` stöder nu utökat logg fils format för W3C.

## EXEMPEL

### Exempel 1: importera process objekt

Det här exemplet visar hur du exporterar och sedan importerar en CSV-fil med process objekt.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
$P = Import-Csv -Path .\Processes.csv
$P | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name                       MemberType   Definition
----                       ----------   ----------
Equals                     Method       bool Equals(System.Object obj)
GetHashCode                Method       int GetHashCode()
GetType                    Method       type GetType()
ToString                   Method       string ToString()
BasePriority               NoteProperty string BasePriority=8
Company                    NoteProperty string Company=Microsoft Corporation
...
```

```powershell
$P | Format-Table
```

```Output
Name                   SI Handles VM            WS        PM        NPM    Path
----                   -- ------- --            --        --        ---    ----
ApplicationFrameHost   4  407     2199293489152 15884288  15151104  23792  C:\WINDOWS\system32\ApplicationFrameHost.exe
...
wininit                0  157     2199112204288 4591616   1630208   10376
winlogon               4  233     2199125549056 7659520   2826240   10992  C:\WINDOWS\System32\WinLogon.exe
WinStore.App           4  846     873435136     33652736  26607616  55432  C:\Program Files\WindowsApps\Microsoft.WindowsStore_11712.1001.13.0_x64__8weky...
WmiPrvSE               0  201     2199100219392 8830976   3297280   10632  C:\WINDOWS\system32\wbem\wmiprvse.exe
WmiPrvSE               0  407     2199157727232 18509824  12922880  16624  C:\WINDOWS\system32\wbem\wmiprvse.exe
WUDFHost               0  834     2199310204928 51945472  87441408  24984  C:\Windows\System32\WUDFHost.exe
```

`Get-Process`Cmdleten skickar process objekt nedåt i pipeline till `Export-Csv` . `Export-Csv`Cmdleten konverterar process objekt till CSV-strängar och sparar strängarna i Processes.csvs filen. `Import-Csv`Cmdleten importerar CSV-strängarna från Processes.csv-filen.
Strängarna sparas i `$P` variabeln. `$P`Variabeln skickas ned pipelinen till den `Get-Member` cmdlet som visar egenskaperna för de importerade CSV-strängarna. `$P`Variabeln skickas ned pipelinen till `Format-Table` cmdleten och visar objekten.

### Exempel 2: Ange avgränsare

Det här exemplet visar hur du använder parametern **delimiter** för `Import-Csv` cmdleten.

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter :
$P = Import-Csv -Path .\Processes.csv -Delimiter :
$P | Format-Table
```

`Get-Process`Cmdleten skickar process objekt nedåt i pipeline till `Export-Csv` . `Export-Csv`Cmdleten konverterar process objekt till CSV-strängar och sparar strängarna i Processes.csvs filen.
Parametern **delimiter** används för att ange en kolon avgränsare. `Import-Csv`Cmdleten importerar CSV-strängarna från Processes.csv-filen. Strängarna sparas i `$P` variabeln. Till- `$P` variabeln skickas ned pipelinen till `Format-Table` cmdleten.

### Exempel 3: Ange den aktuella kulturen för avgränsaren

Det här exemplet visar hur du använder `Import-Csv` cmdleten med parametern **UseCulture** .

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture
Import-Csv -Path .\Processes.csv -UseCulture
```

`Get-Culture`Cmdleten använder de kapslade egenskaperna **Textinfo** och **ListSeparator** för att hämta den aktuella kulturen som är standard för List avgränsare. `Get-Process`Cmdleten skickar process objekt nedåt i pipeline till `Export-Csv` . `Export-Csv`Cmdleten konverterar process objekt till CSV-strängar och sparar strängarna i Processes.csvs filen. Parametern **UseCulture** använder den aktuella kulturen som standard List avgränsare. `Import-Csv`Cmdleten importerar CSV-strängarna från Processes.csv-filen.

### Exempel 4: ändra egenskaps namn i ett importerat objekt

Det här exemplet visar hur du använder parametern **header** i `Import-Csv` för att ändra namn på egenskaper i det resulterande importerade objektet.

```powershell
Start-Job -ScriptBlock { Get-Process } | Export-Csv -Path .\Jobs.csv -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished', 'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error', 'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from file
$A = Get-Content -Path .\Jobs.csv
$A = $A[1..($A.Count - 1)]
$A | Out-File -FilePath .\Jobs.csv
$J = Import-Csv -Path .\Jobs.csv -Header $Header
$J
```

```Output
State         : Running
MoreData      : True
StatusMessage :
Location      : localhost
Command       : Get-Process
StateInfo     : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : a259eb63-6824-4b97-a033-305108ae1c2e
Id            : 1
Name          : Job1
ChildJobs     : System.Collections.Generic.List`1[System.Management.Automation.Job]
BeginTime     : 12/20/2018 18:59:57
EndTime       :
JobType       : BackgroundJob
Output        : System.Management.Automation.PSDataCollection`1[System.Management.Automation.PSObject]
Error         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ErrorRecord]
Progress      : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ProgressRecord]
Verbose       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.VerboseRecord]
Debug         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.DebugRecord]
Warning       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.WarningRecord]
Information   : System.Management.Automation.PSDataCollection`1[System.Management.Automation.InformationRecord]
```

`Start-Job`Cmdleten startar ett bakgrunds jobb som kör `Get-Process` . Ett jobb objekt skickas ned pipelinen till `Export-Csv` cmdleten och konverteras till en CSV-sträng. Parametern **NoTypeInformation** tar bort typ informations huvudet från CSV-utdata och är valfritt i PowerShell Core.
`$Header`Variabeln innehåller en anpassad rubrik som ersätter följande standardvärden: **HasMoreData**, **JobStateInfo**, **PSBeginTime**, **PSEndTime** och **PSJobTypeName**. `$A`Variabeln använder `Get-Content` cmdleten för att hämta CSV-strängen från Jobs.csv-filen. `$A`Variabeln används för att ta bort standard huvudet från filen. `Out-File`Cmdleten sparar den nya versionen av Jobs.csv-filen i `$A` variabeln. `Import-Csv`Cmdleten importerar Jobs.csv-filen och använder parametern **header** för att tillämpa `$Header` variabeln. `$J`Variabeln innehåller den importerade **PSCustomObject** och visar objektet i PowerShell-konsolen.

### Exempel 5: skapa ett anpassat objekt med en CSV-fil

Det här exemplet visar hur du skapar ett anpassat objekt i PowerShell med hjälp av en CSV-fil.

```powershell
Get-Content -Path .\Links.csv
```

```Output
113207,about_Aliases
113208,about_Arithmetic_Operators
113209,about_Arrays
113210,about_Assignment_Operators
113212,about_Automatic_Variables
113213,about_Break
113214,about_Command_Precedence
113215,about_Command_Syntax
144309,about_Comment_Based_Help
113216,about_CommonParameters
113217,about_Comparison_Operators
113218,about_Continue
113219,about_Core_Commands
113220,about_Data_Section
```

```powershell
$A = Import-Csv -Path .\Links.csv -Header 'LinkID', 'TopicTitle'
$A | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
LinkID      NoteProperty string LinkID=113207
TopicTitle  NoteProperty string TopicTitle=about_Aliases
```

```powershell
$A | Where-Object -Property TopicTitle -Like '*alias*'
```

```Output
LinkID TopicTitle
------ ----------
113207 about_Aliases
```

Använd värdena som visas i utdata om du vill skapa en Links.csv-fil `Get-Content` .

`Get-Content`Cmdleten visar Links.csv-filen. `Import-Csv`Cmdleten importerar Links.csv-filen. Parametern **header** anger egenskaps namnen **LinkId** och **TopicTitle**. Objekten lagras i `$A` variabeln. `Get-Member`Cmdleten visar egenskaps namnen från **rubriken** -parametern. `Where-Object`Cmdleten väljer objekt med egenskapen **TopicTitle** som innehåller **alias**.

### Exempel 6: importera en CSV-fil som saknar ett värde

Det här exemplet visar hur `Import-Csv` cmdleten i PowerShell reagerar när rubrik raden i en CSV-fil innehåller ett null-värde eller ett tomt värde. `Import-Csv` ersätter ett standard namn för den saknade rubrik raden som blir egenskaps namnet för det objekt som `Import-Csv` returneras.

```powershell
Get-Content -Path .\Projects.csv
```

```Output
ProjectID,ProjectName,,Completed
13,Inventory,Redmond,True
440,,FarEast,True
469,Marketing,Europe,False
```

```powershell
Import-Csv -Path .\Projects.csv
```

```Output
WARNING: One or more headers were not specified. Default names starting with "H" have been used in place of any missing headers.

ProjectID ProjectName H1      Completed
--------- ----------- --      ---------
13        Inventory   Redmond True
440                   FarEast True
469       Marketing   Europe  False
```

```powershell
(Import-Csv -Path .\Projects.csv).H1
```

```Output
WARNING: One or more headers were not specified. Default names starting with "H" have been used in place of any missing headers.
Redmond
FarEast
Europe
```

Använd värdena som visas i exemplets utdata om du vill skapa en Projects.csv-fil `Get-Content` .

`Get-Content`Cmdleten visar Projects.csv-filen. Rubrik raden saknar ett värde mellan **ProjectName** och **har slutförts**. `Import-Csv`Cmdleten importerar Projects.csv-filen och visar ett varnings meddelande eftersom **H1** är ett standard huvud namn. `(Import-Csv -Path
.\Projects.csv).H1`Kommandot hämtar värdena för **H1** -egenskapen och visar en varning.

## PARAMETRAR

### -Avgränsare

Anger den avgränsare som separerar egenskapsvärdena i CSV-filen.
Standardvärdet är komma (,).

Ange ett tecken, till exempel ett kolon (:).
Ange ett semikolon (;) omge det med enkla citat tecken.

Om du anger ett annat tecken än den faktiska sträng avgränsaren i filen, `Import-Csv` kan inte skapa objekten från CSV-strängarna och returnera CSV-strängarna.

```yaml
Type: System.Char
Parameter Sets: DelimiterPath, DelimiterLiteralPath
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Anger kodningen för den importerade CSV-filen. Standardvärdet är `utf8NoBOM`.

De acceptabla värdena för den här parametern är följande:

- `ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).
- `bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.
- `bigendianutf32`: Kodar i UTF-32-format med big-endian-dataordningen.
- `oem`: Använder standard kodning för MS-DOS-och-konsol program.
- `unicode`: Kodar i UTF-16-format med lite-endian-dataordning.
- `utf7`: Kodar i UTF-7-format.
- `utf8`: Kodar i UTF-8-format.
- `utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)
- `utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)
- `utf32`: Kodar i UTF-32-format.

Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ). Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).

> [!NOTE]
> **UTF-7** _ rekommenderas inte längre att använda. I PowerShell 7,1 skrivs en varning om du anger `utf7` för parametern _ *encoding**.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### – Sidhuvud

Anger en alternativ kolumn rubrik rad för den importerade filen. Kolumn rubriken bestämmer de objekts egenskaps namn som skapats av `Import-Csv` .

Ange kolumn rubriker som en kommaavgränsad lista. Ange inte rubrik strängen inom citat tecken. Omge varje kolumn rubrik med enkla citat tecken.

Om du anger färre kolumn rubriker än det finns data kolumner, ignoreras de återstående data kolumnerna. Om du anger fler kolumn rubriker än det finns data kolumner skapas de ytterligare kolumn rubrikerna med tomma data kolumner.

När du använder parametern **header** tar du bort den ursprungliga rubrik raden från CSV-filen. Annars `Import-Csv` skapar ett extra objekt från objekten i rubrik raden.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Anger sökvägen till den CSV-fil som ska importeras. Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: DelimiterLiteralPath, CultureLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Anger sökvägen till den CSV-fil som ska importeras.
Du kan också skicka en sökväg till `Import-Csv` .

```yaml
Type: System.String[]
Parameter Sets: DelimiterPath, CulturePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseCulture

Använder list avgränsaren för den aktuella kulturen som objekt avgränsare. Använd följande kommando för att hitta List avgränsaren för en kultur: `(Get-Culture).TextInfo.ListSeparator` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CulturePath, CultureLiteralPath
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg till `Import-Csv` .

## UTDATA

### Objekt

Denna cmdlet returnerar de objekt som beskrivs av innehållet i CSV-filen.

## ANTECKNINGAR

Eftersom de importerade objekten är CSV-versioner av objekt typen känns de inte igen och formateras inte av de PowerShell-typer som formaterar icke-CSV-versioner av objekt typen.

Resultatet av ett `Import-Csv` kommando är en samling strängar som utgör ett tabell liknande anpassade objekt. Varje rad är en separat sträng, så du kan använda egenskapen **Count** för objektet för att räkna tabell rader. Kolumnerna är egenskaperna för objektet och objekten i raderna är egenskapsvärdena.

Kolumn rubrik raden bestämmer antalet kolumner och kolumn namnen. Kolumn namnen är också namnen på objektets egenskaper. Den första raden tolkas som kolumn rubriker, om du inte använder parametern **header** för att ange kolumn rubriker. Om en rad har fler värden än rubrik raden ignoreras de ytterligare värdena.

Om kolumn rubrik raden saknar ett värde eller innehåller ett värde som är null eller tomt, `Import-Csv` använder **H** följt av ett tal för kolumn rubriken och egenskaps namnet som saknas.

I CSV-filen representeras varje objekt av en kommaavgränsad lista med objektets egenskaps värden. Egenskapsvärdena konverteras till strängar med hjälp av metoden **toString ()** för objektet, så att de representeras av namnet på egenskap svärdet. `Export-Csv` exporterar inte objektets metoder.

`Import-Csv` stöder även utökat logg format för W3C. Rader som börjar med `#` behandlas som kommentarer och ignoreras om inte kommentaren börjar med `#Fields:` och innehåller en avgränsad lista med kolumn namn. I så fall använder cmdleten dessa kolumn namn. Detta är standardformatet för Windows IIS och andra webb server loggar. Mer information finns i [utökat logg fils format](https://www.w3.org/TR/WD-logfile.html).

## RELATERADE LÄNKAR

[ConvertFrom-CSV](ConvertFrom-Csv.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Exportera-CSV](Export-Csv.md)

[Get-Culture](Get-Culture.md)

