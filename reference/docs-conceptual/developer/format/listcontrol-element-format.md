---
title: ListControl-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354371"
---
# <a name="listcontrol-element-format"></a>ListControl-element (format)

Definierar ett List format för vyn.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format)

## <a name="syntax"></a>Syntax

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `ListControl`. Det här elementet får bara innehålla ett enda underordnat element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListEntries-element (format)](./listentries-element-for-listcontrol-format.md)|Nödvändigt element.<br /><br /> Innehåller definitionerna för listvyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Visa element (format)](./view-element-format.md)|Definierar en vy som används för att visa medlemmar i ett eller flera objekt.|

## <a name="remarks"></a>Anmärkningar

Mer information om hur du skapar en listvy finns i [skapa en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I det här exemplet visas en listvy för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Se även

[Visa element (format)](./view-element-format.md)

[ListEntries-element (format)](./listentries-element-for-listcontrol-format.md)

[Skapa en listvy](./creating-a-list-view.md)

[Skriva en Windows PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
