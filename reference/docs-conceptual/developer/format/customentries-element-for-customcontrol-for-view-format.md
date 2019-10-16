---
title: CustomEntries-element för CustomControl för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355281"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>CustomEntries-element för CustomControl för View (format)

Innehåller definitionerna för vyn anpassad kontroll. Vyn anpassad kontroll måste ange en eller flera definitioner.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) CustomControl-element (format) element (format) CustomEntries-element för CustomControl för vy (format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `CustomControlEntries`. Du måste ange ett eller flera underordnade element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomEntries för vy (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Nödvändigt element.<br /><br /> Innehåller en definition av den anpassade kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomControl-element för vy (format)](./customcontrol-element-for-view-format.md)|Nödvändigt element.<br /><br /> Definierar ett anpassat kontroll format för vyn.|

## <a name="remarks"></a>Anmärkningar

I de flesta fall har en kontroll bara en definition som definieras i ett enda `CustomEntry`-element. Det är dock möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt. I dessa fall kan du definiera ett `CustomEntry`-element för varje objekt eller uppsättning objekt.

## <a name="see-also"></a>Se även

[CustomControl-element för vy (format)](./customcontrol-element-for-view-format.md)

[CustomEntry-element för CustomEntries för vy (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
