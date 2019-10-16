---
title: Script block-element för GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355876"
---
# <a name="scriptblock-element-for-groupby-format"></a>ScriptBlock-element för GroupBy (format)

Anger det skript som startar en ny grupp när dess värde ändras.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) script block-element för GroupBy (format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `ScriptBlock`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[GroupBy-element för vy (format)](./groupby-element-for-view-format.md)|Definierar hur en grupp med .NET-objekt visas.|

## <a name="text-value"></a>Text värde

Ange det skript som utvärderas.

## <a name="remarks"></a>Anmärkningar

PowerShell startar en ny grupp när värdet för det här skriptet ändras.

När det här elementet har angetts kan du inte ange elementet [PropertyName](propertyname-element-for-groupby-format.md) för att starta en ny grupp.

## <a name="see-also"></a>Se även

[PropertyName-element för GroupBy (format)](propertyname-element-for-groupby-format.md)

[GroupBy-element för vy (format)](groupby-element-for-view-format.md)

[Skriva en fil med PowerShell-formatering](writing-a-powershell-formatting-file.md)
