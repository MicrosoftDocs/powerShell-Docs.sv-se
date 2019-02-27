---
title: EnumerableExpansion Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847399"
---
# <a name="enumerableexpansion-element-format"></a>EnumerableExpansion-element (format)

Definierar hur specifik .NET samling objekt visas när de visas i vyn.

Elementet (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EnumerableExpansion` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Valfritt element.<br /><br /> Definierar vilka .NET samling objekt byggs med den här definitionen.|
|[Expandera Element (Format)](./expand-element-format.md)|Anger hur samlingsobjektet utökas för den här definitionen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EnumerableExpansions Element (Format)](./enumerableexpansions-element-format.md)|Definierar de olika sätten .NET samlingen objekt visas när de visas i vyn.|

## <a name="remarks"></a>Anmärkningar

Det här elementet används för att definiera hur samlingen och objekt i samlingen visas. I det här fallet en samling objekt refererar till ett objekt som stöder den **System.Collections.ICollection** gränssnitt.

Standardinställningen är att visa endast egenskaperna för objekten i samlingen.

## <a name="see-also"></a>Se även

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
