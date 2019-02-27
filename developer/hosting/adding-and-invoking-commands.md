---
title: Att lägga till och anropa kommandon | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 31371797ee57f07075da3436e0b42b2ca01aaffd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847756"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="7b4de-102">Lägga till och anropa kommandon</span><span class="sxs-lookup"><span data-stu-id="7b4de-102">Adding and invoking commands</span></span>

<span data-ttu-id="7b4de-103">När du har skapat ett körningsutrymme, kan du lägga till Windows PowerShellcommands och skript för en pipeline och sedan anropa pipelinen synkront eller asynkront.</span><span class="sxs-lookup"><span data-stu-id="7b4de-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="7b4de-104">Skapa en pipeline</span><span class="sxs-lookup"><span data-stu-id="7b4de-104">Creating a pipeline</span></span>

 <span data-ttu-id="7b4de-105">Den [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klassen innehåller flera metoder för att lägga till kommandon, parametrar och skript till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="7b4de-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="7b4de-106">Du kan anropa pipelinen synkront genom att anropa en överlagring för den [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metoden eller asynkront genom att anropa en överlagring för den [ System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) och sedan den [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) metod.</span><span class="sxs-lookup"><span data-stu-id="7b4de-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="7b4de-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="7b4de-107">AddCommand</span></span>

1. <span data-ttu-id="7b4de-108">Skapa en [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objekt.</span><span class="sxs-lookup"><span data-stu-id="7b4de-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="7b4de-109">Lägg till det kommando som du vill köra.</span><span class="sxs-lookup"><span data-stu-id="7b4de-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="7b4de-110">Anropa kommandot.</span><span class="sxs-lookup"><span data-stu-id="7b4de-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="7b4de-111">Om du anropar den [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) metod som är mer än en gång innan du anropar den [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metod, resultatet av den första kommandot skickas till andra och så vidare.</span><span class="sxs-lookup"><span data-stu-id="7b4de-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="7b4de-112">Om du inte vill skicka resultatet av en föregående kommando för att ett kommando lägger du till den genom att anropa den [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) i stället.</span><span class="sxs-lookup"><span data-stu-id="7b4de-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="7b4de-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="7b4de-113">AddParameter</span></span>

 <span data-ttu-id="7b4de-114">Föregående exempel körs ett enda kommando utan några parametrar.</span><span class="sxs-lookup"><span data-stu-id="7b4de-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="7b4de-115">Du kan lägga till parametrar i kommandot med hjälp av den [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) metod till exempel följande kod hämtar en lista över alla processer som namnges `PowerShell` som körs på den datorn.</span><span class="sxs-lookup"><span data-stu-id="7b4de-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="7b4de-116">Du kan lägga till ytterligare parametrar genom att anropa [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) upprepade gånger.</span><span class="sxs-lookup"><span data-stu-id="7b4de-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="7b4de-117">Du kan också lägga till en ordlista över parameternamn och värden som genom att anropa den [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) metod.</span><span class="sxs-lookup"><span data-stu-id="7b4de-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="7b4de-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="7b4de-118">AddStatement</span></span>

 <span data-ttu-id="7b4de-119">Du kan simulera batchbearbetning med hjälp av den [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) metod, som lägger till en ytterligare instruktion i slutet av din pipeline för följande kod hämtar en lista över processer som körs med namnet `PowerShell`, och sedan hämtar listan över aktiva tjänster.</span><span class="sxs-lookup"><span data-stu-id="7b4de-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="7b4de-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="7b4de-120">AddScript</span></span>

 <span data-ttu-id="7b4de-121">Du kan köra ett befintligt skript genom att anropa den [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metod.</span><span class="sxs-lookup"><span data-stu-id="7b4de-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="7b4de-122">I följande exempel lägger till ett skript till pipelinen och kör den.</span><span class="sxs-lookup"><span data-stu-id="7b4de-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="7b4de-123">Det här exemplet förutsätter att det finns redan ett skript som heter `MyScript.ps1` i en mapp med namnet `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="7b4de-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="7b4de-124">Det finns också en version av den [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metod som tar en boolesk parameter som heter `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="7b4de-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="7b4de-125">Om den här parametern anges till `true`, och sedan skriptet körs i det lokala scopet.</span><span class="sxs-lookup"><span data-stu-id="7b4de-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="7b4de-126">Följande kod körs skriptet i det lokala scopet.</span><span class="sxs-lookup"><span data-stu-id="7b4de-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="7b4de-127">Anropa en pipeline synkront</span><span class="sxs-lookup"><span data-stu-id="7b4de-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="7b4de-128">När du lägger till element i pipelinen anropar den.</span><span class="sxs-lookup"><span data-stu-id="7b4de-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="7b4de-129">Om du vill anropa pipelinen synkront du anropar en överlagring för den [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metod.</span><span class="sxs-lookup"><span data-stu-id="7b4de-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="7b4de-130">I följande exempel visar hur du synkroniserat anropa en pipeline.</span><span class="sxs-lookup"><span data-stu-id="7b4de-130">The following example shows how to synchronously invoke a pipeline.</span></span>

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

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="7b4de-131">Anropa en pipeline asynkront</span><span class="sxs-lookup"><span data-stu-id="7b4de-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="7b4de-132">Du anropar en pipeline asynkront genom att anropa en överlagring för den [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) att skapa en [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) objektet och sedan anropa den [ System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) metod.</span><span class="sxs-lookup"><span data-stu-id="7b4de-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="7b4de-133">I följande exempel visas hur du anropar en pipeline-asynchronoulsy.</span><span class="sxs-lookup"><span data-stu-id="7b4de-133">The following example shows how to invoke a pipeline asynchronoulsy.</span></span>

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
      // Get-Process cmdlet. Do not include spaces immediatly
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

## <a name="see-also"></a><span data-ttu-id="7b4de-134">Se även</span><span class="sxs-lookup"><span data-stu-id="7b4de-134">See Also</span></span>

 [<span data-ttu-id="7b4de-135">Skapa en InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="7b4de-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="7b4de-136">Skapa en begränsad körningsutrymme</span><span class="sxs-lookup"><span data-stu-id="7b4de-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
