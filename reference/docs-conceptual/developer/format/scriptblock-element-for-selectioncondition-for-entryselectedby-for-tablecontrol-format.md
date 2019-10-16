---
title: Script block-element för SelectionCondition för EntrySelectedBy för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358920"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>ScriptBlock-element för SelectionCondition för EntrySelectedBy för TableControl (format)

Anger det skript block som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och tabell posten används.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition-element för EntrySelectedBy för TableRowEntry (format) script block-elementet för SelectionCondition för EntrySelectedBy för TableRowEntry (format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `ScriptBlock`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Definierar det villkor som måste finnas för att den här tabell posten ska kunna användas.|

## <a name="text-value"></a>Text värde

Ange det skript som utvärderas.

## <a name="remarks"></a>Anmärkningar

Markerings villkoret måste innehålla minst ett skript block eller egenskaps namn, men kan inte ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
