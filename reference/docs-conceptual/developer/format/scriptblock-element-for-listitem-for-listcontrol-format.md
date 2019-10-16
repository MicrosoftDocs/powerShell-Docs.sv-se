---
title: Script block-element för ListItem för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355792"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ScriptBlock-element för ListItem för ListControl (format)

Anger det skript vars värde visas i raden.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) ListItems-element för ListEntry för ListControl (format) ListItem-elementet för ListItems för ListControl (format) script block-elementet för ListItem för ListControl (format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `ScriptBlock`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItem-element (format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.|

## <a name="text-value"></a>Text värde

Ange det skript vars värde visas på raden.

## <a name="remarks"></a>Anmärkningar

När det här elementet har angetts kan du inte ange elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) .

Mer information om hur du anger skript i listvyn finns i [listvyn](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du anger den egenskap vars värde visas.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>Se även

[PropertyName-element för ListItem för ListControl (format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Skapa en listvy](./creating-a-list-view.md)

[ListItem-element för ListItems för ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
