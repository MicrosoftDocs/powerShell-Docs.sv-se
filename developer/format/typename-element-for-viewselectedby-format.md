---
title: TypeName-Element för ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083764"
---
# <a name="typename-element-for-viewselectedby-format"></a>TypeName-element för ViewSelectedBy (format)

Anger ett .NET-objekt som visas i vyn.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ViewSelectedBy Element (Format) TypeName konfigurationselement för ViewSelectedBy (Format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och de överordnade element i den `TypeName` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ViewSelectedBy Element (Format)](./viewselectedby-element-format.md)|Definierar de .NET-objekt som visas i vyn.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typ, till exempel `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Anmärkningar

Mer information om hur det här elementet används i olika vyer finns i [skapar en tabellvy](./creating-a-table-view.md), [skapar en listvy](./creating-a-list-view.md), [skapar en bred vy](./creating-a-wide-view.md), och [ Anpassad vy komponenter](./creating-custom-controls.md).

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

[ViewSelectedBy Element (Format)](./viewselectedby-element-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
