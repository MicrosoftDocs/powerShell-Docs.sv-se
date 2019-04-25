---
title: Kontrollera Element för kontroller för Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066807"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Control-element för Controls för Configuration (format)

Definierar en gemensam kontroll som kan användas av alla vyer av filen formatering och det namn som används för att referera till kontrollen.

Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för konfiguration (Format)

## <a name="syntax"></a>Syntax

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för den `Control` element. Du måste ange endast en av varje underordnat element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Anpassad kontroll Element för kontroll för kontroller för konfiguration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Element som krävs.<br /><br /> Definierar kontrollen.|
|[Namnelement för kontroll för konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)|Element som krävs.<br /><br /> Anger namnet som refererar till kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Kontroller Element av konfigurationen (Format)](./controls-element-for-configuration-format.md)|Definierar de vanliga kontroller som kan användas av alla vyer i filen formatering eller av andra kontroller.|

## <a name="remarks"></a>Anmärkningar

Namnet på den här kontrollen kan refereras i följande element:

- [ExpressionBinding Element för CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [GroupBy-Element för View(Format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Se även

[Kontroller Element av konfigurationen (Format)](./controls-element-for-configuration-format.md)

[Anpassad kontroll element för kontroll för konfiguration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[ExpressionBinding Element för CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[GroupBy-Element för View(Format)](./groupby-element-for-view-format.md)

[Namnelement för kontroll för kontroller för konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
