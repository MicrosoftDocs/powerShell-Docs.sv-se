---
title: DisplayError-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355218"
---
# <a name="displayerror-element-format"></a>DisplayError-element (format)

Anger att strängen #ERR visas när det uppstår ett fel vid visning av en data del.

Konfigurations element (format) DefaultSettings-element (format) DisplayError-element (format)

## <a name="syntax"></a>Syntax

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `DisplayError`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[DefaultSettings-element (format)](./defaultsettings-element-format.md)|Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.|

## <a name="remarks"></a>Anmärkningar

När ett fel inträffar när ett fel inträffar när ett data försöker visas, lämnas som standard data platsen tom. När det här elementet är inställt på True visas #ERR strängen.

## <a name="see-also"></a>Se även

[DefaultSettings-element (format)](./defaultsettings-element-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
