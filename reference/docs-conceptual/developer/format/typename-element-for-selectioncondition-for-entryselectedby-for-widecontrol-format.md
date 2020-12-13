---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för SelectionCondition för EntrySelectedBy för WideControl (format)
description: TypeName-element för SelectionCondition för EntrySelectedBy för WideControl (format)
ms.openlocfilehash: af6e4782c345b43e16bce59c333bdaaceba0d845
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645502"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>TypeName-element för SelectionCondition för EntrySelectedBy för WideControl (format)

Anger en .NET-typ som utlöser villkoret. När den här typen finns används definitionen.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition-element för EntrySelectedBy för WideEntry (format) element för SelectionCondition (format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Definierar det villkor som måste finnas för att den här breda posten ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..

## <a name="remarks"></a>Kommentarer

Urvals villkoret kan ange en .NET-typ eller en urvals uppsättning, men kan inte ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[SelectionCondition-element för EntrySelectedBy för WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
