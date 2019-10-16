---
title: Definiera urvals uppsättningar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359011"
---
# <a name="defining-selection-sets"></a>Definiera valuppsättningar

När du skapar flera vyer och kontroller kan du definiera uppsättningar av objekt som kallas urvals uppsättningar. Med en urvals uppsättning kan du definiera objekten en gång, utan att behöva definiera dem flera gånger för varje vy eller kontroll. Normalt används urvals uppsättningar när du har en uppsättning relaterade .NET-objekt. Till exempel definierar `FileSystem`-format filen (FileSystem. format. ps1xml) en urvals uppsättning av de fil system typer som flera vyer använder.

## <a name="where-selection-sets-are-defined-and-referenced"></a>Där urvals uppsättningar definieras och refereras till

Du definierar urvals uppsättningar som en del av vanliga data som kan användas av alla vyer och kontroller som definierats i format filen. I följande exempel visas hur du definierar tre urvals uppsättningar.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

Du kan referera till en urvals uppsättning på följande sätt:

- Varje vy har ett `ViewSelectedBy`-element som definierar vilka objekt som visas med hjälp av vyn. Elementet `ViewSelectedBy` har ett underordnat `SelectionSetName`-element som anger den markerings uppsättning som alla definitioner för vyn använder. Det finns ingen begränsning för antalet markerings uppsättningar som du kan referera till från en vy.

- I varje definition av en vy eller kontroll definierar elementet `EntrySelectedBy` vilka objekt som visas genom att använda den definitionen. Normalt har en vy eller kontroll bara en definition så objekten definieras av `ViewSelectedBy`-elementet. Elementet `EntrySelectedBy` i definitionen har ett underordnat `SelectionSetName`-element som anger urvals uppsättningen. Om du anger urvals uppsättningen för en definition kan du inte ange något av de andra underordnade elementen för elementet `EntrySelectedBy`.

- I varje definition av en vy eller kontroll kan `SelectionCondition`-elementet användas för att ange ett villkor för när definitionen används. Elementet `SelectionCondition` har ett underordnat `SelectionSetName`-element som anger den urvals uppsättning som utlöser villkoret. Villkoret utlöses när något av de objekt som definieras i urvals uppsättningen visas. Mer information om hur du anger dessa villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).

## <a name="selection-set-example"></a>Exempel på urvals uppsättning

I följande exempel visas en urvals uppsättning som tas direkt från filen med `FileSystem`-formatering som tillhandahålls av Windows PowerShell. Mer information om andra Windows PowerShell-filer finns i [filer för Windows PowerShell-formatering](./powershell-formatting-files.md).

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

Den tidigare urvals uppsättningen refereras till i `ViewSelectedBy`-elementet i en tabellvy.

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

 Det finns ingen gräns för antalet markerings uppsättningar som du kan definiera. Följande XML-element används för att skapa en urvals uppsättning.

- [SelectionSets](./selectionsets-element-format.md) -elementet definierar de uppsättningar av .net-objekt som refereras till i vyernas vyer och kontroller.

- [SelectionSet](./selectionset-element-format.md) -elementet definierar en enda uppsättning .net-objekt.

- Elementet [Name](./name-element-for-selectionset-format.md) anger namnet som används för att referera till urvals uppsättningen.

- Elementet [types](./types-element-for-selectionset-format.md) anger .net-typerna för objekt i urvals uppsättningen. (I formateringsattribut anges objekt av deras .NET-typ.)

 Följande XML-element används för att ange en urvals uppsättning.

- Följande element anger den urvals uppsättning som ska användas i alla definitioner för vyn:

    - [SelectionSetName-element för ViewSelectedBy (format)](./selectionsetname-element-for-viewselectedby-format.md)

    - [SelectionSetName-element för EntrySelectedBy för GroupBy (format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- Följande element anger den urvals uppsättning som används av en enda View-definition:

    - [SelectionSetName-element för EntrySelectedBy för ListControl (format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [SelectionSetName-element för EntrySelectedBy för TableControl (format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionSetName-element för EntrySelectedBy för WideControl (format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [SelectionSetName-element för EntrySelectedBy för CustomControl för View (format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- Följande element anger den urvals uppsättning som används av vanliga och Visa kontroll definitioner:

    - [SelectionSetName-element för EntrySelectedBy för kontroller för vy (format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [SelectionSetName-element för EntrySelectedBy för kontroller för konfiguration (format)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- Följande element anger den urvals uppsättning som används när du definierar vilket objekt som ska expanderas:

    - [SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Följande element anger den urvals uppsättning som används av urvals villkor.

    - [SelectionSetName-element för SelectionCondition för kontroller för konfiguration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [SelectionSetName-element för SelectionCondition för kontroller för vy (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [SelectionSetName-element för SelectionCondition för CustomControl för View (format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableControl (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [SelectionSetName-element för SelectionCondition för GroupBy (format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Se även

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Namn](./name-element-for-selectionset-format.md)

[Nodtyper](./types-element-for-selectionset-format.md)

[Filer för PowerShell-formatering](./powershell-formatting-files.md)

[Definiera villkor för när data visas](./defining-conditions-for-displaying-data.md)

[Skriva en PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
