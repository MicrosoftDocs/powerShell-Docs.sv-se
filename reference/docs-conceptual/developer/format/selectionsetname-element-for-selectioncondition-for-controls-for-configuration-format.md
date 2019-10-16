---
title: SelectionSetName-element för SelectionCondition för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358842"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a>SelectionSetName-element för SelectionCondition för Controls för Configuration (format)

Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för kontroller för Konfiguration (format) CustomEntry-element för CustomControl for Controls for Configuration (format) EntrySelectedBy element for CustomEntry for Controls for Configuration (format) SelectionCondition element for EntrySelectedBy for Controls for Konfiguration (format) SelectionSetName-element för SelectionCondition för kontroller för konfiguration (format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `SelectionSetName`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för kontroller för konfiguration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.|

## <a name="text-value"></a>Text värde

Ange namnet på urvals uppsättningen.

## <a name="remarks"></a>Anmärkningar

Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar. Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[SelectionCondition-element för EntrySelectedBy för kontroller för konfiguration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[Definiera urvals uppsättningar](./defining-selection-sets.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
