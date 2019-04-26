---
title: WideItem Element för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083645"
---
# <a name="wideitem-element-for-widecontrol-format"></a>WideItem-element för WideControl (format)

Definierar egenskapen eller skript som vars värde visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `WideItem` element. Den `FormatString` element är valfria. Du måste dock ange en `PropertyName` eller `ScriptBlock` element, men du kan inte ange båda.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[FormatString-Element för WideItem för WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Valfritt element.<br /><br /> Anger ett formatmönster som definierar hur värdet för egenskapen eller skript visas i vyn.|
|[PropertyName-Element för WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Anger egenskapen för objektet vars värde visas i bred vy.|
|[ScriptBlock Element för WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Anger skriptet vars värde visas i bred vy.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideEntry Element (Format)](./wideentry-element-for-widecontrol-format.md)|Innehåller en definition av bred vy.|

## <a name="remarks"></a>Anmärkningar

Mer information om komponenter för en bred vy finns i [bred vy](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

I följande exempel visas en `WideEntry` -element som definierar en enda `WideItem` element. Den `WideItem` elementet definierar egenskapen eller skript som vars värde visas i vyn.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Exempel på en bred vy, se [bred vy (grundläggande)](./wide-view-basic.md).

## <a name="see-also"></a>Se även

[FormatString-Element för WideItem för WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[PropertyName-Element för WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[ScriptBlock Element för WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[WideEntry Element (Format)](./wideentry-element-for-widecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
