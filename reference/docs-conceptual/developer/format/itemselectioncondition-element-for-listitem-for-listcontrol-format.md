---
title: ItemSelectionCondition-element för ListItem för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356058"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ItemSelectionCondition-element för ListItem för ListControl (format)

Definierar det villkor som måste finnas för att listobjektet ska kunna användas.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) ListItems-element för ListEntry för ListControl (format) ListItem-elementet för ListItems för ListControl (format) ItemSelectionCondition-elementet för ListItem för ListControl (format)

## <a name="syntax"></a>Syntax

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `ItemSelectionCondition`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-element för ItemSelectionCondition för ListControl (format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[Script block-element för ItemSelectionCondition för ListControl (format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItem-element för ListItems för ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.|

## <a name="remarks"></a>Anmärkningar

Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.

## <a name="see-also"></a>Se även

[ListItem-element för ListItems för ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[PropertyName-element för ItemSelectionCondition för ListControl (format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[Script block-element för ItemSelectionCondition för ListControl (format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
