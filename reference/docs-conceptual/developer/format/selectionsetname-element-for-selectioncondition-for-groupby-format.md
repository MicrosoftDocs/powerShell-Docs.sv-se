---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för SelectionCondition för GroupBy (format)
description: SelectionSetName-element för SelectionCondition för GroupBy (format)
ms.openlocfilehash: a4f28c1caba3790718b99f63659cb0cbed8def16
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654988"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>SelectionSetName-element för SelectionCondition för GroupBy (format)

Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) EntrySelectedBy-element för CustomEntry (format) SelectionCondition element for EntrySelectedBy för groupby (format) SelectionSetName element for SelectionCondition

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
|[SelectionCondition-element för EntrySelectedBy för GroupBy (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar. Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).

När det här elementet har angetts kan du inte ange elementet [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) . Mer information om hur du definierar urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[TypeName-element för SelectionCondition för GroupBy (format)](./typename-element-for-selectioncondition-for-groupby-format.md)

[SelectionCondition-element för EntrySelectedBy för GroupBy (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[Definiera valuppsättningar](./defining-selection-sets.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
