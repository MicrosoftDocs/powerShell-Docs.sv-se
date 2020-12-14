---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: ffe7fe7c44258435c7ec9ddd2bab9ebeb9f6c465
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709823"
---
# ConvertTo-Html

## SAMMANFATTNING
Konverterar .NET-objekt till HTML som kan visas i en webbläsare.

## SYNTAX

### Sida (standard)

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [-Meta <Hashtable>] [-Charset <String>] [-Transitional]
 [<CommonParameters>]
```

### Fragment

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`ConvertTo-Html`Cmdleten konverterar .net-objekt till HTML som kan visas i en webbläsare. Du kan använda den här cmdleten för att visa utdata från ett kommando på en webb sida.

Du kan använda parametrarna för `ConvertTo-Html` för att välja objekt egenskaper, för att ange ett tabell-eller List format, för att ange HTML-sidans rubrik, lägga till text före och efter objektet och bara returnera tabellen eller List fragment, i stället för en strikt DTD-sida.

När du skickar flera objekt till `ConvertTo-Html` skapar PowerShell tabellen (eller listan) baserat på egenskaperna för det första objektet som du skickar. Om de återstående objekten inte har en av de angivna egenskaperna, är egenskap svärdet för objektet en tom cell. Om de återstående objekten har ytterligare egenskaper inkluderas inte dessa egenskaps värden i filen.

## EXEMPEL

### Exempel 1: skapa en webb sida för att visa datumet

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

Det här kommandot skapar en HTML-sida som visar egenskaperna för det aktuella datumet. Parametern **InputObject** används för att skicka resultatet av ett `Get-Date` kommando till `ConvertTo-Html` cmdleten.

### Exempel 2: skapa en webb sida för att Visa PowerShell-alias

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

Det här kommandot skapar en HTML-sida som visar PowerShell-alias i den aktuella konsolen.

Kommandot använder `Get-Alias` cmdleten för att hämta alias. Den använder pipeline-operatorn ( `|` ) för att skicka alias till `ConvertTo-Html` cmdleten, vilket skapar HTML-sidan. Kommandot använder också `Out-File` cmdleten för att skicka HTML-koden till `aliases.htm` filen.

### Exempel 3: skapa en webb sida för att Visa PowerShell-händelser

```powershell
`Get-EventLog` -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

Det här kommandot skapar en HTML-sida `pslog.htm` med namnet som visar händelserna i händelse loggen för Windows PowerShell på den lokala datorn.

Den använder `Get-EventLog` cmdleten för att hämta händelserna i Windows PowerShell-loggen och använder sedan pipeline-operatorn ( `|` ) för att skicka händelserna till `ConvertTo-Html` cmdleten. Kommandot använder också `Out-File` cmdleten för att skicka HTML-koden till `pslog.htm` filen.

Kommandot använder också `Out-File` cmdleten för att skicka HTML-koden till `pslog.htm` filen.

### Exempel 4: skapa en webb sida för att visa processer

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

Dessa kommandon skapar och öppnar en HTML-sida som visar namn, sökväg och företag för processerna på den lokala datorn.

Det första kommandot använder `Get-Process` cmdleten för att hämta objekt som representerar de processer som körs på datorn. Kommandot använder pipeline-operatorn ( `|` ) för att skicka process objekt till `ConvertTo-Html` cmdleten.

Kommandot använder **egenskaps** parametern för att välja tre egenskaper för de process objekt som ska tas med i tabellen. Kommandot använder **title** -parametern för att ange en rubrik för HTML-sidan. Kommandot använder också `Out-File` cmdleten för att skicka den resulterande HTML-koden till en fil med namnet Proc.htm.

Det andra kommandot använder `Invoke-Item` cmdleten för att öppna `Proc.htm` i standard webbläsaren.

### Exempel 5: skapa en webb sida för att Visa tjänst objekt

```powershell
Get-Service | ConvertTo-Html -CssUri "test.css"
```

```Output
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"  "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>HTML TABLE</title>
<link rel="stylesheet" type="text/css" href="test.css" />
...
```

Det här kommandot skapar en HTML-sida för de tjänst objekt som `Get-Service` cmdleten returnerar. Kommandot använder parametern **CssUri** för att ange en sammanhängande formatmall för HTML-sidan.

Parametern **CssUri** lägger till ytterligare en `<link rel="stylesheet" type="text/css" href="test.css">` tagg till den resulterande HTML-koden. HREF-attributet i taggen innehåller namnet på format mal len.

