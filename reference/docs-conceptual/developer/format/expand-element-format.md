---
ms.date: 09/13/2016
ms.topic: reference
title: Expand-element (format)
description: Expand-element (format)
ms.openlocfilehash: 518e132e3e74b921d4e51966fc60088a22ef63f1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667954"
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
