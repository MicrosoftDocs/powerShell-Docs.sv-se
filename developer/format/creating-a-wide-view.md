---
title: Skapa en bred vy | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066727"
---
# <a name="creating-a-wide-view"></a>Skapa en bred vy

En bred vy visar ett värde för varje objekt som visas. Värdet som visas kan vara värdet för en egenskap för .NET-objekt eller värdet för ett skript. Som standard finns ingen etikett eller rubrik för den här vyn.

## <a name="a-wide-view-display"></a>En bred vy visning

I följande exempel visas hur Windows PowerShell visar den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt som returneras av den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet när dess utdata skickas till den [ Formatet hela](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet. (Som standard den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returnerar en tabellvy.) I det här exemplet är de två kolumnerna används för att visa namnet på processen för varje returnerade objektet. Objektets egenskapens namn visas inte, endast värdet för egenskapen.

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

## <a name="defining-the-wide-view"></a>Definiera bred vy

Följande XML visar bred vy schemat för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.

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

- Den [visa](./view-element-format.md) elementet har det överordnade elementet i bred vy. (Detta är samma överordnade element för tabell, lista och anpassad kontroll vyer.)

- Den [namn](./name-element-for-view-format.md) elementet anger namnet på vyn. Det här elementet krävs för alla vyer.

- Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar de objekt som använder vyn. Det här elementet krävs.

- Den [GroupBy](./groupby-element-for-view-format.md) elementet definierar när en ny grupp med objekt visas. En ny grupp har startats när värdet för en specifik egenskap eller ett skript ändras. Det här elementet är valfritt.

- Den [kontroller](./controls-element-for-view-format.md) element definierar de anpassade kontroller som definieras av bred vy. Kontroller ger dig ett sätt som specificerar hur data visas. Det här elementet är valfritt. En vy kan definiera egna anpassade kontroller eller använda vanliga kontroller som kan användas av alla vyer i filen formatering. Mer information om anpassade kontroller finns i [skapar anpassade kontroller](./creating-custom-controls.md).

- Den [WideControl](./widecontrol-element-format.md) elementet och dess underordnade element definierar vad som visas i vyn. I föregående exempel vyn har utformats för att visa den [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) egenskapen.

Ett exempel på en fullständig formatering fil som definierar en enkel bred vy finns i [bred vy (grundläggande)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Att tillhandahålla definitioner för din bred vy

Brett vyer kan ge en eller flera definitioner med hjälp av de underordnade elementen i den [WideControl](./widecontrol-element-format.md) element. Vyn har vanligtvis bara en definition. I följande exempel visas vyn ger en enda definition som visar värdet för den [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) egenskapen. En bred vy kan visa värdet för en egenskap eller värdet för ett skript (visas inte i det här exemplet).

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

Följande XML-element kan användas för att ange definitioner för en bred vy:

- Den [WideControl](./widecontrol-element-format.md) elementet och dess underordnade element definierar vad som visas i vyn.

- Den [AutoSize](./autosize-element-for-widecontrol-format.md) elementet anger om kolumnstorlek och antalet kolumner justeras beroende på storleken på data. Det här elementet är valfritt.

- Den [antal_kolumner anger](./columnnumber-element-for-widecontrol-format.md) elementet anger antalet kolumner som visas i bred vy. Det här elementet är valfritt.

- Den [WideEntries](./wideentries-element-for-widecontrol-format.md) elementet innehåller definitioner av vyn. I de flesta fall har en vy endast en definition. Det här elementet krävs.

- Den [WideEntry](./wideentry-element-for-widecontrol-format.md) elementet innehåller en definition för vyn. Minst en [WideEntry](./wideentry-element-for-widecontrol-format.md) krävs, men det finns ingen högsta gräns för antalet element som du kan lägga till. I de flesta fall har en vy endast en definition.

- Den [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elementet anger de objekt som visas som en viss definition. Det här elementet är valfritt och krävs bara när du definierar flera [WideEntry](./wideentry-element-for-widecontrol-format.md) element som visar olika objekt.

- Den [WideItem](./wideitem-element-for-widecontrol-format.md) elementet anger de data som visas i vyn. Till skillnad från andra typer av vyer, kan en bred kontroll Visa endast ett objekt.

- Den [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elementet anger egenskapen vars värde visas i vyn. Du måste ange en egenskap eller ett skript, men du kan inte ange båda.

- Den [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elementet anger skriptet vars värde visas i vyn. Du måste ange ett skript eller en egenskap, men du kan inte ange båda.

- Den [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elementet anger ett mönster som används för att visa data. Det här elementet är valfritt.

Ett exempel på en fullständig formatering fil som definierar en bred vy-definition finns i [bred vy (grundläggande)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>Definiera de objekt som använder bred vy

Det finns två sätt att definiera vilka .NET-objekt använder bred vy. Du kan använda den [ViewSelectedBy](./viewselectedby-element-format.md) element för att definiera de objekt som kan visas av alla definitioner av vyn eller du kan använda den [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element för att definiera vilka objekt visas som en viss definition för vyn. I de flesta fall har endast en definition i en vy så objekt definieras vanligtvis av den [ViewSelectedBy](./viewselectedby-element-format.md) element.

I följande exempel visas hur du definierar de objekt som visas som en bred vy med hjälp av den [ViewSelectedBy](./viewselectedby-element-format.md) och [TypeName](./typename-element-for-viewselectedby-format.md) element. Det finns ingen gräns för hur många [TypeName](./typename-element-for-viewselectedby-format.md) element att du kan ange och deras inbördes ordning är inte särskilt stor.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Följande XML-element kan användas för att ange objekt som används av bred vy:

- Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar vilka objekt visas i bred vy.

- Den [TypeName](./typename-element-for-viewselectedby-format.md) elementet anger .NET som visas i vyn. Det fullständigt kvalificerade typnamnet .NET krävs. Du måste ange minst en typ eller val som angetts för vyn, men det finns inget högsta antal element som kan anges.

Ett exempel på en fullständig formatering fil, se [bred vy (grundläggande)](./wide-view-basic.md).

I följande exempel används den [ViewSelectedBy](./viewselectedby-element-format.md) och [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element. Använd val av där du har en uppsättning objekt som visas med flera vyer, till exempel när du definierar en bred vy och en tabellvy för samma objekt. Läs mer om hur du skapar en [definiera val av uppsättningar](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Följande XML-element kan användas för att ange objekt som används av bred vy:

- Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar vilka objekt visas i bred vy.

- Den [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementet anger en uppsättning objekt som kan visas i vyn. Du måste ange minst en markering set eller typ för vyn, men det finns inget högsta antal element som kan anges.

I följande exempel visas hur du definierar de objekt som visas av en viss definition av en bred vy med hjälp av den [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element. Med det här elementet kan ange du namnet på .NET objektet, val av flera objekt eller ett val av villkor som anger när definitionen används. Mer information om hur du skapar ett urval villkor finns i [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

Följande XML-element kan användas för att ange objekt som används av en viss definition av bred vy:

- Den [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elementet definierar vilka objekt visas i definitionen.

- Den [TypeName](./typename-element-for-viewselectedby-format.md) elementet anger .NET som visas när definitionen. När du använder det här elementet krävs det fullständigt kvalificerade typnamnet för .NET. Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.

- Den [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (visas inte) anger en uppsättning objekt som kan visas av denna definition. Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.

- Den [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (visas inte) anger ett villkor som måste finnas för den här definitionen som ska användas. Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges. Läs mer om hur du definierar villkoren för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Visa grupper med objekt i en bred vy

Du kan avgränsa de objekt som visas i bred vy i grupper. Detta innebär inte att du definierar en grupp, endast att Windows PowerShell startar en ny grupp när en specifik egenskap eller ett skript ändras. I följande exempel visas en ny grupp har startats när värdet för den [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) egenskapsändringar.

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

Ett exempel på en fullständig formatering fil som definierar grupper finns i [bred vy (GroupBy)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>Med hjälp av formatsträngar

Formatering strängar kan läggas till en bred vy för att ytterligare definiera hur data visas. I följande exempel visas hur du definierar en formateringssträngen för värdet för den `StartTime` egenskapen.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

Följande XML-element kan användas för att ange ett:

- Den [WideItem](./wideitem-element-for-widecontrol-format.md) elementet anger de data som visas i vyn.

- Den [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elementet anger egenskapen vars värde visas i vyn. Du måste ange en egenskap eller ett skript, men du kan inte ange båda.

- Den [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elementet anger ett formatmönster som definierar hur värdet för egenskapen eller skript visas i vyn

- Den [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (visas inte) anger skriptet vars värde visas i vyn. Du måste ange ett skript eller en egenskap, men du kan inte ange båda.

I följande exempel visas den `ToString` metoden anropas för att formatera värdet för skriptet. Skript kan anropa någon-metod för ett objekt. Därför, om ett objekt har en metod som `ToString`, som har formateringsparametrar, skriptet kan anropa metoden för att formatera utdatavärdet för skriptet.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

Följande XML-element som kan användas för att anropa den `ToString` metoden:

- Den [WideItem](./wideitem-element-for-widecontrol-format.md) elementet anger de data som visas i vyn.

- Den [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (visas inte) anger skriptet vars värde visas i vyn. Du måste ange ett skript eller en egenskap, men du kan inte ange båda.

## <a name="see-also"></a>Se även

[Bred vy (grundläggande)](./wide-view-basic.md)

[Bred vy (GroupBy)](./wide-view-groupby.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
