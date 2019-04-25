---
title: Antal_kolumner anger Element för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066914"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>ColumnNumber-element för WideControl (format)

Anger antalet kolumner som visas i bred vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) antal_kolumner anger konfigurationselement för WideControl (Format)

## <a name="syntax"></a>Syntax

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ColumnNumber` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideControl Element (Format)](./widecontrol-element-format.md)|Definierar en bred (enstaka värde) listformat för vyn.|

## <a name="text-value"></a>Textvärde

Ange ett positivt heltalsvärde.

## <a name="remarks"></a>Anmärkningar

När du definierar en bred vy, kan du lägga till den `AutoSize` element eller `ColumnNumber` element, men du kan inte lägga till båda.

Mer information om komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).

Ett exempel på en bred vy finns i [bred vy (grundläggande)](./wide-view-basic.md).

## <a name="see-also"></a>Se även

[AutoSize-Element för WideControl (Format)](./autosize-element-for-widecontrol-format.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Bred vy (grundläggande)](./wide-view-basic.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
