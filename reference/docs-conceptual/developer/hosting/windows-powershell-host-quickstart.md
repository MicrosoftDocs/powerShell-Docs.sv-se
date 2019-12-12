---
title: Snabb start för Windows PowerShell-värd | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 390eb2d0153c65967d8c0711c852aa6e13fe4660
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352992"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="93adf-102">Snabbstart för Windows PowerShell-värd</span><span class="sxs-lookup"><span data-stu-id="93adf-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="93adf-103">För att vara värd för Windows PowerShell i ditt program använder du klassen [system. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) .</span><span class="sxs-lookup"><span data-stu-id="93adf-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="93adf-104">Den här klassen innehåller metoder som skapar en pipeline med kommandon och sedan kör dessa kommandon i en körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="93adf-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="93adf-105">Det enklaste sättet att skapa ett värd program är att använda standard körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="93adf-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="93adf-106">Standard-körnings utrymme innehåller alla Windows PowerShell-kommandon i kärnan.</span><span class="sxs-lookup"><span data-stu-id="93adf-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="93adf-107">Om du vill att programmet endast ska exponera en delmängd av Windows PowerShell-kommandon måste du skapa en anpassad körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="93adf-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="93adf-108">Använda standard körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="93adf-108">Using the default runspace</span></span>

<span data-ttu-id="93adf-109">För att starta ska vi använda standard-körnings utrymme och använda metoderna i klassen [system. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) för att lägga till kommandon, parametrar, instruktioner och skript i en pipeline.</span><span class="sxs-lookup"><span data-stu-id="93adf-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="93adf-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="93adf-110">AddCommand</span></span>

