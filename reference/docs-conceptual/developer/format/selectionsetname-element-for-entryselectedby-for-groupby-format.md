---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för EntrySelectedBy för GroupBy (format)
description: SelectionSetName-element för EntrySelectedBy för GroupBy (format)
ms.openlocfilehash: 7ebe5d884061243c8b4af196788187d84c15a92e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651855"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a>SelectionSetName-element för EntrySelectedBy för GroupBy (format)

Anger en uppsättning .NET-objekt för List posten. Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) EntrySelectedBy-element för CustomEntry (format)

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
|[EntrySelectedBy-element för CustomEntry för GroupBy (format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Definierar de .NET-typer som använder den här anpassade posten eller det villkor som måste finnas för att den här posten ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Varje definition av anpassad kontroll måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.

Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer. Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt. Mer information om hur du definierar urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).

Mer information om komponenterna i en anpassad kontroll vy finns i [skapa anpassade kontroller](./creating-custom-controls.md).

## <a name="see-also"></a>Se även

[EntrySelectedBy-element för CustomEntry för GroupBy (format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Skapa anpassade kontroller](./creating-custom-controls.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
