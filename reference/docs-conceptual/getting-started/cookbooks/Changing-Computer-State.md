---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Ändra datorstatus
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: c659ad54325b0f7305f882e1cb9607062abad6a4
ms.sourcegitcommit: 2ffb9fa92129c2001379ca2c17646466721f7165
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251525"
---
# <a name="changing-computer-state"></a>Ändra datorstatus

Om du vill återställa en dator i Windows PowerShell använder du antingen ett kommandoradsverktyg som standard eller en WMI-klassen. Även om du använder Windows PowerShell endast för att köra verktyget visar Lär dig att ändra en dators energisparläge i Windows PowerShell några av viktig information om hur du arbetar med externa verktyg i Windows PowerShell.

### <a name="locking-a-computer"></a>Låsa en dator

Det enda sättet att låsa en dator direkt med standard tillgängliga verktyg är att anropa den **LockWorkstation()** fungera i **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Det här kommandot låser omedelbart arbetsstationen. Den använder *rundll32.exe*som kör Windows-dll: er (och sparar sina bibliotek för fortlöpande användning) att köra user32.dll, ett bibliotek med funktioner för Windows.

När du låsa en arbetsstation medan snabbt användarbyte är aktiverad, t.ex. på Windows XP datorn visar inloggningsskärmen användaren i stället för att starta den aktuella användaren skärmsläckaren.

Om du vill stänga av viss sessioner på Terminal Server måste du använda den **tsshutdn.exe** kommandoradsverktyget.

### <a name="logging-off-the-current-session"></a>Logga ut den aktuella sessionen

Du kan använda flera olika metoder för att logga ut från en session på det lokala systemet. Det enklaste sättet är att använda kommandoradsverktyget Remote Desktop/Terminal Services **logoff.exe** (Mer information i Windows PowerShell-Kommandotolken skriver **utloggning /?**). Om du vill logga ut den aktuella aktiva sessionen, skriver **utloggning** utan argument.

Du kan också använda den **shutdown.exe** verktyget med utloggningsalternativet dess:

```
shutdown.exe -l
```

Ett tredje alternativ är att använda WMI. Win32_OperatingSystem-klassen har en Win32Shutdown-metod. Startar metod med flaggan 0 initierar utloggning:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Mer information och andra funktioner för metoden Win32Shutdown finns ”Win32Shutdown metod för den Win32_OperatingSystem-klassen” i MSDN.

### <a name="shutting-down-or-restarting-a-computer"></a>Stänga av eller starta om en dator

Stänga av och starta om datorer är vanligtvis samma typ av aktivitet. Verktyg som stänga av datorn normalt startar om den också, och vice versa. Det finns två enkla alternativ för att starta om en dator från Windows PowerShell. Använda Tsshutdn.exe eller Shutdown.exe med lämpliga argument. Du kan få detaljerad användningsinformation från **tsshutdn.exe /?** eller **shutdown.exe /?**.

Du kan också utföra avstängning och starta om operations direkt från Windows PowerShell samt.

Använd kommandot starta om datorn för att stänga av datorn

```powershell
stop-computer
```

Om du vill starta om operativsystemet, använder du kommandot starta om datorn

```powershell
restart-computer
```
