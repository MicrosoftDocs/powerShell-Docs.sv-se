---
title: ViewDefinitions-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353419"
---
# <a name="viewdefinitions-element-format"></a>ViewDefinitions-element (format)

Definierar de vyer som används för att visa .NET-objekt. Dessa vyer kan visa egenskaper och skript värden för ett objekt i tabell format, list format, brett format och anpassat kontroll format.

Konfigurations element (format) ViewDefinitions-element (format-XML)

## <a name="syntax"></a>Syntax

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `ViewDefinitions`-elementet. Det finns ingen gräns för antalet vyer som kan definieras i en formateringsinformation och de kan läggas till i vilken ordning som helst.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Visa element (format)](./view-element-format.md)|Definierar en vy som används för att visa ett eller flera .NET-objekt.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Konfigurations element (format)](./configuration-element-format.md)|Representerar det översta elementet i en textfil.|

## <a name="remarks"></a>Anmärkningar

Mer information om komponenterna i de olika typerna av vyer finns i följande avsnitt:

- [Skapa en tabellvy](./creating-a-table-view.md)

- [Skapa en listvy](./creating-a-list-view.md)

- [Skapa en bred vy](./creating-a-wide-view.md)

- [Anpassade kontroller](./creating-custom-controls.md)

## <a name="example"></a>Exempel

I det här exemplet visas ett `ViewDefinitions`-element som innehåller de överordnade elementen för en tabellvy och en listvy.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>Se även

[Konfigurations element (format)](./configuration-element-format.md)

[Visa element (format)](./view-element-format.md)

[Skapa en tabellvy](./creating-a-table-view.md)

[Skapa en listvy](./creating-a-list-view.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Anpassade kontroller](./creating-custom-controls.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
