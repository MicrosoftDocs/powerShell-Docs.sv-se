---
title: Elementet TypeName för EntrySelectedBy för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5e7b73db5aa597d96141454008c5c58b1827df24
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780227"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>TypeName-element för EntrySelectedBy för ListControl (format)

Anger en .NET-typ som använder den här posten i list visningen. Det finns ingen gräns för antalet typer som kan anges för en List post.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format) EntrySelectedBy-element för ListEntry (format) elementet TypeName för EntrySelectedBy (format)

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
|[EntrySelectedBy-element för ListEntry (format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Definierar de .NET-typer som använder den här List posten eller det villkor som måste finnas för att den här posten ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex `System.IO.DirectoryInfo` ..

## <a name="remarks"></a>Kommentarer

Varje List post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.

Mer information om hur det här elementet används i en listvy finns i [listvyn](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du anger en markerings uppsättning för en post i en listvy.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[EntrySelectedBy-element för ListEntry (format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[SelectionSetName-element för EntrySelectedBy för ListEntry (format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
