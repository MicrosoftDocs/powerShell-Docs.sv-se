---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/new-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-IseSnippet
ms.openlocfilehash: 0ed1c2913fc7531574bfbdd435a002d60931d24a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263876"
---
# New-IseSnippet

## SAMMANFATTNING
Skapar ett Windows PowerShell ISE kodfragment.

## SYNTAX

```
New-IseSnippet [-Title] <String> [-Description] <String> [-Text] <String> [-Author <String>]
 [-CaretOffset <Int32>] [-Force] [<CommonParameters>]
```

## BESKRIVNING

`New-ISESnippet`Cmdleten skapar en återanvändbar text "kodfragment" för Windows PowerShell ISE. Du kan använda kodfragment för att lägga till text i skript fönstret eller kommando fönstret i Windows PowerShell ISE. Den här cmdleten är endast tillgänglig i Windows PowerShell ISE.

Från och med Windows PowerShell 3,0 innehåller Windows PowerShell ISE en samling inbyggda kodfragment. Med `New-ISESnippet` cmdleten kan du skapa egna kod avsnitt som ska läggas till i den inbyggda samlingen. Du kan visa, ändra, lägga till, ta bort och dela fragment-filer och inkludera dem i Windows PowerShell-moduler. Om du vill se kodfragment i Windows PowerShell ISE väljer du **Starta kodfragment** på **Redigera** -menyn eller trycker på <kbd>CTRL</kbd> + <kbd>J</kbd>.

`New-ISESnippet`Cmdleten skapar en `<Title>.Snippets.ps1xml` fil i `$home\Documents\WindowsPowerShell\Snippets` katalogen med den rubrik som du anger. Om du vill inkludera en kodfragments fil i en modul som du redigerar lägger du till kodfragment filen i en under katalog i en kod avsnitt i din modul katalog.

Du kan inte använda användardefinierade kodfragment i en session där körnings principen är **begränsad** eller **AllSigned**.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: skapa ett fragment för Comment-Based hjälp

```
New-IseSnippet -Title Comment-BasedHelp -Description "A template for comment-based help." -Text "<#
    .SYNOPSIS

    .DESCRIPTION
    .PARAMETER  <Parameter-Name>
    .INPUTS
    .OUTPUTS
    .EXAMPLE
    .LINK
#>"
```

Det här kommandot skapar ett Comment-BasedHelp-kodfragment för Windows PowerShell ISE. Den skapar en fil med namnet `Comment-BasedHelp.snippets.ps1xml` i användarens kod avsnitts katalog `$home\Documents\WindowsPowerShell\Snippets` .

### Exempel 2: skapa ett obligatoriskt kod avsnitt

```
$M = @'
Param
(
  [parameter(Mandatory=$true)]
  [String[]]
  $<ParameterName>
)
'@

New-ISESnippet -Text $M -Title Mandatory -Description "Adds a mandatory function parameter." -Author "Patti Fuller, Fabrikam Corp." -Force
```

I det här exemplet skapas ett kodfragment med namnet **obligatorisk** för Windows PowerShell ISE. Det första kommandot sparar kodfragments texten i `$M` variabeln. Det andra kommandot använder `New-ISESnippet` cmdleten för att skapa kodfragmentet. Kommandot använder **Force** -parametern för att skriva över ett tidigare kodfragment med samma namn.

### Exempel 3: kopiera ett obligatoriskt kodfragment från en mapp till en målmapp

```
Copy-Item "$Home\Documents\WindowsPowerShell\Snippets\Mandatory.Snippets.ps1xml" -Destination "\\Server\Share"
```

Det här kommandot använder `Copy-Item` cmdleten för att kopiera det **obligatoriska** kodfragmentet från mappen där `New-ISESnippet` placerar det till fil resursen Server\Share.

## PARAMETRAR

### – Författare

Anger författaren till kodfragmentet. Fältet författare visas i kodfragments filen, men det visas inte när du klickar på kodfragmentet i Windows PowerShell ISE.

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

### -CaretOffset

Anger tecken på kodfragments texten som denna cmdlet placerar markören på. Ange ett heltal som representerar markörens position med "1" som representerar det första text tecknen. Standardvärdet, 0 (noll), placerar markören direkt före det första text tecken. Den här parametern drar inte in text i kodfragmentet.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -Beskrivning

Anger en beskrivning av kodfragmentet. Beskrivning svärdet visas när du klickar på namn kods tycket i Windows PowerShell ISE. Den här parametern är obligatorisk.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Anger att denna cmdlet skriver över kodfragment-filer med samma namn på samma plats. Som standard `New-ISESnippet` skrivs inte filer över.

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

### – Text

Anger det text värde som läggs till när du väljer kodfragmentet. Kodfragmentet visas när du klickar på namn kods tycket i Windows PowerShell ISE. Den här parametern är obligatorisk.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Rubrik

Anger en titel eller ett namn för kodfragmentet. Rubriken namnger också kod filen. Den här parametern är obligatorisk.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Den här cmdleten tar inte emot några ininformation från pipelinen.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

`New-IseSnippet` lagrar nya användare-skapade kodfragment i osignerade. ps1xml-filer. Det innebär att Windows PowerShell inte kan lägga till dem i en session där körnings principen är **AllSigned** eller **begränsad**. I en **begränsad** eller **AllSigned** session kan du skapa, hämta och importera osignerade kodfragment, men du kan inte använda dem i sessionen.

Om du använder `New-IseSnippet` cmdleten i en **begränsad** eller **AllSigned** -session, skapas kodfragmentet, men ett fel meddelande visas när Windows PowerShell försöker lägga till det nyligen skapade kodfragmentet i sessionen. Om du vill använda det nya kodfragmentet (och andra osignerade användar kods tycken) ändrar du körnings principen och startar sedan om Windows PowerShell ISE.

Mer information om körnings principer för Windows PowerShell finns i about_Execution_Policies.

- Ändra kodfragmentet genom att redigera kodfragments filen. Du kan redigera kodfragment-filer i skript fönstret i Windows PowerShell ISE.
- Ta bort ett kodfragment som du har lagt till genom att ta bort kodfragments filen.
- Det går inte att ta bort ett inbyggt kodfragment, men du kan dölja alla inbyggda kodfragment med hjälp av $psise. Options. ShowDefaultSnippets = $false "kommandot.
- Du kan skapa ett kodfragment som har samma namn som ett inbyggt kodfragment. Båda kodfragmenten visas i menyn kodfragment i Windows PowerShell ISE.

## RELATERADE LÄNKAR

[Get-IseSnippet](Get-IseSnippet.md)

[Importera – IseSnippet](Import-IseSnippet.md)
