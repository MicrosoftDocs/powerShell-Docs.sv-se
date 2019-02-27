---
title: EntrySelectedBy Element för WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846097"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>EntrySelectedBy-element för WideEntry (format)

Definierar vilka typer av .NET som använder den här definitionen av bred vy eller ett villkor som måste finnas för den här definitionen som ska användas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format)

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
|[SelectionCondition Element för EntrySelectedBy för WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Valfritt element.<br /><br /> Definierar de villkor som måste finnas för den här definitionen för bred vy som ska användas.|
|[SelectionSetName Element för EntrySelectedBy för WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Valfritt element.<br /><br /> Anger en uppsättning med .NET-typer som använder den här definitionen för bred vy.|
|[TypeName-Element för EntrySelectedBy för WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Valfritt element.<br /><br /> Anger ett .NET-typ som använder den här definitionen för bred vy.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideEntry Element (Format)](./wideentry-element-for-widecontrol-format.md)|Innehåller en definition av bred vy.|

## <a name="remarks"></a>Anmärkningar

Du måste ange minst en typ, val av set eller urvalsvillkoret för en bred vy-definition. Det finns ingen högsta gräns för antalet underordnade element som du kan använda.

Val av villkor används för att definiera ett villkor som måste finnas för definitionen som ska användas, till exempel när ett objekt har en specifik egenskap eller som en specifik egenskapsvärdet eller skriptvärdet utvärderas till `true`. Mer information om val av villkor finns i [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).

Mer information om andra komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[WideEntry Element (Format)](./wideentry-element-for-widecontrol-format.md)

[SelectionCondition Element för EntrySelectedBy för WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName Element för EntrySelectedBy för WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[TypeName-Element för EntrySelectedBy för WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
