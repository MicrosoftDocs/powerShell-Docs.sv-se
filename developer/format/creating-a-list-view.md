---
title: Skapa en listvy | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066863"
---
# <a name="creating-a-list-view"></a>Skapa en listvy

En listvy visar data i en enda kolumn (i sekventiell ordning). Data som visas i listan kan vara värdet för en egenskap för .NET eller värdet för ett skript.

## <a name="a-list-view-display"></a>Visa en lista över vyn

Följande utdata visar hur Windows PowerShell visar egenskaperna för [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt som returneras av den [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. I det här exemplet är returnerades tre objekt, med varje objekt avgränsas från det föregående objektet med en tom rad.

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a>Definiera listvyn

Följande XML visas listan Visa schemat för att visa flera egenskaper för den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt. Du måste ange varje egenskap som du vill ska visas i listvyn.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

Följande XML-element används för att definiera en listvy:

- Den [visa](./view-element-format.md) elementet har det överordnade elementet i listvyn. (Detta är samma överordnade element för tabellen, bred och anpassade vyer.)

- Den [namn](./name-element-for-view-format.md) elementet anger namnet på vyn. Det här elementet krävs för alla vyer.

- Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar de objekt som använder vyn. Det här elementet krävs.

- Den [GroupBy](./groupby-element-for-view-format.md) elementet definierar när en ny grupp med objekt visas. En ny grupp har startats när värdet för en specifik egenskap eller ett skript ändras. Det här elementet är valfritt.

- Den [kontroller](./controls-element-for-view-format.md) elementet definierar de anpassade kontroller som definieras av listvyn. Kontroller ger dig ett sätt som specificerar hur data visas. Det här elementet är valfritt. En vy kan definiera egna anpassade kontroller eller använda vanliga kontroller som kan användas av alla vyer i filen formatering. Mer information om anpassade kontroller finns i [skapar anpassade kontroller](./creating-custom-controls.md).

- Den [ListControl](./listcontrol-element-format.md) elementet definierar vad som visas i vyn och hur den formateras. Precis som alla andra vyer, en listvy kan visa värdena för objektegenskaper eller värden som genererats av skriptet.

Ett exempel på en fullständig formatering fil som definierar en enkel lista vy finns i [listvyn (grundläggande)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Att tillhandahålla definitioner för din listvy

Listvyer kan tillhandahålla en eller flera definitioner med hjälp av de underordnade elementen i den [ListControl](./listcontrol-element-format.md) element. Vyn har vanligtvis bara en definition. I följande exempel visas vyn ger en enda definition som visar flera egenskaper för den [System.Diagnostics.Process? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objekt. En listvy kan visa värdet för en egenskap eller värdet för ett skript (visas inte i det här exemplet).

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

Följande XML-element kan användas för att ange definitioner för en listvy:

- Den [ListControl](./listcontrol-element-format.md) elementet och dess underordnade element definierar vad som visas i vyn.

- Den [ListEntries](./listentries-element-for-listcontrol-format.md) elementet innehåller definitioner av vyn. I de flesta fall har en vy endast en definition. Det här elementet krävs.

- Den [ListEntry](./listentry-element-for-listcontrol-format.md) elementet innehåller en definition för vyn. Minst en [ListEntry](./listentry-element-for-listcontrol-format.md) krävs, men det finns ingen högsta gräns för antalet element som du kan lägga till. I de flesta fall har en vy endast en definition.

- Den [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elementet anger de objekt som visas som en viss definition. Det här elementet är valfritt och krävs bara när du definierar flera [ListEntry](./listentry-element-for-listcontrol-format.md) element som visar olika objekt.

- Den [ListItems som finns](./listitems-element-for-listentry-for-listcontrol-format.md) elementet anger egenskaperna och skript vars värden visas i raderna i listvyn.

- Den [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) elementet anger en egenskap eller ett skript som vars värde visas i en rad i listvyn. En listvy måste ange minst en egenskap eller skript. Det finns ingen högsta gräns för hur många rader som kan anges.

- Den [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elementet anger egenskapen vars värde visas i raden. Du måste ange en egenskap eller ett skript, men du kan inte ange båda.

- Den [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elementet anger skriptet vars värde visas i raden. Du måste ange ett skript eller en egenskap, men du kan inte ange båda.

- Den [etikett](./label-element-for-listitem-for-listcontrol-format.md) elementet anger etiketten som visas till vänster om värdet för egenskapen eller skript på raden. Det här elementet är valfritt. Om en etikett inte anges visas namnet på egenskapen eller skriptet. Ett komplett exempel finns i [listvyn (etiketter)](./list-view-labels.md).

- Den [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) elementet anger ett villkor som måste finnas för raden som ska visas. Läs mer om att lägga till villkor listvyn [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md). Det här elementet är valfritt.

- Den [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elementet anger ett mönster som används för att visa värdet för egenskapen eller skript. Det här elementet är valfritt.

Ett exempel på en fullständig formatering fil som definierar en enkel lista vy finns i [listvyn (grundläggande)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Definiera de objekt som använder listvyn

Det finns två sätt att definiera vilka .NET-objekt använder listvyn. Du kan använda den [ViewSelectedBy](./viewselectedby-element-format.md) element för att definiera de objekt som kan visas av alla definitioner av vyn eller du kan använda den [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element för att definiera vilka objekt visas som en viss definition för vyn. I de flesta fall har endast en definition i en vy så objekt definieras vanligtvis av den [ViewSelectedBy](./viewselectedby-element-format.md) element.

I följande exempel visas hur du definierar de objekt som visas genom att visa listan med de [ViewSelectedBy](./viewselectedby-element-format.md) och [TypeName](./typename-element-for-viewselectedby-format.md) element. Det finns ingen gräns för hur många [TypeName](./typename-element-for-viewselectedby-format.md) element att du kan ange och deras inbördes ordning är inte särskilt stor.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Följande XML-element kan användas för att ange objekt som används av listvyn:

- Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar vilka objekt visas i listvyn.

- Den [TypeName](./typename-element-for-viewselectedby-format.md) elementet anger .NET-objekt som visas i vyn. Det fullständigt kvalificerade typnamnet .NET krävs. Du måste ange minst en typ eller val som angetts för vyn, men det finns inget högsta antal element som kan anges.

Ett exempel på en fullständig formatering fil, se [listvyn (grundläggande)](./list-view-basic.md).

I följande exempel används den [ViewSelectedBy](./viewselectedby-element-format.md) och [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element. Använd val av där du har en uppsättning objekt som visas med flera vyer, till exempel när du definierar en listvy och en tabellvy för samma objekt. Läs mer om hur du skapar en [definiera val av uppsättningar](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Följande XML-element kan användas för att ange objekt som används av listvyn:

- Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar vilka objekt visas i listvyn.

- Den [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementet anger en uppsättning objekt som kan visas i vyn. Du måste ange minst en markering set eller typ för vyn, men det finns inget högsta antal element som kan anges.

I följande exempel visas hur du definierar de objekt som visas av en viss definition av visa listan med de [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element. Med det här elementet kan ange du namnet på .NET objektet, val av flera objekt eller ett val av villkor som anger när definitionen används. Mer information om hur du skapar ett urval villkor finns i [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

Följande XML-element kan användas för att ange objekt som används av en viss definition av listvyn:

- Den [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elementet definierar vilka objekt visas i definitionen.

- Den [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elementet anger .NET-objekt som visas när definitionen. När du använder det här elementet krävs det fullständigt kvalificerade typnamnet för .NET. Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.

- Den [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (visas inte) anger en uppsättning objekt som kan visas av denna definition. Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.

- Den [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (visas inte) anger ett villkor som måste finnas för den här definitionen som ska användas. Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges. Läs mer om hur du definierar villkoren för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Visa grupper med objekt i en listvy

Du kan avgränsa de objekt som visas i listvyn i grupper. Detta innebär inte att du definierar en grupp, endast att Windows PowerShell startar en ny grupp när en specifik egenskap eller ett skript ändras. I följande exempel visas en ny grupp har startats när värdet för den [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) egenskapsändringar.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Följande XML-element används för att definiera när en grupp startas:

- Den [GroupBy](./groupby-element-for-view-format.md) elementet definierar egenskapen eller skript som startar den nya gruppen och definierar hur gruppen visas.

- Den [PropertyName](./propertyname-element-for-groupby-format.md) elementet anger den egenskap som startar en ny grupp när dess värde ändras. Du måste ange en egenskap eller ett skript för att starta gruppen, men du kan inte ange båda.

- Den [ScriptBlock](./scriptblock-element-for-groupby-format.md) elementet anger det skript som startar en ny grupp när dess värde ändras. Du måste ange ett skript eller en egenskap för att starta gruppen, men du kan inte ange båda.

- Den [etikett](./label-element-for-groupby-format.md) elementet definierar en etikett som visas i början av varje grupp. Förutom den text som anges av det här elementet, visar det värde som utlöste den nya gruppen och lägger till en tom rad före och efter etiketten i Windows PowerShell. Det här elementet är valfritt.

- Den [anpassad kontroll](./customcontrol-element-for-groupby-format.md) elementet definierar en kontroll som används för att visa data. Det här elementet är valfritt.

- Den [CustomControlName](./customcontrolname-element-for-groupby-format.md) elementet anger ett vanligt eller visa kontroll som används för att visa data. Det här elementet är valfritt.

Ett exempel på en fullständig formatering fil som definierar grupper finns i [listvyn (GroupBy)](./list-view-groupby.md).

## <a name="using-format-strings"></a>Med hjälp av formatsträngar

Formatering strängar kan läggas till en vy för att ytterligare definiera hur data visas. I följande exempel visas hur du definierar en formateringssträngen för värdet för den `StartTime` egenskapen.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

Följande XML-element kan användas för att ange ett:

- Den [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elementet anger de data som visas i vyn.

- Den [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elementet anger egenskapen vars värde visas i vyn. Du måste ange en egenskap eller ett skript, men du kan inte ange båda.

- Den [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elementet anger ett formatmönster som definierar hur värdet för egenskapen eller skript visas i vyn.

- Den [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (visas inte) anger skriptet vars värde visas i vyn. Du måste ange ett skript eller en egenskap, men du kan inte ange båda.

I följande exempel visas den `ToString` metoden anropas för att formatera värdet för skriptet. Skript kan anropa någon-metod för ett objekt. Därför, om ett objekt har en metod som `ToString`, som har formateringsparametrar, skriptet kan anropa metoden för att formatera utdatavärdet för skriptet.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Följande XML-element som kan användas för att anropa den `ToString` metoden:

- Den [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elementet anger de data som visas i vyn.

- Den [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (visas inte) anger skriptet vars värde visas i vyn. Du måste ange ett skript eller en egenskap, men du kan inte ange båda.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
