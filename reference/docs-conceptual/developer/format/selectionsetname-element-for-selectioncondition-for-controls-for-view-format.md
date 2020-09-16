---
title: SelectionSetName-element för SelectionCondition för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0feb23f860487952344680f75ee674e9e0e6dcc6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787537"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a>SelectionSetName-element för SelectionCondition för Controls för View (format)

Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med den här kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) styr element (format) styr element (format) styr element (format) kontroll element för Controls for View (format) CustomControl-element för kontroll för kontroller för View (format) CustomEntries-element för CustomControl för kontroller (format) CustomEntry-element för CustomEntries for Controls for View (format) EntrySelectedBy-element för CustomEntry for Controls for View (format) SelectionCondition-elementet for EntrySelectedBy for Controls for View (format) SelectionSetName element for SelectionCondition for Controls for View (format)

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
|[SelectionCondition-element för EntrySelectedBy för Controls för View (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar. Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).

Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[SelectionCondition-element för EntrySelectedBy för Controls för View (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[Definiera valuppsättningar](./defining-selection-sets.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
