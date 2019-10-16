---
title: CustomEntries-element för CustomControl för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359043"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntries-element för CustomControl för Controls för Configuration (format)

Innehåller definitionerna för en gemensam kontroll. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Formatering

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `CustomEntries`. Du måste ange ett eller flera underordnade element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomControl för kontroller för konfiguration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Ger en definition av den gemensamma kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomControl-element för kontroll av konfiguration (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Definierar en gemensam kontroll.|

## <a name="remarks"></a>Anmärkningar

I de flesta fall har en kontroll bara en definition som definieras i ett enda `CustomEntry`-element. Det är dock möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt. I dessa fall kan du definiera ett `CustomEntry`-element för varje objekt eller uppsättning objekt.

## <a name="see-also"></a>Se även

[CustomControl-element för kontroll av konfiguration (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[CustomEntry-element för CustomControl för kontroller för konfiguration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
