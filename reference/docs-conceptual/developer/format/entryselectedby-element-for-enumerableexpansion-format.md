---
title: EntrySelectedBy-element för EnumerableExpansion (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358987"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>EntrySelectedBy-element för EnumerableExpansion (format)

Definierar de .NET-typer som använder den här definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.

Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) EntrySelectedBy-element för EnumerableExpansion (format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `EntrySelectedBy`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.|
|[SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Anger en uppsättning .NET-typer som använder den här definitionen av hur samlings objekt expanderas.|
|[Elementet TypeName för EntrySelectedBy för EnumerableExpansion (format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som använder den här definitionen av hur samlings objekt expanderas.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EnumerableExpansion-element (format)](./enumerableexpansion-element-format.md)|Definierar hur vissa .NET Collection-objekt expanderas när de visas i en vy.|

## <a name="remarks"></a>Anmärkningar

Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en definitions post. Det finns ingen övre gräns för antalet underordnade element som du kan använda.

Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller ett angivet egenskaps värde eller skript utvärderar till `true`. Mer information om urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[Definiera villkor för visning av data](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion-element (format)](./enumerableexpansion-element-format.md)

[SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Elementet TypeName för EntrySelectedBy för EnumerableExpansion (format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
