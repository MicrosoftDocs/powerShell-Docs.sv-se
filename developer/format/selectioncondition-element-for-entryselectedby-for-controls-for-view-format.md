---
title: SelectionCondition Element för EntrySelectedBy för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064252"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>SelectionCondition-element för EntrySelectedBy för Controls för View (format)

Definierar ett villkor som måste finnas för kontrolldefinition som ska användas. Det här elementet används när du definierar kontroller som kan användas av en vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för kontroller för att visa (Format) CustomEntry Element för CustomEntries för kontroller för att visa (Format) EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format) SelectionCondition Element för EntrySelectedBy för kontroller för att visa ( Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionCondition` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-Element för SelectionCondition för kontroller för att visa (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger en .NET-egenskap som utlöser villkoret.|
|[ScriptBlock Element för SelectionCondition för kontroller för att visa (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|
|[SelectionSetName Element för SelectionCondition för kontroller för att visa (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger den uppsättning med .NET-typer som utlöser villkoret.|
|[TypeName-Element för SelectionCondition för kontroller för att visa (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger ett .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas.|

## <a name="remarks"></a>Anmärkningar

När du definierar en urvalsvillkoret, gäller följande krav:

- Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skriptblock, men kan inte ange båda.

- Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.

Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[PropertyName-Element för SelectionCondition för kontroller för att visa (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[ScriptBlock Element för SelectionCondition för kontroller för att visa (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[SelectionSetName Element för SelectionCondition för kontroller för att visa (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[TypeName-Element för SelectionCondition för kontroller för att visa (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
