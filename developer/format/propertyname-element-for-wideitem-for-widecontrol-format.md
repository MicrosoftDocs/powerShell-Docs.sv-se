---
title: PropertyName-Element för WideItem för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850283"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>PropertyName-element för WideItem för WideControl (format)

Anger egenskapen för objektet vars värde visas i bred vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName konfigurationselement för WideItem (Format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `PropertyName` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideItem Element (Format)](./wideitem-element-for-widecontrol-format.md)|Definierar egenskapen eller skript som vars värde visas i bred vy.|

## <a name="text-value"></a>Textvärde

Ange namnet på egenskapen vars värde visas.

## <a name="remarks"></a>Anmärkningar

Mer information om komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar en bred vy som visar värdet för egenskapen ProcessName för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.

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

[WideItem Element (Format)](./wideitem-element-for-widecontrol-format.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
