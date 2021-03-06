---
ms.date: 09/13/2016
ms.topic: reference
title: FirstLineIndent-element för Frame för Controls för View (format)
description: FirstLineIndent-element för Frame för Controls för View (format)
ms.openlocfilehash: 425cd9ccafb2cbe36f238177fc73923da048f924
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660148"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a>FirstLineIndent-element för Frame för Controls för View (format)

Anger hur många tecken den första raden med data flyttas till höger. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för Control for View (format) CustomEntries-element för CustomControl för visning (format) CustomEntry-element för CustomEntries for Controls for View (format) CustomItem-element för CustomEntry for Controls for View (format) Frame element for CustomItem for Controls for View (format) FirstLineIndent-elementet i bild rutornas vyer (format)

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
|[Frame-element för CustomItem för Controls för View (format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Definierar hur data visas, till exempel att flytta data till vänster eller höger.|

## <a name="text-value"></a>Textvärde

Ange antalet tecken som du vill flytta den första raden i data.

## <a name="remarks"></a>Kommentarer

Om det här elementet har angetts kan du inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) -elementet.

## <a name="see-also"></a>Se även

[FirstLineHanging-element för Frame för Controls för View (format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Frame-element för CustomItem för Controls för View (format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
