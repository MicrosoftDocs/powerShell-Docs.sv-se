---
title: Typ element för SelectionSet (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358744"
---
# <a name="types-element-for-selectionset-format"></a>Types-element för SelectionSet (format)

Definierar de .NET-objekt som finns i urvals uppsättningen.

Konfigurations element (format) SelectionSets-element (format) SelectionSet element (format) element (format)

## <a name="syntax"></a>Syntax

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `Types`-elementet. Det måste finnas minst ett underordnat element, men det finns ingen övre gräns för antalet underordnade element som kan läggas till.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Element av typen TypeName (format)](./typename-element-for-types-format.md)|Nödvändigt element.<br /><br /> Anger det .NET-objekt som tillhör urvals uppsättningen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionSet-element (format)](./selectionset-element-format.md)|Definierar en uppsättning .NET-objekt som kan refereras till i uppsättningens namn.|

## <a name="remarks"></a>Anmärkningar

De objekt som definieras av det här elementet utgör en urvals uppsättning som kan användas av en vy, i en definition av en vy (vyer kan ha flera definitioner) eller när du anger ett urvals villkor.  Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

I det här exemplet visas ett `SelectionSet`-element som definierar fyra .NET-typer.

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

[Definiera uppsättningar av objekt](./defining-selection-sets.md)

[SelectionSet-element (format)](./selectionset-element-format.md)

[Element av typen TypeName (format)](./typename-element-for-types-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
