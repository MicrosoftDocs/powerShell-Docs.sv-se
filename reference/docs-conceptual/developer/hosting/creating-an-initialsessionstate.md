---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa en InitialSessionState
description: Skapa en InitialSessionState
ms.openlocfilehash: d58a32c2ae8a22132f3095d093e3cb322f65c486
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649420"
---
# <a name="creating-an-initialsessionstate"></a>Skapa en InitialSessionState

PowerShell-kommandon körs i en körnings utrymme.
För att vara värd för PowerShell i ditt program måste du skapa ett [system. Management. Automation. körnings utrymmen. körnings utrymme](/dotnet/api/System.Management.Automation.Runspaces.Runspace) -objekt.
Varje körnings utrymme har ett kopplat [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt.
InitialSessionState anger egenskaperna för körnings utrymme, till exempel vilka kommandon, variabler och moduler som är tillgängliga för den körnings utrymme.

## <a name="create-a-default-initialsessionstate"></a>Skapa en standard-InitialSessionState

Metoderna [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) och [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) för klassen **InitialSessionState** kan användas för att skapa ett **InitialSessionState** -objekt.
Metoden **CreateDefault** skapar en **InitialSessionState** med alla inbyggda kommandon som lästs in, medan metoden **CreateDefault2** bara läser in de kommandon som krävs för att vara värd för PowerShell (kommandona från Microsoft. PowerShell. Core-modulen).

Om du vill begränsa vilka kommandon som är tillgängliga i värd programmet ytterligare måste du skapa en begränsad körnings utrymme.
Mer information finns i [skapa en begränsad körnings utrymme](creating-a-constrained-runspace.md).

Följande kod visar hur du skapar en **InitialSessionState**, tilldelar den till en körnings utrymme, lägger till kommandon i pipelinen i körnings utrymme och anropar kommandona.
Mer information om hur du lägger till och anropar kommandon finns i [lägga till och anropa kommandon](adding-and-invoking-commands.md).

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

[Skapa ett begränsat körningsutrymme](creating-a-constrained-runspace.md)

[Lägga till och anropa kommandon](adding-and-invoking-commands.md)
