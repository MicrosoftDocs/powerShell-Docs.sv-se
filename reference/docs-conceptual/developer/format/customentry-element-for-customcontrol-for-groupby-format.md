---
title: CustomEntry-element för CustomControl for GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4df8e5b96868b3814c6d84fa329950bb5345ef6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785922"
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
