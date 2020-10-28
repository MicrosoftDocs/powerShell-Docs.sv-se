---
ms.date: 09/13/2016
ms.topic: reference
title: Name-element för SelectionSet (format)
description: Name-element för SelectionSet (format)
ms.openlocfilehash: 98c13be6ea352055231fbdb3a60f0eb508f661b8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666474"
---
# <a name="name-element-for-selectionset-format"></a>Name-element för SelectionSet (format)

Anger namnet som används för att referera till urvals uppsättningen.

Konfigurations element (format) SelectionSets-element (format) SelectionSet element (format), element för SelectionSet (format)

## <a name="syntax"></a>Syntax

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `Name` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionSet-element (format)](./selectionset-element-format.md)|Definierar en enda uppsättning .NET-objekt som kan refereras till i uppsättningens namn.|

## <a name="text-value"></a>Textvärde

Ange det namn som ska referera till urvals uppsättningen. Det finns inga begränsningar för vilka tecken som kan användas.

## <a name="remarks"></a>Kommentarer

Namnet som anges här används i- `SelectionSetName` elementet. Den urvals uppsättning som kan användas av en vy, genom en definition av en vy (vyer kan ha flera definitioner) eller när du anger ett urvals villkor. Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

Det här exemplet visar ett- `SelectionSet` element som definierar fyra .net-typer. Namnet på urvals uppsättningen är "FileSystemTypes".

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

[Definiera valuppsättningar](./defining-selection-sets.md)

[SelectionSet-element (format)](./selectionset-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
