---
title: EntrySelectedBy Element för EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846524"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>EntrySelectedBy-element för EnumerableExpansion (format)

Definierar vilka typer av .NET som använder den här definitionen eller villkor som måste finnas för den här definitionen som ska användas.

Elementet (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy konfigurationselement för EnumerableExpansion (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EntrySelectedBy` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Definierar de villkor som måste finnas för att expandera samlingen objekt av den här definitionen.|
|[SelectionSetName Element för EntrySelectedBy för EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Anger en uppsättning med .NET-typer som använder den här definitionen av hur mängdobjekt har expanderats.|
|[TypeName-Element för EntrySelectedBy för EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Anger ett .NET-typ som använder den här definitionen av hur mängdobjekt har expanderats.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EnumerableExpansion Element (Format)](./enumerableexpansion-element-format.md)|Definierar hur specifik .NET samling objekt visas när de visas i vyn.|

## <a name="remarks"></a>Anmärkningar

Du måste ange minst en typ, val av set eller urvalsvillkoret för en definition av posten. Det finns ingen högsta gräns för antalet underordnade element som du kan använda.

Val av villkor används för att definiera ett villkor som måste finnas för definitionen som ska användas, till exempel när ett objekt har en specifik egenskap eller som en specifik egenskapsvärde eller ett skript som utvärderas till `true`. Mer information om val av villkor finns i [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[Definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion Element (Format)](./enumerableexpansion-element-format.md)

[SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[SelectionSetName Element för EntrySelectedBy för EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[TypeName-Element för EntrySelectedBy för EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
