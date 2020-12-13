---
ms.date: 09/13/2016
ms.topic: reference
title: FirstLineHanging-element för Frame för GroupBy (format)
description: FirstLineHanging-element för Frame för GroupBy (format)
ms.openlocfilehash: 6a4ded9cced484440636aee694cd8381b2889ba8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652268"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>FirstLineHanging-element för Frame för GroupBy (format)

Anger hur många tecken den första raden med data flyttas till vänster. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry element for CustomControl for groupby (format) CustomItem-element för CustomEntry-element (format) för CustomItem för (format)

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
|[Frame-element för CustomItem för GroupBy (format)](./frame-element-for-customitem-for-groupby-format.md)|Definierar hur data visas, till exempel att flytta data till vänster eller höger.|

## <a name="text-value"></a>Textvärde

Ange antalet tecken som du vill flytta den första raden i data.

## <a name="remarks"></a>Kommentarer

Om det här elementet har angetts kan du inte ange [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -elementet.

## <a name="see-also"></a>Se även

[FirstLineIndent-element för Frame för GroupBy (format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Frame-element för CustomItem för GroupBy (format)](./frame-element-for-customitem-for-groupby-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
