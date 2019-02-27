---
title: CustomItem Element för CustomEntry för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846944"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>CustomItem-element för CustomEntry för CustomControl för View (format)

Definierar vilka data som visas i vyn anpassad kontroll och hur de visas. Det här elementet används när du definierar en anpassad kontroll vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för vyn (Format) CustomItem elementet för CustomEntry för vy (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomItem` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding Element för CustomItem för anpassad kontroll för vy (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Definierar de data som visas i kontrollen.|
|[Ramens Element för CustomItem för anpassad kontroll för vy (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Definierar vilka data som visas i vyn anpassad kontroll och hur de visas.|
|[Ny rad-Element för CustomItem för anpassad kontroll för vy (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Lägger till en tom rad visningen av kontrollen.|
|[Textelement för CustomItem för anpassad kontroll för vy (Format)](./text-element-for-customitem-for-customview-for-view-format.md)|Valfritt element.<br /><br /> Anger ytterligare text till data som visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry Element för CustomEntries för anpassad kontroll för vy (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Innehåller en definition av vyn anpassad kontroll.|

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[CustomEntry Element för CustomEntries för vy (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[ExpressionBinding Element för CustomItem för anpassad kontroll för vy (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Ramens Element för CustomItem för anpassad kontroll för vy (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Ny rad-Element för CustomItem för anpassad kontroll för vy (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Textelement för CustomItem för anpassad kontroll för vy (Format)](./text-element-for-customitem-for-customview-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
