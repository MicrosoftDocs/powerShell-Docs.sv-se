---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för SelectionCondition för Controls för Configuration (format)
description: SelectionSetName-element för SelectionCondition för Controls för Configuration (format)
ms.openlocfilehash: 4177aace5a6a9374900e7339167c69b531c1e2e7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651655"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a>SelectionSetName-element för SelectionCondition för Controls för Configuration (format)

Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för kontroll för CustomControl-element (format) för Control för Configuration (format) CustomEntries-element för CustomControl för Controls (format) CustomEntry-element för CustomControl for Controls for Configuration (format) EntrySelectedBy-elementet för CustomEntry for Controls for Configuration (format) SelectionCondition element for EntrySelectedBy for Controls for Configuration (format) SelectionSetName element for SelectionCondition for Controls for Configuration (format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar. Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[Definiera valuppsättningar](./defining-selection-sets.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
