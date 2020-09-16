---
title: ListEntries-element för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0fe07e739c2d2fec153599ec6c0c0b3ecc14df18
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785718"
---
# <a name="listentries-element-for-listcontrol-format"></a>ListEntries-element för ListControl (format)

Innehåller definitionerna för listvyn. Listvyn måste innehålla en eller flera definitioner.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) element för ListEntries (format)

## <a name="syntax"></a>Syntax

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `ListEntries` elementets överordnade element. Minst ett underordnat element måste anges.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListEntry-element (format)](./listentry-element-for-listcontrol-format.md)|Ger en definition av listvyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListControl-element (format)](./listcontrol-element-format.md)|Definierar ett List format för vyn.|

## <a name="remarks"></a>Kommentarer

Mer information om listvyer finns i [listvyn](./creating-a-list-view.md).

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

[ListControl-element (format)](./listcontrol-element-format.md)

[ListEntry-element (format)](./listentry-element-for-listcontrol-format.md)

[Listvy](./creating-a-list-view.md)

[Skriva en Windows PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
