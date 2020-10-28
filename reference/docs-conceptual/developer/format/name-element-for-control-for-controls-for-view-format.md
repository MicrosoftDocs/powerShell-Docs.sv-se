---
ms.date: 09/13/2016
ms.topic: reference
title: Name-element för Control för Controls för View (format)
description: Name-element för Control för Controls för View (format)
ms.openlocfilehash: 52b7170777a35596767c34f2d58106dfa6479567
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666492"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Name-element för Control för Controls för View (format)

Anger kontrollens namn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för att visa (format)-elementet för kontroll av visnings namn (format)

## <a name="syntax"></a>Syntax

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `Name` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Kontroll element för kontroller för vy (format)](./control-element-for-controls-for-view-format.md)|Definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.|

## <a name="text-value"></a>Textvärde

Ange det namn som ska användas för att referera till kontrollen.

## <a name="remarks"></a>Kommentarer

Namnet som anges här kan användas i följande element för att referera till den här kontrollen.

- När du skapar en tabell, lista, bred eller anpassad flikkontroll, kan kontrollen anges med följande element: [groupby-element för vy (format)](./groupby-element-for-view-format.md)

- När du skapar en annan kontroll som kan användas av en vy, kan den här kontrollen anges av följande element: [ExpressionBinding-element för CustomItem för kontroller för visning (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Se även

[GroupBy-element för View (format)](./groupby-element-for-view-format.md)

[ExpressionBinding-element för CustomItem för Controls för View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Kontroll element för kontroller för vy (format)](./control-element-for-controls-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
