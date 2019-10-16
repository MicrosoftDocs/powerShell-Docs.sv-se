---
title: Kontroll element för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354854"
---
# <a name="control-element-for-controls-for-view--format"></a>Control-element för Controls för View  (format)

Definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) kontroll element för vyer (format)

## <a name="syntax"></a>Syntax

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `Control`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Namn element för kontroll för vy (format)](./name-element-for-control-for-controls-for-view-format.md)|Nödvändigt element.<br /><br /> Anger kontrollens namn.|
|[CustomControl-element för kontroll för vy (format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Nödvändigt element.<br /><br /> Definierar den kontroll som används i den här vyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Kontrollerar element (format)](./controls-element-for-view-format.md)|Definierar de visnings kontroller som kan användas av en speciell vy.|

## <a name="remarks"></a>Anmärkningar

Den här kontrollen kan anges med följande element:

- [CustomControlName-element för ExpressionBinding för kontroller för vy (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [CustomControlName-element för ExpressionBinding för CustomControl för View (format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [CustomControlName-element för ExpressionBinding för GroupBy (format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [CustomControlName-element för GroupBy (format)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Se även

[CustomControl-element för kontroll för vy (format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[CustomControlName-element för ExpressionBinding för kontroller för vy (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[CustomControlName-element för ExpressionBinding för CustomControl för View (format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControlName-element för ExpressionBinding för GroupBy (format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[CustomControlName-element för ExpressionBinding för GroupBy (format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Kontrollerar element (format)](./controls-element-for-view-format.md)

[Namn element för kontroll för vy (format)](./name-element-for-control-for-controls-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
