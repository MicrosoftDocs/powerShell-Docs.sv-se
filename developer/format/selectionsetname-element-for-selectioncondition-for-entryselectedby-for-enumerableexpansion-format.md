---
title: SelectionSetName Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063868"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)

Anger uppsättningen med .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns är villkoret uppfyllt.

Elementet DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy konfigurationselement för EnumerableExpansion (Format) SelectionCondition elementet för EntrySelectedBy för EnumerableExpansion (Format) SelectionSetName Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `SelectionSetName` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Definierar de villkor som måste finnas för att expandera samlingen objekt av den här definitionen.|

## <a name="text-value"></a>Textvärde

Ange namnet på val av uppsättningen.

## <a name="remarks"></a>Anmärkningar

Urvalsvillkoret kan ange en uppsättning för val av eller en .NET-typ, men kan inte ange båda. Läs mer om hur du använder villkor för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).

Val av som är vanliga grupper av .NET-objekt som kan användas av en vy som definierar filen formatering. Läs mer om att skapa och refererar till val av uppsättningar [definiera val av anger](./defining-selection-sets.md).

## <a name="see-also"></a>Se även

[Definiera inställningarna](./defining-selection-sets.md)

[SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
