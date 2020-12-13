---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för SelectionCondition för CustomControl för View (format)
description: SelectionSetName-element för SelectionCondition för CustomControl för View (format)
ms.openlocfilehash: 839032048739e529057d7066fb3bc6aa2fbc5037
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651605"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>SelectionSetName-element för SelectionCondition för CustomControl för View (format)

Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med den här kontrollen. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) EntrySelectedBy-element för CustomEntry för View (format)

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
|[SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar. Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[Definiera valuppsättningar](./defining-selection-sets.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
