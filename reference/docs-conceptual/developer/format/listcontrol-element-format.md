---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl-element (format)
description: ListControl-element (format)
ms.openlocfilehash: cd5687ac8e94e2245d1ae2de8b2206185e5b8ca4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666594"
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

I följande avsnitt beskrivs attributen, underordnade element och `ListControl` elementets överordnade element. Det här elementet får bara innehålla ett enda underordnat element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListEntries-element (format)](./listentries-element-for-listcontrol-format.md)|Nödvändigt element.<br /><br /> Innehåller definitionerna för listvyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[View-element (format)](./view-element-format.md)|Definierar en vy som används för att visa medlemmar i ett eller flera objekt.|

## <a name="remarks"></a>Kommentarer

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

[View-element (format)](./view-element-format.md)

[ListEntries-element (format)](./listentries-element-for-listcontrol-format.md)

[Skapa en listvy](./creating-a-list-view.md)

[Skriva en Windows PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
