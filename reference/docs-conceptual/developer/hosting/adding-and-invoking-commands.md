---
ms.date: 09/13/2016
ms.topic: reference
title: Lägga till och anropa kommandon
description: Lägga till och anropa kommandon
ms.openlocfilehash: c30cb15d473c344e40b96938c355d77c059fe2d5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96616037"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="9fb2d-103">Lägga till och anropa kommandon</span><span class="sxs-lookup"><span data-stu-id="9fb2d-103">Adding and invoking commands</span></span>

<span data-ttu-id="9fb2d-104">När du har skapat en körnings utrymme kan du lägga till Windows-PowerShellcommands och skript i en pipeline och sedan anropa pipelinen synkront eller asynkront.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-104">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="9fb2d-105">Skapa en pipeline</span><span class="sxs-lookup"><span data-stu-id="9fb2d-105">Creating a pipeline</span></span>

<span data-ttu-id="9fb2d-106">Klassen [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) innehåller flera metoder för att lägga till kommandon, parametrar och skript i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-106">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="9fb2d-107">Du kan anropa pipelinen synkront genom att anropa en överlagring av metoden [system. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) eller asynkront genom att anropa en överlagring av [system. Management. Automation. PowerShell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) och sedan metoden [system. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="9fb2d-107">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="9fb2d-108">AddCommand</span><span class="sxs-lookup"><span data-stu-id="9fb2d-108">AddCommand</span></span>

1. <span data-ttu-id="9fb2d-109">Skapa ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-109">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="9fb2d-110">Lägg till kommandot som du vill köra.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-110">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="9fb2d-111">Anropa kommandot.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-111">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="9fb2d-112">Om du anropar metoden [system. Management. Automation. PowerShell. Addcommand \*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) mer än en gång innan du anropar metoden [system. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) är resultatet av det första kommandot skickas till det andra, och så vidare.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-112">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="9fb2d-113">Om du inte vill skicka vidare resultatet av ett tidigare kommando till ett kommando lägger du till det genom att anropa [system. Management. Automation. PowerShell. Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) i stället.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-113">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="9fb2d-114">AddParameter</span><span class="sxs-lookup"><span data-stu-id="9fb2d-114">AddParameter</span></span>

 <span data-ttu-id="9fb2d-115">I föregående exempel körs ett enda kommando utan några parametrar.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-115">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="9fb2d-116">Du kan lägga till parametrar till kommandot med hjälp av metoden [system. Management. Automation. Pscommand. Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) , exempel: följande kod hämtar en lista över alla processer som heter `PowerShell` körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-116">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="9fb2d-117">Du kan lägga till ytterligare parametrar genom att anropa [system. Management. Automation. Pscommand. Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) upprepade gånger.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-117">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Command")
                   .AddParameter("Name", "Get-VM")
                   .AddParameter("Module", "Hyper-V")
                   .Invoke();
```

<span data-ttu-id="9fb2d-118">Du kan också lägga till en ord lista med parameter namn och värden genom att anropa metoden [system. Management. Automation. PowerShell. AddParameters \*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .</span><span class="sxs-lookup"><span data-stu-id="9fb2d-118">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "Get-VM");

parameters.Add("Module", "Hyper-V");
PowerShell.Create().AddCommand("Get-Command")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="9fb2d-119">AddStatement</span><span class="sxs-lookup"><span data-stu-id="9fb2d-119">AddStatement</span></span>

<span data-ttu-id="9fb2d-120">Du kan simulera batching med hjälp av metoden [system. Management. Automation. PowerShell. Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , som lägger till ytterligare en instruktion i slutet av pipelinen. följande kod hämtar en lista över processer som körs med namnet `PowerShell` och hämtar sedan listan över tjänster som körs.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-120">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="9fb2d-121">AddScript</span><span class="sxs-lookup"><span data-stu-id="9fb2d-121">AddScript</span></span>

<span data-ttu-id="9fb2d-122">Du kan köra ett befintligt skript genom att anropa metoden [system. Management. Automation. PowerShell. Addscript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) .</span><span class="sxs-lookup"><span data-stu-id="9fb2d-122">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="9fb2d-123">I följande exempel läggs ett skript till i pipelinen och körs.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-123">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="9fb2d-124">Det här exemplet förutsätter att det redan finns ett skript `MyScript.ps1` som heter i en mapp med namnet `D:\PSScripts` .</span><span class="sxs-lookup"><span data-stu-id="9fb2d-124">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="9fb2d-125">Det finns också en version av metoden [system. Management. Automation. PowerShell. Addscript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) som tar en boolesk parameter med namnet `useLocalScope` .</span><span class="sxs-lookup"><span data-stu-id="9fb2d-125">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="9fb2d-126">Om den här parametern är inställd på `true` körs skriptet i det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-126">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="9fb2d-127">Följande kod kommer att köra skriptet i det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-127">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="9fb2d-128">Anropa en pipeline synkront</span><span class="sxs-lookup"><span data-stu-id="9fb2d-128">Invoking a pipeline synchronously</span></span>

<span data-ttu-id="9fb2d-129">När du har lagt till element i pipelinen anropar du det.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-129">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="9fb2d-130">Om du vill anropa pipelinen synkront anropar du en överlagring av metoden [system. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) .</span><span class="sxs-lookup"><span data-stu-id="9fb2d-130">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="9fb2d-131">I följande exempel visas hur du synkront anropar en pipeline.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-131">The following example shows how to synchronously invoke a pipeline.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="9fb2d-132">Anropa en pipeline asynkront</span><span class="sxs-lookup"><span data-stu-id="9fb2d-132">Invoking a pipeline asynchronously</span></span>

<span data-ttu-id="9fb2d-133">Du anropar en pipeline asynkront genom att anropa en överlagring av [system. Management. Automation. PowerShell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) för att skapa ett [IAsyncResult](/dotnet/api/system.iasyncresult) -objekt och sedan anropa metoden [system. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="9fb2d-133">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](/dotnet/api/system.iasyncresult) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="9fb2d-134">I följande exempel visas hur du anropar en pipeline asynkront.</span><span class="sxs-lookup"><span data-stu-id="9fb2d-134">The following example shows how to invoke a pipeline asynchronously.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a><span data-ttu-id="9fb2d-135">Se även</span><span class="sxs-lookup"><span data-stu-id="9fb2d-135">See Also</span></span>

 [<span data-ttu-id="9fb2d-136">Skapa en InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="9fb2d-136">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="9fb2d-137">Skapa ett begränsat körningsutrymme</span><span class="sxs-lookup"><span data-stu-id="9fb2d-137">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
