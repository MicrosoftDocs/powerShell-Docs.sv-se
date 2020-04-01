---
title: Redigera referens artiklar
description: Den här artikeln beskriver de specifika kraven för att redigera cmdlet-referenser och om ämnen i PowerShell-dokumentationen.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 3aed1c14429310c57681397d4877a3a6f48400fd
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500980"
---
# <a name="editing-reference-articles"></a>Redigera referens artiklar

Artiklar om cmdlet-referenser har en speciell struktur. Den här strukturen definieras av [PlatyPS][].
PlatyPS genererar cmdlet-hjälpen för PowerShell-moduler i markdown. När du har redigerat markdown-filerna används PlatyPS för att skapa MAML-hjälpfiler som används av `Get-Help`-cmdleten.

PlatyPS har ett hårdkodat schema för cmdlet-referenser som skrivs till koden. [PlatyPS.schema.MD][] -dokumentet försöker beskriva den här strukturen. Schema överträdelser orsakar build-fel som måste åtgärdas innan vi kan acceptera ditt bidrag.

## <a name="general-guidelines"></a>Allmänna riktlinjer

- Ta inte bort någon av huvud strukturerna. PlatyPS förväntar sig en speciell uppsättning huvuden.
- **Indatatypen och utmatnings** **typ** rubrikerna måste ha en typ. Om cmdleten inte kräver inmatade värden eller returnerar ett värde använder du värdet `None`.
- Block med inhägnade kod är endast tillåtna i avsnittet [exempel](#structuring-examples) .
- Infogad kod sträcker kan användas i alla stycken.

## <a name="formatting-about_-files"></a>Formatera About_ filer

`About_*` filer bearbetas nu av [pandoc][], i stället för PlatyPS. `About_*` filer formateras för bästa kompatibilitet i alla versioner av PowerShell och med publicerings verktygen.

Grundläggande rikt linjer för formatering:

- Begränsa rader till 80 tecken
- Kodblock och tabeller är begränsade till 76 tecken, eftersom pandoc indrag av fyra blank steg under konverteringen till oformaterad text
- Tabeller måste rymmas inom 76 tecken
  - Radbryt innehållet i celler manuellt över flera rader
  - Använda inledande och avslutande `|` tecken på varje rad
  - Se ett arbets exempel i [about_Comparison_Operators][about-example]
- Använda pandoc specialtecken `\`,`$`och `<`
  - Inom ett sidhuvud – dessa tecken måste föregås av ett inledande `\` tecken eller omges av bakstreck (`` ` ``)
  - I ett stycke ska de här tecknen placeras i kod intervall. Exempel:

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

## <a name="structuring-examples"></a>Strukturerings exempel

I PlatyPS-schemat är **exempel** rubriken en H2-rubrik och varje exempel är ett H3-huvud.

I ett exempel tillåter schemat inte att kodblock separeras med stycken. Det schema som stöds är:

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

Numrera varje exempel och Lägg till en kort rubrik.

Exempel:

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

[Redaktionell check lista](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
