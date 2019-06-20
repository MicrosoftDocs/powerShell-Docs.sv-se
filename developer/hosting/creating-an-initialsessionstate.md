---
title: Skapa en InitialSessionState | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 9140d03e046def2fbbcc2a842b9ea1b9e1fa2985
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263833"
---
# <a name="creating-an-initialsessionstate"></a>Skapa en InitialSessionState

PowerShell-kommandon körs i ett körningsutrymme.
Om du vill vara värd för PowerShell i ditt program, måste du skapa en [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) objekt.
Varje körningsutrymme har en [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objektet som är associerat med den.
InitialSessionState anger egenskaperna för körningsutrymme, till exempel vilka kommandon, variabler och moduler som är tillgängliga för den körningsutrymme.

## <a name="create-a-default-initialsessionstate"></a>Skapa en standardprincip för InitialSessionState

Den [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) och [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) metoderna i den **InitialSessionState** klassen kan användas för att skapa en **InitialSessionState**objekt.
Den **CreateDefault** metoden skapar en **InitialSessionState** med alla inbyggda kommandon som lästs in, samtidigt som den **CreateDefault2** metoden läser in endast kommandon krävs för att värden PowerShell (kommandon från modulen Microsoft.PowerShell.Core).

Om du vill att ytterligare begränsa kommandona som är tillgängliga i din värdapp måste du skapa ett begränsat körningsutrymme.
Mer information finns i [skapar en begränsad körningsutrymme](creating-a-constrained-runspace.md).

Följande kod visar hur du skapar en **InitialSessionState**, tilldela den till ett körningsutrymme, Lägg till kommandon till pipelinen i den körningsutrymme och anropa kommandon.
Mer information om att lägga till och anropa kommandon finns i [när du lägger till och anropa kommandon](adding-and-invoking-commands.md).

```csharp
namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell object,
      // and then specify the runspace and commands to the pipeline.
      // and create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
      foreach (PSObject result in ps.Invoke())
      {
        Console.WriteLine("{0,-20}{1}",
            result.Members["Name"].Value,
            result.Members["Value"].Value);
      } // End foreach.

      // Close the runspace to free resources.
      rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a>Se även

[Skapa en begränsad körningsutrymme](creating-a-constrained-runspace.md)

[Att lägga till och anropa kommandon](adding-and-invoking-commands.md)
