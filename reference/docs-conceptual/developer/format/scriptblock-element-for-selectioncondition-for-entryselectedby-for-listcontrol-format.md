---
title: Script block-element för SelectionCondition för EntrySelectedBy för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358927"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>ScriptBlock-element för SelectionCondition för EntrySelectedBy för ListControl (format)

Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och list posten används.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry element (format) EntrySelectedBy-element för ListEntry (format) SelectionCondition-element för EntrySelectedBy för ListEntry (format) script block-element för SelectionCondition för EntrySelectedBy för ListEntry (format)

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
|[SelectionCondition-element för EntrySelectedBy för ListEntry (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Definierar det villkor som måste finnas för att den här List posten ska kunna användas.|

## <a name="text-value"></a>Text värde

Ange det skript som utvärderas.

## <a name="remarks"></a>Anmärkningar

Urvals villkoret måste ange minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda. (Mer information om hur urvals villkor kan användas finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).)

Mer information om de andra komponenterna i en listvy finns i [listvyn](./creating-a-list-view.md).

## <a name="see-also"></a>Se även

[ListEntry-element (format)](./listentry-element-for-listcontrol-format.md)

[PropertyName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[SelectionCondition-element för EntrySelectedBy för ListEntry (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Listvy](./creating-a-list-view.md)

[Definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md)

[Skriva en Windows PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
