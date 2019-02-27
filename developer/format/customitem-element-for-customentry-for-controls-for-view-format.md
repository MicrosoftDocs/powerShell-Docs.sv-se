---
title: CustomItem Element för CustomEntry för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846538"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>CustomItem-element för CustomEntry för Controls för View (format)

Definierar vilka data som visas av kontrollen och hur de visas. Det här elementet används när du definierar kontroller som kan användas av en vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för kontroller för att visa (Format) CustomItem Element för CustomEntry för kontroller för att visa (Format)

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomItem` element. Mer information finns i kommentarer.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding Element för CustomItem för kontroller för att visa (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Definierar de data som visas i kontrollen.|
|[Ramens Element för CustomItem för kontroller för att visa (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Definierar hur data visas, till exempel ändra datatypen till vänster eller höger.|
|[Ny rad-Element för CustomItem för kontroller för att visa (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Lägger till en tom rad visningen av kontrollen.|
|[Textelement för CustomItem för kontroller för att visa (Format)](./text-element-for-customitem-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Lägger till text, till exempel parenteser eller hakparenteser, visning av kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry Element för CustomEntries för kontroller för att visa (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Innehåller en definition av kontrollen.|

## <a name="remarks"></a>Anmärkningar

När du anger de underordnade elementen i den `CustomItem` element, Tänk på följande:

- De underordnade elementen måste läggas till i följande ordning: `ExpressionBinding`, `NewLine`, `Text`, och `Frame`.

- Det finns ingen högsta gräns för antalet sekvenser som du kan ange.

- Det finns ingen högsta gräns för antalet i varje sekvens `ExpressionBinding` element som du kan använda.

## <a name="see-also"></a>Se även

[ExpressionBinding Element för CustomItem för kontroller för att visa (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Ramens Element för CustomItem för kontroller för att visa (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Ny rad-Element för CustomItem för kontroller för att visa (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Textelement för CustomItem för kontroller för att visa (Format)](./text-element-for-customitem-for-controls-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
