---
title: CustomEntries-element för CustomControl för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359025"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>CustomEntries-element för CustomControl för Controls för View (format)

Innehåller definitionerna för kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl för Visa kontroller (format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och överordnade element i `CustomEntries`-elementet. Det finns ingen övre gräns för antalet underordnade element som kan anges.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomEntries för kontroller för vy (format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Nödvändigt element.<br /><br /> Ger en definition av kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomControl-element för kontroll för vy (format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Definierar den kontroll som används i vyn.|

## <a name="remarks"></a>Anmärkningar

I de flesta fall har en kontroll bara en definition som anges i ett enda `CustomEntry`-element. Det är dock möjligt att tillhandahålla flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt. I dessa fall kan du definiera ett `CustomEntry`-element för varje objekt eller uppsättning objekt.

## <a name="see-also"></a>Se även

[CustomEntry-element för CustomEntries för kontroller för vy (format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl-element för kontroll för vy (format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