### Exempel 6: skapa en webb sida för att Visa tjänst objekt

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

Det här kommandot skapar en HTML-sida för de tjänst objekt som `Get-Service` cmdleten returnerar. Kommandot använder parametern **as** för att ange ett List format. Cmdleten `Out-File` skickar den resulterande HTML-koden till `Services.htm` filen.

### Exempel 7: skapa en webb tabell för det aktuella datumet

```powershell
Get-Date | ConvertTo-Html -Fragment
```

```Output
<table>
<colgroup>...</colgroup>
<tr><th>DisplayHint</th><th>DateTime</th><th>Date</th><th>Day</th><th>DayOfWeek</th><th>DayOfYear</th><th>Hour</th>
<th>Kind</th><th>Millisecond</th><th>Minute</th><th>Month</th><th>Second</th><th>Ticks</th><th>TimeOfDay</th><th>Year</th></tr>
<tr><td>DateTime</td><td>Monday, May 05, 2008 10:40:04 AM</td><td>5/5/2008 12:00:00 AM</td><td>5</td><td>Monday</td>
<td>126</td><td>10</td><td>Local</td><td>123</td><td>40</td><td>5</td><td>4</td><td>633455808041237213</td><td>10:40:04.12
37213</td><td>2008</td></tr>
</table>
```

Det här kommandot använder `ConvertTo-Html` för att generera en HTML-tabell för det aktuella datumet. Kommandot använder `Get-Date` cmdleten för att hämta det aktuella datumet. Den använder en pipeline-operator (|) för att skicka resultaten till- `ConvertTo-Html` cmdleten.

`ConvertTo-Html`Kommandot innehåller parametern **fragment** , som begränsar utdata till en HTML-tabell. Därför utelämnas andra element på en HTML-sida, t `<HEAD>` `<BODY>` . ex. taggarna och.

### Exempel 8: skapa en webb sida för att Visa PowerShell-händelser

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

Det här kommandot använder `Get-EventLog` cmdleten för att hämta händelser från händelse loggen i Windows PowerShell.

En pipeline-operator () används `|` för att skicka händelserna till `ConvertTo-Html` cmdleten, som konverterar händelserna till HTML-format.

`ConvertTo-Html`Kommandot använder **egenskaps** parametern för att endast välja **ID**, **nivå** och **aktivitets** egenskaper för händelsen.

### Exempel 9: skapa en webb sida för att Visa angivna tjänster

```powershell
$htmlParams = @{
  Title = "Windows Services: Server01"
  Body = Get-Date
  PreContent = "<P>Generated by Corporate IT</P>"
  PostContent = "For details, contact Corporate IT."
}
Get-Service A* |
  ConvertTo-Html @htmlParams |
    Out-File Services.htm
Invoke-Item Services.htm
```

Det här kommandot skapar och öppnar en webb sida som visar de tjänster på datorn som börjar med en. I används **title**-, **Body**-, **precontent**-och **PostContent** -parametrarna för `ConvertTo-Html` för att anpassa utdata.

Den första delen av kommandot använder `Get-Service` cmdleten för att hämta tjänsterna på datorn som börjar med en. Kommandot använder en pipeline-operator ( `|` ) för att skicka resultaten till `ConvertTo-Html` cmdleten. Kommandot använder också `Out-File` cmdleten för att skicka utdata till Services.htm-filen.

Ett semikolon ( `;` ) avslutar det första kommandot och startar ett andra kommando, som använder `Invoke-Item` cmdleten för att öppna `Services.htm` filen i standard webbläsaren.

### Exempel 10: Ange meta-egenskaperna och HTML-teckenuppsättningen

```powershell
Get-Service | ConvertTo-HTML -Meta @{
  refresh=10
  author="Author's Name"
  keywords="PowerShell, HTML, ConvertTo-HTML"
} -Charset "UTF-8"
```

Det här kommandot skapar HTML för en webb sida med metataggarna för uppdatering, författare och nyckelord.
Teckenuppsättningen för sidan är inställd på UTF-8

### Exempel 11: Ange HTML till XHTML-över gångs-DTD

```powershell
Get-Service | ConvertTo-HTML -Transitional
```

Det här kommandot anger DOCTYPE för den returnerade HTML-filen till XHTML-över gångs-DTD

## PARAMETRAR

### – Som

