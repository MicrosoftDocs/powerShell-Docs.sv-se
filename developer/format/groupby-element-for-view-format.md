---
title: GroupBy-Element för Visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849282"
---
# <a name="groupby-element-for-view-format"></a>GroupBy-element för View (format)

Definierar hur en ny grupp med objekt visas. Det här elementet används när du definierar en tabell, lista, brett eller anpassad vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för vy (Format)

## <a name="syntax"></a>Syntax

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, element i underordnade och överordnade element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Anpassad kontroll Element för GroupBy (Format)](./customcontrol-element-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar den anpassade kontrollen som visar nya grupper.|
|[CustomControlName Element för GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger namnet på en kontroll som används för att visa den nya gruppen.|
|[Etikettelement för GroupBy (Format)](./label-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger en etikett som visas när en ny grupp har påträffats.|
|[PropertyName-Element för GroupBy (Format)](./propertyname-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger egenskapen .NET startar en ny grupp när dess värde ändras.|
|[ScriptBlock Element för GroupBy (Format)](./scriptblock-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger det skript som startar en ny grupp när dess värde ändras.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Visa Element (Format)](./view-element-format.md)|Definierar en vy som visar en eller flera .NET-objekt.|

## <a name="remarks"></a>Anmärkningar

När du definierar hur en ny grupp med objekt visas, måste du ange egenskapen eller skript som startar den nya gruppen; Du kan dock ange båda.

## <a name="see-also"></a>Se även

[CustomControlName Element för GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

[Etikettelement för GroupBy (Format)](./label-element-for-groupby-format.md)

[PropertyName-Element för GroupBy (Format)](./propertyname-element-for-groupby-format.md)

[ScriptBlock Element för GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[Visa Element (Format)](./view-element-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
