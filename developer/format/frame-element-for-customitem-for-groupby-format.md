---
title: RAM-Element för CustomItem för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846006"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Frame-element för CustomItem för GroupBy (format)

Definierar hur data visas, till exempel ändra datatypen till vänster eller höger. Det här elementet används när du definierar hur en ny grupp med objekt visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) CustomItem elementet för CustomEntry för GroupBy (Format) RAM-elementet för CustomItem för GroupBy (Format)

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Frame` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|`CustomItem Element`|Element som krävs|
|[FirstLineHanging Element för ramens för GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som den första raden av data ska flyttas till vänster.|
|[FirstLineIndent Element för ramens för GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som den första raden av data ska flyttas till höger.|
|[LeftIndent Element för ramens för GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som data ska flyttas från vänster marginal.|
|[RightIndent Element för ramens för GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element|Valfritt element.<br /><br /> Anger hur många tecken som data ska flyttas från höger marginal.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem Element för CustomEntry för GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Definierar vilka data som visas av kontrollen och hur de visas.|

## <a name="remarks"></a>Anmärkningar

Du kan inte ange den [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) element i samma `Frame` element.

## <a name="see-also"></a>Se även

[FirstLineHanging Element för ramens för GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[FirstLineIndent Element för ramens för GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[LeftIndent Element för ramens för GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md)

[RightIndent Element för ramens för GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)

[CustomItem Element för CustomEntry för GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
