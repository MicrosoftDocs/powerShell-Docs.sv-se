---
title: EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066251"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>EntrySelectedBy-element för CustomEntry för Controls för View (format)

Definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas. Det här elementet används när du definierar kontroller som kan användas av en vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för kontroller för att visa (Format) CustomEntry Element för CustomEntries för kontroller för att visa (Format) EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `EntrySelectedBy` element. Du måste ange minst en typ, val av set eller urvalsvillkoret definieras. Det finns ingen högsta gräns för antalet underordnade element som du kan använda.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition Element för EntrySelectedBy för kontroller för att visa (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Definierar de villkor som måste finnas för den här definitionen som ska användas.|
|[SelectionSetName Element för EntrySelectedBy för kontroller för att visa (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger en uppsättning med .NET-typer som använder den här definitionen för kontrollen.|
|[TypeName-Element för EntrySelectedBy för kontroller för att visa (Format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger ett .NET-typ som använder den här definitionen för kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry Element för CustomEntries för kontroller för att visa (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Innehåller en definition av kontrollen.|

## <a name="remarks"></a>Anmärkningar

Val av villkor används för att definiera ett villkor som måste finnas för definitionen som ska användas, till exempel när ett objekt har en specifik egenskap eller när en specifik egenskapsvärdet eller skript som utvärderas till `true`. Mer information om val av villkor finns i [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[CustomEntry Element för CustomEntries för kontroller för att visa (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
