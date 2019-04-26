---
title: PropertyName-Element för SelectionCondition för EntrySelectedBy för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064909"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>PropertyName-element för SelectionCondition för EntrySelectedBy för ListControl (format)

Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och kortet används.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy konfigurationselement för ListEntry (Format) SelectionCondition elementet för EntrySelectedBy för ListEntry (Format) PropertyName elementet för SelectionCondition för EntrySelectedBy för ListEntry (Format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
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
|[SelectionCondition Element för EntrySelectedBy för ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Definierar de villkor som måste finnas för den här posten som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på .NET-egenskapen.

## <a name="remarks"></a>Anmärkningar

Urvalsvillkoret måste ange minst en egenskapsnamn eller ett skriptblock, men kan inte ange båda. Läs mer om hur du använder villkor för val av [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).

Läs mer om andra komponenter i en listvy, [skapar listvyn](./creating-a-list-view.md).

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[Definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md)

[ListEntry Element (Format)](./listentry-element-for-listcontrol-format.md)

[ScriptBlock Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
