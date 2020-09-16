---
title: ViewSelectedBy-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8704c1504c6e24c9cac6bc8bc25e92a0d9110cc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785021"
---
# <a name="viewselectedby-element-format"></a>ViewSelectedBy-element (format)

Definierar de .NET-objekt som visas i vyn. Varje vy måste innehålla minst ett .NET-objekt.

ViewDefinitions-element (format) Visa element (format) ViewSelectedBy-element (format)

## <a name="syntax"></a>Syntax

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `ViewSelectedBy` elementets överordnade element. Elementet måste innehålla minst ett `TypeName` eller `SelectionSetName` underordnat element. Det finns ingen gräns för antalet underordnade element som kan anges eller som är deras inbördes ordning.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TypeName-element för ViewSelectedBy (format)](./typename-element-for-viewselectedby-format.md)|Valfritt element.<br /><br /> Anger ett .NET-objekt som visas i vyn.|
|[SelectionSetName-element för ViewSelectedBy (format)](./selectionsetname-element-for-viewselectedby-format.md)|Valfritt element.<br /><br /> Anger en uppsättning .NET-objekt som visas i vyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[View-element (format)](./view-element-format.md)|Definierar en vy som visar ett eller flera .NET-objekt.|

## <a name="remarks"></a>Kommentarer

Mer information om hur det här elementet används i olika vyer finns i [tabellvy komponenter](./creating-a-table-view.md), [list Visa](./creating-a-list-view.md)komponenter, [wide View-komponenter](./creating-a-wide-view.md)och [anpassade kontroll komponenter](./creating-custom-controls.md).

`SelectionSetName`Elementet används när format filen definierar en uppsättning objekt som visas av flera vyer. Mer information om hur urvals uppsättningar definieras och refereras till finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du anger objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) för en listvy. Samma schema används för tabeller, breda och anpassade vyer.

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

[Definiera valuppsättningar](./defining-selection-sets.md)

[SelectionSetName-element för ViewSelectedBy (format)](./selectionsetname-element-for-viewselectedby-format.md)

[Elementet TypeName (format)](./typename-element-for-viewselectedby-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
