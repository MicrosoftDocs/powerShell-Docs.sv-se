---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för GroupBy (format)
description: ScriptBlock-element för GroupBy (format)
ms.openlocfilehash: 117cbef93889046626741449886a1caaa39815cb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665251"
---
# <a name="scriptblock-element-for-groupby-format"></a>ScriptBlock-element för GroupBy (format)

Anger det skript som startar en ny grupp när dess värde ändras.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) script block-element för GroupBy (format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[GroupBy-element för View (format)](./groupby-element-for-view-format.md)|Definierar hur en grupp med .NET-objekt visas.|

## <a name="text-value"></a>Textvärde

Ange det skript som utvärderas.

## <a name="remarks"></a>Kommentarer

PowerShell startar en ny grupp när värdet för det här skriptet ändras.

När det här elementet har angetts kan du inte ange elementet [PropertyName](propertyname-element-for-groupby-format.md) för att starta en ny grupp.

## <a name="see-also"></a>Se även

[PropertyName-element för GroupBy (format)](propertyname-element-for-groupby-format.md)

[GroupBy-element för View (format)](groupby-element-for-view-format.md)

[Skriva en PowerShell-formateringsfil](writing-a-powershell-formatting-file.md)
