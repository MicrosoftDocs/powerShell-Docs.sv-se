---
title: Snabbstart för Windows PowerShell-värd | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 9a080b6db7416ae6bf65a1b0353e9f17a56cc6c5
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64530615"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="142ae-102">Snabbstart för Windows PowerShell-värd</span><span class="sxs-lookup"><span data-stu-id="142ae-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="142ae-103">Om du vill vara värd för Windows PowerShell i ditt program, som du använder den [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) klass.</span><span class="sxs-lookup"><span data-stu-id="142ae-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="142ae-104">Den här klassen innehåller metoder som skapar en pipeline med kommandon och sedan köra dessa kommandon i ett körningsutrymme.</span><span class="sxs-lookup"><span data-stu-id="142ae-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="142ae-105">Det enklaste sättet att skapa ett program är att använda standard-körningsutrymmet.</span><span class="sxs-lookup"><span data-stu-id="142ae-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="142ae-106">Standard-körningsutrymme innehåller alla core Windows PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="142ae-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="142ae-107">Om du vill att programmet att exponera en delmängd av Windows PowerShell-kommandon, måste du skapa en anpassad körningsutrymme.</span><span class="sxs-lookup"><span data-stu-id="142ae-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="142ae-108">Med hjälp av standard-körningsutrymmet</span><span class="sxs-lookup"><span data-stu-id="142ae-108">Using the default runspace</span></span>

<span data-ttu-id="142ae-109">Om du vill starta, vi använda standard-körningsutrymme och använda metoderna i den [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) klassen för att lägga till kommandon, parametrar, instruktioner och skript i en pipeline.</span><span class="sxs-lookup"><span data-stu-id="142ae-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="142ae-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="142ae-110">AddCommand</span></span>

