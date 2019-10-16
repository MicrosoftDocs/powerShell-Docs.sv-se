---
title: SelectionSets-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353734"
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

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `SelectionSets`-elementet. Varje underordnat element definierar en uppsättning objekt som kan refereras till av uppsättningens namn. Ordningen på de underordnade elementen är inte signifikant.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionSet-element (format)](./selectionset-element-format.md)|Nödvändigt element.<br /><br /> Definierar en enda uppsättning .NET-objekt som kan refereras till i uppsättningens namn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Konfigurations element](./configuration-element-format.md)|Representerar det översta elementet i en textfil.|

## <a name="remarks"></a>Anmärkningar

Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv. När du definierar dina vyer kan du ange en uppsättning objekt genom att använda namnet på urvals uppsättningen i stället för att visa alla objekt i varje vy.

Vanliga urvals uppsättningar anges med deras namn när du definierar vyerna för format filen eller definitionerna för vyerna. I dessa fall anger det underordnade elementet `SelectionSetName` för elementen `ViewSelectedBy` och `EntrySelectedBy` den uppsättning som ska användas. Mer information om urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

## <a name="see-also"></a>Se även

[Konfigurations element](./configuration-element-format.md)

[Definiera urvals uppsättningar](./defining-selection-sets.md)

[SelectionSet-element (format)](./selectionset-element-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
