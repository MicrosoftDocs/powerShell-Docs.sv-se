---
title: SelectionCondition-element för EntrySelectedBy for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358887"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a>SelectionCondition-element för EntrySelectedBy för GroupBy (format)

Definierar ett villkor som måste finnas för att en kontroll definition ska kunna användas. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) EntrySelectedBy-element för CustomEntry för GroupBy (format) SelectionCondition-element för EntrySelectedBy för GroupBy (format)

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `SelectionCondition`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-element för SelectionCondition för GroupBy (format)](./propertyname-element-for-selectioncondition-for-groupby-format.md)|Valfritt element.<br /><br /> Anger en .NET-egenskap som utlöser villkoret.|
|[Script block-element för SelectionCondition för GroupBy (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|
|[SelectionSetName-element för SelectionCondition för GroupBy (format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|Valfritt element.<br /><br /> Anger den uppsättning av .NET-typer som utlöser villkoret.|
|[Elementet TypeName för SelectionCondition för GroupBy (format)](./typename-element-for-selectioncondition-for-groupby-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för CustomEntry för GroupBy (format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.|

## <a name="remarks"></a>Anmärkningar

När du definierar ett urvals villkor gäller följande krav:

- Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.

- Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.

Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[PropertyName-element för SelectionCondition för CustomControl för vy (format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Script block-element för SelectionCondition för CustomControl för View (format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[SelectionSetName-element för SelectionCondition för anpassad kontroll för vy (format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elementet TypeName för SelectionCondition för GroupBy (format)](./typename-element-for-selectioncondition-for-groupby-format.md)

[EntrySelectedBy-element för CustomEntry för GroupBy (format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)