---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Sortera objekt
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 2df45c64656e74dc8b72957ce59f2a5e5ee663b6
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="sorting-objects"></a>Sortera objekt
Vi kan ordna data som visas för att göra det lättare att skanna med hjälp av den **Sort-Object** cmdlet. **Sortera objekt** använder namnet på en eller flera egenskaper för att sortera och returnerar data sorteras efter värden för dessa egenskaper.

Överväg att problemet med att visa en lista över Win32_SystemDriver instanser. Om vi vill sortera efter **tillstånd** och sedan efter **namn**, vi kan göra det genom att skriva:

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

Även om det är en tidskrävande skärm visas objekt med samma tillstånd som grupperas tillsammans:

```
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

Du kan också sortera objekten i omvänd ordning genom att ange den **fallande** parameter. Detta återför sorteringsordningen så att namnen sorteras i omvänd alfabetisk ordning och siffror sorteras efter fallande ordning.

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```

