---
title: SelectionSetName Element för SelectionCondition för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075587"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>SelectionSetName-element för SelectionCondition för CustomControl för View (format)

Anger uppsättningen med .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns villkoret uppfylls och objektet visas med hjälp av den här kontrollen. Det här elementet används när du definierar en anpassad kontroll vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för EntrySelectedBy vy (Format) Element för CustomEntry för vy (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSetName` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition Element för EntrySelectedBy för anpassad kontroll för vy (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Definierar ett villkor som måste finnas för kontrolldefinition som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på val av uppsättningen.

## <a name="remarks"></a>Anmärkningar

Val av som är vanliga grupper av .NET-objekt som kan användas av en vy som definierar filen formatering. Läs mer om att skapa och refererar till val av uppsättningar [definiera anger av objekt](./defining-selection-sets.md).

Urvalsvillkoret kan ange en uppsättning för val av eller en .NET-typ, men kan inte ange båda. Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[SelectionCondition Element för EntrySelectedBy för anpassad kontroll för vy (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md)

[Definiera inställningarna](./defining-selection-sets.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
