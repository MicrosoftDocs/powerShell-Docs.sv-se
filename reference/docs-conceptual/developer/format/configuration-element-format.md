---
title: Konfigurations element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 90be02f8e27c0bd391e01da1a08ecd8eeb29b84c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783848"
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
