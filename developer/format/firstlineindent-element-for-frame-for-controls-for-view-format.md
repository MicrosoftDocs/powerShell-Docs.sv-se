---
title: FirstLineIndent Element för ramens för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845635"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a>FirstLineIndent-element för Frame för Controls för View (format)

Anger hur många tecken som den första raden av data ska flyttas till höger. Det här elementet används när du definierar kontroller som kan användas av en vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för kontroller för att visa (Format) CustomItem Element för CustomEntry för kontroller för att visa (Format) RAM-Element för CustomItem för kontroller för att visa (Format) FirstLineIndent Element i ramen kontroller av vy (Format)

## <a name="syntax"></a>Syntax

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `FirstLineIndent` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Ramens Element för CustomItem för kontroller för att visa (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Definierar hur data visas, till exempel ändra datatypen till vänster eller höger.|

## <a name="text-value"></a>Textvärde

Ange antalet tecken som du vill flytta den första raden av data.

## <a name="remarks"></a>Anmärkningar

Om det här elementet har angetts, du kan inte ange den [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) element.

## <a name="see-also"></a>Se även

[FirstLineHanging Element för ramens för kontroller för att visa (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Ramens Element för CustomItem för kontroller för att visa (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
