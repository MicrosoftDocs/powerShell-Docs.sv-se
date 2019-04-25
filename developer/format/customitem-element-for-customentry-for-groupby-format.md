---
title: CustomItem Element för CustomEntry för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066407"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>CustomItem-element för CustomEntry för GroupBy (format)

Definierar vilka data som visas i vyn anpassad kontroll och hur de visas. Det här elementet används när du definierar hur en ny grupp med objekt visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomItem elementet för CustomEntry för GroupBy (Format)

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
|[ExpressionBinding Element för CustomItem för GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar de data som visas i kontrollen.|
|[Ramens Element för CustomItem för GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar vilka data som visas i vyn anpassad kontroll och hur de visas.|
|[Ny rad-Element för CustomItem för GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md)|Valfritt element.<br /><br /> Lägger till en tom rad visningen av kontrollen.|
|[Textelement för CustomItem för GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md)|Valfritt element.<br /><br /> Anger ytterligare text till data som visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry Element för anpassad kontroll för GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Innehåller en definition av vyn anpassad kontroll.|

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[CustomEntry Element för anpassad kontroll för GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)

[ExpressionBinding Element för CustomItem för GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Ramens Element för CustomItem för GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[Ny rad-Element för CustomItem för GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md)

[Textelement för CustomItem för GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
