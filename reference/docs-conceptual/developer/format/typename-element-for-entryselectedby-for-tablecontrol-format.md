---
title: Elementet TypeName för EntrySelectedBy för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353566"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a>TypeName-element för EntrySelectedBy för TableControl (format)

Anger en .NET-typ som använder den här posten i vyn tabell. Det finns ingen gräns för antalet typer som kan anges för en tabell post.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) element för TableRowEntries (format) TableRowEntry element (format) EntrySelectedBy element (format) element för EntrySelectedBy för TableRowEntry (format)

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
|[EntrySelectedBy-element (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definierar de .NET-typer som använder den här posten eller det villkor som måste finnas för att den här posten ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på .NET-typen.

## <a name="remarks"></a>Anmärkningar

Varje List post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[EntrySelectedBy-element (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
