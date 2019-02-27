---
title: EntrySelectedBy Element för CustomEntry för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: e930e4422afd203feda6a389655ff8a355e3bec0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848680"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)

Definierar vilka typer av .NET som använder definitionen av den vanliga kontrollen eller villkor som måste finnas för den här kontrollen som ska användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) EntrySelectedBy konfigurationselement för CustomEntry för kontroller för konfiguration (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EntrySelectedBy` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar de villkor som måste finnas för de gemensamma definitionerna för kontrollen som ska användas.|
|[SelectionSetName Element för EntrySelectedBy för kontroller för konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger en uppsättning med .NET-typer som använder den här definitionen för vanliga kontrollen.|
|[TypeName-Element för EntrySelectedBy för kontroller för konfiguration (Format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger ett .NET-typ som använder den här definitionen för vanliga kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Innehåller en definition av vanliga kontrollen.|

## <a name="remarks"></a>Anmärkningar

Varje definition måste minst ha minst en .NET-typ, val av set eller val av villkoret. Det finns ingen högsta gräns för hur många typer, val av uppsättningar eller val av villkor som du kan ange.

## <a name="see-also"></a>Se även

[SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[SelectionSetName Element för EntrySelectedBy för kontroller för konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[TypeName-Element för EntrySelectdBy för kontroller för konfiguration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
