---
title: WideEntries-element för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353426"
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

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `WideEntries`-elementet. Minst ett underordnat element måste anges.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideEntry-element (format)](./wideentry-element-for-widecontrol-format.md)|Ger en definition av den breda vyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideControl-element (format)](./widecontrol-element-format.md)|Definierar ett brett List format (enskilt värde) för vyn.|

## <a name="remarks"></a>Anmärkningar

En bred vy är ett List format som visar ett enda egenskaps värde eller skript värde för varje objekt. Mer information om komponenterna i en bred vy finns i [wide View-komponenter](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

I följande exempel visas ett `WideEntries`-element som definierar ett enda `WideEntry`-element. Elementet `WideEntry` innehåller ett enda `WideItem`-element som definierar vilken egenskap eller vilket skript värde som visas i vyn.

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

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
