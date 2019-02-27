---
title: SelectionSetName Element för EntrySelectedBy för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846132"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>SelectionSetName-element för EntrySelectedBy för CustomControl för View (format)

Anger en uppsättning med .NET-objekt för posten. Det finns ingen gräns för hur många uppsättningar för val av som kan anges för en post.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för EntrySelectedBy vy (Format) Element för CustomEntry för vyn (Format) SelectionSetName elementet för EntrySelectedBy för CustomEntry (Format)

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
|[EntrySelectedBy Element för CustomEntry för vy (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definierar vilka typer av .NET som använder den här anpassade posten eller villkor som måste finnas för den här posten som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på val av uppsättningen.

## <a name="remarks"></a>Anmärkningar

Varje anpassad kontroll post måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.

Inställningarna används vanligtvis när du vill definiera en grupp med objekt som används i flera vyer. Du kanske vill skapa en tabell och en listvy för samma uppsättning objekt. Mer information om hur du definierar inställningarna finns i [definiera val av anger](./defining-selection-sets.md).

Mer information om komponenter för en anpassad kontroll vy finns i [skapar anpassade kontroller](./creating-custom-controls.md).

## <a name="see-also"></a>Se även

[EntrySelectedBy Element för CustomEntry för vy (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Visa anpassad kontroll](./creating-custom-controls.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
