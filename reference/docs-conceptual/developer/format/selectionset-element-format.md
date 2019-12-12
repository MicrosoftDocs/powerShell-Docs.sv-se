---
title: SelectionSet-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358869"
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

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `SelectionSet`-elementet. Varje urvals uppsättning måste ha ett namn och måste ange .NET-objekten för uppsättningen.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Namn element för SelectionSet (format)](./name-element-for-selectionset-format.md)|Nödvändigt element.<br /><br /> Anger namnet som används för att referera till urvals uppsättningen.|
|[Typ element (format)](./types-element-for-selectionset-format.md)|Nödvändigt element.<br /><br /> Definierar de .NET-objekt som finns i urvals uppsättningen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionSets element format](./selectionsets-element-format.md)|Definierar de gemensamma uppsättningar av .NET-objekt som kan användas av alla vyer i format filen.|

## <a name="remarks"></a>Anmärkningar

Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv. När du definierar dina vyer kan du ange en uppsättning objekt genom att använda namnet på urvals uppsättningen i stället för att visa alla objekt i varje vy.

Vanliga urvals uppsättningar anges med deras namn när du definierar vyerna för format filen eller definitionerna för vyerna. I dessa fall anger `SelectionSetName` underordnat element i `ViewSelectedBy` och `EntrySelectedBy` elementen som ska användas. Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

I följande exempel visas ett `SelectionSet`-element som definierar fyra .NET-typer.

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

[Namn element i SelectionSet (format)](./name-element-for-selectionset-format.md)

[SelectionSets-element (format)](./selectionsets-element-format.md)

[Typ element (format)](./types-element-for-selectionset-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
