---
title: Kontrollerar element för konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359097"
---
# <a name="controls-element-for-configuration-format"></a>Controls-element för Configuration (format)

Definierar de gemensamma kontroller som kan användas av alla vyer i formaterings filen.

Konfigurations element (format) styr elementet i konfigurationen (format)

## <a name="syntax"></a>Syntax

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `Controls`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Kontroll element för konfigurations kontroll (format)](./control-element-for-controls-for-configuration-format.md)|Nödvändigt element.<br /><br /> Definierar en gemensam kontroll som kan användas av alla vyer i formaterings filen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Konfigurations element (format)](./configuration-element-format.md)|Representerar det översta elementet i en textfil.|

## <a name="remarks"></a>Anmärkningar

Du kan skapa valfritt antal vanliga kontroller. För varje kontroll måste du ange det namn som ska användas för att referera till kontrollen och kontrollens komponenter.

## <a name="see-also"></a>Se även

[Konfigurations element (format)](./configuration-element-format.md)

[Kontroll element för konfigurations kontroll (format)](./control-element-for-controls-for-configuration-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
