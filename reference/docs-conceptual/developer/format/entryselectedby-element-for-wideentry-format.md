---
title: EntrySelectedBy-element för WideEntry (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354756"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>EntrySelectedBy-element för WideEntry (format)

Definierar de .NET-typer som använder den här definitionen för wide View eller det villkor som måste finnas för att den här definitionen ska kunna användas.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format)

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
|[SelectionCondition-element för EntrySelectedBy för WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att denna wide View-definition ska användas.|
|[SelectionSetName-element för EntrySelectedBy för WideEntry (format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Valfritt element.<br /><br /> Anger en uppsättning av .NET-typer som använder denna wide View-definition.|
|[Elementet TypeName för EntrySelectedBy för WideEntry (format)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som använder denna wide View-definition.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideEntry-element (format)](./wideentry-element-for-widecontrol-format.md)|Ger en definition av den breda vyn.|

## <a name="remarks"></a>Anmärkningar

Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en wide View-definition. Det finns ingen övre gräns för antalet underordnade element som du kan använda.

Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller om ett angivet egenskaps värde eller skript värde utvärderas till `true`. Mer information om urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[WideEntry-element (format)](./wideentry-element-for-widecontrol-format.md)

[SelectionCondition-element för EntrySelectedBy för WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName-element för EntrySelectedBy för WideEntry (format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Elementet TypeName för EntrySelectedBy för WideEntry (format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Definiera villkor för visning av data](./defining-conditions-for-displaying-data.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
