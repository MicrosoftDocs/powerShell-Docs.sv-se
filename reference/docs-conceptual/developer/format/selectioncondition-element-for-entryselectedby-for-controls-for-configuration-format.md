---
title: SelectionCondition-element för EntrySelectedBy för kontroll av konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 748aa1aa0ba603a44334d9401e9e2c0e68f14e03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783423"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)

Definierar ett villkor som måste finnas för att en gemensam kontroll definition ska kunna användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Controls (format) CustomEntry-element för CustomControl för Controls (format) EntrySelectedBy-element för CustomEntry för Controls (format) SelectionCondition-element för EntrySelectedBy för CustomEntry för konfiguration (format)

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
|[PropertyName-element för SelectionCondition för Controls för Configuration (format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger en .NET-egenskap som utlöser villkoret.|
|[ScriptBlock-element för SelectionCondition för Controls för Configuration (format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|
|[SelectionSetName-element för SelectionCondition för Controls för Configuration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger den uppsättning av .NET-typer som utlöser villkoret.|
|[TypeName-element för SelectionCondition för Controls för Configuration (format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Definierar de .NET-typer som använder den här posten i common Control definition.|

## <a name="remarks"></a>Kommentarer

Följande rikt linjer måste följas när du definierar ett urvals villkor:

- Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.

- Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.

Mer information om hur urvals villkor kan användas finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[PropertyName-element för SelectionCondition för Controls för Configuration (format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[ScriptBlock-element för SelectionCondition för Controls för Configuration (format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[SelectionSetName-element för SelectionCondition för Controls för Configuration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[TypeName-element för SelectionCondition för Controls för Configuration (format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Skriva en Windows PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
