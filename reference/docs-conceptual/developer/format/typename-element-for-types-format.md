---
title: Elementet TypeName för typer (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358738"
---
# <a name="typename-element-for-types-format"></a>TypeName-element för Types (format)

Anger .NET-typen för ett objekt som tillhör urvals uppsättningen.

Konfigurations element (format) SelectionSets-element (format) SelectionSet-element (format) Type-element (format) element (format) element typ (format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `TypeName`. Minst ett `TypeName`-element måste ingå i urvals uppsättningen.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Typ element (format)](./types-element-for-selectionset-format.md)|Definierar de .NET-objekt som finns i urvals uppsättningen.|

## <a name="text-value"></a>Text värde

Ange det fullständigt kvalificerade namnet för .NET-typen.

## <a name="remarks"></a>Anmärkningar

Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv. När du definierar dina vyer kan du ange en uppsättning objekt genom att använda namnet på urvals uppsättningen i stället för att visa alla objekt i varje vy.

Vanliga urvals uppsättningar anges med deras namn när du definierar vyerna för format filen. I dessa fall anger det underordnade elementet `SelectionSetName` för elementet `ViewSelectedBy` för vyn. Olika poster i en vy kan dock också ange en markerings uppsättning som endast gäller för posten i vyn. Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

I följande exempel visas ett `SelectionSet`-element som definierar fyra .NET-typer.

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

[Definiera urvals uppsättningar](./defining-selection-sets.md)

[SelectionSet-element (format)](./selectionset-element-format.md)

[SelectionSets-element (format)](./selectionsets-element-format.md)

[Typ element (format)](./types-element-for-selectionset-format.md)

[Skriva en Windows PowerShell-textfil](./writing-a-powershell-formatting-file.md)
