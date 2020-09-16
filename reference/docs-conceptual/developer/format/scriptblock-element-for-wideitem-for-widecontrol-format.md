---
title: Script block-element för WideItem för WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: be649d6de0d2dfa6bad14f2d7476cced9cd6cb6d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787605"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>ScriptBlock-element för WideItem för WideControl (format)

Anger det skript vars värde visas i den breda vyn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) WideItem element (format) script block-element för WideItem (format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `ScriptBlock` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideItem-element (format)](./wideitem-element-for-widecontrol-format.md)|Definierar egenskapen eller skript blocket vars värde visas i den breda vyn.|

## <a name="text-value"></a>Textvärde

Ange det skript vars värde visas.

## <a name="remarks"></a>Kommentarer

Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar ett- `WideItem` element som definierar ett skript vars värde visas i vyn.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Se även

[WideItem-element (format)](./wideitem-element-for-widecontrol-format.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
