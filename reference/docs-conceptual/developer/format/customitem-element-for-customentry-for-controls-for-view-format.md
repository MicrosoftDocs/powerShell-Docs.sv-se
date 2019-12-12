---
title: CustomItem-element för CustomEntry för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355183"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>CustomItem-element för CustomEntry för Controls för View (format)

Definierar vilka data som visas av kontrollen och hur de visas. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl för visnings-(format) CustomEntry-element för CustomEntries för Controls för View (format) CustomItem-elementet för CustomEntry för kontroller för vy (format)

## <a name="syntax"></a>Syntax

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `CustomItem`-elementet. Mer information finns i kommentarer.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem för kontroller för vy (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Definierar de data som visas av kontrollen.|
|[Ram element för CustomItem för kontroller för vy (format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Definierar hur data visas, till exempel att flytta data till vänster eller höger.|
|[Rad matnings element för CustomItem för kontroller för vy (format)](./newline-element-for-customitem-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Lägger till en tom rad i visningen av kontrollen.|
|[Text element för CustomItem för kontroller för vy (format)](./text-element-for-customitem-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Lägger till text, till exempel parenteser eller hakparenteser, för att Visa kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomEntries för kontroller för vy (format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Ger en definition av kontrollen.|

## <a name="remarks"></a>Anmärkningar

Tänk på följande när du anger underordnade element för `CustomItem`-elementet:

- De underordnade elementen måste läggas till i följande ordning: `ExpressionBinding`, `NewLine`, `Text`och `Frame`.

- Det finns ingen övre gräns för antalet sekvenser som du kan ange.

- I varje sekvens finns det ingen övre gräns för antalet `ExpressionBinding`-element som du kan använda.

## <a name="see-also"></a>Se även

[ExpressionBinding-element för CustomItem för kontroller för vy (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Ram element för CustomItem för kontroller för vy (format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Rad matnings element för CustomItem för kontroller för vy (format)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Text element för CustomItem för kontroller för vy (format)](./text-element-for-customitem-for-controls-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
