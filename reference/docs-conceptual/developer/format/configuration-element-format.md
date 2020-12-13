---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration-element (format)
description: Configuration-element (format)
ms.openlocfilehash: 0524736d40dd7a7acb0b6fb61d1438b75672c240
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655697"
---
# <a name="configuration-element-format"></a>Configuration-element (format)

Representerar det översta elementet i en textfil.

Konfigurations element

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

I följande avsnitt beskrivs attributen, underordnade element och `Configuration` elementets överordnade element. Det här elementet måste vara rot elementet för varje fil format och det här elementet måste innehålla minst ett underordnat element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Controls-element för Configuration (format)](./controls-element-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar de gemensamma kontroller som kan användas av alla vyer i formaterings filen.|
|[DefaultSettings-element (format)](./defaultsettings-element-format.md)|Valfritt element.<br /><br /> Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.|
|[SelectionSets element format](./selectionsets-element-format.md)|Valfritt element.<br /><br /> Definierar de gemensamma uppsättningar av .NET-objekt som kan användas av alla vyer i format filen.|
|[ViewDefinitions-element (format)](./viewdefinitions-element-format.md)|Valfritt element.<br /><br /> Definierar de vyer som används för att visa objekt.|

### <a name="parent-elements"></a>Överordnade element

Inga.

## <a name="remarks"></a>Kommentarer

Formatering av filer definierar hur objekt visas. I de flesta fall innehåller det här rot elementet ett [ViewDefinitions](./viewdefinitions-element-format.md) -element som definierar tabell, lista och bred vy av format filen. Förutom visnings definitionerna kan format filen definiera vanliga uppsättningar, inställningar och kontroller som dessa vyer kan använda.

## <a name="see-also"></a>Se även

[Controls-element för Configuration (format)](./controls-element-for-configuration-format.md)

[DefaultSettings-element (format)](./defaultsettings-element-format.md)

[SelectionSets-element (format)](./selectionsets-element-format.md)

[ViewDefinitions-element (format)](./viewdefinitions-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
