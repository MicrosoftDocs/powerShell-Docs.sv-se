---
title: EnumerableExpansions-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354735"
---
# <a name="enumerableexpansions-element-format"></a>EnumerableExpansions-element (format)

Definierar hur .NET-samlings objekt expanderas när de visas i en vy.

Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format)

## <a name="syntax"></a>Syntax

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `EnumerableExpansions`-elementet. Det finns ingen gräns för antalet underordnade element som du kan använda.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EnumerableExpansion-element (format)](./enumerableexpansion-element-format.md)|Valfritt element.<br /><br /> Definierar de olika .NET-samlings objekt som expanderas när de visas i en vy.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[DefaultSettings-element (format)](./defaultsettings-element-format.md)|Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.|

## <a name="remarks"></a>Anmärkningar

Det här elementet används för att definiera hur samlings objekt och objekten i samlingen ska visas. I det här fallet refererar ett samlings objekt till alla objekt som stöder **system. Collections. ICollection** -gränssnittet.

## <a name="see-also"></a>Se även

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
