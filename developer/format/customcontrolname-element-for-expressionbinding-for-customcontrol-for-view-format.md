---
title: CustomControlName Element för ExpressionBinding för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066625"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>CustomControlName-element för ExpressionBinding för CustomControl för View (format)

Anger namnet på en gemensam kontroll eller en kontroll. Det här elementet används när du definierar en anpassad kontroll vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll konfigurationselement för Visa (Format) CustomEntries elementet för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för CustomItem vy (Format) Element för CustomEntry för vyn (Format) ExpressionBinding elementet för CustomItem (Format) CustomControlName Element för uttrycket bindningen för CustomItem (Format)

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
|[ExpressionBinding Element för CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definierar de data som visas i kontrollen.|

## <a name="text-value"></a>Textvärde

Ange namnet på kontrollen.

## <a name="remarks"></a>Anmärkningar

Du kan skapa vanliga kontroller som kan användas av alla vyer av en formatering fil och du kan skapa vyn kontroller som kan användas av en specifik vy. Namnen på de här kontrollerna anges av följande element.

- [Namnelement för kontroll för kontroller för konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Namnelement för kontroll för kontroller för att visa (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Se även

[Namnelement för kontroll för kontroller för konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Namnelement för kontroll för kontroller för att visa (Format)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding Element för CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
