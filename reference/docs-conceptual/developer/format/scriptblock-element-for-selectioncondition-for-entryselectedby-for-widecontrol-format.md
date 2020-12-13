---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för SelectionCondition för EntrySelectedBy för WideControl (format)
description: ScriptBlock-element för SelectionCondition för EntrySelectedBy för WideControl (format)
ms.openlocfilehash: 53d3eba9d453dbcc96afbe8f81a16b61573f2874
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651965"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>ScriptBlock-element för SelectionCondition för EntrySelectedBy för WideControl (format)

Anger det skript som utlöser villkoret. När det här skriptet utvärderas `true` , uppfylls villkoret och den breda post definitionen används.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition element for EntrySelectedBy for WideEntry (format) script block-element för SelectionCondition för EntrySelectedBy (format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange det skript som utvärderas.

## <a name="remarks"></a>Kommentarer

Urvals villkoret måste innehålla minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

Mer information om andra komponenter i en bred vy finns i [wide View](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[SelectionCondition-element för EntrySelectedBy för WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
