---
ms.date: 09/13/2016
ms.topic: reference
title: FirstLineIndent-element för Frame för CustomControl för View (format)
description: FirstLineIndent-element för Frame för CustomControl för View (format)
ms.openlocfilehash: 8dce8b4b072b754c3b7d631b3e5c321a5a3e5a3e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645883"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>FirstLineIndent-element för Frame för CustomControl för View (format)

Anger hur många tecken den första raden med data flyttas till höger. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem element for CustomEntry for CustomControlView (format) CustomItem-element för CustomControl för View (format) FirstLineIndent-element

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
|[Frame-element för CustomItem för CustomControl för View (format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Definierar hur data visas, till exempel att flytta data till vänster eller höger.|

## <a name="text-value"></a>Textvärde

Ange antalet tecken som du vill flytta den första raden i data.

## <a name="remarks"></a>Kommentarer

Om det här elementet har angetts kan du inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) -elementet.

## <a name="see-also"></a>Se även

[FirstLineHanging-element för Frame för CustomControl för View (format)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Frame-element för CustomItem för CustomControl för View (format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
