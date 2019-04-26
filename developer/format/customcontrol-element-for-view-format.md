---
title: Anpassad kontroll Element för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066676"
---
# <a name="customcontrol-element-for-view-format"></a>CustomControl-element för View (format)

Definierar en anpassad kontroll format för vyn.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomControl` element. Du måste ange ett underordnat element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntries Element för anpassad kontroll för vy (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Element som krävs.<br /><br /> Innehåller definitioner av vyn anpassad kontroll.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Visa Element (Format)](./view-element-format.md)|Definierar en vy som används för att visa en eller flera .NET-objekt.|

## <a name="remarks"></a>Anmärkningar

Endast en definition som krävs för varje kontroll vy i de flesta fall, men det är möjligt att ange flera definitioner om du vill använda samma vy för att visa olika .NET-objekt. I sådana fall kan ange du en definition av separat för varje objekt eller en uppsättning objekt.

## <a name="see-also"></a>Se även

[CustomEntries Element för anpassad kontroll för vy (Format)](./customentries-element-for-customcontrol-for-view-format.md)

[Visa Element (Format)](./view-element-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
