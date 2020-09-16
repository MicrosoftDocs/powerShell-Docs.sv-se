---
title: Skapa en listvy | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 24eb673e0db011a1439fa5ba1f2966fcc3bdc338
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783780"
---
# <a name="creating-a-list-view"></a>Skapa en listvy

En listvy visar data i en enskild kolumn (i ordningsföljd). De data som visas i listan kan vara värdet för en .NET-egenskap eller ett skripts värde.

## <a name="a-list-view-display"></a>Visa en listvy

Följande utdata visar hur Windows PowerShell visar egenskaperna för [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt som returneras av [Get-service](/powershell/module/microsoft.powershell.management/get-service) -cmdleten. I det här exemplet returnerades tre objekt, där varje objekt skiljs från föregående objekt med en tom rad.

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

Följande XML visar schemat för List visning för att visa flera egenskaper för [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt. Du måste ange varje egenskap som du vill ska visas i listvyn.

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

- Elementet [View](./view-element-format.md) är det överordnade elementet i list visningen. (Detta är samma överordnade element för vyerna tabell, bred och anpassad kontroll.)

- Elementet [Name](./name-element-for-view-format.md) anger namnet på vyn. Det här elementet krävs för alla vyer.

- [ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar de objekt som använder vyn. Det här elementet är obligatoriskt.

- Elementet [groupby](./groupby-element-for-view-format.md) definierar när en ny grupp av objekt visas. En ny grupp startas när värdet för en speciell egenskap eller skript ändras. Det här elementet är valfritt.

- Elementet [Controls](./controls-element-for-view-format.md) definierar de anpassade kontroller som definieras av list visningen. Kontrollerna ger dig ett sätt att ytterligare ange hur data ska visas. Det här elementet är valfritt. En vy kan definiera egna anpassade kontroller, eller så kan den använda vanliga kontroller som kan användas av vilken vy som helst i format filen. Mer information om anpassade kontroller finns i [skapa anpassade kontroller](./creating-custom-controls.md).

- [ListControl](./listcontrol-element-format.md) -elementet definierar vad som visas i vyn och hur det formateras. På samma sätt som för alla andra vyer kan en listvy Visa värdena för objekt egenskaper eller värden som genereras av skript.

Ett exempel på en hel format fil som definierar en enkel listvy finns i [listvyn (grundläggande)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Tillhandahålla definitioner för listvyn

Listvyer kan tillhandahålla en eller flera definitioner genom att använda de underordnade elementen i [ListControl](./listcontrol-element-format.md) -elementet. En vy är vanligt vis bara en definition. I följande exempel tillhandahåller vyn en enda definition som visar flera egenskaper för [system. Diagnostics. process? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) -objekt. En listvy kan visa värdet för en egenskap eller ett skripts värde (visas inte i exemplet).

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

Följande XML-element kan användas för att tillhandahålla definitioner för en listvy:

- [ListControl](./listcontrol-element-format.md) -elementet och dess underordnade element definierar vad som visas i vyn.

- [ListEntries](./listentries-element-for-listcontrol-format.md) -elementet innehåller definitionerna för vyn. I de flesta fall har en vy bara en definition. Det här elementet är obligatoriskt.

- [ListEntry](./listentry-element-for-listcontrol-format.md) -elementet ger en definition av vyn. Minst en [ListEntry](./listentry-element-for-listcontrol-format.md) krävs. Det finns dock ingen övre gräns för antalet element som du kan lägga till. I de flesta fall har en vy bara en definition.

- [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -elementet anger de objekt som visas av en bestämd definition. Det här elementet är valfritt och behövs bara när du definierar flera [ListEntry](./listentry-element-for-listcontrol-format.md) -element som visar olika objekt.

- [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) -elementet anger de egenskaper och skript vars värden visas i raderna i listvyn.

- [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) -elementet anger en egenskap eller ett skript vars värde visas i en rad i list visningen. En listvy måste ange minst en egenskap eller ett skript. Det finns ingen övre gräns för antalet rader som kan anges.

- Elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) anger den egenskap vars värde visas i raden. Du måste ange antingen en egenskap eller ett skript, men du kan inte ange båda.

- [Script block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -elementet anger det skript vars värde visas i raden. Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.

- Elementet [Label](./label-element-for-listitem-for-listcontrol-format.md) anger etiketten som visas till vänster om egenskapen eller skriptets värde i raden. Det här elementet är valfritt. Om en etikett inte anges visas namnet på egenskapen eller skriptet. Ett fullständigt exempel finns i [listvyn (etiketter)](./list-view-labels.md).

- [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) -elementet anger ett villkor som måste finnas för att raden ska visas. Mer information om hur du lägger till villkor i listvyn finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md). Det här elementet är valfritt.

- Elementet [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) anger ett mönster som används för att visa värdet för egenskapen eller skriptet. Det här elementet är valfritt.

Ett exempel på en hel format fil som definierar en enkel listvy finns i [listvyn (grundläggande)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Definiera de objekt som använder list visningen

Det finns två sätt att definiera vilka .NET-objekt som ska använda List visningen. Du kan använda [ViewSelectedBy](./viewselectedby-element-format.md) -elementet för att definiera de objekt som kan visas av alla definitioner i vyn, eller så kan du använda elementet [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) för att definiera vilka objekt som visas med en bestämd definition av vyn. I de flesta fall har en vy bara en definition, så objekt definieras vanligt vis av [ViewSelectedBy](./viewselectedby-element-format.md) -elementet.

I följande exempel visas hur du definierar de objekt som visas i list visningen med hjälp av elementen [ViewSelectedBy](./viewselectedby-element-format.md) och [TypeName](./typename-element-for-viewselectedby-format.md) . Det finns ingen gräns för antalet element i [TypeName](./typename-element-for-viewselectedby-format.md) som du kan ange, och deras ordning är inte signifikant.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Följande XML-element kan användas för att ange de objekt som används av list visningen:

- [ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar vilka objekt som visas i list visningen.

- Elementet [TypeName](./typename-element-for-viewselectedby-format.md) anger det .net-objekt som visas i vyn. Fullständigt kvalificerat .NET-typnamn måste anges. Du måste ange minst en typ eller urvals uppsättning för vyn, men det finns inget maximalt antal element som kan anges.

Ett exempel på en hel format fil finns i [listvyn (grundläggande)](./list-view-basic.md).

I följande exempel används elementen [ViewSelectedBy](./viewselectedby-element-format.md) och [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) . Använd markerings uppsättningar där du har en relaterad uppsättning objekt som visas med flera vyer, till exempel när du definierar en listvy och en tabellvy för samma objekt. Mer information om hur du skapar en urvals uppsättning finns i [definiera urvals uppsättningar](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Följande XML-element kan användas för att ange de objekt som används av list visningen:

- [ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar vilka objekt som visas i list visningen.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -elementet anger en uppsättning objekt som kan visas i vyn. Du måste ange minst en markerings uppsättning eller typ för vyn, men det finns inget maximalt antal element som kan anges.

I följande exempel visas hur du definierar de objekt som visas av en bestämd definition av list visningen med hjälp av [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -elementet. Med det här elementet kan du ange objektets .NET-typnamn, en urvals uppsättning objekt eller ett markerings villkor som anger när definitionen används. Mer information om hur du skapar ett urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

Följande XML-element kan användas för att ange de objekt som används av en bestämd definition av listvyn:

- [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -elementet definierar vilka objekt som visas av definitionen.

- Elementet [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) anger det .net-objekt som visas av definitionen. När du använder det här elementet krävs det fullständigt kvalificerade .NET-typ namnet. Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) -elementet (visas inte) anger en uppsättning objekt som kan visas av den här definitionen. Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) -elementet (visas inte) anger ett villkor som måste finnas för att den här definitionen ska kunna användas. Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges. Mer information om hur du definierar urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Visa grupper av objekt i en listvy

Du kan separera de objekt som visas i list visningen i grupper. Det innebär inte att du definierar en grupp, bara att Windows PowerShell startar en ny grupp när värdet för en speciell egenskap eller skript ändras. I följande exempel startas en ny grupp när värdet för egenskapen [system. serviceprocess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) ändras.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Följande XML-element används för att definiera när en grupp startas:

- Elementet [groupby](./groupby-element-for-view-format.md) definierar egenskapen eller skriptet som startar den nya gruppen och definierar hur gruppen visas.

- Elementet [PropertyName](./propertyname-element-for-groupby-format.md) anger den egenskap som startar en ny grupp när dess värde ändras. Du måste ange en egenskap eller ett skript för att starta gruppen, men du kan inte ange båda.

- [Script block](./scriptblock-element-for-groupby-format.md) -elementet anger det skript som startar en ny grupp när dess värde ändras. Du måste ange ett skript eller en egenskap för att starta gruppen, men du kan inte ange båda.

- Elementet [Label](./label-element-for-groupby-format.md) definierar en etikett som visas i början av varje grupp. Utöver den text som anges av det här elementet visar Windows PowerShell värdet som utlöste den nya gruppen och lägger till en tom rad före och efter etiketten. Det här elementet är valfritt.

- [CustomControl](./customcontrol-element-for-groupby-format.md) -elementet definierar en kontroll som används för att visa data. Det här elementet är valfritt.

- [CustomControlName](./customcontrolname-element-for-groupby-format.md) -elementet anger en common-eller View-kontroll som används för att visa data. Det här elementet är valfritt.

Ett exempel på en hel format fil som definierar grupper finns i [listvyn (groupby)](./list-view-groupby.md).

## <a name="using-format-strings"></a>Använda format strängar

Du kan lägga till format strängar i en vy för att ytterligare definiera hur data visas. I följande exempel visas hur du definierar en format sträng för `StartTime` egenskapens värde.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

Följande XML-element kan användas för att ange ett format mönster:

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -elementet anger de data som visas i vyn.

- Elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) anger den egenskap vars värde visas i vyn. Du måste ange antingen en egenskap eller ett skript, men du kan inte ange båda.

- [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) -elementet anger ett format mönster som definierar hur egenskapen eller skriptets värde visas i vyn.

- [Script block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -elementet (visas inte) anger det skript vars värde visas i vyn. Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.

I följande exempel `ToString` kallas metoden för att formatera skriptets värde. Skript kan anropa vilken metod som helst av ett objekt. Om ett objekt har en metod, till exempel `ToString` , som har format parametrar, kan skriptet anropa metoden för att formatera utdata för skriptet.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Följande XML-element kan användas för att anropa- `ToString` metoden:

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -elementet anger de data som visas i vyn.

- [Script block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -elementet (visas inte) anger det skript vars värde visas i vyn. Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
