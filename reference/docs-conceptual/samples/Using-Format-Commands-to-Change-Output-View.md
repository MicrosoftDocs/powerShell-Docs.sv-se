---
ms.date: 11/22/2019
keywords: PowerShell, cmdlet
title: Använd formatkommandon för att ändra utdatavyn
ms.openlocfilehash: f270d5ec5efe5caf506d6a8a45285990996f6ae6
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417584"
---
# <a name="using-format-commands-to-change-output-view"></a>Använd formatkommandon för att ändra utdatavyn

PowerShell har en uppsättning cmdletar som gör att du kan styra hur egenskaper visas för specifika objekt. Namnen på alla cmdletar börjar med verb `Format`. De låter dig välja vilka egenskaper du vill visa.

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

I den här artikeln beskrivs cmdletarna `Format-Wide`, `Format-List`och `Format-Table`.

Varje objekt typ i PowerShell har standard egenskaper som används när du inte anger vilka egenskaper som ska visas. Varje cmdlet använder också samma **egenskaps** parameter för att ange vilka egenskaper som du vill visa. Eftersom `Format-Wide` endast visar en enskild egenskap, har **egenskaps** parametern bara ett enda värde, men egenskaps parametrarna för `Format-List` och `Format-Table` acceptera en lista med egenskaps namn.

I det här exemplet visar standardutdata för `Get-Process` cmdlet att vi har två instanser av Internet Explorer igång.

```powershell
Get-Process -Name iexplore
```

Standardformat för **process** objekt visar de egenskaper som visas här:

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a>Använda hel skärms läge för utdata med ett enda objekt

I `Format-Wide`-cmdleten visas som standard endast objektets standard egenskap. Informationen som är kopplad till varje objekt visas i en enda kolumn:

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

Du kan också ange en egenskap som inte är standard:

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a>Kontrol lera format – bred skärm med kolumn

Med `Format-Wide`-cmdlet: en kan du bara visa en enskild egenskap i taget. Detta gör det användbart för att visa stora listor i flera kolumner.

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a>Använda format-lista för att visa en listvy

Cmdleten `Format-List` visar ett objekt i form av en lista, där varje egenskap har etiketten och visas på en separat rad:

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

Du kan ange så många egenskaper du vill:

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Få detaljerad information med hjälp av format-lista med jokertecken

Med hjälp av cmdleten `Format-List` kan du använda ett jokertecken som värde för dess **egenskaps** parameter. På så sätt kan du Visa detaljerad information. Objekt innehåller ofta mer information än vad du behöver, vilket är anledningen till att PowerShell inte visar alla egenskaps värden som standard. Om du vill visa alla egenskaper för ett objekt använder du kommandot `Format-List -Property *`. Följande kommando genererar över 60 rader utdata för en enda process:

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

Även om `Format-List` kommandot är användbart för att visa information, är en enklare tabellvy ofta mer användbar om du vill ha en översikt över utdata som innehåller många objekt.

## <a name="using-format-table-for-tabular-output"></a>Använda format tabell för tabell data

Om du använder `Format-Table`-cmdlet utan några egenskaps namn för att formatera utdata från `Get-Process` kommandot får du exakt samma utdata som du gör utan en `Format`-cmdlet. Som standard visar PowerShell **process** objekt i tabell format.

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a>Förbättra format – tabellens utdata (AutoSize)

Även om en tabellvy är användbar för att visa massor av information kan det vara svårt att tolka om visningen är för smal för data. I föregående exempel trunkeras utdata. Om du anger parametern **AutoSize** när du kör kommandot `Format-Table`, beräknar PowerShell kolumn bredden baserat på de faktiska data som visas. Det gör kolumnerna läsbara.

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

`Format-Table` cmdleten kan fortfarande trunkera data, men de trunkeras bara i slutet av skärmen. Andra egenskaper än den sista som visas, har samma storlek som de behöver för att det ska visas på rätt data element.

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

Kommandot `Format-Table` förutsätter att egenskaperna är listade i prioritetsordning. Det försöker då att helt Visa egenskaperna närmast början. Om kommandot `Format-Table` inte kan visa alla egenskaper tas vissa kolumner bort från visningen. Du kan se det här beteendet i **DependentServices** -egenskapen i föregående exempel.

### <a name="wrapping-format-table-output-in-columns-wrap"></a>Rad brytnings format – tabellens utdata i kolumner (radbyte)

Du kan tvinga långvariga `Format-Table` data att figursättas i sin visnings kolumn med hjälp av parametern **wrap** . **Det går** inte att använda den omslutna parametern, eftersom den använder standardinställningar om du inte också anger **AutoSize**:

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

Att använda **wrap** -parametern i sig saktar inte ned bearbetningen väldigt mycket. Att använda **AutoSize** för att formatera en rekursiv fil listning av en stor katalog struktur kan dock ta lång tid och använda mycket minne innan de första utmatnings objekten visas.

Om du inte bekymrar dig om system belastningen **fungerar** autopassering bra med **wrap** -parametern.
De ursprungliga kolumnerna använder fortfarande så mycket bredd som det behövs för att visa objekt på en rad, men den sista kolumnen är omsluten, om det behövs.

> [!NOTE]
> Vissa kolumner kanske inte visas när du anger de bredaste kolumnerna först. För bästa resultat anger du de minsta data elementen först.

I följande exempel anger vi de bredaste egenskaperna först.

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

Med rad brytning utelämnas kolumnen slutligt **ID** :

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a>Organisera tabellens utdata (-GroupBy)

En annan användbar parameter för kontroll av tabellens utdata är **groupby**. Längre tabell listor kan vara svåra att jämföra. Parametern **groupby** grupperar utdata baserat på ett egenskaps värde. Vi kan till exempel gruppera tjänster efter **StartType** för enklare granskning och utelämna **StartType** -värdet från egenskaps listan:

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
