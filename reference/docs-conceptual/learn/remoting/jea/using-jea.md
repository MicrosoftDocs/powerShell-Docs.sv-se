---
ms.date: 07/10/2019
keywords: Jea, PowerShell, säkerhet
title: Använda JEA
ms.openlocfilehash: 1c424eb4a476dd0db3cc69c0e6f14c89a3c523ba
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500523"
---
# <a name="using-jea"></a><span data-ttu-id="2cf99-103">Använda JEA</span><span class="sxs-lookup"><span data-stu-id="2cf99-103">Using JEA</span></span>

<span data-ttu-id="2cf99-104">I den här artikeln beskrivs de olika sätt som du kan ansluta till och använda en JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="2cf99-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="2cf99-105">Använda JEA interaktivt</span><span class="sxs-lookup"><span data-stu-id="2cf99-105">Using JEA interactively</span></span>

<span data-ttu-id="2cf99-106">Om du testar din JEA-konfiguration eller har enkla uppgifter för användare kan du använda JEA på samma sätt som du skulle göra med en vanlig PowerShell-fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="2cf99-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="2cf99-107">För komplexa fjärr kommunikations uppgifter rekommenderar vi att du använder [implicit fjärr kommunikation](#using-jea-with-implicit-remoting).</span><span class="sxs-lookup"><span data-stu-id="2cf99-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="2cf99-108">Implicit fjärr kommunikation gör att användare kan arbeta med data objekt lokalt.</span><span class="sxs-lookup"><span data-stu-id="2cf99-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="2cf99-109">Om du vill använda JEA interaktivt måste du:</span><span class="sxs-lookup"><span data-stu-id="2cf99-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="2cf99-110">Namnet på datorn som du ansluter till (kan vara den lokala datorn)</span><span class="sxs-lookup"><span data-stu-id="2cf99-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="2cf99-111">Namnet på den JEA-slutpunkt som är registrerad på datorn</span><span class="sxs-lookup"><span data-stu-id="2cf99-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="2cf99-112">Autentiseringsuppgifter som har åtkomst till JEA-slutpunkten på den här datorn</span><span class="sxs-lookup"><span data-stu-id="2cf99-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="2cf99-113">Med den informationen kan du starta en JEA-session med cmdletarna [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) eller [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .</span><span class="sxs-lookup"><span data-stu-id="2cf99-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="2cf99-114">Om det aktuella användar kontot har åtkomst till JEA-slutpunkten kan du utelämna parametern för **autentiseringsuppgifter** .</span><span class="sxs-lookup"><span data-stu-id="2cf99-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="2cf99-115">När PowerShell-prompten ändras till `[localhost]: PS>` du veta att du nu interagerar med den fjärranslutna JEA-sessionen.</span><span class="sxs-lookup"><span data-stu-id="2cf99-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="2cf99-116">Du kan köra `Get-Command` för att kontrol lera vilka kommandon som är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="2cf99-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="2cf99-117">Kontakta administratören om du vill veta om det finns några begränsningar för de tillgängliga parametrarna eller tillåtna parameter värden.</span><span class="sxs-lookup"><span data-stu-id="2cf99-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="2cf99-118">Kom ihåg att JEA-sessioner körs i nolanguage-läge.</span><span class="sxs-lookup"><span data-stu-id="2cf99-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="2cf99-119">Några av de sätt som du vanligt vis använder PowerShell är kanske inte tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="2cf99-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="2cf99-120">Du kan till exempel inte använda variabler för att lagra data eller granska egenskaperna för objekt som returneras från-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="2cf99-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="2cf99-121">I följande exempel visas två metoder för att få samma kommandon att fungera i läget nolanguage.</span><span class="sxs-lookup"><span data-stu-id="2cf99-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

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

