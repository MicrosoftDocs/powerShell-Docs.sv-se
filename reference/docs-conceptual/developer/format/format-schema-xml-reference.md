---
title: Formatera XML-referens för schema | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 437b3d6bb62fdd3a74f3392ec71df360c01a1974
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355029"
---
# <a name="format-schema-xml-reference"></a>XML-referens för formatschema

Ämnena i det här avsnittet beskriver de XML-element som används för att formatera filer (format. ps1xml-filer). Formaterar filer definierar hur .NET-objektet visas. de ändrar inte själva objektet.

## <a name="in-this-section"></a>I detta avsnitt

[Justerings element för TableColumnHeader för TableControl (format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) Definierar hur data i en kolumn rubrik visas.

[Justerings element för TableColumnItem för TableControl (format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) Definierar hur data på raden visas.

[AutoSize-element för TableControl (format)](./autosize-element-for-tablecontrol-format.md) Anger om kolumn storleken och antalet kolumner justeras baserat på data storleken.

[AutoSize-element för WideControl (format)](./autosize-element-for-widecontrol-format.md) Anger om kolumn storleken och antalet kolumner justeras baserat på data storleken.

[ColumnNumber-element för WideControl (format)](./columnnumber-element-for-widecontrol-format.md) Anger antalet kolumner som visas i den bred vyn.

[Konfigurations element (format)](./configuration-element-format.md) Representerar det översta elementet i format filen.

[Kontroll element för konfigurations kontroll (format)](./control-element-for-controls-for-configuration-format.md) Definierar en gemensam kontroll som kan användas av alla vyer i format filen och det namn som används för att referera till kontrollen.

[Kontroll element för kontroller för vy (format)](./control-element-for-controls-for-view-format.md) Definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.

[Styr element för konfiguration (format)](./controls-element-for-configuration-format.md) Definierar de gemensamma kontroller som kan användas av alla vyer i formaterings filen.

[Styr element för vy (format)](./controls-element-for-view-format.md) Definierar de visnings kontroller som kan användas av en speciell vy.

[CustomControl-element för kontroll av konfiguration (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) Definierar en kontroll. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[CustomControl-element för kontroll för vy (format)](./customcontrol-element-for-control-for-controls-for-view-format.md) Definierar en kontroll som används i vyn.

[CustomControl-element för groupby (format)](./customcontrol-element-for-groupby-format.md) Definierar den anpassade kontrollen som visar den nya gruppen.

[CustomControl-element (format)](./customcontrol-element-for-groupby-format.md) Definierar ett anpassat kontroll format för vyn.

[CustomControlName-element för ExpressionBinding för kontroller för konfiguration (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) Anger namnet på en gemensam kontroll. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[CustomControlName-element för ExpressionBindine för kontroller för vy (format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) Anger namnet på en gemensam kontroll eller en visnings kontroll. Det här elementet används när du definierar kontroller som kan användas av en vy.

[CustomControlName-element för groupby (format)](./customcontrolname-element-for-groupby-format.md) Anger namnet på en anpassad kontroll som används för att visa den nya gruppen. Det här elementet används när du definierar en tabell, lista, bred eller anpassad flikkontroll.

[CustomEntry-element för CustomControl för kontroller för konfiguration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) Ger en definition av den gemensamma kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[CustomEntry-element för CustomEntries för kontroller för vy (format)](./customentry-element-for-customentries-for-controls-for-view-format.md) Ger en definition av kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[CustomEntry-element för CustomEntries för vy (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) Innehåller en definition av den anpassade kontrollen.

[CustomEntry-element för CustomControl för groupby (format)](./customentry-element-for-customcontrol-for-groupby-format.md) Ger en definition av kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[CustomEntries-element för CustomControl för konfiguration (format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) Innehåller definitionerna för en gemensam kontroll. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[CustomEntries-element för CustomControl för kontroller för vy (format)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) Innehåller definitionerna för kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[CustomEntries-element för CustomControl för groupby (format)](./customentries-element-for-customcontrol-for-groupby-format.md) Innehåller definitionerna för kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[CustomEntries-element för CustomControl för vy (format)](./customentries-element-for-customcontrol-for-view-format.md) Innehåller definitionerna för vyn anpassad kontroll. Vyn anpassad kontroll måste ange en eller flera definitioner.

[CustomItem-element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md) Definierar vilka data som visas av kontrollen och hur de visas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[CustomItem-element för CustomEntry för kontroller för vy (format)](./customitem-element-for-customentry-for-controls-for-view-format.md) Definierar vilka data som visas av kontrollen och hur de visas. Det här elementet används när du definierar kontroller som kan användas av en vy.

[CustomItem-element för CustomEntry för vy (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) Definierar vilka data som visas i vyn anpassad kontroll och hur den visas. Det här elementet används när du definierar en anpassad kontrol vy.

[CustomItem-element för CustomEntry för groupby (format)](./customitem-element-for-customentry-for-groupby-format.md) Definierar vilka data som visas i vyn anpassad kontroll och hur den visas. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[DefaultSettings-element (format)](./defaultsettings-element-format.md) Definierar vanliga inställningar som gäller för alla vyer i formaterings filen. Vanliga inställningar är att visa fel, figursätta text i tabeller, definiera hur samlingar expanderas och mycket mer.

[DisplayError-element (format)](./displayerror-element-format.md) Anger att strängen #ERR visas när det uppstår ett fel vid visning av en data del.

[EntrySelectedBy-element för CustomEntry för kontroller för konfiguration (format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) Definierar de .NET-typer som använder definitionen av den gemensamma kontrollen eller villkoret som måste finnas för att den här kontrollen ska kunna användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[EntrySelectedBy-element för CustomEntry för kontroller för vy (format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas. Det här elementet används när du definierar kontroller som kan användas av en vy.

[EntrySelectedBy-element för CustomEntry för vy (format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) Definierar de .NET-typer som använder den här anpassade posten eller det villkor som måste finnas för att den här posten ska kunna användas.

[EntrySelectedBy-element för EnumerableExpansion (format)](./entryselectedby-element-for-enumerableexpansion-format.md) Definierar de .NET-typer som använder den här definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.

[EntrySelectedBy-element för CustomEntry för groupby (format)](./entryselectedby-element-for-customentry-for-groupby-format.md) Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[EntrySelectedBy-element för ListEntry för ListControl (format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md) Definierar de .NET-typer som använder den här List vydefinitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas. I de flesta fall behövs bara en definition för en listvy. Du kan dock ange flera definitioner för listvyn om du vill använda samma listvy för att visa olika data för olika objekt.

[EntrySelectedBy-element för TableRowEntry (format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) Definierar de .NET-typer vars egenskaps värden visas på raden.

[EntrySelectedBy-element för WideEntry (format)](./entryselectedby-element-for-wideentry-format.md) Definierar de .NET-typer som använder den här definitionen för wide View eller det villkor som måste finnas för att den här definitionen ska kunna användas.

[EnumerableExpansion-element (format)](./enumerableexpansion-element-format.md) Definierar hur vissa .NET Collection-objekt expanderas när de visas i en vy.

[EnumerableExpansions-element (format)](./enumerableexpansions-element-format.md) Definierar hur .NET-samlings objekt expanderas när de visas i en vy.

[EnumerateCollection-element för ExpressionBinding för kontroller för konfiguration (format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) Anger att elementen i samlingar visas av kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[EnumerateCollection-element för ExpressionBinding för kontroller för vy (format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) Anger att samlings elementen visas. Det här elementet används när du definierar kontroller som kan användas av en vy.

[EnumerateCollection-element för uttrycks bindning för CustomControl för vy (format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) Anger att elementen i samlingar visas. Det här elementet används när du definierar en anpassad kontrol vy.

[EnumerateCollection-element för ExpressionBinding för groupby (format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Anger att elementen i samlingar visas. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[Expandera element (format)](./expand-element-format.md) Anger hur Collection-objektet expanderas för den här definitionen.

[ExpressionBinding-element för CustomItem för kontroller för konfiguration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) Definierar de data som visas av kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[ExpressionBinding-element för CustomItem för kontroller för vy (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) Definierar de data som visas av kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[ExpressionBinding-element för CustomItem för CustomControl för View (format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) Definierar de data som visas av kontrollen. Det här elementet används när du definierar en anpassad kontrol vy.

[ExpressionBinding-element för CustomItem för groupby (format)](./expressionbinding-element-for-customitem-for-groupby-format.md) Definierar de data som visas av kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[FirstLineHanging-element för ram för kontroll av konfiguration (format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) Anger hur många tecken den första raden med data flyttas till vänster. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[FirstLineHanging-element för kontroll bild av vyer (format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) Anger hur många tecken den första raden med data flyttas till vänster. Det här elementet används när du definierar kontroller som kan användas av en vy.

[FirstLineHanging-element för Frame för CustomControl för vy (format)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) Anger hur många tecken den första raden med data flyttas till vänster. Det här elementet används när du definierar en anpassad kontrol vy.

[FirstLineHanging-element för inramad groupby (format)](./firstlinehanging-element-for-frame-for-groupby-format.md) Anger hur många tecken den första raden med data flyttas till vänster. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[FirstLineIndent-element för ram för kontroll av konfiguration (format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) Anger hur många tecken den första raden med data flyttas till höger. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[FirstLineIndent-element för kontroll bild av vyer (format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) Anger hur många tecken den första raden med data flyttas till höger. Det här elementet används när du definierar kontroller som kan användas av en vy.

[FirstLineIndent-element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) Anger hur många tecken den första raden med data flyttas till höger. Det här elementet används när du definierar en anpassad kontrol vy.

[FirstLineIndent-element för inramad groupby (format)](./firstlineindent-element-for-frame-for-groupby-format.md) Anger hur många tecken den första raden med data flyttas till höger. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[FormatString-element för ListItem (format)](./formatstring-element-for-listitem-for-listcontrol-format.md) Anger ett format mönster som definierar hur egenskapen eller skriptets värde visas.

[FormatString-element för TableColumnItem (format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) Anger ett format mönster som definierar hur tabellens egenskaps-eller skript värde visas.

[FormatString-element för WideItem för WideControl (format)](./formatstring-element-for-wideitem-for-widecontrol-format.md) Anger ett format mönster som definierar hur egenskapen eller skriptets värde visas i vyn.

[Ram element för CustomItem för kontroll av konfiguration (format)](./frame-element-for-customitem-for-controls-for-configuration-format.md) Definierar hur data visas, till exempel att flytta data till vänster eller höger. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[Ram element för CustomItem för kontroller för vy (format)](./frame-element-for-customitem-for-controls-for-view-format.md) Definierar hur data visas, till exempel att flytta data till vänster eller höger. Det här elementet används när du definierar kontroller som kan användas av en vy.

[Inramat element för CustomItem för CustomControl för vy (format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md) Definierar hur data visas, till exempel att flytta data till vänster eller höger. Det här elementet används när du definierar en anpassad kontrol vy.

[Ram element för CustomItem för groupby (format)](./frame-element-for-customitem-for-groupby-format.md) Definierar hur data visas, till exempel att flytta data till vänster eller höger. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[Groupby-element för vy (format)](./groupby-element-for-view-format.md) Definierar hur Windows PowerShell visar en ny grupp med objekt.

[HideTableHeaders-element (format)](./hidetableheaders-element-format.md) Anger att tabell rubrikerna inte visas.

[ItemSelectionCondition-element för ExpressionBinding för kontroller för konfiguration (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas. Det här elementet används när du definierar kontroller som kan användas av en vy.

[ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas. Det finns ingen gräns för antalet urvals villkor som kan anges för ett kontroll objekt. Det här elementet används när du definierar en anpassad kontrol vy.

[ItemSelectionCondition-element för ExpressionBinding för groupby (format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas. Det finns ingen gräns för antalet urvals villkor som kan anges för ett kontroll objekt. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[ItemSelectionCondition-element för ListItem (format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) Definierar det villkor som måste finnas för att listobjektet ska kunna användas.

[Etikett element för ListItem för ListControl (format)](./label-element-for-listitem-for-listcontrol-format.md) Anger etiketten för egenskapen eller skriptets värde på raden.

[Etikett element för groupby (format)](./label-element-for-groupby-format.md) Anger en etikett som visas när en ny grupp påträffas.

[Etikett element för TableColumnHeader (format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) Definierar etiketten som visas överst i en kolumn.

[LeftIndent-element för ram för kontroll av konfiguration (format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) Anger hur många tecken data flyttas bort från vänstermarginalen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[LeftIndent-element för kontroll bild av vyer (format)](./leftindent-element-for-frame-for-controls-for-view-format.md) Anger hur många tecken data flyttas bort från vänstermarginalen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[LeftIndent-element för Frame för CustomControl för vy (format)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) Anger hur många tecken data flyttas bort från vänstermarginalen. Det här elementet används när du definierar en anpassad kontrol vy.

[LeftIndent-element för inramad groupby (format)](./leftindent-element-for-frame-for-groupby-format.md) Anger hur många tecken data flyttas bort från vänstermarginalen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[ListControl-element (format)](./listcontrol-element-format.md) Definierar ett List format för vyn.

[ListEntry-element (format)](./listentry-element-for-listcontrol-format.md) Ger en definition av listvyn.

[ListEntries-element (format)](./listentries-element-for-listcontrol-format.md) Definierar hur raderna i listvyn visas.

[ListItem-element (format)](./listitem-element-for-listitems-for-listcontrol-format.md) Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.

[ListItems-element (format)](./listitems-element-for-listentry-for-listcontrol-format.md) Definierar de egenskaper och skript som visas i listvyn.

[Namn element för kontroll för konfiguration (format)](./name-element-for-control-for-controls-for-configuration-format.md) Anger kontrollens namn. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[Namn element för SelectionSet (format)](./name-element-for-selectionset-format.md) Anger namnet som används för att referera till urvals uppsättningen.

[Namn element för vy (format)](./name-element-for-view-format.md) Anger namnet som används för att identifiera vyn.

[Rad matnings element för CustomItem för kontroll av konfiguration (format)](./newline-element-for-customitem-for-controls-for-configuration-format.md) Lägger till en tom rad i visningen av kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[Rad matnings element för CustomItem för kontroller för vy (format)](./newline-element-for-customitem-for-controls-for-view-format.md) Lägger till en tom rad i visningen av kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[Rad matnings element för CustomItem för CustomControl för vy (format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) Lägger till en tom rad i visningen av kontrollen. Det här elementet används när du definierar en anpassad kontrol vy.

[Rad matnings element för CustomItem för groupby (format)](./newline-element-for-customitem-for-groupby-format.md) Lägger till en tom rad i visningen av kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[PropertyName-element för ExpressionBinding för kontroll av konfiguration (format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) Anger .NET-egenskapen vars värde visas av den gemensamma kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[PropertyName-element för ExpressionBinding för kontroller för vy (format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) Anger den .NET-egenskap vars värde visas av kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[PropertyName-element för ExpressionBinding för CustomControl för vy (format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) Anger den .NET-egenskap vars värde visas av kontrollen. Det här elementet används när du definierar en anpassad vy

[PropertyName-element för ExpressionBinding för groupby (format)](./propertyname-element-for-expressionbinding-for-groupby-format.md) Anger den .NET-egenskap vars värde visas av kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[PropertyName-element för groupby (format)](./propertyname-element-for-groupby-format.md) Anger den .NET-egenskap som startar en ny grupp när dess värde ändras.

[PropertyName-element för ItemSeclectionCondition för kontroll av konfiguration (format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och kontrollen används. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[PropertyName-element för ItemSelectionCondition för kontroller för vy (format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och kontrollen används. Det här elementet används när du definierar kontroller som kan användas av en vy.

[PropertyName-element för ItemSelectionCondition för CustomControl för View (format](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) anger den .net-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och kontrollen används. Det här elementet används när du definierar en anpassad kontrol vy.

[PropertyName-element för ItemSelectionCondition för groupby (format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och kontrollen används. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[PropertyName-element för ItemSelectionCondition för ListItem (format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och vyn används. Det här elementet används när du definierar en listvy.

[PropertyName-element för ListItem för ListControl (format)](./propertyname-element-for-listitem-for-listcontrol-format.md) Anger den .NET-egenskap vars värde visas i listan.

[PropertyName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och posten används. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[PropertyName-element för SelectionCondition för kontroller för vy (format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och posten används. Det här elementet används när du definierar kontroller som kan användas av en vy.

[PropertyName-element för SelectionCondition för CustomControl för vy (format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och definitionen används. Det här elementet används när du definierar en anpassad kontrol vy.

[PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och definitionen används.

[PropertyName-element för SelectionCondition för groupby (format)](./propertyname-element-for-selectioncondition-for-groupby-format.md) Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och definitionen används. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[PropertyName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och list posten används.

[PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och tabell posten används.

[PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Anger den .NET-egenskap som utlöser villkoret. När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och definitionen används.

[PropertyName-element för TableColumnItem (format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) Anger den egenskap vars värde visas i kolumnen på raden.

[PropertyName-element för WideItem (format)](./propertyname-element-for-wideitem-for-widecontrol-format.md) Anger egenskapen för det objekt vars värde visas i den bred vyn.

[RightIndent-element för ram för kontroll av konfiguration (format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) Anger hur många tecken data flyttas bort från högermarginalen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[RightIndent-element för kontroll bild av vyer (format)](./rightindent-element-for-frame-for-controls-for-view-format.md) Anger hur många tecken data flyttas bort från högermarginalen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[RightIndent-element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) Anger hur många tecken data flyttas bort från högermarginalen. Det här elementet används när du definierar en anpassad kontrol vy.

[RightIndent-element för inramad groupby (format)](./rightindent-element-for-frame-for-groupby-format.md) Anger hur många tecken data flyttas bort från högermarginalen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[Script block-element för ExpressionBinding för kontroller för konfiguration (format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) Anger det skript vars värde visas av den gemensamma kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[Script block-element för ExpressionBinding för kontroller för vy (format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) Anger det skript vars värde visas i kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[Script block-element för ExpressionBinding för CustomCustomControl för View (format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) Anger det skript vars värde visas i kontrollen. Det här elementet används när du definierar en anpassad kontrol vy.

[Script block-element för ExpressionBinding för groupby (format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md) Anger det skript vars värde visas i kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[Script block-element för groupby (format)](./scriptblock-element-for-groupby-format.md) Anger det skript som startar en ny grupp när dess värde ändras.

[Script block-element för ItemSelectionCondition för kontroller för konfiguration (format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och kontrollen används. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[Script block-element för ItemSelectionCondition för kontroller för vy (format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och kontrollen används. Det här elementet används när du definierar kontroller som kan användas av en vy.

[Script block-element för ItemSelectionCondition för CustomControl för View (format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och kontrollen används. Det här elementet används när du definierar en anpassad kontrol vy.

[Script block-element för ItemSelectionCondition för groupby (format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och kontrollen används. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[Script block-element för ItemSelectionCondition för ListControl (format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och listobjektet används. Det här elementet används när du definierar en listvy.

[Script block-element för ListItem (format)](./scriptblock-element-for-listitem-for-listcontrol-format.md) Anger det skript vars värde visas i raden i listan.

[Script block-element för SelectionCondition för kontroller för konfiguration (format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och definitionen används. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[Script block-element för SelectionCondition för kontroller för vy (format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och definitionen används. Det här elementet används när du definierar kontroller som kan användas av en vy.

[Script block-element för SelectionCondition för CustomControl för View (format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och definitionen används. Det här elementet används när du definierar en anpassad kontrol vy.

[Script block-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Anger det skript som utlöser villkoret.

[Script block-element för SelectionCondition för groupby (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och definitionen används. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[Script block-element för SelectionCondition för EntrySelectedBy för ListEntry (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och list posten används.

[Script block-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Anger det skript block som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och tabell posten används.

[Script block-element för SelectionCondition för EntrySelectedBy för WideEntry (format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Anger det skript som utlöser villkoret. När det här skriptet utvärderas till `true`, uppfylls villkoret och den breda post definitionen används.

[Script block-element för TableColumnItem (format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) Anger det skript vars värde visas i kolumnen på raden.

[Script block-element för WideItem (format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Anger det skript vars värde visas i den breda vyn.

[SelectionCondition-element för EntrySelectedBy för CustomEntry för konfiguration (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) Definierar ett villkor som måste finnas för att en gemensam kontroll definition ska kunna användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[SelectionCondition-element för EntrySelectedBy för kontroller för vy (format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) Definierar ett villkor som måste finnas för att den kontroll definition som ska användas. Det här elementet används när du definierar kontroller som kan användas av en vy.

[SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) Definierar ett villkor som måste finnas för att en kontroll definition ska kunna användas. Det här elementet används när du definierar en anpassad kontrol vy.

[SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.

[SelectionCondition-element för EntrySelectedBy för groupby (format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) Definierar ett villkor som måste finnas för att en kontroll definition ska kunna användas. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[SelectionCondition-element för EntrySelectedBy för ListEntry (format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) Definierar det villkor som måste finnas för att använda den här definitionen av listvyn. Det finns ingen gräns för antalet urvals villkor som kan anges för en List definition.

[SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) Definierar det villkor som måste finnas för att användas för den här definitionen av tabellvy. Det finns ingen gräns för antalet urvals villkor som kan anges för en tabell definition.

[SelectionCondition-element för EntrySelectedBy för WideEntry (format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) Definierar det villkor som måste finnas för att den här definitionen ska kunna användas. Det finns ingen gräns för hur många urvals villkor som kan anges för en bred post definition.

[SelectionSet-element (format)](./selectionset-element-format.md) Definierar en uppsättning .NET-objekt som kan refereras till i uppsättningens namn.

[SelectionSetName-element för EntrySelectedBy för kontroller för konfiguration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[SelectionSetName-element för EntrySelectedBy för kontroller för vy (format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[SelectionSetName-element för EntrySelectedBy för CustomEntry (format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) Anger en uppsättning .NET-objekt för List posten. Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.

[SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) Anger den uppsättning av .NET-typer som expanderas av den här definitionen.

[SelectionSetName-element för EntrySelectedBy för groupby (format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) Anger en uppsättning .NET-objekt för List posten. Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[SelectionSetName-element för EntrySelectedBy för ListEntry (format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) Anger en uppsättning .NET-objekt för List posten. Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.

[SelectionSetName-element för EntrySelectedBy för TableRowEntry (format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) Anger en uppsättning .NET-typer. Använd den här posten i vyn tabell. Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.

[SelectionSetName-element för EntrySelectedBy för WideEntry (format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) Anger en uppsättning .NET-objekt för definitionen. Definitionen används när något av dessa objekt visas.

[SelectionSetName-element för SelectionCondition för kontroller för konfiguration (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[SelectionSetName-element för SelectionCondition för kontroller för vy (format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med den här kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[EntrySelectedBy-element för CustomEntry för vy (format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med den här kontrollen. Det här elementet används när du definierar en anpassad kontrol vy.

[SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen är närvarande uppfylls villkoret.

[SelectionSetName-element för SelectionCondition för groupby (format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här definitionen av listvyn.

[SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här definitionen av tabellvy.

[SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Anger den uppsättning av .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas genom att använda den här definitionen av wide View.

[SelectionSetName-element för ViewSelectedBy (format)](./selectionsetname-element-for-viewselectedby-format.md) Anger en uppsättning .NET-objekt som visas i vyn.

[SelectionSets-element (format)](./selectionsets-element-format.md) Definierar de uppsättningar av .NET-objekt som kan användas av enskilda format-vyer.

[ShowError-element (format)](./showerror-element-format.md) Anger att den fullständiga fel posten visas när ett fel inträffar när en del av data visas.

[TableColumnHeader-element för TableHeaders för TableControl (format)](./tablecolumnheader-element-format.md) Definierar etiketten, bredden på kolumnen och justeringen av etiketten för en kolumn i tabellen.

[TableColumnItem-element (format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) Definierar egenskapen eller skriptet vars värde visas i kolumnen på raden.

[TableColumnItems-element (format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) Definierar de egenskaper eller skript vars värden visas på raden.

[TableControl-element (format)](./tablecontrol-element-format.md) Definierar ett tabell format för en vy.

[TableHeaders-element (format)](./tableheaders-element-format.md) Definierar rubrikerna för kolumnerna i en tabell.

[TableRowEntries-element (format)](./tablerowentries-element-for-tablecontrol-format.md) Definierar raderna i tabellen.

[TableRowEntry-element (format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) Definierar de data som visas i en rad i tabellen.

[Text element för CustomItem för konfigurations kontroller (format)](./text-element-for-customitem-for-controls-for-configuration-format.md) Anger text som läggs till i data som visas av kontrollen, till exempel en etikett, hakparenteser som omger data och blank steg för att dra in data. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[Text element för CustomItem för kontroller för vy (format)](./text-element-for-customitem-for-controls-for-view-format.md) Anger text som läggs till i data som visas av kontrollen, till exempel en etikett, hakparenteser som omger data och blank steg för att dra in data. Det här elementet används när du definierar kontroller som kan användas av en vy.

[Text element för CustomItem (format)](./text-element-for-customitem-for-customview-for-view-format.md) Anger text som läggs till i data som visas av kontrollen, till exempel en etikett, hakparenteser som omger data och blank steg för att dra in data. Det här elementet används när du definierar en anpassad kontrol vy.

[Text element för CustomItem för groupby (format)](./text-element-for-customitem-for-groupby-format.md) Anger text som läggs till i data som visas av kontrollen, till exempel en etikett, hakparenteser som omger data och blank steg för att dra in data. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[Elementet TypeName för EntrySelectedBy för kontroller för konfiguration (format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) Anger en .NET-typ som använder den här definitionen av kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[Elementet TypeName för EntrySelectedBy för kontroller för vyn (format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md) Anger en .NET-typ som använder den här definitionen av kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[Elementet TypeName för EntrySelectedBy för CustomEntry för vyn (format)](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) Anger en .NET-typ som använder den här definitionen för den anpassade kontrollen. Det finns ingen gräns för antalet typer som kan anges för en definition.

[Elementet TypeName för EntrySelectedBy för EnumerableExpansion (format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) Anger en .NET-typ som utökas av den här definitionen. Det här elementet används när du definierar en standardinställning.

[Elementet TypeName för EntrySelectedBy för groupby (format)](./typename-element-for-entryselectedby-for-groupby-format.md) Anger en .NET-typ som använder den här definitionen av den anpassade kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[Elementet TypeName för EntrySelectedBy för ListControl (format)](./typename-element-for-entryselectedby-for-listcontrol-format.md) Anger en .NET-typ som använder den här posten i list visningen. Det finns ingen gräns för antalet typer som kan anges för en List post.

[Elementet TypeName för EntrySelectedBy för TableRowEntry (format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md) Anger en .NET-typ som använder den här posten i vyn tabell. Det finns ingen gräns för antalet typer som kan anges för en tabell post.

[Elementet TypeName för EntrySelectedBy för WideEntry (format)](./typename-element-for-entryselectedby-for-wideentry-format.md) Anger en .NET-typ för definitionen. Definitionen används när det här objektet visas.

[Elementet TypeName för SelectionCondition för kontroller för konfiguration (format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) Anger en .NET-typ som utlöser villkoret. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

[Elementet TypeName för SelectionCondition för kontroller för vyn (format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) Anger en .NET-typ som utlöser villkoret. Det här elementet används när du definierar kontroller som kan användas av en vy.

[Elementet TypeName för SelectionCondition för CustomControl för vyn (format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) Anger en .NET-typ som utlöser villkoret. Det här elementet används när du definierar en anpassad kontrol vy.

[Elementet TypeName för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Anger en .NET-typ som utlöser villkoret.

[Elementet TypeName för SelectionCondition för groupby (format)](./typename-element-for-selectioncondition-for-groupby-format.md) Anger en .NET-typ som utlöser villkoret. Det här elementet används när du definierar hur en ny grupp av objekt visas.

[Elementet TypeName för SelectionCondition för EntrySelectedBy för ListControl (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Anger en .NET-typ som utlöser villkoret. När den här typen finns används List posten.

[Elementet TypeName för SelectionCondition för EntrySelectedBy för TableRowEntry (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Anger en .NET-typ som utlöser villkoret. När den här typen är närvarande uppfylls villkoret och tabell raden används.

[Elementet TypeName för SelectionCondition för EntrySelectedBy för WideEntry (format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Anger en .NET-typ som utlöser villkoret. När den här typen finns används definitionen.

[Elementet TypeName för typer (format)](./typename-element-for-types-format.md) Anger .NET-typen för ett objekt som tillhör urvals uppsättningen.

[Elementet TypeName för ViewSelectedBy (format)](./typename-element-for-viewselectedby-format.md) Anger ett .NET-objekt som visas i vyn.

[Typ element (format)](./types-element-for-selectionset-format.md) Definierar de .NET-objekt som finns i urvals uppsättningen.

[Visa element (format)](./view-element-format.md) Definierar en vy som används för att visa ett eller flera .NET-objekt.

[ViewDefinitions-element (format)](./viewdefinitions-element-format.md) Definierar de vyer som används för att visa objekt.

[ViewSelectedBy-element (format)](./viewselectedby-element-format.md) Definierar de .NET-objekt som visas i vyn.

[WideControl-element (format)](./widecontrol-element-format.md) Definierar ett brett List format (enskilt värde) för vyn. I den här vyn visas ett enskilt egenskaps värde eller skript värde för varje objekt.

[WideEntries-element (format)](./wideentries-element-for-widecontrol-format.md) Innehåller definitionerna för den breda vyn. Wide View måste ange en eller flera definitioner.

[WideEntry-element (format)](./wideentry-element-for-widecontrol-format.md) Ger en definition av den breda vyn.

[WideItem-element (format)](./wideitem-element-for-widecontrol-format.md) Definierar egenskapen eller skriptet vars värde visas.

[Bredd element (format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) Definierar bredden (i tecken) för en kolumn.

Omslutande [element (format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) Anger att text som överskrider kolumn bredden visas på nästa rad.

[WrapTables-element (format)](./wraptables-element-format.md) Anger att data i en tabell cell flyttas till nästa rad om data är längre än kolumnens bredd.

## <a name="see-also"></a>Se även

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
