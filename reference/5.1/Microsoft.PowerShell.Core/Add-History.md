---
external help file: System.Management.Automation.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-history?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-History
ms.openlocfilehash: 29f1bbab871a91a9bd77c42f99f9e7f11e18b588
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263685"
---
# Add-History

## SAMMANFATTNING
Lägger till poster i sessionens historik.

## SYNTAX

```
Add-History [[-InputObject] <PSObject[]>] [-Passthru] [<CommonParameters>]
```

## BESKRIVNING

`Add-History`Cmdleten lägger till poster i slutet av tidigare sessioner, det vill säga en lista över kommandon som angavs under den aktuella sessionen.

Tidigare session är en lista över kommandon som anges under sessionen. Tidigare sessioner representerar körnings ordning, status och start-och slut tid för kommandot. När du anger varje kommando lägger PowerShell till det i historiken så att du kan återanvända det. Mer information om tidigare sessioner finns [about_History](About/about_History.md).

Historiken för sessionen hanteras separat från historiken som underhålls av **PSReadLine** -modulen.
Båda historiken är tillgängliga i sessioner där **PSReadLine** har lästs in. Den här cmdleten fungerar bara med tidigare session. Mer information finns i [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).

Du kan använda `Get-History` cmdleten för att hämta kommandon och skicka dem till `Add-History` , eller så kan du exportera kommandona till en CSV-eller XML-fil, sedan importera kommandona och skicka den importerade filen till `Add-History` . Du kan använda denna cmdlet för att lägga till vissa kommandon i historiken eller för att skapa en enskild historik fil som innehåller kommandon från fler än en session.

## EXEMPEL

### Exempel 1: Lägg till kommandon i historiken för en annan session

I det här exemplet lägger du till kommandona som skrevs i en PowerShell-session i historiken för en annan PowerShell-session.

```powershell
Get-History | Export-Csv c:\testing\history.csv -IncludeTypeInformation
Import-Csv c:\testing\history.csv | Add-History
```

Det första kommandot hämtar objekt som representerar kommandona i historiken och exporterar dem till `History.csv` filen.

Det andra kommandot anges på kommando raden i en annan session. Den använder `Import-Csv` cmdleten för att importera objekten i `History.csv` filen. Pipeline-operatorn ( `|` ) skickar objekten till `Add-History` cmdleten, som lägger till de objekt som representerar kommandona i `History.csv` filen i den aktuella tidigare sessionen.

### Exempel 2: importera och kör kommandon

Det här exemplet importerar kommandon från `History.xml` filen, lägger till dem i den aktuella tidigare sessionen och kör sedan kommandona i den kombinerade historiken.

```powershell
Import-Clixml c:\temp\history.xml | Add-History -PassThru | ForEach-Object -Process {Invoke-History}
```

Det första kommandot använder `Import-Clixml` cmdleten för att importera en kommando historik som exporter ATS till `History.xml` filen. Pipeline-operatorn skickar kommandon till `Add-History` cmdleten, som lägger till kommandon i den aktuella tidigare sessionen. Parametern **Passthru** skickar objekten som representerar de tillagda kommandona nedåt i pipelinen.

Kommandot använder sedan `ForEach-Object` cmdleten för att tillämpa `Invoke-History` kommandot på varje kommando i den kombinerade historiken. `Invoke-History`Kommandot är formaterat som ett skript block som omges av klammerparenteser ( `{}` ), vilket krävs för cmdlet-parametern **process** `ForEach-Object` .

### Exempel 3: Lägg till kommandon i historiken i slutet av historiken

Det här exemplet lägger till de första fem kommandona i historiken i slutet av historik listan.

```powershell
Get-History -Id 5 -Count 5 | Add-History
```

`Get-History`Cmdlet: en hämtar de fem kommandona som slutar på kommando 5. Pipeline-operatorn skickar dem till `Add-History` cmdleten, som lägger till dem i den aktuella historiken. `Add-History`Kommandot innehåller inga parametrar, men PowerShell associerar objekten som skickas via pipelinen med **InputObject** -parametern för `Add-History` .

### Exempel 4: Lägg till kommandon i en CSV-fil i den aktuella historiken

I det här exemplet lägger du till kommandona i `History.csv` filen i den aktuella tidigare sessionen.

