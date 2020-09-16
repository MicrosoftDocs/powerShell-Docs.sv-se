---
title: SelectionCondition-element för EntrySelectedBy för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1c14b2638249bdbfe25f7a96e917d66ea10ed239
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787588"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>SelectionCondition-element för EntrySelectedBy för Controls för View (format)

Definierar ett villkor som måste finnas för att den kontroll definition som ska användas. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl for Controls for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) EntrySelectedBy-elementet for CustomEntry for Controls for View (format) SelectionCondition element for EntrySelectedBy for Controls for View (format)

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

I följande avsnitt beskrivs attribut, underordnade element och `SelectionCondition` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-element för SelectionCondition för Controls för View (format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger en .NET-egenskap som utlöser villkoret.|
|[ScriptBlock-element för SelectionCondition för Controls för View (format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|
|[SelectionSetName-element för SelectionCondition för Controls för View (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger den uppsättning av .NET-typer som utlöser villkoret.|
|[TypeName-element för SelectionCondition för Controls för View (format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för CustomEntry för Controls för View (format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.|

## <a name="remarks"></a>Kommentarer

När du definierar ett urvals villkor gäller följande krav:

- Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.

- Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.

Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[PropertyName-element för SelectionCondition för Controls för View (format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[ScriptBlock-element för SelectionCondition för Controls för View (format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[SelectionSetName-element för SelectionCondition för Controls för View (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[TypeName-element för SelectionCondition för Controls för View (format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[EntrySelectedBy-element för CustomEntry för Controls för View (format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
