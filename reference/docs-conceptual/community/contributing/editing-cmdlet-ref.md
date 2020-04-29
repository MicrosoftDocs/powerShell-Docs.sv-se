---
title: Redigera referens artiklar
description: Den här artikeln beskriver de specifika kraven för att redigera cmdlet-referenser och om ämnen i PowerShell-dokumentationen.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: e135f6cc81ba7537a535a08421e1ca9b2b2af573
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624779"
---
# <a name="editing-reference-articles"></a>Redigera referens artiklar

Artiklar med cmdlet-referenser har en speciell struktur. Strukturen definieras av [PlatyPS][].
PlatyPS genererar cmdlet-hjälpen för PowerShell-moduler i markdown. När du har redigerat Markdown-filerna används PlatyPS för att skapa MAML-hjälpfiler som används av cmdleten `Get-Help`.

PlatyPS har ett hårdkodat schema för cmdlet-referenser som skrivs in i koden. Dokumentet [platyPS.schema.md][] är ett försök att beskriva strukturen. Schemaöverträdelser orsakar build-fel som måste åtgärdas innan vi kan acceptera ditt bidrag.

## <a name="general-guidelines"></a>Allmänna riktlinjer

- Ta inte bort någon av rubrikstrukturerna. PlatyPS förväntar sig en specifik uppsättning rubriker.
- Rubrikerna **Indatatyp** och **Utdatatyp** måste ha en typ. Om cmdleten inte kräver inmatade värden eller returnerar ett värde använder du `None`värdet.
- Inhägnade kodblock är bara tillåtna i avsnittet [Exempel](#structuring-examples).
- Infogade kodomfång kan användas i alla stycken.

## <a name="formatting-about_-files"></a>Formatera About_-filer

`About_*`filerna skrivs i markdown men levereras som oformaterade textfiler. Vi använder [pandoc][] för att konvertera markdown till oformaterad text. `About_*`filerna är formaterade för bästa kompatibilitet i alla versioner av PowerShell och med publicerings verktygen.

Riktlinjer för grundläggande formatering:

- Begränsa rader till 80 tecken. Pandoc drar in vissa markdown-block så att dessa block måste justeras.
  - Kodblock är begränsade till 76 tecken
  - Tabeller är begränsade 76 tecken
  - Blockquotes (och aviseringar) är begränsade 78 tecken

- Använda pandoc särskilda meta-tecken `\`, och`$``<`
  - Inom ett sidhuvud – dessa tecken måste föregås av ett inledande `\` tecken eller omges av kod intervall med hjälp av baktick ()`` ` ``
  - I ett stycke ska de här tecknen placeras i kod intervall. Ett exempel:

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- Tabeller måste rymmas inom 76 tecken
  - Radbryt innehållet i celler manuellt över flera rader
  - Använd inledande och avslutande `|`-tecken på varje rad
  - I följande exempel visas hur du skapar en tabell som innehåller information som radbryts på flera rader i en cell.

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > Begränsningen 76-kolumn gäller endast för `About_*` ämnen. Du kan använda breda kolumner i konceptuella eller cmdlet Reference-artiklar.

## <a name="structuring-examples"></a>Strukturerings exempel

I PlatyPS-schemat är rubriken **EXEMPEL** en H2-rubrik, och varje exempel är en H3-rubrik.

I ett exempel tillåter inte schemat att kodblock avgränsas med stycken. Det schema som stöds är:

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

Numrera varje exempel och lägg till en kort rubrik.

Ett exempel:

### <a name="example-1-get-cmdlets-functions-and-aliases"></a>Exempel 1: Hämta cmdlets, Functions och alias

Det här kommandot hämtar PowerShell-cmdletar, funktioner och alias som är installerade på datorn.

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a>Exempel 2: Hämta kommandon i den aktuella sessionen

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a>Nästa steg

[Checklista för redigering](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
