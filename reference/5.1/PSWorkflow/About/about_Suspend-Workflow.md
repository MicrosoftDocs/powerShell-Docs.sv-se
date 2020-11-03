---
description: Beskriver `Suspend-Workflow` aktiviteten, som pausar arbets flödet där aktiviteten visas.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_suspend-workflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Suspend arbets flöde
ms.openlocfilehash: cbe5386ae5aa4bd863079fde240ddf2ce5384727
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270921"
---
# <a name="about-suspend-workflow"></a>Om Suspend-Workflow

## <a name="short-description"></a>Kort beskrivning

Beskriver `Suspend-Workflow` aktiviteten, som pausar arbets flödet där aktiviteten visas.

## <a name="long-description"></a>Lång beskrivning

`Suspend-Workflow`Aktiviteten stoppar tillfälligt arbets flödes bearbetningen inifrån arbets flödet. Innan du gör uppehåll, tar Windows PowerShell-arbetsflöde en kontroll punkt så att arbets flödets tillstånd och data bevaras och arbets flödet kan återupptas från uppehålls punkten.

För att återuppta arbets flödet använder användaren som kör arbets flödet `Resume-Job` cmdleten. Du kan inte återuppta ett arbets flöde inifrån arbets flödet.

## <a name="syntax"></a>Syntax

```
workflow <Verb-Noun>
{
    Suspend-Workflow
}
```

## <a name="detailed-description"></a>Detaljerad beskrivning

`Suspend-Workflow`Arbets flödet stoppas tillfälligt och ett jobb objekt som representerar arbets flödes jobbet returneras. Ett jobb objekt returneras även om du inte körde arbets flödet som ett jobb. Till exempel med den gemensamma parametern **AsJob** Workflow. Jobb tillståndet har **pausats**.

Du kan använda jobb-cmdletar för att hantera det pausade arbets flödes jobbet. Använd cmdleten för att återuppta arbets flödes jobbet `Resume-Job` .

När du återupptar arbets flödes jobbet återupptas arbets flödet vid kommandot som följer efter- `Suspend-Workflow` aktiviteten.

Följande arbets flöde innehåller till exempel `Suspend-Workflow` aktiviteten.
När du kör arbets flödet kör det `Get-Date` aktiviteten, sparar dess utdata i `$a` variabeln och pausar sedan arbets flödet och returnerar ett jobb objekt som representerar det pausade arbets flödet. Jobb typen är **PSWorkflowJob**.

Du kan använda jobb-cmdlet: ar, till exempel `Get-Job` för att hantera arbets flödes jobbet.

```powershell
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

Test-Suspend
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Suspended  True         localhost Test-Suspend
```

## <a name="resuming-a-workflow-job"></a>Återupptar ett arbets flödes jobb

Använd cmdleten för att återuppta arbets flödes jobbet `Resume-Job` . `Resume-Job`Cmdleten returnerar arbets flödes jobbets objekt omedelbart, även om det inte kan återupptas ännu. Om du vill vänta på att jobbet ska återupptas använder du parametern **wait** eller använder `Get-Job` cmdleten för att hämta aktuellt jobb objekt.

```powershell
Resume-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State    HasMoreData  Location  Command
--  ----  -------------  -----    -----------  --------  -------
8   Job8  PSWorkflowJob  Running  True         localhost Test-Suspend
```

```powershell
Get-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Completed  True         localhost Test-Suspend
```

## <a name="getting-the-output-of-a-workflow-job"></a>Hämta utdata för ett arbets flödes jobb

Använd cmdleten för att hämta utdata för ett arbets flödes jobb `Receive-Job` . Utdata visar att arbets flödet har återupptagits vid kommandot som följde `Suspend-Workflow` cmdleten. Värdet för `$a` variabeln, som fylldes före SUS pensionen, är tillgängligt för arbets flödet när det återupptas.

```powershell
Get-Job -Name Job8 | Receive-Job
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 19
Milliseconds      : 823
Ticks             : 198230041
TotalDays         : 0.000229432917824074
TotalHours        : 0.00550639002777778
TotalMinutes      : 0.330383401666667
TotalSeconds      : 19.8230041
TotalMilliseconds : 19823.0041
PSComputerName    : localhost
```

## <a name="see-also"></a>Se även

[about_Workflows](about_Workflows.md)

[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)

[PSWorkflow](xref:PSWorkflow) -cmdletar

[Arbetsflödesguiden](/previous-versions/powershell/scripting/components/workflows-guide)

[Skriva ett Windows PowerShell-arbetsflöde](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
