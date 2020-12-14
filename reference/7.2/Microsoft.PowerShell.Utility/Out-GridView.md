---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 19a53b5b14d2dfdb513fbbda4c55ba0df37ab1c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709067"
---
# Out-GridView

## SAMMANFATTNING
Skickar utdata till en interaktiv tabell i ett separat fönster.

## SYNTAX

### PassThru (standard)

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### Vänta

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### OutputMode

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## BESKRIVNING

`Out-GridView`Cmdleten skickar utdata från ett kommando till ett fönster för rutnätsvy där utdata visas i en interaktiv tabell.

Eftersom denna cmdlet kräver ett användar gränssnitt fungerar den inte på Windows Server Core eller Windows Nano Server.

Du kan använda följande funktioner i tabellen för att undersöka dina data:

- Dölj, Visa och ordna om kolumner
- Sortera rader
- Snabb filter
- Lägg till villkors filter
- Kopiera och klistra in

Fullständiga instruktioner finns i avsnittet [anteckningar](#notes) i den här artikeln.

> [!NOTE]
> Den här cmdleten introducerades om i PowerShell 7. Den här cmdleten är endast tillgänglig på Windows-system som stöder Windows-skrivbordet. En plattforms oberoende version av denna cmdlet finns i [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) -modulen i PowerShell-galleriet.

## EXEMPEL

### Exempel 1: utmatnings processer till en rutnätsvy

Det här exemplet hämtar processerna som körs på den lokala datorn och skickar dem till ett fönster för rutnätsvy.

```powershell
Get-Process | Out-GridView
```

### Exempel 2: använda en variabel för att visa processer i en rutnätsvy

Det här exemplet hämtar också processerna som körs på den lokala datorn och skickar dem till ett fönster för rutnätsvy.

```powershell
$P = Get-Process
$P | Out-GridView
```

Utdata från `Get-Process` cmdleten sparas i `$P` variabeln. Sedan `$P` är skickas till `Out-GridView` .

### Exempel 3: Visa markerade egenskaper i en rutnätsvy

I det här exemplet visas valda egenskaper för de processer som körs i en rutnätsvy.

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

Utdatan från `Get-Process` är skickas `Select-Object` till för att välja egenskaper för **namn**, för-och **PeakWorkingSet** . En annan pipeline-operator skickar filtrerade objekt till `Sort-Object` cmdleten för att sortera dem i fallande ordning efter värdet för den **aktiva** egenskapen.
Sedan är de sorterade resultaten skickas till `Out-GridView` . Nu kan du använda funktionerna i diagramvyn för att söka, sortera och filtrera data.

### Exempel 4: spara utdata till en variabel och sedan Visa en rutnätsvy

Det här exemplet sparar cmdlet-utdata i en variabel och skickar den sedan till `Out-GridView` .

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

`Get-ChildItem` hämtar alla filer i installations katalogen för PowerShell och dess under kataloger med hjälp av den `$PSHOME` automatiska variabeln. Parenteserna i kommandot fastställer ordningen för åtgärder. Därför sparas utdata från `Get-ChildItem` kommandot i `$A` variabeln innan det skickas till `Out-GridView` .

### Exempel 5: utmatnings processer för en angiven dator till en rutnätsvy

I det här exemplet visas de processer som körs på Server01-datorn i ett fönster för rutnätsvy.

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

Examle använder `ogv` , vilket är aliaset för `Out-GridView` cmdleten. Parametern **title** anger fönstrets rubrik.

### Exempel 6: Spara data från fjärrdatorer till en rutnätsvy

Det här exemplet visar hur du skickar data som samlas in från fjärrdatorer till `Out-GridView` .

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

`Invoke-Command` körs `Get-Culture` på tre fjärrdatorer. Resulterande data är skickas `Out-GridView` . Observera att skript blocket som körs på fjärrdatorn inte innehåller `Out-GridView` kommandot. Om den gjorde det kunde kommandot inte utföras när det försökte öppna ett fönster för rutnätsvy på var och en av de fjärranslutna datorerna.

### Exempel 7: skicka flera objekt via `Out-GridView`

I det här exemplet kan du välja flera processer i `Out-GridView` fönstret. De processer som du väljer skickas till `Export-Csv` kommandot och skrivs till `ProcessLog.csv` filen.

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

Med parametern **Passthru** `Out-GridView` kan du skicka flera objekt nedåt i pipelinen. Parametern **Passthru** motsvarar användningen av **Multiple** -värdet för parametern **OutputMode** .

### Exempel 8: skapa en Windows-genväg till `Out-GridView`

Det här exemplet visar hur du använder **wait** -parametern för `Out-GridView` för att skapa en Windows-genväg till `Out-GridView` fönstret.

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

Den här kommando raden kan användas i en Windows-genväg. Utan parametern **wait** avslutas PowerShell så snart `Out-GridView` fönstret har öppnats, vilket skulle stänga `Out-GridView` fönstret nästan omedelbart.

## PARAMETRAR

### – InputObject

Anger objekt som cmdleten accepterar som ininformation för `Out-GridView` .

När du använder parametern **InputObject** för att skicka en samling objekt till `Out-GridView` , `Out-GridView` behandlar samlingen som ett samlings objekt och visar en rad som representerar samlingen. Om du vill visa varje objekt i samlingen använder du en pipeline-operator ( `|` ) för att skicka objekt till `Out-GridView` .

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

### -OutputMode

Anger de objekt som det interaktiva fönstret skickar nedåt i pipeline som ininformation till andra kommandon.
Som standard genererar denna cmdlet inga utdata. Om du vill skicka objekt från det interaktiva fönstret nedåt i pipelinen klickar du på objekten och klickar sedan på OK.

Värdena för den här parametern avgör hur många objekt du kan skicka pipelinen.

- Inga.  Inga objekt. Detta är standardvärdet.
- Samma. Noll objekt eller ett objekt. Använd det här värdet när nästa kommando bara kan ta ett indatamängds objekt.
- Flera. Noll, ett eller flera objekt. Använd det här värdet när nästa kommando kan ta flera inobjekt. Värdet motsvarar parametern **Passthru** .

```yaml
Type: Microsoft.PowerShell.Commands.OutputModeOption
Parameter Sets: OutputMode
Aliases:
Accepted values: None, Single, Multiple

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru

Anger att cmdleten skickar objekt från det interaktiva fönstret nedåt i pipeline som ininformation till andra kommandon. Som standard genererar denna cmdlet inga utdata. Den här parametern motsvarar att använda **Multiple** -värdet för parametern **OutputMode** .

Om du vill skicka objekt från det interaktiva fönstret nedåt i pipelinen klickar du på objekten och klickar sedan på OK. Shift-klicka och Ctrl-klicka stöds.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PassThru
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Rubrik

Anger den text som visas i namn listen för `Out-GridView` fönstret. Som standard visar namn listen det kommando som anropar `Out-GridView` .

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

### – Vänta

Anger att cmdleten ignorerar kommando tolken och förhindrar att Windows PowerShell stängs tills `Out-GridView` fönstret har stängts. Som standard returnerar kommando tolken när `Out-GridView` fönstret öppnas.

Med den här funktionen kan du använda `Out-GridView` cmdlets i Windows-genvägar. När `Out-GridView` används i en genväg utan parametern **wait** , `Out-GridView` visas fönstret bara tillfälligt innan PowerShell stängs.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Wait
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

Du kan skicka valfritt objekt till denna cmdlet.

## UTDATA

### Inga

Normalt `Out-GridView` returnerar inte några objekt. När du använder parametern **Passthru** returneras objekten som representerar de valda raderna till pipelinen.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

Du kan inte använda ett fjärran slutet kommando för att öppna ett fönster för rutnätsvy på en annan dator.

Kommandots utdata som du skickar till `Out-GridView` kan inte formateras med `Format` cmdletarna, till exempel `Format-Table` eller- `Format-Wide` cmdletar. Använd cmdleten för att välja egenskaper `Select-Object` .

Avserialiserade utdata från fjärrkommandon kanske inte är korrekt formaterade i rutnätsvy-fönstret.

Kortkommandon **för**`Out-GridView`

|              Använd den här nyckeln:              |                                   För att utföra den här åtgärden:                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| <kbd>Tabbtecken</kbd>                          | Flyttar markören från **filter** rutan till menyn **Lägg till villkor** i tabellen och tillbaka. |
| <kbd>Nedåtpil</kbd>                      | Flytta upp en rad. Flyttar till kolumn rubriker från första raden med data.                             |
| <kbd>NEDPIL</kbd>                    | Flytta ned en rad.                                                                           |
| <kbd>LeftArrow</kbd>                    | Flytta en kolumn till vänster i kolumn rubrik raden.                                                  |
| <kbd>RightArrow</kbd>                   | I kolumn rubrik raden flyttar du en kolumn till höger.                                                 |
| <kbd>ContextMenuKey</kbd>               | I kolumn rubrik raden visas alternativet Välj kolumner.                                    |
| <kbd>Ange</kbd> eller <kbd>blank steg</kbd> | I kolumn rubrik raden sorterar du kolumn data (växla A-Z, Z-A).                                    |

**Använda funktionerna i rutnätsvy-fönstret**

**För att dölja eller Visa en kolumn:**

1. Högerklicka på en kolumn rubrik och klicka på **Välj kolumner**.
2. I dialog rutan **Välj kolumner** använder du piltangenterna för att flytta kolumnerna mellan de markerade kolumnerna i rutorna tillgängliga kolumner. Endast kolumner i rutan **Välj kolumner** visas i fönstret rutnätsvy.

**Så här ordnar du om kolumner:**

Du kan dra och släppa kolumner till önskad plats. Eller Använd följande steg:

1. Högerklicka på en kolumn rubrik och klicka på **Välj kolumner**.
2. I dialog rutan **Välj kolumner** använder du knapparna **Flytta upp** och **Flytta ned** för att ändra ordning på kolumnerna. Kolumner överst i listan visas till vänster om kolumner längst ned i listan i fönstret rutnätsvy.

**Sortera tabell data**

- Om du vill sortera data klickar du på en kolumn rubrik.
- Klicka på kolumn rubriken igen om du vill ändra sorterings ordningen. Varje gången du klickar på samma rubrik växlar sorterings ordningen mellan stigande till fallande ordning. Den aktuella ordningen anges av en triangel i kolumn rubriken.

**Så här väljer du tabell data**

- Om du vill markera en rad markerar du raden eller använder upp-eller nedpilen för att navigera till raden.
- Om du vill markera alla rader (förutom rubrik raden) trycker du på <kbd>CTRL</kbd> + <kbd>A</kbd>.
- Om du vill markera efterföljande rader trycker du på och håller <kbd>ned SKIFT</kbd> -tangenten medan du klickar på raderna eller använder piltangenterna.
- Om du vill markera rader som inte är i följd trycker du på <kbd>CTRL</kbd> -tangenten och klickar för att lägga till en rad i markeringen.
- Det går inte att markera kolumner och det går inte att markera hela kolumn rubrik raden.

**Kopiera rader**

- Om du vill kopiera en eller flera rader från tabellen markerar du raderna och trycker sedan på CTRL + C.

  Du kan klistra in data i valfritt text-eller kalkyl blads program. Du kan inte kopiera kolumner eller delar av rader och du kan inte kopiera kolumn rubrik raden.

**Söka i tabellen (snabb filter)**

Använd filter rutan för att söka efter data i tabellen. När du skriver i rutan visas endast objekt som innehåller texten som skrivs in i tabellen.

- Sök efter text. Om du vill söka efter text i tabellen skriver du den text som du vill söka efter i rutan filter.
- Sök efter flera ord. Om du vill söka efter flera ord i tabellen skriver du orden avgränsade med blank steg. `Out-GridView` visar rader som innehåller alla ord (logiska och).
- Sök efter litterala fraser. Om du vill söka efter fraser som innehåller blank steg eller specialtecken, omger du frasen med citat tecken. `Out-GridView` visar rader som innehåller en exakt matchning för frasen.
- Sök i kolumner. Om du vill söka efter text i en eller flera kolumner använder du följande format:

  `<column>:<text> [<column>:<text>] ...`

  Om du till exempel vill hitta "net" i kolumnen **DisplayName** i rutan **filter** skriver du:

  `displayname:net`

  Om du vill hitta rader med "net" i kolumnerna **DisplayName** och **namn** , skriver du följande i rutan **filter** :

  `displayname:net name:net`

- Stäng av Sök funktionen. Om du vill visa hela tabellen igen klickar du på knappen röd X i det övre högra hörnet av **filter** rutan eller tar bort texten från **filter** rutan.

**Använd villkor för att filtrera tabellen**

Du kan använda regler eller kriterier för att avgöra vilka objekt som visas i tabellen. Objekt visas bara när de uppfyller alla kriterier som du upprättar. De tillgängliga kriterierna bestäms av egenskaperna för de objekt som visas i fönstret rutnätsvy och .NET Framework typer av dessa egenskaper.

Varje kriterium har följande format:

`<column> <operator> <value>`

Villkor för olika egenskaper är anslutna med **och**. Villkor för samma egenskap är anslutna med **eller**. Du kan inte ändra de logiska anslutningarna.

Kriterierna påverkar bara visningen. Objekt tas inte bort från tabellen.

**Lägga till villkor**

1. Om du vill visa meny knappen **Lägg till villkor** klickar du på pilen i det övre högra hörnet i fönstret.
2. Klicka på Meny knappen **Lägg till villkor** .
3. Klicka för att välja kolumner (egenskaper). Du kan välja en eller flera egenskaper.
4. När du är färdig med att välja egenskaper klickar du på knappen **Lägg till** .
5. Klicka på **Avbryt** om du vill avbryta tilläggen.
6. Om du vill lägga till fler villkor klickar du på knappen **Lägg till villkor** igen.

**Så här redigerar du ett kriterium**

- Om du vill ändra en operator klickar du på värdet blå operator och väljer sedan en annan operator i list rutan.
- Ange ett värde i rutan värde om du vill ange eller ändra ett värde. Om du anger ett värde som inte är giltigt visas en cirkel X-ikon. Ändra värdet om du vill ta bort det.
- Om du vill skapa en **or** -instruktion lägger du till ett villkor med samma egenskap.

**Ta bort villkor**

- Om du vill ta bort de valda villkoren klickar du på det röda krysset bredvid varje kriterium.
- Om du vill ta bort alla kriterier klickar du på knappen **Rensa alla** .

## RELATERADE LÄNKAR

[Ut-fil](Out-File.md)

[Out-Printer](Out-Printer.md)

[Out-sträng](Out-String.md)

