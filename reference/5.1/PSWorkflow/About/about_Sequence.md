---
description: Beskriver `Sequence` nyckelordet som kör markerade aktiviteter sekventiellt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_sequence?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Sequence
ms.openlocfilehash: a9dd4fb24274fe4e1478ca69c734b43a2f196792
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270938"
---
# <a name="about-sequence"></a>Om sekvenser

## <a name="short-description"></a>Kort beskrivning

Beskriver `Sequence` nyckelordet som kör markerade aktiviteter sekventiellt.

## <a name="long-description"></a>Lång beskrivning

`Sequence`Nyckelordet kör markerade arbets flödes aktiviteter i tur och ordning. Arbets flödes aktiviteter körs i den ordning som de visas och körs inte samtidigt. `Sequence`Nyckelordet är endast giltigt i ett PowerShell-arbetsflöde.

`Sequence`Nyckelordet används i ett- `Parallel` skript block för att köra markerade kommandon i tur och ordning.

Eftersom arbets flödes aktiviteter körs sekventiellt som standard `Sequence` är nyckelordet endast effektivt i ett- `Parallel` skript block. Om `Sequence` nyckelordet inte ingår i ett `Parallel` -skript block, är det giltigt men ineffektiv.

Med `Sequence` skript blocket kan du köra fler kommandon parallellt genom att köra beroende kommandon i tur och ordning.

## <a name="syntax"></a>Syntax

### <a name="workflow-using-sequence"></a>Arbets flöde med sekvens

```
workflow <Verb-Noun>
{
    Sequence
    {
        [<Activity>]
        [<Activity>]
        # ...
    }
}
```

### <a name="workflow-using-parallel-and-sequence"></a>Arbets flöde med parallell och sekvens

```
workflow <Verb-Noun>
{
    Parallel
    {
        [<Activity>]
        Sequence
        {
            [<Activity>]
            [<Activity>]
            # ...
        }
    }
}
```

## <a name="detailed-description"></a>Detaljerad beskrivning

Kommandona i ett- `Parallel` skript block kan köras samtidigt. Ordningen som de körs i avgörs inte. Den här funktionen förbättrar prestanda för ett skript arbets flöde.

Du kan använda ett- `Sequence` skript block för att köra valda aktiviteter sekventiellt, även om aktiviteterna visas i ett- `Parallel` skript block.

Aktiviteterna i ett `Sequence` skript block körs löpande i den ordning som de visas. En aktivitet i ett- `Sequence` skript block startar först efter att föregående aktivitet har slutförts.

Men när skript blocket `Sequence` visas i ett `Parallel` -skript block, bestäms i vilken ordning `Sequence` skript blocket körs. Det kan köras före, efter eller samtidigt med andra aktiviteter i `Parallel` skript blocket.

Följande arbets flöde innehåller till exempel ett- `Parallel` skript block som kör aktiviteter som får processer och tjänster på datorn. `Parallel`Skript blocket innehåller ett `Sequence` skript block som hämtar information från en fil och använder informationen som indata till ett skript.

`Get-Process` `Get-Service` Kommandona, och som hör till Hotfix är oberoende av varandra. Kommandona kan köras samtidigt eller i vilken ordning som helst. Men kommandot som hämtar information om snabb korrigeringar måste köras före det kommando som använder det.

```powershell
workflow Test-Workflow
{
    Parallel
    {
    Get-Process
    Get-Service

    Sequence
    {
        $Hotfix = Get-Content 'D:\HotFixes\Required.txt'
        Foreach ($h in $Hotfix) {'D:\Scripts\Verify-Hotfix' -Hotfix $h}
        }
    }
}
```

## <a name="see-also"></a>Se även

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[about_ForEach – parallell](about_ForEach-Parallel.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Parallel](about_Parallel.md)

[about_Workflows](about_Workflows.md)

[Skapa ett arbetsflöde med hjälp av ett Windows PowerShell-skript](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)
