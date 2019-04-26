---
title: PropertyName-Element för ListItem för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064925"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>PropertyName-element för ListItem för ListControl (format)

Anger egenskapen .NET vars värde visas i listan.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems som finns Element (Format) ListItem Element (Format) PropertyName konfigurationselement för ListItem (Format)

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
|[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definierar egenskapen eller skript som vars värde visas i raden i listvyn.|

## <a name="text-value"></a>Textvärde

Ange namnet på egenskapen vars värde visas.

## <a name="remarks"></a>Anmärkningar

När det här elementet har angetts ska du inte ange den [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.

Förutom att visa egenskapens värde, kan du även ange en etikett för värdet eller en formatsträng som kan användas för att ändra hur värdet. Läs mer om hur du anger data i en listvy [skapar en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du anger etiketten och egenskapen vars värde visas.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Se även

[ScriptBlock Element för ListItem för ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Skapa en listvy](./creating-a-list-view.md)

[ListItem Element för ListControl(Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
