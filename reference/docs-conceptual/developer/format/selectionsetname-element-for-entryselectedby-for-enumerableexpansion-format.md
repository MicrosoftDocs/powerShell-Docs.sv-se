---
title: SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8745ef9e6f326c3e8a5dbf185a595bbe93e92414
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785327"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)

Anger den uppsättning av .NET-typer som expanderas av den här definitionen.

Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionSetName-element för EntrySelectedBy (format)

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
|[EntrySelectedBy-element för EnumerableExpansion (format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Definierar de .NET-samlings objekt som ska expanderas av den här definitionen.|

## <a name="text-value"></a>Textvärde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Kommentarer

Varje definition måste ange ett eller flera typnamn, en markerings uppsättning eller ett markerings villkor.

Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer. Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt. Mer information om hur du definierar urvals uppsättningar finns i [definiera uppsättningar av objekt för en vy](./defining-selection-sets.md).

## <a name="see-also"></a>Se även

[Definiera valuppsättningar](./defining-selection-sets.md)

[EntrySelectedBy-element för EnumerableExpansion (format)](./entryselectedby-element-for-enumerableexpansion-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
