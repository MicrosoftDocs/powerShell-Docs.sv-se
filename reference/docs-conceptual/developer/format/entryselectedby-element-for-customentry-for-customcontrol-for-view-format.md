---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy-element för CustomEntry för CustomControl för View (format)
description: EntrySelectedBy-element för CustomEntry för CustomControl för View (format)
ms.openlocfilehash: 4821f22560f35034f90d018e5a109004f331441f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655354"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>EntrySelectedBy-element för CustomEntry för CustomControl för View (format)

Definierar de .NET-typer som använder den här anpassade posten eller det villkor som måste finnas för att den här posten ska kunna användas.

Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) EntrySelectedBy-element för CustomEntry för View (format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
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
|[SelectionCondition-element för EntrySelectedBy för CustomEntry (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.|
|[SelectionSetName-element för EntrySelectedBy för CustomEntry (format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen View.|
|[Elementet TypeName för EntrySelectedBy för CustomEntry (format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som använder den här definitionen av kontroll visningen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomEntries för vy (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Definierar de kontroller som används av vissa .NET-objekt.|

## <a name="remarks"></a>Kommentarer

Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en post. Det finns ingen övre gräns för antalet underordnade element som du kan använda.

Urvals villkor används för att definiera ett villkor som måste finnas för att posten ska kunna användas, till exempel när ett objekt har en speciell egenskap eller när ett angivet egenskaps värde eller skript utvärderas till `true` . Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).

Mer information om komponenterna i en anpassad kontroll visas i [vyn anpassad kontroll](./creating-custom-controls.md).

## <a name="see-also"></a>Se även

[SelectionCondition-element för EntrySelectedBy för CustomEntry (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[SelectionSetName-element för EntrySelectedBy för CustomEntry (format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[Elementet TypeName för EntrySelectedBy för CustomEntry (format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[CustomEntry-element för CustomEntries för vy (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Vy för anpassad kontroll](./creating-custom-controls.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
