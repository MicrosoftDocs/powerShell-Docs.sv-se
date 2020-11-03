---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: 2fe48f90b020d0566364f4f24554cb3442880ab5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264974"
---
# <span data-ttu-id="88651-103">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="88651-103">Import-PSSession</span></span>

## <span data-ttu-id="88651-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="88651-104">SYNOPSIS</span></span>
<span data-ttu-id="88651-105">Importerar kommandon från en annan session till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-105">Imports commands from another session into the current session.</span></span>

## <span data-ttu-id="88651-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="88651-106">SYNTAX</span></span>

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## <span data-ttu-id="88651-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="88651-107">DESCRIPTION</span></span>
<span data-ttu-id="88651-108">Cmdleten **import-PSSession** importerar kommandon, till exempel cmdlets, Functions och alias, från en PSSession på en lokal eller fjärran sluten dator till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-108">The **Import-PSSession** cmdlet imports commands , such as cmdlets, functions, and aliases, from a PSSession on a local or remote computer into the current session.</span></span>
<span data-ttu-id="88651-109">Du kan importera alla kommandon som Get-Command-cmdlet: en kan hitta i PSSession.</span><span class="sxs-lookup"><span data-stu-id="88651-109">You can import any command that the Get-Command cmdlet can find in the PSSession.</span></span>

<span data-ttu-id="88651-110">Använd ett **import-PSSession-** kommando för att importera kommandon från ett anpassat gränssnitt, till exempel ett Microsoft Exchange Server-gränssnitt eller från en session som innehåller Windows PowerShell-moduler och snapin-moduler eller andra element som inte finns i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-110">Use an **Import-PSSession** command to import commands from a customized shell, such as a Microsoft Exchange Server shell, or from a session that includes Windows PowerShell modules and snap-ins or other elements that are not in the current session.</span></span>

<span data-ttu-id="88651-111">Om du vill importera kommandon använder du först New-PSSession-cmdlet: en för att skapa en PSSession.</span><span class="sxs-lookup"><span data-stu-id="88651-111">To import commands, first use the New-PSSession cmdlet to create a PSSession.</span></span>
<span data-ttu-id="88651-112">Använd sedan cmdleten **import-PSSession** för att importera kommandona.</span><span class="sxs-lookup"><span data-stu-id="88651-112">Then, use the **Import-PSSession** cmdlet to import the commands.</span></span>
<span data-ttu-id="88651-113">Som standard importerar **import-PSSession** alla kommandon utom kommandon som har samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-113">By default, **Import-PSSession** imports all commands except for commands that have the same names as commands in the current session.</span></span>
<span data-ttu-id="88651-114">Om du vill importera alla kommandon använder du parametern *AllowClobber* .</span><span class="sxs-lookup"><span data-stu-id="88651-114">To import all the commands, use the *AllowClobber* parameter.</span></span>

<span data-ttu-id="88651-115">Du kan använda importerade kommandon precis som med alla kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-115">You can use imported commands just as you would use any command in the session.</span></span>
<span data-ttu-id="88651-116">När du använder ett importerat kommando körs den importerade delen av kommandot implicit i den session som det importerades från.</span><span class="sxs-lookup"><span data-stu-id="88651-116">When you use an imported command, the imported part of the command runs implicitly in the session from which it was imported.</span></span>
<span data-ttu-id="88651-117">Fjärråtgärder hanteras dock helt av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88651-117">However, the remote operations are handled entirely by Windows PowerShell.</span></span>
<span data-ttu-id="88651-118">Du behöver inte ens vara medveten om dem, förutom att du måste hålla anslutningen till den andra sessionen (PSSession) öppen.</span><span class="sxs-lookup"><span data-stu-id="88651-118">You need not even be aware of them, except that you must keep the connection to the other session (PSSession) open.</span></span>
<span data-ttu-id="88651-119">Om du stänger den är de importerade kommandona inte längre tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="88651-119">If you close it, the imported commands are no longer available.</span></span>

<span data-ttu-id="88651-120">Eftersom importerade kommandon kan ta längre tid att köra än lokala kommandon, lägger **import-PSSession** till en *AsJob* -parameter till alla importerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="88651-120">Because imported commands might take longer to run than local commands, **Import-PSSession** adds an *AsJob* parameter to every imported command.</span></span>
<span data-ttu-id="88651-121">Med den här parametern kan du köra kommandot som ett bakgrunds jobb i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88651-121">This parameter allows you to run the command as a Windows PowerShell background job.</span></span>
<span data-ttu-id="88651-122">Mer information finns i artikeln om jobb.</span><span class="sxs-lookup"><span data-stu-id="88651-122">For more information, see about_Jobs.</span></span>

<span data-ttu-id="88651-123">När du använder **import-PSSession** lägger Windows PowerShell till de importerade kommandona till en tillfällig modul som bara finns i din session och returnerar ett objekt som representerar modulen.</span><span class="sxs-lookup"><span data-stu-id="88651-123">When you use **Import-PSSession** , Windows PowerShell adds the imported commands to a temporary module that exists only in your session and returns an object that represents the module.</span></span>
<span data-ttu-id="88651-124">Använd Export-PSSession-cmdleten om du vill skapa en beständig modul som du kan använda i framtida sessioner.</span><span class="sxs-lookup"><span data-stu-id="88651-124">To create a persistent module that you can use in future sessions, use the Export-PSSession cmdlet.</span></span>

<span data-ttu-id="88651-125">Cmdlet **: en import-PSSession** använder funktionen för implicit fjärr kommunikation i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88651-125">The **Import-PSSession** cmdlet uses the implicit remoting feature of Windows PowerShell.</span></span>
<span data-ttu-id="88651-126">När du importerar kommandon till den aktuella sessionen körs de implicit i den ursprungliga sessionen eller i en liknande session på den ursprungliga datorn.</span><span class="sxs-lookup"><span data-stu-id="88651-126">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

<span data-ttu-id="88651-127">Från och med Windows PowerShell 3,0 kan du använda cmdleten Import-Module för att importera moduler från en fjärran sluten session till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-127">Beginning in Windows PowerShell 3.0, you can use the Import-Module cmdlet to import modules from a remote session into the current session.</span></span>
<span data-ttu-id="88651-128">Den här funktionen använder implicit fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="88651-128">This feature uses implicit remoting.</span></span>
<span data-ttu-id="88651-129">Det motsvarar att använda **import-PSSession** för att importera valda moduler från en fjärrsession till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-129">It is equivalent to using **Import-PSSession** to import selected modules from a remote session into the current session.</span></span>

## <span data-ttu-id="88651-130">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="88651-130">EXAMPLES</span></span>

