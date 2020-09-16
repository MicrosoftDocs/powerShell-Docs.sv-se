---
title: Namn element för kontroll för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 109f3a40606dbe82322decf0c69d2367c75175f6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781094"
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
