---
title: SelectionCondition-element för EntrySelectedBy för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358900"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)

Definierar ett villkor som måste finnas för att en gemensam kontroll definition ska kunna användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för kontroller för Konfiguration (format) CustomEntry-element för CustomControl for Controls for Configuration (format) EntrySelectedBy-element för CustomEntry for Controls for Configuration (format) SelectionCondition-element för EntrySelectedBy för CustomEntry för Konfiguration (format)

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
|[PropertyName-element för SelectionCondition för kontroll av konfiguration (format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger en .NET-egenskap som utlöser villkoret.|
|[Script block-element för SelectionCondition för kontroller för konfiguration (format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|
|[SelectionSetName-element för SelectionCondition för kontroller för konfiguration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger den uppsättning av .NET-typer som utlöser villkoret.|
|[Elementet TypeName för SelectionCondition för kontroller för konfiguration (format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för CustomEntry för kontroller för konfiguration (format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Definierar de .NET-typer som använder den här posten i common Control definition.|

## <a name="remarks"></a>Anmärkningar

Följande rikt linjer måste följas när du definierar ett urvals villkor:

- Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.

- Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.

Mer information om hur urvals villkor kan användas finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[PropertyName-element för SelectionCondition för kontroll av konfiguration (format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Script block-element för SelectionCondition för kontroller för konfiguration (format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[SelectionSetName-element för SelectionCondition för kontroller för konfiguration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elementet TypeName för SelectionCondition för kontroller för konfiguration (format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[EntrySelectedBy-element för CustomEntry för kontroller för konfiguration (format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Skriva en Windows PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
