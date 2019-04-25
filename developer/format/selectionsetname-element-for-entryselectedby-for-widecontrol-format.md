---
title: SelectionSetName Element för EntrySelectedBy för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064041"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>SelectionSetName-element för EntrySelectedBy för WideControl (format)

Anger en uppsättning med .NET-objekt för definitionen. Definitionen används när en av de här objekten visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format) SelectionSetName elementet för EntrySelectedBy för WideEntry (Format)

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
|[EntrySelectedBy Element för WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Definierar vilka typer av .NET som använder den här wide posten eller villkor som måste finnas för den här posten som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på val av uppsättningen.

## <a name="remarks"></a>Anmärkningar

Varje definition måste ange ett namn, val av set eller urvalsvillkoret.

Inställningarna används vanligtvis när du vill definiera en grupp med objekt som används i flera vyer. Du kanske vill skapa en tabell och en listvy för samma uppsättning objekt. Mer information om hur du definierar inställningarna finns i [definiera anger av objekt för en vy](./defining-selection-sets.md).

Mer information om andra komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[Definiera inställningarna](./defining-selection-sets.md)

[EntrySelectedBy Element för WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
