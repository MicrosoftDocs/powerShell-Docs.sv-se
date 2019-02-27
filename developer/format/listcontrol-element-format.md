---
title: ListControl Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847833"
---
# <a name="listcontrol-element-format"></a>ListControl-element (format)

Definierar ett listformat för vyn.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ListControl` element. Det här elementet måste innehålla en enda underelement.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListEntries Element (Format)](./listentries-element-for-listcontrol-format.md)|Element som krävs.<br /><br /> Innehåller definitioner i listvyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Visa Element (Format)](./view-element-format.md)|Definierar en vy som används för att visa medlemmarna i ett eller flera objekt.|

## <a name="remarks"></a>Anmärkningar

Läs mer om hur du skapar en listvy [skapar en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar en listvy för den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt.

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

[Visa Element (Format)](./view-element-format.md)

[ListEntries Element (Format)](./listentries-element-for-listcontrol-format.md)

[Skapa en listvy](./creating-a-list-view.md)

[Skriva ett Windows PowerShell formatering och skriver fil](./writing-a-powershell-formatting-file.md)
