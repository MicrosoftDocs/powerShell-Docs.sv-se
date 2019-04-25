---
title: SelectionSetName Element för EntrySelectedBy för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075570"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a>SelectionSetName-element för EntrySelectedBy för ListControl (format)

Anger en uppsättning med .NET-objekt för posten. Det finns ingen gräns för hur många uppsättningar för val av som kan anges för en post.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy konfigurationselement för ListEntry (Format) SelectionSetName elementet för EntrySelectedBy för ListEntry (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `SelectionSetName` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Definierar vilka typer av .NET som använder den här posten eller villkor som måste finnas för den här posten som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på val av uppsättningen.

## <a name="remarks"></a>Anmärkningar

Varje listpost måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.

Inställningarna används vanligtvis när du vill definiera en grupp med objekt som används i flera vyer. Du kanske vill skapa en tabell och en listvy för samma uppsättning objekt. Mer information om hur du definierar inställningarna finns i [definiera anger av objekt som en vy](./defining-selection-sets.md).

Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du anger ett urval som angetts för en post av en listvy.

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[EntrySelectedBy Element för ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
