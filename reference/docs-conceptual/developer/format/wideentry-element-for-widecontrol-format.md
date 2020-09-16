---
title: WideEntry-element för WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13dd1f6ad7ac1e9d8d0524f0a0f18fe80ffaf8e2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780023"
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

I följande avsnitt beskrivs attributen, underordnade element och `WideEntry` elementets överordnade element. Du måste ange ett enda `WideItem` underordnat element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy-element för WideEntry (format)](./entryselectedby-element-for-wideentry-format.md)|Valfritt element.<br /><br /> Definierar de .NET-typer som använder den här breda post definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.|
|[WideItem-element (format)](./wideitem-element-for-widecontrol-format.md)|Nödvändigt element.<br /><br /> Definierar egenskapen eller skriptet vars värde visas.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideEntries-element (format)](./wideentries-element-for-widecontrol-format.md)|Innehåller definitionerna för den breda vyn.|

## <a name="remarks"></a>Kommentarer

En bred vy är ett List format som visar ett enda egenskaps värde eller skript värde för varje objekt. Till skillnad från andra typer av vyer kan du bara ange ett objekt element för varje vydefinition. Mer information om de andra komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

I följande exempel visas ett `WideEntry` element som definierar ett enda `WideItem` element. `WideItem`Elementet definierar den egenskap vars värde visas i vyn.

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

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
