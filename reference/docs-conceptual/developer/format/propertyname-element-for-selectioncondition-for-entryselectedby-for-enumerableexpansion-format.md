---
title: PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c0081cb724ccaf1c04241aafa177880d7c0e5dbe
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783474"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)

Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och definitionen används.

Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format) PropertyName-element för SelectionCondition för EntrySelectedBy (format)

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
|[SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.|

## <a name="text-value"></a>Textvärde

Ange .NET-egenskaps namnet.

## <a name="remarks"></a>Kommentarer

Urvals villkoret måste innehålla minst ett egenskaps namn eller ett skript som ska utvärderas, men det går inte att ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[ScriptBlock-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