<span data-ttu-id="142ae-111">Du använder den [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) metod för att lägga till kommandon i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="142ae-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="142ae-112">Anta exempelvis att du vill hämta en lista över processer som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="142ae-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="142ae-113">Sättet att köra det här kommandot är som följer.</span><span class="sxs-lookup"><span data-stu-id="142ae-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="142ae-114">Skapa en [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) objekt.</span><span class="sxs-lookup"><span data-stu-id="142ae-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="142ae-115">Lägg till det kommando som du vill köra.</span><span class="sxs-lookup"><span data-stu-id="142ae-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="142ae-116">Anropa kommandot.</span><span class="sxs-lookup"><span data-stu-id="142ae-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="142ae-117">Om du anropar metoden AddCommand mer än en gång innan du anropar den [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metod, resultatet av det första kommandot skickas till andra och så vidare.</span><span class="sxs-lookup"><span data-stu-id="142ae-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="142ae-118">Om du inte vill skicka resultatet av en föregående kommando för att ett kommando lägger du till den genom att anropa den [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) i stället.</span><span class="sxs-lookup"><span data-stu-id="142ae-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="142ae-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="142ae-119">AddParameter</span></span>

<span data-ttu-id="142ae-120">Föregående exempel körs ett enda kommando utan några parametrar.</span><span class="sxs-lookup"><span data-stu-id="142ae-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="142ae-121">Du kan lägga till parametrar i kommandot med hjälp av den [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) metod.</span><span class="sxs-lookup"><span data-stu-id="142ae-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="142ae-122">Till exempel följande kod hämtar en lista över alla processer som namnges `PowerShell` körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="142ae-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="142ae-123">Du kan lägga till ytterligare parametrar genom att anropa metoden AddParameter upprepade gånger.</span><span class="sxs-lookup"><span data-stu-id="142ae-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

<span data-ttu-id="142ae-124">Du kan också lägga till en ordlista över parameternamn och värden som genom att anropa den [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) metod.</span><span class="sxs-lookup"><span data-stu-id="142ae-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="142ae-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="142ae-125">AddStatement</span></span>

<span data-ttu-id="142ae-126">Du kan simulera batchbearbetning med hjälp av den [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) metod, som lägger till en ytterligare instruktion i slutet av pipelinen.</span><span class="sxs-lookup"><span data-stu-id="142ae-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="142ae-127">Följande kod hämtar en lista över processer som körs med namnet `PowerShell`, och sedan hämtar listan över aktiva tjänster.</span><span class="sxs-lookup"><span data-stu-id="142ae-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="142ae-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="142ae-128">AddScript</span></span>

<span data-ttu-id="142ae-129">Du kan köra ett befintligt skript genom att anropa den [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metod.</span><span class="sxs-lookup"><span data-stu-id="142ae-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="142ae-130">I följande exempel lägger till ett skript till pipelinen och kör den.</span><span class="sxs-lookup"><span data-stu-id="142ae-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="142ae-131">Det här exemplet förutsätter att det finns redan ett skript som heter `MyScript.ps1` i en mapp med namnet `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="142ae-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="142ae-132">Det finns också en version av metoden AddScript som använder en boolesk parameter som heter `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="142ae-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="142ae-133">Om den här parametern anges till `true`, och sedan skriptet körs i det lokala scopet.</span><span class="sxs-lookup"><span data-stu-id="142ae-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="142ae-134">Följande kod körs skriptet i det lokala scopet.</span><span class="sxs-lookup"><span data-stu-id="142ae-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="142ae-135">Skapa en anpassad körningsutrymme</span><span class="sxs-lookup"><span data-stu-id="142ae-135">Creating a custom runspace</span></span>

<span data-ttu-id="142ae-136">Du kan skapa ett anpassat körningsutrymme som läser in endast en delmängd av alla kommandon som angivna medan standard-körningsutrymmet som används i föregående exempel har lästs in alla core Windows PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="142ae-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="142ae-137">Du kanske vill göra detta för att förbättra prestanda (läser in fler kommandon är en träff prestanda), eller för att begränsa möjligheterna för användaren att utföra åtgärder.</span><span class="sxs-lookup"><span data-stu-id="142ae-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="142ae-138">Ett körningsutrymme som exponerar endast ett begränsat antal kommandon kallas för ett begränsat körningsutrymme.</span><span class="sxs-lookup"><span data-stu-id="142ae-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="142ae-139">Om du vill skapa ett begränsat körningsutrymme som du använder den [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) och [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) klasser.</span><span class="sxs-lookup"><span data-stu-id="142ae-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="142ae-140">Skapa ett InitialSessionState-objekt</span><span class="sxs-lookup"><span data-stu-id="142ae-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="142ae-141">Om du vill skapa en anpassad körningsutrymme, måste du först skapa en [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objekt.</span><span class="sxs-lookup"><span data-stu-id="142ae-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="142ae-142">I följande exempel använder vi den [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) att skapa ett körningsutrymme när du har skapat ett standard InitialSessionState-objekt.</span><span class="sxs-lookup"><span data-stu-id="142ae-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="142ae-143">Begränsa körningsutrymmet</span><span class="sxs-lookup"><span data-stu-id="142ae-143">Constraining the runspace</span></span>

<span data-ttu-id="142ae-144">I exemplet ovan skapade vi en standard [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objekt som läser in alla av de inbyggda grundläggande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="142ae-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="142ae-145">Vi också har anropat den [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) metod för att skapa ett InitialSessionState-objekt som skulle läsa in kommandona i Microsoft.PowerShell.Core snapin-modulen.</span><span class="sxs-lookup"><span data-stu-id="142ae-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="142ae-146">Om du vill skapa en mer begränsad körningsutrymme, måste du skapa en tom InitialSessionState objekt genom att anropa den [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) metod, och Lägg sedan till kommandon för att den InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="142ae-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="142ae-147">Med hjälp av ett körningsutrymme som läser in endast de kommandon som du anger ger betydligt bättre prestanda.</span><span class="sxs-lookup"><span data-stu-id="142ae-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="142ae-148">Du använder metoderna i den [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) klassen för att definiera-cmdletar för inledande sessionens tillstånd.</span><span class="sxs-lookup"><span data-stu-id="142ae-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="142ae-149">I följande exempel skapar en tom inledande sessionstillstånd, och sedan definierar och lägger till den `Get-Command` och `Import-Module` kommandon för att det inledande sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="142ae-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="142ae-150">Vi sedan skapa ett körningsutrymme begränsas av den första sessionstillstånd och kör kommandon i den körningsutrymme.</span><span class="sxs-lookup"><span data-stu-id="142ae-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="142ae-151">Skapa det första sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="142ae-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="142ae-152">Definiera och Lägg till kommandon till det första sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="142ae-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="142ae-153">Skapa och öppna körningsutrymmet.</span><span class="sxs-lookup"><span data-stu-id="142ae-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="142ae-154">Köra ett kommando och visa resultatet.</span><span class="sxs-lookup"><span data-stu-id="142ae-154">Execute a command and show the result.</span></span>

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

<span data-ttu-id="142ae-155">När du kör, resultatet av den här koden ska se ut så här.</span><span class="sxs-lookup"><span data-stu-id="142ae-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
