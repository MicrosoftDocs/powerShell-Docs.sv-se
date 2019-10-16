---
title: SelectionCondition-element för EntrySelectedBy för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353860"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>SelectionCondition-element för EntrySelectedBy för Controls för View (format)

Definierar ett villkor som måste finnas för att den kontroll definition som ska användas. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl for Controls for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) EntrySelectedBy-elementet for CustomEntry for Controls for View (format) SelectionCondition element for EntrySelectedBy for Controls for View ( Formatering

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
|[PropertyName-element för SelectionCondition för kontroller för vy (format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger en .NET-egenskap som utlöser villkoret.|
|[Script block-element för SelectionCondition för kontroller för vy (format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|
|[SelectionSetName-element för SelectionCondition för kontroller för vy (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger den uppsättning av .NET-typer som utlöser villkoret.|
|[Elementet TypeName för SelectionCondition för kontroller för vyn (format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för CustomEntry för kontroller för vy (format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.|

## <a name="remarks"></a>Anmärkningar

När du definierar ett urvals villkor gäller följande krav:

- Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.

- Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.

Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[PropertyName-element för SelectionCondition för kontroller för vy (format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[Script block-element för SelectionCondition för kontroller för vy (format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[SelectionSetName-element för SelectionCondition för kontroller för vy (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[Elementet TypeName för SelectionCondition för kontroller för vyn (format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[EntrySelectedBy-element för CustomEntry för kontroller för vy (format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
