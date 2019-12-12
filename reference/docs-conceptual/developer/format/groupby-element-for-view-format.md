---
title: GroupBy-element för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354966"
---
# <a name="groupby-element-for-view-format"></a>GroupBy-element för View (format)

Definierar hur en ny grupp av objekt visas. Det här elementet används när du definierar en tabell, en lista, en bred eller en anpassad vy.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för vy (format)

## <a name="syntax"></a>Syntax

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och överordnade element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomControl-element för GroupBy (format)](./customcontrol-element-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar den anpassade kontrollen som visar nya grupper.|
|[CustomControlName-element för GroupBy (format)](./customcontrolname-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger namnet på en kontroll som används för att visa den nya gruppen.|
|[Etikett element för GroupBy (format)](./label-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger en etikett som visas när en ny grupp påträffas.|
|[PropertyName-element för GroupBy (format)](./propertyname-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger .NET-egenskapen som startar en ny grupp när dess värde ändras.|
|[Script block-element för GroupBy (format)](./scriptblock-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger det skript som startar en ny grupp när dess värde ändras.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Visa element (format)](./view-element-format.md)|Definierar en vy som visar ett eller flera .NET-objekt.|

## <a name="remarks"></a>Anmärkningar

När du definierar hur en ny grupp av objekt visas måste du ange den egenskap eller det skript som ska starta den nya gruppen. Du kan dock inte ange båda.

## <a name="see-also"></a>Se även

[CustomControlName-element för GroupBy (format)](./customcontrolname-element-for-groupby-format.md)

[Etikett element för GroupBy (format)](./label-element-for-groupby-format.md)

[PropertyName-element för GroupBy (format)](./propertyname-element-for-groupby-format.md)

[Script block-element för GroupBy (format)](./scriptblock-element-for-groupby-format.md)

[Visa element (format)](./view-element-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
