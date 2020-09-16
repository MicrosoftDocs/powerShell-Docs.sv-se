---
title: SelectionSet-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: cf47229993458492c712d28e04913e75d1bde386
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783406"
---
# <a name="selectionset-element-format"></a>SelectionSet-element (format)

Definierar en uppsättning .NET-objekt som kan refereras till i uppsättningens namn.

Konfigurations element (format) SelectionSets-element (format) SelectionSet-element (format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `SelectionSet` elementets överordnade element. Varje urvals uppsättning måste ha ett namn och måste ange .NET-objekten för uppsättningen.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Name-element för SelectionSet (format)](./name-element-for-selectionset-format.md)|Nödvändigt element.<br /><br /> Anger namnet som används för att referera till urvals uppsättningen.|
|[Typ element (format)](./types-element-for-selectionset-format.md)|Nödvändigt element.<br /><br /> Definierar de .NET-objekt som finns i urvals uppsättningen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionSets element format](./selectionsets-element-format.md)|Definierar de gemensamma uppsättningar av .NET-objekt som kan användas av alla vyer i format filen.|

## <a name="remarks"></a>Kommentarer

Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv. När du definierar dina vyer kan du ange en uppsättning objekt genom att använda namnet på urvals uppsättningen i stället för att visa alla objekt i varje vy.

Vanliga urvals uppsättningar anges med deras namn när du definierar vyerna för format filen eller definitionerna för vyerna. I dessa fall anger det `SelectionSetName` underordnade elementet i `ViewSelectedBy` `EntrySelectedBy` elementen och den uppsättning som ska användas. Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

I följande exempel visas ett- `SelectionSet` element som definierar fyra .net-typer.

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

[Namn element i SelectionSet (format)](./name-element-for-selectionset-format.md)

[SelectionSets-element (format)](./selectionsets-element-format.md)

[Typ element (format)](./types-element-for-selectionset-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
