---
ms.date: 09/13/2016
ms.topic: reference
title: FirstLineIndent-element för Frame för Controls för Configuration (format)
description: FirstLineIndent-element för Frame för Controls för Configuration (format)
ms.openlocfilehash: 59a41410160879c2414819de4d367ecdedd8e182
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660155"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a>FirstLineIndent-element för Frame för Controls för Configuration (format)

Anger hur många tecken den första raden med data flyttas till höger. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration (format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem-elementet för CustomEntry for Controls for Control List element for CustomItem for Controls for Configuration (format) FirstLineIndent element for Frame for Controls for Configuration (format)

## <a name="syntax"></a>Syntax

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `FirstLineIndent` elementets överordnade element.

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

Om det här elementet har angetts kan du inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) -elementet.

## <a name="see-also"></a>Se även

[FirstLineHanging-element för Frame för Controls för Configuration (format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Frame-element för CustomItem för Controls för Configuration (format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
