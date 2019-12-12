---
title: ExpressionBinding-element för CustomItem for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358961"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>ExpressionBinding-element för CustomItem för GroupBy (format)

Definierar de data som visas av kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) CustomItem-element för CustomEntry för GroupBy (format) ExpressionBinding-element för CustomItem för GroupBy (format)

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `ExpressionBinding`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|`CustomControl Element`|Valfritt element.<br /><br /> Definierar en kontroll som används av den här kontrollen.|
|[CustomControlName-element för ExpressionBinding för GroupBy (format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Valfritt element.<br /><br /> Anger namnet på en gemensam kontroll eller en visnings kontroll.|
|[EnumerateCollection-element för ExpressionBinding för groupby (format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) EnumerateCollection-element för ExpressionBinding för GroupBy (format)|Valfritt element.<br /><br /> Anger att samlings elementen visas.|
|[ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.|
|[PropertyName-element för ExpressionBinding för GroupBy (format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap vars värde visas av kontrollen.|
|[Script block-element för ExpressionBinding för GroupBy (format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Valfritt element.<br /><br /> Anger det skript vars värde visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem-element för CustomEntry för GroupBy (format)](./customitem-element-for-customentry-for-groupby-format.md)|Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.|

## <a name="see-also"></a>Se även

[CustomControlName-element för ExpressionBinding för GroupBy (format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[EnumerateCollection-element för ExpressionBinding för GroupBy (format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[PropertyName-element för ExpressionBinding för GroupBy (format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[Script block-element för ExpressionBinding för GroupBy (format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[CustomItem-element för CustomEntry för GroupBy (format)](./customitem-element-for-customentry-for-groupby-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
