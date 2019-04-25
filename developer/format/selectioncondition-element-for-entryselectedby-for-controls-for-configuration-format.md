---
title: SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075774"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)

Definierar ett villkor som måste finnas för en gemensam kontrolldefinition som ska användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för kontroller för (Format) CustomEntry konfigurationselement för anpassad kontroll för kontroller för (Format) EntrySelectedBy konfigurationselement för CustomEntry för kontroller för (Format) SelectionCondition konfigurationselement för EntrySelectedBy för CustomEntry för Konfiguration (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionCondition` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-Element för SelectionCondition för kontroller för konfiguration (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger en .NET-egenskap som utlöser villkoret.|
|[ScriptBlock Element för SelectionCondition för kontroller för konfiguration (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|
|[SelectionSetName Element för SelectionCondition för kontroller för konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger den uppsättning med .NET-typer som utlöser villkoret.|
|[TypeName-Element för SelectionCondition för kontroller för konfiguration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger ett .NET-typ som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för CustomEntry för kontroller för konfiguration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Definierar vilka typer av .NET som använder den här posten gemensam kontroll definition.|

## <a name="remarks"></a>Anmärkningar

Måste följa följande riktlinjer när du definierar ett val av villkor:

- Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skriptblock, men kan inte ange båda.

- Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.

Läs mer om hur du kan använda villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[PropertyName-Element för SelectionCondition för kontroller för konfiguration (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[ScriptBlock Element för SelectionCondition för kontroller för konfiguration (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[SelectionSetName Element för SelectionCondition för kontroller för konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[TypeName-Element för SelectionCondition för kontroller för konfiguration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[EntrySelectedBy Element för CustomEntry för kontroller för konfiguration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Skriva ett Windows PowerShell formatering och skriver fil](./writing-a-powershell-formatting-file.md)
