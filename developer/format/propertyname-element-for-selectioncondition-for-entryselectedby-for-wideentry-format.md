---
title: PropertyName-Element för SelectionCondition för EntrySelectedBy för WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064687"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a>PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)

Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och definitionen används.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format) SelectionCondition elementet för EntrySelectedBy för WideEntry (Format) PropertyName elementet för SelectionCondition för EntrySelectedBy för WideEntry (Format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition Element för EntrySelectedBy för WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Definierar de villkor som måste finnas för den här definitionen som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på .NET-egenskapen.

## <a name="remarks"></a>Anmärkningar

Urvalsvillkoret måste ange minst en egenskapsnamn eller ett skript för att utvärdera, men kan inte ange båda. Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).

Mer information om andra komponenter för en bred vy finns i [bred vy](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[Definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md)

[ScriptBlock Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[SelectionCondition Element för EntrySelectedBy för WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
