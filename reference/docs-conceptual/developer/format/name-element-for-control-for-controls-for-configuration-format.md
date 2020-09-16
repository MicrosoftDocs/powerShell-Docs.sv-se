---
title: Namn element för kontroll för konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3d45ba98b909ebee18e01d2b6985a48906ce39d9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783542"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Name-element för Control för Controls för Configuration (format)

Anger kontrollens namn. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations element (format) kontroll element för kontroll av namn element för konfiguration (format) för kontroll för konfiguration av kontroller (format)

## <a name="syntax"></a>Syntax

```xml
<Name>NameOfControl</Name>

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
|[Control-element för Controls för Configuration (format)](./control-element-for-controls-for-configuration-format.md)|Definierar en gemensam kontroll som kan användas av alla vyer i format filen och det namn som används för att referera till kontrollen.|

## <a name="text-value"></a>Textvärde

Ange det namn som ska användas för att referera till den här kontrollen.

## <a name="remarks"></a>Kommentarer

Namnet som anges här kan användas i följande element för att referera till den här kontrollen.

- När du skapar en tabell, lista, bred eller anpassad flikkontroll, kan kontrollen anges med följande element: [groupby-element för vy (format)](./groupby-element-for-view-format.md)

- När du skapar en annan gemensam kontroll, kan den här kontrollen anges av följande element: [ExpressionBinding-element för CustomItem för kontroller för konfiguration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- När du skapar en kontroll som kan användas av en vy, kan den här kontrollen anges med följande element: [ExpressionBinding-element för CustomItem för kontroller för vy (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Se även

[Control-element för Controls för Configuration (format)](./control-element-for-controls-for-configuration-format.md)

[ExpressionBinding-element för CustomItem för Controls för Configuration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[ExpressionBinding-element för CustomItem för Controls för View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[GroupBy-element för View (format)](./groupby-element-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
