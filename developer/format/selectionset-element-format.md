---
title: SelectionSet Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850423"
---
# <a name="selectionset-element-format"></a>SelectionSet-element (format)

Definierar en uppsättning av .NET-objekt som kan refereras av namnet på uppsättningen.

Elementet (Format) SelectionSets Element (Format) SelectionSet konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSet` element. Varje uppsättning val måste ha ett namn och det måste ange .NET-objekt i uppsättningen.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Namnelement för SelectionSet (Format)](./name-element-for-selectionset-format.md)|Element som krävs.<br /><br /> Anger namnet som refererar till uppsättningen val.|
|[Typer av Element (Format)](./types-element-for-selectionset-format.md)|Element som krävs.<br /><br /> Definierar de .NET-objekt som är i urvalet inställda.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionSets Element Format](./selectionsets-element-format.md)|Definierar gemensamma uppsättningar med .NET-objekt som kan användas av alla vyer i filen formatering.|

## <a name="remarks"></a>Anmärkningar

Du kan använda inställningarna när du har en uppsättning relaterade objekt som du vill referera till med hjälp av ett enda namn, till exempel en uppsättning objekt som är relaterade genom arv. När du definierar dina vyer kan du ange en uppsättning objekt med hjälp av namnet på den val av i stället för att visa en lista över alla objekt i varje vy.

Vanliga val av uppsättningar anges efter deras namn när du definierar vyer i filen formatering eller definitioner av vyerna. I dessa fall kan den `SelectionSetName` underordnat element av den `ViewSelectedBy` och `EntrySelectedBy` anger de element som ska användas. Mer information om inställningarna finns i [definiera anger av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

I följande exempel visas en `SelectionSet` -element som definierar fyra typer av .NET.

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

[Namnelement av SelectionSet (Format)](./name-element-for-selectionset-format.md)

[SelectionSets Element (Format)](./selectionsets-element-format.md)

[Typer av Element (Format)](./types-element-for-selectionset-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
