---
title: Lägga till och anropa kommandon | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: f776f13fe743a3f5f67de0d94883e3f754040ffc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357759"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="776df-102">Lägga till och anropa kommandon</span><span class="sxs-lookup"><span data-stu-id="776df-102">Adding and invoking commands</span></span>

<span data-ttu-id="776df-103">När du har skapat en körnings utrymme kan du lägga till Windows-PowerShellcommands och skript i en pipeline och sedan anropa pipelinen synkront eller asynkront.</span><span class="sxs-lookup"><span data-stu-id="776df-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="776df-104">Skapa en pipeline</span><span class="sxs-lookup"><span data-stu-id="776df-104">Creating a pipeline</span></span>

 <span data-ttu-id="776df-105">Klassen [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) innehåller flera metoder för att lägga till kommandon, parametrar och skript i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="776df-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="776df-106">Du kan anropa pipelinen synkront genom att anropa en överlagring av metoden [system. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) eller asynkront genom att anropa en överlagring av [systemet. Management. Automation. PowerShell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) och sedan metoden [system. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="776df-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="776df-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="776df-107">AddCommand</span></span>

1. <span data-ttu-id="776df-108">Skapa ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt.</span><span class="sxs-lookup"><span data-stu-id="776df-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="776df-109">Lägg till kommandot som du vill köra.</span><span class="sxs-lookup"><span data-stu-id="776df-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="776df-110">Anropa kommandot.</span><span class="sxs-lookup"><span data-stu-id="776df-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="776df-111">Om du anropar metoden [system. Management. Automation. PowerShell. Addcommand \*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) mer än en gång innan du anropar metoden [system. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) är resultatet av det första kommandot skickas till det andra, och så vidare.</span><span class="sxs-lookup"><span data-stu-id="776df-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="776df-112">Om du inte vill skicka vidare resultatet av ett tidigare kommando till ett kommando lägger du till det genom att anropa [system. Management. Automation. PowerShell. Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) i stället.</span><span class="sxs-lookup"><span data-stu-id="776df-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="776df-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="776df-113">AddParameter</span></span>

 <span data-ttu-id="776df-114">I föregående exempel körs ett enda kommando utan några parametrar.</span><span class="sxs-lookup"><span data-stu-id="776df-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="776df-115">Du kan lägga till parametrar till kommandot med hjälp av metoden [system. Management. Automation. Pscommand. Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) , exempel: följande kod hämtar en lista över alla processer som heter `PowerShell` som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="776df-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="776df-116">Du kan lägga till ytterligare parametrar genom att anropa [system. Management. Automation. Pscommand. Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) upprepade gånger.</span><span class="sxs-lookup"><span data-stu-id="776df-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="776df-117">Du kan också lägga till en ord lista med parameter namn och värden genom att anropa metoden [system. Management. Automation. PowerShell. AddParameters \*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .</span><span class="sxs-lookup"><span data-stu-id="776df-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="776df-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="776df-118">AddStatement</span></span>

 <span data-ttu-id="776df-119">Du kan simulera batching med hjälp av metoden [system. Management. Automation. PowerShell. Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , som lägger till ytterligare en instruktion i slutet av pipelinen. följande kod hämtar en lista över processer som körs med namnet `PowerShell` och hämtar listan över tjänster som körs.</span><span class="sxs-lookup"><span data-stu-id="776df-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="776df-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="776df-120">AddScript</span></span>

 <span data-ttu-id="776df-121">Du kan köra ett befintligt skript genom att anropa metoden [system. Management. Automation. PowerShell. Addscript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) .</span><span class="sxs-lookup"><span data-stu-id="776df-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="776df-122">I följande exempel läggs ett skript till i pipelinen och körs.</span><span class="sxs-lookup"><span data-stu-id="776df-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="776df-123">Det här exemplet förutsätter att det redan finns ett skript med namnet `MyScript.ps1` i en mapp med namnet `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="776df-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="776df-124">Det finns också en version av metoden [system. Management. Automation. PowerShell. Addscript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) som tar en boolesk parameter med namnet `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="776df-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="776df-125">Om den här parametern är inställd på `true` körs skriptet i det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="776df-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="776df-126">Följande kod kommer att köra skriptet i det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="776df-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="776df-127">Anropa en pipeline synkront</span><span class="sxs-lookup"><span data-stu-id="776df-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="776df-128">När du har lagt till element i pipelinen anropar du det.</span><span class="sxs-lookup"><span data-stu-id="776df-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="776df-129">Om du vill anropa pipelinen synkront anropar du en överlagring av metoden [system. Management. Automation. PowerShell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) .</span><span class="sxs-lookup"><span data-stu-id="776df-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="776df-130">I följande exempel visas hur du synkront anropar en pipeline.</span><span class="sxs-lookup"><span data-stu-id="776df-130">The following example shows how to synchronously invoke a pipeline.</span></span>

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

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="776df-131">Anropa en pipeline asynkront</span><span class="sxs-lookup"><span data-stu-id="776df-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="776df-132">Du anropar en pipeline asynkront genom att anropa en överlagring av [system. Management. Automation. PowerShell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) för att skapa ett [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) -objekt och sedan anropa [system. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) -metod.</span><span class="sxs-lookup"><span data-stu-id="776df-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="776df-133">I följande exempel visas hur du anropar en pipeline asynkront.</span><span class="sxs-lookup"><span data-stu-id="776df-133">The following example shows how to invoke a pipeline asynchronously.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="776df-134">Se även</span><span class="sxs-lookup"><span data-stu-id="776df-134">See Also</span></span>

 [<span data-ttu-id="776df-135">Skapa en InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="776df-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="776df-136">Skapa en begränsad körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="776df-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
