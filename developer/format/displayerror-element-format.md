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
ms.openlocfilehash: 431e5d8407b9f689a5224b329d8c7b52802e19e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846055"
---
# <a name="displayerror-element-format"></a>DisplayError-element (format)

Anger att strängen #ERR visas när ett fel uppstår visar en typ av data.

Elementet (Format) DefaultSettings Element (Format) DisplayError konfigurationselement (Frmat)

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
