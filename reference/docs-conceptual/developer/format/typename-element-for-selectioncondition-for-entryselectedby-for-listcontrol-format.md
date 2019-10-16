---
title: Elementet TypeName för SelectionCondition för EntrySelectedBy för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353517"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>TypeName-element för SelectionCondition för EntrySelectedBy för ListControl (format)

Anger en .NET-typ som utlöser villkoret. När den här typen finns används List posten.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) EntrySelectedBy-element för ListEntry för ListControl (format) SelectionCondition-element för EntrySelectedBy för ListControl (format) TypeName-element för SelectionCondition för EntrySelectedBy (format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `TypeName`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för ListControl (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Definierar det villkor som måste finnas för att den här List posten ska kunna användas.|

## <a name="text-value"></a>Text värde

Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex. `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Anmärkningar

Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

Mer information om andra komponenter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[SelectionCondition-element för EntrySelectedBy för ListControl (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
