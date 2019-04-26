---
title: TypeName-Element för EntrySelectedBy för WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083934"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>TypeName-element för EntrySelectedBy för WideEntry (format)

Anger en .NET-typ för definitionen. Definitionen används när det här objektet visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format) TypeName-elementet för WideEntry ( Format)

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
|[EntrySelectedBy Element för WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Definierar vilka typer av .NET som använder den här wide posten eller villkor som måste finnas för den här posten som ska användas.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typ, till exempel `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Anmärkningar

Varje post i wide måste ange en eller flera typer i .NET eller en Urvalsvillkoret som måste finnas för definitionen som ska användas.

Mer information om andra komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[EntrySelectedBy Element för WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
