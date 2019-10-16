---
title: WideEntry-element för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353157"
---
# <a name="wideentry-element-for-widecontrol-format"></a>WideEntry-element för WideControl (format)

Ger en definition av den breda vyn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format)

## <a name="syntax"></a>Syntax

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `WideEntry`. Du måste ange ett enskilt `WideItem`-underordnat element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för WideEntry (format)](./entryselectedby-element-for-wideentry-format.md)|Valfritt element.<br /><br /> Definierar de .NET-typer som använder den här breda post definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.|
|[WideItem-element (format)](./wideitem-element-for-widecontrol-format.md)|Nödvändigt element.<br /><br /> Definierar egenskapen eller skriptet vars värde visas.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideEntries-element (format)](./wideentries-element-for-widecontrol-format.md)|Innehåller definitionerna för den breda vyn.|

## <a name="remarks"></a>Anmärkningar

En bred vy är ett List format som visar ett enda egenskaps värde eller skript värde för varje objekt. Till skillnad från andra typer av vyer kan du bara ange ett objekt element för varje vydefinition. Mer information om de andra komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

I följande exempel visas ett `WideEntry`-element som definierar ett enda `WideItem`-element. Elementet `WideItem` definierar den egenskap vars värde visas i vyn.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Ett fullständigt exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[SelectionCondition-element för WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName-element för WideEntry (format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Elementet TypeName för WideEntry (format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[WideEntries-element (format)](./wideentries-element-for-widecontrol-format.md)

[WideItem-element (format)](./wideitem-element-for-widecontrol-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
