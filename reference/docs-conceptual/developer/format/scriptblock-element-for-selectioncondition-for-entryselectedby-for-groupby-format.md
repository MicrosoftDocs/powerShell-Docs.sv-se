---
title: Script block-element för SelectionCondition för EntrySelectedBy för GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358934"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a>ScriptBlock-element för SelectionCondition för EntrySelectedBy för GroupBy (format)

Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och definitionen används. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) EntrySelectedBy-element för CustomEntry för GroupBy (format) SelectionCondition-element för EntrySelectedBy för GroupBy (format) script block-element för SelectionCondition för GroupBy (format)

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
|[SelectionCondition-element för EntrySelectedBy för GroupBy (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.|

## <a name="text-value"></a>Text värde

Ange det skript som utvärderas.

## <a name="remarks"></a>Anmärkningar

Urvals villkoret måste ange minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda. Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[SelectionCondition-element för EntrySelectedBy för GroupBy (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