<span data-ttu-id="93adf-111">Du använder metoden [system. Management. Automation. PowerShell. AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) för att lägga till kommandon i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="93adf-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="93adf-112">Anta till exempel att du vill hämta en lista över processer som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="93adf-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="93adf-113">Du kan köra det här kommandot på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="93adf-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="93adf-114">Skapa ett [system. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) -objekt.</span><span class="sxs-lookup"><span data-stu-id="93adf-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="93adf-115">Lägg till kommandot som du vill köra.</span><span class="sxs-lookup"><span data-stu-id="93adf-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="93adf-116">Anropa kommandot.</span><span class="sxs-lookup"><span data-stu-id="93adf-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="93adf-117">Om du anropar AddCommand-metoden mer än en gång innan du anropar metoden [system. Management. Automation. PowerShell. Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , är resultatet av det första kommandot skickas till det andra, och så vidare.</span><span class="sxs-lookup"><span data-stu-id="93adf-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="93adf-118">Om du inte vill skicka vidare resultatet av ett tidigare kommando till ett kommando, lägger du till det genom att anropa [system. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) i stället.</span><span class="sxs-lookup"><span data-stu-id="93adf-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="93adf-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="93adf-119">AddParameter</span></span>

<span data-ttu-id="93adf-120">I föregående exempel körs ett enda kommando utan några parametrar.</span><span class="sxs-lookup"><span data-stu-id="93adf-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="93adf-121">Du kan lägga till parametrar till kommandot med hjälp av metoden [system. Management. Automation. PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) .</span><span class="sxs-lookup"><span data-stu-id="93adf-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="93adf-122">Följande kod hämtar till exempel en lista över alla processer som heter `PowerShell` körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="93adf-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="93adf-123">Du kan lägga till ytterligare parametrar genom att anropa metoden AddParameter upprepade gånger.</span><span class="sxs-lookup"><span data-stu-id="93adf-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

<span data-ttu-id="93adf-124">Du kan också lägga till en ord lista med parameter namn och värden genom att anropa metoden [system. Management. Automation. PowerShell. AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .</span><span class="sxs-lookup"><span data-stu-id="93adf-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="93adf-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="93adf-125">AddStatement</span></span>

<span data-ttu-id="93adf-126">Du kan simulera batching med hjälp av metoden [system. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , som lägger till ytterligare en instruktion i slutet av pipelinen.</span><span class="sxs-lookup"><span data-stu-id="93adf-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="93adf-127">Följande kod hämtar en lista över processer som körs med namnet `PowerShell`och hämtar sedan listan över tjänster som körs.</span><span class="sxs-lookup"><span data-stu-id="93adf-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="93adf-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="93adf-128">AddScript</span></span>

<span data-ttu-id="93adf-129">Du kan köra ett befintligt skript genom att anropa metoden [system. Management. Automation. PowerShell. AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) .</span><span class="sxs-lookup"><span data-stu-id="93adf-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="93adf-130">I följande exempel läggs ett skript till i pipelinen och körs.</span><span class="sxs-lookup"><span data-stu-id="93adf-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="93adf-131">Det här exemplet förutsätter att det redan finns ett skript med namnet `MyScript.ps1` i en mapp med namnet `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="93adf-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="93adf-132">Det finns också en version av AddScript-metoden som tar en boolesk parameter med namnet `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="93adf-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="93adf-133">Om den här parametern är inställd på `true`körs skriptet i det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="93adf-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="93adf-134">Följande kod kommer att köra skriptet i det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="93adf-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="93adf-135">Skapa en anpassad körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="93adf-135">Creating a custom runspace</span></span>

<span data-ttu-id="93adf-136">Även om standard-körnings utrymme som används i föregående exempel läser in alla viktiga Windows PowerShell-kommandon, kan du skapa en anpassad körnings utrymme som endast läser in en viss delmängd av alla kommandon.</span><span class="sxs-lookup"><span data-stu-id="93adf-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="93adf-137">Du kanske vill göra detta för att förbättra prestandan (att läsa in ett stort antal kommandon är en prestanda träff) eller att begränsa möjligheten för användaren att utföra åtgärder.</span><span class="sxs-lookup"><span data-stu-id="93adf-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="93adf-138">En körnings utrymme som visar bara ett begränsat antal kommandon kallas för en begränsad körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="93adf-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="93adf-139">Om du vill skapa en begränsad körnings utrymme använder du klasserna [system. Management. Automation. körnings utrymmen. körnings utrymme](/dotnet/api/System.Management.Automation.Runspaces.Runspace) och [system. Management. Automation. körnings utrymmen. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="93adf-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="93adf-140">Skapa ett InitialSessionState-objekt</span><span class="sxs-lookup"><span data-stu-id="93adf-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="93adf-141">Om du vill skapa en anpassad körnings utrymme måste du först skapa ett [system. Management. Automation. körnings utrymmen. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt.</span><span class="sxs-lookup"><span data-stu-id="93adf-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="93adf-142">I följande exempel använder vi [system. Management. Automation. körnings utrymmen. RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) för att skapa en körnings utrymme när du har skapat ett standard InitialSessionState-objekt.</span><span class="sxs-lookup"><span data-stu-id="93adf-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="93adf-143">Begränsa körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="93adf-143">Constraining the runspace</span></span>

<span data-ttu-id="93adf-144">I föregående exempel skapade vi ett standard [system. Management. Automation. körnings utrymmen. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt som läser in alla inbyggda kärnor i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93adf-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="93adf-145">Vi kan också ha anropat metoden [system. Management. Automation. körnings utrymmen. InitialSessionState. CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) för att skapa ett InitialSessionState-objekt som endast läser in kommandona i snapin-modulen Microsoft. PowerShell. Core.</span><span class="sxs-lookup"><span data-stu-id="93adf-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="93adf-146">Om du vill skapa en mer begränsad körnings utrymme måste du skapa ett tomt InitialSessionState-objekt genom att anropa metoden [system. Management. Automation. körnings utrymmen. InitialSessionState. Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) och sedan lägga till kommandon i InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="93adf-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="93adf-147">Om du använder en körnings utrymme som bara läser in de kommandon som du anger får du avsevärt bättre prestanda.</span><span class="sxs-lookup"><span data-stu-id="93adf-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="93adf-148">Du kan använda metoderna i klassen [system. Management. Automation. körnings utrymmen. SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) för att definiera cmdletar för det första sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="93adf-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="93adf-149">I följande exempel skapas ett tomt tillstånd för inledande session och sedan definieras och läggs till `Get-Command` och `Import-Module` kommandon i det första sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="93adf-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="93adf-150">Vi skapar sedan en körnings utrymme som är begränsad av det första sessionstillståndet och kör kommandona i den körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="93adf-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="93adf-151">Skapa det första sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="93adf-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="93adf-152">Definiera och Lägg till kommandon i det första sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="93adf-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="93adf-153">Skapa och öppna körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="93adf-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="93adf-154">Kör ett kommando och visa resultatet.</span><span class="sxs-lookup"><span data-stu-id="93adf-154">Execute a command and show the result.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

<span data-ttu-id="93adf-155">När det körs kommer utdata från den här koden att se ut så här.</span><span class="sxs-lookup"><span data-stu-id="93adf-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
