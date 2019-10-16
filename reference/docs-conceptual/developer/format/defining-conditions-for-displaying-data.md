---
title: Definiera villkor för att visa data | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355155"
---
# <a name="defining-conditions-for-displaying-data"></a>Definiera villkor för datavisning

När du definierar vilka data som visas i en vy eller en kontroll kan du ange ett villkor som måste finnas för att de data som ska visas. Villkoret kan utlösas av en speciell egenskap, eller när ett skript eller egenskaps värde utvärderas till `true`. När urvals villkoret är uppfyllt används definitionen för vyn eller kontrollen.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Ange ett urvals villkor för en definition

När du skapar en definition för en vy eller kontroll, används `EntrySelectedBy`-elementet för att ange vilka objekt som ska använda definitionen eller vilket villkor som måste finnas för att definitionen ska kunna användas. Villkoret anges av elementet `SelectionCondition`.

I följande exempel anges ett urvals villkor för en definition av en tabellvy. I det här exemplet används definitionen endast när det angivna skriptet utvärderas till `true`.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

Det finns ingen gräns för antalet urvals villkor som du kan ange för en definition av en vy eller kontroll. De enda kraven är följande:

- Markerings villkoret måste ange ett egenskaps namn eller skript för att utlösa villkoret, men det går inte att ange båda.

- Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.

## <a name="specifying-a-selection-condition-for-an-item"></a>Ange ett urvals villkor för ett objekt

Du kan också ange när ett objekt i en listvy eller kontroll ska användas genom att inkludera elementet `ItemSelectionCondition` i objekt definitionen. I följande exempel anges ett urvals villkor för ett objekt i en listvy. I det här exemplet används objektet bara när skriptet utvärderas till `true`.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

Du kan bara ange ett markerings villkor för ett objekt. Villkoret måste ange ett egenskaps namn eller skript för att utlösa villkoret, men det går inte att ange båda.

## <a name="xml-elements"></a>XML-element

 Följande XML-element används för att skapa ett urvals villkor.

- Följande element anger urvals villkor för visnings definitioner:

    - [SelectionCondition-element för EntrySelectedBy för TableControl (format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionCondition-element för EntrySelectedBy för ListControl (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [SelectionCondition-element för EntrySelectedBy för WideControl (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [SelectionCondition-element för EntrySelectedBy för CustomControl (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Följande element anger urvals villkor för vanliga och Visa kontroll definitioner:

    - [SelectionCondition-element för EntrySelectedBy för kontroller för konfiguration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [SelectionCondition-element för EntrySelectedBy för kontroller för vy (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- Följande element anger urvals villkoret för att expandera samlings objekt:

    - [SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Följande element anger urvals villkoret för att visa en ny grupp med data:

    - [SelectionCondition-element för EntrySelectedBy för GroupBy (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- Följande element anger ett objekt urvals villkor för en listvy:

    - [ItemSelectionCondition-element för ListItem för ListControl (format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Följande element anger ett objekt urvals villkor för kontroller:

    - [ItemSelectionCondition-element för ExpressionBinding för kontroller för konfiguration (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [ItemSelectionCondition-element för ExpressionBinding för CustomControl (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Se även

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)