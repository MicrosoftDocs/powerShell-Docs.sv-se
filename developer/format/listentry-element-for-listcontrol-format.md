---
title: ListEntry Element för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065231"
---
# <a name="listentry-element-for-listcontrol-format"></a>ListEntry-element för ListControl (format)

Innehåller en definition av listvyn.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ListEntry` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Valfritt element.<br /><br /> Definierar de .NET-objekt som använder den här listan vydefinitionen eller villkor som måste finnas för den här definitionen som ska användas.|
|[ListItems som finns Element (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Element som krävs.<br /><br /> Definierar egenskaperna och skript vars värden visas i listvyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListEntries Element (Format)](./listentries-element-for-listcontrol-format.md)|Innehåller definitioner i listvyn.|

## <a name="remarks"></a>Anmärkningar

En listvy är ett listformat som visar egenskapsvärden eller skript värden för varje objekt. Läs mer om listvyer [skapar en listvy](./creating-a-list-view.md).

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

[Skapa en listvy](./creating-a-list-view.md)

[EntrySelectedBy Element för ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntries Element (Format)](./listentries-element-for-listcontrol-format.md)

[ListItems som finns Element (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Skriva ett Windows PowerShell formatering och skriver fil](./writing-a-powershell-formatting-file.md)
