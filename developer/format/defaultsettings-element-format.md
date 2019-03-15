---
title: DefaultSettings Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: 59cc0514087cc52438e0d1271b8b77a7799eb32c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846580"
---
# <a name="defaultsettings-element-format"></a>DefaultSettings-element (format)

Definierar gemensamma inställningar som gäller för alla vyer i filen formatering. Vanliga inställningar inkluderar visar fel, radbrytning i tabeller, definiera hur samlingar har expanderats och mycket annat.

Konfigurationselementet Element (Format) DefaultSettings (Format)

## <a name="syntax"></a>Syntax

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `DefaultSettings` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[DisplayError Element (Frmat)](./displayerror-element-format.md)|Valfritt element.<br /><br /> Anger att strängen #ERR visas när ett fel uppstår medan du visar en typ av data.|
|[EnumerableExpansions Element (Format)](./enumerableexpansions-element-format.md)|Valfritt element.<br /><br /> Definierar hur .NET objekt visas när de visas i vyn.|
|[PropertyCountForTable (Format)](./propertycountfortable-element-format.md)|Valfritt element.<br /><br /> Anger det minsta antalet egenskaper som ett objekt måste ha för att visa objektet i en tabellvy.|
|[ShowError-Element (Format)](./showerror-element-format.md)|Valfritt element.<br /><br /> Anger att en fullständig Felpost visas när ett fel uppstår medan du visar en typ av data.|
|[WrapTables Element (Format)](./wraptables-element-format.md)|Valfritt element.<br /><br /> Anger att data i en tabell har flyttats till nästa rad om det inte passar i bredden på kolumnen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Konfigurationselement](./configuration-element-format.md)|Representerar det översta elementet i en formatering fil.|

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[Konfigurationselement](./configuration-element-format.md)

[DisplayError Element (Frmat)](./displayerror-element-format.md)

[EnumerableExpansions Element (Format)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (Format)](./propertycountfortable-element-format.md)

[ShowError-Element (Format)](./showerror-element-format.md)

[WrapTables Element (Format)](./wraptables-element-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)