### <span data-ttu-id="88651-131">Exempel 1: importera alla kommandon från en PSSession</span><span class="sxs-lookup"><span data-stu-id="88651-131">Example 1: Import all commands from a PSSession</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

<span data-ttu-id="88651-132">Det här kommandot importerar alla kommandon från en PSSession på Server01-datorn till den aktuella sessionen, förutom kommandon som har samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-132">This command imports all commands from a PSSession on the Server01 computer into the current session, except for commands that have the same names as commands in the current session.</span></span>

<span data-ttu-id="88651-133">Eftersom det här kommandot inte använder *commandname* -parametern importeras även all formatering som krävs för de importerade kommandona.</span><span class="sxs-lookup"><span data-stu-id="88651-133">Because this command does not use the *CommandName* parameter, it also imports all of the formatting data required for the imported commands.</span></span>

### <span data-ttu-id="88651-134">Exempel 2: importera kommandon som slutar med en angiven sträng</span><span class="sxs-lookup"><span data-stu-id="88651-134">Example 2: Import commands that end with a specific string</span></span>

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

<span data-ttu-id="88651-135">Kommandona importerar kommandona med namn som slutar med "-test" från en PSSession till den lokala sessionen, och sedan visar de hur man använder en importerad cmdlet.</span><span class="sxs-lookup"><span data-stu-id="88651-135">These commands import the commands with names that end in "-test" from a PSSession into the local session, and then they show how to use an imported cmdlet.</span></span>

<span data-ttu-id="88651-136">Det första kommandot använder New-PSSession-cmdlet för att skapa en PSSession.</span><span class="sxs-lookup"><span data-stu-id="88651-136">The first command uses the New-PSSession cmdlet to create a PSSession.</span></span>
<span data-ttu-id="88651-137">Den sparar PSSession i variabeln $S.</span><span class="sxs-lookup"><span data-stu-id="88651-137">It saves the PSSession in the $S variable.</span></span>

<span data-ttu-id="88651-138">Det andra kommandot använder cmdleten **import-PSSession** för att importera kommandon från PSSession i $S till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-138">The second command uses the **Import-PSSession** cmdlet to import commands from the PSSession in $S into the current session.</span></span>
<span data-ttu-id="88651-139">Parametern *commandname* används för att ange kommandon med parametern test Substantiv och parametern *FormatTypeName* för att importera formateringsinformationen för test kommandona.</span><span class="sxs-lookup"><span data-stu-id="88651-139">It uses the *CommandName* parameter to specify commands with the Test noun and the *FormatTypeName* parameter to import the formatting data for the Test commands.</span></span>

<span data-ttu-id="88651-140">De tredje och fjärde kommandona använder de importerade kommandona i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-140">The third and fourth commands use the imported commands in the current session.</span></span>
<span data-ttu-id="88651-141">Eftersom importerade kommandon faktiskt läggs till i den aktuella sessionen använder du den lokala syntaxen för att köra dem.</span><span class="sxs-lookup"><span data-stu-id="88651-141">Because imported commands are actually added to the current session, you use the local syntax to run them.</span></span>
<span data-ttu-id="88651-142">Du behöver inte använda Invoke-Command cmdlet för att köra ett importerat kommando.</span><span class="sxs-lookup"><span data-stu-id="88651-142">You do not need to use the Invoke-Command cmdlet to run an imported command.</span></span>

### <span data-ttu-id="88651-143">Exempel 3: importera cmdletar från en PSSession</span><span class="sxs-lookup"><span data-stu-id="88651-143">Example 3: Import cmdlets from a PSSession</span></span>

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

<span data-ttu-id="88651-144">Det här exemplet visar att du kan använda importerade cmdlets på samma sätt som du använder lokala cmdlets.</span><span class="sxs-lookup"><span data-stu-id="88651-144">This example shows that you can use imported cmdlets just as you would use local cmdlets.</span></span>

<span data-ttu-id="88651-145">Dessa kommandon importerar New-Test-och Get-Test-cmdletar från en PSSession på Server01-datorn och Set-Test-cmdleten från en PSSession på Server02-datorn.</span><span class="sxs-lookup"><span data-stu-id="88651-145">These commands import the New-Test and Get-Test cmdlets from a PSSession on the Server01 computer and the Set-Test cmdlet from a PSSession on the Server02 computer.</span></span>

<span data-ttu-id="88651-146">Även om cmdletarna har importer ATS från olika PSSessions kan du skicka ett objekt från en cmdlet till en annan utan fel.</span><span class="sxs-lookup"><span data-stu-id="88651-146">Even though the cmdlets were imported from different PSSessions, you can pipe an object from one cmdlet to another without error.</span></span>

### <span data-ttu-id="88651-147">Exempel 4: kör ett importerat kommando som bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="88651-147">Example 4: Run an imported command as a background job</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

<span data-ttu-id="88651-148">Det här exemplet visar hur du kör ett importerat kommando som bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="88651-148">This example shows how to run an imported command as a background job.</span></span>

<span data-ttu-id="88651-149">Eftersom importerade kommandon kan ta längre tid att köra än lokala kommandon, lägger **import-PSSession** till en *AsJob* -parameter till alla importerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="88651-149">Because imported commands might take longer to run than local commands, **Import-PSSession** adds an *AsJob* parameter to every imported command.</span></span>
<span data-ttu-id="88651-150">Med parametern *AsJob* kan du köra kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="88651-150">The *AsJob* parameter lets you run the command as a background job.</span></span>

<span data-ttu-id="88651-151">Det första kommandot skapar en PSSession på Server01-datorn och sparar PSSession-objektet i variabeln $S.</span><span class="sxs-lookup"><span data-stu-id="88651-151">The first command creates a PSSession on the Server01 computer and saves the PSSession object in the $S variable.</span></span>

<span data-ttu-id="88651-152">Det andra kommandot använder **import-PSSession** för att importera test-cmdletarna från PSSession i $S till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-152">The second command uses **Import-PSSession** to import the Test cmdlets from the PSSession in $S into the current session.</span></span>

<span data-ttu-id="88651-153">Det tredje kommandot använder parametern *AsJob* för den importerade New-Test-cmdleten för att köra ett New-Test-kommando som bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="88651-153">The third command uses the *AsJob* parameter of the imported New-Test cmdlet to run a New-Test command as a background job.</span></span>
<span data-ttu-id="88651-154">Kommandot sparar jobbobjektet som New-Test returnerar i $batch variabeln.</span><span class="sxs-lookup"><span data-stu-id="88651-154">The command saves the job object that New-Test returns in the $batch variable.</span></span>

