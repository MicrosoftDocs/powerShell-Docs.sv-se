---
title: CustomControlName Element för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066557"
---
# <a name="customcontrolname-element-for-groupby-format"></a>CustomControlName-element för GroupBy (format)

Anger namnet på en anpassad kontroll som används för att visa den nya gruppen. Det här elementet används när du definierar en tabell, lista, brett eller anpassad vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) CustomControlName Element i GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade element i den `CustomControlName` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)|Definierar hur Windows PowerShell visar en ny grupp med objekt.|

## <a name="text-value"></a>Textvärde

Ange namnet på den anpassade kontrollen som används för att visa en ny grupp.

## <a name="remarks"></a>Anmärkningar

Du kan skapa vanliga kontroller som kan användas av alla vyer av en formatering fil och du kan skapa vyn kontroller som kan användas av en specifik vy. Följande element ange namnen på dessa anpassade kontroller:

- [Namnelement för kontroll för kontroller för konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Namnelement för kontroll för kontroller för att visa (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Se även

[GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)

[Namnelement för kontroll för kontroller för konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Namnelement för kontroll för kontroller för att visa (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
