---
title: Expandera Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848617"
---
# <a name="expand-element-format"></a>Expand-element (format)

Anger hur samlingsobjektet utökas för den här definitionen.

Elementet (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion konfigurationselement (Format) expanderar Element (Format)

## <a name="syntax"></a>Syntax

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Expand` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EnumerableExpansion Element (Format)](./enumerableexpansion-element-format.md)|Definierar hur specifik .NET samling objekt visas när de visas i vyn.|

## <a name="text-value"></a>Textvärde

Ange en av följande värden:

- EnumOnly: Visar endast egenskaperna för objekten i samlingen.

- CoreOnly: Visar endast egenskaperna för samlingsobjektet.

- Both: Visar egenskaperna för objekten i samlingen och egenskaperna för samlingsobjektet.

## <a name="remarks"></a>Anmärkningar

Det här elementet används för att definiera hur samlingen och objekt i samlingen visas. I det här fallet en samling objekt refererar till ett objekt som stöder den **System.Collections.ICollection** gränssnitt.

Standardinställningen är att visa endast egenskaperna för objekten i samlingen.

## <a name="see-also"></a>Se även

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
