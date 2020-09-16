---
title: GroupBy-element för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2f9071a3ebbc7cc2ccb7721dd518e82723e9cc4e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781434"
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

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomControl-element för GroupBy (format)](./customcontrol-element-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar den anpassade kontrollen som visar nya grupper.|
|[CustomControlName-element för GroupBy (format)](./customcontrolname-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger namnet på en kontroll som används för att visa den nya gruppen.|
|[Label-element för GroupBy (format)](./label-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger en etikett som visas när en ny grupp påträffas.|
|[PropertyName-element för GroupBy (format)](./propertyname-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger .NET-egenskapen som startar en ny grupp när dess värde ändras.|
|[ScriptBlock-element för GroupBy (format)](./scriptblock-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger det skript som startar en ny grupp när dess värde ändras.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[View-element (format)](./view-element-format.md)|Definierar en vy som visar ett eller flera .NET-objekt.|

## <a name="remarks"></a>Kommentarer

När du definierar hur en ny grupp av objekt visas måste du ange den egenskap eller det skript som ska starta den nya gruppen. Du kan dock inte ange båda.

## <a name="see-also"></a>Se även

[CustomControlName-element för GroupBy (format)](./customcontrolname-element-for-groupby-format.md)

[Label-element för GroupBy (format)](./label-element-for-groupby-format.md)

[PropertyName-element för GroupBy (format)](./propertyname-element-for-groupby-format.md)

[ScriptBlock-element för GroupBy (format)](./scriptblock-element-for-groupby-format.md)

[View-element (format)](./view-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
