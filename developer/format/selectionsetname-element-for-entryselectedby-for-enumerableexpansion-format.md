---
title: SelectionSetName Element för EntrySelectedBy för EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076267"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)

Anger uppsättningen med .NET-typer som byggs med den här definitionen.

Elementet (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy konfigurationselement för EnumerableExpansion (Format) SelectionSetName elementet för EntrySelectedBy för EnumerableExpansion (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSetName` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Definierar de .NET samling objekt som byggs med den här definitionen.|

## <a name="text-value"></a>Textvärde

Ange namnet på val av uppsättningen.

## <a name="remarks"></a>Anmärkningar

Varje definition måste ange en eller flera namn, en eller ett val av villkor.

Inställningarna används vanligtvis när du vill definiera en grupp med objekt som används i flera vyer. Du kanske vill skapa en tabell och en listvy för samma uppsättning objekt. Mer information om hur du definierar inställningarna finns i [definiera anger av objekt för en vy](./defining-selection-sets.md).

## <a name="see-also"></a>Se även

[Definiera inställningarna](./defining-selection-sets.md)

[EntrySelectedBy Element för EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
