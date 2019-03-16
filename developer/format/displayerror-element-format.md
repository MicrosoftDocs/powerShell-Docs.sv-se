---
title: DisplayError Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056489"
---
# <a name="displayerror-element-format"></a>DisplayError-element (format)

Anger att strängen #ERR visas när ett fel uppstår visar en typ av data.

Elementet (Format) DefaultSettings Element (Format) DisplayError konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `DisplayError` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[DefaultSettings Element (Format)](./defaultsettings-element-format.md)|Definierar gemensamma inställningar som gäller för alla vyer i filen formatering.|

## <a name="remarks"></a>Anmärkningar

Som standard när ett fel uppstår när du försöker visa en typ av data, är platsen för dina data tomt. När det här elementet har angetts till true, #ERR sträng visas.

## <a name="see-also"></a>Se även

[DefaultSettings Element (Format)](./defaultsettings-element-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
