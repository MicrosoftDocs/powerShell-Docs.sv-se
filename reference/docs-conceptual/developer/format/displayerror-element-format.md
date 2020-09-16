---
title: DisplayError-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5d46c2fbd48f592db5ba1b33eb6cead8dc1c4698
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774294"
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
