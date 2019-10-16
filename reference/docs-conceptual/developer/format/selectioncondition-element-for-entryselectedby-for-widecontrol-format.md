---
title: SelectionCondition-element för EntrySelectedBy för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355771"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>SelectionCondition-element för EntrySelectedBy för WideControl (format)

Definierar det villkor som måste finnas för att den här definitionen ska kunna användas. Det finns ingen gräns för hur många urvals villkor som kan anges för en bred post definition.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition-element för EntrySelectedBy för WideEntry (format)

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `SelectionCondition`. Du måste ange ett enskilt `PropertyName`-eller `ScriptBlock`-element. Elementen `SelectionSetName` och `TypeName` är valfria. Du kan ange ett av båda elementen.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[Script block-element för SelectionCondition för EntrySelectedBy för WideEntry (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Valfritt element.<br /><br /> Anger det skript block som utlöser villkoret.|
|[SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Valfritt element.<br /><br /> Anger den uppsättning av .NET-typer som utlöser villkoret.|
|[Elementet TypeName för SelectionCondition för EntrySelectedBy för WideEntry (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för WideEntry (format)](./entryselectedby-element-for-wideentry-format.md)|Definierar de .NET-typer som använder den här breda posten eller det villkor som måste finnas för att den här posten ska kunna användas.|

## <a name="remarks"></a>Anmärkningar

Varje bred post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.

När du definierar ett urvals villkor gäller följande krav:

- Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.

- Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.

Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).

Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[EntrySelectedBy-element för WideEntry (format)](./entryselectedby-element-for-wideentry-format.md)

[PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Script block-element för SelectionCondition för EntrySelectedBy för WideEntry (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Elementet TypeName för SelectionCondition för EntrySelectedBy för WideEntry (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
