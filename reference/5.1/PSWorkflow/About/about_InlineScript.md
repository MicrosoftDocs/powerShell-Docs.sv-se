---
description: Beskriver `InlineScript` aktiviteten som kör PowerShell-kommandon i ett arbets flöde.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_inlinescript?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_InlineScript
ms.openlocfilehash: 2eaeb02c6441865551b586e27a39c4000826752b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270951"
---
# <a name="about-inlinescript"></a>Om InlineScript

## <a name="short-description"></a>Kort beskrivning

Beskriver `InlineScript` aktiviteten som kör PowerShell-kommandon i ett arbets flöde.

## <a name="long-description"></a>Lång beskrivning

`InlineScript`Aktiviteten Kör kommandon i en delad PowerShell-sessions arbets flöde. `InlineScript` är bara giltig i arbets flöden.

## <a name="syntax"></a>Syntax

```
InlineScript {<script block>} <ActivityCommonParameters>
```

## <a name="detailed-description"></a>Detaljerad beskrivning

`InlineScript`Aktiviteten Kör kommandon i en delad PowerShell-session. Du kan inkludera det i ett arbets flöde för att köra kommandon som delar data och kommandon som inte annars är giltiga i ett arbets flöde.

`InlineScript`Skript blocket kan innehålla alla giltiga PowerShell-kommandon och-uttryck. Eftersom kommandon och uttryck i ett `InlineScript` skript block körs i samma session, delar de alla tillstånd och data, inklusive importerade moduler och värden för variabler.

Du kan placera en `InlineScript` aktivitet var som helst i ett arbets flöde eller ett kapslat arbets flöde, inklusive i en loop eller kontroll-instruktion eller ett parallell-eller sekvens-skript block.

`InlineScript`Aktiviteten har gemensamma aktivitets parametrar, inklusive **PSPersist**. Kommandona och uttrycken i ett- `InlineScript` skript block har dock inte de arbets flödes funktioner som kontroll punkter, eller beständighet, och gemensamma parametrar för arbets flöde eller aktivitet. Mer information finns i [about_ActivityCommonParameters](about_ActivityCommonParameters.md).

## <a name="inlinescript-variables"></a>InlineScript-variabler

Som standard är variablerna som definieras i ett arbets flöde inte synliga för kommandona i `InlineScript` skript blocket. `InlineScript`Använd omfångs modifieraren för att göra variabler för arbets flöden synliga för `$Using` . `$Using`Omfångs modifieraren krävs bara en gång för varje variabel i `InlineScript` .

Mer information om `$Using` omfångs modifieraren finns i [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).

I följande exempel visas att `$Using` omfångs modifieraren gör värdet för den `$a` översta arbets flödes variabeln som är tillgänglig för kommandona i `InlineScript` skript blocket.

```powershell
workflow Test-Workflow {
  $a = 3

  ## Without $Using, the $a workflow variable isn't visible
  ## in inline script.
  InlineScript {"Inline A0 = $a"}

  ## $Using imports the variable and its current value.
  InlineScript {"Inline A1 = $Using:a"}
}

Test-Workflow
```

```output
Inline A0 =
Inline A1 = 3
```

## <a name="returning-variables-in-inlinescript"></a>Returnera variabler i InlineScript

`InlineScript` kommandon kan ändra värdet för variabeln som har importer ATS från arbets flödets omfattning, men ändringarna visas inte i arbets flödes omfånget. Om du vill göra dem synliga returnerar du det ändrade värdet till arbets flödes omfånget, som du ser i följande exempel.

```powershell
workflow Test-Workflow {
  $a = 3

  ##  Changes to the InlineScript variable value don't
  ##  change the workflow variable.
  InlineScript {
    $a = $Using:a+1;
    "Inline A = $a"
  }
  "Workflow A = $a"

  ##  To change the variable in workflow scope, return the
  ##  new value.
  $a = InlineScript {$b = $Using:a+1; $b}
  "Workflow New A = $a"
}

Test-Workflow
```

```output
Inline A = 4
Workflow A = 3
Workflow New A = 4
```

> [!NOTE]
> En instruktion med `$Using` omfångs modifieraren bör visas innan variabeln används i- `InlineScript` skript blocket.

## <a name="running-in-process"></a>Körs i processen

För att förbättra tillförlitligheten körs kommandona i `InlineScript` skript blocket i sin egen process, separerade från processen där arbets flödet körs, och returnerar sedan utdata till arbets flödes processen.

Om du vill Direct PowerShell för att köra `InlineScript` aktiviteten i arbets flödes processen tar du bort `InlineScript` värdet från **OutOfProcessActivity** -egenskapen i sessionen, till exempel genom att använda `New-PSWorkflowExecutionOption` cmdleten.

### <a name="example"></a>Exempel

`InlineScript`I följande arbets flöde innehåller kommandon som är giltiga i PowerShell, men som inte är giltiga i arbets flöden. Till exempel `New-Object` cmdleten med parametern **ComObject** .

```powershell
workflow Test-Workflow
{
  $ie = InlineScript {
    $ie = New-Object -ComObject InternetExplorer.Application -Property @{navigate2="www.microsoft.com"}

    $ie.Visible = $true
  }

  $ie
}

Test-Workflow
```

## <a name="see-also"></a>Se även

[about_ActivityCommonParameters](about_ActivityCommonParameters.md)

[about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)

[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)

[PSWorkflow](xref:PSWorkflow) -cmdletar

[Arbetsflödesguiden](/previous-versions/powershell/scripting/components/workflows-guide)

[Skriva ett Windows PowerShell-arbetsflöde](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
