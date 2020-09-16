---
title: CustomControlName-element för GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4e3102f12cd37fa72a2de1bf1db5d1f82db31222
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783746"
---
# <a name="customcontrolname-element-for-groupby-format"></a>CustomControlName-element för GroupBy (format)

Anger namnet på en anpassad kontroll som används för att visa den nya gruppen. Det här elementet används när du definierar en tabell, lista, bred eller anpassad flikkontroll.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControlName element för GroupBy (format)

## <a name="syntax"></a>Syntax

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `CustomControlName` elementens överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[GroupBy-element för View (format)](./groupby-element-for-view-format.md)|Definierar hur Windows PowerShell visar en ny grupp med objekt.|

## <a name="text-value"></a>Textvärde

Ange namnet på den anpassade kontroll som används för att visa en ny grupp.

## <a name="remarks"></a>Kommentarer

Du kan skapa vanliga kontroller som kan användas av alla vyer i en fil format och du kan skapa visnings kontroller som kan användas av en speciell vy. Följande element anger namnen på dessa anpassade kontroller:

- [Name-element för Control för Controls för Configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name-element för Control för Controls för View (format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Se även

[GroupBy-element för View (format)](./groupby-element-for-view-format.md)

[Name-element för Control för Controls för Configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name-element för Control för Controls för View (format)](./name-element-for-control-for-controls-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
