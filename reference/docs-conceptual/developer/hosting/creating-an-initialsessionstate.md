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
ms.sourcegitcommit: 4eda0bc902658d4a188159bd7310e64399f6e178
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83271890"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="84493-102">Skapa en InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="84493-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="84493-103">PowerShell-kommandon körs i en körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="84493-103">PowerShell commands run in a runspace.</span></span>
<span data-ttu-id="84493-104">För att vara värd för PowerShell i ditt program måste du skapa ett [system. Management. Automation. körnings utrymmen. körnings utrymme](/dotnet/api/System.Management.Automation.Runspaces.Runspace) -objekt.</span><span class="sxs-lookup"><span data-stu-id="84493-104">To host PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>
<span data-ttu-id="84493-105">Varje körnings utrymme har ett [system. Management. Automation. körnings utrymmen. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt som är kopplat till det.</span><span class="sxs-lookup"><span data-stu-id="84493-105">Every runspace has an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span>
<span data-ttu-id="84493-106">InitialSessionState anger egenskaperna för körnings utrymme, till exempel vilka kommandon, variabler och moduler som är tillgängliga för den körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="84493-106">The InitialSessionState specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="84493-107">Skapa en standard-InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="84493-107">Create a default InitialSessionState</span></span>

<span data-ttu-id="84493-108">Metoderna [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) och [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) för klassen **InitialSessionState** kan användas för att skapa ett **InitialSessionState** -objekt.</span><span class="sxs-lookup"><span data-stu-id="84493-108">The [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) and [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods of the **InitialSessionState** class can be used to create an **InitialSessionState** object.</span></span>
<span data-ttu-id="84493-109">Metoden **CreateDefault** skapar en **InitialSessionState** med alla inbyggda kommandon som lästs in, medan metoden **CreateDefault2** bara läser in de kommandon som krävs för att vara värd för PowerShell (kommandona från Microsoft. PowerShell. Core-modulen).</span><span class="sxs-lookup"><span data-stu-id="84493-109">The **CreateDefault** method creates an **InitialSessionState** with all of the built-in commands loaded, while the **CreateDefault2** method loads only the commands required to host PowerShell (the commands from the Microsoft.PowerShell.Core module).</span></span>

<span data-ttu-id="84493-110">Om du vill begränsa vilka kommandon som är tillgängliga i värd programmet ytterligare måste du skapa en begränsad körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="84493-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span>
<span data-ttu-id="84493-111">Mer information finns i [skapa en begränsad körnings utrymme](creating-a-constrained-runspace.md).</span><span class="sxs-lookup"><span data-stu-id="84493-111">For information, see [Creating a constrained runspace](creating-a-constrained-runspace.md).</span></span>

<span data-ttu-id="84493-112">Följande kod visar hur du skapar en **InitialSessionState**, tilldelar den till en körnings utrymme, lägger till kommandon i pipelinen i körnings utrymme och anropar kommandona.</span><span class="sxs-lookup"><span data-stu-id="84493-112">The following code shows how to create an **InitialSessionState**, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span>
<span data-ttu-id="84493-113">Mer information om hur du lägger till och anropar kommandon finns i [lägga till och anropa kommandon](adding-and-invoking-commands.md).</span><span class="sxs-lookup"><span data-stu-id="84493-113">For more information about adding and invoking commands, see [Adding and invoking commands](adding-and-invoking-commands.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="84493-114">Se även</span><span class="sxs-lookup"><span data-stu-id="84493-114">See Also</span></span>

[<span data-ttu-id="84493-115">Skapa ett begränsat körningsutrymme</span><span class="sxs-lookup"><span data-stu-id="84493-115">Creating a constrained runspace</span></span>](creating-a-constrained-runspace.md)

[<span data-ttu-id="84493-116">Lägga till och anropa kommandon</span><span class="sxs-lookup"><span data-stu-id="84493-116">Adding and invoking commands</span></span>](adding-and-invoking-commands.md)
