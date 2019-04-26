---
title: 'Formatering: översikt | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065741"
---
# <a name="formatting-file-overview"></a>Översikt över formateringsfiler

Visningsformatet för de objekt som returneras av kommandon (cmdlet: ar, funktioner och skript) definieras med hjälp av formatering (filer format.ps1xml). Flera av de här filerna tillhandahålls av PowerShell för att definiera visningsformat för de objekt som returneras av förutsatt att PowerShell kommandon, till exempel den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objektet som returneras av den `Get-Process` cmdlet. Men du kan också skapa dina egna anpassade formatering filer om du vill skriva över format som standard visas eller du kan skriva en anpassad formatering fil för att definiera visningen av objekten som returneras av dina egna kommandon.

> [!IMPORTANT]
> Formatering filer styr inte den del av ett objekt som returneras till pipelinen. När ett objekt returneras till pipelinen kan är alla medlemmar i objektet tillgängliga även om vissa inte visas.

PowerShell använder data i dessa formatering filer för att avgöra vad som visas och hur data som visas är formaterad. Data som visas kan innehålla egenskaperna för ett objekt eller värdet för ett skript. Skript används om du vill visa ett värde som inte är tillgänglig direkt från egenskaperna för ett objekt, till exempel att lägga till värdet för två egenskaper för ett objekt och sedan visa summan som en typ av data. Formatering av data som visas gör du genom att definiera vyer för de objekt som du vill visa. Du kan definiera en vy för varje objekt, kan du definiera en vy för flera objekt eller du kan definiera flera vyer för samma objekt. Det finns ingen gräns för antal vyer som du kan definiera.

## <a name="common-features-of-formatting-files"></a>Vanliga funktioner av formatering filer

Varje formatering fil kan definiera följande komponenter som kan delas mellan alla vyer som definieras av filen:

- Som standard konfigurationsinställning, till exempel om data som visas i raderna i tabellerna ska visas på nästa rad om data är längre än bredden på kolumnen. Mer information om dessa inställningar finns i [definierar gemensamma konfigurationsinställningar](./defining-common-configuration-features.md).

- Uppsättningar med objekt som kan visas med någon av vyerna i filen formatering. Mer information om dessa uppsättningar (kallas *val av uppsättningar*), se [definiera anger av objekt](./defining-selection-sets.md).

- Vanliga kontroller som kan användas av alla vyer i filen formatering. Kontroller ger mer detaljerad kontroll på hur data visas. Mer information om kontroller finns i [definiera anpassade kontroller](./creating-custom-controls.md).

## <a name="formatting-views"></a>Formatering vyer

Formatering vyer kan visa objekt i ett tabellformat listformat, brett format och anpassat format. För det mesta beskrivs varje formatering definition av en uppsättning XML-taggar som beskriver vyn. Varje vy innehåller namnet på vyn objekt som använder vyn och element i vyn, till exempel kolumn- och information för en tabellvy.

Visa Tabellistor egenskaperna för ett objekt eller ett skript block värde i en eller flera kolumner. Varje kolumn representerar en enskild egenskap för objektet eller ett skriptvärde. Du kan definiera en tabellvy som visar alla egenskaper för ett objekt, en delmängd av egenskaperna för ett objekt eller en kombination av egenskaper och värden för skriptet. Varje rad i tabellen representerar en returnerade objektet. Skapa en tabellvy liknar när du skicka ett objekt för att den `Format-Table` cmdlet. Mer information om den här vyn finns i [tabellvy](./creating-a-table-view.md).

Lista visas egenskaperna för ett objekt eller ett skriptvärde i en enda kolumn. Varje rad i listan visar en valfri etikett eller egenskapens namn följt av värdet för egenskapen eller skript. Skapa en listvy liknar att skicka ett objekt för att den `Format-List` cmdlet. Mer information om den här vyn finns i [listvyn](./creating-a-list-view.md).

Bred vy innehåller en enda egenskap för ett objekt eller ett skriptvärde i en eller flera kolumner. Det finns ingen etikett eller rubrik för den här vyn. Skapa en bred vy liknar att skicka ett objekt för att den `Format-Wide` cmdlet. Mer information om den här vyn finns i [bred vy](./creating-a-wide-view.md).

Anpassad vy visar en anpassningsbar objektegenskaper eller skript värden som inte följer den fasta strukturen för tabellvyer, listvyer eller wide vyer. Du kan definiera en anpassad vy som är fristående eller du kan definiera en anpassad vy som används av en annan vy, till exempel en tabell eller listvy. Skapa en anpassad vy liknar att skicka ett objekt för att den `Format-Custom` cmdlet. Mer information om den här vyn finns i [anpassad vy](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Komponenterna i en vy

I följande XML-exempel visas XML grundkomponenterna i en vy. Enskilda XML-elementen varierar beroende på vilken vy som du vill skapa men grundkomponenterna i vyerna är likadana.

Börja med varje vy har en `Name` element som anger ett användarvänligt namn som används för att referera till vyn. en `ViewSelectedBy` -element som definierar vilka .NET-objekt visas i vyn, och en *kontroll* element som definierar vyn.

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

I control-elementet kan du definiera en eller flera *post* element. Om du använder flera definitioner, måste du ange vilka .NET-objekt använder varje definition. Vanligtvis krävs bara en post med endast en definition för varje kontroll.

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

Inom varje post element i en vy som du anger den *objekt* element som definierar egenskaper för .NET eller skript som visas i vyn.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

I föregående exempel visas formatering filen kan innehålla flera vyer, en vy kan innehålla flera definitioner och varje definition kan innehålla flera objekt.

## <a name="example-of-a-table-view"></a>Exempel på en tabellvy

I följande exempel visar XML-taggar som används för att definiera en tabellvy som innehåller två kolumner. Den [ViewDefinitions](./viewdefinitions-element-format.md) elementet är elementet behållare för alla vyer som definieras i filen formatering. Den [visa](./view-element-format.md) elementet definierar viss tabell, lista, brett eller anpassade vy. Inom varje [visa](./view-element-format.md) element, den [namn](./name-element-for-view-format.md) elementet anger namnet på vyn, den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar de objekt som använder vyn och de olika styra element (till exempel den `TableControl` element som visas i följande exempel) definiera typ av vy.

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

[Skriva ett PowerShell-formatering och typer fil](./writing-a-powershell-formatting-file.md)
