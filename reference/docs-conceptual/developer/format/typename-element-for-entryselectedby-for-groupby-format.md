---
title: Elementet TypeName för EntrySelectedBy för GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e62762cf142bd2d20b21ad8f4249285bd3679280
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780277"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a>TypeName-element för EntrySelectedBy för GroupBy (format)

Anger en .NET-typ som använder den här definitionen av den anpassade kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för visnings-(format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry element for CustomControl for groupby (format) EntrySelectedBy-element för CustomEntry

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
|[EntrySelectedBy-element för CustomEntry för GroupBy (format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..

## <a name="remarks"></a>Kommentarer

Varje kontroll definition måste ha minst ett typ namn, en markerings uppsättning eller ett urvals villkor definierat.

Mer information om komponenterna i en anpassad kontroll vy finns i [skapa anpassade kontroller](./creating-custom-controls.md).

## <a name="see-also"></a>Se även

[Skapa anpassade kontroller](./creating-custom-controls.md)

[EntrySelectedBy-element för CustomEntry för GroupBy (format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
