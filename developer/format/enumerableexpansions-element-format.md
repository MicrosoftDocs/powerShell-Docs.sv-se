---
title: EnumerableExpansions Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066098"
---
# <a name="enumerableexpansions-element-format"></a>EnumerableExpansions-element (format)

Definierar hur .NET samling objekt visas när de visas i vyn.

Elementet (Format) DefaultSettings Element (Format) EnumerableExpansions konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EnumerableExpansions` element. Det finns ingen gräns för antalet underordnade element som du kan använda.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EnumerableExpansion Element (Format)](./enumerableexpansion-element-format.md)|Valfritt element.<br /><br /> Definierar de specifika .NET samling objekt som visas när de visas i vyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[DefaultSettings Element (Format)](./defaultsettings-element-format.md)|Definierar gemensamma inställningar som gäller för alla vyer i filen formatering.|

## <a name="remarks"></a>Anmärkningar

Det här elementet används för att definiera hur samlingen och objekt i samlingen visas. I det här fallet en samling objekt refererar till ett objekt som stöder den **System.Collections.ICollection** gränssnitt.

## <a name="see-also"></a>Se även

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
