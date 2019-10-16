---
title: Script block-element för SelectionCondition för EntrySelectedBy för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358910"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>ScriptBlock-element för SelectionCondition för EntrySelectedBy för WideControl (format)

Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och den breda post definitionen används.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition-element för EntrySelectedBy för WideEntry (format) script block-element för SelectionCondition för EntrySelectedBy för WideEntry (format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `ScriptBlock`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.|

## <a name="text-value"></a>Text värde

Ange det skript som utvärderas.

## <a name="remarks"></a>Anmärkningar

Urvals villkoret måste innehålla minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda. Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

Mer information om andra komponenter i en bred vy finns i [wide View](./creating-a-wide-view.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[SelectionCondition-element för EntrySelectedBy för WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
