---
title: SelectionSetName Element för EntrySelectedBy för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846881"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>SelectionSetName-element för EntrySelectedBy för TableControl (format)

Anger en uppsättning .NET skriver att använda den här posten i tabellvyn. Det finns ingen gräns för hur många uppsättningar för val av som kan anges för en post.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName konfigurationselement för EntrySelectedBy för TableRowEntry (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, element i underordnade och överordnade element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definierar vilka typer av .NET som använder den här posten eller villkor som måste finnas för den här posten som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på val av uppsättningen.

## <a name="remarks"></a>Anmärkningar

Inställningarna används vanligtvis när du vill definiera en grupp med objekt som används i flera vyer. Du kanske vill skapa en tabell och en listvy för samma uppsättning objekt. Mer information om hur du definierar inställningarna finns i [definiera anger av objekt som en vy](./defining-selection-sets.md).

Om du anger ett urval som angetts för en post, kan du inte ange ett namn. Läs mer om hur du anger en .NET-typ, [TypeName-Element för EntrySelectedBy för TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).

Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).

## <a name="see-also"></a>Se även

[EntrySelectedBy Element (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Definiera uppsättningar med objekt för en vy](./defining-selection-sets.md)

[Skapa en tabellvy](./creating-a-table-view.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
