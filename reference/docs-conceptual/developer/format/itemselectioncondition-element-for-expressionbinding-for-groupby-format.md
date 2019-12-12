---
title: ItemSelectionCondition-element för ExpressionBinding for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356128"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)

Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas. Det finns ingen gräns för antalet urvals villkor som kan anges för ett kontroll objekt. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) CustomItem-element för CustomEntry för GroupBy (format) ExpressionBinding-element för CustomItem för GroupBy (format) ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)

## <a name="syntax"></a>Syntax

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `ItemSelectionCondition`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-element för ItemSelectionCondition för GroupBy (format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[Script block-element för ItemSelectionCondition för GroupBy (format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem för GroupBy (format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definierar de data som visas av kontrollen.|

## <a name="remarks"></a>Anmärkningar

Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.

## <a name="see-also"></a>Se även

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)

[ExpressionBinding-element för CustomItem för GroupBy (format)](./expressionbinding-element-for-customitem-for-groupby-format.md)
