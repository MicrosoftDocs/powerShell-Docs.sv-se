---
title: PropertyName-element för WideItem för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355883"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>PropertyName-element för WideItem för WideControl (format)

Anger egenskapen för det objekt vars värde visas i den bred vyn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) WideItem element (format) PropertyName-element för WideItem (format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `PropertyName`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideItem-element (format)](./wideitem-element-for-widecontrol-format.md)|Definierar egenskapen eller skriptet vars värde visas i den breda vyn.|

## <a name="text-value"></a>Text värde

Ange namnet på den egenskap vars värde visas.

## <a name="remarks"></a>Anmärkningar

Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

I det här exemplet visas en bred vy som visar värdet för egenskapen ProcessName för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a>Se även

[WideItem-element (format)](./wideitem-element-for-widecontrol-format.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
