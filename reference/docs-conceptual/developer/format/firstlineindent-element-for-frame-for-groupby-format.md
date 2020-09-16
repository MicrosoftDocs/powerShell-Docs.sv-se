---
title: FirstLineIndent-element för inramad GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: def5b4e9ca98a15edbb36675ca506e886de567dc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781672"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a>FirstLineIndent-element för Frame för GroupBy (format)

Anger hur många tecken den första raden med data flyttas till höger. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry element for CustomControl for groupby (format) CustomItem-element för CustomEntry-element (format) för CustomItem för (format)

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
|[Frame-element för CustomItem för GroupBy (format)](./frame-element-for-customitem-for-groupby-format.md)|Definierar hur data visas, till exempel att flytta data till vänster eller höger.|

## <a name="text-value"></a>Textvärde

Ange antalet tecken som du vill flytta den första raden i data.

## <a name="remarks"></a>Kommentarer

Om det här elementet har angetts kan du inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) -elementet.

## <a name="see-also"></a>Se även

[FirstLineHanging-element för Frame för GroupBy (format)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Frame-element för CustomItem för GroupBy (format)](./frame-element-for-customitem-for-groupby-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
