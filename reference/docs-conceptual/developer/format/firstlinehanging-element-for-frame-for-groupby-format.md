---
title: FirstLineHanging-element för inramad GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355099"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>FirstLineHanging-element för Frame för GroupBy (format)

Anger hur många tecken den första raden med data flyttas till vänster. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) CustomItem-element för CustomEntry för GroupBy (format)-ram element för CustomItem för GroupBy (format) FirstLineHanging-element för ram for GroupBy (format)

## <a name="syntax"></a>Syntax

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `FirstLineHanging`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Ram element för CustomItem för GroupBy (format)](./frame-element-for-customitem-for-groupby-format.md)|Definierar hur data visas, till exempel att flytta data till vänster eller höger.|

## <a name="text-value"></a>Textvärde

Ange antalet tecken som du vill flytta den första raden i data.

## <a name="remarks"></a>Anmärkningar

Om det här elementet har angetts kan du inte ange [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -elementet.

## <a name="see-also"></a>Se även

[FirstLineIndent-element för inramad GroupBy (format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Ram element för CustomItem för GroupBy (format)](./frame-element-for-customitem-for-groupby-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
