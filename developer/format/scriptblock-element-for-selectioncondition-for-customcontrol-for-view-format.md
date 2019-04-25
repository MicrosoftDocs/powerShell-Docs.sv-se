---
title: ScriptBlock Element för SelectionCondition för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064568"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a>ScriptBlock-element för SelectionCondition för CustomControl för View (format)

Anger det skript som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och definitionen används. Det här elementet används när du definierar en anpassad kontroll vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll konfigurationselement för Visa (Format) CustomEntries elementet för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för anpassad kontroll för Visa ( Format) CustomItem Element för CustomEntry för anpassad kontroll för Visa (Format) SelectionCondition elementet för EntrySelectedBy för anpassad kontroll för Visa (Format) ScriptBlock elementet för SelectionCondition för anpassad kontroll för vy (Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition Element för EntrySelectedBy för anpassad kontroll för vy (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Definierar ett villkor som måste finnas för kontrolldefinition som ska användas.|

## <a name="text-value"></a>Textvärde

Ange det skript som ska utvärderas.

## <a name="remarks"></a>Anmärkningar

Urvalsvillkoret måste ange ett minst ett skript eller egenskapen namn för att utvärdera, men kan inte ange båda. Läs mer om hur du kan använda villkor för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Se även

[SelectionCondition Element för EntrySelectedBy för anpassad kontroll för vy (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
