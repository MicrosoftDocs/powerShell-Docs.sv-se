---
description: Beskriver hur du kör och skriver skript i PowerShell.
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scripts
ms.openlocfilehash: 2fc81d1d43b8cdddaacb917deaa5d58536a541cb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710549"
---
# <a name="about-scripts"></a><span data-ttu-id="f224b-103">Om skript</span><span class="sxs-lookup"><span data-stu-id="f224b-103">About Scripts</span></span>

## <a name="short-description"></a><span data-ttu-id="f224b-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="f224b-104">Short description</span></span>
<span data-ttu-id="f224b-105">Beskriver hur du kör och skriver skript i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f224b-105">Describes how to run and write scripts in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="f224b-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="f224b-106">Long description</span></span>

<span data-ttu-id="f224b-107">Ett skript är en oformaterad textfil som innehåller ett eller flera PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="f224b-107">A script is a plain text file that contains one or more PowerShell commands.</span></span>
<span data-ttu-id="f224b-108">PowerShell-skript har ett `.ps1` fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="f224b-108">PowerShell scripts have a `.ps1` file extension.</span></span>

<span data-ttu-id="f224b-109">Att köra ett skript är ett mycket som att köra en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f224b-109">Running a script is a lot like running a cmdlet.</span></span> <span data-ttu-id="f224b-110">Du anger sökvägen och fil namnet för skriptet och använder parametrar för att skicka data och ange alternativ.</span><span class="sxs-lookup"><span data-stu-id="f224b-110">You type the path and file name of the script and use parameters to submit data and set options.</span></span> <span data-ttu-id="f224b-111">Du kan köra skript på datorn eller i en fjärran sluten session på en annan dator.</span><span class="sxs-lookup"><span data-stu-id="f224b-111">You can run scripts on your computer or in a remote session on a different computer.</span></span>

<span data-ttu-id="f224b-112">Att skriva ett skript sparar ett kommando för senare användning och gör det enkelt att dela med andra.</span><span class="sxs-lookup"><span data-stu-id="f224b-112">Writing a script saves a command for later use and makes it easy to share with others.</span></span> <span data-ttu-id="f224b-113">Viktigast är att du kan köra kommandona genom att skriva skript Sök vägen och fil namnet.</span><span class="sxs-lookup"><span data-stu-id="f224b-113">Most importantly, it lets you run the commands simply by typing the script path and the filename.</span></span> <span data-ttu-id="f224b-114">Skript kan vara lika enkla som ett enda kommando i en fil eller som ett komplext program.</span><span class="sxs-lookup"><span data-stu-id="f224b-114">Scripts can be as simple as a single command in a file or as extensive as a complex program.</span></span>

<span data-ttu-id="f224b-115">Skript har ytterligare funktioner, till exempel `#Requires` särskilda kommentarer, användning av parametrar, stöd för data avsnitt och digital signering för säkerhet.</span><span class="sxs-lookup"><span data-stu-id="f224b-115">Scripts have additional features, such as the `#Requires` special comment, the use of parameters, support for data sections, and digital signing for security.</span></span>
<span data-ttu-id="f224b-116">Du kan också skriva Hjälp avsnitt för skript och för alla funktioner i skriptet.</span><span class="sxs-lookup"><span data-stu-id="f224b-116">You can also write Help topics for scripts and for any functions in the script.</span></span>

## <a name="how-to-run-a-script"></a><span data-ttu-id="f224b-117">Så här kör du ett skript</span><span class="sxs-lookup"><span data-stu-id="f224b-117">How to run a script</span></span>

<span data-ttu-id="f224b-118">Innan du kan köra ett skript i Windows måste du ändra standard körnings principen för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f224b-118">Before you can run a script on Windows, you need to change the default PowerShell execution policy.</span></span> <span data-ttu-id="f224b-119">Körnings principen gäller inte för PowerShell som körs på andra plattformar än Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="f224b-119">Execution policy does not apply to PowerShell running on non-Windows platforms.</span></span>

<span data-ttu-id="f224b-120">Standard körnings principen, `Restricted` , förhindrar att alla skript körs, inklusive skript som du skriver på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f224b-120">The default execution policy, `Restricted`, prevents all scripts from running, including scripts that you write on the local computer.</span></span> <span data-ttu-id="f224b-121">Mer information finns i [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="f224b-121">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="f224b-122">Körnings principen sparas i registret, så du behöver bara ändra den en gång på varje dator.</span><span class="sxs-lookup"><span data-stu-id="f224b-122">The execution policy is saved in the registry, so you need to change it only once on each computer.</span></span>

<span data-ttu-id="f224b-123">Använd följande procedur om du vill ändra körnings principen.</span><span class="sxs-lookup"><span data-stu-id="f224b-123">To change the execution policy, use the following procedure.</span></span>

<span data-ttu-id="f224b-124">Skriv följande i kommandotolken:</span><span class="sxs-lookup"><span data-stu-id="f224b-124">At the command prompt, type:</span></span>

```powershell
Set-ExecutionPolicy AllSigned
```

