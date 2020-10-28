---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa en bred vy
description: Skapa en bred vy
ms.openlocfilehash: 4230ef91a3612e962b2773b12e8016df6f760eae
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655612"
---
# <a name="creating-a-wide-view"></a>Skapa en bred vy

En bred vy visar ett enda värde för varje objekt som visas. Det visade värdet kan vara värdet för en .NET-objekt egenskap eller ett skripts värde. Som standard finns det ingen etikett eller rubrik för den här vyn.

## <a name="a-wide-view-display"></a>En bred vy-skärm

I följande exempel visas hur Windows PowerShell visar objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) som returneras av cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) när dess utdata är skickas till den [format breda](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdleten. (Som standard returnerar cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en tabellvy.) I det här exemplet används de två kolumnerna för att visa namnet på processen för varje returnerat objekt. Namnet på objektets egenskap visas inte, bara egenskapens värde.

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a>Definiera den breda vyn

Följande XML visar wide View-schemat för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

Följande XML-element används för att definiera en bred vy:

- Elementet [View](./view-element-format.md) är det överordnade elementet i den breda vyn. (Detta är samma överordnade element för vyerna tabell, lista och anpassad kontroll.)

- Elementet [Name](./name-element-for-view-format.md) anger namnet på vyn. Det här elementet krävs för alla vyer.

- [ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar de objekt som använder vyn. Det här elementet är obligatoriskt.

- Elementet [groupby](./groupby-element-for-view-format.md) definierar när en ny grupp av objekt visas. En ny grupp startas när värdet för en speciell egenskap eller skript ändras. Det här elementet är valfritt.

- [Kontroll](./controls-element-for-view-format.md) elementen definierar de anpassade kontroller som definieras av den breda vyn. Kontrollerna ger dig ett sätt att ytterligare ange hur data ska visas. Det här elementet är valfritt. En vy kan definiera egna anpassade kontroller, eller så kan den använda vanliga kontroller som kan användas av vilken vy som helst i format filen. Mer information om anpassade kontroller finns i [skapa anpassade kontroller](./creating-custom-controls.md).

- [WideControl](./widecontrol-element-format.md) -elementet och dess underordnade element definierar vad som visas i vyn. I föregående exempel är vyn utformad för att visa egenskapen [system. Diagnostics. process. processname](/dotnet/api/System.Diagnostics.Process.ProcessName) .

Ett exempel på en hel format fil som definierar en enkel bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Tillhandahålla definitioner för din bred vy

Breda vyer kan tillhandahålla en eller flera definitioner genom att använda de underordnade elementen i [WideControl](./widecontrol-element-format.md) -elementet. En vy är vanligt vis bara en definition. I följande exempel tillhandahåller vyn en enda definition som visar värdet för egenskapen [system. Diagnostics. process. processname](/dotnet/api/System.Diagnostics.Process.ProcessName) . En bred vy kan visa värdet för en egenskap eller ett skripts värde (visas inte i exemplet).

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

Följande XML-element kan användas för att tillhandahålla definitioner för en bred vy:

- [WideControl](./widecontrol-element-format.md) -elementet och dess underordnade element definierar vad som visas i vyn.

- Elementet [AutoSize](./autosize-element-for-widecontrol-format.md) anger om kolumn storleken och antalet kolumner justeras baserat på data storleken. Det här elementet är valfritt.

- [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) -elementet anger antalet kolumner som visas i den breda vyn. Det här elementet är valfritt.

- [WideEntries](./wideentries-element-for-widecontrol-format.md) -elementet innehåller definitionerna för vyn. I de flesta fall har en vy bara en definition. Det här elementet är obligatoriskt.

- [WideEntry](./wideentry-element-for-widecontrol-format.md) -elementet ger en definition av vyn. Minst en [WideEntry](./wideentry-element-for-widecontrol-format.md) krävs. Det finns dock ingen övre gräns för antalet element som du kan lägga till. I de flesta fall har en vy bara en definition.

- [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) -elementet anger de objekt som visas av en bestämd definition. Det här elementet är valfritt och behövs bara när du definierar flera [WideEntry](./wideentry-element-for-widecontrol-format.md) -element som visar olika objekt.

- [WideItem](./wideitem-element-for-widecontrol-format.md) -elementet anger de data som visas i vyn. Till skillnad från andra typer av vyer kan en bred kontroll bara visa ett objekt.

- Elementet [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) anger den egenskap vars värde visas i vyn. Du måste ange antingen en egenskap eller ett skript, men du kan inte ange båda.

- [Script block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -elementet anger det skript vars värde visas i vyn. Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.

- Elementet [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) anger ett mönster som används för att visa data. Det här elementet är valfritt.

Ett exempel på en hel format fil som definierar en bred visnings definition finns i [wide View (grundläggande)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>Definiera de objekt som använder wide View

Det finns två sätt att definiera vilka .NET-objekt som använder wide-vyn. Du kan använda [ViewSelectedBy](./viewselectedby-element-format.md) -elementet för att definiera de objekt som kan visas av alla definitioner i vyn, eller så kan du använda elementet [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) för att definiera vilka objekt som visas med en bestämd definition av vyn. I de flesta fall har en vy bara en definition, så objekt definieras vanligt vis av [ViewSelectedBy](./viewselectedby-element-format.md) -elementet.

I följande exempel visas hur du definierar de objekt som visas i den breda vyn med hjälp av elementen [ViewSelectedBy](./viewselectedby-element-format.md) och [TypeName](./typename-element-for-viewselectedby-format.md) . Det finns ingen gräns för antalet element i [TypeName](./typename-element-for-viewselectedby-format.md) som du kan ange, och deras ordning är inte signifikant.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Följande XML-element kan användas för att ange de objekt som används i den breda vyn:

- [ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar vilka objekt som visas i den breda vyn.

- Elementet [TypeName](./typename-element-for-viewselectedby-format.md) anger det .net som visas i vyn. Fullständigt kvalificerat .NET-typnamn måste anges. Du måste ange minst en typ eller urvals uppsättning för vyn, men det finns inget maximalt antal element som kan anges.

Ett exempel på en hel format fil finns i [wide View (grundläggande)](./wide-view-basic.md).

I följande exempel används elementen [ViewSelectedBy](./viewselectedby-element-format.md) och [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) . Använd markerings uppsättningar där du har en relaterad uppsättning objekt som visas med flera vyer, till exempel när du definierar en bred vy och en tabellvy för samma objekt. Mer information om hur du skapar en urvals uppsättning finns i [definiera urvals uppsättningar](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Följande XML-element kan användas för att ange de objekt som används i den breda vyn:

- [ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar vilka objekt som visas i den breda vyn.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -elementet anger en uppsättning objekt som kan visas i vyn. Du måste ange minst en markerings uppsättning eller typ för vyn, men det finns inget maximalt antal element som kan anges.

I följande exempel visas hur du definierar de objekt som visas av en bestämd definition av den breda vyn med hjälp av [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) -elementet. Med det här elementet kan du ange objektets .NET-typnamn, en urvals uppsättning objekt eller ett markerings villkor som anger när definitionen används. Mer information om hur du skapar ett urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

Följande XML-element kan användas för att ange de objekt som används av en bestämd definition av den breda vyn:

- [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) -elementet definierar vilka objekt som visas av definitionen.

- Elementet [TypeName](./typename-element-for-viewselectedby-format.md) anger det .net som visas av definitionen. När du använder det här elementet krävs fullständigt kvalificerat .NET-typnamn. Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -elementet (visas inte) anger en uppsättning objekt som kan visas av den här definitionen. Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) -elementet (visas inte) anger ett villkor som måste finnas för att den här definitionen ska kunna användas. Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges. Mer information om hur du definierar urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Visa grupper av objekt i en bred vy

Du kan separera de objekt som visas i den breda vyn i grupper. Det innebär inte att du definierar en grupp, bara att Windows PowerShell startar en ny grupp när värdet för en speciell egenskap eller skript ändras. I följande exempel startas en ny grupp när värdet för egenskapen [system. serviceprocess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) ändras.

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

Ett exempel på en hel format fil som definierar grupper finns i [wide View (groupby)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>Använda format strängar

Format strängar kan läggas till i en bred vy för att ytterligare definiera hur data visas. I följande exempel visas hur du definierar en format sträng för `StartTime` egenskapens värde.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

Följande XML-element kan användas för att ange ett format mönster:

- [WideItem](./wideitem-element-for-widecontrol-format.md) -elementet anger de data som visas i vyn.

- Elementet [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) anger den egenskap vars värde visas i vyn. Du måste ange antingen en egenskap eller ett skript, men du kan inte ange båda.

- [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) -elementet anger ett format mönster som definierar hur egenskapen eller skriptets värde visas i vyn

- [Script block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -elementet (visas inte) anger det skript vars värde visas i vyn. Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.

I följande exempel `ToString` kallas metoden för att formatera skriptets värde. Skript kan anropa vilken metod som helst av ett objekt. Om ett objekt har en metod, till exempel `ToString` , som har format parametrar, kan skriptet anropa metoden för att formatera utdata för skriptet.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

Följande XML-element kan användas för att anropa- `ToString` metoden:

- [WideItem](./wideitem-element-for-widecontrol-format.md) -elementet anger de data som visas i vyn.

- [Script block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -elementet (visas inte) anger det skript vars värde visas i vyn. Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.

## <a name="see-also"></a>Se även

[Bred vy (grundläggande)](./wide-view-basic.md)

[Bred vy (gruppbaserad)](./wide-view-groupby.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
