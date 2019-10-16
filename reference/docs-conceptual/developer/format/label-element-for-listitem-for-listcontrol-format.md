---
title: Etikett element för ListItem för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354448"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Label-element för ListItem för ListControl (format)

Anger etiketten som visas till vänster om egenskapen eller skriptets värde på raden.

Konfigurations element (format) ViewDefinitions element (format) View element (format) ListControl element (format) ListEntries-element för ListControl (format) ListEntry-element för ListControl (format) ListItems för ListEntry för ListControl-element ( Format) ListItem-element för ListItems for ListControl (format)-elementet för ListItem för ListControl (format)

## <a name="syntax"></a>Syntax

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `Label`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItem-element för ListItems för ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.|

## <a name="text-value"></a>Text värde

Ange etiketten som ska visas till vänster om egenskapen eller värdet för skriptet.

## <a name="remarks"></a>Anmärkningar

Om en etikett inte anges visas namnet på egenskapen eller skriptet. Mer information om hur du använder etiketter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).

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

[ListItem-element (format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
