---
title: EntrySelectedBy-element för CustomEntry för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355148"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>EntrySelectedBy-element för CustomEntry för Controls för View (format)

Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl for Controls for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) EntrySelectedBy element for CustomEntry for Controls for View (format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och ett överordnat element för elementet `EntrySelectedBy`. Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en definition. Det finns ingen övre gräns för antalet underordnade element som du kan använda.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för kontroller för vy (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.|
|[SelectionSetName-element för EntrySelectedBy för kontroller för vy (format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen.|
|[Elementet TypeName för EntrySelectedBy för kontroller för vyn (format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som använder den här definitionen av kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomEntries för kontroller för vy (format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Ger en definition av kontrollen.|

## <a name="remarks"></a>Anmärkningar

Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller när ett angivet egenskaps värde eller skript utvärderar till `true`. Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[CustomEntry-element för CustomEntries för kontroller för vy (format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
