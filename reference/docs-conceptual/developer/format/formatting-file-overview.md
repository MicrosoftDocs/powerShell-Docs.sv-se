---
title: Formaterar fil översikt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355008"
---
# <a name="formatting-file-overview"></a>Översikt över formateringsfiler

Visnings formatet för de objekt som returneras av kommandon (cmdlets, Functions och scripts) definieras med hjälp av formateringsattribut (format. ps1xml-filer). Flera av de här filerna tillhandahålls av PowerShell för att definiera visnings formatet för de objekt som returneras av PowerShell-kommandon, till exempel [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet som returnerades av `Get-Process`-cmdleten. Men du kan också skapa egna filer för att skriva över standardformat, eller så kan du skriva en anpassad formatering för att definiera visningen av objekt som returneras av dina egna kommandon.

> [!IMPORTANT]
> Filer formateras inte med de element som returneras till pipelinen. När ett objekt returneras till pipelinen är alla medlemmar i objektet tillgängliga även om några inte visas.

PowerShell använder data i dessa filer för att avgöra vad som visas och hur de data som visas är formaterade. De data som visas kan innehålla egenskaperna för ett objekt eller ett skripts värde. Skript används om du vill visa ett värde som inte är tillgängligt direkt från egenskaperna för ett objekt, t. ex. genom att lägga till värdet för två egenskaper för ett objekt och sedan Visa summan som en del av data. Formatering av visade data görs genom att definiera vyer för de objekt som du vill visa. Du kan definiera en enskild vy för varje objekt, du kan definiera en enskild vy för flera objekt, eller så kan du definiera flera vyer för samma objekt. Det finns ingen gräns för hur många vyer du kan definiera.

## <a name="common-features-of-formatting-files"></a>Vanliga funktioner i att formatera filer

Varje fil format kan definiera följande komponenter som kan delas över alla vyer som definieras av filen:

- Standard konfigurations inställning, till exempel om data som visas i rader med tabeller ska visas på nästa rad, om data är längre än kolumnens bredd. Mer information om de här inställningarna finns i [definiera vanliga konfigurations inställningar](./defining-common-configuration-features.md).

- Objekt uppsättningar som kan visas av alla vyer i format filen. Mer information om dessa uppsättningar (kallas *urvals uppsättningar*) finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).

- Vanliga kontroller som kan användas av alla vyer i format filen. Kontrollerna ger dig bättre kontroll över hur data visas. Mer information om kontroller finns i [definiera anpassade kontroller](./creating-custom-controls.md).

## <a name="formatting-views"></a>Formatera vyer

Vyer för formatering kan visa objekt i tabell format, list format, brett format och anpassat format. För det mesta beskrivs varje format definition av en uppsättning XML-taggar som beskriver vyn. Varje vy innehåller namnet på vyn, de objekt som använder vyn och elementen i vyn, till exempel kolumn-och rad information för en tabellvy.

I Tabellvy visas egenskaperna för ett objekt eller ett skript Blocks värde i en eller flera kolumner. Varje kolumn representerar en enskild egenskap hos objektet eller ett skript värde. Du kan definiera en tabellvy som visar alla egenskaper för ett objekt, en delmängd av egenskaperna för ett objekt eller en kombination av egenskaper och skript värden. Varje rad i tabellen representerar ett returnerat objekt. Att skapa en tabellvy liknar när du rör ett objekt till `Format-Table`-cmdleten. Mer information om den här vyn finns i [tabellvy](./creating-a-table-view.md).

Listvy visar egenskaperna för ett objekt eller ett skript värde i en kolumn. Varje rad i listan visar en valfri etikett eller egenskaps namnet följt av värdet för egenskapen eller skriptet. Att skapa en listvy är mycket likt att skicka ett objekt till `Format-List`-cmdlet. Mer information om den här vyn finns i [listvyn](./creating-a-list-view.md).

Wide View visar en enskild egenskap för ett objekt eller ett skript värde i en eller flera kolumner. Det finns ingen etikett eller rubrik för den här vyn. Att skapa en bred vy liknar att skicka ett objekt till `Format-Wide`-cmdlet. Mer information om den här vyn finns i [wide View](./creating-a-wide-view.md).

Anpassad vy visar en anpassningsbar vy av objekt egenskaper eller skript värden som inte följer den stela strukturen i tabellvyer, listvyer eller breda vyer. Du kan definiera en fristående anpassad vy eller definiera en anpassad vy som används av en annan vy, till exempel en tabellvy eller listvy. Att skapa en anpassad vy är mycket likt att skicka ett objekt till `Format-Custom`-cmdlet. Mer information om den här vyn finns i [anpassad vy](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Komponenter i en vy

I följande XML-exempel visas de grundläggande XML-komponenterna i en vy. De enskilda XML-elementen varierar beroende på vilken vy du vill skapa, men de grundläggande komponenterna i vyerna är samma.

För att börja med, har varje vy ett `Name`-element som anger ett eget användarvänligt namn som används för att referera till vyn. ett `ViewSelectedBy`-element som definierar vilka .NET-objekt som visas i vyn och ett *kontroll* element som definierar vyn.

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

I kontroll elementet kan du definiera ett eller flera *post* element. Om du använder flera definitioner måste du ange vilka .NET-objekt som ska använda varje definition. Vanligt vis behövs bara en post, med bara en definition, för varje kontroll.

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

I varje post element i en vy anger du de *objekts* element som definierar de .net-egenskaper eller skript som visas i den vyn.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Som du ser i föregående exempel kan format filen innehålla flera vyer, en vy kan innehålla flera definitioner och varje definition kan innehålla flera objekt.

## <a name="example-of-a-table-view"></a>Exempel på en tabellvy

I följande exempel visas de XML-taggar som används för att definiera en tabellvy som innehåller två kolumner. [ViewDefinitions](./viewdefinitions-element-format.md) -elementet är behållar elementet för alla vyer som definierats i format filen. Elementet [View](./view-element-format.md) definierar den aktuella vyn för tabeller, listor, bred eller anpassad. I varje [View](./view-element-format.md) -element anger elementet [Name](./name-element-for-view-format.md) namnet på vyn, [ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar de objekt som använder vyn och de olika kontroll elementen (till exempel elementet `TableControl` som visas i följande exempel) definiera typ av vy.

```xml
<ViewDefinitions>
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[Skapa en tabellvy](./creating-a-table-view.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Skapa anpassade kontroller](./creating-custom-controls.md)

[Skriva en PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
