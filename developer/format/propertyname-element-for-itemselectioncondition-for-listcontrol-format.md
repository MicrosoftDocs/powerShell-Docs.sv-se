---
title: PropertyName-Element för ItemSelectionCondition för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064755"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>PropertyName-element för ItemSelectionCondition för ListControl (format)

Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och den används. Det här elementet används när du definierar en listvy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry konfigurationselement för ListControl (Format) ListItems som finns elementet för ListEntry för ListItem ListControl (Format) Element för ListItems som finns för ListControl (Format) ItemSelectionCondition elementet för ListItem för ListControls PropertyName elementet för ItemSelectionCondition för ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och de överordnade element i den `PropertyName` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ItemSelectionCondition Element för ListItem för ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>Textvärde

Ange namnet på egenskapen vars värde visas.

## <a name="remarks"></a>Anmärkningar

Om det här elementet används som du kan inte ange den [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element när du definierar urvalsvillkoret.

## <a name="see-also"></a>Se även

[ScriptBlock Element för ItemSelectionCondition för ListIControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[ItemSelectionCondition Element för ListItem för ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
