---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för EntrySelectedBy för WideEntry (format)
description: TypeName-element för EntrySelectedBy för WideEntry (format)
ms.openlocfilehash: 2e0facd6ff7c6fec96dabf488449a8502429bcff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654784"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>TypeName-element för EntrySelectedBy för WideEntry (format)

Anger en .NET-typ för definitionen. Definitionen används när det här objektet visas.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format) element för WideEntry (format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `TypeName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för WideEntry (format)](./entryselectedby-element-for-wideentry-format.md)|Definierar de .NET-typer som använder den här breda posten eller det villkor som måste finnas för att den här posten ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..

## <a name="remarks"></a>Kommentarer

Varje bred post måste innehålla en eller flera .NET-typer, en urvals uppsättning eller ett urvals villkor som måste finnas för att definitionen ska kunna användas.

Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[EntrySelectedBy-element för WideEntry (format)](./entryselectedby-element-for-wideentry-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
