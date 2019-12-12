---
title: Namn element för SelectionSet (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354294"
---
# <a name="name-element-for-selectionset-format"></a>Name-element för SelectionSet (format)

Anger namnet som används för att referera till urvals uppsättningen.

Konfigurations element (format) SelectionSets-element (format) SelectionSet element (format), element för SelectionSet (format)

## <a name="syntax"></a>Syntax

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `Name`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionSet-element (format)](./selectionset-element-format.md)|Definierar en enda uppsättning .NET-objekt som kan refereras till i uppsättningens namn.|

## <a name="text-value"></a>Textvärde

Ange det namn som ska referera till urvals uppsättningen. Det finns inga begränsningar för vilka tecken som kan användas.

## <a name="remarks"></a>Anmärkningar

Namnet som anges här används i `SelectionSetName`-elementet. Den urvals uppsättning som kan användas av en vy, genom en definition av en vy (vyer kan ha flera definitioner) eller när du anger ett urvals villkor. Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

I det här exemplet visas ett `SelectionSet`-element som definierar fyra .NET-typer. Namnet på urvals uppsättningen är "FileSystemTypes".

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

[Definiera urvals uppsättningar](./defining-selection-sets.md)

[SelectionSet-element (format)](./selectionset-element-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
