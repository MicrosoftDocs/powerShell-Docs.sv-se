---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för SelectionCondition för EntrySelectedBy för ListControl (format)
description: ScriptBlock-element för SelectionCondition för EntrySelectedBy för ListControl (format)
ms.openlocfilehash: ec7691358d0ff3758411317a349221e1704a1895
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659905"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>ScriptBlock-element för SelectionCondition för EntrySelectedBy för ListControl (format)

Anger det skript som utlöser villkoret. När det här skriptet utvärderas `true` , uppfylls villkoret och list posten används.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format) EntrySelectedBy-element för ListEntry (format) SelectionCondition element for EntrySelectedBy for ListEntry (format) script block-element för SelectionCondition för EntrySelectedBy (format)

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
|[SelectionCondition-element för EntrySelectedBy för ListEntry (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Definierar det villkor som måste finnas för att den här List posten ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange det skript som utvärderas.

## <a name="remarks"></a>Kommentarer

Urvals villkoret måste ange minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda. (Mer information om hur urvals villkor kan användas finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).)

Mer information om de andra komponenterna i en listvy finns i [listvyn](./creating-a-list-view.md).

## <a name="see-also"></a>Se även

[ListEntry-element (format)](./listentry-element-for-listcontrol-format.md)

[PropertyName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[SelectionCondition-element för EntrySelectedBy för ListEntry (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Listvy](./creating-a-list-view.md)

[Definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md)

[Skriva en Windows PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
