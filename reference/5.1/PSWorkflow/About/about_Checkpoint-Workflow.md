---
description: Beskriver Checkpoint-Workflow aktivitet, som tar en kontroll punkt i ett arbets flöde.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_checkpoint-workflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Checkpoint arbets flöde
ms.openlocfilehash: 223deb07ff6ed387cf04736116ea0ce3f998bb59
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270957"
---
# <a name="about-checkpoint-workflow"></a>Om Checkpoint-Workflow

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver Checkpoint-Workflow aktivitet, som tar en kontroll punkt i ett arbets flöde.

## <a name="long-description"></a>LÅNG BESKRIVNING

Checkpoint-Workflow-aktiviteten tar en kontroll punkt, vilket sparar tillstånd och data i arbets flödet. Om arbets flödet pausas eller avbryts kan det återupptas från den senaste kontroll punkten, i stället för att behöva startas om.

Checkpoint-Workflow-aktiviteten är bara giltig i ett arbets flöde.

### <a name="syntax"></a>SYNTAX

```
Workflow <Verb-Noun>
{
    Checkpoint-Workflow
}
```

Checkpoint-Workflow aktiviteten accepterar inte några parametrar, inklusive vanliga parametrar och gemensamma parametrar för arbets flöde.

Du kan placera Checkpoint-Activity kontroll punkt var som helst i ett arbets flöde efter instruktionen CmdletBinding eller param. Men när du placerar kontroll punkter bör du överväga prestanda kostnaden för insamling av data och skrivning till disk på den dator som kör arbets flödet.

Se till att tiden det tar att köra en del av arbets flödet igen om det avbryts är större än tiden det tar att skriva kontroll punkts tillstånd och data till disk.

Överväg att ta kontroll punkter efter viktiga steg så att arbets flödet kan återupptas i stället för att starta om. Ta till exempel en kontroll punkt efter kommandon som inte är idempotenta.

### <a name="about-checkpoints"></a>OM KONTROLL PUNKTER

En kontroll punkt är en ögonblicks bild av arbets flödets aktuella tillstånd, inklusive de aktuella värdena för variabler och alla utdata som genererats till den punkten och sparar dem på disk.

Om ett arbets flöde avbryts, avsiktligt eller oavsiktligt, använder Windows PowerShell-arbetsflödeet automatiskt data i den senaste kontroll punkten för att återställa och återuppta arbets flödet.

När du kör arbets flödet som ett jobb, t. ex. genom att använda den gemensamma AsJob-parametern för arbets flödet, behålls arbets flödets kontroll punkter tills du tar bort jobbet, till exempel med hjälp av Remove-Job cmdlet.
Annars tas kontroll punkter för arbets flöden bort när arbets flödet har slutförts.

### <a name="other-checkpointing-techniques"></a>ANDRA METODER FÖR KONTROLL PUNKTER

Utöver Checkpoint-Workflow aktivitet stöder Windows PowerShell-arbetsflöde andra kontroll punkter, inklusive följande:

- Gemensam parameter för PSPersist-arbetsflöde
- Gemensam parameter för PSPersist-aktivitet
- PSPersistPreference-variabel (i ett arbets flöde)

Mer information om hur du lägger till en kontroll punkt i ett arbets flöde finns i "så här lägger du till kontroll punkter i ett arbets flöde".

## <a name="examples"></a>EXEMPEL

Följande arbets flöde innehåller ett anrop till Checkpoint-Workflow-aktiviteten när en tids krävande funktion har slutförts och ett skript som delar data.

```powershell
Workflow Test-Workflow
{
    $a = Invoke-LongRunningFunction
    InlineScript { \\Server\Share\Get-DataPacks.ps1 $Using:a}
    Checkpoint-Workflow

    Invoke-LongRunningFunction
    {
        ...
    }
}
```

## <a name="see-also"></a>SE ÄVEN

[Skriva ett Windows PowerShell-arbetsflöde](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
