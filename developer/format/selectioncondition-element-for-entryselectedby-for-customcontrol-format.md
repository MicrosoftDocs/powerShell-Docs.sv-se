---
title: SelectionCondition Element för EntrySelectedBy för anpassad kontroll (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075757"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>SelectionCondition-element för EntrySelectedBy för CustomControl (format)

Definierar ett villkor som måste finnas en definition för kontrollen som ska användas. Det här elementet används när du definierar en anpassad kontroll vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll konfigurationselement för Visa (Format) CustomEntries elementet för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för anpassad kontroll för Visa ( Format) CustomItem Element för CustomEntry för anpassad kontroll för Visa (Format) EntrySelectedBy elementet för CustomEntry för anpassad kontroll för Visa (Format) SelectionCondition elementet för EntrySelectedBy för anpassad kontroll för vy (Format)

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
|[PropertyName-Element för SelectionCondition för anpassad kontroll för vy (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger en .NET-egenskap som utlöser villkoret.|
|[ScriptBlock Element för SelectionCondition för anpassad kontroll för vy (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|
|[SelectionSetName Element för SelectionCondition för anpassad kontroll för vy (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger den uppsättning med .NET-typer som utlöser villkoret.|
|[TypeName-Element för SelectionCondition för anpassad kontroll för vy (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger ett .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för CustomEntry för anpassad kontroll för vy (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas.|

## <a name="remarks"></a>Anmärkningar

När du definierar en urvalsvillkoret, gäller följande krav:

- Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skriptblock, men kan inte ange båda.

- Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.

Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[PropertyName-Element för SelectionCondition för anpassad kontroll för vy (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[ScriptBlock Element för SelectionCondition för anpassad kontroll för vy (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[SelectionSetName Element för SelectionCondition för anpassad kontroll för vy (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[TypeName-Element för SelectionCondition för anpassad kontroll för vy (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[EntrySelectedBy Element för CustomEntry för anpassad kontroll för vy (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
