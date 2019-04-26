---
title: TypeName-Element för SelectionCondition för EntrySelectedBy för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083849"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>TypeName-element för SelectionCondition för EntrySelectedBy för TableControl (format)

Anger ett .NET-typ som utlöser villkoret. Om den här typen finns villkoret uppfylls och tabellraden används.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy konfigurationselement för TableRowEntry (Format) SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format) TypeName-elementet för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Definierar de villkor som måste finnas för den här tabellraden som ska användas.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typ, till exempel `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Anmärkningar

Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda. Läs mer om hur du använder villkor för val av [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).

Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[Definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md)

[SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[SelectionSetName Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
