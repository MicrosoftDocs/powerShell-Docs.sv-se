---
title: Namn på Element för Visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849268"
---
# <a name="name-element-for-view-format"></a>Name-element för View (format)

Anger namnet som används för att identifiera vyn.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) namn konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Name` element. Endast en `Name` element tillåts för varje vy.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Visa Element (Format)](./view-element-format.md)|Definierar en vy som används för att visa medlemmarna i en eller flera .NET-objekt.|

## <a name="text-value"></a>Textvärde

Ange ett unikt namn för vyn. Det här namnet kan innehålla en referens till typ av vy (till exempel en tabell eller listvy), vilka objekt eller en uppsättning objekt använder vyn, vilka kommandot returnerar objekt eller en kombination av dessa.

## <a name="remarks"></a>Anmärkningar

Mer information om de olika typerna av vyer finns i följande avsnitt: [Tabellen visa](./creating-a-table-view.md), [listvy](./creating-a-list-view.md), [bred vy](./creating-a-wide-view.md), och [anpassad vy](./creating-custom-controls.md).

## <a name="example"></a>Exempel

I följande exempel visas en `View` -element som definierar en tabellvy för den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt. Namnet på vyn är ”tjänst”.

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

[Visa Element (Format)](./view-element-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
