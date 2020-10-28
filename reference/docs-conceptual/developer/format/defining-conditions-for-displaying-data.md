---
ms.date: 09/13/2016
ms.topic: reference
title: Definiera villkor för datavisning
description: Definiera villkor för datavisning
ms.openlocfilehash: 9a8b7a618da8c64de978c13b527435a2d7793677
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660317"
---
# <a name="defining-conditions-for-displaying-data"></a>Definiera villkor för datavisning

När du definierar vilka data som visas i en vy eller en kontroll kan du ange ett villkor som måste finnas för att de data som ska visas. Villkoret kan utlösas av en speciell egenskap eller när ett skript eller egenskaps värde utvärderas till `true` . När urvals villkoret är uppfyllt används definitionen för vyn eller kontrollen.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Ange ett urvals villkor för en definition

När du skapar en definition för en vy eller kontroll, `EntrySelectedBy` används elementet för att ange vilka objekt som ska använda definitionen eller vilket villkor som måste finnas för att definitionen ska kunna användas. Villkoret anges av `SelectionCondition` elementet.

I följande exempel anges ett urvals villkor för en definition av en tabellvy. I det här exemplet används definitionen endast när det angivna skriptet utvärderas till `true` .

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

Du kan också ange när ett objekt i en listvy eller kontroll ska användas genom att inkludera `ItemSelectionCondition` elementet i objekt definitionen. I följande exempel anges ett urvals villkor för ett objekt i en listvy. I det här exemplet används objektet bara när skriptet utvärderas till `true` .

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

  - [SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

  - [SelectionCondition-element för EntrySelectedBy för Controls för View (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- Följande element anger urvals villkoret för att expandera samlings objekt:

  - [SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Följande element anger urvals villkoret för att visa en ny grupp med data:

  - [SelectionCondition-element för EntrySelectedBy för GroupBy (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- Följande element anger ett objekt urvals villkor för en listvy:

  - [ItemSelectionCondition-element för ListItem för ListControl (format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Följande element anger ett objekt urvals villkor för kontroller:

  - [ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

  - [ItemSelectionCondition-element för ExpressionBinding för Controls för View (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

  - [ItemSelectionCondition-element för ExpressionBinding för CustomControl (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Se även

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
