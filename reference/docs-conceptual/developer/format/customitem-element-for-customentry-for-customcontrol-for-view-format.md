---
title: CustomItem-element för CustomEntry för CustomControl för View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355190"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>CustomItem-element för CustomEntry för CustomControl för View (format)

Definierar vilka data som visas i vyn anpassad kontroll och hur den visas. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för vy (format)

## <a name="syntax"></a>Syntax

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `CustomItem`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem för CustomControl för View (format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Definierar de data som visas av kontrollen.|
|[Inramat element för CustomItem för CustomControl för vy (format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.|
|[Rad matnings element för CustomItem för anpassad kontroll för vy (format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Lägger till en tom rad i visningen av kontrollen.|
|[Text element för CustomItem för CustomControl för vy (format)](./text-element-for-customitem-for-customview-for-view-format.md)|Valfritt element.<br /><br /> Anger ytterligare text för de data som visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomEntries för CustomControl för View (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Innehåller en definition av den anpassade kontrollen.|

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[CustomEntry-element för CustomEntries för vy (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[ExpressionBinding-element för CustomItem för CustomControl för View (format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Inramat element för CustomItem för CustomControl för vy (format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Rad matnings element för CustomItem för CustomControl för vy (format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Text element för CustomItem för CustomControl för vy (format)](./text-element-for-customitem-for-customview-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
