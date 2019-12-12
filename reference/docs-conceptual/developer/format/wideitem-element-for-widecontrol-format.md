---
title: WideItem-element för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353405"
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

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `WideItem`-elementet. `FormatString`-elementet är valfritt. Du måste dock ange ett `PropertyName`-eller `ScriptBlock`-element, men du kan inte ange båda.

### <a name="attributes"></a>Attribut

Ingen.

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

## <a name="remarks"></a>Anmärkningar

Mer information om komponenterna i en bred vy finns i [wide View](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

I följande exempel visas ett `WideEntry`-element som definierar ett enskilt `WideItem`-element. `WideItem`-elementet definierar egenskapen eller skriptet vars värde visas i vyn.

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

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
