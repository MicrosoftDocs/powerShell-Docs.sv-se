---
title: PropertyName-element för SelectionCondition för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 251fc129896cfa4a6255330e23854b014675ac5f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780822"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a>PropertyName-element för SelectionCondition för Controls för View (format)

Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och posten används. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) styr element (format) styr element (format) styr element (format) kontroll element för Controls for View (format) CustomControl-element för kontroll för kontroller för View (format) CustomEntries-element för CustomControl för kontroller (format) CustomEntry-element för CustomEntries for Controls for View (format) EntrySelectedBy-element för CustomEntry for Controls for View (format) SelectionCondition-element for EntrySelectedBy for Controls for View (format) PropertyName-element för SelectionCondition för Controls for View (format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för Controls för View (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.|

## <a name="text-value"></a>Textvärde

Ange .NET-egenskaps namnet.

## <a name="remarks"></a>Kommentarer

Urvals villkoret måste ange minst ett egenskaps namn eller ett skript, men kan inte ange båda. Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[SelectionCondition-element för EntrySelectedBy för Controls för View (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
