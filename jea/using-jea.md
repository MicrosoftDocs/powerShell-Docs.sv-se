---
ms.date: 07/10/2019
keywords: jea, powershell, säkerhet
title: Använda JEA
ms.openlocfilehash: 8f3cc9186c61a2ae5b64eb3dc4f72ca83f1a58c5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734219"
---
# <a name="using-jea"></a><span data-ttu-id="052c7-103">Använda JEA</span><span class="sxs-lookup"><span data-stu-id="052c7-103">Using JEA</span></span>

<span data-ttu-id="052c7-104">Den här artikeln beskrivs de olika sätt du kan ansluta till och använda en JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="052c7-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="052c7-105">Använda JEA interaktivt</span><span class="sxs-lookup"><span data-stu-id="052c7-105">Using JEA interactively</span></span>

<span data-ttu-id="052c7-106">Om du testar din JEA-konfiguration eller har enkla uppgifter för användare, kan du använda JEA på samma sätt som en vanlig PowerShell-session för fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="052c7-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="052c7-107">För komplexa fjärrkommunikation aktiviteter, rekommenderar vi för att använda [implicit fjärrkommunikation](#using-jea-with-implicit-remoting).</span><span class="sxs-lookup"><span data-stu-id="052c7-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="052c7-108">Implicit fjärrkommunikation tillåter användare att arbeta med dataobjekt lokalt.</span><span class="sxs-lookup"><span data-stu-id="052c7-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="052c7-109">Om du vill använda JEA interaktivt, behöver du:</span><span class="sxs-lookup"><span data-stu-id="052c7-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="052c7-110">Namnet på den dator som du ansluter till (kan vara den lokala datorn)</span><span class="sxs-lookup"><span data-stu-id="052c7-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="052c7-111">Namnet på JEA-slutpunkt som registrerats på datorn</span><span class="sxs-lookup"><span data-stu-id="052c7-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="052c7-112">Autentiseringsuppgifter som har åtkomst till JEA-slutpunkt på datorn</span><span class="sxs-lookup"><span data-stu-id="052c7-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="052c7-113">Med den här informationen kan du starta en JEA-session med den [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) eller [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdletar.</span><span class="sxs-lookup"><span data-stu-id="052c7-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="052c7-114">Om det aktuella användarkontot har åtkomst till JEA-slutpunkt, kan du utesluta den **Credential** parametern.</span><span class="sxs-lookup"><span data-stu-id="052c7-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="052c7-115">När PowerShell frågar ändringar `[localhost]: PS>` du vet att du nu interagerar med JEA fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="052c7-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="052c7-116">Du kan köra `Get-Command` att kontrollera vilka kommandon är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="052c7-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="052c7-117">Kontakta administratören om du vill lära dig om det finns några begränsningar på tillgängliga parametrar eller tillåtna parametervärden.</span><span class="sxs-lookup"><span data-stu-id="052c7-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="052c7-118">Kom ihåg att JEA-sessioner som arbetar i NoLanguage läge.</span><span class="sxs-lookup"><span data-stu-id="052c7-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="052c7-119">Exempel på hur du använder vanligtvis PowerShell kanske inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="052c7-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="052c7-120">Du kan inte exempelvis använda variabler för att lagra data eller kontrollera egenskaperna för objekt som returneras från cmdlet: ar.</span><span class="sxs-lookup"><span data-stu-id="052c7-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="052c7-121">I följande exempel visas två metoder för att få samma kommandon för att arbeta i NoLanguage läge.</span><span class="sxs-lookup"><span data-stu-id="052c7-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="052c7-122">Överväg att använda för mer komplexa kommando-anrop som gör den här metoden svårt [implicit fjärrkommunikation](#using-jea-with-implicit-remoting) eller [skapa anpassade funktioner](role-capabilities.md#creating-custom-functions) som omsluter vilka funktioner du behöver.</span><span class="sxs-lookup"><span data-stu-id="052c7-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="052c7-123">Använda JEA med implicit fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="052c7-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="052c7-124">PowerShell har en modell för implicit fjärrkommunikation som kan du importera proxy-cmdlet: ar från en fjärrdator och interagera med dem som om de vore lokala kommandon.</span><span class="sxs-lookup"><span data-stu-id="052c7-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="052c7-125">Implicit fjärrkommunikation förklaras i det här **Hey, Scripting Guy!**</span><span class="sxs-lookup"><span data-stu-id="052c7-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="052c7-126">[blogginlägget](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="052c7-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="052c7-127">Implicit fjärrkommunikation är användbart när du arbetar med JEA eftersom den tillåter dig att arbeta med JEA-cmdletar i ett språkläge med fullständig.</span><span class="sxs-lookup"><span data-stu-id="052c7-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="052c7-128">Du kan använda tabbifyllning, variabler, manipulera objekt och även använda lokala skript för att automatisera åtgärder mot en JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="052c7-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="052c7-129">Varje gång du anropar en proxy-kommandot data skickas till JEA-slutpunkt på fjärrdatorn och det körs.</span><span class="sxs-lookup"><span data-stu-id="052c7-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="052c7-130">Implicit fjärrkommunikation fungerar genom att importera cmdlet: ar från en befintlig PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="052c7-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="052c7-131">Du kan välja att prefixet substantiven för varje proxy-cmdlet med en sträng med valfritt.</span><span class="sxs-lookup"><span data-stu-id="052c7-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="052c7-132">Prefixet kan du skilja kommandon som är för fjärrsystemet.</span><span class="sxs-lookup"><span data-stu-id="052c7-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="052c7-133">En tillfällig skriptmodul som innehåller alla proxy kommandon skapas och importeras för varaktigheten för din lokala PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="052c7-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="052c7-134">Vissa system kanske inte att importera en hel JEA-session på grund av begränsningar i standard JEA-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="052c7-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="052c7-135">För att undvika detta, bara importera de kommandon som du behöver från JEA-sessionen genom att uttryckligen ange namnen till de `-CommandName` parametern.</span><span class="sxs-lookup"><span data-stu-id="052c7-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="052c7-136">En kommande uppdatering kan lösa problemet med att importera hela JEA-sessioner på en dator.</span><span class="sxs-lookup"><span data-stu-id="052c7-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="052c7-137">Om det inte går att importera en JEA-session på grund av begränsningar av JEA i standardparametrarna, följer du stegen nedan för att filtrera bort standardkommandona från importerade uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="052c7-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="052c7-138">Du kan fortsätta använda kommandon som `Select-Object`, men ska du bara använda den lokala versionen som installerats på datorn i stället för den som importerats från JEA fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="052c7-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

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

<span data-ttu-id="052c7-139">Du kan också spara via proxy-cmdletar från implicit fjärrkommunikation med [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="052c7-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="052c7-140">Mer information om implicit fjärrkommunikation finns i dokumentationen för [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) och [Import-Module](/powershell/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="052c7-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="052c7-141">Använda JEA programmässigt</span><span class="sxs-lookup"><span data-stu-id="052c7-141">Using JEA programmatically</span></span>

<span data-ttu-id="052c7-142">JEA kan också användas i automatiseringssystem och användarprogram, till exempel interna supportavdelningen appar och webbplatser.</span><span class="sxs-lookup"><span data-stu-id="052c7-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="052c7-143">Metoden är samma som för att bygga appar som kommunicerar med obegränsad PowerShell-slutpunkter.</span><span class="sxs-lookup"><span data-stu-id="052c7-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="052c7-144">Se till att programmet har utformats för att arbeta med begränsningar som införts av JEA.</span><span class="sxs-lookup"><span data-stu-id="052c7-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="052c7-145">Du kan använda enkla, oneoff aktivitetsinformation, [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) att köra kommandon i en JEA-session.</span><span class="sxs-lookup"><span data-stu-id="052c7-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="052c7-146">Du kan kontrollera vilka kommandon är tillgängliga för användning när du ansluter till en JEA-session genom att köra `Get-Command` och gå igenom de resultat att söka efter de tillåtna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="052c7-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="052c7-147">Om du bygger en C# app, kan du skapa ett PowerShell-körningsutrymme som ansluter till en JEA-session genom att ange konfigurationsnamnet i en [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) objekt.</span><span class="sxs-lookup"><span data-stu-id="052c7-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),
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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="052c7-148">Använda JEA med PowerShell direkt</span><span class="sxs-lookup"><span data-stu-id="052c7-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="052c7-149">Hyper-V i Windows 10 och Windows Server 2016 erbjuder [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), en funktion som gör att Hyper-V-administratörer att hantera virtuella datorer med PowerShell oavsett nätverkskonfiguration eller fjärrhantering inställningarna på den virtuella datorn.</span><span class="sxs-lookup"><span data-stu-id="052c7-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="052c7-150">Du kan använda PowerShell Direct med JEA för att ge en Hyper-V begränsad administratörsåtkomst till den virtuella datorn.</span><span class="sxs-lookup"><span data-stu-id="052c7-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="052c7-151">Detta kan vara användbart om du förlorar nätverksanslutningen till den virtuella datorn och behöver en datacenter-administratör att åtgärda nätverksinställningarna.</span><span class="sxs-lookup"><span data-stu-id="052c7-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="052c7-152">Ingen ytterligare konfiguration krävs för att använda JEA via PowerShell Direct.</span><span class="sxs-lookup"><span data-stu-id="052c7-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="052c7-153">Gästoperativsystemet som körs på den virtuella datorn måste dock vara Windows 10, Windows Server 2016 eller senare.</span><span class="sxs-lookup"><span data-stu-id="052c7-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="052c7-154">Hyper-V-administratören kan ansluta till JEA-slutpunkt med hjälp av den `-VMName` eller `-VMId` parametrar om PSRemoting-cmdletar:</span><span class="sxs-lookup"><span data-stu-id="052c7-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="052c7-155">Du bör du skapa ett dedikerat användarkonto med lägsta behörighet som krävs för att hantera system för användning av en Hyper-V-administratör.</span><span class="sxs-lookup"><span data-stu-id="052c7-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="052c7-156">Kom ihåg att även en icke-privilegierade användare kan logga in på en Windows-dator som standard, inklusive med obegränsad PowerShell.</span><span class="sxs-lookup"><span data-stu-id="052c7-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="052c7-157">Som gör att de kan bläddra i filsystemet och lär dig mer om din OS-miljö.</span><span class="sxs-lookup"><span data-stu-id="052c7-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="052c7-158">För att låsa en Hyper-V-administratör och begränsa dem för att bara åtkomst till en virtuell dator med PowerShell Direct med JEA, måste du neka lokal inloggningsrättigheter till Hyper-V-administratörens JEA-konto.</span><span class="sxs-lookup"><span data-stu-id="052c7-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
