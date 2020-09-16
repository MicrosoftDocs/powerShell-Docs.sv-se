---
title: SelectionSetName-element för EntrySelectedBy för CustomControl för View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3728a1886d5406b8fa4888125d1c031d0f9b1b03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785310"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>SelectionSetName-element för EntrySelectedBy för CustomControl för View (format)

Anger en uppsättning .NET-objekt för List posten. Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.

Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) EntrySelectedBy-element för CustomEntry för View (format) SelectionSetName-element för EntrySelectedBy för CustomEntry (format)

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
|[EntrySelectedBy-element för CustomEntry för vy (format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definierar de .NET-typer som använder den här anpassade posten eller det villkor som måste finnas för att den här posten ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Varje anpassad kontroll post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.

Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer. Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt. Mer information om hur du definierar urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).

Mer information om komponenterna i en anpassad kontroll vy finns i [skapa anpassade kontroller](./creating-custom-controls.md).

## <a name="see-also"></a>Se även

[EntrySelectedBy-element för CustomEntry för vy (format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Vy för anpassad kontroll](./creating-custom-controls.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
