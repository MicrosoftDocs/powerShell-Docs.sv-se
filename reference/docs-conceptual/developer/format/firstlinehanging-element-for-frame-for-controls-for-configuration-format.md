---
ms.date: 09/13/2016
ms.topic: reference
title: FirstLineHanging-element för Frame för Controls för Configuration (format)
description: FirstLineHanging-element för Frame för Controls för Configuration (format)
ms.openlocfilehash: 94d59ef7b54e036f76e38a3b06b769700443b9fb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655229"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a>FirstLineHanging-element för Frame för Controls för Configuration (format)

Anger hur många tecken den första raden med data flyttas till vänster. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration (format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem-elementet för CustomEntry for Controls for Control List element for CustomItem for Controls for Configuration (format) FirstLineHanging element for Frame for Controls for Configuration (format)

## <a name="syntax"></a>Syntax

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `FirstLineHanging` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Frame-element för CustomItem för Controls för Configuration (format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Definierar hur data visas, till exempel att flytta data till vänster eller höger.|

## <a name="text-value"></a>Textvärde

Ange antalet tecken som du vill flytta den första raden i data.

## <a name="remarks"></a>Kommentarer

Om det här elementet har angetts kan du inte ange `FirstLineIndent` elementet.

## <a name="see-also"></a>Se även

[Frame-element för CustomItem för Controls för Configuration (format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
