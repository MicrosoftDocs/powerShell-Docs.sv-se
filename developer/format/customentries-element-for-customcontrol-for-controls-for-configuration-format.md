---
title: CustomEntries Element för anpassad kontroll för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066608"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntries-element för CustomControl för Controls för Configuration (format)

Innehåller definitioner av en gemensam kontroll. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomEntries` element. Du måste ange en eller flera underordnade element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Innehåller en definition av vanliga kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Anpassad kontroll Element för kontroll för konfiguration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Definierar en gemensam kontroll.|

## <a name="remarks"></a>Anmärkningar

I de flesta fall en kontroll har endast en definition som definieras i en enda `CustomEntry` element. Det är dock möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt. I sådana fall kan du definiera en `CustomEntry` element för varje objekt eller en uppsättning objekt.

## <a name="see-also"></a>Se även

[Anpassad kontroll Element för kontroll för konfiguration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
