---
title: TypeName-Element för typer (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: 4f463ac6b70a00f628c5b93b112c5fa510ff3bfb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845117"
---
# <a name="typename-element-for-types-format"></a>TypeName-element för Types (format)

Anger .NET-typ för ett objekt som hör till val av uppsättningen.

Elementet (Format) SelectionSets Element (Format) SelectionSet konfigurationselement (Format) datatyper Element (Format) TypeName Element av typer (Format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` element. Minst en `TypeName` elementet måste finnas med i val av uppsättningen.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Typer av Element (Format)](./types-element-for-selectionset-format.md)|Definierar de .NET-objekt som är i urvalet inställda.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typen.

## <a name="remarks"></a>Anmärkningar

Du kan använda inställningarna när du har en uppsättning relaterade objekt som du vill referera till med hjälp av ett enda namn, till exempel en uppsättning objekt som är relaterade genom arv. När du definierar dina vyer kan du ange en uppsättning objekt med hjälp av namnet på den val av i stället för att visa en lista över alla objekt i varje vy.

Vanliga val av uppsättningar anges efter deras namn när du definierar vyer i filen formatering. I dessa fall kan den `SelectionSetName` underordnat element av den `ViewSelectedBy` element för vyn anger. Olika poster i en vy kan även ange en uppsättning för val av som gäller för den aktuella posten för vyn. Mer information om inställningarna finns i [definiera anger av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

I följande exempel visas en `SelectionSet` -element som definierar fyra typer av .NET.

```
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

[SelectionSets Element (Format)](./selectionsets-element-format.md)

[Typer av Element (Format)](./types-element-for-selectionset-format.md)

[Skriva ett Windows PowDefining uppsättningar ObjecterShell formatering fil](./writing-a-powershell-formatting-file.md)
