---
ms.date: 12/23/2019
keywords: PowerShell, cmdlet
title: Ändra datorstatus
ms.openlocfilehash: 9278df55ba027134a61c8ed4e89b5b839d460b29
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736921"
---
# <a name="changing-computer-state"></a>Ändra datorstatus

Om du vill återställa en dator i PowerShell använder du antingen ett standard kommando rads verktyg, WMI eller CIM-klass.
Även om du bara använder PowerShell för att köra verktyget, kan du lära dig hur du ändrar datorns energi tillstånd i PowerShell. här visas några viktiga detaljer om hur du arbetar med externa verktyg i PowerShell.

## <a name="locking-a-computer"></a>Låsa en dator

Det enda sättet att låsa en dator direkt med de standard verktyg som är tillgängliga är att anropa funktionen **LockWorkstation ()** i **user32. dll**:

```powershell
rundll32.exe user32.dll,LockWorkStation
```

Det här kommandot låser arbets stationen omedelbart. Den använder **rundll32. exe**, som kör Windows-DLL-filer (och sparar bibliotek för upprepad användning) för att köra `user32.dll`, ett bibliotek med Windows Management-funktioner.

När du låser en arbets Station medan snabbt användar byte är aktiverat, till exempel på Windows XP, visar datorn inloggnings skärmen för användare i stället för att starta den aktuella användarens skärmsläckare.

Om du vill stänga av vissa sessioner på en Terminal Server använder du kommando rads verktyget **tsshutdn. exe** .

## <a name="logging-off-the-current-session"></a>Logga ut den aktuella sessionen

Du kan använda flera olika tekniker för att logga ut från en session på det lokala systemet. Det enklaste sättet är att använda kommando rads verktyget fjärr skrivbord/Terminal Services, **LOGOFF. exe** (mer information finns i PowerShell-prompten genom att skriva `logoff /?`). Om du vill logga ut från den aktuella aktiva sessionen skriver du `logoff` utan argument.

Du kan också använda **Shutdown. exe** -verktyget med dess utloggnings alternativ:

```powershell
shutdown.exe -l
```

Ett annat alternativ är att använda WMI. **Win32_OperatingSystem** -klassen har en **avslutnings** metod.
När du anropar metoden med flaggan 0 påbörjas utloggning:

Mer information om metoden för **avstängning** finns i [metoden shutdown i Win32_OperatingSystem-klassen](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a>Stänga av eller starta om en dator

Att stänga av och starta om datorer är vanligt vis samma typer av uppgift. Verktyg som stänger av en dator startar normalt även om det, och vice versa. Det finns två enkla alternativ för att starta om en dator från PowerShell. Använd antingen **tsshutdn. exe** eller **Shutdown. exe** med lämpliga argument. Du kan få detaljerad användnings information från `tsshutdn.exe /?` eller `shutdown.exe /?`.

Du kan också utföra åtgärder för avstängning och omstart direkt från PowerShell.

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
