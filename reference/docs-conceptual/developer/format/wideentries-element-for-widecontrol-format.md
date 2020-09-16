---
title: WideEntries-element för WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74383b288c945008c1d7b5119363a166c04802ae
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785055"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideEntries-element för WideControl (format)

Innehåller definitionerna för den breda vyn. Wide View måste ange en eller flera definitioner.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) element för WideEntries (format)

## <a name="syntax"></a>Syntax

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `WideEntries` elementets överordnade element. Minst ett underordnat element måste anges.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideEntry-element (format)](./wideentry-element-for-widecontrol-format.md)|Ger en definition av den breda vyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideControl-element (format)](./widecontrol-element-format.md)|Definierar ett brett List format (enskilt värde) för vyn.|

## <a name="remarks"></a>Kommentarer

En bred vy är ett List format som visar ett enda egenskaps värde eller skript värde för varje objekt. Mer information om komponenterna i en bred vy finns i [wide View-komponenter](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

I följande exempel visas ett `WideEntries` element som definierar ett enda `WideEntry` element. `WideEntry`Elementet innehåller ett enda `WideItem` element som definierar vilken egenskap eller vilket skript värde som visas i vyn.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Ett fullständigt exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[WideControl-element (format)](./widecontrol-element-format.md)

[WideEntry-element (format)](./wideentry-element-for-widecontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
