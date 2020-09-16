---
title: SelectionSetName-element för EntrySelectedBy för kontroll av konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 72072d8d13e6ca22afdb9bca2e0237d29ba0594f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787571"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a>SelectionSetName-element för EntrySelectedBy för Controls för Configuration (format)

Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för Controls (format) EntrySelectedBy-element för CustomEntry för Controls (format) SelectionSetName-element för EntrySelectedBy för Controls (format)-element

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inget

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Varje kontroll definition måste ha minst ett typ namn, en markerings uppsättning eller ett urvals villkor definierat.

Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer. Mer information om hur du definierar urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).

## <a name="see-also"></a>Se även

[EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
