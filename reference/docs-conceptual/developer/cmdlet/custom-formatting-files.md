---
title: Filer för anpassad formatering | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359417"
---
# <a name="custom-formatting-files"></a>Anpassade formateringsfiler

Visnings formatet för de objekt som returneras av cmdlets, Functions och scripts definieras med hjälp av filer (format. ps1xml-filer). Flera av de här filerna tillhandahålls av Windows PowerShell för att definiera standard visnings formatet för de objekt som returneras av Windows PowerShell-cmdlets. Men du kan också skapa egna filer för att skriva över standard visnings formaten eller definiera visningen av objekt som returneras av dina egna kommandon.

Windows PowerShell använder datan i dessa filer för att avgöra vad som visas och hur data formateras. De data som visas kan innehålla egenskaperna för ett objekt eller värdet för ett skript block.  Skript block används om du vill visa ett värde som inte är tillgängligt direkt från egenskaperna för ett objekt. Du kanske exempelvis vill lägga till värdet för två egenskaper för ett objekt och Visa summan som en separat del av data. När du skriver din egen fil format måste du definiera *vyer* för de objekt som du vill visa. Du kan definiera en enskild vy för varje objekt, du kan definiera en enskild vy för flera objekt, eller så kan du definiera flera vyer för samma objekt. Det finns ingen gräns för hur många vyer du kan definiera.

> [!IMPORTANT]
> Filer formateras inte med de element som returneras till pipelinen. När ett objekt returneras till pipelinen är alla medlemmar i objektet tillgängliga.

## <a name="format-views"></a>Formatera vyer

Vyer för formatering kan visa objekt i tabell format, ett List format, ett brett format och ett anpassat format. För det mesta beskrivs varje format definition av en uppsättning XML-taggar som beskriver en vy. Varje vy innehåller namnet på vyn, de objekt som använder vyn och elementen i vyn, till exempel kolumn-och rad information för en tabellvy.

Följande vyer är tillgängliga.

I Tabellvy visas egenskaperna för ett objekt eller ett skript Blocks värde i en eller flera kolumner. Varje kolumn representerar en egenskap hos objektet eller ett skript Blocks värde. Du kan definiera en tabellvy som visar alla egenskaper för ett objekt, en delmängd av egenskaperna för ett objekt eller en kombination av egenskaper och skript Blocks värden. Varje rad i tabellen representerar ett returnerat objekt. Mer information om den här vyn finns i [tabellvy](../format/creating-a-table-view.md).

Listvy visar egenskaperna för ett objekt eller ett skript Blocks värde i en kolumn. Varje rad i listan visar en valfri etikett eller egenskaps namnet följt av värdet för egenskapen eller skript blocket. Mer information om den här vyn finns i [listvyn](../format/creating-a-list-view.md).

Wide View visar en enskild egenskap för ett objekt eller ett skript Blocks värde i en eller flera kolumner. Det finns ingen etikett eller rubrik för den här vyn. Mer information om den här vyn finns i [wide View](../format/creating-a-wide-view.md).

Anpassad vy visar en anpassningsbar vy av objekt egenskaper eller skript Blocks värden som inte följer den stela strukturen i tabellvyer, listvyer eller breda vyer. Du kan definiera en fristående anpassad vy, eller så kan du definiera en anpassad vy som används av en annan vy, till exempel en tabellvy eller listvy. Mer information om den här vyn finns i [anpassad vy](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>Visa XML-element

I följande exempel visas de XML-taggar som används för att definiera en tabellvy som innehåller två kolumner. [ViewDefinitions](../format/viewdefinitions-element-format.md) -elementet är behållar elementet för alla vyer som definierats i format filen. Elementet [View](../format/view-element-format.md) definierar den aktuella vyn för tabeller, listor, bred eller anpassad. I varje vy anger [Name](../format/name-element-for-view-format.md) -elementet namnet på vyn, [ViewSelectedBy](../format/viewselectedby-element-format.md) -elementet definierar de objekt som använder vyn och de olika kontroll elementen (till exempel elementet `TableControl`) definierar formatet för vyn.

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

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