<span data-ttu-id="88651-155">Det fjärde kommandot använder cmdleten Receive-Job för att hämta resultatet av jobbet i $batch variabeln.</span><span class="sxs-lookup"><span data-stu-id="88651-155">The fourth command uses the Receive-Job cmdlet to get the results of the job in the $batch variable.</span></span>

### <span data-ttu-id="88651-156">Exempel 5: importera cmdlets och Functions från en Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="88651-156">Example 5: Import cmdlets and functions from a Windows PowerShell module</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

<span data-ttu-id="88651-157">Det här exemplet visar hur du importerar cmdlets och Functions från en Windows PowerShell-modul på en fjärrdator till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-157">This example shows how to import the cmdlets and functions from a Windows PowerShell module on a remote computer into the current session.</span></span>

<span data-ttu-id="88651-158">Det första kommandot skapar en PSSession på Server01-datorn och sparar den i variabeln $S.</span><span class="sxs-lookup"><span data-stu-id="88651-158">The first command creates a PSSession on the Server01 computer and saves it in the $S variable.</span></span>

<span data-ttu-id="88651-159">Det andra kommandot använder cmdleten **Invoke-Command** för att köra ett Import-Module-kommando i PSSession i $S.</span><span class="sxs-lookup"><span data-stu-id="88651-159">The second command uses the **Invoke-Command** cmdlet to run an Import-Module command in the PSSession in $S.</span></span>

<span data-ttu-id="88651-160">Normalt läggs modulen till i alla sessioner med kommandot **import-module** i en Windows PowerShell-profil, men profilerna körs inte i PSSessions.</span><span class="sxs-lookup"><span data-stu-id="88651-160">Typically, the module would be added to all sessions by an **Import-Module** command in a Windows PowerShell profile, but profiles are not run in PSSessions.</span></span>

<span data-ttu-id="88651-161">Det tredje kommandot använder *modulen modul*  för **import-PSSession** för att importera cmdletarna och funktionerna i modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-161">The third command uses the *Module*  parameter of **Import-PSSession** to import the cmdlets and functions in the module into the current session.</span></span>

### <span data-ttu-id="88651-162">Exempel 6: skapa en modul i en temporär fil</span><span class="sxs-lookup"><span data-stu-id="88651-162">Example 6: Create a module in a temporary file</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="88651-163">Det här exemplet visar att **import-PSSession** skapar en modul i en temporär fil på disk.</span><span class="sxs-lookup"><span data-stu-id="88651-163">This example shows that **Import-PSSession** creates a module in a temporary file on disk.</span></span>
<span data-ttu-id="88651-164">Det visar också att alla kommandon konverteras till funktioner innan de importeras till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-164">It also shows that all commands are converted into functions before they are imported into the current session.</span></span>

<span data-ttu-id="88651-165">Kommandot använder cmdleten **import-PSSession** för att importera en Get-Date-cmdlet och en SearchHelp-funktion till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-165">The command uses the **Import-PSSession** cmdlet to import a Get-Date cmdlet and a SearchHelp function into the current session.</span></span>

<span data-ttu-id="88651-166">Cmdleten **import-PSSession** returnerar ett **PSModuleInfo** -objekt som representerar den temporära modulen.</span><span class="sxs-lookup"><span data-stu-id="88651-166">The **Import-PSSession** cmdlet returns a **PSModuleInfo** object that represents the temporary module.</span></span>
<span data-ttu-id="88651-167">Värdet för egenskapen **sökväg** visar att **import-PSSession** skapade en skriptfil (. psm1)-fil på en tillfällig plats.</span><span class="sxs-lookup"><span data-stu-id="88651-167">The value of the **Path** property shows that **Import-PSSession** created a script module (.psm1) file in a temporary location.</span></span>
<span data-ttu-id="88651-168">Egenskapen **ExportedFunctions** visar att **Get-date-** cmdlet: en och SearchHelp-funktionen har importer ATS som functions.</span><span class="sxs-lookup"><span data-stu-id="88651-168">The **ExportedFunctions** property shows that the **Get-Date** cmdlet and the SearchHelp function were both imported as functions.</span></span>

### <span data-ttu-id="88651-169">Exempel 7: köra ett kommando som är dolt av ett importerat kommando</span><span class="sxs-lookup"><span data-stu-id="88651-169">Example 7: Run a command that is hidden by an imported command</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date -FormatTypeName * -AllowClobber

PS C:\> Get-Command Get-Date -All

CommandType   Name       Definition
-----------   ----       ----------
Function      Get-Date   ...
Cmdlet        Get-Date   Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>]

PS C:\> Get-Date
09074

PS C:\> (Get-Command -Type Cmdlet -Name Get-Date).PSSnapin.Name
Microsoft.PowerShell.Utility

