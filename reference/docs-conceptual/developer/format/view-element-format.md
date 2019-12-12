---
title: Visa element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353447"
---
# <a name="view-element-format"></a>View-element (format)

Definierar en vy som visar ett eller flera .NET-objekt. Det finns ingen gräns för hur många vyer som kan definieras i en textfil.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format)

## <a name="syntax"></a>Syntax

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `View`-elementet. Du måste ange ett och endast ett av de underordnade elementen för kontrollen och du måste ange namnet på vyn och de objekt som använder vyn. Definiera anpassade kontroller, gruppera objekt och ange om vyn är out-of-band är valfri.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Styr element för vy (format)](./controls-element-for-view-format.md)|Valfritt element.<br /><br /> Definierar en uppsättning kontroller som kan refereras till av deras namn inifrån vyn.|
|[CustomControl-element (format)](./customcontrol-element-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar ett anpassat kontroll format för vyn.|
|[GroupBy-element för vy (format)](./groupby-element-for-view-format.md)|Valfritt element.<br /><br /> Definierar hur medlemmarna i .NET-objekten grupperas.|
|[ListControl-element (format)](./listcontrol-element-format.md)|Valfritt element.<br /><br /> Definierar ett List format för vyn.|
|[Namn element för vy (format)](./name-element-for-view-format.md)|Nödvändigt element.<br /><br /> Anger namnet som används för att referera till vyn.|
|[TableControl-element (format)](./tablecontrol-element-format.md)|Valfritt element.<br /><br /> Definierar ett tabell format för vyn.|
|[ViewSelectedBy-element för vy (format)](./viewselectedby-element-format.md)|Nödvändigt element.<br /><br /> Definierar de .NET-objekt som visas i den här vyn.|
|[WideControl-element (format)](./widecontrol-element-format.md)|Valfritt element.<br /><br /> Definierar ett brett List format (enskilt värde) för vyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ViewDefinitions-element (format)](./viewdefinitions-element-format.md)|Definierar de vyer som används för att visa objekt.|

## <a name="remarks"></a>Anmärkningar

Mer information om komponenterna i olika vyer och anpassade kontroller finns i följande avsnitt:

- [Table View-komponenter](./creating-a-table-view.md)

- [Visa List komponenter](./creating-a-list-view.md)

- [Wide View-komponenter](./creating-a-wide-view.md)

- [Anpassade kontroller](./creating-custom-controls.md)

## <a name="example"></a>Exempel

I det här exemplet visas ett `View`-element som definierar en tabellvy för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Se även

[ViewDefinitions-element (format)](./viewdefinitions-element-format.md)

[Namn element för vy (format)](./name-element-for-view-format.md)

[ViewSelectedBy-element (format)](./viewselectedby-element-format.md)

[Styr element för vy (format)](./controls-element-for-view-format.md)

[GroupBy-element för vy (format)](./groupby-element-for-view-format.md)

[TableControl-element (format)](./tablecontrol-element-format.md)

[ListControl-element (format)](./listcontrol-element-format.md)

[WideControl-element (format)](./widecontrol-element-format.md)

[CustomControl-element (format)](./customcontrol-element-for-groupby-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
