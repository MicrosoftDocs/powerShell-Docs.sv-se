---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntry-element för CustomEntries för Controls för View (format)
description: CustomEntry-element för CustomEntries för Controls för View (format)
ms.openlocfilehash: a525b198c8f595e04dc0804d36b5533b94f43c6b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646092"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>CustomEntry-element för CustomEntries för Controls för View (format)

Ger en definition av kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) (format) styr element (format) styr element (format) kontroll element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format)

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
|[EntrySelectedBy-element för CustomEntry för Controls för View (format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.|
|[CustomItem-element för CustomEntry för Controls för View (format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Nödvändigt element.<br /><br /> Definierar hur kontrollen visar data.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntries-element för CustomControl för View (format)](./customentries-element-for-customcontrol-for-view-format.md)|Innehåller definitionerna för kontrollen.|

## <a name="remarks"></a>Kommentarer

## <a name="see-also"></a>Se även

[CustomEntries-element för CustomControl för View (format)](./customentries-element-for-customcontrol-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
