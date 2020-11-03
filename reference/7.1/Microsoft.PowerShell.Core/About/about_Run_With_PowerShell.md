---
description: Förklarar hur du använder funktionen "kör med PowerShell" för att köra ett skript från en fil system enhet.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_run_with_powershell?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Run_With_PowerShell
ms.openlocfilehash: 83931fcfcc89340b1d4958e41cb182642a554737
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272312"
---
# <a name="about-run-with-powershell"></a>Om att köra med PowerShell

## <a name="short-description"></a>KORT BESKRIVNING
Förklarar hur du använder funktionen "kör med PowerShell" för att köra ett skript från en fil system enhet.

## <a name="long-description"></a>LÅNG BESKRIVNING

Från och med Windows PowerShell 3,0 kan du använda funktionen "kör med PowerShell" för att köra skript från Utforskaren i Windows 8 och Windows Server 2012 och från Utforskaren i tidigare versioner av Windows.

Funktionen "kör med PowerShell" är utformad för att köra skript som inte har nödvändiga parametrar och som inte returnerar utdata till kommando tolken.

När du använder funktionen "kör med PowerShell" visas fönstret PowerShell-konsol bara kort, om det finns. Du kan inte interagera med den.

Använda funktionen "kör med PowerShell":

I Utforskaren (eller Utforskaren) högerklickar du på skript filens namn och väljer sedan kör med PowerShell.

Funktionen "kör med PowerShell" startar en PowerShell-session som har en körnings princip som kringgås, kör skriptet och stänger sessionen.

Det kör ett kommando med följande format:

```
PowerShell.exe -File <FileName> -ExecutionPolicy Bypass
```

"Kör med PowerShell" ställer bara in principen för att kringgå körning för sessionen (den aktuella instansen av PowerShell-processen) som skriptet körs i.
Den här funktionen ändrar inte körnings principen för datorn eller användaren.

Funktionen "kör med PowerShell" påverkas bara av AllSigned-körnings principen. Om körnings principen för AllSigned är effektiv för datorn eller användaren, kör med PowerShell bara signerade skript. "Kör med PowerShell" påverkas inte av någon annan körnings princip. Mer information finns i [about_Execution_Policies](about_Execution_Policies.md).

Fel söknings meddelande: kör med PowerShell kommando kan du uppmanas att bekräfta körnings princip ändringen.

## <a name="see-also"></a>SE ÄVEN

[about_Execution_Policies](about_Execution_Policies.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Scripts](about_Scripts.md)

