---
title: ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846209"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>ExpressionBinding-element för CustomItem för Controls för Configuration (format)

Definierar de data som visas i kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) CustomItem konfigurationselement för CustomEntry för kontroller för ExpressionBinding konfigurationselement för CustomItem för kontroller för konfiguration (Format)

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
|[CustomControlName Element för ExpressionBinding för kontroller för konfiguration (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger namnet på en gemensam kontroll eller en kontroll.|
|[EnumerateCollection Element för ExpressionBinding för kontroller för konfiguration (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Ange att elementen i samlingar visas i kontrollen.|
|[ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar de villkor som måste finnas för den här vanliga kontrollen som ska användas.|
|[PropertyName-Element för ExpressionBinding för kontroller för konfiguration (Format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger egenskapen .NET vars värde visas som vanliga kontrollen.|
|[ScriptBlock Element för ExpressionBinding för kontroller för konfiguration (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger skriptet vars värde visas som vanliga kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem Element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definierar vilka data som visas i vyn anpassad kontroll och hur de visas.|

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[CustomItem Element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
