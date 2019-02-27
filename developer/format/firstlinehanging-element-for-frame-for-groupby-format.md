---
title: FirstLineHanging Element för ramens för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846545"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>FirstLineHanging-element för Frame för GroupBy (format)

Anger hur många tecken som den första raden av data ska flyttas till vänster. Det här elementet används när du definierar hur en ny grupp med objekt visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) CustomItem elementet för CustomEntry för GroupBy (Format) RAM-elementet för CustomItem för GroupBy (Format) FirstLineHanging elementet för ramens för GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `FirstLineHanging` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Ramens Element för CustomItem för GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Definierar hur data visas, till exempel ändra datatypen till vänster eller höger.|

## <a name="text-value"></a>Textvärde

Ange antalet tecken som du vill flytta den första raden av data.

## <a name="remarks"></a>Anmärkningar

Om det här elementet har angetts, du kan inte ange den [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) element.

## <a name="see-also"></a>Se även

[FirstLineIndent Element för ramens för GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Ramens Element för CustomItem för GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
