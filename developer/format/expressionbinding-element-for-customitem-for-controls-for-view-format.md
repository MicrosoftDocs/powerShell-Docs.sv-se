---
title: ExpressionBinding Element för CustomItem för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848421"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>ExpressionBinding-element för CustomItem för Controls för View (format)

Definierar de data som visas i kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för kontroller för att visa (Format) CustomItem Element för CustomEntry för kontroller för att visa (Format) ExpressionBinding Element för CustomItem för kontroller för att visa (Format)

## <a name="syntax"></a>Syntax

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ExpressionBinding` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|`CustomControl Element`|Valfritt element.<br /><br /> Definierar en kontroll som används av den här kontrollen.|
|[CustomControlName Element för ExpressionBinding för kontroller för att visa (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger namnet på en gemensam kontroll eller en kontroll.|
|[EnumerateCollection Element för ExpressionBinding för kontroller för att visa (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger att elementen i samlingar visas.|
|[ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Definierar de villkor som måste finnas för den här kontrollen som ska användas.|
|[PropertyName-Element för ExpressionBinding för kontroller för att visa (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger egenskapen .NET vars värde visas i kontrollen.|
|[ScriptBlock Element för ExpressionBinding för kontroller för att visa (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger skriptet vars värde visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem Element för CustomEntry för kontroller för att visa (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definierar vilka data som visas av kontrollen och hur de visas.|

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[CustomItem Element för CustomEntry för kontroller för att visa (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[CustomControlName Element för ExpressionBinding för kontroller för att visa (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[EnumerateCollection Element för ExpressionBinding för kontroller för att visa (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[PropertyName-Element för ExpressionBinding för kontroller för att visa (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[ScriptBlock Element för ExpressionBinding för kontroller för att visa (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
