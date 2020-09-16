---
title: PropertyName-element för ItemSelectionCondition för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8bdbb05326f7ff5ccffa46215631a5c954080dc1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780873"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>PropertyName-element för ItemSelectionCondition för ListControl (format)

Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och vyn används. Det här elementet används när du definierar en listvy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element för ListControl (format) ListItems-element för ListEntry (format) ListControl-element för ListItem (format) ListItems-element för ListControl (format) ItemSelectionCondition-element för ListItem-elementet ListControls (format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ItemSelectionCondition-element för ListItem för ListControl (format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>Textvärde

Ange namnet på den egenskap vars värde visas.

## <a name="remarks"></a>Kommentarer

Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) -elementet när du definierar urvals villkoret.

## <a name="see-also"></a>Se även

[Script block-element för ItemSelectionCondition för ListIControl (format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[ItemSelectionCondition-element för ListItem för ListControl (format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
