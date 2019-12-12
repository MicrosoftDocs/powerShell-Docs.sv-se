---
title: Konfigurations element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354875"
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

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `Configuration`-elementet. Det här elementet måste vara rot elementet för varje fil format och det här elementet måste innehålla minst ett underordnat element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Styr element för konfiguration (format)](./controls-element-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar de gemensamma kontroller som kan användas av alla vyer i formaterings filen.|
|[DefaultSettings-element (format)](./defaultsettings-element-format.md)|Valfritt element.<br /><br /> Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.|
|[SelectionSets element format](./selectionsets-element-format.md)|Valfritt element.<br /><br /> Definierar de gemensamma uppsättningar av .NET-objekt som kan användas av alla vyer i format filen.|
|[ViewDefinitions-element (format)](./viewdefinitions-element-format.md)|Valfritt element.<br /><br /> Definierar de vyer som används för att visa objekt.|

### <a name="parent-elements"></a>Överordnade element

Ingen.

## <a name="remarks"></a>Anmärkningar

Formatering av filer definierar hur objekt visas. I de flesta fall innehåller det här rot elementet ett [ViewDefinitions](./viewdefinitions-element-format.md) -element som definierar tabell, lista och bred vy av format filen. Förutom visnings definitionerna kan format filen definiera vanliga uppsättningar, inställningar och kontroller som dessa vyer kan använda.

## <a name="see-also"></a>Se även

[Styr element för konfiguration (format)](./controls-element-for-configuration-format.md)

[DefaultSettings-element (format)](./defaultsettings-element-format.md)

[SelectionSets-element (format)](./selectionsets-element-format.md)

[ViewDefinitions-element (format)](./viewdefinitions-element-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
