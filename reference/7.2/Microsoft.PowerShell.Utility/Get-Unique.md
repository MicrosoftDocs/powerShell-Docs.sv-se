---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Unique
ms.openlocfilehash: de827d956e6e813e84d87bb1578ee7d596fe2f15
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710098"
---
# Get-Unique

## SAMMANFATTNING
Returnerar unika objekt från en sorterad lista.

## SYNTAX

### Uppsträng (standard)

```
Get-Unique [-InputObject <PSObject>] [-AsString] [<CommonParameters>]
```

### UniqueByType

```
Get-Unique [-InputObject <PSObject>] [-OnType] [<CommonParameters>]
```

## BESKRIVNING

`Get-Unique`Cmdleten jämför varje objekt i en sorterad lista med nästa objekt, eliminerar dubbletter och returnerar bara en instans av varje objekt. Listan måste vara sorterad för att cmdleten ska fungera korrekt.

`Get-Unique` är Skift läges känsligt. Det innebär att strängar som bara skiljer sig i gemener och versaler anses vara unika.

## EXEMPEL

### Exempel 1: Hämta unika ord i en textfil

De här kommandona hittar antalet unika ord i en textfil.

```powershell
$A = $( foreach ($line in Get-Content C:\Test1\File1.txt) {
    $line.tolower().split(" ")
  }) | Sort-Object | Get-Unique
$A.count
```

Det första kommandot hämtar innehållet i File.txts filen. Alla text rader konverteras till gemener och sedan delas varje ord på en separat rad i utrymmet (""). Sedan sorteras den resulterande listan i alfabetisk ordning (standard) och använder `Get-Unique` cmdleten för att ta bort duplicerade ord. Resultaten lagras i `$A` variabeln.

Det andra kommandot använder egenskapen **Count** för samlingen med strängar i `$A` för att fastställa hur många objekt som finns `$A` .

### Exempel 2: Hämta unika heltal i en matris

Det här kommandot hittar unika medlemmar i uppsättningen med heltal.

```powershell
1,1,1,1,12,23,4,5,4643,5,3,3,3,3,3,3,3 | Sort-Object | Get-Unique
```

```Output
1
3
4
5
12
23
4643
```

Det första kommandot tar en matris med heltal som skrivs på kommando raden, kopplar dem till cmdlet: en `Sort-Object` som ska sorteras och kopplar dem sedan till `Get-Unique` , vilket eliminerar dubbletter av poster.

### Exempel 3: Hämta unika objekt typer i en katalog

Det här kommandot använder `Get-ChildItem` cmdleten för att hämta innehållet i den lokala katalogen, inklusive filer och kataloger.

```powershell
Get-ChildItem | Sort-Object {$_.GetType()} | Get-Unique -OnType
```

Pipeline-operatorn (|) skickar resultaten till `Sort-Object` cmdleten. `$_.GetType()`Instruktionen använder **gettype** -metoden för varje fil eller katalog. `Sort-Object`Sorterar sedan objekt efter typ. En annan pipeline-operator skickar resultatet till `Get-Unique` . Parametern **OnType** styrs `Get-Unique` för att returnera endast ett objekt av varje typ.

### Exempel 4: Hämta unika processer

Det här kommandot hämtar namnen på de processer som körs på datorn med borttagna dubbletter.

```powershell
Get-Process | Sort-Object | Select-Object processname | Get-Unique -AsString
```

`Get-Process`Kommandot hämtar alla processer på datorn. Pipeline-operatorn (|) skickar resultatet till `Sort-Object` , som som standard sorterar processerna i alfabetisk ordning efter processname. Resultaten är skickas till `Select-Object` cmdleten, som endast väljer värden för egenskapen processname för varje objekt. Resultatet blir sedan skickas för `Get-Unique` att eliminera dubbletter.

Parametern **enstring** instruerar `Get-Unique` att behandla **processname** -värden som strängar.
Utan den här parametern `Get-Unique` behandlar **processname** -värden som objekt och returnerar bara en instans av objektet, det vill säga det första process namnet i listan.

## PARAMETRAR

### -Uppsträng

Anger att denna cmdlet använder data som en sträng. Utan den här parametern behandlas data som ett objekt, så när du skickar en samling objekt av samma typ till `Get-Unique` , till exempel en samling filer, returnerar den bara en (första). Du kan använda den här parametern för att hitta unika värden för objekt egenskaper, t. ex. fil namnen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger ininformation för `Get-Unique` . Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

Den här cmdleten behandlar inskickade inskickade med **InputObject** som en samling. den räknar inte upp enskilda objekt i samlingen. Eftersom samlingen är ett enda objekt returneras alltid insamlade inskickade med **InputObject** .

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

### -OnType

Anger att denna cmdlet bara returnerar ett objekt av varje typ.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UniqueByType
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

Du kan skicka vidare alla typer av objekt till `Get-Unique` .

## UTDATA

### System. Management. Automation. PSObject

Den typ av objekt som `Get-Unique` returneras bestäms av indatamängden.

## ANTECKNINGAR

Du kan också referera till `Get-Unique` med dess inbyggda alias `gu` . Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

Om du vill sortera en lista använder du sorterings objekt. Du kan också använda den **unika** parametern för `Sort-Object` för att hitta unika objekt i en lista.

## RELATERADE LÄNKAR

[Select-Object](Select-Object.md)

[Sortera objekt](Sort-Object.md)

