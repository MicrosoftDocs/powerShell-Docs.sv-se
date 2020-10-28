---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)
description: EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)
ms.openlocfilehash: fadcdb69ac71269ba2f2f80baf139bb363d4acba
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666679"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)

Definierar de .NET-typer som använder definitionen av den gemensamma kontrollen eller villkoret som måste finnas för att den här kontrollen ska kunna användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för Controls (format) EntrySelectedBy-element för CustomEntry för kontroll av konfiguration (format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den gemensamma kontroll definitionen ska kunna användas.|
|[SelectionSetName-element för EntrySelectedBy för Controls för Configuration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger en uppsättning av .NET-typer som använder den här definitionen av den gemensamma kontrollen.|
|[TypeName-element för EntrySelectedBy för Controls för Configuration (format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som använder den här definitionen av den gemensamma kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomControl för Controls för Configuration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Ger en definition av den gemensamma kontrollen.|

## <a name="remarks"></a>Kommentarer

Varje definition måste minst ha minst en .NET-typ, markerings uppsättning eller ett urvals villkor angivet. Det finns ingen övre gräns för antalet typer, markerings uppsättningar eller markerings villkor som du kan ange.

## <a name="see-also"></a>Se även

[SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[SelectionSetName-element för EntrySelectedBy för Controls för Configuration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[CustomEntry-element för CustomControl för Controls för Configuration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[TypeName-element för EntrySelectedBy för Controls för Configuration (format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
