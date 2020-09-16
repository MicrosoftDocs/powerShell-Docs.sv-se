---
title: Elementet TypeName för SelectionCondition för kontroller för konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2db856d1b84dded315204d8c8574ae86acb63515
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780074"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a>TypeName-element för SelectionCondition för Controls för Configuration (format)

Anger en .NET-typ som utlöser villkoret. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för kontroll för CustomControl-element (format) för Control för Configuration (format) CustomEntries-element för CustomControl för Controls (format) CustomEntry-element för CustomControl for Controls for Configuration (format) EntrySelectedBy-elementet för CustomEntry for Controls for Configuration (format) SelectionCondition element for EntrySelectedBy for CustomEntry for Configuration (format) elementet TypeName for SelectionCondition for Controls for Configuration (format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition-element för EntrySelectedBy för CustomEntry för konfiguration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.|

## <a name="text-value"></a>Textvärde

Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..

## <a name="remarks"></a>Kommentarer

## <a name="see-also"></a>Se även

[SelectionCondition-element för EntrySelectedBy för CustomEntry för konfiguration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
