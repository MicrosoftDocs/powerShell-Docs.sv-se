---
title: Anpassad formatering filer | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850038"
---
# <a name="custom-formatting-files"></a>Anpassade formateringsfiler

Visningsformatet för objekten som returneras av cmdlet: ar, funktioner och skript definieras med hjälp av formatering (filer format.ps1xml). Flera av de här filerna tillhandahålls av Windows PowerShell för att definiera visningsformat standard för de objekt som returneras av Windows PowerShell-cmdlets. Du kan också skapa dina egna anpassade formatering filer att skriva över format som standard visas eller för att definiera visningen av objekten som returneras av dina egna kommandon.

Windows PowerShell använder data i dessa formatering filer för att avgöra vad som visas och hur informationen har formaterats. Data som visas kan innehålla egenskaperna för ett objekt eller värdet för ett skriptblock.  Skriptblocken används om du vill visa ett värde som inte är tillgänglig direkt från egenskaperna för ett objekt. Du kanske vill lägga till värdet för två egenskaper för ett objekt och visa summan som en separat del av data. När du skriver din egen formatering fil du behöver definiera *vyer* för de objekt som du vill visa. Du kan definiera en vy för varje objekt, kan du definiera en vy för flera objekt eller du kan definiera flera vyer för samma objekt. Det finns ingen gräns för antal vyer som du kan definiera.

> [!IMPORTANT]
> Formatering filer styr inte den del av ett objekt som returneras till pipelinen. Alla medlemmar i objektet är tillgängliga när ett objekt returneras till pipelinen.

## <a name="format-views"></a>Formatet vyer

Formatering vyer kan visa objekt i ett tabellformat, ett listformat, ett brett format och ett anpassat format. För det mesta beskrivs varje formatering definition av en uppsättning XML-taggar som beskriver en vy. Varje vy innehåller namnet på vyn objekt som använder vyn och element i vyn, till exempel kolumn- och information för en tabellvy.

Följande vyer är tillgängliga.

Tabellvy visas egenskaperna för ett objekt eller ett skript block värde i en eller flera kolumner. Varje kolumn representerar en egenskap för objektet eller ett skript block-värde. Du kan definiera en tabellvy som visar alla egenskaper för ett objekt, en delmängd av egenskaperna för ett objekt eller en kombination av egenskaper och värden för skript-block. Varje rad i tabellen representerar en returnerade objektet. Mer information om den här vyn finns i [tabellvy](../format/creating-a-table-view.md).

Listvyn visas egenskaperna för ett objekt eller ett skript block värde i en enda kolumn. Varje rad i listan visar en valfri etikett eller egenskapens namn följt av värdet för den egenskapen eller skript. Mer information om den här vyn finns i [listvyn](../format/creating-a-list-view.md).

Bred vy innehåller en enda egenskap för ett objekt eller ett skript block värde i en eller flera kolumner. Det finns ingen etikett eller rubrik för den här vyn. Mer information om den här vyn finns i [bred vy](../format/creating-a-wide-view.md).

Anpassad vy visar en anpassningsbar objektegenskaper eller skript block värden som inte följer den fasta strukturen för tabellvyer, listvyer eller wide vyer. Du kan definiera en anpassad vy för fristående eller du kan definiera en anpassad vy som används av en annan vy, till exempel en tabell eller listvy. Mer information om den här vyn finns i [anpassad vy](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>Visa XML-element

I följande exempel visar XML-taggar som används för att definiera en tabellvy som innehåller två kolumner. Den [ViewDefinitions](../format/viewdefinitions-element-format.md) elementet är elementet behållare för alla vyer som definieras i filen formatering. Den [visa](../format/view-element-format.md) elementet definierar viss tabell, lista, brett eller anpassade vy. I varje vy i [namn](../format/name-element-for-view-format.md) elementet anger namnet på vyn, den [ViewSelectedBy](../format/viewselectedby-element-format.md) elementet definierar de objekt som använder vyn och de olika kontrollelementen (som den `TableControl` elementet) definierar formatet för vyn.

```xml
ViewDefinitions
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

[Tabellvy](../format/creating-a-table-view.md)

[Listvy](../format/creating-a-list-view.md)

[Bred vy](../format/creating-a-wide-view.md)

[Anpassad vy](../format/creating-custom-controls.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