<span data-ttu-id="f224b-125">eller</span><span class="sxs-lookup"><span data-stu-id="f224b-125">or</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<span data-ttu-id="f224b-126">Ändringen träder i kraft omedelbart.</span><span class="sxs-lookup"><span data-stu-id="f224b-126">The change is effective immediately.</span></span>

<span data-ttu-id="f224b-127">Om du vill köra ett skript anger du det fullständiga namnet och den fullständiga sökvägen till skript filen.</span><span class="sxs-lookup"><span data-stu-id="f224b-127">To run a script, type the full name and the full path to the script file.</span></span>

<span data-ttu-id="f224b-128">Om du till exempel vill köra Get-ServiceLog.ps1-skriptet i C:\Scripts-katalogen skriver du:</span><span class="sxs-lookup"><span data-stu-id="f224b-128">For example, to run the Get-ServiceLog.ps1 script in the C:\Scripts directory, type:</span></span>

```powershell
C:\Scripts\Get-ServiceLog.ps1
```

<span data-ttu-id="f224b-129">Om du vill köra ett skript i den aktuella katalogen anger du sökvägen till den aktuella katalogen eller använder en punkt för att representera den aktuella katalogen, följt av en sökväg för omvänt snedstreck ( `.\` ).</span><span class="sxs-lookup"><span data-stu-id="f224b-129">To run a script in the current directory, type the path to the current directory, or use a dot to represent the current directory, followed by a path backslash (`.\`).</span></span>

<span data-ttu-id="f224b-130">Om du till exempel vill köra ServicesLog.ps1-skriptet i den lokala katalogen skriver du:</span><span class="sxs-lookup"><span data-stu-id="f224b-130">For example, to run the ServicesLog.ps1 script in the local directory, type:</span></span>

```powershell
.\Get-ServiceLog.ps1
```

<span data-ttu-id="f224b-131">Om skriptet har parametrar anger du parametrarna och parameter värdena efter skript fil namnet.</span><span class="sxs-lookup"><span data-stu-id="f224b-131">If the script has parameters, type the parameters and parameter values after the script filename.</span></span>

<span data-ttu-id="f224b-132">Följande kommando använder till exempel parametern ServiceName i Get-ServiceLog-skriptet för att begära en logg över WinRM-tjänsteaktiviteten.</span><span class="sxs-lookup"><span data-stu-id="f224b-132">For example, the following command uses the ServiceName parameter of the Get-ServiceLog script to request a log of WinRM service activity.</span></span>

```powershell
.\Get-ServiceLog.ps1 -ServiceName WinRM
```

<span data-ttu-id="f224b-133">Som en säkerhetsfunktion kör PowerShell inte skript när du dubbelklickar på skript ikonen i Utforskaren eller när du skriver skript namnet utan en fullständig sökväg, även om skriptet finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="f224b-133">As a security feature, PowerShell does not run scripts when you double-click the script icon in File Explorer or when you type the script name without a full path, even when the script is in the current directory.</span></span> <span data-ttu-id="f224b-134">Mer information om att köra kommandon och skript i PowerShell finns [about_Command_Precedence](about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="f224b-134">For more information about running commands and scripts in PowerShell, see [about_Command_Precedence](about_Command_Precedence.md).</span></span>

### <a name="run-with-powershell"></a><span data-ttu-id="f224b-135">Kör med PowerShell</span><span class="sxs-lookup"><span data-stu-id="f224b-135">Run with PowerShell</span></span>

<span data-ttu-id="f224b-136">Från och med PowerShell 3,0 kan du köra skript från Utforskaren.</span><span class="sxs-lookup"><span data-stu-id="f224b-136">Beginning in PowerShell 3.0, you can run scripts from File Explorer.</span></span>

<span data-ttu-id="f224b-137">Använda funktionen "kör med PowerShell":</span><span class="sxs-lookup"><span data-stu-id="f224b-137">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="f224b-138">Kör Utforskaren, högerklicka på skript filen och välj sedan kör med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f224b-138">Run File Explorer, right-click the script filename and then select "Run with PowerShell".</span></span>

<span data-ttu-id="f224b-139">Funktionen "kör med PowerShell" är utformad för att köra skript som inte har nödvändiga parametrar och som inte returnerar utdata till kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="f224b-139">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="f224b-140">Mer information finns i [about_Run_With_PowerShell](about_Run_With_PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="f224b-140">For more information, see [about_Run_With_PowerShell](about_Run_With_PowerShell.md).</span></span>

### <a name="running-scripts-on-other-computers"></a><span data-ttu-id="f224b-141">Köra skript på andra datorer</span><span class="sxs-lookup"><span data-stu-id="f224b-141">Running scripts on other computers</span></span>

<span data-ttu-id="f224b-142">Om du vill köra ett skript på en eller flera fjärrdatorer använder du parametern **sökväg** för `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f224b-142">To run a script on one or more remote computers, use the **FilePath** parameter of the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="f224b-143">Ange sökvägen och fil namnet för skriptet som värdet för parametern **sökväg** .</span><span class="sxs-lookup"><span data-stu-id="f224b-143">Enter the path and filename of the script as the value of the **FilePath** parameter.</span></span> <span data-ttu-id="f224b-144">Skriptet måste finnas på den lokala datorn eller i en katalog som den lokala datorn kan komma åt.</span><span class="sxs-lookup"><span data-stu-id="f224b-144">The script must reside on the local computer or in a directory that the local computer can access.</span></span>

<span data-ttu-id="f224b-145">Följande kommando kör `Get-ServiceLog.ps1` skriptet på fjärrdatorerna med namnet Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="f224b-145">The following command runs the `Get-ServiceLog.ps1` script on the remote computers named Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01,Server02 -FilePath `
  C:\Scripts\Get-ServiceLog.ps1
```

## <a name="get-help-for-scripts"></a><span data-ttu-id="f224b-146">Få hjälp med skript</span><span class="sxs-lookup"><span data-stu-id="f224b-146">Get help for scripts</span></span>

<span data-ttu-id="f224b-147">Get-Help-cmdlet: en hämtar hjälp avsnitten för skript samt för cmdlets och andra typer av kommandon.</span><span class="sxs-lookup"><span data-stu-id="f224b-147">The Get-Help cmdlet gets the help topics for scripts as well as for cmdlets and other types of commands.</span></span> <span data-ttu-id="f224b-148">Om du vill hämta hjälp avsnittet för ett skript skriver du `Get-Help` följt av Skriptets sökväg och namn.</span><span class="sxs-lookup"><span data-stu-id="f224b-148">To get the help topic for a script, type `Get-Help` followed by the path and filename of the script.</span></span> <span data-ttu-id="f224b-149">Om skript Sök vägen är i din `Path` miljö variabel kan du utelämna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="f224b-149">If the script path is in your `Path` environment variable, you can omit the path.</span></span>

<span data-ttu-id="f224b-150">Om du till exempel vill få hjälp med ServicesLog.ps1 skriptet skriver du:</span><span class="sxs-lookup"><span data-stu-id="f224b-150">For example, to get help for the ServicesLog.ps1 script, type:</span></span>

```powershell
get-help C:\admin\scripts\ServicesLog.ps1
```

## <a name="how-to-write-a-script"></a><span data-ttu-id="f224b-151">Så här skriver du ett skript</span><span class="sxs-lookup"><span data-stu-id="f224b-151">How to write a script</span></span>

<span data-ttu-id="f224b-152">Ett skript kan innehålla alla giltiga PowerShell-kommandon, inklusive enskilda kommandon, kommandon som använder pipeline-, Function-och kontroll strukturer som if-satser och for-slingor.</span><span class="sxs-lookup"><span data-stu-id="f224b-152">A script can contain any valid PowerShell commands, including single commands, commands that use the pipeline, functions, and control structures such as If statements and For loops.</span></span>

<span data-ttu-id="f224b-153">Om du vill skriva ett skript öppnar du en ny fil i en text redigerare, skriver kommandon och sparar dem i en fil med ett giltigt fil namn med `.ps1` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="f224b-153">To write a script, open a new file in a text editor, type the commands, and save them in a file with a valid filename with the `.ps1` file extension.</span></span>

<span data-ttu-id="f224b-154">Följande exempel är ett enkelt skript som hämtar de tjänster som körs på det aktuella systemet och sparar dem i en loggfil.</span><span class="sxs-lookup"><span data-stu-id="f224b-154">The following example is a simple script that gets the services that are running on the current system and saves them to a log file.</span></span> <span data-ttu-id="f224b-155">Logg fil namnet skapas från det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="f224b-155">The log filename is created from the current date.</span></span>

```powershell
$date = (get-date).dayofyear
get-service | out-file "$date.log"
```

<span data-ttu-id="f224b-156">Om du vill skapa skriptet öppnar du en text redigerare eller en skript redigerare, skriver dessa kommandon och sparar dem i en fil med namnet `ServiceLog.ps1` .</span><span class="sxs-lookup"><span data-stu-id="f224b-156">To create this script, open a text editor or a script editor, type these commands, and then save them in a file named `ServiceLog.ps1`.</span></span>

### <a name="parameters-in-scripts"></a><span data-ttu-id="f224b-157">Parametrar i skript</span><span class="sxs-lookup"><span data-stu-id="f224b-157">Parameters in scripts</span></span>

<span data-ttu-id="f224b-158">Använd en param-instruktion för att definiera parametrar i ett skript.</span><span class="sxs-lookup"><span data-stu-id="f224b-158">To define parameters in a script, use a Param statement.</span></span> <span data-ttu-id="f224b-159">`Param`Instruktionen måste vara den första instruktionen i ett skript, förutom kommentarer och eventuella `#Require` instruktioner.</span><span class="sxs-lookup"><span data-stu-id="f224b-159">The `Param` statement must be the first statement in a script, except for comments and any `#Require` statements.</span></span>

<span data-ttu-id="f224b-160">Skript parametrar fungerar som funktions parametrar.</span><span class="sxs-lookup"><span data-stu-id="f224b-160">Script parameters work like function parameters.</span></span> <span data-ttu-id="f224b-161">Parameter värden är tillgängliga för alla kommandon i skriptet.</span><span class="sxs-lookup"><span data-stu-id="f224b-161">The parameter values are available to all of the commands in the script.</span></span> <span data-ttu-id="f224b-162">Alla funktioner i funktions parametrar, inklusive parameter-attributet och de namngivna argumenten, är också giltiga i skript.</span><span class="sxs-lookup"><span data-stu-id="f224b-162">All of the features of function parameters, including the Parameter attribute and its named arguments, are also valid in scripts.</span></span>

<span data-ttu-id="f224b-163">När skriptet körs skriver skript användare parametrarna efter skript namnet.</span><span class="sxs-lookup"><span data-stu-id="f224b-163">When running the script, script users type the parameters after the script name.</span></span>

<span data-ttu-id="f224b-164">I följande exempel visas ett `Test-Remote.ps1` skript som har en **computername** -parameter.</span><span class="sxs-lookup"><span data-stu-id="f224b-164">The following example shows a `Test-Remote.ps1` script that has a **ComputerName** parameter.</span></span> <span data-ttu-id="f224b-165">Båda skript funktionerna kan komma åt värdet för parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="f224b-165">Both of the script functions can access the **ComputerName** parameter value.</span></span>

```powershell
param ($ComputerName = $(throw "ComputerName parameter is required."))

function CanPing {
   $error.clear()
   $tmp = test-connection $computername -erroraction SilentlyContinue

   if (!$?)
       {write-host "Ping failed: $ComputerName."; return $false}
   else
       {write-host "Ping succeeded: $ComputerName"; return $true}
}

function CanRemote {
    $s = new-pssession $computername -erroraction SilentlyContinue

    if ($s -is [System.Management.Automation.Runspaces.PSSession])
        {write-host "Remote test succeeded: $ComputerName."}
    else
        {write-host "Remote test failed: $ComputerName."}
}

if (CanPing $computername) {CanRemote $computername}
```

<span data-ttu-id="f224b-166">Om du vill köra skriptet skriver du parameter namnet efter skript namnet.</span><span class="sxs-lookup"><span data-stu-id="f224b-166">To run this script, type the parameter name after the script name.</span></span> <span data-ttu-id="f224b-167">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f224b-167">For example:</span></span>

```powershell
C:\PS> .\test-remote.ps1 -computername Server01

Ping succeeded: Server01
Remote test failed: Server01
```

<span data-ttu-id="f224b-168">Mer information om param-instruktionen och funktions parametrarna finns i [about_Functions](about_Functions.md) och [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f224b-168">For more information about the Param statement and the function parameters, see [about_Functions](about_Functions.md) and [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="writing-help-for-scripts"></a><span data-ttu-id="f224b-169">Skriver hjälp för skript</span><span class="sxs-lookup"><span data-stu-id="f224b-169">Writing help for scripts</span></span>

<span data-ttu-id="f224b-170">Du kan skriva ett hjälp avsnitt för ett skript med någon av följande två metoder:</span><span class="sxs-lookup"><span data-stu-id="f224b-170">You can write a help topic for a script by using either of the two following methods:</span></span>

- <span data-ttu-id="f224b-171">Comment-Based hjälp för skript</span><span class="sxs-lookup"><span data-stu-id="f224b-171">Comment-Based Help for Scripts</span></span>

  <span data-ttu-id="f224b-172">Skapa ett hjälp avsnitt genom att använda särskilda nyckelord i kommentarerna.</span><span class="sxs-lookup"><span data-stu-id="f224b-172">Create a Help topic by using special keywords in the comments.</span></span> <span data-ttu-id="f224b-173">Om du vill skapa en kommenterad hjälp för ett skript måste kommentarerna placeras i början eller slutet av skript filen.</span><span class="sxs-lookup"><span data-stu-id="f224b-173">To create comment-based Help for a script, the comments must be placed at the beginning or end of the script file.</span></span> <span data-ttu-id="f224b-174">Mer information om kommenterad hjälp finns [about_Comment_Based_Help](about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="f224b-174">For more information about comment-based Help, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span>

- <span data-ttu-id="f224b-175">XML-Based hjälp för skript</span><span class="sxs-lookup"><span data-stu-id="f224b-175">XML-Based Help  for Scripts</span></span>

  <span data-ttu-id="f224b-176">Skapa ett XML-baserat hjälp avsnitt, till exempel den typ som vanligt vis skapas för cmdletar.</span><span class="sxs-lookup"><span data-stu-id="f224b-176">Create an XML-based Help topic, such as the type that is typically created for cmdlets.</span></span> <span data-ttu-id="f224b-177">XML-baserad hjälp krävs om du översätter hjälp ämnen till flera språk.</span><span class="sxs-lookup"><span data-stu-id="f224b-177">XML-based Help is required if you are translating Help topics into multiple languages.</span></span>

<span data-ttu-id="f224b-178">Om du vill associera skriptet med det XML-baserade hjälp avsnittet använder du. ExternalHelp hjälp kommentar nyckelord.</span><span class="sxs-lookup"><span data-stu-id="f224b-178">To associate the script with the XML-based Help topic, use the .ExternalHelp Help comment keyword.</span></span> <span data-ttu-id="f224b-179">Mer information om nyckelordet ExternalHelp finns [about_Comment_Based_Help](about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="f224b-179">For more information about the ExternalHelp keyword, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span> <span data-ttu-id="f224b-180">Mer information om XML-baserad hjälp finns i [så här skriver du cmdlet-hjälpen](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="f224b-180">For more information about XML-based help, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

### <a name="returning-an-exit-value"></a><span data-ttu-id="f224b-181">Returnerar ett slut värde</span><span class="sxs-lookup"><span data-stu-id="f224b-181">Returning an exit value</span></span>

<span data-ttu-id="f224b-182">Som standard returnerar skript inte en avslutnings status när skriptet slutar.</span><span class="sxs-lookup"><span data-stu-id="f224b-182">By default, scripts do not return an exit status when the script ends.</span></span> <span data-ttu-id="f224b-183">Du måste använda `exit` instruktionen för att returnera en avslutnings kod från ett skript.</span><span class="sxs-lookup"><span data-stu-id="f224b-183">You must use the `exit` statement to return an exit code from a script.</span></span> <span data-ttu-id="f224b-184">Som standard `exit` returnerar instruktionen `0` .</span><span class="sxs-lookup"><span data-stu-id="f224b-184">By default, the `exit` statement returns `0`.</span></span> <span data-ttu-id="f224b-185">Du kan ange ett numeriskt värde för att returnera en annan avslutnings status.</span><span class="sxs-lookup"><span data-stu-id="f224b-185">You can provide a numeric value to return a different exit status.</span></span> <span data-ttu-id="f224b-186">En avslutnings kod som inte är noll signalerar vanligt vis ett haveri.</span><span class="sxs-lookup"><span data-stu-id="f224b-186">A nonzero exit code typically signals a failure.</span></span>

<span data-ttu-id="f224b-187">I Windows är alla siffror mellan `[int]::MinValue` och `[int]::MaxValue` tillåtna.</span><span class="sxs-lookup"><span data-stu-id="f224b-187">On Windows, any number between `[int]::MinValue` and `[int]::MaxValue` is allowed.</span></span>

<span data-ttu-id="f224b-188">På UNIX tillåts endast positiva tal mellan `[byte]::MinValue` (0) och `[byte]::MaxValue` (255).</span><span class="sxs-lookup"><span data-stu-id="f224b-188">On Unix, only positive numbers between `[byte]::MinValue` (0) and `[byte]::MaxValue` (255) are allowed.</span></span> <span data-ttu-id="f224b-189">Ett negativt tal i intervallet `-1` genom `-255` översätts automatiskt till ett positivt tal genom att lägga till</span><span class="sxs-lookup"><span data-stu-id="f224b-189">A negative number in the range of `-1` through `-255` is automatically translated into a positive number by adding</span></span>
256. <span data-ttu-id="f224b-190">`-2`Transformera till exempel till `254` .</span><span class="sxs-lookup"><span data-stu-id="f224b-190">For example, `-2` is transformed to `254`.</span></span>

<span data-ttu-id="f224b-191">I PowerShell `exit` anger instruktionen värdet för `$LASTEXITCODE` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f224b-191">In PowerShell, the `exit` statement sets the value of the `$LASTEXITCODE` variable.</span></span> <span data-ttu-id="f224b-192">I kommando tolken i Windows (cmd.exe) anger avslutnings instruktionen värdet för `%ERRORLEVEL%` miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="f224b-192">In the Windows Command Shell (cmd.exe), the exit statement sets the value of the `%ERRORLEVEL%` environment variable.</span></span>

<span data-ttu-id="f224b-193">Alla argument som inte är numeriska eller utanför det plattformsspecifika intervallet översätts till värdet `0` .</span><span class="sxs-lookup"><span data-stu-id="f224b-193">Any argument that is non-numeric or outside the platform-specific range is translated to the value of `0`.</span></span>

## <a name="script-scope-and-dot-sourcing"></a><span data-ttu-id="f224b-194">Skript omfattning och punkt källa</span><span class="sxs-lookup"><span data-stu-id="f224b-194">Script scope and dot sourcing</span></span>

<span data-ttu-id="f224b-195">Varje skript körs i sitt eget omfång.</span><span class="sxs-lookup"><span data-stu-id="f224b-195">Each script runs in its own scope.</span></span> <span data-ttu-id="f224b-196">Funktioner, variabler, alias och enheter som skapas i skriptet finns bara i skript omfånget.</span><span class="sxs-lookup"><span data-stu-id="f224b-196">The functions, variables, aliases, and drives that are created in the script exist only in the script scope.</span></span> <span data-ttu-id="f224b-197">Du kan inte komma åt dessa objekt eller deras värden i omfånget där skriptet körs.</span><span class="sxs-lookup"><span data-stu-id="f224b-197">You cannot access these items or their values in the scope in which the script runs.</span></span>

<span data-ttu-id="f224b-198">Om du vill köra ett skript i ett annat omfång kan du ange ett omfång, till exempel globalt eller lokalt, eller så kan du dot-källan till skriptet.</span><span class="sxs-lookup"><span data-stu-id="f224b-198">To run a script in a different scope, you can specify a scope, such as Global or Local, or you can dot source the script.</span></span>

<span data-ttu-id="f224b-199">Med funktionen punkt-ursprung kan du köra ett skript i det aktuella omfånget i stället för i skript omfånget.</span><span class="sxs-lookup"><span data-stu-id="f224b-199">The dot sourcing feature lets you run a script in the current scope instead of in the script scope.</span></span> <span data-ttu-id="f224b-200">När du kör ett skript som är i punkt form körs kommandona i skriptet som om du hade skrivit dem i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="f224b-200">When you run a script that is dot sourced, the commands in the script run as though you had typed them at the command prompt.</span></span> <span data-ttu-id="f224b-201">De funktioner, variabler, alias och enheter som skriptet skapar skapas i den omfattning som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="f224b-201">The functions, variables, aliases, and drives that the script creates are created in the scope in which you are working.</span></span> <span data-ttu-id="f224b-202">När skriptet har körts kan du använda de skapade objekten och komma åt deras värden i sessionen.</span><span class="sxs-lookup"><span data-stu-id="f224b-202">After the script runs, you can use the created items and access their values in your session.</span></span>

<span data-ttu-id="f224b-203">Skriv en punkt (.) och ett blank steg före skript Sök vägen för att ange ett skript för punkt källa.</span><span class="sxs-lookup"><span data-stu-id="f224b-203">To dot source a script, type a dot (.) and a space before the script path.</span></span>

<span data-ttu-id="f224b-204">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f224b-204">For example:</span></span>

```powershell
. C:\scripts\UtilityFunctions.ps1
```

<span data-ttu-id="f224b-205">eller</span><span class="sxs-lookup"><span data-stu-id="f224b-205">or</span></span>

```powershell
. .\UtilityFunctions.ps1
```

<span data-ttu-id="f224b-206">När `UtilityFunctions.ps1` skriptet har körts läggs de funktioner och variabler som skriptet skapar till i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="f224b-206">After the `UtilityFunctions.ps1` script runs, the functions and variables that the script creates are added to the current scope.</span></span>

<span data-ttu-id="f224b-207">Skriptet skapar till exempel `UtilityFunctions.ps1` `New-Profile` funktionen och `$ProfileName` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f224b-207">For example, the `UtilityFunctions.ps1` script creates the `New-Profile` function and the `$ProfileName` variable.</span></span>

```powershell
#In UtilityFunctions.ps1

function New-Profile
{
  Write-Host "Running New-Profile function"
  $profileName = split-path $profile -leaf

  if (test-path $profile)
    {write-error "Profile $profileName already exists on this computer."}
  else
    {new-item -type file -path $profile -force }
}
```

<span data-ttu-id="f224b-208">Om du kör `UtilityFunctions.ps1` skriptet i en egen skript omfattning, `New-Profile` finns funktionen och `$ProfileName` variabeln bara när skriptet körs.</span><span class="sxs-lookup"><span data-stu-id="f224b-208">If you run the `UtilityFunctions.ps1` script in its own script scope, the `New-Profile` function and the `$ProfileName` variable exist only while the script is running.</span></span> <span data-ttu-id="f224b-209">När skriptet avslutas tas funktionen och variabeln bort, som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="f224b-209">When the script exits, the function and variable are removed, as shown in the following example.</span></span>

```powershell
C:\PS> .\UtilityFunctions.ps1

C:\PS> New-Profile
The term 'new-profile' is not recognized as a cmdlet, function, operable
program, or script file. Verify the term and try again.
At line:1 char:12
+ new-profile <<<<
   + CategoryInfo          : ObjectNotFound: (new-profile:String) [],
   + FullyQualifiedErrorId : CommandNotFoundException

C:\PS> $profileName
C:\PS>
```

<span data-ttu-id="f224b-210">När du dot-källans skript och kör det skapar skriptet `New-Profile` funktionen och `$ProfileName` variabeln i din-session i ditt omfång.</span><span class="sxs-lookup"><span data-stu-id="f224b-210">When you dot source the script and run it, the script creates the `New-Profile` function and the `$ProfileName` variable in your session in your scope.</span></span> <span data-ttu-id="f224b-211">När skriptet har körts kan du använda `New-Profile` funktionen i din session, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="f224b-211">After the script runs, you can use the `New-Profile` function in your session, as shown in the following example.</span></span>

```powershell
C:\PS> . .\UtilityFunctions.ps1

C:\PS> New-Profile

    Directory: C:\Users\juneb\Documents\WindowsPowerShell

    Mode    LastWriteTime     Length Name
    ----    -------------     ------ ----
    -a---   1/14/2009 3:08 PM      0 Microsoft.PowerShellISE_profile.ps1

C:\PS> $profileName
Microsoft.PowerShellISE_profile.ps1
```

<span data-ttu-id="f224b-212">Mer information om omfång finns i about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="f224b-212">For more information about scope, see about_Scopes.</span></span>

## <a name="scripts-in-modules"></a><span data-ttu-id="f224b-213">Skript i moduler</span><span class="sxs-lookup"><span data-stu-id="f224b-213">Scripts in modules</span></span>

<span data-ttu-id="f224b-214">En modul är en uppsättning relaterade PowerShell-resurser som kan distribueras som en enhet.</span><span class="sxs-lookup"><span data-stu-id="f224b-214">A module is a set of related PowerShell resources that can be distributed as a unit.</span></span> <span data-ttu-id="f224b-215">Du kan använda moduler för att organisera skript, funktioner och andra resurser.</span><span class="sxs-lookup"><span data-stu-id="f224b-215">You can use modules to organize your scripts, functions, and other resources.</span></span> <span data-ttu-id="f224b-216">Du kan också använda moduler för att distribuera din kod till andra och hämta kod från betrodda källor.</span><span class="sxs-lookup"><span data-stu-id="f224b-216">You can also use modules to distribute your code to others, and to get code from trusted sources.</span></span>

<span data-ttu-id="f224b-217">Du kan inkludera skript i dina moduler, eller så kan du skapa en-skript-modul, som är en modul som helt eller huvudsakligen består av ett skript och stöd resurser.</span><span class="sxs-lookup"><span data-stu-id="f224b-217">You can include scripts in your modules, or you can create a script module, which is a module that consists entirely or primarily of a script and supporting resources.</span></span> <span data-ttu-id="f224b-218">En skript-modul är bara ett skript med fil namns tillägget. psm1.</span><span class="sxs-lookup"><span data-stu-id="f224b-218">A script module is just a script with a .psm1 file extension.</span></span>

<span data-ttu-id="f224b-219">Mer information om moduler finns i [about_Modules](about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="f224b-219">For more information about modules, see [about_Modules](about_Modules.md).</span></span>

## <a name="other-script-features"></a><span data-ttu-id="f224b-220">Andra skript funktioner</span><span class="sxs-lookup"><span data-stu-id="f224b-220">Other script features</span></span>

<span data-ttu-id="f224b-221">PowerShell har många användbara funktioner som du kan använda i skript.</span><span class="sxs-lookup"><span data-stu-id="f224b-221">PowerShell has many useful features that you can use in scripts.</span></span>

- <span data-ttu-id="f224b-222">`#Requires` -Du kan använda en `#Requires` instruktion för att förhindra att ett skript körs utan angivna moduler eller snapin-moduler och en angiven version av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f224b-222">`#Requires` - You can use a `#Requires` statement to prevent a script from running without specified modules or snap-ins and a specified version of PowerShell.</span></span> <span data-ttu-id="f224b-223">Mer information finns i about_Requires.</span><span class="sxs-lookup"><span data-stu-id="f224b-223">For more information, see about_Requires.</span></span>

- <span data-ttu-id="f224b-224">`$PSCommandPath` -Innehåller den fullständiga sökvägen till och namnet på skriptet som körs.</span><span class="sxs-lookup"><span data-stu-id="f224b-224">`$PSCommandPath` - Contains the full path and name of the script that is being run.</span></span> <span data-ttu-id="f224b-225">Den här parametern är giltig i alla skript.</span><span class="sxs-lookup"><span data-stu-id="f224b-225">This parameter is valid in all scripts.</span></span> <span data-ttu-id="f224b-226">Den här automatiska variabeln introduceras i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f224b-226">This automatic variable is introduced in PowerShell 3.0.</span></span>

- <span data-ttu-id="f224b-227">`$PSScriptRoot` -Innehåller den katalog som ett skript körs från.</span><span class="sxs-lookup"><span data-stu-id="f224b-227">`$PSScriptRoot` - Contains the directory from which a script is being run.</span></span> <span data-ttu-id="f224b-228">I PowerShell 2,0 är den här variabeln endast giltig i script modules ( `.psm1` ).</span><span class="sxs-lookup"><span data-stu-id="f224b-228">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
  <span data-ttu-id="f224b-229">Från och med PowerShell 3,0 är det giltigt i alla skript.</span><span class="sxs-lookup"><span data-stu-id="f224b-229">Beginning in PowerShell 3.0, it is valid in all scripts.</span></span>

- <span data-ttu-id="f224b-230">`$MyInvocation` -Den `$MyInvocation` automatiska variabeln innehåller information om det aktuella skriptet, inklusive information om hur det startades eller "anropades".</span><span class="sxs-lookup"><span data-stu-id="f224b-230">`$MyInvocation` - The `$MyInvocation` automatic variable contains information about the current script, including information about how it was started or "invoked."</span></span> <span data-ttu-id="f224b-231">Du kan använda den här variabeln och dess egenskaper för att hämta information om skriptet medan det körs.</span><span class="sxs-lookup"><span data-stu-id="f224b-231">You can use this variable and its properties to get information about the script while it is running.</span></span> <span data-ttu-id="f224b-232">Till exempel `$MyInvocation` . En ' for Command. Path '-variabel innehåller sökvägen och fil namnet för skriptet.</span><span class="sxs-lookup"><span data-stu-id="f224b-232">For example, the `$MyInvocation`.MyCommand.Path variable contains the path and filename of the script.</span></span> <span data-ttu-id="f224b-233">`$MyInvocation`. Raden innehåller kommandot som startade skriptet, inklusive alla parametrar och värden.</span><span class="sxs-lookup"><span data-stu-id="f224b-233">`$MyInvocation`.Line contains the command that started the script, including all parameters and values.</span></span>

  <span data-ttu-id="f224b-234">Från och med PowerShell 3,0 `$MyInvocation` har två nya egenskaper som ger information om skriptet som anropade eller anropade det aktuella skriptet.</span><span class="sxs-lookup"><span data-stu-id="f224b-234">Beginning in PowerShell 3.0, `$MyInvocation` has two new properties that provide information about the script that called or invoked the current script.</span></span> <span data-ttu-id="f224b-235">Värdena för dessa egenskaper fylls bara i när anroparen eller anroparen är ett skript.</span><span class="sxs-lookup"><span data-stu-id="f224b-235">The values of these properties are populated only when the invoker or caller is a script.</span></span>

  - <span data-ttu-id="f224b-236">**PSCommandPath** innehåller den fullständiga sökvägen till och namnet på skriptet som anropade eller anropade det aktuella skriptet.</span><span class="sxs-lookup"><span data-stu-id="f224b-236">**PSCommandPath** contains the full path and name of the script that called or invoked the current script.</span></span>

  - <span data-ttu-id="f224b-237">**PSScriptRoot** innehåller katalogen i skriptet som anropade eller anropade det aktuella skriptet.</span><span class="sxs-lookup"><span data-stu-id="f224b-237">**PSScriptRoot** contains the directory of the script that called or invoked the current script.</span></span>

  <span data-ttu-id="f224b-238">Till skillnad från `$PSCommandPath` de `$PSScriptRoot` automatiska variablerna, som innehåller information om det aktuella skriptet, innehåller egenskaperna **PSCommandPath** och **PSScriptRoot** för `$MyInvocation` variabeln information om det skript som anropade det aktuella skriptet.</span><span class="sxs-lookup"><span data-stu-id="f224b-238">Unlike the `$PSCommandPath` and `$PSScriptRoot` automatic variables, which contain information about the current script, the **PSCommandPath** and **PSScriptRoot** properties of the `$MyInvocation` variable contain information about the script that called the current script.</span></span>

- <span data-ttu-id="f224b-239">Data avsnitt – du kan använda `Data` nyckelordet för att separera data från logik i skript.</span><span class="sxs-lookup"><span data-stu-id="f224b-239">Data sections - You can use the `Data` keyword to separate data from logic in scripts.</span></span> <span data-ttu-id="f224b-240">Data avsnitt kan också förenkla lokaliseringen.</span><span class="sxs-lookup"><span data-stu-id="f224b-240">Data sections can also make localization easier.</span></span> <span data-ttu-id="f224b-241">Mer information finns i [about_Data_Sections](about_Data_Sections.md) och [about_Script_Internationalization](about_Script_Internationalization.md).</span><span class="sxs-lookup"><span data-stu-id="f224b-241">For more information, see [about_Data_Sections](about_Data_Sections.md) and [about_Script_Internationalization](about_Script_Internationalization.md).</span></span>

- <span data-ttu-id="f224b-242">Skript signering – du kan lägga till en digital signatur i ett skript.</span><span class="sxs-lookup"><span data-stu-id="f224b-242">Script Signing - You can add a digital signature to a script.</span></span> <span data-ttu-id="f224b-243">Beroende på körnings principen kan du använda digitala signaturer för att begränsa körningen av skript som kan innehålla osäkra kommandon.</span><span class="sxs-lookup"><span data-stu-id="f224b-243">Depending on the execution policy, you can use digital signatures to restrict the running of scripts that could include unsafe commands.</span></span> <span data-ttu-id="f224b-244">Mer information finns i [about_Execution_Policies](about_Execution_Policies.md) och [about_Signing](about_Signing.md).</span><span class="sxs-lookup"><span data-stu-id="f224b-244">For more information, see [about_Execution_Policies](about_Execution_Policies.md) and [about_Signing](about_Signing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f224b-245">Se även</span><span class="sxs-lookup"><span data-stu-id="f224b-245">See also</span></span>

[<span data-ttu-id="f224b-246">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="f224b-246">about_Command_Precedence</span></span>](about_Command_Precedence.md)

[<span data-ttu-id="f224b-247">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="f224b-247">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="f224b-248">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="f224b-248">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="f224b-249">about_Functions</span><span class="sxs-lookup"><span data-stu-id="f224b-249">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="f224b-250">about_Modules</span><span class="sxs-lookup"><span data-stu-id="f224b-250">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="f224b-251">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="f224b-251">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="f224b-252">about_Requires</span><span class="sxs-lookup"><span data-stu-id="f224b-252">about_Requires</span></span>](about_Requires.md)

[<span data-ttu-id="f224b-253">about_Run_With_PowerShell</span><span class="sxs-lookup"><span data-stu-id="f224b-253">about_Run_With_PowerShell</span></span>](about_Run_With_PowerShell.md)

[<span data-ttu-id="f224b-254">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="f224b-254">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="f224b-255">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="f224b-255">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="f224b-256">about_Signing</span><span class="sxs-lookup"><span data-stu-id="f224b-256">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="f224b-257">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="f224b-257">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)