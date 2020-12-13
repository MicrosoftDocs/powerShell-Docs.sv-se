---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa ett begränsat körningsutrymme
description: Skapa ett begränsat körningsutrymme
ms.openlocfilehash: 53fee3cc7d8625425bc6a73196aee9eee7f17ed6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651166"
---
# <a name="creating-a-constrained-runspace"></a><span data-ttu-id="548ce-103">Skapa ett begränsat körningsutrymme</span><span class="sxs-lookup"><span data-stu-id="548ce-103">Creating a constrained runspace</span></span>

<span data-ttu-id="548ce-104">Av prestanda-eller säkerhets skäl kanske du vill begränsa vilka Windows PowerShell-kommandon som är tillgängliga för värd programmet.</span><span class="sxs-lookup"><span data-stu-id="548ce-104">For performance or security reasons, you might want to restrict the Windows PowerShell commands available to your host application.</span></span> <span data-ttu-id="548ce-105">Om du vill göra det skapar du en tom [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) genom att anropa [System.Management.Automation.Runspaces.Initialsessionstate. Skapa \*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) Metod och Lägg sedan till endast de kommandon som du vill ha tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="548ce-105">To do this you create an empty [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) by calling the [System.Management.Automation.Runspaces.Initialsessionstate.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add only the commands you want available.</span></span>

 <span data-ttu-id="548ce-106">Om du använder en körnings utrymme som bara läser in de kommandon som du anger får du avsevärt bättre prestanda.</span><span class="sxs-lookup"><span data-stu-id="548ce-106">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

 <span data-ttu-id="548ce-107">Du kan använda metoderna i klassen [system. Management. Automation. körnings utrymmen. Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) för att definiera cmdletar för det första sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="548ce-107">You use the methods of the [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>

 <span data-ttu-id="548ce-108">Du kan också göra kommandon privata.</span><span class="sxs-lookup"><span data-stu-id="548ce-108">You can also make commands private.</span></span> <span data-ttu-id="548ce-109">Privata kommandon kan användas av värd programmet, men inte av användare av programmet.</span><span class="sxs-lookup"><span data-stu-id="548ce-109">Private commands can be used by the host application, but not by users of the application.</span></span>

## <a name="adding-commands-to-an-empty-runspace"></a><span data-ttu-id="548ce-110">Lägga till kommandon till en tom körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="548ce-110">Adding commands to an empty runspace</span></span>

 <span data-ttu-id="548ce-111">Följande exempel visar hur du skapar en tom InitialSessionState och lägger till kommandon i den.</span><span class="sxs-lookup"><span data-stu-id="548ce-111">The following example demonstrates how to create an empty InitialSessionState and add commands to it.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using Microsoft.PowerShell.Commands;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class Runspace10b
  {
    /// <summary>
    /// This sample shows how to create an empty initial session state,
    /// how to add commands to the session state, and then how to create a
    /// runspace that has only those two commands. A PowerShell object
    /// is used to run the Get-Command cmdlet to show that only two commands
    /// are available.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create an empty InitialSessionState and then add two commands.
      InitialSessionState iss = InitialSessionState.Create();

      // Add the Get-Process and Get-Command cmdlets to the session state.
      SessionStateCmdletEntry ssce1 = new SessionStateCmdletEntry(
                                                            "get-process",
                                                            typeof(GetProcessCommand),
                                                            null);
      iss.Commands.Add(ssce1);

      SessionStateCmdletEntry ssce2 = new SessionStateCmdletEntry(
                                                            "get-command",
                                                            typeof(GetCommandCommand),
                                                            null);
      iss.Commands.Add(ssce2);

      // Create a runspace.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Create a pipeline with the Get-Command command.
          powershell.AddCommand("get-command");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Verb                 Noun");
          Console.WriteLine("----------------------------");

          // Display each result object.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                             "{0,-20} {1}",
                             result.Members["verb"].Value,
                             result.Members["Noun"].Value);
          }
        }

        // Close the runspace and release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="making-commands-private"></a><span data-ttu-id="548ce-112">Göra kommandon privata</span><span class="sxs-lookup"><span data-stu-id="548ce-112">Making commands private</span></span>

 <span data-ttu-id="548ce-113">Du kan också göra ett kommando privat genom att ställa in egenskapen [system. Management. Automation. Commandinfo. visibility](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) på [system. Management. Automation. SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **Private**.</span><span class="sxs-lookup"><span data-stu-id="548ce-113">You can also make a command private, by setting it's [System.Management.Automation.Commandinfo.Visibility](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) property to [System.Management.Automation.SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **Private**.</span></span> <span data-ttu-id="548ce-114">Värd programmet och andra kommandon kan anropa det kommandot, men användare av programmet kan inte.</span><span class="sxs-lookup"><span data-stu-id="548ce-114">The host application and other commands can call that command, but the user of the application cannot.</span></span> <span data-ttu-id="548ce-115">I följande exempel är kommandot [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) privat.</span><span class="sxs-lookup"><span data-stu-id="548ce-115">In the following example, the [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) command is private.</span></span>

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a><span data-ttu-id="548ce-116">Se även</span><span class="sxs-lookup"><span data-stu-id="548ce-116">See Also</span></span>

 [<span data-ttu-id="548ce-117">Skapa en InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="548ce-117">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)
