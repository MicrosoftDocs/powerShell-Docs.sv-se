---
title: EntrySelectedBy Element för CustomEntry för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851585"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>EntrySelectedBy-element för CustomEntry för GroupBy (format)

Definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas. Det här elementet används när du definierar hur en ny grupp med objekt visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) EntrySelectedBy elementet för CustomEntry för GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `EntrySelectedBy` element. Du måste ange minst en typ, val av set eller urvalsvillkoret definieras. Det finns ingen högsta gräns för antalet underordnade element som du kan använda.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition Element för EntrySelectedBy för GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar de villkor som måste finnas för den här definitionen som ska användas.|
|[SelectionSetName Element för EntrySelectedBy för GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|Valfritt element.<br /><br /> Anger en uppsättning med .NET-typer som använder den här definitionen för kontrollen.|
|[TypeName-Element för EntrySelectedBy för GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md)|Valfritt element.<br /><br /> Anger ett .NET-typ som använder den här definitionen för kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry Element för anpassad kontroll för GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Innehåller en definition av kontrollen.|

## <a name="remarks"></a>Anmärkningar

Val av villkor används för att definiera ett villkor som måste finnas för definitionen som ska användas, till exempel när ett objekt har en specifik egenskap eller när en specifik egenskapsvärdet eller skript som utvärderas till `true`. Mer information om val av villkor finns i [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[SelectionCondition Element för EntrySelectedBy för GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[SelectionSetName Element för EntrySelectedBy för GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[TypeName-Element för EntrySelectedBy för GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md)

[CustomEntry Element för CustomEntries för kontroller för att visa (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
