---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för Types (format)
description: TypeName-element för Types (format)
ms.openlocfilehash: c656b8e7e5877b72ff2164e5b417857273cada61
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664619"
---
# <a name="typename-element-for-types-format"></a>TypeName-element för Types (format)

Anger .NET-typen för ett objekt som tillhör urvals uppsättningen.

Konfigurations element (format) SelectionSets-element (format) SelectionSet-element (format) Type-element (format) element (format) element typ (format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `TypeName` elementets överordnade element. Minst ett `TypeName` element måste ingå i urvals uppsättningen.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Typ element (format)](./types-element-for-selectionset-format.md)|Definierar de .NET-objekt som finns i urvals uppsättningen.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typen.

## <a name="remarks"></a>Kommentarer

Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv. När du definierar dina vyer kan du ange en uppsättning objekt genom att använda namnet på urvals uppsättningen i stället för att visa alla objekt i varje vy.

Vanliga urvals uppsättningar anges med deras namn när du definierar vyerna för format filen. I dessa fall anger det `SelectionSetName` underordnade elementet för `ViewSelectedBy` vyns element uppsättning. Olika poster i en vy kan dock också ange en markerings uppsättning som endast gäller för posten i vyn. Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

I följande exempel visas ett- `SelectionSet` element som definierar fyra .net-typer.

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

[Definiera valuppsättningar](./defining-selection-sets.md)

[SelectionSet-element (format)](./selectionset-element-format.md)

[SelectionSets-element (format)](./selectionsets-element-format.md)

[Typ element (format)](./types-element-for-selectionset-format.md)

[Skriva en Windows PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
