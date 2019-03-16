---
title: SelectionCondition Element för EntrySelectedBy för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 633204f3b181316761746ea2679910216fb74657
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058972"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>SelectionCondition-element för EntrySelectedBy för ListControl (format)

Definierar de villkor som måste finnas för att använda den här definitionen i listvyn. Det finns ingen gräns för hur många val av villkor som kan anges för en definition av listan.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy konfigurationselement för ListEntry (Format) SelectionCondition elementet för EntrySelectedBy för ListEntry (Format)

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
|[PropertyName-Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[ScriptBlock Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|
|[SelectionSetName Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|Valfritt element.<br /><br /> Anger uppsättningen med .NET-typer som utlöser villkoret.|
|[TypeName-Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger ett .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definierar vilka typer av .NET som använder den här tabellposten eller villkor som måste finnas för den här posten som ska användas.|

## <a name="remarks"></a>Anmärkningar

lWhen som du definierar ett villkor för val av följande krav gäller:

- Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skriptblock, men kan inte ange båda.

- Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.

Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).

Läs mer om andra komponenter i en listvy, [skapar en listvy](./creating-a-list-view.md).

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[Definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md)

[ListEntry Element (Format)](./listentry-element-for-listcontrol-format.md)

[SelectionSetName Element för EntrySelectedBy för ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[TypeName-Element för EntrySelectedBy för ListEntry (Format)](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
