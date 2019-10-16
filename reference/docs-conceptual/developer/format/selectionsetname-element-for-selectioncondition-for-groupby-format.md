---
title: SelectionSetName-element för SelectionCondition for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353727"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>SelectionSetName-element för SelectionCondition för GroupBy (format)

Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) EntrySelectedBy-element för CustomEntry för GroupBy (format) SelectionCondition-element för EntrySelectedBy för GroupBy (format) SelectionSetName-element för SelectionCondition för GroupBy (format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `SelectionSetName`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för GroupBy (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.|

## <a name="text-value"></a>Text värde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Anmärkningar

Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar. Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).

När det här elementet har angetts kan du inte ange elementet [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) . Mer information om hur du definierar urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[Elementet TypeName för SelectionCondition för GroupBy (format)](./typename-element-for-selectioncondition-for-groupby-format.md)

[SelectionCondition-element för EntrySelectedBy för GroupBy (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[Definiera urvals uppsättningar](./defining-selection-sets.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
