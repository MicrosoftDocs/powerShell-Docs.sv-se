---
title: CustomControlName-element för ExpressionBinding för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 871c6afd89db9360ea5012191b08863a9441f899
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786024"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>CustomControlName-element för ExpressionBinding för Controls för View (format)

Anger namnet på en gemensam kontroll eller en visnings kontroll. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för Control for View (format) CustomEntries-element för CustomControl för visning (format) CustomEntry-element för CustomEntries for Controls for View (format) CustomItem-element för CustomEntry for Controls for View (format) ExpressionBinding-elementet for CustomItem for Controls for View (format) CustomControlName element for ExpressionBindine for Controls for View (format)

## <a name="syntax"></a>Syntax

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `CustomControlName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem för Controls för View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Definierar de data som visas av kontrollen.|

## <a name="text-value"></a>Textvärde

Ange namnet på kontrollen.

## <a name="remarks"></a>Kommentarer

Du kan skapa vanliga kontroller som kan användas av alla vyer i en fil format och du kan skapa visnings kontroller som kan användas av en speciell vy. Följande element anger namnen på dessa kontroller:

- [Name-element för Control för Controls för Configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name-element för Control för Controls för View (format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Se även

[Name-element för Control för Controls för Configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name-element för Control för Controls för View (format)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding-element för CustomItem för Controls för View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
