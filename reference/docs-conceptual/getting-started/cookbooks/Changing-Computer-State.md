---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Ändra datorstatus
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: 4b5b4adb349dd8036117c364ed2ebb1ffaf8c88f
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267893"
---
# <a name="changing-computer-state"></a>Ändra datorstatus

Om du vill återställa en dator i Windows PowerShell använder du ett kommandoradsverktyg som standard eller en WMI-klass. Även om du använder Windows PowerShell endast för att köra verktyget, visar lära dig hur du ändrar energinivån för en dator i Windows PowerShell några av viktig information om hur du arbetar med externa verktyg i Windows PowerShell.

### <a name="locking-a-computer"></a>Låsa en dator

Det enda sättet att låsa en dator direkt med standardverktyg för tillgänglig är att anropa den **LockWorkstation()** fungera i **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Det här kommandot låses omedelbart arbetsstationen. Den använder *rundll32.exe*, som kör Windows-dll: er (och sparar sina bibliotek för upprepad användning) att köra user32.dll, ett bibliotek med Windows-hanteringsfunktioner.

När du låsa en arbetsstation medan snabbt användarbyte är aktiverat, t.ex. på Windows XP datorn visar inloggningsskärmen för användaren i stället för att starta den aktuella användaren skärmsläckaren.

Om du vill stänga av specifika sessioner på en Terminal Server använder den **tsshutdn.exe** kommandoradsverktyget.

### <a name="logging-off-the-current-session"></a>Logga ut den aktuella sessionen

Du kan använda flera olika tekniker för att logga ut från en session på det lokala systemet. Det enklaste sättet är att använda kommandoradsverktyget Remote Desktop/Terminal Services **logoff.exe** (Mer information finns i Windows PowerShell-Kommandotolken skriver du **utloggning /?**). Om du vill logga ut den aktuella aktiva sessionen, skriver **utloggning** utan argument.

Du kan också använda den **shutdown.exe** verktyget med utloggningsalternativet dess:

```
shutdown.exe -l
```

Ett tredje alternativ är att använda WMI. Win32_OperatingSystem-klassen har en Win32Shutdown-metod. Anropa metoden med flaggan 0 initierar utloggning:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Mer information och hitta andra funktioner i metoden Win32Shutdown finns ”Win32Shutdown metoden av the Win32_OperatingSystem-klassen” i MSDN.

### <a name="shutting-down-or-restarting-a-computer"></a>Stänga av eller starta om en dator

Stänga av och starta om datorer är vanligtvis samma typ av uppgift. Verktyg som stänga av datorn Allmänt startar om den också, och vice versa. Det finns två enkla alternativ för att starta om en dator från Windows PowerShell. Använd Tsshutdn.exe eller Shutdown.exe med rätt argument. Du kan få detaljerad användningsinformation från **tsshutdn.exe /?** eller **shutdown.exe /?**.

Du kan också utföra avstängning och starta om åtgärder direkt från Windows PowerShell samt.

Om du vill stänga av datorn, använder du kommandot stop-computer

```powershell
stop-computer
```

Om du vill starta om operativsystemet, använder du kommandot starta om datorn

```powershell
restart-computer
```
