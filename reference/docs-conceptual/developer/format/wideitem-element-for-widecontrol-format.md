---
title: WideItem-element för WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6b2f7c97978c20350caeec894589c5995ae7ccc4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779904"
---
# <a name="wideitem-element-for-widecontrol-format"></a>WideItem-element för WideControl (format)

Definierar egenskapen eller skriptet vars värde visas.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) WideItem-element (format)

## <a name="syntax"></a>Syntax

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `WideItem` elementets överordnade element. `FormatString`Elementet är valfritt. Du måste dock ange ett `PropertyName` eller `ScriptBlock` -element, men du kan inte ange båda.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[FormatString-element för WideItem för WideControl (format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Valfritt element.<br /><br /> Anger ett format mönster som definierar hur egenskapen eller skriptets värde visas i vyn.|
|[PropertyName-element för WideItem (format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Anger egenskapen för det objekt vars värde visas i den bred vyn.|
|[Script block-element för WideItem (format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Anger det skript vars värde visas i den breda vyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideEntry-element (format)](./wideentry-element-for-widecontrol-format.md)|Ger en definition av den breda vyn.|

## <a name="remarks"></a>Kommentarer

Mer information om komponenterna i en bred vy finns i [wide View](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

I följande exempel visas ett `WideEntry` element som definierar ett enda `WideItem` element. `WideItem`Elementet definierar egenskapen eller skriptet vars värde visas i vyn.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Ett fullständigt exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).

## <a name="see-also"></a>Se även

[FormatString-element för WideItem för WideControl (format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[PropertyName-element för WideItem (format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[Script block-element för WideItem (format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[WideEntry-element (format)](./wideentry-element-for-widecontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
