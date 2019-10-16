---
title: Skapa en tabellvy | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354812"
---
# <a name="creating-a-table-view"></a>Skapa en tabellvy

I en tabellvy visas data i en eller flera kolumner. Varje rad i tabellen representerar ett .NET-objekt och varje kolumn i tabellen representerar en egenskap för objektet eller ett skript värde. Du kan definiera en tabellvy som visar alla egenskaper för ett objekt eller en delmängd av egenskaperna för ett objekt.

## <a name="a-table-view-display"></a>Visa en tabellvy

I följande exempel visas hur Windows PowerShell visar objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) som returneras av cmdleten [Get-service](/powershell/module/microsoft.powershell.management/get-service) . För det här objektet har Windows PowerShell definierat en tabellvy som visar egenskapen `Status`, egenskapen `Name` (den här egenskapen är en alias-egenskap för egenskapen `ServiceName`) och egenskapen `DisplayName`. Varje rad i tabellen representerar ett objekt som returneras av cmdleten.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>Definiera tabellvy

Följande XML visar schemat för tabellvy för att visa [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt. Du måste ange varje egenskap som du vill ska visas i vyn tabell.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

Följande XML-element används för att definiera en listvy:

- Elementet [View](./view-element-format.md) är det överordnade elementet i vyn tabell. (Detta är samma överordnade element för vyerna lista, bred och anpassad.)

- Elementet [Name](./name-element-for-view-format.md) anger namnet på vyn. Det här elementet krävs för alla vyer.

- [ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar de objekt som använder vyn. Det här elementet är obligatoriskt.

- Elementet [groupby](./groupby-element-for-view-format.md) (visas inte i det här exemplet) definierar när en ny grupp av objekt visas. En ny grupp startas när värdet för en speciell egenskap eller skript ändras. Det här elementet är valfritt.

- Elementet [Controls](./controls-element-for-view-format.md) (visas inte i det här exemplet) definierar de anpassade kontroller som definieras av tabellvy. Kontrollerna ger dig ett sätt att ytterligare ange hur data ska visas. Det här elementet är valfritt. En vy kan definiera egna anpassade kontroller, eller så kan den använda vanliga kontroller som kan användas av vilken vy som helst i format filen. Mer information om anpassade kontroller finns i [skapa anpassade kontroller](./creating-custom-controls.md).

- [HideTableHeaders](./hidetableheaders-element-format.md) -elementet (visas inte i det här exemplet) anger att tabellen inte kommer att visa några etiketter överst i tabellen. Det här elementet är valfritt.

- Det [TableControl](./tablecontrol-element-format.md) -element som definierar tabellens rubrik och rad information. I likhet med alla andra vyer kan en tabellvy Visa värdena för objekt egenskaper eller värden som genereras av skript.

## <a name="defining-column-headers"></a>Definiera kolumn rubriker

1. [TableHeaders](./tableheaders-element-format.md) -elementet och dess underordnade element definierar vad som visas överst i tabellen.

2. [TableColumnHeader](./tablecolumnheader-element-format.md) -elementet definierar vad som visas överst i en kolumn i tabellen. Ange dessa element i den ordning som du vill att rubrikerna ska visas.

   Det finns ingen gräns för hur många element du kan använda, men antalet [TableColumnHeader](./tablecolumnheader-element-format.md) -element i din tabellvy måste vara lika med antalet [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) -element som du använder.

3. Elementet [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) anger texten som visas. Det här elementet är valfritt.

4. Elementet [width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) anger bredden (i tecken) för kolumnen. Det här elementet är valfritt.

5. Elementet [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) anger hur etiketten visas. Etiketten kan justeras till vänster, till höger eller centrerad. Det här elementet är valfritt.

## <a name="defining-the-table-rows"></a>Definiera tabell rader

Tabellvyer kan tillhandahålla en eller flera definitioner som anger vilka data som visas i raderna i tabellen med hjälp av de underordnade elementen i [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) -elementet. Observera att du kan ange flera definitioner för raderna i tabellen, men rubrikerna för raderna förblir desamma, oavsett vilken rad definition som används. Normalt har en tabell bara en definition.

I följande exempel tillhandahåller vyn en enda definition som visar värdena för flera egenskaper för [system. Diagnostics. process? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) -objekt. En tabellvy kan visa värdet för en egenskap eller värdet för ett skript (visas inte i exemplet) i dess rader.

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

Följande XML-element kan användas för att tillhandahålla definitioner för en rad:

- [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) -elementet och dess underordnade element definierar vad som visas i tabellens rader.

- [TableRowEntry](./listentry-element-for-listcontrol-format.md) -elementet tillhandahåller en definition av raden. Minst en [TableRowEntry](./listentry-element-for-listcontrol-format.md) krävs. Det finns dock ingen övre gräns för antalet element som du kan lägga till. I de flesta fall har en vy bara en definition.

- [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -elementet anger de objekt som visas av en bestämd definition. Det här elementet är valfritt och behövs bara när du definierar flera [TableRowEntry](./listentry-element-for-listcontrol-format.md) -element som visar olika objekt.

- Elementet [wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) anger att text som överskrider kolumn bredden visas på nästa rad. Som standard är text som överskrider kolumn bredden trunkerad.

- [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) -elementet definierar de egenskaper eller skript vars värden visas på raden.

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -elementet definierar egenskapen eller skriptet vars värde visas i kolumnen i raden. Ett [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element krävs för varje kolumn i raden. Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.

- Elementet [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) anger den egenskap vars värde visas i raden. Du måste ange antingen en egenskap eller ett skript, men du kan inte ange båda.

- [Script block](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) -elementet anger det skript vars värde visas i raden. Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.

- [FormatString](./label-element-for-listitem-for-listcontrol-format.md) -elementet anger ett format mönster som definierar hur egenskapen eller skriptets värde visas. Det här elementet är valfritt.

- Elementet [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) anger hur värdet för egenskapen eller skriptet visas. Värdet kan justeras till vänster, till höger eller centreras. Det här elementet är valfritt.

## <a name="defining-the-objects-that-use-the-table-view"></a>Definiera de objekt som använder vyn tabellvy

Det finns två sätt att definiera vilka .NET-objekt som använder vyn tabellvy. Du kan använda [ViewSelectedBy](./viewselectedby-element-format.md) -elementet för att definiera de objekt som kan visas av alla definitioner i vyn, eller så kan du använda elementet [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) för att definiera vilka objekt som visas med en bestämd definition av vyn. I de flesta fall har en vy bara en definition, så objekt definieras vanligt vis av [ViewSelectedBy](./viewselectedby-element-format.md) -elementet.

I följande exempel visas hur du definierar de objekt som visas i vyn tabell med hjälp av elementen [ViewSelectedBy](./viewselectedby-element-format.md) och [TypeName](./typename-element-for-viewselectedby-format.md) . Det finns ingen gräns för antalet element i [TypeName](./typename-element-for-viewselectedby-format.md) som du kan ange, och deras ordning är inte signifikant.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Följande XML-element kan användas för att ange de objekt som används i vyn tabellvy:

- [ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar vilka objekt som visas i list visningen.

- Elementet [TypeName](./typename-element-for-viewselectedby-format.md) anger det .net-objekt som visas i vyn. Fullständigt kvalificerat .NET-typnamn måste anges. Du måste ange minst en typ eller urvals uppsättning för vyn, men det finns inget maximalt antal element som kan anges.

I följande exempel används elementen [ViewSelectedBy](./viewselectedby-element-format.md) och [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) . Använd markerings uppsättningar där du har en relaterad uppsättning objekt som visas med flera vyer, till exempel när du definierar en listvy och en tabellvy för samma objekt. Mer information om hur du skapar en urvals uppsättning finns i [definiera urvals uppsättningar](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Följande XML-element kan användas för att ange de objekt som används av list visningen:

- [ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar vilka objekt som visas i list visningen.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -elementet anger en uppsättning objekt som kan visas i vyn. Du måste ange minst en markerings uppsättning eller typ för vyn, men det finns inget maximalt antal element som kan anges.

I följande exempel visas hur du definierar de objekt som visas av en bestämd definition i vyn tabell med hjälp av [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -elementet. Med det här elementet kan du ange objektets .NET-typnamn, en urvals uppsättning objekt eller ett markerings villkor som anger när definitionen används. Mer information om hur du skapar ett urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> När du skapar flera definitioner av tabellvy kan du inte ange olika kolumn rubriker. Du kan bara ange vad som visas i raderna i tabellen, till exempel vilka objekt som visas.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

Följande XML-element kan användas för att ange de objekt som används av en bestämd definition av listvyn:

- [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -elementet definierar vilka objekt som visas av definitionen.

- Elementet [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) anger det .net-objekt som visas av definitionen. När du använder det här elementet krävs det fullständigt kvalificerade .NET-typ namnet. Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) -elementet (visas inte) anger en uppsättning objekt som kan visas av den här definitionen. Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) -elementet (visas inte) anger ett villkor som måste finnas för att den här definitionen ska kunna användas. Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges. Mer information om hur du definierar urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>Använda format strängar

Du kan lägga till format strängar i en vy för att ytterligare definiera hur data visas. I följande exempel visas hur du definierar en format sträng för värdet för egenskapen `StartTime`.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

Följande XML-element kan användas för att ange ett format mönster:

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -elementet definierar egenskapen eller skriptet vars värde visas i kolumnen i raden. Ett [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element krävs för varje kolumn i raden. Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.

- Elementet [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) anger den egenskap vars värde visas i raden. Du måste ange antingen en egenskap eller ett skript, men du kan inte ange båda.

- [FormatString](./label-element-for-listitem-for-listcontrol-format.md) -elementet anger ett format mönster som definierar hur egenskapen eller skriptets värde visas.

I följande exempel kallas metoden `ToString` för att formatera värdet för skriptet. Skript kan anropa vilken metod som helst av ett objekt. Det innebär att om ett objekt har en metod, till exempel `ToString`, som har formateringsegenskaper, kan skriptet anropa metoden för att formatera utdata för skriptet.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Följande XML-element kan användas för att anropa metoden `ToString`:

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -elementet definierar egenskapen eller skriptet vars värde visas i kolumnen i raden. Ett [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element krävs för varje kolumn i raden. Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.

- [Script block](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) -elementet anger det skript vars värde visas i raden. Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.

## <a name="see-also"></a>Se även

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
