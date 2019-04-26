---
title: ExpressionBinding Element för CustomItem för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065911"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>ExpressionBinding-element för CustomItem för GroupBy (format)

Definierar de data som visas i kontrollen. Det här elementet används när du definierar hur en ny grupp med objekt visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) CustomItem elementet för CustomEntry för GroupBy (Format) ExpressionBinding elementet för CustomItem för GroupBy (Format)

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
|[CustomControlName Element för ExpressionBinding för GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Valfritt element.<br /><br /> Anger namnet på en gemensam kontroll eller en kontroll.|
|[EnumerateCollection Element för ExpressionBinding för GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element för ExpressionBinding för GroupBy (Format)|Valfritt element.<br /><br /> Ange att elementen i samlingar visas.|
|[ItemSelectionCondition Element för ExpressionBinding för GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar de villkor som måste finnas för den här kontrollen som ska användas.|
|[PropertyName-Element för ExpressionBinding för GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Valfritt element.<br /><br /> Anger egenskapen .NET vars värde visas i kontrollen.|
|[ScriptBlock Element för ExpressionBinding för GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Valfritt element.<br /><br /> Anger skriptet vars värde visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem Element för CustomEntry för GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Definierar vilka data som visas i vyn anpassad kontroll och hur de visas.|

## <a name="see-also"></a>Se även

[CustomControlName Element för ExpressionBinding för GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[EnumerateCollection Element för ExpressionBinding för GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[ItemSelectionCondition Element för ExpressionBinding för GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[PropertyName-Element för ExpressionBinding för GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[ScriptBlock Element för ExpressionBinding för GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[CustomItem Element för CustomEntry för GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
