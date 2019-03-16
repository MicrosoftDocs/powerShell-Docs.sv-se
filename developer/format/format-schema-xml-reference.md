---
title: Formatera XML-Schemareferens | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 437b3d6bb62fdd3a74f3392ec71df360c01a1974
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056659"
---
# <a name="format-schema-xml-reference"></a>XML-referens för formatschema

I det här avsnittet beskrivs de XML-element som används genom att formatera (Format.ps1xml filer). Formateras som definierar hur .NET-objekt visas; de ändras inte själva objektet.

## <a name="in-this-section"></a>I detta avsnitt

[Justering Element för TableColumnHeader för TableControl (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) definierar hur data i en kolumnrubrik visas.

[Justering Element för TableColumnItem för TableControl (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) definierar hur data i raden visas.

[AutoSize-Element för TableControl (Format)](./autosize-element-for-tablecontrol-format.md) anger om kolumnstorlek och antalet kolumner justeras baserat på storleken på data.

[AutoSize-Element för WideControl (Format)](./autosize-element-for-widecontrol-format.md) anger om kolumnstorlek och antalet kolumner justeras baserat på storleken på data.

[Antal_kolumner anger Element för WideControl (Format)](./columnnumber-element-for-widecontrol-format.md) anger antalet kolumner som visas i bred vy.

[Konfigurationselementet (Format)](./configuration-element-format.md) representerar det översta elementet i filen formatering.

[Styra Element för kontroller för konfiguration (Format)](./control-element-for-controls-for-configuration-format.md) definierar en gemensam kontroll som kan användas av alla vyer av filen formatering och det namn som används för att referera till kontrollen.

[Styra Element för kontroller för att visa (Format)](./control-element-for-controls-for-view-format.md) definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.

[Styr Element för konfiguration (Format)](./controls-element-for-configuration-format.md) definierar de vanliga kontroller som kan användas av alla vyer i filen formatering.

[Styr Element för vy (Format)](./controls-element-for-view-format.md) definierar vyn kontroller som kan användas av en specifik vy.

[Anpassad kontroll Element för kontroll för konfiguration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) definierar en kontroll. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[Anpassad kontroll Element för kontroll för kontroller för att visa (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md) definierar en kontroll som används av vyn.

[Anpassad kontroll Element för GroupBy (Format)](./customcontrol-element-for-groupby-format.md) definierar den anpassade kontrollen som visar den nya gruppen.

[Anpassad kontroll Element (Format)](./customcontrol-element-for-groupby-format.md) definierar en anpassad kontroll formatet för vyn.

[CustomControlName Element för ExpressionBinding för kontroller för konfiguration (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) anger namnet på en gemensam kontroll. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[CustomControlName Element för ExpressionBindine för kontroller för att visa (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) anger namnet på en gemensam kontroll eller en kontroll. Det här elementet används när du definierar kontroller som kan användas av en vy.

[CustomControlName Element i GroupBy (Format)](./customcontrolname-element-for-groupby-format.md) anger namnet på en anpassad kontroll som används för att visa den nya gruppen. Det här elementet används när du definierar en tabell, lista, brett eller anpassad vy.

[CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) innehåller en definition av vanliga kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[CustomEntry Element för CustomEntries för kontroller för att visa (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md) innehåller en definition av kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[CustomEntry Element för CustomEntries för vy (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) innehåller en definition av vyn anpassad kontroll.

[CustomEntry Element för anpassad kontroll för GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md) innehåller en definition av kontrollen. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[CustomEntries Element för anpassad kontroll för konfiguration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) innehåller definitionerna av en gemensam kontroll. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[CustomEntries Element för anpassad kontroll för kontroller för att visa (Format)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) innehåller definitioner för kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[CustomEntries Element för anpassad kontroll för GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md) innehåller definitioner för kontrollen. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[CustomEntries Element för anpassad kontroll för vy (Format)](./customentries-element-for-customcontrol-for-view-format.md) innehåller definitioner av vyn anpassad kontroll. Den anpassade kontroll vyn måste ange en eller flera definitioner.

[CustomItem Element för CustomEntry för kontroller för konfiguration av](./customitem-element-for-customentry-for-controls-for-configuration-format.md) definierar vilka data som visas av kontrollen och hur de visas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[CustomItem Element för CustomEntry för kontroller för att visa (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md) definierar vilka data som visas av kontrollen och hur de visas. Det här elementet används när du definierar kontroller som kan användas av en vy.

[CustomItem Element för CustomEntry för vy (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) definierar vilka data som visas i vyn anpassad kontroll och hur de visas. Det här elementet används när du definierar en anpassad kontroll vy.

[CustomItem Element för CustomEntry för GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md) definierar vilka data som visas i vyn anpassad kontroll och hur de visas. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[DefaultSettings Element (Format)](./defaultsettings-element-format.md) definierar vanliga inställningar som gäller för alla vyer i filen formatering. Vanliga inställningar inkluderar visar fel, radbrytning i tabeller, definiera hur samlingar har expanderats och mycket annat.

[DisplayError Element (Format)](./displayerror-element-format.md) anger att strängen #ERR visas när ett fel uppstår visar en typ av data.

[EntrySelectedBy Element för CustomEntry för kontroller för konfiguration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) definierar vilka typer av .NET som använder definitionen av den vanliga kontrollen eller villkor som måste finnas för den här kontrollen som ska användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas. Det här elementet används när du definierar kontroller som kan användas av en vy.

[EntrySelectedBy Element för CustomEntry för vy (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) definierar vilka typer av .NET som använder den här anpassade posten eller villkor som måste finnas för den här posten som ska användas.

[EntrySelectedBy Element för EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md) definierar vilka typer av .NET som använder den här definitionen eller villkor som måste finnas för den här definitionen som ska användas.

[EntrySelectedBy Element för CustomEntry för GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md) definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[EntrySelectedBy Element för ListEntry för ListControl (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md) definierar vilka typer av .NET som använder den här listan vydefinitionen eller villkor som måste finnas för den här definitionen som ska användas. I de flesta fall behövs bara en definition för en listvy. Du kan ange flera definitioner för listvyn om du vill använda samma listvyn för att visa olika data för olika objekt.

[EntrySelectedBy Element för TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) definierar vilka .NET egenskaper visas i raden.

[EntrySelectedBy Element för WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md) definierar vilka typer av .NET som använder den här definitionen av bred vy eller ett villkor som måste finnas för den här definitionen som ska användas.

[EnumerableExpansion Element (Format)](./enumerableexpansion-element-format.md) definierar hur specifik .NET samling objekt visas när de visas i vyn.

[EnumerableExpansions Element (Format)](./enumerableexpansions-element-format.md) definierar hur .NET samling objekt visas när de visas i vyn.

[EnumerateCollection Element för ExpressionBinding för kontroller för konfiguration (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) anges att elementen i samlingar visas i kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[EnumerateCollection Element för ExpressionBinding för kontroller för att visa (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) anges att elementen i samlingar visas. Det här elementet används när du definierar kontroller som kan användas av en vy.

[EnumerateCollection Element för uttrycket bindning för anpassad kontroll för vy (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) anger att elementen i samlingar visas. Det här elementet används när du definierar en anpassad kontroll vy.

[EnumerateCollection Element för ExpressionBinding för GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) anger att elementen i samlingar visas. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[Expandera Element (Format)](./expand-element-format.md) anger hur samlingsobjektet utökas för den här definitionen.

[ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) definierar de data som visas i kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[ExpressionBinding Element för CustomItem för kontroller för att visa (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) definierar de data som visas i kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[ExpressionBinding Element för CustomItem för anpassad kontroll för vy (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) definierar de data som visas i kontrollen. Det här elementet används när du definierar en anpassad kontroll vy.

[ExpressionBinding Element för CustomItem för GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md) definierar de data som visas i kontrollen. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[FirstLineHanging Element för ramens för kontroller för konfiguration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) anger hur många tecken som den första raden av data ska flyttas till vänster. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[FirstLineHanging Element av kontrollerna för Visa (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) anger hur många tecken som den första raden av data ska flyttas till vänster. Det här elementet används när du definierar kontroller som kan användas av en vy.

[FirstLineHanging Element för ramens för anpassad kontroll för vy (Format)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) anger hur många tecken som den första raden av data ska flyttas till vänster. Det här elementet används när du definierar en anpassad kontroll vy.

[FirstLineHanging Element för ramens för GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md) anger hur många tecken som den första raden av data ska flyttas till vänster. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[FirstLineIndent Element för ramens för kontroller för konfiguration (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) anger hur många tecken som den första raden av data ska flyttas till höger. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[FirstLineIndent Element av kontrollerna för Visa (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) anger hur många tecken som den första raden av data ska flyttas till höger. Det här elementet används när du definierar kontroller som kan användas av en vy.

[FirstLineIndent elementet](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) anger hur många tecken som den första raden av data ska flyttas till höger. Det här elementet används när du definierar en anpassad kontroll vy.

[FirstLineIndent Element för ramens för GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md) anger hur många tecken som den första raden av data ska flyttas till höger. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[FormatString-Element för ListItem (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md) anger ett formatmönster som definierar hur värdet för egenskapen eller skript visas.

[FormatString-Element för TableColumnItem (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) anger ett formatmönster som definierar hur värdet för egenskapen eller ett skript för tabellen visas.

[FormatString-Element för WideItem för WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md) anger ett formatmönster som definierar hur värdet för egenskapen eller skript visas i vyn.

[RAM-Element för CustomItem för kontroller för konfiguration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md) definierar hur data visas, till exempel ändra datatypen till vänster eller höger. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[RAM-Element för CustomItem för kontroller för att visa (Format)](./frame-element-for-customitem-for-controls-for-view-format.md) definierar hur data visas, till exempel ändra datatypen till vänster eller höger. Det här elementet används när du definierar kontroller som kan användas av en vy.

[RAM-Element för CustomItem för anpassad kontroll för vy (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md) definierar hur data visas, till exempel ändra datatypen till vänster eller höger. Det här elementet används när du definierar en anpassad kontroll vy.

[RAM-Element för CustomItem för GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md) definierar hur data visas, till exempel ändra datatypen till vänster eller höger. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[GroupBy-Element för Visa (Format)](./groupby-element-for-view-format.md) definierar hur Windows PowerShell visar en ny grupp med objekt.

[HideTableHeaders Element (Format)](./hidetableheaders-element-format.md) anger att tabellen huvuden inte visas.

[ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) definierar de villkor som måste finnas för den här kontrollen som ska användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) definierar de villkor som måste finnas för den här kontrollen som ska användas. Det här elementet används när du definierar kontroller som kan användas av en vy.

[ItemSelectionCondition Element för uttrycket bindning för anpassad kontroll för vy (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) definierar de villkor som måste finnas för den här kontrollen som ska användas. Det finns ingen gräns för hur många val av villkor som kan anges för ett kontrollobjekt. Det här elementet används när du definierar en anpassad kontroll vy.

[ItemSelectionCondition Element för ExpressionBinding för GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) definierar de villkor som måste finnas för den här kontrollen som ska användas. Det finns ingen gräns för hur många val av villkor som kan anges för ett kontrollobjekt. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[ItemSelectionCondition Element för ListItem (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) definierar de villkor som måste finnas för det här objektet i listan som ska användas.

[Etikettera Element för ListItem för ListControl(Format)](./label-element-for-listitem-for-listcontrol-format.md) Anger etiketten för värdet för egenskapen eller skript på raden.

[Etikettera Element för GroupBy (Format)](./label-element-for-groupby-format.md) anger en etikett som visas när en ny grupp har påträffats.

[Etikettera Element för TableColumnHeader (Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) definierar den etikett som visas överst i en kolumn.

[LeftIndent Element för ramens för kontroller för konfiguration (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) anger hur många tecken som data ska flyttas från vänster marginal. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[LeftIndent Element av kontrollerna för Visa (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md) anger hur många tecken som data ska flyttas från vänster marginal. Det här elementet används när du definierar kontroller som kan användas av en vy.

[LeftIndent Element för ramens för anpassad kontroll för vy (Format)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) anger hur många tecken som data ska flyttas från vänster marginal. Det här elementet används när du definierar en anpassad kontroll vy.

[LeftIndent Element för ramens för GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md) anger hur många tecken som data ska flyttas från vänster marginal. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[ListControl Element (Format)](./listcontrol-element-format.md) definierar ett listformat för vyn.

[ListEntry Element (Format)](./listentry-element-for-listcontrol-format.md) innehåller en definition av listvyn.

[ListEntries Element (Format)](./listentries-element-for-listcontrol-format.md) definierar hur raderna i listvyn visas.

[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md) definierar egenskapen eller skript som vars värde visas i en rad i listvyn.

[ListItems som finns Element (Format)](./listitems-element-for-listentry-for-listcontrol-format.md) egenskaper och skript som visas i listvyn.

[Namn på Element för kontroll för kontroller för konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md) anger namnet på kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[Namn på Element för SelectionSet (Format)](./name-element-for-selectionset-format.md) anger namnet som refererar till uppsättningen val.

[Namn på Element för Visa (Format)](./name-element-for-view-format.md) anger namnet som används för att identifiera vyn.

[Ny rad-Element för CustomItem för kontroller för konfiguration (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md) lägger till en tom rad i visningen av kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[Ny rad-Element för CustomItem för kontroller för att visa (Format)](./newline-element-for-customitem-for-controls-for-view-format.md) lägger till en tom rad i visningen av kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[Ny rad-Element för CustomItem för anpassad kontroll för vy (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) lägger till en tom rad i visningen av kontrollen. Det här elementet används när du definierar en anpassad kontroll vy.

[Ny rad-Element för CustomItem för GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md) lägger till en tom rad i visningen av kontrollen. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[PropertyName-Element för ExpressionBinding för kontroller för konfiguration (Format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) anger egenskapen .NET vars värde visas som vanliga kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[PropertyName-Element för ExpressionBinding för kontroller för att visa (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) anger egenskapen .NET vars värde visas i kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[PropertyName-Element för ExpressionBinding för anpassad kontroll för vy (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) anger egenskapen .NET vars värde visas i kontrollen. Det här elementet används när du definierar en anpassad kontroll-vy

[PropertyName-Element för ExpressionBinding för GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md) anger egenskapen .NET vars värde visas i kontrollen. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[PropertyName-Element för GroupBy (Format)](./propertyname-element-for-groupby-format.md) anger egenskapen .NET som startar en ny grupp när dess värde ändras.

[PropertyName-Element för ItemSeclectionCondition för kontroller för konfiguration (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) anger egenskapen .NET som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och kontrollen används. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[PropertyName-Element för ItemSelectionCondition för kontroller för att visa (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) anger egenskapen .NET som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och kontrollen används. Det här elementet används när du definierar kontroller som kan användas av en vy.

[PropertyName-Element för ItemSelectionCondition för anpassad kontroll för vy (Format](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) anger egenskapen .NET som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och kontrollen används. Det här elementet används när du definierar en anpassad kontroll vy.

[PropertyName-Element för ItemSelectionCondition för GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) anger egenskapen .NET som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och kontrollen används. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[PropertyName-Element för ItemSelectionCondition för ListItem (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) anger egenskapen .NET som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och den används. Det här elementet används när du definierar en listvy.

[PropertyName-Element för ListItem för ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md) anger egenskapen .NET vars värde visas i listan.

[PropertyName-Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) anger egenskapen .NET som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och posten används. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[PropertyName-Element för SelectionCondition för kontroller för att visa (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) anger egenskapen .NET som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och posten används. Det här elementet används när du definierar kontroller som kan användas av en vy.

[PropertyName-Element för SelectionCondition för anpassad kontroll för vy (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) anger egenskapen .NET som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och definitionen används. Det här elementet används när du definierar en anpassad kontroll vy.

[PropertyName-Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) anger egenskapen .NET som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och definitionen används.

[PropertyName-Element för SelectionCondition för GroupBy (Format)](./propertyname-element-for-selectioncondition-for-groupby-format.md) anger egenskapen .NET som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och definitionen används. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[PropertyName-Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) anger egenskapen .NET som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och kortet används.

[PropertyName-Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) anger egenskapen .NET som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och tabellposten används.

[PropertyName-Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) anger egenskapen .NET som utlöser villkoret. När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och definitionen används.

[PropertyName-Element för TableColumnItem (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) anger egenskapen vars värde visas i kolumnen i raden.

[PropertyName-Element för WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md) anger egenskapen för objektet vars värde visas i bred vy.

[RightIndent Element för ramens för kontroller för konfiguration (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) anger hur många tecken som data ska flyttas från höger marginal. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[RightIndent Element av kontrollerna för Visa (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md) anger hur många tecken som data ska flyttas från höger marginal. Det här elementet används när du definierar kontroller som kan användas av en vy.

[RightIndent elementet](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) anger hur många tecken som data ska flyttas från höger marginal. Det här elementet används när du definierar en anpassad kontroll vy.

[RightIndent Element för ramens för GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md) anger hur många tecken som data ska flyttas från höger marginal. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[ScriptBlock Element för ExpressionBinding för kontroller för konfiguration (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) anger skriptet vars värde visas som vanliga kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[ScriptBlock Element för ExpressionBinding för kontroller för att visa (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) anger skriptet vars värde visas i kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[ScriptBlock Element för ExpressionBinding för CustomCustomControl för vy (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) anger skriptet vars värde visas i kontrollen. Det här elementet används när du definierar en anpassad kontroll vy.

[ScriptBlock Element för ExpressionBinding för GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md) anger skriptet vars värde visas i kontrollen. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[ScriptBlock Element för GroupBy (Format)](./scriptblock-element-for-groupby-format.md) anger det skript som startar en ny grupp när dess värde ändras.

[ScriptBlock Element för ItemSelectionCondition för kontroller för konfiguration (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) anger det skript som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och kontrollen används. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[ScriptBlock Element för ItemSelectionCondition för kontroller för att visa (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) anger det skript som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och kontrollen används. Det här elementet används när du definierar kontroller som kan användas av en vy.

[ScriptBlock Element för ItemSelectionCondition för anpassad kontroll för vy (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) anger det skript som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och kontrollen används. Det här elementet används när du definierar en anpassad kontroll vy.

[ScriptBlock Element för ItemSelectionCondition för GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) anger det skript som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och kontrollen används. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[ScriptBlock Element för ItemSelectionCondition för ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) anger det skript som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och listobjektet används. Det här elementet används när du definierar en listvy.

[ScriptBlock Element för ListItem (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md) anger skriptet vars värde visas i raden i listan.

[ScriptBlock Element för SelectionCondition för kontroller för konfiguration (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) anger det skript som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och definitionen används. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[ScriptBlock Element för SelectionCondition för kontroller för att visa (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) anger det skript som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och definitionen används. Det här elementet används när du definierar kontroller som kan användas av en vy.

[ScriptBlock Element för SelectionCondition för anpassad kontroll för vy (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) anger det skript som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och definitionen används. Det här elementet används när du definierar en anpassad kontroll vy.

[ScriptBlock Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) anger det skript som utlöser villkoret.

[ScriptBlock Element för SelectionCondition för GroupBy (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) anger det skript som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och definitionen används. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[ScriptBlock Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) anger det skript som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och kortet används.

[ScriptBlock Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) anger skriptblocket som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och tabellposten används.

[ScriptBlock Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) anger det skript som utlöser villkoret. När det här skriptet ska utvärderas till `true`villkoret uppfylls och definitionen för bred posten används.

[ScriptBlock Element för TableColumnItem (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) anger skriptet vars värde visas i kolumnen i raden.

[ScriptBlock Element för WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) anger skriptet vars värde visas i bred vy.

[SelectionCondition Element för EntrySelectedBy för CustomEntry för konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) definierar ett villkor som måste finnas för en gemensam kontrolldefinition som ska användas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[SelectionCondition Element för EntrySelectedBy för kontroller för att visa (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) definierar ett villkor som måste finnas för kontrolldefinition som ska användas. Det här elementet används när du definierar kontroller som kan användas av en vy.

[SelectionCondition Element för EntrySelectedBy för anpassad kontroll för vy (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) definierar ett villkor som måste finnas en definition för kontrollen som ska användas. Det här elementet används när du definierar en anpassad kontroll vy.

[SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) definierar de villkor som måste finnas för att expandera samlingen objekt av den här definitionen.

[SelectionCondition Element för EntrySelectedBy för GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) definierar ett villkor som måste finnas en definition för kontrollen som ska användas. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[SelectionCondition Element för EntrySelectedBy för ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) definierar de villkor som måste finnas för att använda den här definitionen i listvyn. Det finns ingen gräns för hur många val av villkor som kan anges för en definition av listan.

[SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) definierar de villkor som måste finnas för att använda för den här definitionen av tabellvyn. Det finns ingen gräns för hur många val av villkor som kan anges för en tabelldefinition.

[SelectionCondition Element för EntrySelectedBy för WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) definierar de villkor som måste finnas för den här definitionen som ska användas. Det finns ingen gräns för hur många val av villkor som kan anges för en bred post-definition.

[SelectionSet Element (Format)](./selectionset-element-format.md) definierar en uppsättning .NET-objekt som kan refereras av namnet på uppsättningen.

[SelectionSetName Element för EntrySelectedBy för kontroller för konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) anger en uppsättning med .NET-typer som använder den här definitionen för kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[SelectionSetName Element för EntrySelectedBy för kontroller för att visa (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) anger en uppsättning med .NET-typer som använder den här definitionen för kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[SelectionSetName Element för EntrySelectedBy för CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) anger en uppsättning med .NET-objekt för posten. Det finns ingen gräns för hur många uppsättningar för val av som kan anges för en post.

[SelectionSetName Element för EntrySelectedBy för EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) anger uppsättning med .NET-typer som byggs med den här definitionen.

[SelectionSetName Element för EntrySelectedBy för GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) anger en uppsättning med .NET-objekt för posten. Det finns ingen gräns för hur många uppsättningar för val av som kan anges för en post. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[SelectionSetName Element för EntrySelectedBy för ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) anger en uppsättning med .NET-objekt för posten. Det finns ingen gräns för hur många uppsättningar för val av som kan anges för en post.

[SelectionSetName Element för EntrySelectedBy för TableRowEntry (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) anger en uppsättning .NET skriver att använda den här posten i tabellvyn. Det finns ingen gräns för hur många uppsättningar för val av som kan anges för en post.

[SelectionSetName Element för EntrySelectedBy för WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) anger en uppsättning med .NET-objekt för definitionen. Definitionen används när en av de här objekten visas.

[SelectionSetName Element för SelectionCondition för kontroller för konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) anger uppsättning med .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns villkoret uppfylls och objektet visas med hjälp av den här kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[SelectionSetName Element för SelectionCondition för kontroller för att visa (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) anger uppsättning med .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns villkoret uppfylls och objektet visas med hjälp av den här kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[EntrySelectedBy Element för CustomEntry för vy (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) anger uppsättning med .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns villkoret uppfylls och objektet visas med hjälp av den här kontrollen. Det här elementet används när du definierar en anpassad kontroll vy.

[SelectionSetName Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) anger uppsättning med .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns är villkoret uppfyllt.

[SelectionSetName Element för SelectionCondition för GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) anger uppsättning med .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns villkoret uppfylls och objektet visas med hjälp av den här kontrollen. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[SelectionSetName Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) anger uppsättning med .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns villkoret uppfylls och objektet visas med hjälp av den här definitionen i listvyn.

[SelectionSetName Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) anger uppsättning med .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns villkoret uppfylls och objektet visas med hjälp av den här definitionen av tabellvyn.

[SelectionSetName Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) anger uppsättning med .NET-typer som utlöser villkoret. När någon av typerna i den här uppsättningen finns villkoret uppfylls och objektet visas med hjälp av den här definitionen av bred vy.

[SelectionSetName Element för ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md) anger en uppsättning med .NET-objekt som visas i vyn.

[SelectionSets Element (Format)](./selectionsets-element-format.md) definierar uppsättningar med .NET-objekt som kan användas av enskilda format vyer.

[ShowError-Element (Format)](./showerror-element-format.md) anger att en fullständig Felpost visas när ett fel uppstår medan du visar en typ av data.

[TableColumnHeader Element för TableHeaders för TableControl (Format)](./tablecolumnheader-element-format.md) definierar etiketten, bredden på kolumnen och justering för etiketten för en kolumn i tabellen.

[TableColumnItem Element (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) definierar egenskapen eller skript som vars värde visas i kolumnen i raden.

[TableColumnItems Element (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) definierar de egenskaper eller skript som vars värden visas i raden.

[TableControl Element (Format)](./tablecontrol-element-format.md) definierar ett tabellformat för en vy.

[TableHeaders Element (Format)](./tableheaders-element-format.md) definierar rubriker för kolumner i en tabell.

[TableRowEntries Element (Format)](./tablerowentries-element-for-tablecontrol-format.md) definierar raderna i tabellen.

[TableRowEntry Element (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) definierar de data som visas i en rad i tabellen.

[Textelement för CustomItem för kontroller för konfiguration (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md) anger text som läggs till i de data som visas av kontroll, till exempel en etikett, hakparenteser för att skriva data och blanksteg dra in data. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[Textelement för CustomItem för kontroller för att visa (Format)](./text-element-for-customitem-for-controls-for-view-format.md) anger text som läggs till i de data som visas av kontroll, till exempel en etikett, hakparenteser för att skriva data och blanksteg dra in data. Det här elementet används när du definierar kontroller som kan användas av en vy.

[Textelement för CustomItem (Format)](./text-element-for-customitem-for-customview-for-view-format.md) anger text som läggs till i de data som visas av kontroll, till exempel en etikett, hakparenteser för att skriva data och blanksteg dra in data. Det här elementet används när du definierar en anpassad kontroll vy.

[Textelement för CustomItem för GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md) anger text som läggs till i de data som visas av kontroll, till exempel en etikett, hakparenteser för att skriva data och blanksteg dra in data. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[TypeName-Element för EntrySelectedBy för kontroller för konfiguration (Format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) anger ett .NET-typ som använder den här definitionen för kontrollen. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[TypeName-Element för EntrySelectedBy för kontroller för att visa (Format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md) anger ett .NET-typ som använder den här definitionen för kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

[TypeName-Element för EntrySelectedBy för CustomEntry för vy (Format)](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) anger ett .NET-typ som använder den här definitionen av vyn anpassad kontroll. Det finns ingen gräns för hur många typer som kan anges för en Definitionsuppdatering.

[TypeName-Element för EntrySelectedBy för EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) anger en .NET-typ som utökas av denna definition. Det här elementet används när du definierar en standardinställningarna.

[TypeName-Element för EntrySelectedBy för GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md) anger ett .NET-typ som använder den här definitionen av den anpassade kontrollen. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[TypeName-Element för EntrySelectedBy för ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md) anger ett .NET-typ som använder den här posten i listvyn. Det finns ingen gräns för hur många typer som kan anges för en listpost.

[TypeName-Element för EntrySelectedBy för TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md) anger ett .NET-typ som använder den här posten i tabellvyn. Det finns ingen gräns för hur många typer som kan anges för en post.

[TypeName-Element för EntrySelectedBy för WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md) anger en .NET-typ för definitionen. Definitionen används när det här objektet visas.

[TypeName-Element för SelectionCondition för kontroller för konfiguration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) anger ett .NET-typ som utlöser villkoret. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

[TypeName-Element för SelectionCondition för kontroller för att visa (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) anger ett .NET-typ som utlöser villkoret. Det här elementet används när du definierar kontroller som kan användas av en vy.

[TypeName-Element för SelectionCondition för anpassad kontroll för vy (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) anger ett .NET-typ som utlöser villkoret. Det här elementet används när du definierar en anpassad kontroll vy.

[TypeName-Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) anger ett .NET-typ som utlöser villkoret.

[TypeName-Element för SelectionCondition för GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md) anger ett .NET-typ som utlöser villkoret. Det här elementet används när du definierar hur en ny grupp med objekt visas.

[TypeName-Element för SelectionCondition för EntrySelectedBy för ListControl (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) anger ett .NET-typ som utlöser villkoret. Om den här typen finns används posten.

[TypeName-Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) anger ett .NET-typ som utlöser villkoret. Om den här typen finns villkoret uppfylls och tabellraden används.

[TypeName-Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) anger ett .NET-typ som utlöser villkoret. Om den här typen finns används definitionen.

[TypeName-Element för typer (Format)](./typename-element-for-types-format.md) anger .NET-typ för ett objekt som hör till val av uppsättningen.

[TypeName-Element för ViewSelectedBy (Format)](./typename-element-for-viewselectedby-format.md) anger ett .NET-objekt som visas i vyn.

[Datatyper Element (Format)](./types-element-for-selectionset-format.md) definierar de .NET-objekt som är i urvalet inställda.

[Visa Element (Format)](./view-element-format.md) definierar en vy som används för att visa en eller flera .NET-objekt.

[ViewDefinitions Element (Format)](./viewdefinitions-element-format.md) definierar de vyer som används för att visa objekt.

[ViewSelectedBy Element (Format)](./viewselectedby-element-format.md) definierar de .NET-objekt som visas i vyn.

[WideControl Element (Format)](./widecontrol-element-format.md) definierar en lista över hela (enstaka värde)-format för vyn. Den här vyn visar ett enda egenskapsvärdet eller skriptvärde för varje objekt.

[WideEntries Element (Format)](./wideentries-element-for-widecontrol-format.md) innehåller definitionerna av bred vy. Bred vy måste ange en eller flera definitioner.

[WideEntry Element (Format)](./wideentry-element-for-widecontrol-format.md) innehåller en definition av bred vy.

[WideItem Element (Format)](./wideitem-element-for-widecontrol-format.md) definierar egenskapen eller skript som vars värde visas.

[Bredd-Element (Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) anger bredden (i antal tecken) för en kolumn.

[Omsluta Element (Format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) anger att text som överskrider kolumnbredden visas på nästa rad.

[WrapTables Element (Format)](./wraptables-element-format.md) anger att data i en tabellcell flyttas till nästa rad om data är längre än bredden på kolumnen.

## <a name="see-also"></a>Se även

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
