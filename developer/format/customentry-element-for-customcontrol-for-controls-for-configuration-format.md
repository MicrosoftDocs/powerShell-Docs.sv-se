---
title: CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849478"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntry-element för CustomControl för Controls för Configuration (format)

Innehåller en definition av vanliga kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomEntry` element. Du måste ange objekt som visas av definitionen.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för CustomEntry för kontroller för konfiguration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar vilka typer av .NET som använder definitionen av den vanliga kontrollen eller villkor som måste finnas för den här kontrollen som ska användas.|
|[CustomItem Element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Element som krävs.<br /><br /> Definierar vilka data som visas av kontrollen och hur de visas.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntries Element för anpassad kontroll för konfiguration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Innehåller definitionerna av vanliga kontrollen.|

## <a name="remarks"></a>Anmärkningar

Endast en definition som krävs för varje anpassad kontroll som är vanliga i de flesta fall, men det är möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt. I sådana fall kan ange du en definition av separat för varje objekt eller en uppsättning objekt.

## <a name="see-also"></a>Se även

[CustomEntries Element för anpassad kontroll för konfiguration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[CustomItem Element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
