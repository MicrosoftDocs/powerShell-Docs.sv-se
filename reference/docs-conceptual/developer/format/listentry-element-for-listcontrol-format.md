---
title: ListEntry-element för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d98f0b5215eea7668f866d2733214ade79d748f1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785701"
---
# <a name="listentry-element-for-listcontrol-format"></a>ListEntry-element för ListControl (format)

Ger en definition av listvyn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format)

## <a name="syntax"></a>Syntax

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `ListEntry` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för ListEntry (format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Valfritt element.<br /><br /> Definierar de .NET-objekt som använder den här List vydefinitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.|
|[ListItems-element (format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Nödvändigt element.<br /><br /> Definierar egenskaper och skript vars värden visas i list visningen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListEntries-element (format)](./listentries-element-for-listcontrol-format.md)|Innehåller definitionerna för listvyn.|

## <a name="remarks"></a>Kommentarer

En listvy är ett List format som visar egenskaps värden eller skript värden för varje objekt. Mer information om listvyer finns i [skapa en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I det här exemplet visas de XML-element som definierar listvyn för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

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

[EntrySelectedBy-element för ListEntry (format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntries-element (format)](./listentries-element-for-listcontrol-format.md)

[ListItems-element (format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Skriva en Windows PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
