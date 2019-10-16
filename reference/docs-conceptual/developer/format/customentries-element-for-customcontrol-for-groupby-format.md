---
title: CustomEntries-element för CustomControl for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355288"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>CustomEntries-element för CustomControl för GroupBy (format)

Innehåller definitionerna för kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl för GroupBy (format)

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
|[CustomEntry-element för CustomControl för GroupBy (format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Nödvändigt element.<br /><br /> Ger en definition av kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomControl-element för GroupBy (format)](./customcontrol-element-for-groupby-format.md)|Definierar den anpassade kontrollen som visar den nya gruppen.|

## <a name="remarks"></a>Anmärkningar

I de flesta fall har en kontroll bara en definition som anges i ett enda `CustomEntry`-element. Det är dock möjligt att tillhandahålla flera definitioner om du vill använda samma kontroll för att visa olika grupper. I dessa fall kan du definiera ett `CustomEntry`-element för en grupp.

## <a name="see-also"></a>Se även

[CustomEntry-element för CustomEntries för kontroller för vy (format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl-element för GroupBy (format)](./customcontrol-element-for-groupby-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
