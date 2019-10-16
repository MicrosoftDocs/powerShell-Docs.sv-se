---
title: Script block-element för WideItem för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353846"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>ScriptBlock-element för WideItem för WideControl (format)

Anger det skript vars värde visas i den breda vyn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) WideItem element (format) script block-element för WideItem (format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `ScriptBlock`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[WideItem-element (format)](./wideitem-element-for-widecontrol-format.md)|Definierar egenskapen eller skript blocket vars värde visas i den breda vyn.|

## <a name="text-value"></a>Text värde

Ange det skript vars värde visas.

## <a name="remarks"></a>Anmärkningar

Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar ett `WideItem`-element som definierar ett skript vars värde visas i vyn.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Se även

[WideItem-element (format)](./wideitem-element-for-widecontrol-format.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