```powershell
$a = Import-Csv c:\testing\history.csv
Add-History -InputObject $a -PassThru
```

`Import-Csv`Cmdleten importerar kommandona i `History.csv` filen och lagrar dess innehåll i variabeln `$a` .

Det andra kommandot använder `Add-History` cmdleten för att lägga till kommandona från `History.csv` i den aktuella tidigare sessionen. Parametern **InputObject** används för att ange `$a` variabeln och parametern **Passthru** för att generera ett objekt som ska visas på kommando raden. Utan parametern **Passthru** `Add-History` genererar cmdleten inga utdata.

### Exempel 5: Lägg till kommandon i en XML-fil i den aktuella historiken

I det här exemplet läggs kommandona i `history.xml` filen till i den aktuella tidigare sessionen.

```powershell
Add-History -InputObject (Import-Clixml c:\temp\history.xml)
```

Parametern **InputObject** skickar kommandots resultat inom parentes till `Add-History` cmdleten. Kommandot inom parenteser, som körs först, importerar `history.xml` filen till PowerShell. `Add-History`Cmdleten lägger sedan till kommandona i filen i tidigare sessioner.

## PARAMETRAR

### – InputObject

Anger en matris med poster som ska läggas till i historiken som **HistoryInfo** -objekt i sessionens historik.
Du kan använda den här parametern för att skicka ett **HistoryInfo** -objekt, till exempel de som returneras av `Get-History` `Import-Clixml` cmdletarna,, eller `Import-Csv` `Add-History` .

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – Passthru

Anger att denna cmdlet returnerar ett **HistoryInfo** -objekt för varje historik post. Som standard genererar denna cmdlet inga utdata.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Microsoft. PowerShell. commands. HistoryInfo

Du kan skicka ett **HistoryInfo** -objekt till denna cmdlet.

## UTDATA

### Ingen eller Microsoft. PowerShell. commands. HistoryInfo

Denna cmdlet returnerar ett **HistoryInfo** -objekt om du anger parametern **Passthru** . Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

Tidigare session är en lista över de kommandon som angavs under sessionen tillsammans med ID: t. Tidigare sessioner representerar körnings ordning, status och start-och slut tid för kommandot. När du anger varje kommando lägger PowerShell till det i historiken så att du kan återanvända det. Mer information om tidigare sessioner finns [about_History](About/about_History.md).

Använd parametern **InputObject** för att ange vilka kommandon som ska läggas till i historiken. `Add-History`Kommandot accepterar endast **HistoryInfo** -objekt, till exempel de som returneras för varje kommando av `Get-History` cmdleten. Du kan inte skicka en sökväg och ett fil namn eller en lista med kommandon.

Du kan använda parametern **InputObject** för att skicka en fil med **HistoryInfo** -objekt till `Add-History` . Det gör du genom att exportera resultatet av ett `Get-History` kommando till en fil med hjälp av `Export-Csv` `Export-Clixml` cmdleten eller och sedan importera filen med hjälp av `Import-Csv` `Import-Clixml` cmdletarna eller. Sedan kan du skicka filen med importerade **HistoryInfo** -objekt till `Add-History` en pipeline eller i en variabel. Mer information finns i exemplen.

Filen med **HistoryInfo** -objekt som du skickar till `Add-History` cmdleten måste innehålla typ information, kolumn rubriker och alla egenskaper för **HistoryInfo** -objekten. Om du tänker skicka tillbaka objekten till ska `Add-History` du inte använda **NoTypeInformation** -parametern för `Export-Csv` cmdleten och inte ta bort typ informationen, kolumn rubrikerna eller något fält i filen.

Om du vill ändra sessionens historik exporterar du sessionen till en CSV-eller XML-fil, ändrar filen, importerar filen och använder `Add-History` den för att lägga till den i den aktuella tidigare sessionen.

## RELATERADE LÄNKAR

[Rensa – historik](Clear-History.md)

[Hämta historik](Get-History.md)

[Anropa-historik](Invoke-History.md)

[about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)

[Get-PSReadLineOption](/powershell/module/psreadline/get-psreadlineoption)

[Set-PSReadLineOption](/powershell/module/psreadline/set-psreadlineoption)
