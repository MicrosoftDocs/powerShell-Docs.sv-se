---
title: Kontrollera Element för kontrollerna för Visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845222"
---
# <a name="control-element-for-controls-for-view--format"></a>Control-element för Controls för View  (format)

Definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.

Elementet (Format) ViewDefinitions Element (Format) visa konfigurationselement (Format) styr Element (Format) kontroll Element för kontroller för vy (Format)

## <a name="syntax"></a>Syntax

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Control` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Namnelement för kontroll för vy (Format)](./name-element-for-control-for-controls-for-view-format.md)|Element som krävs.<br /><br /> Anger namnet på kontrollen.|
|[Anpassad kontroll Element för kontroll för kontroller för att visa (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Element som krävs.<br /><br /> Definierar den kontroll som används av den här vyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Kontroller Element (Format)](./controls-element-for-view-format.md)|Definierar vyn kontroller som kan användas av en specifik vy.|

## <a name="remarks"></a>Anmärkningar

Den här kontrollen kan anges med följande element:

- [CustomControlName Element för ExpressionBinding för kontroller för att visa (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [CustomControlName Element för ExpressionBinding för anpassad kontroll för vy (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [CustomControlName Element för ExpressionBinding för GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [CustomControlName Element för GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Se även

[Anpassad kontroll Element för kontroll för kontroller för att visa (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[CustomControlName Element för ExpressionBinding för kontroller för att visa (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[CustomControlName Element för ExpressionBinding för anpassad kontroll för vy (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControlName Element för ExpressionBinding för GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[CustomControlName Element för ExpressionBinding för GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Kontroller Element (Format)](./controls-element-for-view-format.md)

[Namnelement för kontroll för kontroller för att visa (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
