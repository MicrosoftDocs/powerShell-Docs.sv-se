---
title: ViewDefinitions-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a108c4f8b03e3dec3905181b390aee2c82ab0028
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772492"
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

I följande avsnitt beskrivs attributen, underordnade element och `ViewDefinitions` elementets överordnade element. Det finns ingen gräns för antalet vyer som kan definieras i en formateringsinformation och de kan läggas till i vilken ordning som helst.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[View-element (format)](./view-element-format.md)|Definierar en vy som används för att visa ett eller flera .NET-objekt.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Configuration-element (format)](./configuration-element-format.md)|Representerar det översta elementet i en textfil.|

## <a name="remarks"></a>Kommentarer

Mer information om komponenterna i de olika typerna av vyer finns i följande avsnitt:

- [Skapa en tabellvy](./creating-a-table-view.md)

- [Skapa en listvy](./creating-a-list-view.md)

- [Skapa en bred vy](./creating-a-wide-view.md)

- [Anpassade kontroller](./creating-custom-controls.md)

## <a name="example"></a>Exempel

Det här exemplet visar ett `ViewDefinitions` element som innehåller de överordnade elementen för en tabellvy och en listvy.

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

[Configuration-element (format)](./configuration-element-format.md)

[View-element (format)](./view-element-format.md)

[Skapa en tabellvy](./creating-a-table-view.md)

[Skapa en listvy](./creating-a-list-view.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Anpassade kontroller](./creating-custom-controls.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
