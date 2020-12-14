---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: 1a87783f9d12d852d3a6809e9457a55ad6e7be50
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708618"
---
# <span data-ttu-id="4d61c-102">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="4d61c-102">Import-PSSession</span></span>

## <span data-ttu-id="4d61c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4d61c-103">SYNOPSIS</span></span>
<span data-ttu-id="4d61c-104">Importerar kommandon från en annan session till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-104">Imports commands from another session into the current session.</span></span>

## <span data-ttu-id="4d61c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4d61c-105">SYNTAX</span></span>

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## <span data-ttu-id="4d61c-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4d61c-106">DESCRIPTION</span></span>

<span data-ttu-id="4d61c-107">`Import-PSSession`Cmdleten importerar kommandon, till exempel cmdlets, Functions och alias, från en PSSession på en lokal eller fjärran sluten dator till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-107">The `Import-PSSession` cmdlet imports commands , such as cmdlets, functions, and aliases, from a PSSession on a local or remote computer into the current session.</span></span> <span data-ttu-id="4d61c-108">Du kan importera alla kommandon som `Get-Command` cmdleten kan hitta i PSSession.</span><span class="sxs-lookup"><span data-stu-id="4d61c-108">You can import any command that the `Get-Command` cmdlet can find in the PSSession.</span></span>

<span data-ttu-id="4d61c-109">Använd ett `Import-PSSession` kommando för att importera kommandon från ett anpassat gränssnitt, till exempel ett Microsoft Exchange Server-gränssnitt eller från en-session som innehåller Windows PowerShell-moduler och snapin-moduler eller andra element som inte finns i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-109">Use an `Import-PSSession` command to import commands from a customized shell, such as a Microsoft Exchange Server shell, or from a session that includes Windows PowerShell modules and snap-ins or other elements that are not in the current session.</span></span>

<span data-ttu-id="4d61c-110">Om du vill importera kommandon använder du först `New-PSSession` cmdleten för att skapa en PSSession.</span><span class="sxs-lookup"><span data-stu-id="4d61c-110">To import commands, first use the `New-PSSession` cmdlet to create a PSSession.</span></span> <span data-ttu-id="4d61c-111">Använd sedan `Import-PSSession` cmdleten för att importera kommandona.</span><span class="sxs-lookup"><span data-stu-id="4d61c-111">Then, use the `Import-PSSession` cmdlet to import the commands.</span></span> <span data-ttu-id="4d61c-112">Som standard `Import-PSSession` importerar alla kommandon utom kommandon som har samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-112">By default, `Import-PSSession` imports all commands except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="4d61c-113">Om du vill importera alla kommandon använder du parametern **AllowClobber** .</span><span class="sxs-lookup"><span data-stu-id="4d61c-113">To import all the commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="4d61c-114">Du kan använda importerade kommandon precis som med alla kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-114">You can use imported commands just as you would use any command in the session.</span></span> <span data-ttu-id="4d61c-115">När du använder ett importerat kommando körs den importerade delen av kommandot implicit i den session som det importerades från.</span><span class="sxs-lookup"><span data-stu-id="4d61c-115">When you use an imported command, the imported part of the command runs implicitly in the session from which it was imported.</span></span> <span data-ttu-id="4d61c-116">Fjärråtgärder hanteras dock helt av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d61c-116">However, the remote operations are handled entirely by Windows PowerShell.</span></span> <span data-ttu-id="4d61c-117">Du behöver inte ens vara medveten om dem, förutom att du måste hålla anslutningen till den andra sessionen (PSSession) öppen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-117">You need not even be aware of them, except that you must keep the connection to the other session (PSSession) open.</span></span> <span data-ttu-id="4d61c-118">Om du stänger den är de importerade kommandona inte längre tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="4d61c-118">If you close it, the imported commands are no longer available.</span></span>

<span data-ttu-id="4d61c-119">Eftersom importerade kommandon kan ta längre tid att köra än lokala kommandon, `Import-PSSession` lägger till en **AsJob** -parameter till alla importerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="4d61c-119">Because imported commands might take longer to run than local commands, `Import-PSSession` adds an **AsJob** parameter to every imported command.</span></span> <span data-ttu-id="4d61c-120">Med den här parametern kan du köra kommandot som ett bakgrunds jobb i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d61c-120">This parameter allows you to run the command as a Windows PowerShell background job.</span></span> <span data-ttu-id="4d61c-121">Mer information finns i artikeln [om jobb](../Microsoft.PowerShell.Core/about/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="4d61c-121">For more information, see [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md).</span></span>

<span data-ttu-id="4d61c-122">När du använder `Import-PSSession` lägger Windows PowerShell till de importerade kommandona i en tillfällig modul som bara finns i din session och returnerar ett objekt som representerar modulen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-122">When you use `Import-PSSession`, Windows PowerShell adds the imported commands to a temporary module that exists only in your session and returns an object that represents the module.</span></span> <span data-ttu-id="4d61c-123">Använd cmdleten för att skapa en beständig modul som du kan använda i framtida sessioner `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="4d61c-123">To create a persistent module that you can use in future sessions, use the `Export-PSSession` cmdlet.</span></span>

<span data-ttu-id="4d61c-124">`Import-PSSession`Cmdleten använder funktionen implicit fjärr kommunikation i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d61c-124">The `Import-PSSession` cmdlet uses the implicit remoting feature of Windows PowerShell.</span></span> <span data-ttu-id="4d61c-125">När du importerar kommandon till den aktuella sessionen körs de implicit i den ursprungliga sessionen eller i en liknande session på den ursprungliga datorn.</span><span class="sxs-lookup"><span data-stu-id="4d61c-125">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

<span data-ttu-id="4d61c-126">Från och med Windows PowerShell 3,0 kan du använda `Import-Module` cmdleten för att importera moduler från en fjärrsession till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-126">Beginning in Windows PowerShell 3.0, you can use the `Import-Module` cmdlet to import modules from a remote session into the current session.</span></span> <span data-ttu-id="4d61c-127">Den här funktionen använder implicit fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="4d61c-127">This feature uses implicit remoting.</span></span> <span data-ttu-id="4d61c-128">Det motsvarar att använda `Import-PSSession` för att importera valda moduler från en fjärrsession till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-128">It is equivalent to using `Import-PSSession` to import selected modules from a remote session into the current session.</span></span>

## <span data-ttu-id="4d61c-129">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4d61c-129">EXAMPLES</span></span>

