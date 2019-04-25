---
title: ItemSelectionCondition Element för ListItem för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065452"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ItemSelectionCondition-element för ListItem för ListControl (format)

Definierar de villkor som måste finnas för det här objektet i listan som ska användas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för ListControl (Format) ListEntry elementet för ListEntries för ListControl (Format) ListItems som finns elementet för ListEntry för ListControl (Format) ListItem elementet för ListItems som finns för ListControl (Format) ItemSelectionCondition elementet för ListItem för ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ItemSelectionCondition` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[PropertyName-Element för ItemSelectionCondition för ListControl (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap som utlöser villkoret.|
|[ScriptBlock Element för ItemSelectionCondition för ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger det skript som utlöser villkoret.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItem Element för ListItems som finns för ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definierar egenskapen eller skript som vars värde visas i en rad i listvyn.|

## <a name="remarks"></a>Anmärkningar

Du kan ange ett egenskapsnamn eller ett skript för det här villkoret men kan inte ange båda.

## <a name="see-also"></a>Se även

[ListItem Element för ListItems som finns för ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[PropertyName-Element för ItemSelectionCondition för ListControl (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[ScriptBlock Element för ItemSelectionCondition för ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
