---
title: SelectionCondition Element för EntrySelectedBy för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075672"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a>SelectionCondition-element för EntrySelectedBy för TableControl (format)

Definierar de villkor som måste finnas för att använda för den här definitionen av tabellvyn. Det finns ingen gräns för hur många val av villkor som kan anges för en tabelldefinition.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy konfigurationselement för TableRowEntry (Format) SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i elementet SelectionCondition.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[ScriptBlock Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|
|[SelectionSetName Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger uppsättningen med .NET-typer som utlöser villkoret.|
|[TypeName-Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger ett .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definierar vilka typer av .NET som använder den här tabellposten eller villkor som måste finnas för den här posten som ska användas.|

## <a name="remarks"></a>Anmärkningar

Varje listpost måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.

När du definierar en urvalsvillkoret, gäller följande krav:

- Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skriptblock, men kan inte ange båda.

- Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.

Läs mer om hur du använder villkor för val av [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).

Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[Definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md)

[EntrySelectedBy Element (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[PropertyName-Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[ScriptBlock Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[SelectionSetName Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[TypeName-Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Skriva ett Windows PowerShell formatering och skriver fil](./writing-a-powershell-formatting-file.md)
