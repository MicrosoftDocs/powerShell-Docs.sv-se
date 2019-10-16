---
title: CustomControlName-element för GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359033"
---
# <a name="customcontrolname-element-for-groupby-format"></a>CustomControlName-element för GroupBy (format)

Anger namnet på en anpassad kontroll som används för att visa den nya gruppen. Det här elementet används när du definierar en tabell, lista, bred eller anpassad flikkontroll.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControlName element för GroupBy (format)

## <a name="syntax"></a>Syntax

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och överordnade element i `CustomControlName`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[GroupBy-element för vy (format)](./groupby-element-for-view-format.md)|Definierar hur Windows PowerShell visar en ny grupp med objekt.|

## <a name="text-value"></a>Text värde

Ange namnet på den anpassade kontroll som används för att visa en ny grupp.

## <a name="remarks"></a>Anmärkningar

Du kan skapa vanliga kontroller som kan användas av alla vyer i en fil format och du kan skapa visnings kontroller som kan användas av en speciell vy. Följande element anger namnen på dessa anpassade kontroller:

- [Namn element för kontroll för konfiguration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Namn element för kontroll för vy (format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Se även

[GroupBy-element för vy (format)](./groupby-element-for-view-format.md)

[Namn element för kontroll för konfiguration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Namn element för kontroll för vy (format)](./name-element-for-control-for-controls-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