### <span data-ttu-id="4d61c-130">Exempel 1: importera alla kommandon från en PSSession</span><span class="sxs-lookup"><span data-stu-id="4d61c-130">Example 1: Import all commands from a PSSession</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

<span data-ttu-id="4d61c-131">Det här kommandot importerar alla kommandon från en PSSession på Server01-datorn till den aktuella sessionen, förutom kommandon som har samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-131">This command imports all commands from a PSSession on the Server01 computer into the current session, except for commands that have the same names as commands in the current session.</span></span>

<span data-ttu-id="4d61c-132">Eftersom det här kommandot inte använder **commandname** -parametern importeras även all formatering som krävs för de importerade kommandona.</span><span class="sxs-lookup"><span data-stu-id="4d61c-132">Because this command does not use the **CommandName** parameter, it also imports all of the formatting data required for the imported commands.</span></span>

### <span data-ttu-id="4d61c-133">Exempel 2: importera kommandon som slutar med en angiven sträng</span><span class="sxs-lookup"><span data-stu-id="4d61c-133">Example 2: Import commands that end with a specific string</span></span>

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

<span data-ttu-id="4d61c-134">Kommandona importerar kommandona med namn som slutar med "-test" från en PSSession till den lokala sessionen, och sedan visar de hur man använder en importerad cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4d61c-134">These commands import the commands with names that end in "-test" from a PSSession into the local session, and then they show how to use an imported cmdlet.</span></span>

<span data-ttu-id="4d61c-135">Det första kommandot använder `New-PSSession` cmdleten för att skapa en PSSession.</span><span class="sxs-lookup"><span data-stu-id="4d61c-135">The first command uses the `New-PSSession` cmdlet to create a PSSession.</span></span> <span data-ttu-id="4d61c-136">Den sparar PSSession i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4d61c-136">It saves the PSSession in the `$S` variable.</span></span>

<span data-ttu-id="4d61c-137">Det andra kommandot använder `Import-PSSession` cmdleten för att importera kommandon från PSSession i `$S` till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-137">The second command uses the `Import-PSSession` cmdlet to import commands from the PSSession in `$S` into the current session.</span></span> <span data-ttu-id="4d61c-138">Parametern **commandname** används för att ange kommandon med parametern test Substantiv och parametern **FormatTypeName** för att importera formateringsinformationen för test kommandona.</span><span class="sxs-lookup"><span data-stu-id="4d61c-138">It uses the **CommandName** parameter to specify commands with the Test noun and the **FormatTypeName** parameter to import the formatting data for the Test commands.</span></span>

<span data-ttu-id="4d61c-139">De tredje och fjärde kommandona använder de importerade kommandona i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-139">The third and fourth commands use the imported commands in the current session.</span></span> <span data-ttu-id="4d61c-140">Eftersom importerade kommandon faktiskt läggs till i den aktuella sessionen använder du den lokala syntaxen för att köra dem.</span><span class="sxs-lookup"><span data-stu-id="4d61c-140">Because imported commands are actually added to the current session, you use the local syntax to run them.</span></span> <span data-ttu-id="4d61c-141">Du behöver inte använda `Invoke-Command` cmdleten för att köra ett importerat kommando.</span><span class="sxs-lookup"><span data-stu-id="4d61c-141">You do not need to use the `Invoke-Command` cmdlet to run an imported command.</span></span>

### <span data-ttu-id="4d61c-142">Exempel 3: importera cmdletar från en PSSession</span><span class="sxs-lookup"><span data-stu-id="4d61c-142">Example 3: Import cmdlets from a PSSession</span></span>

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

<span data-ttu-id="4d61c-143">Det här exemplet visar att du kan använda importerade cmdlets på samma sätt som du använder lokala cmdlets.</span><span class="sxs-lookup"><span data-stu-id="4d61c-143">This example shows that you can use imported cmdlets just as you would use local cmdlets.</span></span>

<span data-ttu-id="4d61c-144">Kommandona importerar `New-Test` `Get-Test` cmdletarna och från en PSSession på Server01-datorn och `Set-Test` cmdleten från en PSSession på Server02-datorn.</span><span class="sxs-lookup"><span data-stu-id="4d61c-144">These commands import the `New-Test` and `Get-Test` cmdlets from a PSSession on the Server01 computer and the `Set-Test` cmdlet from a PSSession on the Server02 computer.</span></span>

<span data-ttu-id="4d61c-145">Även om cmdletarna har importer ATS från olika PSSessions kan du skicka ett objekt från en cmdlet till en annan utan fel.</span><span class="sxs-lookup"><span data-stu-id="4d61c-145">Even though the cmdlets were imported from different PSSessions, you can pipe an object from one cmdlet to another without error.</span></span>

### <span data-ttu-id="4d61c-146">Exempel 4: kör ett importerat kommando som bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="4d61c-146">Example 4: Run an imported command as a background job</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

<span data-ttu-id="4d61c-147">Det här exemplet visar hur du kör ett importerat kommando som bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="4d61c-147">This example shows how to run an imported command as a background job.</span></span>

<span data-ttu-id="4d61c-148">Eftersom importerade kommandon kan ta längre tid att köra än lokala kommandon, `Import-PSSession` lägger till en **AsJob** -parameter till alla importerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="4d61c-148">Because imported commands might take longer to run than local commands, `Import-PSSession` adds an **AsJob** parameter to every imported command.</span></span> <span data-ttu-id="4d61c-149">Med parametern **AsJob** kan du köra kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="4d61c-149">The **AsJob** parameter lets you run the command as a background job.</span></span>

<span data-ttu-id="4d61c-150">Det första kommandot skapar en PSSession på Server01-datorn och sparar PSSession-objektet i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4d61c-150">The first command creates a PSSession on the Server01 computer and saves the PSSession object in the `$S` variable.</span></span>

<span data-ttu-id="4d61c-151">Det andra kommandot använder `Import-PSSession` för att importera test-cmdletarna från PSSession i `$S` till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-151">The second command uses `Import-PSSession` to import the Test cmdlets from the PSSession in `$S` into the current session.</span></span>

<span data-ttu-id="4d61c-152">Det tredje kommandot använder parametern **AsJob** för den importerade `New-Test` cmdleten för att köra ett `New-Test` kommando som bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="4d61c-152">The third command uses the **AsJob** parameter of the imported `New-Test` cmdlet to run a `New-Test` command as a background job.</span></span> <span data-ttu-id="4d61c-153">Kommandot sparar jobbobjektet som `New-Test` returneras i `$batch` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4d61c-153">The command saves the job object that `New-Test` returns in the `$batch` variable.</span></span>

