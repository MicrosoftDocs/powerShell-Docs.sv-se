---
title: CustomControlName-element för ExpressionBinding för CustomControl för View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355302"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>CustomControlName-element för ExpressionBinding för CustomControl för View (format)

Anger namnet på en gemensam kontroll eller en visnings kontroll. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem Element för CustomEntry för View (format) ExpressionBinding-element för CustomItem (format) CustomControlName-elementet för uttrycks bindning för CustomItem (format)

## <a name="syntax"></a>Syntax

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `CustomControlName`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definierar de data som visas av kontrollen.|

## <a name="text-value"></a>Text värde

Ange namnet på kontrollen.

## <a name="remarks"></a>Anmärkningar

Du kan skapa vanliga kontroller som kan användas av alla vyer i en fil format och du kan skapa visnings kontroller som kan användas av en speciell vy. Namnen på dessa kontroller anges med följande element.

- [Namn element för kontroll för konfiguration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Namn element för kontroll för vy (format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Se även

[Namn element för kontroll för konfiguration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Namn element för kontroll för vy (format)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding-element för CustomItem (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
