---
title: Definiera villkor för att visa Data | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066336"
---
# <a name="defining-conditions-for-displaying-data"></a>Definiera villkor för datavisning

När du definierar vilka data som visas genom en vy eller en kontroll måste ange du ett villkor som måste finnas för data som ska visas. Villkoret kan utlösas av en specifik egenskap, eller när ett skript eller egenskapsvärdet utvärderas till `true`. När val av villkor är uppfyllt, används definitionen av vyn eller kontroll.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Ange ett villkor för val av en definition

När du skapar en definition för en vy eller en kontroll, den `EntrySelectedBy` elementet används för att ange vilka objekt använder definitionen eller vilket villkor som måste finnas för definitionen som ska användas. Villkoret har angetts av den `SelectionCondition` element.

I exemplet nedan anges ett val av villkor för en definition av en tabellvy. I det här exemplet definitionen används endast när det angivna skriptet utvärderas till `true`.

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

Det finns ingen gräns för hur många val av villkor som du kan ange en definition av en vy eller kontroll. De enda kraven är följande:

- Urvalsvillkoret måste ange ett egenskapsnamn och skript för att utlösa villkoret, men kan inte ange båda.

- Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.

## <a name="specifying-a-selection-condition-for-an-item"></a>Ange ett villkor för val av för ett objekt

Du kan också ange när ett objekt av en listvy eller kontroll används genom att inkludera den `ItemSelectionCondition` element i definitionen av objektet. I exemplet nedan anges ett val av villkor för objekt av en listvy. I det här exemplet artikeln används bara när skriptet har utvärderats till `true`.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

Du kan ange endast en urvalsvillkoret för ett objekt. Och villkoret måste ange ett egenskapsnamn och skript för att utlösa villkoret, men kan inte ange båda.

## <a name="xml-elements"></a>XML-element

 Följande XML-element används för att skapa ett val av villkor.

- Följande element anger val av villkor för vydefinitioner:

    - [SelectionCondition Element för EntrySelectedBy för TableControl (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionCondition Element för EntrySelectedBy för ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [SelectionCondition Element för EntrySelectedBy för WideControl (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [SelectionCondition Element för EntrySelectedBy för anpassad kontroll (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Följande element anger val av villkor för gemensamma och visa styra definitioner:

    - [SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [SelectionCondition Element för EntrySelectedBy för kontroller för att visa (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- Följande element anger urvalsvillkoret för att expandera samlingen objekt:

    - [SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Följande element anger urvalsvillkoret för att visa en ny grupp av data:

    - [SelectionCondition Element för EntrySelectedBy för GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- Följande element anger ett villkor för val av objekt för en listvy:

    - [ItemSelectionCondition Element för ListItem för ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Följande element ange ett villkor för val av objekt för kontroller:

    - [ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [ItemSelectionCondition Element för ExpressionBinding för kontroller för att visa (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [ItemSelectionCondition Element för ExpressionBinding för anpassad kontroll (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Se även

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
