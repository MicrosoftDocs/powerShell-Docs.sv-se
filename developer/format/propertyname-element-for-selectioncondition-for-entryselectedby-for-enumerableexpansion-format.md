---
title: PropertyName-Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064960"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)

Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och definitionen används.

Elementet (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy konfigurationselement för EnumerableExpansion (Format) SelectionCondition elementet för EntrySelectedBy för EnumerableExpansion (Format) PropertyName Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)

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
|[SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Definierar de villkor som måste finnas för att expandera samlingen objekt av den här definitionen.|

## <a name="text-value"></a>Textvärde

Ange namnet på .NET-egenskapen.

## <a name="remarks"></a>Anmärkningar

Urvalsvillkoret måste ange minst en egenskapsnamn eller ett skript för att utvärdera, men kan inte ange båda. Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[Definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md)

[ScriptBlock Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
