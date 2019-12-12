---
title: Elementet TypeName för SelectionCondition för EntrySelectedBy för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353454"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>TypeName-element för SelectionCondition för EntrySelectedBy för TableControl (format)

Anger en .NET-typ som utlöser villkoret. När den här typen är närvarande uppfylls villkoret och tabell raden används.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition-element för EntrySelectedBy för TableRowEntry (format) elementet TypeName för SelectionCondition för EntrySelectedBy för TableRowEntry (format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `TypeName`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Definierar det villkor som måste finnas för att den här tabell raden ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex. `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Anmärkningar

Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
