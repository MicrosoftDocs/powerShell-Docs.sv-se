---
title: Elementet TypeName för EntrySelectedBy för WideEntry (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353559"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>TypeName-element för EntrySelectedBy för WideEntry (format)

Anger en .NET-typ för definitionen. Definitionen används när det här objektet visas.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) EntrySelectedBy-element för WideEntry (format) elementet TypeName för WideEntry ( Formatering

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `TypeName`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för WideEntry (format)](./entryselectedby-element-for-wideentry-format.md)|Definierar de .NET-typer som använder den här breda posten eller det villkor som måste finnas för att den här posten ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex. `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Anmärkningar

Varje bred post måste innehålla en eller flera .NET-typer, en urvals uppsättning eller ett urvals villkor som måste finnas för att definitionen ska kunna användas.

Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[EntrySelectedBy-element för WideEntry (format)](./entryselectedby-element-for-wideentry-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
