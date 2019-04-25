---
title: SelectionCondition Element för EntrySelectedBy för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064014"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>SelectionCondition-element för EntrySelectedBy för WideControl (format)

Definierar de villkor som måste finnas för den här definitionen som ska användas. Det finns ingen gräns för hur många val av villkor som kan anges för en bred post-definition.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format) SelectionCondition elementet för EntrySelectedBy för WideEntry (Format)

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionCondition` element. Du måste ange en enda `PropertyName` eller `ScriptBlock` element. Den `SelectionSetName` och `TypeName` element är valfria. Du kan ange en av antingen element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[ScriptBlock Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Valfritt element.<br /><br /> Anger skriptblocket som utlöser villkoret.|
|[SelectionSetName Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Valfritt element.<br /><br /> Anger den uppsättning med .NET-typer som utlöser villkoret.|
|[TypeName-Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Valfritt element.<br /><br /> Anger ett .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Definierar vilka typer av .NET som använder den här wide posten eller villkor som måste finnas för den här posten som ska användas.|

## <a name="remarks"></a>Anmärkningar

Varje wide post måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.

När du definierar en urvalsvillkoret, gäller följande krav:

- Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skriptblock, men kan inte ange båda.

- Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.

Läs mer om hur du använder villkor för val av [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).

Mer information om andra komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[Definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md)

[EntrySelectedBy Element för WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[PropertyName-Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[ScriptBlock Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[TypeName-Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
