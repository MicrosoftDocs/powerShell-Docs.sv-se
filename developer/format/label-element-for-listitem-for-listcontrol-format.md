---
title: Etikettera Element för ListItem för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845957"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Label-element för ListItem för ListControl (format)

Anger etiketten som visas till vänster om värdet för egenskapen eller skript på raden.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för ListControl (Format) ListEntry elementet för ListItems ListControl (Format) som finns för ListEntry för ListControl Element ( Format) ListItem Element för ListItems som finns för ListControl (Format) etikett elementet för ListItem för ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Label` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItem Element för ListItems som finns för ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definierar egenskapen eller skript som vars värde visas i en rad i listvyn.|

## <a name="text-value"></a>Textvärde

Ange etiketten ska visas till vänster om värdet för egenskapen eller skript.

## <a name="remarks"></a>Anmärkningar

Om en etikett inte anges visas namnet på egenskapen eller skriptet. Läs mer om hur du använder etiketter i en listvy [skapar en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du lägger till en etikett till en rad.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
