---
title: Namnge Element för kontroll för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065197"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Name-element för Control för Controls för Configuration (format)

Anger namnet på kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för Configuration (Format) namnelement för kontroll för kontroller för konfiguration (Format)

## <a name="syntax"></a>Syntax

```xml
<Name>NameOfControl</Name>

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
|[Control-Element för kontroller för Configuration (Format)](./control-element-for-controls-for-configuration-format.md)|Definierar en gemensam kontroll som kan användas av alla vyer av filen formatering och det namn som används för att referera till kontrollen.|

## <a name="text-value"></a>Textvärde

Ange ett namn som används för att referera till den här kontrollen.

## <a name="remarks"></a>Anmärkningar

Namnet som anges här kan användas i följande element för att referera till den här kontrollen.

- När du skapar en tabell, lista, brett eller anpassade vy, kan kontrollen anges med följande element: [GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)

- När du skapar en annan vanliga kontroll, kan den här kontrollen anges med följande element: [ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- När du skapar en kontroll som kan användas av en vy, kan den här kontrollen anges med följande element: [ExpressionBinding Element för CustomItem för kontroller för att visa (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Se även

[Control-Element för kontroller för Configuration (Format)](./control-element-for-controls-for-configuration-format.md)

[ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[ExpressionBinding Element för CustomItem för kontroller för att visa (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
