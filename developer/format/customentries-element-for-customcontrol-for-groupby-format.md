---
title: CustomEntries Element för anpassad kontroll för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066555"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>CustomEntries-element för CustomControl för GroupBy (format)

Innehåller definitioner för kontrollen. Det här elementet används när du definierar hur en ny grupp med objekt visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format)

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
|[CustomEntry Element för anpassad kontroll för GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Element som krävs.<br /><br /> Innehåller en definition av kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Anpassad kontroll Element för GroupBy (Format)](./customcontrol-element-for-groupby-format.md)|Definierar den anpassade kontrollen som visar den nya gruppen.|

## <a name="remarks"></a>Anmärkningar

I de flesta fall en kontroll har endast en definition som anges i en enda `CustomEntry` element. Det är dock möjligt att ange flera definitioner om du vill använda samma kontroll för att visa olika grupper. I sådana fall kan du definiera en `CustomEntry` element för en grupp.

## <a name="see-also"></a>Se även

[CustomEntry Element för CustomEntries för kontroller för att visa (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Anpassad kontroll Element för GroupBy (Format)](./customcontrol-element-for-groupby-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
