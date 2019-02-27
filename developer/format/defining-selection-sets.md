---
title: Definiera inställningarna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848862"
---
# <a name="defining-selection-sets"></a>Definiera valuppsättningar

När du skapar flera vyer och kontroller, kan du definiera uppsättningar med objekt som refereras som inställningarna. En kan du definiera objekt en gång utan att behöva definiera dem flera gånger för varje vy eller kontroll. Inställningarna används vanligtvis när du har en uppsättning relaterade .NET-objekt. Till exempel den `FileSystem` formatering fil (FileSystem.format.ps1xml) definierar en uppsättning system filtyper som använder flera vyer val.

## <a name="where-selection-sets-are-defined-and-referenced"></a>Var inställningarna finns definierade och refererat

Du definierar inställningarna som en del av de vanliga data som kan användas av alla vyer och kontroller som definieras i filen formatering. I följande exempel visas hur du definierar tre val av uppsättningar.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

Du kan referera till en markering anger på följande sätt:

- Varje vy har en `ViewSelectedBy` element som definierar vilka objekt visas med hjälp av vyn. Den `ViewSelectedBy` elementet har en `SelectionSetName` underordnade elementet som anger markeringen inställt som alla definitioner för att visa. Det finns ingen begränsning för hur många val av uppsättningar som du kan referera till från en vy.

- I varje definitionen för en vy eller en kontroll, den `EntrySelectedBy` elementet definierar vilka objekt visas med hjälp av den definitionen. En vy eller en kontroll har normalt bara en definition så att objekt som definieras av den `ViewSelectedBy` element. Den `EntrySelectedBy` element i definitionen har en `SelectionSetName` underordnat element som definierar vilka val. Om du anger alternativet för en definition, du kan inte ange någon av de andra underordnade elementen i `EntrySelectedBy` element.

- I varje definitionen för en vy eller en kontroll, den `SelectionCondition` element kan användas för att ange ett villkor för när definitionen används. Den `SelectionCondition` elementet har en `SelectionSetName` underordnat element som anger markeringen ange som utlöser villkoret. Villkoret utlöses när någon av de objekt som definierats i uppsättningen markeringen visas. Mer information om hur du anger dessa villkor finns i [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).

## <a name="selection-set-example"></a>Val av Set-exempel

I följande exempel visas en markering uppsättning som tagits direkt från den `FileSystem` formatering fil som tillhandahålls av Windows PowerShell. Mer information om andra Windows PowerShell formatering filer finns i [Windows PowerShell-formatering filer](./powershell-formatting-files.md).

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

Den tidigare val av uppsättningen refereras till i den `ViewSelectedBy` element i en tabellvy.

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a>XML-element

 Det finns ingen gräns för hur många val av uppsättningar som du kan definiera. Följande XML-element används för att skapa en.

- Den [SelectionSets](./selectionsets-element-format.md) elementet definierar uppsättningar med .NET-objekt som refereras av vyer och kontroller av filen formatering.

- Den [SelectionSet](./selectionset-element-format.md) elementet definierar en uppsättning med .NET-objekt.

- Den [namn](./name-element-for-selectionset-format.md) elementet anger namnet som används för att referera till val av uppsättningen.

- Den [typer](./types-element-for-selectionset-format.md) elementet anger vilka .NET-typer av objekt för val av uppsättningen. (Inom formatering filer objekt anges efter typ .NET.)

 Följande XML-element för att ange en.

- Följande element anger valet inställd på att använda i alla definitioner av vyn:

    - [SelectionSetName Element för ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)

    - [SelectionSetName Element för EntrySelectedBy för GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- Följande element ange val av uppsättningen som används av en enda vy-definition:

    - [SelectionSetName Element för EntrySelectedBy för ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [SelectionSetName Element för EntrySelectedBy för TableControl (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionSetName Element för EntrySelectedBy för WideControl (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [SelectionSetName Element för EntrySelectedBy för anpassad kontroll för vy (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- Följande element anger du de val som angivits av gemensamma och visa kontroll definitioner:

    - [SelectionSetName Element för EntrySelectedBy för kontroller för att visa (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [SelectionSetName Element för EntrySelectedBy för kontroller för konfiguration (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- Följande element ange de val som angivits när du definierar vilka objekt att expandera:

    - [SelectionSetName Element för EntrySelectedBy för EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Följande element ange de val som angivits av val av villkor.

    - [SelectionSetName Element för SelectionCondition för kontroller för konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [SelectionSetName Element för SelectionCondition för kontroller för att visa (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [SelectionSetName Element för SelectionCondition för anpassad kontroll för vy (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [SelectionSetName Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [SelectionSetName Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [SelectionSetName Element för SelectionCondition för EntrySelectedBy för TableControl (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionSetName Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [SelectionSetName Element för SelectionCondition för GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Se även

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Namn](./name-element-for-selectionset-format.md)

[Typer](./types-element-for-selectionset-format.md)

[PowerShell-formatering filer](./powershell-formatting-files.md)

[Definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md)

[Skriva ett PowerShell-formatering och typer fil](./writing-a-powershell-formatting-file.md)
