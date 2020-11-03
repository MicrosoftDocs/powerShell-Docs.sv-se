---
description: Beskriver det parallella nyckelordet, som kör aktiviteterna i ett arbets flöde parallellt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parallel
ms.openlocfilehash: 402e93672bbea4ec9b6bfda8d608f266f6c40a21
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270944"
---
# <a name="about-parallel"></a>Om parallell

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver det parallella nyckelordet, som kör aktiviteterna i ett arbets flöde parallellt.

## <a name="long-description"></a>LÅNG BESKRIVNING

Det parallella nyckelordet kör arbets flödes aktiviteter parallellt. Det här nyckelordet är endast giltigt i Windows PowerShell-arbetsflöde.

### <a name="syntax"></a>SYNTAX

```
workflow <Verb-Noun>
{
     Parallel
     {
          [<Activity>]
          [<Activity>]
        ...
     }
 }
```

## <a name="detailed-description"></a>DETALJERAD BESKRIVNING

Kommandona i ett parallellt skript block kan köras samtidigt. Ordningen som de körs i avgörs inte.

Följande arbets flöde innehåller till exempel ett parallellt skript block som kör aktiviteter som får processer och tjänster på datorn. Eftersom Get-Process-och Get-Service-kommandona är oberoende av varandra, kan de köras samtidigt och i vilken ordning som helst.

```powershell
workflow Test-Workflow
{
    Parallel
    {
         Get-Process
         Get-Service
    }
}
```

Att köra kommandon parallellt är mycket effektivt och minskar den tid det tar att slutföra ett arbets flöde avsevärt.

Om du vill köra markerade kommandon i ett parallellt skript block i sekventiell ordning använder du nyckelordet Sequence. Mer information finns i about_Sequence.

Om du vill köra ett parallellt skript block för objekt i en samling, använder du förtagnings-eller förgrunds-Parallel-nyckelord.

## <a name="see-also"></a>SE ÄVEN

["Skriva ett skript arbets flöde"](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[about_ForEach – parallell](about_ForEach-Parallel.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Sequence](about_Sequence.md)

[about_Workflows](about_workflows.md)
