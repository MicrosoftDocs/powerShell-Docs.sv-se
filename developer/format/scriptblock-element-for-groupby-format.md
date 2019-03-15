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
ms.openlocfilehash: 41a6aaa24e5850bd390c8e3b6505cc88fc80b7b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846958"
---
# <a name="scriptblock-element-for-groupby-format"></a>ScriptBlock-element för GroupBy (format)

Anger det skript som startar en ny grupp när dess värde ändras.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) ScriptBlock elementet för GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBolck>ScriptToEvaluate</ScriptBlock>
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

Windows PowerShell startar en ny grupp när det här skriptet ändras.

När det här elementet har angetts ska du inte ange den [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element att starta en ny grupp.

## <a name="see-also"></a>Se även

[PropertyName-Element för GroupBy (Format)](./propertyname-element-for-groupby-format.md)

[GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)