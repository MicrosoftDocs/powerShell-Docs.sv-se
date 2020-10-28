---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion-element (format)
description: EnumerableExpansion-element (format)
ms.openlocfilehash: 207ad99d5335e99701660159ab77279b55b0b6b5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92668022"
---
# <a name="enumerableexpansion-element-format"></a>EnumerableExpansion-element (format)

Definierar hur vissa .NET Collection-objekt expanderas när de visas i en vy.

Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) element för EnumerableExpansion (format)

## <a name="syntax"></a>Syntax

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `EnumerableExpansion` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för EnumerableExpansion (format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Definierar vilka .NET-samlings objekt som expanderas av den här definitionen.|
|[Expand-element (format)](./expand-element-format.md)|Anger hur Collection-objektet expanderas för den här definitionen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EnumerableExpansions-element (format)](./enumerableexpansions-element-format.md)|Definierar de olika sätt som .NET-samlings objekt expanderas när de visas i en vy.|

## <a name="remarks"></a>Kommentarer

Det här elementet används för att definiera hur samlings objekt och objekten i samlingen ska visas. I det här fallet refererar ett samlings objekt till alla objekt som stöder  **system. Collections. ICollection** -gränssnittet.

Standard beteendet är att endast visa egenskaperna för objekten i samlingen.

## <a name="see-also"></a>Se även

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
