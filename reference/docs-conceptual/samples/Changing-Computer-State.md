---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Ändra datorstatus
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386290"
---
# <a name="changing-computer-state"></a>Ändra datorstatus

Om du vill återställa en dator i Windows PowerShell använder du antingen ett standard kommando rads verktyg, WMI eller CIM-klass. Även om du bara använder Windows PowerShell för att köra verktyget, kan du lära dig hur du ändrar datorns energi tillstånd i Windows PowerShell. här visas några viktiga detaljer om hur du arbetar med externa verktyg i Windows PowerShell.

## <a name="locking-a-computer"></a>Låsa en dator

Det enda sättet att låsa en dator direkt med de standard verktyg som är tillgängliga är att anropa funktionen **LockWorkstation ()** i **user32. dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Det här kommandot låser arbets stationen omedelbart. Den använder *rundll32. exe*, som kör Windows-DLL: er (och sparar deras bibliotek för upprepad användning) för att köra user32. dll, ett bibliotek med Windows Management-funktioner.

När du låser en arbets Station medan snabbt användar byte är aktiverat, till exempel på Windows XP, visar datorn inloggnings skärmen för användare i stället för att starta den aktuella användarens skärmsläckare.

Om du vill stänga av vissa sessioner på en Terminal Server använder du kommando rads verktyget **tsshutdn. exe** .

## <a name="logging-off-the-current-session"></a>Logga ut den aktuella sessionen

Du kan använda flera olika tekniker för att logga ut från en session på det lokala systemet. Det enklaste sättet är att använda kommando rads verktyget fjärr skrivbord/Terminal Services, **LOGOFF. exe** (mer information finns i Windows PowerShell-prompten genom att skriva **LOGOFF/?** ). Logga ut den aktuella aktiva sessionen genom att skriva **LOGOFF** utan argument.

Du kan också använda **Shutdown. exe** -verktyget med dess utloggnings alternativ:

```
shutdown.exe -l
```

Ett annat alternativ är att använda WMI. Win32_OperatingSystem-klassen har en Win32Shutdown-metod. När du anropar metoden med flaggan 0 påbörjas utloggning:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Mer information och hitta andra funktioner i Win32Shutdown-metoden finns i "Win32Shutdown-metoden för klassen Win32_OperatingSystem" i MSDN.

Slutligen kan du använda CIM med samma Win32_OperatingSystem-klass enligt beskrivningen ovan i WMI-metoden.

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a>Stänga av eller starta om en dator

Att stänga av och starta om datorer är vanligt vis samma typer av uppgift. Verktyg som stänger av en dator startar normalt även om det, och vice versa. Det finns två enkla alternativ för att starta om en dator från Windows PowerShell. Använd antingen tsshutdn. exe eller Shutdown. exe med lämpliga argument. Du kan få detaljerad användnings information från **tsshutdn. exe/?** eller **Shutdown. exe/?** .

Du kan också utföra åtgärder för avstängning och omstart direkt från Windows PowerShell.

Om du vill stänga av datorn använder du kommandot Stop-Computer

```powershell
Stop-Computer
```

Starta om operativ systemet genom att använda kommandot Restart-Computer

```powershell
Restart-Computer
```

Använd parametern-Force om du vill framtvinga en omedelbar omstart av datorn.

```powershell
Restart-Computer -Force
```
