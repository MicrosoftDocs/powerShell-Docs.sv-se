---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för GroupBy (format)
description: PropertyName-element för GroupBy (format)
ms.openlocfilehash: 44351c46ff2386f967644fef4f423b3858dc1619
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666152"
---
# <a name="propertyname-element-for-groupby-format"></a>PropertyName-element för GroupBy (format)

Anger den .NET-egenskap som startar en ny grupp när dess värde ändras.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) PropertyName-element för GroupBy (format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[GroupBy-element för View (format)](./groupby-element-for-view-format.md)|Definierar hur en grupp med .NET-objekt visas.|

## <a name="text-value"></a>Textvärde

Ange .NET-egenskaps namnet.

## <a name="remarks"></a>Kommentarer

Windows PowerShell startar en ny grupp när värdet för den här egenskapen ändras.

När det här elementet har angetts kan du inte ange [script block](./scriptblock-element-for-groupby-format.md) -elementet för att starta en ny grupp.

## <a name="example"></a>Exempel

I följande exempel visas hur du startar en ny grupp när värdet för en egenskap ändras.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Ett exempel på en hel format fil som innehåller det här elementet finns i [wide View (groupby)](./wide-view-groupby.md).

## <a name="see-also"></a>Se även

[GroupBy-element för View (format)](./groupby-element-for-view-format.md)

[ScriptBlock-element för GroupBy (format)](./scriptblock-element-for-groupby-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
