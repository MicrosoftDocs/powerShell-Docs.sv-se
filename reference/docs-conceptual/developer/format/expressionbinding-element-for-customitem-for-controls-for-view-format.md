---
title: ExpressionBinding-element för CustomItem för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355071"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>ExpressionBinding-element för CustomItem för Controls för View (format)

Definierar de data som visas av kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl för visnings-(format) CustomEntry-element för CustomEntries for Controls for View (format) CustomItem-elementet for CustomEntry for Controls for View (format) ExpressionBinding element for CustomItem for Controls for View (format)

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `ExpressionBinding`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|`CustomControl Element`|Valfritt element.<br /><br /> Definierar en kontroll som används av den här kontrollen.|
|[CustomControlName-element för ExpressionBinding för kontroller för vy (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger namnet på en gemensam kontroll eller en visnings kontroll.|
|[EnumerateCollection-element för ExpressionBinding för kontroller för vy (format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger att elementen i samlingar visas.|
|[ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|
|[PropertyName-element för ExpressionBinding för kontroller för vy (format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap vars värde visas av kontrollen.|
|[Script block-element för ExpressionBinding för kontroller för vy (format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger det skript vars värde visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem-element för CustomEntry för kontroller för vy (format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definierar vilka data som visas av kontrollen och hur de visas.|

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[CustomItem-element för CustomEntry för kontroller för vy (format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[CustomControlName-element för ExpressionBinding för kontroller för vy (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[EnumerateCollection-element för ExpressionBinding för kontroller för vy (format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[PropertyName-element för ExpressionBinding för kontroller för vy (format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[Script block-element för ExpressionBinding för kontroller för vy (format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
