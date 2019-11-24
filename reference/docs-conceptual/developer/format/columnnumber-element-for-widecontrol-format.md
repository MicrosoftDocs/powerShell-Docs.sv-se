---
title: ColumnNumber-element för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355379"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>ColumnNumber-element för WideControl (format)

Anger antalet kolumner som visas i den bred vyn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) element för WideControl (format)

## <a name="syntax"></a>Syntax

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `ColumnNumber`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Description|
|-------------|-----------------|
|[WideControl-element (format)](./widecontrol-element-format.md)|Definierar ett brett List format (enskilt värde) för vyn.|

## <a name="text-value"></a>Text värde

Ange ett positivt heltals värde.

## <a name="remarks"></a>Kommentarer

När du definierar en bred vy kan du lägga till `AutoSize`-elementet eller `ColumnNumber`-elementet, men du kan inte lägga till båda.

Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

Ett exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).

## <a name="see-also"></a>Se även

[AutoSize-element för WideControl (format)](./autosize-element-for-widecontrol-format.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Bred vy (grundläggande)](./wide-view-basic.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
