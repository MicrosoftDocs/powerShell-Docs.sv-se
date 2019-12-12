---
title: DefaultSettings-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355134"
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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `DefaultSettings`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

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

## <a name="remarks"></a>Anmärkningar

## <a name="see-also"></a>Se även

[Konfigurations element](./configuration-element-format.md)

[DisplayError-element (format)](./displayerror-element-format.md)

[EnumerableExpansions-element (format)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (format)](./propertycountfortable-element-format.md)

[ShowError-element (format)](./showerror-element-format.md)

[WrapTables-element (format)](./wraptables-element-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
