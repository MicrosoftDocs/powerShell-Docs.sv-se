---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för WideItem för WideControl (format)
description: PropertyName-element för WideItem för WideControl (format)
ms.openlocfilehash: 1d4d5eaf7708dfbd7997122fac156a36487538ea
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665625"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>PropertyName-element för WideItem för WideControl (format)

Anger egenskapen för det objekt vars värde visas i den bred vyn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) WideItem element (format) PropertyName-element för WideItem (format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `PropertyName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideItem-element (format)](./wideitem-element-for-widecontrol-format.md)|Definierar egenskapen eller skriptet vars värde visas i den breda vyn.|

## <a name="text-value"></a>Textvärde

Ange namnet på den egenskap vars värde visas.

## <a name="remarks"></a>Kommentarer

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

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
