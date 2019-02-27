---
title: FirstLineHanging Element för ramens för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ae4ad8ae3e6cb5d1174dc001b30aa84dd182a606
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849779"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a>FirstLineHanging-element för Frame för CustomControl för View (format)

Anger hur många tecken som den första raden av data ska flyttas till vänster. Det här elementet används när du definierar en anpassad kontroll vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för vyn (Format) CustomItem elementet för CustomEntry för CutomControlView (Format) RAM-elementet för CustomItem för anpassad kontroll för Visa (Format) FirstLineHanging elementet för ramens för anpassad kontroll för vy (Format)

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
|[Ramens Element för CustomItem för anpassad kontroll för vy (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Definierar hur data visas, till exempel ändra datatypen till vänster eller höger.|

## <a name="text-value"></a>Textvärde

Ange antalet tecken som du vill flytta den första raden av data.

## <a name="remarks"></a>Anmärkningar

Om det här elementet har angetts, du kan inte ange den [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element.

## <a name="see-also"></a>Se även

[FirstLineIndent Element för ramens för anpassad kontroll för vy (Format)](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Ramens Element för CustomItem för anpassad kontroll för vy (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
