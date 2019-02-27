---
title: CustomControlName Element för ExpressionBinding för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845621"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>CustomControlName-element för ExpressionBinding för GroupBy (format)

Anger namnet på en gemensam kontroll eller en kontroll. Det här elementet används när du definierar hur en ny grupp med objekt visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) CustomItem elementet för CustomEntry för GroupBy (Format) ExpressionBinding elementet för CustomItem för GroupBy (Format) CustomControlName elementet för ExpressionBinding för GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomControlName` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding Element för CustomItem för GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definierar de data som visas i kontrollen.|

## <a name="text-value"></a>Textvärde

Ange namnet på kontrollen.

## <a name="remarks"></a>Anmärkningar

Du kan skapa vanliga kontroller som kan användas av alla vyer av en formatering fil och du kan skapa vyn kontroller som kan användas av en specifik vy. Följande element ange namnen på de här kontrollerna:

- [Namnelement för kontroll för kontroller för konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Namnelement för kontroll för kontroller för att visa (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Se även

[Namnelement för kontroll för kontroller för konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Namnelement för kontroll för kontroller för att visa (Format)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding Element för CustomItem för GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
