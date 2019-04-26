---
title: ScriptBlock Element för WideItem för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064211"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>ScriptBlock-element för WideItem för WideControl (format)

Anger skriptet vars värde visas i bred vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock konfigurationselement för WideItem (Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `ScriptBlock` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideItem Element (Format)](./wideitem-element-for-widecontrol-format.md)|Definierar egenskapen eller skript blocket vars värde visas i bred vy.|

## <a name="text-value"></a>Textvärde

Ange skriptet vars värde visas.

## <a name="remarks"></a>Anmärkningar

Mer information om komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar en `WideItem` -element som definierar ett skript som vars värde visas i vyn.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Se även

[WideItem Element (Format)](./wideitem-element-for-widecontrol-format.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
