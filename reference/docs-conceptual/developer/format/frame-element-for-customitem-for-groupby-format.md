---
title: Ram element för CustomItem for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354490"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Frame-element för CustomItem för GroupBy (format)

Definierar hur data visas, till exempel att flytta data till vänster eller höger. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl för GroupBy (format) CustomItem-element för CustomEntry för GroupBy (format)-ram element för CustomItem för GroupBy (format)

## <a name="syntax"></a>Syntax

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `Frame`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|`CustomItem Element`|Nödvändigt element|
|[FirstLineHanging-element för inramad GroupBy (format)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Valfritt element.<br /><br /> Anger hur många tecken den första raden med data flyttas till vänster.|
|[FirstLineIndent-element för inramad GroupBy (format)](./firstlineindent-element-for-frame-for-groupby-format.md)|Valfritt element.<br /><br /> Anger hur många tecken den första raden med data flyttas till höger.|
|[LeftIndent-element för inramad GroupBy (format)](./leftindent-element-for-frame-for-groupby-format.md)|Valfritt element.<br /><br /> Anger hur många tecken data flyttas bort från vänstermarginalen.|
|[RightIndent-element för inramad groupby (format)](./rightindent-element-for-frame-for-groupby-format.md) RightIndent-element|Valfritt element.<br /><br /> Anger hur många tecken data flyttas bort från högermarginalen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem-element för CustomEntry för GroupBy (format)](./customitem-element-for-customentry-for-groupby-format.md)|Definierar vilka data som visas av kontrollen och hur de visas.|

## <a name="remarks"></a>Anmärkningar

Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -elementen i samma `Frame`-element.

## <a name="see-also"></a>Se även

[FirstLineHanging-element för inramad GroupBy (format)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[FirstLineIndent-element för inramad GroupBy (format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[LeftIndent-element för inramad GroupBy (format)](./leftindent-element-for-frame-for-groupby-format.md)

[RightIndent-element för inramad GroupBy (format)](./rightindent-element-for-frame-for-groupby-format.md)

[CustomItem-element för CustomEntry för GroupBy (format)](./customitem-element-for-customentry-for-groupby-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
