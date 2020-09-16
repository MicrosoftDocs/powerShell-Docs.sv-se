---
title: Script block-element för ItemSelectionCondition för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 38dc952bfadd6aed24bae8cbef05adcd22e61dd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787639"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>ScriptBlock-element för ItemSelectionCondition för ListControl (format)

Anger det skript som utlöser villkoret. När det här skriptet utvärderas `true` , uppfylls villkoret och listobjektet används. Det här elementet används när du definierar en listvy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) ListItems-element för ListEntry för ListControl (format) ListItem-element för ListItems (format) ItemSelectionCondition-element för ListItem (format) ListControl-element för script block (format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ItemSelectionCondition-element för ListItem för ListControl (format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Definierar det villkor som måste finnas för att listobjektet ska kunna användas.|

## <a name="text-value"></a>Textvärde

Ange det skript som utvärderas.

## <a name="remarks"></a>Kommentarer

Om det här elementet används kan du inte ange `PropertyName` elementet när du definierar urvals villkoret.

## <a name="see-also"></a>Se även

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
