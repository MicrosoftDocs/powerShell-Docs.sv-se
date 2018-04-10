---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Sortera objekt
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 272d550a67b206f9924ebe143eca2f5906c0a304
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="sorting-objects"></a>Sortera objekt

Vi kan ordna data som visas för att göra det lättare att skanna med hjälp av den **Sort-Object** cmdlet. **Sortera objekt** använder namnet på en eller flera egenskaper för att sortera och returnerar data sorteras efter värden för dessa egenskaper.

Överväg att problemet med att visa en lista över Win32_SystemDriver instanser. Om vi vill sortera efter **tillstånd** och sedan efter **namn**, vi kan göra det genom att skriva:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

Även om det är en tidskrävande skärm visas objekt med samma tillstånd som grupperas tillsammans:

```output
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