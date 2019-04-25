---
title: ListEntries Element för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065401"
---
# <a name="listentries-element-for-listcontrol-format"></a>ListEntries-element för ListControl (format)

Innehåller definitioner i listvyn. Listvyn måste ange en eller flera definitioner.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ListEntries` element. Du måste ange minst ett underordnat element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListEntry Element (Format)](./listentry-element-for-listcontrol-format.md)|Innehåller en definition av listvyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListControl Element (Format)](./listcontrol-element-format.md)|Definierar ett listformat för vyn.|

## <a name="remarks"></a>Anmärkningar

Läs mer om listvyer [listvyn](./creating-a-list-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar XML-element som definierar listvyn för den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Se även

[ListControl Element (Format)](./listcontrol-element-format.md)

[ListEntry Element (Format)](./listentry-element-for-listcontrol-format.md)

[Listvy](./creating-a-list-view.md)

[Skriva ett Windows PowerShell formatering och skriver fil](./writing-a-powershell-formatting-file.md)
