---
title: FirstLineHanging-element för Frame för CustomControl för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354637"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a>FirstLineHanging-element för Frame för CustomControl för View (format)

Anger hur många tecken den första raden med data flyttas till vänster. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för CustomControlView (format)-ram element för CustomItem för CustomControl för View (format) FirstLineHanging-element för bild ruta för CustomControl för vy (format)

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
|[Inramat element för CustomItem för CustomControl för vy (format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Definierar hur data visas, till exempel att flytta data till vänster eller höger.|

## <a name="text-value"></a>Textvärde

Ange antalet tecken som du vill flytta den första raden i data.

## <a name="remarks"></a>Anmärkningar

Om det här elementet har angetts kan du inte ange [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) -elementet.

## <a name="see-also"></a>Se även

[FirstLineIndent-element för Frame för CustomControl för vy (format)](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Inramat element för CustomItem för CustomControl för vy (format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