<span data-ttu-id="4d61c-154">Det fjärde kommandot använder `Receive-Job` cmdleten för att hämta resultatet av jobbet i `$batch` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4d61c-154">The fourth command uses the `Receive-Job` cmdlet to get the results of the job in the `$batch` variable.</span></span>

### <span data-ttu-id="4d61c-155">Exempel 5: importera cmdlets och Functions från en Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="4d61c-155">Example 5: Import cmdlets and functions from a Windows PowerShell module</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

<span data-ttu-id="4d61c-156">Det här exemplet visar hur du importerar cmdlets och Functions från en Windows PowerShell-modul på en fjärrdator till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-156">This example shows how to import the cmdlets and functions from a Windows PowerShell module on a remote computer into the current session.</span></span>

<span data-ttu-id="4d61c-157">Det första kommandot skapar en PSSession på Server01-datorn och sparar den i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4d61c-157">The first command creates a PSSession on the Server01 computer and saves it in the `$S` variable.</span></span>

<span data-ttu-id="4d61c-158">Det andra kommandot använder `Invoke-Command` cmdleten för att köra ett `Import-Module` kommando i PSSession i `$S` .</span><span class="sxs-lookup"><span data-stu-id="4d61c-158">The second command uses the `Invoke-Command` cmdlet to run an `Import-Module` command in the PSSession in `$S`.</span></span>

<span data-ttu-id="4d61c-159">Normalt läggs modulen till i alla sessioner med ett `Import-Module` kommando i en Windows PowerShell-profil, men profiler körs inte i PSSessions.</span><span class="sxs-lookup"><span data-stu-id="4d61c-159">Typically, the module would be added to all sessions by an `Import-Module` command in a Windows PowerShell profile, but profiles are not run in PSSessions.</span></span>

<span data-ttu-id="4d61c-160">Det tredje kommandot använder **modulen modul** för `Import-PSSession` för att importera cmdlets och Functions i modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-160">The third command uses the **Module** parameter of `Import-PSSession` to import the cmdlets and functions in the module into the current session.</span></span>

### <span data-ttu-id="4d61c-161">Exempel 6: skapa en modul i en temporär fil</span><span class="sxs-lookup"><span data-stu-id="4d61c-161">Example 6: Create a module in a temporary file</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="4d61c-162">Det här exemplet visar att `Import-PSSession` skapar en modul i en temporär fil på disk.</span><span class="sxs-lookup"><span data-stu-id="4d61c-162">This example shows that `Import-PSSession` creates a module in a temporary file on disk.</span></span> <span data-ttu-id="4d61c-163">Det visar också att alla kommandon konverteras till funktioner innan de importeras till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-163">It also shows that all commands are converted into functions before they are imported into the current session.</span></span>

<span data-ttu-id="4d61c-164">Kommandot använder `Import-PSSession` cmdleten för att importera en `Get-Date` cmdlet och en SearchHelp-funktion till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-164">The command uses the `Import-PSSession` cmdlet to import a `Get-Date` cmdlet and a SearchHelp function into the current session.</span></span>

<span data-ttu-id="4d61c-165">`Import-PSSession`Cmdleten returnerar ett **PSModuleInfo** -objekt som representerar den temporära modulen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-165">The `Import-PSSession` cmdlet returns a **PSModuleInfo** object that represents the temporary module.</span></span> <span data-ttu-id="4d61c-166">Värdet för egenskapen **Path** visar att `Import-PSSession` en psm1-fil har skapats på en tillfällig plats.</span><span class="sxs-lookup"><span data-stu-id="4d61c-166">The value of the **Path** property shows that `Import-PSSession` created a script module (.psm1) file in a temporary location.</span></span> <span data-ttu-id="4d61c-167">Egenskapen **ExportedFunctions** visar att `Get-Date` cmdleten och funktionen SearchHelp både har importer ATS som funktioner.</span><span class="sxs-lookup"><span data-stu-id="4d61c-167">The **ExportedFunctions** property shows that the `Get-Date` cmdlet and the SearchHelp function were both imported as functions.</span></span>

### <span data-ttu-id="4d61c-168">Exempel 7: köra ett kommando som är dolt av ett importerat kommando</span><span class="sxs-lookup"><span data-stu-id="4d61c-168">Example 7: Run a command that is hidden by an imported command</span></span>

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

<span data-ttu-id="4d61c-169">Det här exemplet visar hur du kör ett kommando som är dolt av ett importerat kommando.</span><span class="sxs-lookup"><span data-stu-id="4d61c-169">This example shows how to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="4d61c-170">Det första kommandot importerar en `Get-Date` cmdlet från PSSession i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4d61c-170">The first command imports a `Get-Date` cmdlet from the PSSession in the `$S` variable.</span></span> <span data-ttu-id="4d61c-171">Eftersom den aktuella sessionen innehåller en `Get-Date` cmdlet krävs **AllowClobber** -parametern i kommandot.</span><span class="sxs-lookup"><span data-stu-id="4d61c-171">Because the current session includes a `Get-Date` cmdlet, the **AllowClobber** parameter is required in the command.</span></span>

<span data-ttu-id="4d61c-172">Det andra kommandot använder parametern **all** för `Get-Command` cmdlet: en för att hämta alla `Get-Date` kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-172">The second command uses the **All** parameter of the `Get-Command` cmdlet to get all `Get-Date` commands in the current session.</span></span> <span data-ttu-id="4d61c-173">Utdata visar att sessionen innehåller den ursprungliga `Get-Date` cmdleten och en `Get-Date` funktion.</span><span class="sxs-lookup"><span data-stu-id="4d61c-173">The output shows that the session includes the original `Get-Date` cmdlet and a `Get-Date` function.</span></span> <span data-ttu-id="4d61c-174">`Get-Date`Funktionen kör den importerade `Get-Date` cmdleten i PSSession i `$S` .</span><span class="sxs-lookup"><span data-stu-id="4d61c-174">The `Get-Date` function runs the imported `Get-Date` cmdlet in the PSSession in `$S`.</span></span>

<span data-ttu-id="4d61c-175">Det tredje kommandot kör ett `Get-Date` kommando.</span><span class="sxs-lookup"><span data-stu-id="4d61c-175">The third command runs a `Get-Date` command.</span></span> <span data-ttu-id="4d61c-176">Eftersom funktioner prioriteras över cmdletar kör Windows PowerShell den importerade `Get-Date` funktionen, som returnerar ett Juliansk-datum.</span><span class="sxs-lookup"><span data-stu-id="4d61c-176">Because functions take precedence over cmdlets, Windows PowerShell runs the imported `Get-Date` function, which returns a Julian date.</span></span>

