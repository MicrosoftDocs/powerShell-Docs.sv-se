---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för ViewSelectedBy (format)
description: TypeName-element för ViewSelectedBy (format)
ms.openlocfilehash: 62edc2fe4b4c1c5f1b17dd2f8b0943f28ff5dfb7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667733"
---
# <a name="typename-element-for-viewselectedby-format"></a>TypeName-element för ViewSelectedBy (format)

Anger ett .NET-objekt som visas i vyn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ViewSelectedBy-element (format) element för ViewSelectedBy (format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ViewSelectedBy-element (format)](./viewselectedby-element-format.md)|Definierar de .NET-objekt som visas i vyn.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..

## <a name="remarks"></a>Kommentarer

Mer information om hur det här elementet används i olika vyer finns i [skapa en tabellvy](./creating-a-table-view.md), [skapa en listvy](./creating-a-list-view.md), [skapa en bred vy](./creating-a-wide-view.md)och [Anpassa View-komponenter](./creating-custom-controls.md).

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

[ViewSelectedBy-element (format)](./viewselectedby-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
