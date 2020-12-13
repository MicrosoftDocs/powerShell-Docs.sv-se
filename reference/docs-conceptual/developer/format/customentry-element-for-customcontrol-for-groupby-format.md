---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntry-element för CustomControl för GroupBy (format)
description: CustomEntry-element för CustomControl för GroupBy (format)
ms.openlocfilehash: 0df2ff9c15308939e6d2552f51e2961bdabc59fb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646075"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>CustomEntry-element för CustomControl för GroupBy (format)

Ger en definition av kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for groupby (format) CustomEntry-element för CustomControl för GroupBy (format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `CustomEntry` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för CustomEntry för GroupBy (format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.|
|[CustomItem-element för CustomEntry för GroupBy (format)](./customitem-element-for-customentry-for-groupby-format.md)|Nödvändigt element.<br /><br /> Definierar hur kontrollen visar data.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntries-element för CustomControl för GroupBy (format)](./customentries-element-for-customcontrol-for-groupby-format.md)|Innehåller definitionerna för kontrollen.|

## <a name="remarks"></a>Kommentarer

## <a name="see-also"></a>Se även

[EntrySelectedBy-element för CustomEntry för GroupBy (format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[CustomItem-element för CustomEntry för GroupBy (format)](./customitem-element-for-customentry-for-groupby-format.md)

[CustomEntries-element för CustomControl för GroupBy (format)](./customentries-element-for-customcontrol-for-groupby-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
