---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea powershell säkerhet"
title: "Med hjälp av JEA"
ms.openlocfilehash: f0c22bf0f823b9fafa203e7f98049a6a6b3b7c05
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="using-jea"></a><span data-ttu-id="76b4b-103">Med hjälp av JEA</span><span class="sxs-lookup"><span data-stu-id="76b4b-103">Using JEA</span></span>

> <span data-ttu-id="76b4b-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="76b4b-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="76b4b-105">Det här avsnittet beskrivs de olika sätt som du kan ansluta till och använda en JEA slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="76b4b-105">This topic describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="76b4b-106">Använda JEA interaktivt</span><span class="sxs-lookup"><span data-stu-id="76b4b-106">Using JEA interactively</span></span>

<span data-ttu-id="76b4b-107">Om du vill testa konfigurationen JEA eller har enkla uppgifter för användare att utföra kan du använda JEA på samma sätt som en vanlig PowerShell-session för fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="76b4b-107">If you are testing your JEA configuration or have simple tasks for users to perform, you can use JEA the same way you would a regular PowerShell remoting session.</span></span>
<span data-ttu-id="76b4b-108">För komplexa fjärrkommunikation aktiviteter, rekommenderas att använda [implicit fjärrkommunikation](#using-jea-with-implicit-remoting) i stället för att göra det enklare för användarna genom att tillåta användare att arbeta med data objekt lokalt.</span><span class="sxs-lookup"><span data-stu-id="76b4b-108">For complex remoting tasks, it is recommended to use [implicit remoting](#using-jea-with-implicit-remoting) instead to make it easier for your users by allowing users to operate with the data objects locally.</span></span>

<span data-ttu-id="76b4b-109">Om du vill använda JEA interaktivt, behöver du:</span><span class="sxs-lookup"><span data-stu-id="76b4b-109">To use JEA interactively, you will need:</span></span>
- <span data-ttu-id="76b4b-110">Namnet på den dator som du ansluter till (kan vara den lokala datorn)</span><span class="sxs-lookup"><span data-stu-id="76b4b-110">The name of the computer you are connecting to (can be the local machine)</span></span>
- <span data-ttu-id="76b4b-111">Namnet på slutpunkten JEA registrerad på datorn</span><span class="sxs-lookup"><span data-stu-id="76b4b-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="76b4b-112">Autentiseringsuppgifter för datorn som har åtkomst till JEA slutpunkten</span><span class="sxs-lookup"><span data-stu-id="76b4b-112">Credentials for the computer that have access to the JEA endpoint</span></span>

<span data-ttu-id="76b4b-113">Med informationen i manuellt, kan du starta en JEA sessionen med hjälp av [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) eller [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="76b4b-113">With that information in hand, you can start a JEA session using [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="76b4b-114">Om det konto som du är för närvarande inloggad som har åtkomst till JEA slutpunkten kan du utelämna den `-Credential` parameter.</span><span class="sxs-lookup"><span data-stu-id="76b4b-114">If the account you're currently logged in as has access to the JEA endpoint, you can omit the `-Credential` parameter.</span></span>

<span data-ttu-id="76b4b-115">När PowerShell fråga ändringar `[localhost]: PS>` vet du att du nu interagerar med JEA fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="76b4b-115">When the PowerShell prompt changes to `[localhost]: PS>` you will know that you are now interacting with the remote JEA session.</span></span>
<span data-ttu-id="76b4b-116">Du kan köra `Get-Command` att kontrollera vilka kommandon som är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="76b4b-116">You can run `Get-Command` to check which commands are available.</span></span>
<span data-ttu-id="76b4b-117">Du måste kontakta din administratör om du vill veta om det finns några begränsningar på tillgängliga parametrar eller tillåtna parametervärden.</span><span class="sxs-lookup"><span data-stu-id="76b4b-117">You will need to consult with your administrator to learn if there are any restrictions on the available parameters or allowable parameter values.</span></span>

<span data-ttu-id="76b4b-118">Som en påminnelse drivas JEA sessioner i NoLanguage läge, så att några av de sätt som du vanligtvis använder PowerShell inte kanske tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="76b4b-118">As a reminder, JEA sessions operate in NoLanguage mode, so some of the ways you typically use PowerShell may not be available.</span></span>
<span data-ttu-id="76b4b-119">Du kan inte exempelvis använda variabler för att lagra data eller kontrollera egenskaperna för objekt som returnerades från cmdlets.</span><span class="sxs-lookup"><span data-stu-id="76b4b-119">For instance, you cannot use variables to store data or inspect the properties on objects returned from cmdlets.</span></span>
<span data-ttu-id="76b4b-120">Den nedan exempel visas ett exempel på hur du kan använda PowerShell idag och två sätt att få samma kommando arbetar i NoLanguage läge.</span><span class="sxs-lookup"><span data-stu-id="76b4b-120">The below example shows an example of how you may be using PowerShell today, and two approaches to get the same command working in NoLanguage mode.</span></span>

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="76b4b-121">Överväg att använda för mer komplexa kommando-anrop som gör den här metoden svårt [implicit fjärrkommunikation](#using-jea-with-implicit-remoting) eller [skapa anpassade funktioner](role-capabilities.md#creating-custom-functions) som omsluter funktioner som du önskar.</span><span class="sxs-lookup"><span data-stu-id="76b4b-121">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you desire.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="76b4b-122">JEA med implicit fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="76b4b-122">Using JEA with implicit remoting</span></span>

<span data-ttu-id="76b4b-123">PowerShell stöder ett alternativt fjärrkommunikation modell där du kan importera cmdlet: ar från en fjärrdator på den lokala datorn och interagera med dem som om de vore lokala kommandon.</span><span class="sxs-lookup"><span data-stu-id="76b4b-123">PowerShell supports an alternative remoting model where you can import proxy cmdlets from a remote machine on your local computer and interact with them as if they were local commands.</span></span>
<span data-ttu-id="76b4b-124">Detta kallas för implicit fjärrkommunikation och beskrivs också i [detta *artikel från Hey, Scripting Guy!* blogginlägget](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="76b4b-124">This is called implicit remoting, and is explained well in [this *Hey, Scripting Guy!* blog post](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="76b4b-125">Implicit fjärrkommunikation är särskilt användbar när du arbetar med JEA eftersom du kan arbeta med JEA cmdlets i ett läge för fullständig språk.</span><span class="sxs-lookup"><span data-stu-id="76b4b-125">Implicit remoting is particularly useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span>
<span data-ttu-id="76b4b-126">Det innebär att du kan använda flikavslutande, variabler, ändra objekt och även använda lokala skript för att lättare för att automatisera mot en JEA slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="76b4b-126">This means you can use tab completion, variables, manipulate objects, and even use local scripts to more easily automate against a JEA endpoint.</span></span>
<span data-ttu-id="76b4b-127">När du anropar en proxy-kommandot skickas till slutpunkten JEA på fjärrdatorn data och utförs där.</span><span class="sxs-lookup"><span data-stu-id="76b4b-127">Anytime you invoke a proxy command, the data will be sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="76b4b-128">Implicit fjärrkommunikation fungerar genom att importera cmdlet: ar från en befintlig PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="76b4b-128">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span>
<span data-ttu-id="76b4b-129">Du kan välja att prefixet substantiven för varje proxy-cmdlet med en sträng som du väljer att skilja vilka kommandon som för fjärrsystemet.</span><span class="sxs-lookup"><span data-stu-id="76b4b-129">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing to distinguish which commands are for the remote system.</span></span>
<span data-ttu-id="76b4b-130">En tillfällig skriptmodul som innehåller alla kommandon som proxy skapas och kan användas för hela din lokala PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="76b4b-130">A temporary script module containing all of the proxy commands will be created and can be used for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="76b4b-131">Vissa datorer kan inte importera en hel JEA-session på grund av begränsningar i standard JEA-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="76b4b-131">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span>
> <span data-ttu-id="76b4b-132">För att komma runt detta Importera endast de kommandon som krävs från JEA-session genom att explicit ange namnen på de `-CommandName` parameter.</span><span class="sxs-lookup"><span data-stu-id="76b4b-132">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span>
> <span data-ttu-id="76b4b-133">En framtida uppdatering kan lösa problemet med att importera hela JEA sessioner på en dator.</span><span class="sxs-lookup"><span data-stu-id="76b4b-133">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="76b4b-134">Om det inte går att importera en JEA session på grund av begränsningar i standardparametrarna för JEA kan följa du stegen nedan för att filtrera bort standard kommandon från den importera uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="76b4b-134">If you are unable to import a JEA session due to constraints on the default JEA parameters, you can follow the steps below to filter out the default commands from the imported set.</span></span>
<span data-ttu-id="76b4b-135">Du kommer fortfarande att kunna använda kommandon som `Select-Object` --ska du bara använda den lokala versionen installerad på datorn i stället för det fjärranslutna i JEA-sessionen.</span><span class="sxs-lookup"><span data-stu-id="76b4b-135">You will still be able to use commands like `Select-Object` -- you'll just use the local version installed on your computer instead of the remote one in the JEA session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands 
```

<span data-ttu-id="76b4b-136">Du kan också spara via proxy cmdlets från implicit fjärrkommunikation med [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="76b4b-136">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="76b4b-137">Ta en titt i hjälpen för mer information om implicit fjärrkommunikation [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) och [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="76b4b-137">For more information about implicit remoting, check out the help documentation for [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) and [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programatically"></a><span data-ttu-id="76b4b-138">Med hjälp av JEA genom att programmera</span><span class="sxs-lookup"><span data-stu-id="76b4b-138">Using JEA programatically</span></span>

<span data-ttu-id="76b4b-139">JEA kan också användas i automatiseringssystem och program, till exempel interna supportavdelningen appar och webbplatser.</span><span class="sxs-lookup"><span data-stu-id="76b4b-139">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and web sites.</span></span>
<span data-ttu-id="76b4b-140">Metoden är densamma som för att skapa appar som kommunicerar med obegränsad PowerShell slutpunkter med den begränsning att programmet ska vara medveten om att JEA är att begränsa de kommandon som kan köras i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="76b4b-140">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints, with the caveat that the program should be aware that JEA is limiting the commands that can be run in the remote session.</span></span>

<span data-ttu-id="76b4b-141">Du kan använda för enkla, oneoff uppgifter [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) att köra en uppsättning kommandon med hjälp av JEA.</span><span class="sxs-lookup"><span data-stu-id="76b4b-141">For simple, one-off tasks, you can use [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) to run a set of commands using JEA.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="76b4b-142">Om du vill kontrollera vilka kommandon som är tillgängliga för användning när du ansluter till en session JEA kör `Get-Command` och gå igenom de resultat som ska eftersökas tillåtna parametrar.</span><span class="sxs-lookup"><span data-stu-id="76b4b-142">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="76b4b-143">Om du skapar en C#-app, kan du skapa ett PowerShell-körningsutrymme som ansluter till en JEA-session genom att ange konfigurationsnamnet i en [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) objekt.</span><span class="sxs-lookup"><span data-stu-id="76b4b-143">If you are building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.</span></span>

```csharp

// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/en-us/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
                    creds);                // Credentials
// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="76b4b-144">Med PowerShell Direct JEA</span><span class="sxs-lookup"><span data-stu-id="76b4b-144">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="76b4b-145">Hyper-V i Windows 10 och Windows Server 2016 erbjuder [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), en funktion som gör att Hyper-V-administratörer att hantera virtuella datorer med PowerShell oavsett nätverkskonfiguration eller fjärrhantering inställningarna på den virtuella datorn.</span><span class="sxs-lookup"><span data-stu-id="76b4b-145">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), a feature which allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="76b4b-146">Du kan använda PowerShell direkt med JEA för att ge en Hyper-V begränsad administratörsåtkomst till den virtuella datorn, vilket kan vara användbart om du förlorar nätverksanslutningen till den virtuella datorn och behöver en datacenter-administratör att åtgärda nätverksinställningarna.</span><span class="sxs-lookup"><span data-stu-id="76b4b-146">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM, which can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="76b4b-147">Ingen ytterligare konfiguration krävs för att använda JEA via PowerShell direkt, men operativsystemet som körs på den virtuella datorn måste vara Windows 10 eller Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="76b4b-147">No additional configuration is required to use JEA over PowerShell Direct, however the operating system running inside the virtual machine must be Windows 10 or Windows Server 2016.</span></span>
<span data-ttu-id="76b4b-148">Hyper-V-administratör kan ansluta till JEA slutpunkten med hjälp av den `-VMName` eller `-VMId` för PSRemoting-cmdlets:</span><span class="sxs-lookup"><span data-stu-id="76b4b-148">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="76b4b-149">Det rekommenderas starkt att du skapar en dedikerad lokal användare med ingen behörighet att hantera system för Hyper-V-administratörer använder.</span><span class="sxs-lookup"><span data-stu-id="76b4b-149">It is strongly recommended that you create a dedicated local user with no other rights to manage the system for your Hyper-V administrators to use.</span></span>
<span data-ttu-id="76b4b-150">Kom ihåg att även en icke-privilegierade användare kan fortfarande logga in på en Windows-dator som standard med obegränsad PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76b4b-150">Remember that even an unprivileged user can still log into a Windows machine by default, including using unconstrained PowerShell.</span></span>
<span data-ttu-id="76b4b-151">Som gör att de kan bläddra (del av) filsystemet och lär dig mer om OS-miljön.</span><span class="sxs-lookup"><span data-stu-id="76b4b-151">That will allow them to browse (some of) the file system and learn more about your OS environment.</span></span>
<span data-ttu-id="76b4b-152">Om du vill låsa en Hyper-V-administratör att endast få åtkomst till en virtuell dator med hjälp av PowerShell direkt med JEA behöver du neka lokal inloggningsrättigheter till Hyper-V-administratörens JEA konto.</span><span class="sxs-lookup"><span data-stu-id="76b4b-152">To lock down a Hyper-V administrator to only access a VM using PowerShell Direct with JEA, you will need to deny local logon rights to the Hyper-V admin's JEA account.</span></span>

