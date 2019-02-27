---
title: TypeName-Element för EntrySelectedBy för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846888"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>TypeName-element för EntrySelectedBy för ListControl (format)

Anger ett .NET-typ som använder den här posten i listvyn. Det finns ingen gräns för hur många typer som kan anges för en listpost.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy konfigurationselement för ListEntry (Format) TypeName-elementet för EntrySelectedBy för ListControl (Format)

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
|[EntrySelectedBy Element för ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Definierar vilka typer av .NET som använder den här posten eller villkor som måste finnas för den här posten som ska användas.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet på .NET-typ som `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Anmärkningar

Varje listpost måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.

Läs mer om hur det här elementet används i en listvy [listvyn](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du anger ett urval som angetts för en post av en listvy.

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

[EntrySelectedBy Element för ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[SelectionSetName Element för EnrtySelectedBy för ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
