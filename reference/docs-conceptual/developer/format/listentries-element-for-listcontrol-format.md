---
title: ListEntries-element för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354357"
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

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `ListEntries`. Minst ett underordnat element måste anges.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListEntry-element (format)](./listentry-element-for-listcontrol-format.md)|Ger en definition av listvyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListControl-element (format)](./listcontrol-element-format.md)|Definierar ett List format för vyn.|

## <a name="remarks"></a>Anmärkningar

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