PS C:\> Microsoft.PowerShell.Utility\Get-Date
Sunday, March 15, 2009 2:08:26 PM
```

<span data-ttu-id="88651-170">Det här exemplet visar hur du kör ett kommando som är dolt av ett importerat kommando.</span><span class="sxs-lookup"><span data-stu-id="88651-170">This example shows how to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="88651-171">Det första kommandot importerar en Get-Date-cmdlet från PSSession i $S-variabeln.</span><span class="sxs-lookup"><span data-stu-id="88651-171">The first command imports a Get-Date cmdlet from the PSSession in the $S variable.</span></span>
<span data-ttu-id="88651-172">Eftersom den aktuella sessionen innehåller en **Get-date-** cmdlet, krävs parametern *AllowClobber* i kommandot.</span><span class="sxs-lookup"><span data-stu-id="88651-172">Because the current session includes a **Get-Date** cmdlet, the *AllowClobber* parameter is required in the command.</span></span>

<span data-ttu-id="88651-173">Det andra kommandot använder parametern **all** i Get-Command-cmdlet för att hämta alla **Get-date-** kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-173">The second command uses the **All** parameter of the Get-Command cmdlet to get all **Get-Date** commands in the current session.</span></span>
<span data-ttu-id="88651-174">Utdata visar att sessionen innehåller den ursprungliga **Get-date-** cmdleten och en **Get-date-** funktion.</span><span class="sxs-lookup"><span data-stu-id="88651-174">The output shows that the session includes the original **Get-Date** cmdlet and a **Get-Date** function.</span></span>
<span data-ttu-id="88651-175">Funktionen **Get-date** kör den importerade **Get-date-** cmdleten i PSSession i $S.</span><span class="sxs-lookup"><span data-stu-id="88651-175">The **Get-Date** function runs the imported **Get-Date** cmdlet in the PSSession in $S.</span></span>

<span data-ttu-id="88651-176">Det tredje kommandot kör ett **Get-date-** kommando.</span><span class="sxs-lookup"><span data-stu-id="88651-176">The third command runs a **Get-Date** command.</span></span>
<span data-ttu-id="88651-177">Eftersom Functions har företräde framför cmdlets, kör Windows PowerShell den importerade **Get-date-** funktionen som returnerar ett Juliansk-datum.</span><span class="sxs-lookup"><span data-stu-id="88651-177">Because functions take precedence over cmdlets, Windows PowerShell runs the imported **Get-Date** function, which returns a Julian date.</span></span>

<span data-ttu-id="88651-178">De fjärde och femte kommandona visar hur du använder ett kvalificerat namn för att köra ett kommando som är dolt av ett importerat kommando.</span><span class="sxs-lookup"><span data-stu-id="88651-178">The fourth and fifth commands show how to use a qualified name to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="88651-179">Det fjärde kommandot hämtar namnet på Windows PowerShell-snapin-modulen som lade till den ursprungliga cmdleten **Get-date** i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-179">The fourth command gets the name of the Windows PowerShell snap-in that added the original **Get-Date** cmdlet to the current session.</span></span>

<span data-ttu-id="88651-180">Det femte kommandot använder det Snap-i-kvalificerade namnet för **Get-date** -cmdleten för att köra ett **Get-date** -kommando.</span><span class="sxs-lookup"><span data-stu-id="88651-180">The fifth command uses the snap-in-qualified name of the **Get-Date** cmdlet to run a **Get-Date** command.</span></span>

<span data-ttu-id="88651-181">Mer information om kommando prioritet och dolda kommandon finns about_Command_Precedence.</span><span class="sxs-lookup"><span data-stu-id="88651-181">For more information about command precedence and hidden commands, see about_Command_Precedence.</span></span>

### <span data-ttu-id="88651-182">Exempel 8: importera kommandon som har en angiven sträng i sina namn</span><span class="sxs-lookup"><span data-stu-id="88651-182">Example 8: Import commands that have a specific string in their names</span></span>

```
PS C:\> Import-PSSession -Session $S -CommandName *Item* -AllowClobber
```

<span data-ttu-id="88651-183">Det här kommandot importerar kommandon vars namn innehåller objekt från PSSession i $S.</span><span class="sxs-lookup"><span data-stu-id="88651-183">This command imports commands whose names include Item from the PSSession in $S.</span></span>
<span data-ttu-id="88651-184">Eftersom kommandot innehåller parametern *commandname* men inte parametern *FormatTypeData* , importeras bara kommandot.</span><span class="sxs-lookup"><span data-stu-id="88651-184">Because the command includes the *CommandName* parameter but not the *FormatTypeData* parameter, only the command is imported.</span></span>

<span data-ttu-id="88651-185">Använd det här kommandot när du använder **import-PSSession** för att köra ett kommando på en fjärrdator och du redan har format data för kommandot i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-185">Use this command when you are using **Import-PSSession** to run a command on a remote computer and you already have the formatting data for the command in the current session.</span></span>

### <span data-ttu-id="88651-186">Exempel 9: Använd parametern module för att identifiera vilka kommandon som har importer ATS till sessionen</span><span class="sxs-lookup"><span data-stu-id="88651-186">Example 9: Use the Module parameter to discover which commands were imported into the session</span></span>

```
PS C:\> $M = Import-PSSession -Session $S -CommandName *bits* -FormatTypeName *bits*
PS C:\> Get-Command -Module $M
CommandType     Name
-----------     ----
Function        Add-BitsFile
Function        Complete-BitsTransfer
Function        Get-BitsTransfer
Function        Remove-BitsTransfer
Function        Resume-BitsTransfer
Function        Set-BitsTransfer
Function        Start-BitsTransfer
Function        Suspend-BitsTransfer
```

<span data-ttu-id="88651-187">Det här kommandot visar hur du använder parametern *module* för **Get-Command** för att ta reda på vilka kommandon som har importer ATS till sessionen av ett **import-PSSession-** kommando.</span><span class="sxs-lookup"><span data-stu-id="88651-187">This command shows how to use the *Module* parameter of **Get-Command** to find out which commands were imported into the session by an **Import-PSSession** command.</span></span>

<span data-ttu-id="88651-188">Det första kommandot använder cmdleten **import-PSSession** för att importera kommandon vars namn innehåller "bitar" från PSSession i variabeln $S.</span><span class="sxs-lookup"><span data-stu-id="88651-188">The first command uses the **Import-PSSession** cmdlet to import commands whose names include "bits" from the PSSession in the $S variable.</span></span>
<span data-ttu-id="88651-189">Kommandot **import-PSSession** returnerar en tillfällig modul och kommandot sparar modulen i variabeln $m.</span><span class="sxs-lookup"><span data-stu-id="88651-189">The **Import-PSSession** command returns a temporary module, and the command saves the module in the $m variable.</span></span>

<span data-ttu-id="88651-190">Det andra kommandot använder cmdleten Get-Command för att hämta de kommandon som exporteras av modulen i $M variabeln.</span><span class="sxs-lookup"><span data-stu-id="88651-190">The second command uses the Get-Command cmdlet to get the commands that are exported by the module in the $M variable.</span></span>

<span data-ttu-id="88651-191">Parametern *module* använder ett sträng värde, vilket är utformat för modulnamnet.</span><span class="sxs-lookup"><span data-stu-id="88651-191">The *Module* parameter takes a string value, which is designed for the module name.</span></span>
<span data-ttu-id="88651-192">Men när du skickar ett modul-objekt använder Windows PowerShell metoden **toString** i objektet module, som returnerar modulnamnet.</span><span class="sxs-lookup"><span data-stu-id="88651-192">However, when you submit a module object, Windows PowerShell uses the **ToString** method on the module object, which returns the module name.</span></span>

<span data-ttu-id="88651-193">Kommandot **Get-Command** motsvarar `Get-Command $M.Name` ".</span><span class="sxs-lookup"><span data-stu-id="88651-193">The **Get-Command** command is the equivalent of `Get-Command $M.Name`".</span></span>

## <span data-ttu-id="88651-194">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="88651-194">PARAMETERS</span></span>

### <span data-ttu-id="88651-195">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="88651-195">-AllowClobber</span></span>
<span data-ttu-id="88651-196">Anger att denna cmdlet importerar de angivna kommandona, även om de har samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-196">Indicates that this cmdlet imports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="88651-197">Om du importerar ett kommando med samma namn som ett kommando i den aktuella sessionen, döljer det importerade kommandot eller ersätter de ursprungliga kommandona.</span><span class="sxs-lookup"><span data-stu-id="88651-197">If you import a command with the same name as a command in the current session, the imported command hides or replaces the original commands.</span></span>
<span data-ttu-id="88651-198">Mer information finns i about_Command_Precedence.</span><span class="sxs-lookup"><span data-stu-id="88651-198">For more information, see about_Command_Precedence.</span></span>

<span data-ttu-id="88651-199">**Import-PSSession** importerar som standard inte kommandon som har samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-199">By default, **Import-PSSession** does not import commands that have the same name as commands in the current session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88651-200">– Argument List</span><span class="sxs-lookup"><span data-stu-id="88651-200">-ArgumentList</span></span>
<span data-ttu-id="88651-201">Anger en matris med kommandon som resulterar från att använda de angivna argumenten (parameter värden).</span><span class="sxs-lookup"><span data-stu-id="88651-201">Specifies an array of commands that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="88651-202">För att till exempel importera varianten av kommandot Get-Item i certifikatet (cert:) enhet i PSSession i $S skriver du `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .</span><span class="sxs-lookup"><span data-stu-id="88651-202">For instance, to import the variant of the Get-Item command in the certificate (Cert:) drive in the PSSession in $S, type `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88651-203">– Certifikat</span><span class="sxs-lookup"><span data-stu-id="88651-203">-Certificate</span></span>
<span data-ttu-id="88651-204">Anger det klient certifikat som används för att signera format-filer (\* .Format.ps1XML) eller psm1 (.) i den temporära modul som **import-PSSession** skapar.</span><span class="sxs-lookup"><span data-stu-id="88651-204">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the temporary module that **Import-PSSession** creates.</span></span>

<span data-ttu-id="88651-205">Ange en variabel som innehåller ett certifikat eller ett kommando eller uttryck som hämtar certifikatet.</span><span class="sxs-lookup"><span data-stu-id="88651-205">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="88651-206">Använd cmdleten Get-PfxCertificate för att hitta ett certifikat eller Använd cmdleten Get-ChildItem i certifikatet (cert:) kombinationsenhet.</span><span class="sxs-lookup"><span data-stu-id="88651-206">To find a certificate, use the Get-PfxCertificate cmdlet or use the Get-ChildItem cmdlet in the Certificate (Cert:) drive.</span></span>
<span data-ttu-id="88651-207">Om certifikatet inte är giltigt eller inte har tillräcklig behörighet, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="88651-207">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88651-208">– CommandName</span><span class="sxs-lookup"><span data-stu-id="88651-208">-CommandName</span></span>
<span data-ttu-id="88651-209">Anger kommandon med angivna namn eller namn mönster.</span><span class="sxs-lookup"><span data-stu-id="88651-209">Specifies commands with the specified names or name patterns.</span></span>
<span data-ttu-id="88651-210">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="88651-210">Wildcards are permitted.</span></span>
<span data-ttu-id="88651-211">Använd *commandname* eller dess alias, *namn*.</span><span class="sxs-lookup"><span data-stu-id="88651-211">Use *CommandName* or its alias, *Name*.</span></span>

<span data-ttu-id="88651-212">Som standard importerar **import-PSSession** alla kommandon från sessionen, förutom kommandon som har samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-212">By default, **Import-PSSession** imports all commands from the session, except for commands that have the same names as commands in the current session.</span></span>
<span data-ttu-id="88651-213">Detta förhindrar att importerade kommandon döljer eller ersätter kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-213">This prevents imported commands from hiding or replacing commands in the session.</span></span>
<span data-ttu-id="88651-214">Om du vill importera alla kommandon, även de som döljer eller ersätter andra kommandon, använder du parametern *AllowClobber* .</span><span class="sxs-lookup"><span data-stu-id="88651-214">To import all commands, even those that hide or replace other commands, use the *AllowClobber* parameter.</span></span>

<span data-ttu-id="88651-215">Om du använder parametern *commandname* importeras inte formateringsattribut för kommandona om du inte använder parametern *FormatTypeName* .</span><span class="sxs-lookup"><span data-stu-id="88651-215">If you use the *CommandName* parameter, the formatting files for the commands are not imported unless you use the *FormatTypeName* parameter.</span></span>
<span data-ttu-id="88651-216">På liknande sätt importeras inga kommandon om du använder parametern *FormatTypeName* , om du inte använder parametern *commandname* .</span><span class="sxs-lookup"><span data-stu-id="88651-216">Similarly, if you use the *FormatTypeName* parameter, no commands are imported unless you use the *CommandName* parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88651-217">-CommandType</span><span class="sxs-lookup"><span data-stu-id="88651-217">-CommandType</span></span>
<span data-ttu-id="88651-218">Anger typ av kommando objekt.</span><span class="sxs-lookup"><span data-stu-id="88651-218">Specifies the type of command objects.</span></span>
<span data-ttu-id="88651-219">Standardvärdet är cmdlet.</span><span class="sxs-lookup"><span data-stu-id="88651-219">The default value is Cmdlet.</span></span>
<span data-ttu-id="88651-220">Använd *CommandType* eller dess alias och *Skriv*.</span><span class="sxs-lookup"><span data-stu-id="88651-220">Use *CommandType* or its alias, *Type*.</span></span>
<span data-ttu-id="88651-221">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="88651-221">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="88651-222">Aliasuppsättning.</span><span class="sxs-lookup"><span data-stu-id="88651-222">Alias.</span></span>
<span data-ttu-id="88651-223">Windows PowerShell-alias i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-223">The Windows PowerShell aliases in the remote session.</span></span>
- <span data-ttu-id="88651-224">Vissa.</span><span class="sxs-lookup"><span data-stu-id="88651-224">All.</span></span>
<span data-ttu-id="88651-225">Cmdlets och Functions i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-225">The cmdlets and functions in the remote session.</span></span>
- <span data-ttu-id="88651-226">Applicering.</span><span class="sxs-lookup"><span data-stu-id="88651-226">Application.</span></span>
<span data-ttu-id="88651-227">Alla filer utom Windows-PowerShell filer i Sök vägarna som anges i miljövariabeln PATH ($env:p ökväg) i fjärrsessionen, inklusive. txt-,. exe-och. dll-filer.</span><span class="sxs-lookup"><span data-stu-id="88651-227">All the files other than Windows-PowerShell files in the paths that are listed in the Path environment variable ($env:path) in the remote session, including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="88651-228">Kommandon.</span><span class="sxs-lookup"><span data-stu-id="88651-228">Cmdlet.</span></span>
<span data-ttu-id="88651-229">Cmdletarna i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-229">The cmdlets in the remote session.</span></span>
<span data-ttu-id="88651-230">"Cmdlet" är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="88651-230">"Cmdlet" is the default.</span></span>
- <span data-ttu-id="88651-231">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="88651-231">ExternalScript.</span></span>
<span data-ttu-id="88651-232">. Ps1-filerna i Sök vägarna som anges i miljövariabeln PATH ($env:p ökväg) i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-232">The .ps1 files in the paths listed in the Path environment variable ($env:path) in the remote session.</span></span>
- <span data-ttu-id="88651-233">Filter och funktion.</span><span class="sxs-lookup"><span data-stu-id="88651-233">Filter and Function.</span></span>
<span data-ttu-id="88651-234">Windows PowerShell-funktionerna i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-234">The Windows PowerShell functions in the remote session.</span></span>
- <span data-ttu-id="88651-235">Över.</span><span class="sxs-lookup"><span data-stu-id="88651-235">Script.</span></span>
<span data-ttu-id="88651-236">Skript block i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-236">The script blocks in the remote session.</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88651-237">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="88651-237">-DisableNameChecking</span></span>
<span data-ttu-id="88651-238">Anger att denna cmdlet undertrycker meddelandet som varnar dig när du importerar en cmdlet eller funktion vars namn innehåller ett ej godkänt verb eller ett otillåtet Character.</span><span class="sxs-lookup"><span data-stu-id="88651-238">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="88651-239">Som standard visas följande varnings meddelande när en modul som du importerar exporterar cmdlets eller funktioner som har icke godkända verb i sina namn:</span><span class="sxs-lookup"><span data-stu-id="88651-239">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, the Windows PowerShell displays the following warning message:</span></span>

<span data-ttu-id="88651-240">"Varning! vissa importerade kommando namn innehåller icke godkända verb som kan göra dem mindre synliga.</span><span class="sxs-lookup"><span data-stu-id="88651-240">"WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span>
<span data-ttu-id="88651-241">Använd verbose-parametern för mer information eller Skriv Get-Verb om du vill visa en lista över godkända verb. "</span><span class="sxs-lookup"><span data-stu-id="88651-241">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs."</span></span>

<span data-ttu-id="88651-242">Det här meddelandet är bara en varning.</span><span class="sxs-lookup"><span data-stu-id="88651-242">This message is only a warning.</span></span>
<span data-ttu-id="88651-243">Den kompletta modulen importeras fortfarande, inklusive kommandon som inte överensstämmer.</span><span class="sxs-lookup"><span data-stu-id="88651-243">The complete module is still imported, including the non-conforming commands.</span></span>
<span data-ttu-id="88651-244">Även om meddelandet visas för modulen användare, bör namngivnings problemet åtgärdas av den som skapade modulen.</span><span class="sxs-lookup"><span data-stu-id="88651-244">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88651-245">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="88651-245">-FormatTypeName</span></span>
<span data-ttu-id="88651-246">Anger formateringsregler för de angivna Microsoft .NET Ramverks typerna.</span><span class="sxs-lookup"><span data-stu-id="88651-246">Specifies formatting instructions for the specified Microsoft .NET Framework types.</span></span>
<span data-ttu-id="88651-247">Ange typ namn.</span><span class="sxs-lookup"><span data-stu-id="88651-247">Enter the type names.</span></span>
<span data-ttu-id="88651-248">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="88651-248">Wildcards are permitted.</span></span>

<span data-ttu-id="88651-249">Värdet för den här parametern måste vara namnet på en typ som returneras av ett Get-FormatData-kommando i sessionen som kommandona importeras från.</span><span class="sxs-lookup"><span data-stu-id="88651-249">The value of this parameter must be the name of a type that is returned by a Get-FormatData command in the session from which the commands are being imported.</span></span>
<span data-ttu-id="88651-250">Om du vill hämta alla formaterings data i fjärrsessionen skriver du \*.</span><span class="sxs-lookup"><span data-stu-id="88651-250">To get all of the formatting data in the remote session, type \*.</span></span>

<span data-ttu-id="88651-251">Om kommandot inte inkluderar *commandname* -eller *FormatTypeName* -parametern **importeras-PSSession** importerar formaterings instruktioner för alla .NET Framework typer som returneras av ett **Get-FormatData** -kommando i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-251">If the command does not include either the *CommandName* or *FormatTypeName* parameter, **Import-PSSession** imports formatting instructions for all .NET Framework types returned by a **Get-FormatData** command in the remote session.</span></span>

<span data-ttu-id="88651-252">Om du använder parametern *FormatTypeName* importeras inga kommandon om du inte använder parametern *commandname* .</span><span class="sxs-lookup"><span data-stu-id="88651-252">If you use the *FormatTypeName* parameter, no commands are imported unless you use the *CommandName* parameter.</span></span>

<span data-ttu-id="88651-253">Om du använder parametern *commandname* importeras inte filerna för kommandona om du inte använder parametern *FormatTypeName* .</span><span class="sxs-lookup"><span data-stu-id="88651-253">Similarly, if you use the *CommandName* parameter, the formatting files for the commands are not imported unless you use the *FormatTypeName* parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88651-254">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="88651-254">-FullyQualifiedModule</span></span>
<span data-ttu-id="88651-255">Anger moduler med namn som anges i form av **ModuleSpecification** -objekt (beskrivs i avsnittet anmärkningar i ModuleSpecification- [konstruktorn (hash)](https://msdn.microsoft.com/library/jj136290) i MSDN-biblioteket).</span><span class="sxs-lookup"><span data-stu-id="88651-255">Specifies modules with names that are specified in the form of **ModuleSpecification** objects (described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290) in the MSDN library).</span></span>
<span data-ttu-id="88651-256">*FullyQualifiedModule* -parametern accepterar till exempel ett modulnamn som anges i formatet @ {Modulnamn = "Modulnamn"; ModuleVersion = "version_number"} eller @ {Modulnamn = "Modulnamn"; ModuleVersion = "version_number"; GUID = "GUID"}.</span><span class="sxs-lookup"><span data-stu-id="88651-256">For example, the *FullyQualifiedModule* parameter accepts a module name that is specified in the format @{ModuleName = "modulename"; ModuleVersion = "version_number"} or @{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.</span></span>
<span data-ttu-id="88651-257">**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="88651-257">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="88651-258">Det går inte att ange parametern *FullyQualifiedModule* i samma kommando som en *modul* parameter. de två parametrarna kan inte anges samtidigt.</span><span class="sxs-lookup"><span data-stu-id="88651-258">You cannot specify the *FullyQualifiedModule* parameter in the same command as a *Module* parameter; the two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88651-259">– Modul</span><span class="sxs-lookup"><span data-stu-id="88651-259">-Module</span></span>
<span data-ttu-id="88651-260">Anger och en matris med kommandon i Windows PowerShell snapin-moduler och moduler.</span><span class="sxs-lookup"><span data-stu-id="88651-260">Specifies and array of commands in the Windows PowerShell snap-ins and modules.</span></span>
<span data-ttu-id="88651-261">Ange namnet på snapin-modulen och-modulen.</span><span class="sxs-lookup"><span data-stu-id="88651-261">Enter the snap-in and module names.</span></span>
<span data-ttu-id="88651-262">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="88651-262">Wildcards are not permitted.</span></span>

<span data-ttu-id="88651-263">**Import-PSSession** kan inte importera providrar från en snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="88651-263">**Import-PSSession** cannot import providers from a snap-in.</span></span>

<span data-ttu-id="88651-264">Mer information finns i about_PSSnapins och [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="88651-264">For more information, see about_PSSnapins and [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88651-265">-Prefix</span><span class="sxs-lookup"><span data-stu-id="88651-265">-Prefix</span></span>
<span data-ttu-id="88651-266">Anger ett prefix till substantiven i namnen på importerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="88651-266">Specifies a prefix to the nouns in the names of imported commands.</span></span>

<span data-ttu-id="88651-267">Använd den här parametern för att undvika namn konflikter som kan uppstå när olika kommandon i sessionen har samma namn.</span><span class="sxs-lookup"><span data-stu-id="88651-267">Use this parameter to avoid name conflicts that might occur when different commands in the session have the same name.</span></span>

<span data-ttu-id="88651-268">Om du till exempel anger prefixet Remote och sedan importerar en Get-Date-cmdlet, är cmdleten känd i sessionen som Get-RemoteDate och den förväxlas inte med den ursprungliga cmdleten **Get-date** .</span><span class="sxs-lookup"><span data-stu-id="88651-268">For instance, if you specify the prefix Remote and then import a Get-Date cmdlet, the cmdlet is known in the session as Get-RemoteDate, and it is not confused with the original **Get-Date** cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88651-269">– Session</span><span class="sxs-lookup"><span data-stu-id="88651-269">-Session</span></span>
<span data-ttu-id="88651-270">Anger **PSSession** som cmdletarna importeras från.</span><span class="sxs-lookup"><span data-stu-id="88651-270">Specifies the **PSSession** from which the cmdlets are imported.</span></span>
<span data-ttu-id="88651-271">Ange en variabel som innehåller ett session-objekt eller ett kommando som hämtar ett sessionsobjekt, till exempel ett New-PSSession-eller Get-PSSession-kommando.</span><span class="sxs-lookup"><span data-stu-id="88651-271">Enter a variable that contains a session object or a command that gets a session object, such as a New-PSSession or Get-PSSession command.</span></span>
<span data-ttu-id="88651-272">Du kan bara ange en session.</span><span class="sxs-lookup"><span data-stu-id="88651-272">You can specify only one session.</span></span>
<span data-ttu-id="88651-273">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="88651-273">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88651-274">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="88651-274">CommonParameters</span></span>
<span data-ttu-id="88651-275">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="88651-275">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="88651-276">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="88651-276">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="88651-277">INDATA</span><span class="sxs-lookup"><span data-stu-id="88651-277">INPUTS</span></span>

### <span data-ttu-id="88651-278">Inget</span><span class="sxs-lookup"><span data-stu-id="88651-278">None</span></span>
<span data-ttu-id="88651-279">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="88651-279">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="88651-280">UTDATA</span><span class="sxs-lookup"><span data-stu-id="88651-280">OUTPUTS</span></span>

### <span data-ttu-id="88651-281">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="88651-281">System.Management.Automation.PSModuleInfo</span></span>
<span data-ttu-id="88651-282">**Import-PSSession** returnerar samma modul-objekt som New-Module och Get-Module-cmdletar returnerar.</span><span class="sxs-lookup"><span data-stu-id="88651-282">**Import-PSSession** returns the same module object that New-Module and Get-Module cmdlets return.</span></span>
<span data-ttu-id="88651-283">Den importerade modulen är dock tillfällig och finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-283">However, the imported module is temporary and exists only in the current session.</span></span>
<span data-ttu-id="88651-284">Använd Export-PSSession-cmdleten om du vill skapa en permanent modul på disk.</span><span class="sxs-lookup"><span data-stu-id="88651-284">To create a permanent module on disk, use the Export-PSSession cmdlet.</span></span>

## <span data-ttu-id="88651-285">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="88651-285">NOTES</span></span>

* <span data-ttu-id="88651-286">**Import-PSSession** förlitar sig på infrastrukturen för fjärr kommunikation i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88651-286">**Import-PSSession** relies on the Windows PowerShell remoting infrastructure.</span></span> <span data-ttu-id="88651-287">Om du vill använda denna cmdlet måste datorn konfigureras för WS-Management fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="88651-287">To use this cmdlet, the computer must be configured for WS-Management remoting.</span></span> <span data-ttu-id="88651-288">Mer information finns i about_Remote och about_Remote_Requirements.</span><span class="sxs-lookup"><span data-stu-id="88651-288">For more information, see about_Remote and about_Remote_Requirements.</span></span>
* <span data-ttu-id="88651-289">**Import-PSSession** importerar inte variabler eller Windows PowerShell-providrar.</span><span class="sxs-lookup"><span data-stu-id="88651-289">**Import-PSSession** does not import variables or Windows PowerShell providers.</span></span>
* <span data-ttu-id="88651-290">När du importerar kommandon som har samma namn som kommandon i den aktuella sessionen kan de importerade kommandona dölja alias, funktioner och cmdlets i sessionen och de kan ersätta funktioner och variabler i sessionen.</span><span class="sxs-lookup"><span data-stu-id="88651-290">When you import commands that have the same names as commands in the current session, the imported commands can hide aliases, functions, and cmdlets in the session and they can replace functions and variables in the session.</span></span> <span data-ttu-id="88651-291">Använd parametern *prefix* för att förhindra namn konflikter.</span><span class="sxs-lookup"><span data-stu-id="88651-291">To prevent name conflicts, use the *Prefix* parameter.</span></span> <span data-ttu-id="88651-292">Mer information finns i about_Command_Precedence.</span><span class="sxs-lookup"><span data-stu-id="88651-292">For more information, see about_Command_Precedence.</span></span>
* <span data-ttu-id="88651-293">**Import-PSSession** konverterar alla kommandon till funktioner innan de importeras.</span><span class="sxs-lookup"><span data-stu-id="88651-293">**Import-PSSession** converts all commands into functions before it imports them.</span></span> <span data-ttu-id="88651-294">Det innebär att importerade kommandon fungerar lite annorlunda än om de behåller sin ursprungliga kommando typ.</span><span class="sxs-lookup"><span data-stu-id="88651-294">As a result, imported commands behave a bit differently than they would if they retained their original command type.</span></span> <span data-ttu-id="88651-295">Om du t. ex. importerar en cmdlet från en PSSession och sedan importerar en cmdlet med samma namn från en modul eller snapin-modul, körs den cmdlet som importeras från PSSession alltid som standard eftersom Functions prioriteras över cmdletar.</span><span class="sxs-lookup"><span data-stu-id="88651-295">For example, if you import a cmdlet from a PSSession and then import a cmdlet with the same name from a module or snap-in, the cmdlet that is imported from the PSSession always runs by default because functions take precedence over cmdlets.</span></span> <span data-ttu-id="88651-296">Om du importerar ett alias till en-session som har ett alias med samma namn, används alltid det ursprungliga aliaset, eftersom alias har företräde framför funktioner.</span><span class="sxs-lookup"><span data-stu-id="88651-296">Conversely, if you import an alias into a session that has an alias with the same name, the original alias is always used, because aliases take precedence over functions.</span></span> <span data-ttu-id="88651-297">Mer information finns i about_Command_Precedence.</span><span class="sxs-lookup"><span data-stu-id="88651-297">For more information, see about_Command_Precedence.</span></span>
* <span data-ttu-id="88651-298">**Import-PSSession** använder cmdleten Write-Progress för att visa förloppet för kommandot.</span><span class="sxs-lookup"><span data-stu-id="88651-298">**Import-PSSession** uses the Write-Progress cmdlet to display the progress of the command.</span></span> <span data-ttu-id="88651-299">Du kan se förlopps indikatorn när kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="88651-299">You might see the progress bar while the command is running.</span></span>
* <span data-ttu-id="88651-300">För att hitta de kommandon som ska importeras använder **import-PSSession** cmdleten Invoke-Command för att köra ett Get-Command-kommando i PSSession.</span><span class="sxs-lookup"><span data-stu-id="88651-300">To find the commands to import, **Import-PSSession** uses the Invoke-Command cmdlet to run a Get-Command command in the PSSession.</span></span> <span data-ttu-id="88651-301">Om du vill hämta formateringen för kommandona använder den Get-FormatData-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="88651-301">To get formatting data for the commands, it uses the Get-FormatData cmdlet.</span></span> <span data-ttu-id="88651-302">Du kan se fel meddelanden från dessa cmdletar när du kör kommandot **import-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="88651-302">You might see error messages from these cmdlets when you run an **Import-PSSession** command.</span></span> <span data-ttu-id="88651-303">**Import-PSSession** kan heller inte importera kommandon från en PSSession som inte inkluderar Get-Command-, get-FormatData-, Select-Object-och Get-Help-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="88651-303">Also, **Import-PSSession** cannot import commands from a PSSession that does not include the Get-Command, Get-FormatData, Select-Object, and Get-Help cmdlets.</span></span>
* <span data-ttu-id="88651-304">Importerade kommandon har samma begränsningar som andra fjärrkommandon, inklusive möjligheten att starta ett program med ett användar gränssnitt, t. ex. anteckningar.</span><span class="sxs-lookup"><span data-stu-id="88651-304">Imported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>
* <span data-ttu-id="88651-305">Eftersom Windows PowerShell-profiler inte körs i PSSessions är kommandona som en profil lägger till i en session inte tillgängliga för **import-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="88651-305">Because Windows PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to **Import-PSSession**.</span></span> <span data-ttu-id="88651-306">Om du vill importera kommandon från en profil använder du ett Invoke-Command-kommando för att köra profilen i PSSession manuellt innan du importerar kommandon.</span><span class="sxs-lookup"><span data-stu-id="88651-306">To import commands from a profile, use an Invoke-Command command to run the profile in the PSSession manually before importing commands.</span></span>
* <span data-ttu-id="88651-307">Den temporära modul som **import-PSSession** skapar kan innehålla en formateringsinformation, även om kommandot inte importerar formaterings data.</span><span class="sxs-lookup"><span data-stu-id="88651-307">The temporary module that **Import-PSSession** creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="88651-308">Om kommandot inte importerar dataformaterade data kommer eventuella filer som skapas inte att innehålla formatering.</span><span class="sxs-lookup"><span data-stu-id="88651-308">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>
* <span data-ttu-id="88651-309">För att kunna använda **import-PSSession** , kan körnings principen i den aktuella sessionen inte vara begränsad eller AllSigned, eftersom den temporära modul som **import-PSSession** skapar innehåller osignerade skriptfiler som är förbjudna av dessa principer.</span><span class="sxs-lookup"><span data-stu-id="88651-309">To use **Import-PSSession** , the execution policy in the current session cannot be Restricted or AllSigned, because the temporary module that **Import-PSSession** creates contains unsigned script files that are prohibited by these policies.</span></span> <span data-ttu-id="88651-310">Om du vill använda **import-PSSession** utan att ändra körnings principen för den lokala datorn använder du *omfattnings* parametern för Set-ExecutionPolicy för att ange en mindre begränsande körnings princip för en enda process.</span><span class="sxs-lookup"><span data-stu-id="88651-310">To use **Import-PSSession** without changing the execution policy for the local computer, use the *Scope* parameter of Set-ExecutionPolicy to set a less restrictive execution policy for a single process.</span></span>
* <span data-ttu-id="88651-311">I Windows PowerShell 2,0 innehåller hjälp avsnitten för kommandon som importeras från en annan session inte det prefix som du tilldelar med hjälp av parametern *prefix* .</span><span class="sxs-lookup"><span data-stu-id="88651-311">In Windows PowerShell 2.0, help topics for commands that are imported from another session do not include the prefix that you assign by using the *Prefix* parameter.</span></span> <span data-ttu-id="88651-312">Om du vill ha hjälp med ett importerat kommando i Windows PowerShell 2,0 använder du det ursprungliga kommando namnet (icke-förfixet).</span><span class="sxs-lookup"><span data-stu-id="88651-312">To get help for an imported command in Windows PowerShell 2.0, use the original (non-prefixed) command name.</span></span>

## <span data-ttu-id="88651-313">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="88651-313">RELATED LINKS</span></span>

[<span data-ttu-id="88651-314">Exportera – PSSession</span><span class="sxs-lookup"><span data-stu-id="88651-314">Export-PSSession</span></span>](Export-PSSession.md)
