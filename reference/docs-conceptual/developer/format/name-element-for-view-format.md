---
ms.date: 09/13/2016
ms.topic: reference
title: Name-element för View (format)
description: Name-element för View (format)
ms.openlocfilehash: 5781bcdf7a0e1eb5e9c7e97bb6acc0a383dc0262
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666473"
---
# <a name="name-element-for-view-format"></a>Name-element för View (format)

Anger namnet som används för att identifiera vyn.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) namn element (format)

## <a name="syntax"></a>Syntax

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `Name` elementets överordnade element. Endast ett- `Name` element tillåts för varje vy.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[View-element (format)](./view-element-format.md)|Definierar en vy som används för att visa medlemmar i ett eller flera .NET-objekt.|

## <a name="text-value"></a>Textvärde

Ange ett unikt eget namn för vyn. Det här namnet kan innehålla en referens till typen av vy (till exempel en tabellvy eller listvy), vilket objekt eller en uppsättning objekt som använder vyn, vilket kommando returnerar objekten eller en kombination av dessa.

## <a name="remarks"></a>Kommentarer

Mer information om olika typer av vyer finns i följande avsnitt: [tabellvy](./creating-a-table-view.md), [listvy](./creating-a-list-view.md), [bred vy](./creating-a-wide-view.md)och [anpassad vy](./creating-custom-controls.md).

## <a name="example"></a>Exempel

I följande exempel visas ett- `View` element som definierar en tabellvy för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) . Namnet på vyn är "tjänst".

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[Skapa en tabellvy](./creating-a-table-view.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Skapa anpassade kontroller](./creating-custom-controls.md)

[View-element (format)](./view-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