<span data-ttu-id="2cf99-122">För mer komplexa kommando anrop som gör den här metoden svår, kan du överväga att använda [implicit fjärr kommunikation](#using-jea-with-implicit-remoting) eller [skapa anpassade funktioner](role-capabilities.md#creating-custom-functions) som omsluter de funktioner du behöver.</span><span class="sxs-lookup"><span data-stu-id="2cf99-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="2cf99-123">Använda JEA med implicit fjärr kommunikation</span><span class="sxs-lookup"><span data-stu-id="2cf99-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="2cf99-124">PowerShell har en implicit fjärr kommunikations modell som låter dig importera proxy-cmdletar från en fjärrdator och interagera med dem som om de var lokala kommandon.</span><span class="sxs-lookup"><span data-stu-id="2cf99-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="2cf99-125">Implicit fjärr kommunikation förklaras i den här **Hey, Scripting Guy!**</span><span class="sxs-lookup"><span data-stu-id="2cf99-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="2cf99-126">[blogg inlägg](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="2cf99-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="2cf99-127">Implicit fjärr kommunikation är användbart när du arbetar med JEA eftersom det gör att du kan arbeta med JEA-cmdlets i ett fullständigt språk läge.</span><span class="sxs-lookup"><span data-stu-id="2cf99-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="2cf99-128">Du kan använda ifyllning, variabler, manipulera objekt och till och med använda lokala skript för att automatisera uppgifter mot en JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="2cf99-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="2cf99-129">När du anropar ett proxy-kommando skickas data till JEA-slutpunkten på fjärrdatorn och körs där.</span><span class="sxs-lookup"><span data-stu-id="2cf99-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="2cf99-130">Implicit fjärr kommunikation fungerar genom att importera cmdletar från en befintlig PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="2cf99-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="2cf99-131">Du kan välja att ange prefix för varje proxy-cmdlet med en valfri sträng som du väljer.</span><span class="sxs-lookup"><span data-stu-id="2cf99-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="2cf99-132">Med prefixet kan du skilja på kommandona för fjärrsystemet.</span><span class="sxs-lookup"><span data-stu-id="2cf99-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="2cf99-133">En tillfällig skript-modul som innehåller alla proxy-kommandon skapas och importeras under den lokala PowerShell-sessionens varaktighet.</span><span class="sxs-lookup"><span data-stu-id="2cf99-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="2cf99-134">Vissa system kanske inte kan importera en hel JEA-session på grund av begränsningar i standard-cmdletarna för JEA.</span><span class="sxs-lookup"><span data-stu-id="2cf99-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="2cf99-135">Du kan komma runt detta genom att bara importera de kommandon du behöver från JEA-sessionen genom att uttryckligen ange namnen på `-CommandName`-parametern.</span><span class="sxs-lookup"><span data-stu-id="2cf99-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="2cf99-136">En framtida uppdatering löser problemet med att importera hela JEA-sessioner på berörda system.</span><span class="sxs-lookup"><span data-stu-id="2cf99-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="2cf99-137">Om du inte kan importera en JEA-session på grund av JEA-begränsningar på standard parametrarna följer du stegen nedan för att filtrera bort standard kommandona från den importerade uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="2cf99-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="2cf99-138">Du kan fortsätta använda kommandon som `Select-Object`, men du kommer bara att använda den lokala versionen som är installerad på datorn i stället för den som importer ATS från JEA-sessionen.</span><span class="sxs-lookup"><span data-stu-id="2cf99-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

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

<span data-ttu-id="2cf99-139">Du kan också spara proxy-cmdletar från implicit fjärr kommunikation med hjälp av [export-PSSession](/powershell/module/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="2cf99-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/module/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="2cf99-140">Mer information om implicit fjärr kommunikation finns i dokumentationen för [import-PSSession](/powershell/module/microsoft.powershell.utility/import-pssession) och [import-module](/powershell/module/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="2cf99-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/module/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/module/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="2cf99-141">Använda JEA program mässigt</span><span class="sxs-lookup"><span data-stu-id="2cf99-141">Using JEA programmatically</span></span>

<span data-ttu-id="2cf99-142">JEA kan också användas i Automation-system och i användar program, t. ex. interna Helpdesk-appar och webbplatser.</span><span class="sxs-lookup"><span data-stu-id="2cf99-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="2cf99-143">Metoden är densamma som för att skapa appar som kommunicerar med obegränsade PowerShell-slutpunkter.</span><span class="sxs-lookup"><span data-stu-id="2cf99-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="2cf99-144">Se till att programmet är utformat för att fungera med begränsning från JEA.</span><span class="sxs-lookup"><span data-stu-id="2cf99-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="2cf99-145">För enkla, enkelriktade uppgifter kan du använda [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) för att köra kommandon i en Jea-session.</span><span class="sxs-lookup"><span data-stu-id="2cf99-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="2cf99-146">Du kan kontrol lera vilka kommandon som är tillgängliga för användning när du ansluter till en JEA-session genom att köra `Get-Command` och iterera genom resultaten för att kontrol lera de tillåtna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="2cf99-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="2cf99-147">Om du skapar en C# app kan du skapa en PowerShell-körnings utrymme som ansluter till en Jea-session genom att ange konfigurations namnet i ett [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) -objekt.</span><span class="sxs-lookup"><span data-stu-id="2cf99-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

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
    string.Format(CultureInfo.InvariantCulture, "https://schemas.microsoft.com/powershell/{0}", configName),
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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="2cf99-148">Använda JEA med PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="2cf99-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="2cf99-149">Hyper-V i Windows 10 och Windows Server 2016 erbjuder [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), en funktion som gör att Hyper-v-administratörer kan hantera virtuella datorer med PowerShell oavsett nätverks konfigurationen eller inställningar för fjärrhantering på den virtuella datorn.</span><span class="sxs-lookup"><span data-stu-id="2cf99-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="2cf99-150">Du kan använda PowerShell Direct med JEA för att ge en Hyper-V-administratör begränsad åtkomst till den virtuella datorn.</span><span class="sxs-lookup"><span data-stu-id="2cf99-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="2cf99-151">Detta kan vara användbart om du tappar bort nätverks anslutningen till den virtuella datorn och behöver en data Center administratör för att åtgärda nätverks inställningarna.</span><span class="sxs-lookup"><span data-stu-id="2cf99-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="2cf99-152">Ingen ytterligare konfiguration krävs för att använda JEA via PowerShell Direct.</span><span class="sxs-lookup"><span data-stu-id="2cf99-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="2cf99-153">Men gäst operativ systemet som körs i den virtuella datorn måste vara Windows 10, Windows Server 2016 eller senare.</span><span class="sxs-lookup"><span data-stu-id="2cf99-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="2cf99-154">Hyper-V-administratören kan ansluta till JEA-slutpunkten med hjälp av `-VMName`-eller `-VMId`-parametrarna på PSRemoting-cmdlet: ar:</span><span class="sxs-lookup"><span data-stu-id="2cf99-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="2cf99-155">Vi rekommenderar att du skapar ett dedikerat användar konto med den minsta behörighet som krävs för att hantera systemet för användning av en Hyper-V-administratör.</span><span class="sxs-lookup"><span data-stu-id="2cf99-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="2cf99-156">Kom ihåg att även om en obehörig användare kan logga in på en Windows-dator som standard, inklusive att använda obegränsade PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2cf99-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="2cf99-157">Detta gör att de kan bläddra i fil systemet och lära sig mer om din operativ system miljö.</span><span class="sxs-lookup"><span data-stu-id="2cf99-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="2cf99-158">Om du vill låsa en Hyper-V-administratör och begränsa dem till endast åtkomst till en virtuell dator med hjälp av PowerShell Direct med JEA, måste du neka lokala inloggnings rättigheter till Hyper-V-administratörens JEA-konto.</span><span class="sxs-lookup"><span data-stu-id="2cf99-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
