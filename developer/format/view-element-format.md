---
title: Visa Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846916"
---
# <a name="view-element-format"></a>View-element (format)

Definierar en vy som visar en eller flera .NET-objekt. Det finns ingen gräns för antal vyer som kan definieras i en fil med formatering.

Elementet (Format) ViewDefinitions Element (Format) visa konfigurationselement (Format)

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `View` element. Du måste ange endast en av kontroll underordnade element och du måste ange namnet på vyn och de objekt som använder vyn. Definiera anpassade kontroller, gruppering objekt och ange om vyn är out-of-band är valfria.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Kontroller Element för vy (Format)](./controls-element-for-view-format.md)|Valfritt element.<br /><br /> Definierar en uppsättning kontroller som kan refereras av deras namn från i vyn.|
|[Anpassad kontroll Element (Format)](./customcontrol-element-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar en anpassad kontroll format för vyn.|
|[GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)|Valfritt element.<br /><br /> Definierar hur medlemmarna i .NET-objekt grupperas.|
|[ListControl Element (Format)](./listcontrol-element-format.md)|Valfritt element.<br /><br /> Definierar ett listformat för vyn.|
|[Namnelement för vy (Format)](./name-element-for-view-format.md)|Element som krävs.<br /><br /> Anger namnet som refererar till vyn.|
|[TableControl Element (Format)](./tablecontrol-element-format.md)|Valfritt element.<br /><br /> Definierar ett tabellformat för vyn.|
|[ViewSelectedBy Element för vy (Format)](./viewselectedby-element-format.md)|Element som krävs.<br /><br /> Definierar de .NET-objekt som den här vyn visas.|
|[WideControl Element (Format)](./widecontrol-element-format.md)|Valfritt element.<br /><br /> Definierar en bred (enstaka värde) listformat för vyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ViewDefinitions Element (Format)](./viewdefinitions-element-format.md)|Definierar de vyer som används för att visa objekt.|

## <a name="remarks"></a>Anmärkningar

Mer information om komponenter av olika vyer och anpassade kontroller finns i följande avsnitt:

- [Tabell visa komponenter](./creating-a-table-view.md)

- [Listan Visa komponenter](./creating-a-list-view.md)

- [Bred vy komponenter](./creating-a-wide-view.md)

- [Anpassade kontroller](./creating-custom-controls.md)

## <a name="example"></a>Exempel

Det här exemplet visar en `View` -element som definierar en tabellvy för den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt.

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

[ViewDefinitions Element (Format)](./viewdefinitions-element-format.md)

[Namnelement för vy (Format)](./name-element-for-view-format.md)

[ViewSelectedBy Element (Format)](./viewselectedby-element-format.md)

[Kontroller Element för vy (Format)](./controls-element-for-view-format.md)

[GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md)

[TableControl Element (Format)](./tablecontrol-element-format.md)

[ListControl Element (Format)](./listcontrol-element-format.md)

[WideControl Element (Format)](./widecontrol-element-format.md)

[Anpassad kontroll Element (Format)](./customcontrol-element-for-groupby-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
