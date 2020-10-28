---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSets-element (format)
description: SelectionSets-element (format)
ms.openlocfilehash: e5c928dfb82bc6963b4a87aef9ec06d34cacfdcb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654928"
---
# <a name="selectionsets-element-format"></a>SelectionSets-element (format)

Definierar de gemensamma uppsättningar av .NET-objekt som kan användas av alla vyer i format filen. Vyer och kontroller i format filen kan referera till en fullständig uppsättning objekt genom att bara använda namnet på uppsättningen.

SelectionSets element format för konfigurations element

## <a name="syntax"></a>Syntax

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `SelectionSets` elementets överordnade element. Varje underordnat element definierar en uppsättning objekt som kan refereras till av uppsättningens namn. Ordningen på de underordnade elementen är inte signifikant.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionSet-element (format)](./selectionset-element-format.md)|Nödvändigt element.<br /><br /> Definierar en enda uppsättning .NET-objekt som kan refereras till i uppsättningens namn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Konfigurations element](./configuration-element-format.md)|Representerar det översta elementet i en textfil.|

## <a name="remarks"></a>Kommentarer

Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv. När du definierar dina vyer kan du ange en uppsättning objekt genom att använda namnet på urvals uppsättningen i stället för att visa alla objekt i varje vy.

Vanliga urvals uppsättningar anges med deras namn när du definierar vyerna för format filen eller definitionerna för vyerna. I dessa fall anger det `SelectionSetName` underordnade elementet i `ViewSelectedBy` `EntrySelectedBy` elementen och den uppsättning som ska användas. Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

## <a name="see-also"></a>Se även

[Konfigurations element](./configuration-element-format.md)

[Definiera valuppsättningar](./defining-selection-sets.md)

[SelectionSet-element (format)](./selectionset-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
