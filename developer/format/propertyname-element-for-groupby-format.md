---
title: PropertyName-Element för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075876"
---
# <a name="propertyname-element-for-groupby-format"></a>PropertyName-element för GroupBy (format)

Anger den .NET-egenskap som startar en ny grupp när dess värde ändras.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) PropertyName elementet för GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)|Definierar hur en grupp med .NET-objekt visas.|

## <a name="text-value"></a>Textvärde

Ange namnet på .NET-egenskapen.

## <a name="remarks"></a>Anmärkningar

Windows PowerShell startar en ny grupp när den här egenskapen ändras.

När det här elementet har angetts ska du inte ange den [ScriptBlock](./scriptblock-element-for-groupby-format.md) element att starta en ny grupp.

## <a name="example"></a>Exempel

I följande exempel visas hur du startar en ny grupp när en egenskap ändras.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Ett exempel på en fullständig formatering fil som innehåller det här elementet finns [bred vy (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Se även

[GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)

[ScriptBlock Element för GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
