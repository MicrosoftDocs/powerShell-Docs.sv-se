---
title: EntrySelectedBy-element för CustomEntry för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359005"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)

Definierar de .NET-typer som använder definitionen av den gemensamma kontrollen eller villkoret som måste finnas för att den här kontrollen ska kunna användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) EntrySelectedBy-element för CustomEntry för kontroll av konfiguration (format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `EntrySelectedBy`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för kontroller för konfiguration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den gemensamma kontroll definitionen ska kunna användas.|
|[SelectionSetName-element för EntrySelectedBy för kontroller för konfiguration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger en uppsättning av .NET-typer som använder den här definitionen av den gemensamma kontrollen.|
|[Elementet TypeName för EntrySelectedBy för kontroller för konfiguration (format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger en .NET-typ som använder den här definitionen av den gemensamma kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomControl för kontroller för konfiguration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Ger en definition av den gemensamma kontrollen.|

## <a name="remarks"></a>Anmärkningar

Varje definition måste minst ha minst en .NET-typ, markerings uppsättning eller ett urvals villkor angivet. Det finns ingen övre gräns för antalet typer, markerings uppsättningar eller markerings villkor som du kan ange.

## <a name="see-also"></a>Se även

[SelectionCondition-element för EntrySelectedBy för kontroller för konfiguration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[SelectionSetName-element för EntrySelectedBy för kontroller för konfiguration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[CustomEntry-element för CustomControl för kontroller för konfiguration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Elementet TypeName för EntrySelectedBy för kontroller för konfiguration (format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
