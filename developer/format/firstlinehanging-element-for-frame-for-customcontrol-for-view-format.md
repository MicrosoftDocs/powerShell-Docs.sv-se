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
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065979"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a>FirstLineHanging-element för Frame för CustomControl för View (format)

Anger hur många tecken som den första raden av data ska flyttas till vänster. Det här elementet används när du definierar en anpassad kontroll vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för vyn (Format) CustomItem elementet för CustomEntry för CustomControlView (Format) RAM-elementet för CustomItem för anpassad kontroll för Visa (Format) FirstLineHanging elementet för ramens för anpassad kontroll för vy (Format)

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
