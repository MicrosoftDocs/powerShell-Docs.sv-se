---
title: SelectionSetName Element för EntrySelectedBy för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848813"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a>SelectionSetName-element för EntrySelectedBy för GroupBy (format)

Anger en uppsättning med .NET-objekt för posten. Det finns ingen gräns för hur många uppsättningar för val av som kan anges för en post. Det här elementet används när du definierar hur en ny grupp med objekt visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) EntrySelectedBy elementet för CustomEntry för GroupBy (Format) SelectionSetName elementet för EntrySelectedBy för GroupBy (Format)

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
|[EntrySelectedBy Element för CustomEntry för GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Definierar vilka typer av .NET som använder den här anpassade posten eller villkor som måste finnas för den här posten som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på val av uppsättningen.

## <a name="remarks"></a>Anmärkningar

Varje anpassad kontrolldefinition måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.

Inställningarna används vanligtvis när du vill definiera en grupp med objekt som används i flera vyer. Du kanske exempelvis vill skapa en tabell och en listvy för samma uppsättning objekt. Mer information om hur du definierar inställningarna finns i [definiera val av anger](./defining-selection-sets.md).

Mer information om komponenter för en anpassad kontroll vy finns i [skapar anpassade kontroller](./creating-custom-controls.md).

## <a name="see-also"></a>Se även

[EntrySelectedBy Element för CustomEntry för GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Skapa anpassade kontroller](./creating-custom-controls.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
