---
title: CustomEntry Element för CustomEntries för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066455"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>CustomEntry-element för CustomEntries för CustomControl för View (format)

Innehåller en definition av vyn anpassad kontroll.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för vy (Format)

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
|[EntrySelectedBy Element för CustomEntry för vy (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Definierar vilka typer av .NET som använder definitionen av den anpassade kontroll vyn eller ett villkor som måste finnas för den här definitionen som ska användas.|
|[CustomItem Element för CustomEntry för vy (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definierar en kontroll för den anpassade kontroll-definitionen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntries Element för anpassad kontroll för vy (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Innehåller definitioner av vyn anpassad kontroll. Den anpassade kontroll vyn måste ange en eller flera definitioner.|

## <a name="remarks"></a>Anmärkningar

Endast en definition som krävs för varje anpassad kontroll vy i de flesta fall, men det är möjligt att ha flera definitioner om du vill använda samma vy för att visa olika .NET-objekt. I sådana fall kan ange du en definition av separat för varje objekt eller en uppsättning objekt.

## <a name="see-also"></a>Se även

[Anpassad kontroll Element för vy (Format)](./customcontrol-element-for-view-format.md)

[CustomItem Element för CustomEntry för vy (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[EntrySelectedBy Element för CustomEntry för vy (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
