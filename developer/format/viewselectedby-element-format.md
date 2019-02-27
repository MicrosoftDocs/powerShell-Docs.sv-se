---
title: ViewSelectedBy Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851844"
---
# <a name="viewselectedby-element-format"></a>ViewSelectedBy-element (format)

Definierar de .NET-objekt som visas i vyn. Varje vy måste ange minst en .NET-objekt.

ViewDefinitions Element (Format) visa Element (Format) ViewSelectedBy Element (Format)

## <a name="syntax"></a>Syntax

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `ViewSelectedBy` element. Det här elementet måste innehålla minst ett `TypeName` eller `SelectionSetName` underordnat element. Det finns ingen gräns för antalet underordnade element som kan anges och kan inte heller deras inbördes ordning betydande.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TypeName-Element för ViewSelectedBy (Format)](./typename-element-for-viewselectedby-format.md)|Valfritt element.<br /><br /> Anger ett .NET-objekt som visas i vyn.|
|[SelectionSetName Element för ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)|Valfritt element.<br /><br /> Anger en uppsättning med .NET-objekt som visas i vyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Visa Element (Format)](./view-element-format.md)|Definierar en vy som visar en eller flera .NET-objekt.|

## <a name="remarks"></a>Anmärkningar

Mer information om hur det här elementet används i olika vyer finns i [tabell visa komponenter](./creating-a-table-view.md), [listan Visa komponenter](./creating-a-list-view.md), [bred vy komponenter](./creating-a-wide-view.md), och [Anpassad kontroll komponenter](./creating-custom-controls.md).

Den `SelectionSetName` element som ska användas när filen formatering definierar en uppsättning objekt som visas i flera vyer. Mer information om hur inställningarna definieras och refererar till finns i [definiera anger av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du anger den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt för en listvy. Samma schema används för tabellen, bred och anpassade vyer.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[Skapa en tabellvy](./creating-a-table-view.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Skapa anpassade kontroller](./creating-custom-controls.md)

[Definiera inställningarna](./defining-selection-sets.md)

[SelectionSetName Element för ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName-Element (Format)](./typename-element-for-viewselectedby-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
