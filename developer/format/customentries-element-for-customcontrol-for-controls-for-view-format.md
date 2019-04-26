---
title: CustomEntries Element för anpassad kontroll för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066591"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>CustomEntries-element för CustomControl för Controls för View (format)

Innehåller definitioner för kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för kontroller för att visa (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och överordnade element i den `CustomEntries` element. Det finns ingen högsta gräns för antalet underordnade element som kan anges.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry Element för CustomEntries för kontroller för att visa (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Element som krävs.<br /><br /> Innehåller en definition av kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Anpassad kontroll Element för kontroll för kontroller för att visa (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Definierar den kontroll som används av vyn.|

## <a name="remarks"></a>Anmärkningar

I de flesta fall en kontroll har endast en definition som anges i en enda `CustomEntry` element. Det är dock möjligt att ange flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt. I sådana fall kan du definiera en `CustomEntry` element för varje objekt eller en uppsättning objekt.

## <a name="see-also"></a>Se även

[CustomEntry Element för CustomEntries för kontroller för att visa (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Anpassad kontroll Element för kontroll för kontroller för att visa (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
