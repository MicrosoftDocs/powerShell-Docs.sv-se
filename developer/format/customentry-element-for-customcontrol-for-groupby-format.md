---
title: CustomEntry Element för anpassad kontroll för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849870"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>CustomEntry-element för CustomControl för GroupBy (format)

Innehåller en definition av kontrollen. Det här elementet används när du definierar hur en ny grupp med objekt visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och de överordnade element i den `CustomEntry` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[EntrySelectedBy Element för CustomEntry för GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas.|
|[CustomItem Element för CustomEntry för GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Element som krävs.<br /><br /> Definierar hur data visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntries Element för anpassad kontroll för GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)|Innehåller definitioner för kontrollen.|

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[EntrySelectedBy Element för CustomEntry för GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[CustomItem Element för CustomEntry för GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[CustomEntries Element för anpassad kontroll för GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
