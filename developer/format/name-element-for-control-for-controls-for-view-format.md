---
title: Namnge Element för kontroll för kontroller för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065112"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Name-element för Control för Controls för View (format)

Anger namnet på kontrollen.

Elementet (Format) ViewDefinitions Element (Format) visa konfigurationselement (Format) styr Element (Format) kontroll Element för kontroller för namnelement vy (Format) för kontroll för vy (Format)

## <a name="syntax"></a>Syntax

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Name` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Control-Element för kontroller för att visa (Format)](./control-element-for-controls-for-view-format.md)|Definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.|

## <a name="text-value"></a>Textvärde

Ange ett namn som används för att referera till kontrollen.

## <a name="remarks"></a>Anmärkningar

Namnet som anges här kan användas i följande element för att referera till den här kontrollen.

- När du skapar en tabell, lista, brett eller anpassade vy, kan kontrollen anges med följande element: [GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)

- När du skapar en annan kontroll som kan användas av en vy, kan den här kontrollen anges med följande element: [ExpressionBinding Element för CustomItem för kontroller för att visa (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Se även

[GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)

[ExpressionBinding Element för CustomItem för kontroller för att visa (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Control-Element för kontroller för att visa (Format)](./control-element-for-controls-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
