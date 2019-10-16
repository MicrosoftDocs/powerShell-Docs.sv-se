---
title: CustomEntry-element för CustomControl för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355274"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntry-element för CustomControl för Controls för Configuration (format)

Ger en definition av den gemensamma kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl för kontroller för konfiguration (format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `CustomEntry`. Du måste ange de objekt som ska visas av definitionen.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för CustomEntry för kontroller för konfiguration (format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar de .NET-typer som använder definitionen av den gemensamma kontrollen eller villkoret som måste finnas för att den här kontrollen ska kunna användas.|
|[CustomItem-element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Nödvändigt element.<br /><br /> Definierar vilka data som visas av kontrollen och hur de visas.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntries-element för CustomControl för konfiguration (format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Innehåller definitionerna för den gemensamma kontrollen.|

## <a name="remarks"></a>Anmärkningar

I de flesta fall krävs bara en definition för varje gemensam anpassad kontroll, men det är möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt. I dessa fall kan du ange en separat definition för varje objekt eller uppsättning objekt.

## <a name="see-also"></a>Se även

[CustomEntries-element för CustomControl för konfiguration (format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[CustomItem-element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
