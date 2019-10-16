---
title: FirstLineIndent-element för inramad GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354581"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a>FirstLineIndent-element för Frame för GroupBy (format)

Anger hur många tecken den första raden med data flyttas till höger. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) CustomItem-element för CustomEntry för GroupBy (format)-ram element för CustomItem för GroupBy (format) FirstLineIndent-element för ram for GroupBy (format)

## <a name="syntax"></a>Syntax

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och ett överordnat element för elementet `FirstLineIndent`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Ram element för CustomItem för GroupBy (format)](./frame-element-for-customitem-for-groupby-format.md)|Definierar hur data visas, till exempel att flytta data till vänster eller höger.|

## <a name="text-value"></a>Text värde

Ange antalet tecken som du vill flytta den första raden i data.

## <a name="remarks"></a>Anmärkningar

Om det här elementet har angetts kan du inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) -elementet.

## <a name="see-also"></a>Se även

[FirstLineHanging-element för inramad GroupBy (format)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Ram element för CustomItem för GroupBy (format)](./frame-element-for-customitem-for-groupby-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
