---
title: SelectionSets Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845110"
---
# <a name="selectionsets-element-format"></a>SelectionSets-element (format)

Definierar gemensamma uppsättningar med .NET-objekt som kan användas av alla vyer i filen formatering. Vyer och kontroller av filen formatering kan referera till en fullständig uppsättning med objekt med hjälp av endast namnet på val av uppsättningen.

Konfiguration av elementet SelectionSets elementet Format

## <a name="syntax"></a>Syntax

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `SelectionSets` element. Varje underordnat element definierar en uppsättning objekt som kan refereras av namnet på uppsättningen. Ordningen på de underordnade elementen är inte viktig.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionSet Element (Format)](./selectionset-element-format.md)|Element som krävs.<br /><br /> Definierar en uppsättning med .NET-objekt som kan refereras av namnet på uppsättningen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Konfigurationselement](./configuration-element-format.md)|Representerar det översta elementet i en formatering fil.|

## <a name="remarks"></a>Anmärkningar

Du kan använda inställningarna när du har en uppsättning relaterade objekt som du vill referera till med hjälp av ett enda namn, till exempel en uppsättning objekt som är relaterade genom arv. När du definierar dina vyer kan du ange en uppsättning objekt med hjälp av namnet på den val av i stället för att visa en lista över alla objekt i varje vy.

Vanliga val av uppsättningar anges efter deras namn när du definierar vyer i filen formatering eller definitioner av vyerna. I dessa fall kan den `SelectionSetName` underordnat element av den `ViewSelectedBy` och `EntrySelectedBy` anger de element som ska användas. Mer information om inställningarna finns i [definiera anger av objekt](./defining-selection-sets.md).

## <a name="see-also"></a>Se även

[Konfigurationselement](./configuration-element-format.md)

[Definiera inställningarna](./defining-selection-sets.md)

[SelectionSet Element (Format)](./selectionset-element-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
