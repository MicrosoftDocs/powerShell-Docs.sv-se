---
title: ScriptBlock Element för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229311"
---
# <a name="scriptblock-element-for-groupby-format"></a>ScriptBlock-element för GroupBy (format)

Anger det skript som startar en ny grupp när dess värde ändras.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) ScriptBlock elementet för GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)|Definierar hur en grupp med .NET-objekt visas.|

## <a name="text-value"></a>Textvärde

Ange det skript som ska utvärderas.

## <a name="remarks"></a>Anmärkningar

PowerShell startar en ny grupp när det här skriptet ändras.

När det här elementet har angetts ska du inte ange den [PropertyName](propertyname-element-for-groupby-format.md) element att starta en ny grupp.

## <a name="see-also"></a>Se även

[PropertyName-Element för GroupBy (Format)](propertyname-element-for-groupby-format.md)

[GroupBy-Element för Visa (Format)](groupby-element-for-view-format.md)

[Skriva ett PowerShell formatering fil](writing-a-powershell-formatting-file.md)
