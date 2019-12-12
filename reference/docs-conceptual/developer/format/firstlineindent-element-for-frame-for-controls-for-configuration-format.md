---
title: FirstLineIndent-element för ram för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354609"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a>FirstLineIndent-element för Frame för Controls för Configuration (format)

Anger hur många tecken den första raden med data flyttas till höger. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem-element för CustomEntry for Controls for Configuration Frame element for CustomItem for Controls for Configuration (format) FirstLineIndent element for Frame för inställningar för konfiguration (format)

## <a name="syntax"></a>Syntax

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `FirstLineIndent`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Ram element för CustomItem för kontroll av konfiguration (format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Definierar hur data visas, till exempel att flytta data till vänster eller höger.|

## <a name="text-value"></a>Textvärde

Ange antalet tecken som du vill flytta den första raden i data.

## <a name="remarks"></a>Anmärkningar

Om det här elementet har angetts kan du inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) -elementet.

## <a name="see-also"></a>Se även

[FirstLineHanging-element för ram för kontroll av konfiguration (format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Ram element för CustomItem för kontroll av konfiguration (format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
