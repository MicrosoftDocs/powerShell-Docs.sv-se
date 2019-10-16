---
title: ExpressionBinding-element för CustomItem för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354658"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>ExpressionBinding-element för CustomItem för Controls för Configuration (format)

Definierar de data som visas av kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem element for CustomEntry for Controls for Configuration ExpressionBinding element for CustomItem for Controls for Configuration (format)

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
|[CustomControlName-element för ExpressionBinding för kontroller för konfiguration (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger namnet på en gemensam kontroll eller en visnings kontroll.|
|[EnumerateCollection-element för ExpressionBinding för kontroller för konfiguration (format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger att elementen i samlingar visas av kontrollen.|
|[ItemSelectionCondition-element för ExpressionBinding för kontroller för konfiguration (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att den här gemensamma kontrollen ska kunna användas.|
|[PropertyName-element för ExpressionBinding för kontroll av konfiguration (format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger .NET-egenskapen vars värde visas av den gemensamma kontrollen.|
|[Script block-element för ExpressionBinding för kontroller för konfiguration (format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger det skript vars värde visas av den gemensamma kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem-element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.|

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[CustomItem-element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
