---
title: EnumerableExpansion-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358973"
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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `EnumerableExpansion`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för EnumerableExpansion (format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Definierar vilka .NET-samlings objekt som expanderas av den här definitionen.|
|[Expandera element (format)](./expand-element-format.md)|Anger hur Collection-objektet expanderas för den här definitionen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EnumerableExpansions-element (format)](./enumerableexpansions-element-format.md)|Definierar de olika sätt som .NET-samlings objekt expanderas när de visas i en vy.|

## <a name="remarks"></a>Anmärkningar

Det här elementet används för att definiera hur samlings objekt och objekten i samlingen ska visas. I det här fallet refererar ett samlings objekt till alla objekt som stöder **system. Collections. ICollection** -gränssnittet.

Standard beteendet är att endast visa egenskaperna för objekten i samlingen.

## <a name="see-also"></a>Se även

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
