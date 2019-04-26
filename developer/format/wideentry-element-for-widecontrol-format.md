---
title: WideEntry Element för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083679"
---
# <a name="wideentry-element-for-widecontrol-format"></a>WideEntry-element för WideControl (format)

Innehåller en definition av bred vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `WideEntry` element. Du måste ange en enda `WideItem` underordnat element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Valfritt element.<br /><br /> Definierar vilka typer av .NET som använder den här definitionen för bred posten eller villkor som måste finnas för den här definitionen som ska användas.|
|[WideItem Element (Format)](./wideitem-element-for-widecontrol-format.md)|Element som krävs.<br /><br /> Definierar egenskapen eller skript som vars värde visas.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideEntries Element (Format)](./wideentries-element-for-widecontrol-format.md)|Innehåller definitioner av bred vy.|

## <a name="remarks"></a>Anmärkningar

En bred vy är ett listformat som visar en enda egenskapsvärdet eller skriptvärde för varje objekt. Till skillnad från andra typer av vyer kan ange du endast ett angivet objekt-element för varje vydefinitionen. Mer information om de andra komponenterna för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

I följande exempel visas en `WideEntry` -element som definierar en enda `WideItem` element. Den `WideItem` elementet definierar egenskapen vars värde visas i vyn.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Exempel på en bred vy, se [bred vy (grundläggande)](./wide-view-basic.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[SelectionCondition Element för WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName Element för WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[TypeName-Element för WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[WideEntries Element (Format)](./wideentries-element-for-widecontrol-format.md)

[WideItem Element (Format)](./wideitem-element-for-widecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
