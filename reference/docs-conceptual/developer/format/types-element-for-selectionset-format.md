---
title: Typ element för SelectionSet (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9978daefb3e97ab131774ca4dff633dde6b4dfbf
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772526"
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

I följande avsnitt beskrivs attributen, underordnade element och `Types` elementets överordnade element. Det måste finnas minst ett underordnat element, men det finns ingen övre gräns för antalet underordnade element som kan läggas till.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Element av typen TypeName (format)](./typename-element-for-types-format.md)|Nödvändigt element.<br /><br /> Anger det .NET-objekt som tillhör urvals uppsättningen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionSet-element (format)](./selectionset-element-format.md)|Definierar en uppsättning .NET-objekt som kan refereras till i uppsättningens namn.|

## <a name="remarks"></a>Kommentarer

De objekt som definieras av det här elementet utgör en urvals uppsättning som kan användas av en vy, i en definition av en vy (vyer kan ha flera definitioner) eller när du anger ett urvals villkor.  Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

Det här exemplet visar ett- `SelectionSet` element som definierar fyra .net-typer.

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

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
