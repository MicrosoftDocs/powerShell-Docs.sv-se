---
title: Konfigurationselementet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847042"
---
# <a name="configuration-element-format"></a>Configuration-element (format)

Representerar det översta elementet i en formatering fil.

Konfigurationselement

## <a name="syntax"></a>Syntax

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Configuration` element. Det här elementet måste vara rotelementet för varje formatering fil och det här elementet måste innehålla minst ett underordnat element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Kontroller Element för konfiguration (Format)](./controls-element-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar de vanliga kontroller som kan användas av alla vyer i filen formatering.|
|[DefaultSettings Element (Format)](./defaultsettings-element-format.md)|Valfritt element.<br /><br /> Definierar gemensamma inställningar som gäller för alla vyer i filen formatering.|
|[SelectionSets Element Format](./selectionsets-element-format.md)|Valfritt element.<br /><br /> Definierar gemensamma uppsättningar med .NET-objekt som kan användas av alla vyer i filen formatering.|
|[ViewDefinitions Element (Format)](./viewdefinitions-element-format.md)|Valfritt element.<br /><br /> Definierar de vyer som används för att visa objekt.|

### <a name="parent-elements"></a>Överordnade element

Ingen.

## <a name="remarks"></a>Anmärkningar

Formateras definierar hur objekt visas. I de flesta fall är detta rotelement innehåller en [ViewDefinitions](./viewdefinitions-element-format.md) -element som definierar den tabell, lista och många vyer i filen formatering. Förutom att visa-definitioner kan filen formatering definiera vanliga val av uppsättningar, inställningar och kontroller som kan använda för dessa vyer.

## <a name="see-also"></a>Se även

[Kontroller Element för konfiguration (Format)](./controls-element-for-configuration-format.md)

[DefaultSettings Element (Format)](./defaultsettings-element-format.md)

[SelectionSets Element (Format)](./selectionsets-element-format.md)

[ViewDefinitions Element (Format)](./viewdefinitions-element-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
