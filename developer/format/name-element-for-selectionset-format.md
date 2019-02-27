---
title: Namn på Element för SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848330"
---
# <a name="name-element-for-selectionset-format"></a>Name-element för SelectionSet (format)

Anger namnet som refererar till uppsättningen val.

Elementet (Format) SelectionSets Element (Format) SelectionSet Element (Format) namn konfigurationselement för SelectionSet (Format)

## <a name="syntax"></a>Syntax

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `Name` Element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionSet Element (Format)](./selectionset-element-format.md)|Definierar en uppsättning med .NET-objekt som kan refereras av namnet på uppsättningen.|

## <a name="text-value"></a>Textvärde

Ange ett namn för att referera till val av uppsättningen. Det finns inga begränsningar vad gäller vilka tecken som kan användas.

## <a name="remarks"></a>Anmärkningar

Namnet som anges här används i den `SelectionSetName` element. Val av uppsättningen som kan användas av en vy av en definition av en vy (vyer kan ha flera definitioner), eller när du anger ett val av villkor. Mer information om inställningarna finns i [definiera anger av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

Det här exemplet visar en `SelectionSet` -element som definierar fyra typer av .NET. Val av uppsättningen heter ”FileSystemTypes”.

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

[Definiera inställningarna](./defining-selection-sets.md)

[SelectionSet Element (Format)](./selectionset-element-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
