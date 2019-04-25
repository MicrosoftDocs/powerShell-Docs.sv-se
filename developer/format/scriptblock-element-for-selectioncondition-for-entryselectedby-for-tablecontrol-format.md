---
title: ScriptBlock Element för SelectionCondition för EntrySelectedBy för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076352"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>ScriptBlock-element för SelectionCondition för EntrySelectedBy för TableControl (format)

Anger skriptblocket som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och tabellposten används.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy konfigurationselement för TableRowEntry (Format) SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format) ScriptBlock elementet för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Definierar de villkor som måste finnas för den här tabellposten som ska användas.|

## <a name="text-value"></a>Textvärde

Ange det skript som ska utvärderas.

## <a name="remarks"></a>Anmärkningar

Urvalsvillkoret måste ange minst en blockera eller egenskapen skriptnamn, men kan inte ange båda. Läs mer om hur du använder villkor för val av [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).

Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[Definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md)

[PropertyName-Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
