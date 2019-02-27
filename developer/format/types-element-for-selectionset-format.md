---
title: Datatyper Element för SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851277"
---
# <a name="types-element-for-selectionset-format"></a>Types-element för SelectionSet (format)

Definierar de .NET-objekt som är i urvalet inställda.

Elementet (Format) SelectionSets Element (Format) SelectionSet konfigurationselement (Format) datatyper Element (Format)

## <a name="syntax"></a>Syntax

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Types` element. Det måste finnas minst ett underordnat element, men det finns ingen högsta gräns för antalet underordnade element som kan läggas till.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TypeName-elementet i typer (Format)](./typename-element-for-types-format.md)|Element som krävs.<br /><br /> Anger det .NET-objekt som hör till val av uppsättningen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionSet Element (Format)](./selectionset-element-format.md)|Definierar en uppsättning av .NET-objekt som kan refereras av namnet på uppsättningen.|

## <a name="remarks"></a>Anmärkningar

De objekt som definierats av det här elementet utgör en uppsättning för val av som kan användas av en vy av en definition av en vy (vyer kan ha flera definitioner), eller när du anger ett val av villkor.  Mer information om inställningarna finns i [definiera anger av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

Det här exemplet visar en `SelectionSet` -element som definierar fyra typer av .NET.

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a>Se även

[Definiera uppsättningar med objekt](./defining-selection-sets.md)

[SelectionSet Element (Format)](./selectionset-element-format.md)

[TypeName-elementet i typer (Format)](./typename-element-for-types-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
