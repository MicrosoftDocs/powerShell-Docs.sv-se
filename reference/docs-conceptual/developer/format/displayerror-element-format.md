---
ms.date: 09/13/2016
ms.topic: reference
title: DisplayError-element (format)
description: DisplayError-element (format)
ms.openlocfilehash: fb54df86a3558263687a8c417870495b7066f563
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649927"
---
# <a name="displayerror-element-format"></a>DisplayError-element (format)

Anger att strängen #ERR visas när det uppstår ett fel vid visning av en data del.

Konfigurations element (format) DefaultSettings-element (format) DisplayError-element (format)

## <a name="syntax"></a>Syntax

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `DisplayError` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[DefaultSettings-element (format)](./defaultsettings-element-format.md)|Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.|

## <a name="remarks"></a>Kommentarer

När ett fel inträffar när ett fel inträffar när ett data försöker visas, lämnas som standard data platsen tom. När det här elementet är inställt på True visas #ERR strängen.

## <a name="see-also"></a>Se även

[DefaultSettings-element (format)](./defaultsettings-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