Anger om objektet är formaterat som en tabell eller en lista. Giltiga värden är **Table** och **list**. Standardvärdet är **Table**.

**Table** -värdet genererar en HTML-tabell som liknar PowerShell-tabellens format. Rubrik raden visar egenskaps namnen. Varje tabell rad representerar ett objekt och visar objektets värden för varje egenskap.

**List** svärdet genererar en HTML-tabell med två kolumner för varje objekt som liknar PowerShell-List formatet. Den första kolumnen visar egenskaps namnet. Den andra kolumnen visar egenskap svärdet.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Table, List

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Body

Anger den text som ska läggas till efter den inledande `<BODY>` taggen. Som standard finns det ingen text på den platsen.

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Teckenuppsättning

Anger text som ska läggas till i öppnings `<charset>` tag gen. Som standard finns det ingen text på den platsen.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CssUri

Anger Uniform Resource Identifier (URI) för det sammanhängande format bladet (CSS) som tillämpas på HTML-filen. URI: n tas med i en Formatmallslänkar i utdata.

```yaml
Type: System.Uri
Parameter Sets: Page
Aliases: cu, uri

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Fragment

Genererar endast en HTML-tabell. Taggarna HTML, HEAD, TITLE och BODY utelämnas.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Fragment
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Head

Anger `<HEAD>` taggens innehåll. Standardvärdet är `<title\>HTML TABLE</title>`. Om du använder **Head** -parametern ignoreras **title** -parametern.

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger de objekt som ska visas i HTML. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

Om du använder den här parametern för att skicka flera objekt, till exempel alla tjänster på en dator, `ConvertTo-Html` skapar en tabell som visar egenskaperna för en samling eller en objekt mat ris. Om du vill skapa en tabell med de enskilda objekten använder du pipeline-operatorn för att skicka objekten till `ConvertTo-Html` .

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

### -Meta

Anger text som ska läggas till i öppnings `<meta>` tag gen. Som standard finns det ingen text på den platsen.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PostContent

Anger text som ska läggas till efter den avslutande `</TABLE>` taggen. Som standard finns det ingen text på den platsen.

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

### -För-innehåll

Anger text som ska läggas till före öppnings `<TABLE>` tag gen. Som standard finns det ingen text på den platsen.

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

### – Egenskap

Innehåller de angivna egenskaperna för objekten i HTML-koden. Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap. Den beräknade egenskapen kan vara ett skript block eller en hash-tabell. Giltiga nyckel/värde-par är:

- Namn (eller etikett) – `<string>` (lades till i PowerShell 6. x)
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
Accept wildcard characters: False
```

### – Rubrik

Anger en rubrik för HTML-filen, det vill säga texten som visas mellan `<TITLE>` taggarna.

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Över gång

Ändrar **doctype** till **XHTML-över gångs-DTD**, standard- **doctype** är en **XHTML Strict DTD**.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Page
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

### System. Management. Automation. PSObject

Du kan skicka alla .NET-objekt till `ConvertTo-Html` .

## UTDATA

### System. String eller System.Xml.Xmldokument

`ConvertTo-Html` Returnerar en serie med strängar som utgör giltig HTML.

## ANTECKNINGAR

Om du vill använda den här cmdleten, rör ett eller flera objekt till cmdleten eller Använd parametern **InputObject** för att ange objektet. När indatan består av flera objekt är resultatet av dessa två metoder ganska annorlunda.

- När du rör flera objekt till en cmdlet skickar PowerShell objekten till cmdleten en i taget. Därför `ConvertTo-Html` skapar en tabell som visar de enskilda objekten. Om du till exempel rör processerna på en dator till `ConvertTo-Html` , visar den resulterande tabellen alla processer.

- När du använder parametern **InputObject** för att skicka flera objekt, `ConvertTo-Html` tar emot dessa objekt som en samling eller som en matris. Därför skapas en tabell som visar matrisen och dess egenskaper, inte objekten i matrisen. Om du till exempel använder **InputObject** för att skicka processerna på en dator till `ConvertTo-Html` , visar den resulterande tabellen en objekt mat ris och dess egenskaper.

  För att följa den strikta XHTML DTD-koden ändras DOCTYPE-taggen enligt följande:

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## RELATERADE LÄNKAR

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertTo-Xml](ConvertTo-Xml.md)

[Exportera – CliXml](Export-Clixml.md)

[Importera – CliXml](Import-Clixml.md)
