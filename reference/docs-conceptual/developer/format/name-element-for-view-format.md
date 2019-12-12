---
title: Namn element för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354273"
---
# <a name="name-element-for-view-format"></a>Name-element för View (format)

Anger namnet som används för att identifiera vyn.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) namn element (format)

## <a name="syntax"></a>Syntax

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `Name`-elementet. Endast ett `Name`-element tillåts för varje vy.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Visa element (format)](./view-element-format.md)|Definierar en vy som används för att visa medlemmar i ett eller flera .NET-objekt.|

## <a name="text-value"></a>Textvärde

Ange ett unikt eget namn för vyn. Det här namnet kan innehålla en referens till typen av vy (till exempel en tabellvy eller listvy), vilket objekt eller en uppsättning objekt som använder vyn, vilket kommando returnerar objekten eller en kombination av dessa.

## <a name="remarks"></a>Anmärkningar

Mer information om olika typer av vyer finns i följande avsnitt: [tabellvy](./creating-a-table-view.md), [listvy](./creating-a-list-view.md), [bred vy](./creating-a-wide-view.md)och [anpassad vy](./creating-custom-controls.md).

## <a name="example"></a>Exempel

I följande exempel visas ett `View`-element som definierar en tabellvy för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) . Namnet på vyn är "tjänst".

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

[Visa element (format)](./view-element-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
