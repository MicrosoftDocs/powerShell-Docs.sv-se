---
title: EntrySelectedBy Element för CustomEntry för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066285"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>EntrySelectedBy-element för CustomEntry för CustomControl för View (format)

Definierar vilka typer av .NET som använder den här anpassade posten eller villkor som måste finnas för den här posten som ska användas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för EntrySelectedBy vy (Format) Element för CustomEntry för vy (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EntrySelectedBy` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition Element för EntrySelectedBy för CustomEntry (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Valfritt element.<br /><br /> Definierar de villkor som måste finnas för den här definitionen som ska användas.|
|[SelectionSetName Element för EntrySelectedBy för CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger en uppsättning med .NET-typer som använder den här definitionen av vyn kontroll.|
|[TypeName-Element för EntrySelectedBy för CustomEntry (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger ett .NET-typ som använder den här definitionen av vyn kontroll.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry Element för CustomEntries för vy (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Definierar de kontroller som används av specifika .NET-objekt.|

## <a name="remarks"></a>Anmärkningar

Du måste ange minst en typ, val av set eller urvalsvillkoret efter en post. Det finns ingen högsta gräns för antalet underordnade element som du kan använda.

Val av villkor används för att definiera ett villkor som måste finnas för posten som ska användas, till exempel när ett objekt har en specifik egenskap eller när en specifik egenskapsvärdet eller skript som utvärderas till `true`. Mer information om val av villkor finns i [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).

Mer information om komponenter för en anpassad kontroll vy finns i [anpassad kontroll vy](./creating-custom-controls.md).

## <a name="see-also"></a>Se även

[SelectionCondition Element för EntrySelectedBy för CustomEntry (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[SelectionSetName Element för EntrySelectedBy för CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[TypeName-Element för EntrySelectedBy för CustomEntry (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[CustomEntry Element för CustomEntries för vy (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Visa anpassad kontroll](./creating-custom-controls.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
