---
title: WideEntries Element för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083696"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideEntries-element för WideControl (format)

Innehåller definitioner av bred vy. Bred vy måste ange en eller flera definitioner.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `WideEntries` element. Du måste ange minst ett underordnat element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideEntry Element (Format)](./wideentry-element-for-widecontrol-format.md)|Innehåller en definition av bred vy.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideControl Element (Format)](./widecontrol-element-format.md)|Definierar en bred (enstaka värde) listformat för vyn.|

## <a name="remarks"></a>Anmärkningar

En bred vy är ett listformat som visar en enda egenskapsvärdet eller skriptvärde för varje objekt. Mer information om komponenter för en bred vy finns i [bred vy komponenter](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

I följande exempel visas en `WideEntries` -element som definierar en enda `WideEntry` element. Den `WideEntry` elementet innehåller en enda `WideItem` element som definierar vilket värde som egenskapen eller skript visas i vyn.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Exempel på en bred vy, se [bred vy (grundläggande)](./wide-view-basic.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[WideControl Element (Format)](./widecontrol-element-format.md)

[WideEntry Element (Format)](./wideentry-element-for-widecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
