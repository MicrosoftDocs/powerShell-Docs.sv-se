---
title: EntrySelectedBy-element för ListEntry för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355106"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>EntrySelectedBy-element för ListEntry för ListControl (format)

Definierar de .NET-typer som använder den här List vydefinitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas. I de flesta fall behövs bara en definition för en listvy. Du kan dock ange flera definitioner för listvyn om du vill använda samma listvy för att visa olika data för olika objekt.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntry för ListControl (format) EntrySelectedBy-element för ListEntry för ListControl (format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `EntrySelectedBy`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för ListControl (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den här List visnings definitionen ska kunna användas.|
|[SelectionSetName-element för EntrySelectedBy för ListControl (format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger en uppsättning av .NET-typer som använder den här List vydefinitionen.|
|[Elementet TypeName för EntrySelectedBy för ListControl (format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som använder den här List vydefinitionen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListEntry-element för ListControl (format)](./listentry-element-for-listcontrol-format.md)|Definierar hur rader i listan visas.|

## <a name="remarks"></a>Anmärkningar

Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en lista med en listvy. Det finns ingen övre gräns för antalet underordnade element som du kan använda.

Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller ett angivet egenskaps värde eller skript utvärderar till `true`. Mer information om urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du definierar objekten för en listvy med deras .NET-typnamn.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Se även

[ListEntry-element för ListControl (format)](./listentry-element-for-listcontrol-format.md)

[SelectionCondition-element för EntrySelectedBy för ListControl (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[SelectionSetName-element för EntrySelectedBy för ListControl (format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Elementet TypeName för EntrySelectedBy för ListControl (format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Skapa en listvy](./creating-a-list-view.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
