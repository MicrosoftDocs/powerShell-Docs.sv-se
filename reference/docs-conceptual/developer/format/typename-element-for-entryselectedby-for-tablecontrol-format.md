---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för EntrySelectedBy för TableControl (format)
description: TypeName-element för EntrySelectedBy för TableControl (format)
ms.openlocfilehash: 5a9f5cda1810d461d19ffb48a1cfa2d41f87ca96
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651426"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a>TypeName-element för EntrySelectedBy för TableControl (format)

Anger en .NET-typ som använder den här posten i vyn tabell. Det finns ingen gräns för antalet typer som kan anges för en tabell post.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry element (format) EntrySelectedBy element (format) element för EntrySelectedBy för TableRowEntry (format)

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
|[EntrySelectedBy-element (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definierar de .NET-typer som använder den här posten eller det villkor som måste finnas för att den här posten ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på .NET-typen.

## <a name="remarks"></a>Kommentarer

Varje List post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[EntrySelectedBy-element (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
