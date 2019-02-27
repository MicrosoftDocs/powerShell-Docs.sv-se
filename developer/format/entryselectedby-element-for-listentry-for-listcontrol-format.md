---
title: EntrySelectedBy Element för ListEntry för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 723619e67612b859d0acbab37eecd82141adf923
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846076"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>EntrySelectedBy-element för ListEntry för ListControl (format)

Definierar vilka typer av .NET som använder den här listan vydefinitionen eller villkor som måste finnas för den här definitionen som ska användas. I de flesta fall behövs bara en definition för en listvy. Du kan ange flera definitioner för listvyn om du vill använda samma listvyn för att visa olika data för olika objekt.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för ListControl (Format) ListEntry elementet för ListEntry för ListControl (Format) EntrySelectedBy elementet för ListEntry för ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EntrySelectedBy` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[SelectionCondition Element för EntrySelectedBy för ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Valfritt element.<br /><br /> Definierar de villkor som måste finnas för den här listan vydefinitionen som ska användas.|
|[SelectionSetName Element för EnrtySelectedBy för ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger en uppsättning med .NET-typer som använder den här listan vydefinitionen.|
|[TypeName-Element för EntrySelectedBy för ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger ett .NET-typ som använder den här listan vydefinitionen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListEntry Element för ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Definierar hur raderna i listan visas.|

## <a name="remarks"></a>Anmärkningar

Du måste ange minst en typ, val av set eller urvalsvillkoret för en lista över vydefinitionen. Det finns ingen högsta gräns för antalet underordnade element som du kan använda.

Val av villkor används för att definiera ett villkor som måste finnas för definitionen som ska användas, till exempel när ett objekt har en specifik egenskap eller som en specifik egenskapsvärde eller ett skript som utvärderas till `true`. Mer information om val av villkor finns i [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).

Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du definierar objekt för en listvy med hjälp av sina .NET-typnamn.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Se även

[ListEntry Element för ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[SelectionCondition Element för EntrySelectedBy för ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[SelectionSetName Element för EnrtySelectedBy för ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[TypeName-Element för EntrySelectedBy för ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Skapa en listvy](./creating-a-list-view.md)

[Definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
