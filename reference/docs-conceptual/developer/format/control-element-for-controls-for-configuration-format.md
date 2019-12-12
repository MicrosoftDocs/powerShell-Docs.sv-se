---
title: Kontroll element för konfigurations kontroll (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359085"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Control-element för Controls för Configuration (format)

Definierar en gemensam kontroll som kan användas av alla vyer i format filen och det namn som används för att referera till kontrollen.

Konfigurations element (format) styr element i konfigurations-(format) kontroll element för konfigurations inställningar (format)

## <a name="syntax"></a>Syntax

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för `Control`-elementet. Du måste ange ett av varje underordnat element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomControl-element för kontroll av konfigurations inställningar (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Nödvändigt element.<br /><br /> Definierar kontrollen.|
|[Namn element för kontroll av konfiguration (format)](./name-element-for-control-for-controls-for-configuration-format.md)|Nödvändigt element.<br /><br /> Anger det namn som ska användas för att referera till kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Kontrollerar konfigurations element (format)](./controls-element-for-configuration-format.md)|Definierar de vanliga kontroller som kan användas av alla vyer i formaterings filen eller av andra kontroller.|

## <a name="remarks"></a>Anmärkningar

Det namn som ges till den här kontrollen kan refereras till i följande element:

- [ExpressionBinding-element för CustomItem (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [GroupBy-element för vy (format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Se även

[Kontrollerar konfigurations element (format)](./controls-element-for-configuration-format.md)

[CustomControl-element för kontroll av konfiguration (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[ExpressionBinding-element för CustomItem (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[GroupBy-element för vy (format)](./groupby-element-for-view-format.md)

[Namn element för kontroll för konfiguration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
