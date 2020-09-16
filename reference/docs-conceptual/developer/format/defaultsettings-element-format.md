---
title: DefaultSettings-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7da7948fc0814e38a8f3910596e223470ec27d75
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787741"
---
# <a name="defaultsettings-element-format"></a>DefaultSettings-element (format)

Definierar vanliga inställningar som gäller för alla vyer i formaterings filen. Vanliga inställningar är att visa fel, figursätta text i tabeller, definiera hur samlingar expanderas och mycket mer.

Konfigurations element (format) DefaultSettings-element (format)

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

I följande avsnitt beskrivs attribut, underordnade element och `DefaultSettings` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[DisplayError-element (format)](./displayerror-element-format.md)|Valfritt element.<br /><br /> Anger att strängen #ERR visas när ett fel inträffar när en del av data visas.|
|[EnumerableExpansions-element (format)](./enumerableexpansions-element-format.md)|Valfritt element.<br /><br /> Definierar de olika sätt som .NET-objekt expanderas när de visas i en vy.|
|[PropertyCountForTable (format)](./propertycountfortable-element-format.md)|Valfritt element.<br /><br /> Anger det minsta antalet egenskaper som ett objekt måste ha för att visa objektet i en tabellvy.|
|[ShowError-element (format)](./showerror-element-format.md)|Valfritt element.<br /><br /> Anger att den fullständiga fel posten visas när ett fel inträffar när en del av data visas.|
|[WrapTables-element (format)](./wraptables-element-format.md)|Valfritt element.<br /><br /> Anger att data i en tabell flyttas till nästa rad om den inte passar in i kolumnens bredd.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Konfigurations element](./configuration-element-format.md)|Representerar det översta elementet i en textfil.|

## <a name="remarks"></a>Kommentarer

## <a name="see-also"></a>Se även

[Konfigurations element](./configuration-element-format.md)

[DisplayError-element (format)](./displayerror-element-format.md)

[EnumerableExpansions-element (format)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (format)](./propertycountfortable-element-format.md)

[ShowError-element (format)](./showerror-element-format.md)

[WrapTables-element (format)](./wraptables-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
