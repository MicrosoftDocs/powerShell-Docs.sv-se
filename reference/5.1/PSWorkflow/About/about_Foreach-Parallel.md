---
description: Beskriver `ForEach -Parallel` språk konstruktion i Windows PowerShell-arbetsflöde.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_foreach-parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach parallell
ms.openlocfilehash: 1012b45396b65d424dacac067c2af8d3b6823f92
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270956"
---
# <a name="about-foreach-parallel"></a>Om Foreach-Parallel

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver `ForEach -Parallel` språk konstruktion i Windows PowerShell-arbetsflöde.

## <a name="long-description"></a>LÅNG BESKRIVNING

Den **parallella** parametern för `ForEach` nyckelordet kör kommandona i ett `ForEach` skript block en gång för varje objekt i en angiven samling.

Objekten i samlingen, till exempel en disk i en samling diskar, bearbetas parallellt. Kommandona i skript blocket körs sekventiellt på varje objekt i samlingen.

`ForEach -Parallel` är endast giltig i ett Windows PowerShell-arbetsflöde.

### <a name="syntax"></a>SYNTAX

```
ForEach -Parallel ($<item> in $<collection>)
{
    [<Activity1>]
    [<Activity2>]
    ...
}
```

### <a name="detailed-description"></a>DETALJERAD BESKRIVNING

Precis som i Windows PowerShell måste variabeln som innehåller samling `$<collection>` definieras före `ForEach -Parallel` instruktionen, men variabeln som representerar det aktuella objektet `$<item>` definieras i `ForEach -Parallel` instruktionen.

`ForEach -Parallel`Konstruktionen skiljer sig från `ForEach` nyckelordet och den **parallella** parametern. `ForEach`Nyckelordet bearbetar objekten i insamlingen i sekvensen. Den **parallella** parametern kör kommandon i ett skript block parallellt. Du kan sätta ett parallellt skript block i ett- `ForEach -Parallel` skript block.

Mål datorerna i ett arbets flöde, till exempel de som anges av den gemensamma parametern för **PSComputerName** -arbetsflöde, bearbetas alltid parallellt.
Du behöver inte ange `ForEach -Parallel` nyckelordet för det här ändamålet.

### <a name="examples"></a>EXEMPEL

Följande arbets flöde innehåller en `ForEach -Parallel` instruktion som bearbetar de diskar som `Get-Disk` aktiviteten hämtar. Kommandona i `ForEach -Parallel` skript blocket körs sekventiellt, men de körs på diskarna parallellt. Diskarna kan bearbetas samtidigt och i vilken ordning som helst.

```powershell
workflow Test-Workflow
{
    $Disks = Get-Disk

    # The disks are processed in parallel.
    ForEach -Parallel ($Disk in $Disks)
    {
        # The commands run sequentially on each disk.
        $DiskPath = $Disk.Path
        $Disk | Initialize-Disk
        Set-Disk -Path $DiskPath
    }
}

workflow Test-Workflow
{
    #Run commands in parallel.
    Parallel
    {
        Get-Process
        Get-Service
    }

   $Disks = Get-Disk

   # The disks are processed in parallel.
   ForEach -Parallel ($Disk in $Disks)
   {
       # The commands run in parallel on each disk.
       Parallel
       {
           Initialize-Disk
           InlineScript {.\Get-DiskInventory}
       }
   }
}
```

## <a name="see-also"></a>SE ÄVEN

[Skriva ett skript arbets flöde](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_ForEach.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Parallel](about_Parallel.md)

[about_Workflows](about_Workflows.md)
