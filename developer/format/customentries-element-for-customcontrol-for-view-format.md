---
title: CustomEntries Element för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066523"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>CustomEntries-element för CustomControl för View (format)

Innehåller definitioner av vyn anpassad kontroll. Den anpassade kontroll vyn måste ange en eller flera definitioner.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för vy (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomControlEntries` element. Du måste ange en eller flera underordnade element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry Element för CustomEntries för vy (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Element som krävs.<br /><br /> Innehåller en definition av vyn anpassad kontroll.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Anpassad kontroll Element för vy (Format)](./customcontrol-element-for-view-format.md)|Element som krävs.<br /><br /> Definierar en anpassad kontroll format för vyn.|

## <a name="remarks"></a>Anmärkningar

I de flesta fall en kontroll har endast en definition som definieras i en enda `CustomEntry` element. Det är dock möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt. I sådana fall kan du definiera en `CustomEntry` element för varje objekt eller en uppsättning objekt.

## <a name="see-also"></a>Se även

[Anpassad kontroll Element för vy (Format)](./customcontrol-element-for-view-format.md)

[CustomEntry Element för CustomEntries för vy (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
