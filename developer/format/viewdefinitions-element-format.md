---
title: ViewDefinitions Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083713"
---
# <a name="viewdefinitions-element-format"></a>ViewDefinitions-element (format)

Definierar de vyer som används för att visa .NET-objekt. Vyerna kan visa egenskaperna och värdena för skript för ett objekt i ett tabellformat, lista, brett format och anpassad kontroll format.

Konfigurationselementet Element (Format) ViewDefinitions (XML-Format)

## <a name="syntax"></a>Syntax

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `ViewDefinitions` element. Det finns ingen gräns för antal vyer som kan definieras i en fil med formatering och de kan läggas till i valfri ordning.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Visa Element (Format)](./view-element-format.md)|Definierar en vy som används för att visa en eller flera .NET-objekt.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Konfigurationselementet (Format)](./configuration-element-format.md)|Representerar det översta elementet i en formatering fil.|

## <a name="remarks"></a>Anmärkningar

Mer information om komponenterna i de olika typerna av vyer finns i följande avsnitt:

- [Skapa en tabellvy](./creating-a-table-view.md)

- [Skapa en listvy](./creating-a-list-view.md)

- [Skapa en bred vy](./creating-a-wide-view.md)

- [Anpassade kontroller](./creating-custom-controls.md)

## <a name="example"></a>Exempel

Det här exemplet visar en `ViewDefinitions` element som innehåller de överordnade element för en tabell och en listvy.

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

[Konfigurationselementet (Format)](./configuration-element-format.md)

[Visa Element (Format)](./view-element-format.md)

[Skapa en tabellvy](./creating-a-table-view.md)

[Skapa en listvy](./creating-a-list-view.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Anpassade kontroller](./creating-custom-controls.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
