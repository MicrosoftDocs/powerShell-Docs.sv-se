---
title: TypeName-Element för EntrySelectedBy för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083968"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a>TypeName-element för EntrySelectedBy för TableControl (format)

Anger ett .NET-typ som använder den här posten i tabellvyn. Det finns ingen gräns för hur många typer som kan anges för en post.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName konfigurationselement för EntrySelectedBy för TableRowEntry (Format)

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
|[EntrySelectedBy Element (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definierar vilka typer av .NET som använder den här posten eller villkor som måste finnas för den här posten som ska användas.|

## <a name="text-value"></a>Textvärde

Ange namnet på .NET-typen.

## <a name="remarks"></a>Anmärkningar

Varje listpost måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.

Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[EntrySelectedBy Element (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
