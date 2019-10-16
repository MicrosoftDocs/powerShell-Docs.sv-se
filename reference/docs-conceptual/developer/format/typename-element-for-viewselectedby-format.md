---
title: Elementet TypeName för ViewSelectedBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353433"
---
# <a name="typename-element-for-viewselectedby-format"></a>TypeName-element för ViewSelectedBy (format)

Anger ett .NET-objekt som visas i vyn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ViewSelectedBy-element (format) element för ViewSelectedBy (format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och de överordnade elementen för elementet `TypeName`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ViewSelectedBy-element (format)](./viewselectedby-element-format.md)|Definierar de .NET-objekt som visas i vyn.|

## <a name="text-value"></a>Text värde

Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex. `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Anmärkningar

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

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