<span data-ttu-id="4d61c-177">De fjärde och femte kommandona visar hur du använder ett kvalificerat namn för att köra ett kommando som är dolt av ett importerat kommando.</span><span class="sxs-lookup"><span data-stu-id="4d61c-177">The fourth and fifth commands show how to use a qualified name to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="4d61c-178">Det fjärde kommandot hämtar namnet på Windows PowerShell-snapin-modulen som lade till den ursprungliga `Get-Date` cmdleten i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-178">The fourth command gets the name of the Windows PowerShell snap-in that added the original `Get-Date` cmdlet to the current session.</span></span>

<span data-ttu-id="4d61c-179">Det femte kommandot använder det Snap-i-kvalificerade namnet för `Get-Date` cmdleten för att köra ett `Get-Date` kommando.</span><span class="sxs-lookup"><span data-stu-id="4d61c-179">The fifth command uses the snap-in-qualified name of the `Get-Date` cmdlet to run a `Get-Date` command.</span></span>

<span data-ttu-id="4d61c-180">Mer information om kommando prioritet och dolda kommandon finns [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="4d61c-180">For more information about command precedence and hidden commands, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="4d61c-181">Exempel 8: importera kommandon som har en angiven sträng i sina namn</span><span class="sxs-lookup"><span data-stu-id="4d61c-181">Example 8: Import commands that have a specific string in their names</span></span>

```
PS C:\> Import-PSSession -Session $S -CommandName **Item** -AllowClobber
```

<span data-ttu-id="4d61c-182">Det här kommandot importerar kommandon vars namn innehåller objekt från PSSession i `$S` .</span><span class="sxs-lookup"><span data-stu-id="4d61c-182">This command imports commands whose names include Item from the PSSession in `$S`.</span></span> <span data-ttu-id="4d61c-183">Eftersom kommandot innehåller parametern **commandname** men inte parametern **FormatTypeData** , importeras bara kommandot.</span><span class="sxs-lookup"><span data-stu-id="4d61c-183">Because the command includes the **CommandName** parameter but not the **FormatTypeData** parameter, only the command is imported.</span></span>

<span data-ttu-id="4d61c-184">Använd det här kommandot när du använder `Import-PSSession` för att köra ett kommando på en fjärrdator och du redan har format data för kommandot i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-184">Use this command when you are using `Import-PSSession` to run a command on a remote computer and you already have the formatting data for the command in the current session.</span></span>

### <span data-ttu-id="4d61c-185">Exempel 9: Använd parametern module för att identifiera vilka kommandon som har importer ATS till sessionen</span><span class="sxs-lookup"><span data-stu-id="4d61c-185">Example 9: Use the Module parameter to discover which commands were imported into the session</span></span>

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

<span data-ttu-id="4d61c-186">Det här kommandot visar hur du använder **modulen modul** för `Get-Command` för att ta reda på vilka kommandon som har importer ATS till sessionen med ett `Import-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="4d61c-186">This command shows how to use the **Module** parameter of `Get-Command` to find out which commands were imported into the session by an `Import-PSSession` command.</span></span>

<span data-ttu-id="4d61c-187">Det första kommandot använder `Import-PSSession` cmdleten för att importera kommandon vars namn innehåller "bitar" från PSSession i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4d61c-187">The first command uses the `Import-PSSession` cmdlet to import commands whose names include "bits" from the PSSession in the `$S` variable.</span></span> <span data-ttu-id="4d61c-188">`Import-PSSession`Kommandot returnerar en tillfällig modul och kommandot sparar modulen i `$m` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4d61c-188">The `Import-PSSession` command returns a temporary module, and the command saves the module in the `$m` variable.</span></span>

<span data-ttu-id="4d61c-189">Det andra kommandot använder `Get-Command` cmdleten för att hämta de kommandon som exporteras av modulen i `$M` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4d61c-189">The second command uses the `Get-Command` cmdlet to get the commands that are exported by the module in the `$M` variable.</span></span>

<span data-ttu-id="4d61c-190">Parametern **module** använder ett sträng värde, vilket är utformat för modulnamnet.</span><span class="sxs-lookup"><span data-stu-id="4d61c-190">The **Module** parameter takes a string value, which is designed for the module name.</span></span> <span data-ttu-id="4d61c-191">Men när du skickar ett modul-objekt använder Windows PowerShell metoden **toString** i objektet module, som returnerar modulnamnet.</span><span class="sxs-lookup"><span data-stu-id="4d61c-191">However, when you submit a module object, Windows PowerShell uses the **ToString** method on the module object, which returns the module name.</span></span>

<span data-ttu-id="4d61c-192">`Get-Command`Kommandot motsvarar `Get-Command $M.Name` ".</span><span class="sxs-lookup"><span data-stu-id="4d61c-192">The `Get-Command` command is the equivalent of `Get-Command $M.Name`".</span></span>

## <span data-ttu-id="4d61c-193">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4d61c-193">PARAMETERS</span></span>

### <span data-ttu-id="4d61c-194">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="4d61c-194">-AllowClobber</span></span>

<span data-ttu-id="4d61c-195">Anger att denna cmdlet importerar de angivna kommandona, även om de har samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-195">Indicates that this cmdlet imports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="4d61c-196">Om du importerar ett kommando med samma namn som ett kommando i den aktuella sessionen, döljer det importerade kommandot eller ersätter de ursprungliga kommandona.</span><span class="sxs-lookup"><span data-stu-id="4d61c-196">If you import a command with the same name as a command in the current session, the imported command hides or replaces the original commands.</span></span> <span data-ttu-id="4d61c-197">Mer information finns i [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="4d61c-197">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="4d61c-198">Som standard `Import-PSSession` importerar inte kommandon som har samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-198">By default, `Import-PSSession` does not import commands that have the same name as commands in the current session.</span></span>

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

### <span data-ttu-id="4d61c-199">– Argument List</span><span class="sxs-lookup"><span data-stu-id="4d61c-199">-ArgumentList</span></span>

<span data-ttu-id="4d61c-200">Anger en matris med kommandon som resulterar från att använda de angivna argumenten (parameter värden).</span><span class="sxs-lookup"><span data-stu-id="4d61c-200">Specifies an array of commands that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="4d61c-201">För att till exempel importera `Get-Item` kommandots variant i certifikatet (cert:) enhet i PSSession i `$S` skriver du `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .</span><span class="sxs-lookup"><span data-stu-id="4d61c-201">For instance, to import the variant of the `Get-Item` command in the certificate (Cert:) drive in the PSSession in `$S`, type `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

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

### <span data-ttu-id="4d61c-202">– Certifikat</span><span class="sxs-lookup"><span data-stu-id="4d61c-202">-Certificate</span></span>

<span data-ttu-id="4d61c-203">Anger det klient certifikat som används för att signera format-filer (\* .Format.ps1XML) eller psm1 (.) i den temporära modul som `Import-PSSession` skapas.</span><span class="sxs-lookup"><span data-stu-id="4d61c-203">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the temporary module that `Import-PSSession` creates.</span></span>

<span data-ttu-id="4d61c-204">Ange en variabel som innehåller ett certifikat eller ett kommando eller uttryck som hämtar certifikatet.</span><span class="sxs-lookup"><span data-stu-id="4d61c-204">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="4d61c-205">Om du vill söka efter ett certifikat använder du `Get-PfxCertificate` cmdleten eller använder `Get-ChildItem` cmdleten i certifikatet (cert:) kombinationsenhet.</span><span class="sxs-lookup"><span data-stu-id="4d61c-205">To find a certificate, use the `Get-PfxCertificate` cmdlet or use the `Get-ChildItem` cmdlet in the Certificate (Cert:) drive.</span></span> <span data-ttu-id="4d61c-206">Om certifikatet inte är giltigt eller inte har tillräcklig behörighet, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="4d61c-206">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="4d61c-207">– CommandName</span><span class="sxs-lookup"><span data-stu-id="4d61c-207">-CommandName</span></span>

<span data-ttu-id="4d61c-208">Anger kommandon med angivna namn eller namn mönster.</span><span class="sxs-lookup"><span data-stu-id="4d61c-208">Specifies commands with the specified names or name patterns.</span></span> <span data-ttu-id="4d61c-209">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4d61c-209">Wildcards are permitted.</span></span> <span data-ttu-id="4d61c-210">Använd **commandname** eller dess alias, **namn**.</span><span class="sxs-lookup"><span data-stu-id="4d61c-210">Use **CommandName** or its alias, **Name**.</span></span>

<span data-ttu-id="4d61c-211">Som standard `Import-PSSession` importerar alla kommandon från sessionen, förutom kommandon som har samma namn som kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-211">By default, `Import-PSSession` imports all commands from the session, except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="4d61c-212">Detta förhindrar att importerade kommandon döljer eller ersätter kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-212">This prevents imported commands from hiding or replacing commands in the session.</span></span> <span data-ttu-id="4d61c-213">Om du vill importera alla kommandon, även de som döljer eller ersätter andra kommandon, använder du parametern **AllowClobber** .</span><span class="sxs-lookup"><span data-stu-id="4d61c-213">To import all commands, even those that hide or replace other commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="4d61c-214">Om du använder parametern **commandname** importeras inte formateringsattribut för kommandona om du inte använder parametern **FormatTypeName** .</span><span class="sxs-lookup"><span data-stu-id="4d61c-214">If you use the **CommandName** parameter, the formatting files for the commands are not imported unless you use the **FormatTypeName** parameter.</span></span> <span data-ttu-id="4d61c-215">På liknande sätt importeras inga kommandon om du använder parametern **FormatTypeName** , om du inte använder parametern **commandname** .</span><span class="sxs-lookup"><span data-stu-id="4d61c-215">Similarly, if you use the **FormatTypeName** parameter, no commands are imported unless you use the **CommandName** parameter.</span></span>

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

### <span data-ttu-id="4d61c-216">-CommandType</span><span class="sxs-lookup"><span data-stu-id="4d61c-216">-CommandType</span></span>

<span data-ttu-id="4d61c-217">Anger typ av kommando objekt.</span><span class="sxs-lookup"><span data-stu-id="4d61c-217">Specifies the type of command objects.</span></span> <span data-ttu-id="4d61c-218">Standardvärdet är cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4d61c-218">The default value is Cmdlet.</span></span> <span data-ttu-id="4d61c-219">Använd **CommandType** eller dess alias och **Skriv**.</span><span class="sxs-lookup"><span data-stu-id="4d61c-219">Use **CommandType** or its alias, **Type**.</span></span> <span data-ttu-id="4d61c-220">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="4d61c-220">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4d61c-221">Aliasuppsättning.</span><span class="sxs-lookup"><span data-stu-id="4d61c-221">Alias.</span></span> <span data-ttu-id="4d61c-222">Windows PowerShell-alias i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-222">The Windows PowerShell aliases in the remote session.</span></span>
- <span data-ttu-id="4d61c-223">Vissa.</span><span class="sxs-lookup"><span data-stu-id="4d61c-223">All.</span></span> <span data-ttu-id="4d61c-224">Cmdlets och Functions i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-224">The cmdlets and functions in the remote session.</span></span>
- <span data-ttu-id="4d61c-225">Applicering.</span><span class="sxs-lookup"><span data-stu-id="4d61c-225">Application.</span></span> <span data-ttu-id="4d61c-226">Alla filer utom Windows-PowerShell filer i Sök vägarna som anges i miljövariabeln PATH ( `$env:path` ) i fjärrsessionen, inklusive. txt-,. exe-och. dll-filer.</span><span class="sxs-lookup"><span data-stu-id="4d61c-226">All the files other than Windows-PowerShell files in the paths that are listed in the Path environment variable (`$env:path`) in the remote session, including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="4d61c-227">Kommandon.</span><span class="sxs-lookup"><span data-stu-id="4d61c-227">Cmdlet.</span></span> <span data-ttu-id="4d61c-228">Cmdletarna i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-228">The cmdlets in the remote session.</span></span> <span data-ttu-id="4d61c-229">"Cmdlet" är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="4d61c-229">"Cmdlet" is the default.</span></span>
- <span data-ttu-id="4d61c-230">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="4d61c-230">ExternalScript.</span></span> <span data-ttu-id="4d61c-231">. Ps1-filerna i Sök vägarna som anges i miljövariabeln PATH ( `$env:path` ) i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-231">The .ps1 files in the paths listed in the Path environment variable (`$env:path`) in the remote session.</span></span>
- <span data-ttu-id="4d61c-232">Filter och funktion.</span><span class="sxs-lookup"><span data-stu-id="4d61c-232">Filter and Function.</span></span> <span data-ttu-id="4d61c-233">Windows PowerShell-funktionerna i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-233">The Windows PowerShell functions in the remote session.</span></span>
- <span data-ttu-id="4d61c-234">Över.</span><span class="sxs-lookup"><span data-stu-id="4d61c-234">Script.</span></span> <span data-ttu-id="4d61c-235">Skript block i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-235">The script blocks in the remote session.</span></span>

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

### <span data-ttu-id="4d61c-236">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="4d61c-236">-DisableNameChecking</span></span>

<span data-ttu-id="4d61c-237">Anger att denna cmdlet undertrycker meddelandet som varnar dig när du importerar en cmdlet eller funktion vars namn innehåller ett ej godkänt verb eller ett otillåtet Character.</span><span class="sxs-lookup"><span data-stu-id="4d61c-237">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="4d61c-238">Som standard visas följande varnings meddelande när en modul som du importerar exporterar cmdlets eller funktioner som har icke godkända verb i sina namn:</span><span class="sxs-lookup"><span data-stu-id="4d61c-238">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, the Windows PowerShell displays the following warning message:</span></span>

<span data-ttu-id="4d61c-239">"Varning! vissa importerade kommando namn innehåller icke godkända verb som kan göra dem mindre synliga.</span><span class="sxs-lookup"><span data-stu-id="4d61c-239">"WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="4d61c-240">Använd verbose-parametern för mer information eller Skriv `Get-Verb` om du vill visa en lista över godkända verb. "</span><span class="sxs-lookup"><span data-stu-id="4d61c-240">Use the Verbose parameter for more detail or type `Get-Verb` to see the list of approved verbs."</span></span>

<span data-ttu-id="4d61c-241">Det här meddelandet är bara en varning.</span><span class="sxs-lookup"><span data-stu-id="4d61c-241">This message is only a warning.</span></span> <span data-ttu-id="4d61c-242">Den kompletta modulen importeras fortfarande, inklusive kommandon som inte överensstämmer.</span><span class="sxs-lookup"><span data-stu-id="4d61c-242">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="4d61c-243">Även om meddelandet visas för modulen användare, bör namngivnings problemet åtgärdas av den som skapade modulen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-243">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

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

### <span data-ttu-id="4d61c-244">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="4d61c-244">-FormatTypeName</span></span>

<span data-ttu-id="4d61c-245">Anger formateringsregler för de angivna Microsoft .NET Ramverks typerna.</span><span class="sxs-lookup"><span data-stu-id="4d61c-245">Specifies formatting instructions for the specified Microsoft .NET Framework types.</span></span>
<span data-ttu-id="4d61c-246">Ange typ namn.</span><span class="sxs-lookup"><span data-stu-id="4d61c-246">Enter the type names.</span></span>
<span data-ttu-id="4d61c-247">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4d61c-247">Wildcards are permitted.</span></span>

<span data-ttu-id="4d61c-248">Värdet för den här parametern måste vara namnet på en typ som returneras av ett `Get-FormatData` kommando i den session som kommandona importeras från.</span><span class="sxs-lookup"><span data-stu-id="4d61c-248">The value of this parameter must be the name of a type that is returned by a `Get-FormatData` command in the session from which the commands are being imported.</span></span> <span data-ttu-id="4d61c-249">Om du vill hämta alla formaterings data i fjärrsessionen skriver du `*` .</span><span class="sxs-lookup"><span data-stu-id="4d61c-249">To get all of the formatting data in the remote session, type `*`.</span></span>

<span data-ttu-id="4d61c-250">Om kommandot inte innehåller någon av **commandname** -eller **FormatTypeName** -parametern `Import-PSSession` importeras instruktioner för alla .NET Framework typer som returneras av ett `Get-FormatData` kommando i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-250">If the command does not include either the **CommandName** or **FormatTypeName** parameter, `Import-PSSession` imports formatting instructions for all .NET Framework types returned by a `Get-FormatData` command in the remote session.</span></span>

<span data-ttu-id="4d61c-251">Om du använder parametern **FormatTypeName** importeras inga kommandon om du inte använder parametern **commandname** .</span><span class="sxs-lookup"><span data-stu-id="4d61c-251">If you use the **FormatTypeName** parameter, no commands are imported unless you use the **CommandName** parameter.</span></span>

<span data-ttu-id="4d61c-252">Om du använder parametern **commandname** importeras inte filerna för kommandona om du inte använder parametern **FormatTypeName** .</span><span class="sxs-lookup"><span data-stu-id="4d61c-252">Similarly, if you use the **CommandName** parameter, the formatting files for the commands are not imported unless you use the **FormatTypeName** parameter.</span></span>

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

### <span data-ttu-id="4d61c-253">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="4d61c-253">-FullyQualifiedModule</span></span>

<span data-ttu-id="4d61c-254">Anger moduler med namn som anges i form av **ModuleSpecification** -objekt (beskrivs i avsnittet anmärkningar i ModuleSpecification- [konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) i PowerShell SDK.</span><span class="sxs-lookup"><span data-stu-id="4d61c-254">Specifies modules with names that are specified in the form of **ModuleSpecification** objects (described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) in the PowerShell SDK.</span></span> <span data-ttu-id="4d61c-255">Parametern **FullyQualifiedModule** accepterar till exempel ett modulnamn som anges i formatet:</span><span class="sxs-lookup"><span data-stu-id="4d61c-255">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in the format:</span></span>

- <span data-ttu-id="4d61c-256">`@{ModuleName = "modulename"; ModuleVersion = "version_number"}` eller</span><span class="sxs-lookup"><span data-stu-id="4d61c-256">`@{ModuleName = "modulename"; ModuleVersion = "version_number"}` or</span></span>
- <span data-ttu-id="4d61c-257">`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.</span><span class="sxs-lookup"><span data-stu-id="4d61c-257">`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.</span></span>

<span data-ttu-id="4d61c-258">**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="4d61c-258">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="4d61c-259">Det går inte att ange parametern **FullyQualifiedModule** i samma kommando som en **modul** -parameter.</span><span class="sxs-lookup"><span data-stu-id="4d61c-259">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="4d61c-260">De två parametrarna kan inte anges samtidigt.</span><span class="sxs-lookup"><span data-stu-id="4d61c-260">The two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="4d61c-261">– Modul</span><span class="sxs-lookup"><span data-stu-id="4d61c-261">-Module</span></span>

<span data-ttu-id="4d61c-262">Anger och en matris med kommandon i Windows PowerShell snapin-moduler och moduler.</span><span class="sxs-lookup"><span data-stu-id="4d61c-262">Specifies and array of commands in the Windows PowerShell snap-ins and modules.</span></span> <span data-ttu-id="4d61c-263">Ange namnet på snapin-modulen och-modulen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-263">Enter the snap-in and module names.</span></span> <span data-ttu-id="4d61c-264">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4d61c-264">Wildcards are not permitted.</span></span>

<span data-ttu-id="4d61c-265">`Import-PSSession` Det går inte att importera providrar från en snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="4d61c-265">`Import-PSSession` cannot import providers from a snap-in.</span></span>

<span data-ttu-id="4d61c-266">Mer information finns i [about_PSSnapins](/powershell/module/Microsoft.PowerShell.Core/About/about_PSSnapins) och [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="4d61c-266">For more information, see [about_PSSnapins](/powershell/module/Microsoft.PowerShell.Core/About/about_PSSnapins) and [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

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

### <span data-ttu-id="4d61c-267">-Prefix</span><span class="sxs-lookup"><span data-stu-id="4d61c-267">-Prefix</span></span>

<span data-ttu-id="4d61c-268">Anger ett prefix till substantiven i namnen på importerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="4d61c-268">Specifies a prefix to the nouns in the names of imported commands.</span></span>

<span data-ttu-id="4d61c-269">Använd den här parametern för att undvika namn konflikter som kan uppstå när olika kommandon i sessionen har samma namn.</span><span class="sxs-lookup"><span data-stu-id="4d61c-269">Use this parameter to avoid name conflicts that might occur when different commands in the session have the same name.</span></span>

<span data-ttu-id="4d61c-270">Om du till exempel anger prefixet Remote och sedan importerar en `Get-Date` cmdlet, är cmdleten känd i sessionen som `Get-RemoteDate` och den förväxlas inte med den ursprungliga `Get-Date` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4d61c-270">For instance, if you specify the prefix Remote and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-RemoteDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

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

### <span data-ttu-id="4d61c-271">– Session</span><span class="sxs-lookup"><span data-stu-id="4d61c-271">-Session</span></span>

<span data-ttu-id="4d61c-272">Anger **PSSession** som cmdletarna importeras från.</span><span class="sxs-lookup"><span data-stu-id="4d61c-272">Specifies the **PSSession** from which the cmdlets are imported.</span></span> <span data-ttu-id="4d61c-273">Ange en variabel som innehåller ett session-objekt eller ett kommando som hämtar ett sessionsobjekt, till exempel ett `New-PSSession` eller- `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="4d61c-273">Enter a variable that contains a session object or a command that gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="4d61c-274">Du kan bara ange en session.</span><span class="sxs-lookup"><span data-stu-id="4d61c-274">You can specify only one session.</span></span> <span data-ttu-id="4d61c-275">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="4d61c-275">This parameter is required.</span></span>

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

### <span data-ttu-id="4d61c-276">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4d61c-276">CommonParameters</span></span>

<span data-ttu-id="4d61c-277">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4d61c-277">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4d61c-278">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4d61c-278">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4d61c-279">INDATA</span><span class="sxs-lookup"><span data-stu-id="4d61c-279">INPUTS</span></span>

### <span data-ttu-id="4d61c-280">Inga</span><span class="sxs-lookup"><span data-stu-id="4d61c-280">None</span></span>

<span data-ttu-id="4d61c-281">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4d61c-281">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="4d61c-282">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4d61c-282">OUTPUTS</span></span>

### <span data-ttu-id="4d61c-283">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="4d61c-283">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="4d61c-284">`Import-PSSession` returnerar samma modul-objekt som `New-Module` och `Get-Module` cmdlets returnerar.</span><span class="sxs-lookup"><span data-stu-id="4d61c-284">`Import-PSSession` returns the same module object that `New-Module` and `Get-Module` cmdlets return.</span></span>
<span data-ttu-id="4d61c-285">Den importerade modulen är dock tillfällig och finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-285">However, the imported module is temporary and exists only in the current session.</span></span> <span data-ttu-id="4d61c-286">Använd cmdleten för att skapa en permanent modul på disk `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="4d61c-286">To create a permanent module on disk, use the `Export-PSSession` cmdlet.</span></span>

## <span data-ttu-id="4d61c-287">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4d61c-287">NOTES</span></span>

- <span data-ttu-id="4d61c-288">`Import-PSSession` förlitar sig på PowerShell-infrastrukturen för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="4d61c-288">`Import-PSSession` relies on the  PowerShell remoting infrastructure.</span></span> <span data-ttu-id="4d61c-289">Om du vill använda denna cmdlet måste datorn konfigureras för WS-Management fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="4d61c-289">To use this cmdlet, the computer must be configured for WS-Management remoting.</span></span> <span data-ttu-id="4d61c-290">Mer information finns i [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) och [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d61c-290">For more information, see [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) and [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="4d61c-291">`Import-PSSession` importerar inte variabler eller PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="4d61c-291">`Import-PSSession` does not import variables or  PowerShell providers.</span></span>
- <span data-ttu-id="4d61c-292">När du importerar kommandon som har samma namn som kommandon i den aktuella sessionen kan de importerade kommandona dölja alias, funktioner och cmdlets i sessionen och de kan ersätta funktioner och variabler i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d61c-292">When you import commands that have the same names as commands in the current session, the imported commands can hide aliases, functions, and cmdlets in the session and they can replace functions and variables in the session.</span></span> <span data-ttu-id="4d61c-293">Använd parametern **prefix** för att förhindra namn konflikter.</span><span class="sxs-lookup"><span data-stu-id="4d61c-293">To prevent name conflicts, use the **Prefix** parameter.</span></span> <span data-ttu-id="4d61c-294">Mer information finns i [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="4d61c-294">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>
- <span data-ttu-id="4d61c-295">`Import-PSSession` konverterar alla kommandon till funktioner innan de importeras.</span><span class="sxs-lookup"><span data-stu-id="4d61c-295">`Import-PSSession` converts all commands into functions before it imports them.</span></span> <span data-ttu-id="4d61c-296">Det innebär att importerade kommandon fungerar lite annorlunda än om de behåller sin ursprungliga kommando typ.</span><span class="sxs-lookup"><span data-stu-id="4d61c-296">As a result, imported commands behave a bit differently than they would if they retained their original command type.</span></span> <span data-ttu-id="4d61c-297">Om du t. ex. importerar en cmdlet från en PSSession och sedan importerar en cmdlet med samma namn från en modul eller snapin-modul, körs den cmdlet som importeras från PSSession alltid som standard eftersom Functions prioriteras över cmdletar.</span><span class="sxs-lookup"><span data-stu-id="4d61c-297">For example, if you import a cmdlet from a PSSession and then import a cmdlet with the same name from a module or snap-in, the cmdlet that is imported from the PSSession always runs by default because functions take precedence over cmdlets.</span></span> <span data-ttu-id="4d61c-298">Om du importerar ett alias till en-session som har ett alias med samma namn, används alltid det ursprungliga aliaset, eftersom alias har företräde framför funktioner.</span><span class="sxs-lookup"><span data-stu-id="4d61c-298">Conversely, if you import an alias into a session that has an alias with the same name, the original alias is always used, because aliases take precedence over functions.</span></span> <span data-ttu-id="4d61c-299">Mer information finns i [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="4d61c-299">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>
- <span data-ttu-id="4d61c-300">`Import-PSSession` använder `Write-Progress` cmdleten för att visa förloppet för kommandot.</span><span class="sxs-lookup"><span data-stu-id="4d61c-300">`Import-PSSession` uses the `Write-Progress` cmdlet to display the progress of the command.</span></span> <span data-ttu-id="4d61c-301">Du kan se förlopps indikatorn när kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="4d61c-301">You might see the progress bar while the command is running.</span></span>
- <span data-ttu-id="4d61c-302">För att hitta de kommandon som ska importeras `Import-PSSession` använder `Invoke-Command` cmdleten för att köra ett `Get-Command` kommando i PSSession.</span><span class="sxs-lookup"><span data-stu-id="4d61c-302">To find the commands to import, `Import-PSSession` uses the `Invoke-Command` cmdlet to run a `Get-Command` command in the PSSession.</span></span> <span data-ttu-id="4d61c-303">För att hämta formatering av data för kommandona används `Get-FormatData` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4d61c-303">To get formatting data for the commands, it uses the `Get-FormatData` cmdlet.</span></span> <span data-ttu-id="4d61c-304">Du kan se fel meddelanden från dessa cmdletar när du kör ett `Import-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="4d61c-304">You might see error messages from these cmdlets when you run an `Import-PSSession` command.</span></span> <span data-ttu-id="4d61c-305">`Import-PSSession`Det går inte heller att importera kommandon från en PSSession som inte innehåller `Get-Command` `Get-FormatData` `Select-Object` cmdletarna,, och `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="4d61c-305">Also, `Import-PSSession` cannot import commands from a PSSession that does not include the `Get-Command`, `Get-FormatData`, `Select-Object`, and `Get-Help` cmdlets.</span></span>
- <span data-ttu-id="4d61c-306">Importerade kommandon har samma begränsningar som andra fjärrkommandon, inklusive möjligheten att starta ett program med ett användar gränssnitt, t. ex. anteckningar.</span><span class="sxs-lookup"><span data-stu-id="4d61c-306">Imported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>
- <span data-ttu-id="4d61c-307">Eftersom Windows PowerShell-profiler inte körs i PSSessions är kommandona som en profil lägger till i en session inte tillgängliga för `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="4d61c-307">Because Windows PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to `Import-PSSession`.</span></span> <span data-ttu-id="4d61c-308">Om du vill importera kommandon från en profil använder du ett `Invoke-Command` kommando för att köra profilen i PSSession manuellt innan du importerar kommandon.</span><span class="sxs-lookup"><span data-stu-id="4d61c-308">To import commands from a profile, use an `Invoke-Command` command to run the profile in the PSSession manually before importing commands.</span></span>
- <span data-ttu-id="4d61c-309">Den temporära modul som `Import-PSSession` skapar kan innehålla en formateringsinformation, även om kommandot inte importerar formaterings data.</span><span class="sxs-lookup"><span data-stu-id="4d61c-309">The temporary module that `Import-PSSession` creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="4d61c-310">Om kommandot inte importerar dataformaterade data kommer eventuella filer som skapas inte att innehålla formatering.</span><span class="sxs-lookup"><span data-stu-id="4d61c-310">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>
- <span data-ttu-id="4d61c-311">För att kunna använda `Import-PSSession` kan körnings principen i den aktuella sessionen inte vara begränsad eller AllSigned, eftersom den temporära modul som `Import-PSSession` skapar innehåller osignerade skriptfiler som är förbjudna av dessa principer.</span><span class="sxs-lookup"><span data-stu-id="4d61c-311">To use `Import-PSSession`, the execution policy in the current session cannot be Restricted or AllSigned, because the temporary module that `Import-PSSession` creates contains unsigned script files that are prohibited by these policies.</span></span> <span data-ttu-id="4d61c-312">Om du vill använda `Import-PSSession` utan att ändra körnings principen för den lokala datorn använder du **omfattnings** parametern för `Set-ExecutionPolicy` att ange en mindre begränsande körnings princip för en enda process.</span><span class="sxs-lookup"><span data-stu-id="4d61c-312">To use `Import-PSSession` without changing the execution policy for the local computer, use the **Scope** parameter of `Set-ExecutionPolicy` to set a less restrictive execution policy for a single process.</span></span>
- <span data-ttu-id="4d61c-313">I Windows PowerShell 2,0 innehåller hjälp avsnitten för kommandon som importeras från en annan session inte det prefix som du tilldelar med hjälp av parametern **prefix** .</span><span class="sxs-lookup"><span data-stu-id="4d61c-313">In Windows PowerShell 2.0, help topics for commands that are imported from another session do not include the prefix that you assign by using the **Prefix** parameter.</span></span> <span data-ttu-id="4d61c-314">Om du vill ha hjälp med ett importerat kommando i Windows PowerShell 2,0 använder du det ursprungliga kommando namnet (icke-förfixet).</span><span class="sxs-lookup"><span data-stu-id="4d61c-314">To get help for an imported command in Windows PowerShell 2.0, use the original (non-prefixed) command name.</span></span>

## <span data-ttu-id="4d61c-315">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4d61c-315">RELATED LINKS</span></span>

[<span data-ttu-id="4d61c-316">Exportera – PSSession</span><span class="sxs-lookup"><span data-stu-id="4d61c-316">Export-PSSession</span></span>](Export-PSSession.md)
