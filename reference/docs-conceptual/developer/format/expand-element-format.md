---
title: Expandera element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: deee832254bb8a774ee2c1f5bd451d3ced1bd47a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783661"
---
# <a name="expand-element-format"></a>Expand-element (format)

Anger hur Collection-objektet expanderas för den här definitionen.

Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) Expand-element (format)

## <a name="syntax"></a>Syntax

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `Expand` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EnumerableExpansion-element (format)](./enumerableexpansion-element-format.md)|Definierar hur vissa .NET Collection-objekt expanderas när de visas i en vy.|

## <a name="text-value"></a>Textvärde

Ange ett av följande värden:

- EnumOnly: visar endast egenskaperna för objekten i samlingen.

- CoreOnly: visar endast egenskaperna för objektet samling.

- Båda: visar egenskaperna för objekten i samlingen och egenskaperna för objektet samling.

## <a name="remarks"></a>Kommentarer

Det här elementet används för att definiera hur samlings objekt och objekten i samlingen ska visas. I det här fallet refererar ett samlings objekt till alla objekt som stöder  **system. Collections. ICollection** -gränssnittet.

Standard beteendet är att endast visa egenskaperna för objekten i samlingen.

## <a name="see-also"></a>Se även

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
