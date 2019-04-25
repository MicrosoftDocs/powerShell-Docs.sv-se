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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066846"
---
# <a name="creating-a-table-view"></a>Skapa en tabellvy

En tabellvy visar data i en eller flera kolumner. Varje rad i tabellen representerar ett .NET-objekt och varje kolumn i tabellen representerar en egenskap för objektet eller ett skriptvärde. Du kan definiera en tabellvy som visar alla egenskaper för ett objekt eller en delmängd av egenskaperna för ett objekt.

## <a name="a-table-view-display"></a>En tabell visa visning

I följande exempel visas hur Windows PowerShell visar den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt som returneras av den [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. För det här objektet Windows PowerShell har definierat en tabellvy som visar den `Status` egenskapen den `Name` egenskapen (den här egenskapen är en egenskap för alias för den `ServiceName` egenskapen), och `DisplayName` egenskapen. Varje rad i tabellen representerar ett objekt som returneras av cmdlet: en.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>Definiera tabellvyn

Följande XML visar Visa tabellschemat för att visa den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt. Du måste ange varje egenskap som du vill ska visas i tabellvyn.

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

- Den [visa](./view-element-format.md) elementet har det överordnade elementet i tabellvyn. (Detta är samma överordnade element lista, bred och anpassade vyer.)

- Den [namn](./name-element-for-view-format.md) elementet anger namnet på vyn. Det här elementet krävs för alla vyer.

- Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar de objekt som använder vyn. Det här elementet krävs.

- Den [GroupBy](./groupby-element-for-view-format.md) (visas inte i det här exemplet)-elementet definierar när en ny grupp med objekt visas. En ny grupp har startats när värdet för en specifik egenskap eller ett skript ändras. Det här elementet är valfritt.

- Den [kontroller](./controls-element-for-view-format.md) (visas inte i det här exemplet)-elementet definierar de anpassade kontroller som definieras av tabellvyn. Kontroller ger dig ett sätt som specificerar hur data visas. Det här elementet är valfritt. En vy kan definiera egna anpassade kontroller eller använda vanliga kontroller som kan användas av alla vyer i filen formatering. Mer information om anpassade kontroller finns i [skapar anpassade kontroller](./creating-custom-controls.md).

- Den [HideTableHeaders](./hidetableheaders-element-format.md) element (inte visas i det här exemplet) anger att tabellen inte visar alla etiketter överst i tabellen. Det här elementet är valfritt.

- Den [TableControl](./tablecontrol-element-format.md) element som definierar informationen som rubrik och raden i tabellen. Precis som alla andra vyer, en tabellvy kan visa värdena för objektegenskaper eller värden som genererats av skript.

## <a name="defining-column-headers"></a>Definiera kolumnrubriker

1. Den [TableHeaders](./tableheaders-element-format.md) elementet och dess underordnade element definierar vad som visas överst i tabellen.

2. Den [TableColumnHeader](./tablecolumnheader-element-format.md) elementet definierar vad som visas överst i en kolumn i tabellen. Ange de här elementen i den ordning som du vill att de rubriker som visas.

   Det finns ingen gräns för hur många av dessa element som du kan använda, men antalet [TableColumnHeader](./tablecolumnheader-element-format.md) element i tabellvyn måste vara lika med antalet [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) element som du använder.

3. Den [etikett](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) elementet anger den text som visas. Det här elementet är valfritt.

4. Den [bredd](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) elementet anger bredden (i antal tecken) för kolumnen. Det här elementet är valfritt.

5. Den [justering](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) elementet anger hur etiketten visas. Etiketten kan justeras till vänster till höger, eller centrerad. Det här elementet är valfritt.

## <a name="defining-the-table-rows"></a>Definiera tabellraderna

Tabellvyer kan ge en eller flera definitioner som anger vilka data som visas i raderna i tabellen med hjälp av de underordnade elementen i den [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element. Observera att du kan ange flera definitioner för raderna i tabellen, men rubrikerna för rader förblir detsamma oavsett vilken raddefinition används. En tabell har vanligtvis bara en definition.

I följande exempel visas vyn ger en enda definition som visar värdena för flera egenskaper för den [System.Diagnostics.Process? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objekt. En tabellvy kan visa värdet för en egenskap eller värdet för ett skript (visas inte i det här exemplet) i sina rader.

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

Följande XML-element kan användas för att ange definitioner för en rad:

- Den [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elementet och dess underordnade element definierar vad som visas i raderna i tabellen.

- Den [TableRowEntry](./listentry-element-for-listcontrol-format.md) elementet innehåller en definition av raden. Minst en [TableRowEntry](./listentry-element-for-listcontrol-format.md) krävs, men det finns ingen högsta gräns för antalet element som du kan lägga till. I de flesta fall har en vy endast en definition.

- Den [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elementet anger de objekt som visas som en viss definition. Det här elementet är valfritt och krävs bara när du definierar flera [TableRowEntry](./listentry-element-for-listcontrol-format.md) element som visar olika objekt.

- Den [omsluta](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) elementet anger att text som överskrider kolumnbredden visas på nästa rad. Som standard trunkeras text som överskrider kolumnbredden.

- Den [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) elementet definierar de egenskaper eller skript som vars värden visas i raden.

- Den [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elementet definierar egenskapen eller skript som vars värde visas i kolumnen i raden. En [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element krävs för varje kolumn i raden. Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.

- Den [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elementet anger egenskapen vars värde visas i raden. Du måste ange en egenskap eller ett skript, men du kan inte ange båda.

- Den [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elementet anger skriptet vars värde visas i raden. Du måste ange ett skript eller en egenskap, men du kan inte ange båda.

- Den [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elementet anger ett formatmönster som definierar hur värdet för egenskapen eller skript visas. Det här elementet är valfritt.

- Den [justering](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) elementet anger hur värdet för egenskapen eller skript visas. Värdet kan justeras till vänster till höger, eller centrerad. Det här elementet är valfritt.

## <a name="defining-the-objects-that-use-the-table-view"></a>Definiera de objekt som använder tabellvyn

Det finns två sätt att definiera vilka .NET-objekt använder tabellvyn. Du kan använda den [ViewSelectedBy](./viewselectedby-element-format.md) element för att definiera de objekt som kan visas av alla definitioner av vyn eller du kan använda den [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element för att definiera vilka objekt visas som en viss definition för vyn. I de flesta fall har endast en definition i en vy så objekt definieras vanligtvis av den [ViewSelectedBy](./viewselectedby-element-format.md) element.

I följande exempel visas hur du definierar de objekt som visas genom att visa tabellen med den [ViewSelectedBy](./viewselectedby-element-format.md) och [TypeName](./typename-element-for-viewselectedby-format.md) element. Det finns ingen gräns för hur många [TypeName](./typename-element-for-viewselectedby-format.md) element att du kan ange och deras inbördes ordning är inte särskilt stor.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Följande XML-element kan användas för att ange objekt som används av tabellvyn:

- Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar vilka objekt visas i listvyn.

- Den [TypeName](./typename-element-for-viewselectedby-format.md) elementet anger .NET-objekt som visas i vyn. Det fullständigt kvalificerade typnamnet .NET krävs. Du måste ange minst en typ eller val som angetts för vyn, men det finns inget högsta antal element som kan anges.

I följande exempel används den [ViewSelectedBy](./viewselectedby-element-format.md) och [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element. Använd val av där du har en uppsättning objekt som visas med flera vyer, till exempel när du definierar en listvy och en tabellvy för samma objekt. Läs mer om hur du skapar en [definiera val av uppsättningar](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Följande XML-element kan användas för att ange objekt som används av listvyn:

- Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar vilka objekt visas i listvyn.

- Den [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementet anger en uppsättning objekt som kan visas i vyn. Du måste ange minst en markering set eller typ för vyn, men det finns inget högsta antal element som kan anges.

I följande exempel visas hur du definierar de objekt som visas av en viss definition av tabellen vy med den [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element. Med det här elementet kan ange du namnet på .NET objektet, val av flera objekt eller ett val av villkor som anger när definitionen används. Mer information om hur du skapar ett urval villkor finns i [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> När du skapar flera definitioner av tabellvyn kan du inte ange olika kolumnrubriker. Du kan ange bara vad som visas på raderna i tabellen, till exempel vilka objekt visas.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

Följande XML-element kan användas för att ange objekt som används av en viss definition av listvyn:

- Den [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elementet definierar vilka objekt visas i definitionen.

- Den [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elementet anger .NET-objekt som visas när definitionen. När du använder det här elementet krävs det fullständigt kvalificerade typnamnet för .NET. Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.

- Den [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (visas inte) anger en uppsättning objekt som kan visas av denna definition. Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.

- Den [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (visas inte) anger ett villkor som måste finnas för den här definitionen som ska användas. Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges. Läs mer om hur du definierar villkoren för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>Med hjälp av formatsträngar

Formatering strängar kan läggas till en vy för att ytterligare definiera hur data visas. I följande exempel visas hur du definierar en formateringssträngen för värdet för den `StartTime` egenskapen.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

Följande XML-element kan användas för att ange ett:

- Den [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elementet definierar egenskapen eller skript som vars värde visas i kolumnen i raden. En [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element krävs för varje kolumn i raden. Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.

- Den [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elementet anger egenskapen vars värde visas i raden. Du måste ange en egenskap eller ett skript, men du kan inte ange båda.

- Den [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elementet anger ett formatmönster som definierar hur värdet för egenskapen eller skript visas.

I följande exempel visas den `ToString` metoden anropas för att formatera värdet för skriptet. Skript kan anropa någon-metod för ett objekt. Därför, om ett objekt har en metod som `ToString`, som har formateringsparametrar, skriptet kan anropa metoden för att formatera utdatavärdet för skriptet.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Följande XML-element som kan användas för att anropa den `ToString` metoden:

- Den [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elementet definierar egenskapen eller skript som vars värde visas i kolumnen i raden. En [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element krävs för varje kolumn i raden. Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.

- Den [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elementet anger skriptet vars värde visas i raden. Du måste ange ett skript eller en egenskap, men du kan inte ange båda.

## <a name="see-also"></a>Se även

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
