---
title: CustomControl-element för kontroll för konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9d92a9e-c680-46ca-962e-e82452726953
caps.latest.revision: 10
ms.openlocfilehash: 1d72ce5b18e89bd81c7f81b27f4b8c60bed99764
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359069"
---
# <a name="customcontrol-element-for-control-for-controls-for-configuration-format"></a>CustomControl-element för Control för Controls för Configuration (format)

Definierar en kontroll. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för kontroll av CustomControl-element (format) för kontroll av konfiguration (format)

## <a name="syntax"></a>Syntax

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `CustomControl`. Elementet måste ha minst ett underordnat element. Det finns ingen övre gräns för antalet underordnade element som kan anges.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntries-element för CustomControl för konfiguration (format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Nödvändigt element.<br /><br /> Tillhandahåller definitioner för en kontroll.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Kontroll element för konfigurations kontroll (format)](./control-element-for-controls-for-configuration-format.md)|Definierar en gemensam kontroll som kan användas av alla vyer i format filen och det namn som används för att referera till kontrollen.|

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[Kontroll element för konfigurations kontroll (format)](./control-element-for-controls-for-configuration-format.md)

[CustomEntries-element för CustomControl för konfiguration (format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
