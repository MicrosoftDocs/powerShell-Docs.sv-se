---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-process?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Process
ms.openlocfilehash: 543c2b683ca3631e2e05f57d9c70ff4455071e4b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267686"
---
# <span data-ttu-id="cdd53-103">Get-Process</span><span class="sxs-lookup"><span data-stu-id="cdd53-103">Get-Process</span></span>

## <span data-ttu-id="cdd53-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="cdd53-104">SYNOPSIS</span></span>
<span data-ttu-id="cdd53-105">Hämtar de processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cdd53-105">Gets the processes that are running on the local computer.</span></span>

## <span data-ttu-id="cdd53-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cdd53-106">SYNTAX</span></span>

### <span data-ttu-id="cdd53-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="cdd53-107">Name (Default)</span></span>

```
Get-Process [[-Name] <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="cdd53-108">NameWithUserName</span><span class="sxs-lookup"><span data-stu-id="cdd53-108">NameWithUserName</span></span>

```
Get-Process [[-Name] <String[]>] -IncludeUserName [<CommonParameters>]
```

### <span data-ttu-id="cdd53-109">Id</span><span class="sxs-lookup"><span data-stu-id="cdd53-109">Id</span></span>

```
Get-Process -Id <Int32[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="cdd53-110">IdWithUserName</span><span class="sxs-lookup"><span data-stu-id="cdd53-110">IdWithUserName</span></span>

```
Get-Process -Id <Int32[]> -IncludeUserName [<CommonParameters>]
```

### <span data-ttu-id="cdd53-111">InputObject</span><span class="sxs-lookup"><span data-stu-id="cdd53-111">InputObject</span></span>

```
Get-Process -InputObject <Process[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="cdd53-112">InputObjectWithUserName</span><span class="sxs-lookup"><span data-stu-id="cdd53-112">InputObjectWithUserName</span></span>

```
Get-Process -InputObject <Process[]> -IncludeUserName [<CommonParameters>]
```

## <span data-ttu-id="cdd53-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cdd53-113">DESCRIPTION</span></span>

<span data-ttu-id="cdd53-114">`Get-Process`Cmdleten hämtar processerna på en lokal dator.</span><span class="sxs-lookup"><span data-stu-id="cdd53-114">The `Get-Process` cmdlet gets the processes on a local computer.</span></span>

<span data-ttu-id="cdd53-115">Utan parametrar hämtar denna cmdlet alla processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cdd53-115">Without parameters, this cmdlet gets all of the processes on the local computer.</span></span>
<span data-ttu-id="cdd53-116">Du kan också ange en viss process efter process namn eller process-ID (PID) eller skicka ett process objekt via pipelinen till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cdd53-116">You can also specify a particular process by process name or process ID (PID) or pass a process object through the pipeline to this cmdlet.</span></span>

<span data-ttu-id="cdd53-117">Som standard returnerar denna cmdlet ett process objekt med detaljerad information om processen och stöder metoder som gör att du kan starta och stoppa processen.</span><span class="sxs-lookup"><span data-stu-id="cdd53-117">By default, this cmdlet returns a process object that has detailed information about the process and supports methods that let you start and stop the process.</span></span>
<span data-ttu-id="cdd53-118">Du kan också använda parametrarna för `Get-Process` cmdleten för att hämta fil versions information för programmet som körs i processen och för att hämta de moduler som processen läste in.</span><span class="sxs-lookup"><span data-stu-id="cdd53-118">You can also use the parameters of the `Get-Process` cmdlet to get file version information for the program that runs in the process and to get the modules that the process loaded.</span></span>

## <span data-ttu-id="cdd53-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="cdd53-119">EXAMPLES</span></span>

### <span data-ttu-id="cdd53-120">Exempel 1: Hämta en lista över alla aktiva processer på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="cdd53-120">Example 1: Get a list of all active processes on the local computer</span></span>

```powershell
Get-Process
```

<span data-ttu-id="cdd53-121">Det här kommandot hämtar en lista över alla aktiva processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cdd53-121">This command gets a list of all active processes running on the local computer.</span></span>
<span data-ttu-id="cdd53-122">En definition av varje kolumn finns i avsnittet om [anteckningar](#notes) .</span><span class="sxs-lookup"><span data-stu-id="cdd53-122">For a definition of each column, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="cdd53-123">Exempel 2: Hämta alla tillgängliga data om en eller flera processer</span><span class="sxs-lookup"><span data-stu-id="cdd53-123">Example 2: Get all available data about one or more processes</span></span>

```powershell
Get-Process winword, explorer | Format-List *
```

<span data-ttu-id="cdd53-124">Det här kommandot hämtar alla tillgängliga data om Winword-och Utforskaren-processer på datorn.</span><span class="sxs-lookup"><span data-stu-id="cdd53-124">This command gets all available data about the Winword and Explorer processes on the computer.</span></span>
<span data-ttu-id="cdd53-125">Den använder **Name** -parametern för att ange processerna, men utelämnar det valfria parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="cdd53-125">It uses the **Name** parameter to specify the processes, but it omits the optional parameter name.</span></span>
<span data-ttu-id="cdd53-126">Pipeline-operatorn `|` skickar data till `Format-List` cmdleten, som visar alla tillgängliga egenskaper `*` för process objekt i Winword och Utforskaren.</span><span class="sxs-lookup"><span data-stu-id="cdd53-126">The pipeline operator `|` passes the data to the `Format-List` cmdlet, which displays all available properties `*` of the Winword and Explorer process objects.</span></span>

<span data-ttu-id="cdd53-127">Du kan också identifiera processerna efter process-ID.</span><span class="sxs-lookup"><span data-stu-id="cdd53-127">You can also identify the processes by their process IDs.</span></span>
<span data-ttu-id="cdd53-128">Till exempel `Get-Process -Id 664, 2060` .</span><span class="sxs-lookup"><span data-stu-id="cdd53-128">For instance, `Get-Process -Id 664, 2060`.</span></span>

### <span data-ttu-id="cdd53-129">Exempel 3: Hämta alla processer med en arbets mängd som är större än en angiven storlek</span><span class="sxs-lookup"><span data-stu-id="cdd53-129">Example 3: Get all processes with a working set greater than a specified size</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -gt 20000000}
```

<span data-ttu-id="cdd53-130">Det här kommandot hämtar alla processer som har en arbets mängd som är större än 20 MB.</span><span class="sxs-lookup"><span data-stu-id="cdd53-130">This command gets all processes that have a working set greater than 20 MB.</span></span>
<span data-ttu-id="cdd53-131">Den använder `Get-Process`  cmdleten för att hämta alla processer som körs.</span><span class="sxs-lookup"><span data-stu-id="cdd53-131">It uses the `Get-Process`  cmdlet to get all running processes.</span></span>
<span data-ttu-id="cdd53-132">Pipeline-operatorn `|` överför process objekt till `Where-Object` cmdleten, som endast väljer objektet med ett värde som är större än 20 000 000 byte för den **aktiva** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="cdd53-132">The pipeline operator `|` passes the process objects to the `Where-Object` cmdlet, which selects only the object with a value greater than 20,000,000 bytes for the **WorkingSet** property.</span></span>

<span data-ttu-id="cdd53-133">Den **aktiva** processen är en av många egenskaper för process objekt.</span><span class="sxs-lookup"><span data-stu-id="cdd53-133">**WorkingSet** is one of many properties of process objects.</span></span>
<span data-ttu-id="cdd53-134">Om du vill se alla egenskaper skriver du `Get-Process | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="cdd53-134">To see all of the properties, type `Get-Process | Get-Member`.</span></span>
<span data-ttu-id="cdd53-135">Som standard är värdena för alla mängd egenskaper i byte, även om standard visningen visar dem i kilobyte och megabyte.</span><span class="sxs-lookup"><span data-stu-id="cdd53-135">By default, the values of all amount properties are in bytes, even though the default display lists them in kilobytes and megabytes.</span></span>

### <span data-ttu-id="cdd53-136">Exempel 4: Visa en lista över processer på datorn i grupper baserat på prioritet</span><span class="sxs-lookup"><span data-stu-id="cdd53-136">Example 4: List processes on the computer in groups based on priority</span></span>

```powershell
$A = Get-Process
$A | Get-Process | Format-Table -View priority
```

<span data-ttu-id="cdd53-137">De här kommandona visar processerna på datorn i grupper baserat på deras prioritets klass.</span><span class="sxs-lookup"><span data-stu-id="cdd53-137">These commands list the processes on the computer in groups based on their priority class.</span></span>
<span data-ttu-id="cdd53-138">Det första kommandot hämtar alla processer på datorn och lagrar dem sedan i `$A` variabeln.</span><span class="sxs-lookup"><span data-stu-id="cdd53-138">The first command gets all the processes on the computer and then stores them in the `$A` variable.</span></span>

<span data-ttu-id="cdd53-139">Det andra kommandot rör objektet **process** som lagras i `$A` variabeln till `Get-Process` cmdleten, sedan till `Format-Table` cmdleten, som formaterar processerna med hjälp av vyn **prioritet** .</span><span class="sxs-lookup"><span data-stu-id="cdd53-139">The second command pipes the **Process** object stored in the `$A` variable to the `Get-Process` cmdlet, then to the `Format-Table` cmdlet, which formats the processes by using the **Priority** view.</span></span>

<span data-ttu-id="cdd53-140">Vyn **prioritet** , och andra vyer, definieras i PS1XML-format-filer i PowerShell-arbetskatalogen ( `$pshome` ).</span><span class="sxs-lookup"><span data-stu-id="cdd53-140">The **Priority** view, and other views, are defined in the PS1XML format files in the PowerShell home directory (`$pshome`).</span></span>

### <span data-ttu-id="cdd53-141">Exempel 5: Lägg till en egenskap till standard visningen Get-Process utdata</span><span class="sxs-lookup"><span data-stu-id="cdd53-141">Example 5: Add a property to the standard Get-Process output display</span></span>

```powershell
Get-Process pwsh | Format-Table `
    @{Label = "NPM(K)"; Expression = {[int]($_.NPM / 1024)}},
    @{Label = "PM(K)"; Expression = {[int]($_.PM / 1024)}},
    @{Label = "WS(K)"; Expression = {[int]($_.WS / 1024)}},
    @{Label = "VM(M)"; Expression = {[int]($_.VM / 1MB)}},
    @{Label = "CPU(s)"; Expression = {if ($_.CPU) {$_.CPU.ToString("N")}}},
    Id, MachineName, ProcessName -AutoSize
```

```Output
NPM(K) PM(K) WS(K) VM(M) CPU(s)   Id MachineName ProcessName
------ ----- ----- ----- ------   -- ----------- -----------
     6 23500 31340   142 1.70   1980 .           pwsh
     6 23500 31348   142 2.75   4016 .           pwsh
    27 54572 54520   576 5.52   4428 .           pwsh
```

<span data-ttu-id="cdd53-142">Det här exemplet innehåller ett `Format-Table` kommando som lägger till egenskapen **MachineName** i `Get-Process` standardutdata-visningen.</span><span class="sxs-lookup"><span data-stu-id="cdd53-142">This example provides a `Format-Table` command that adds the **MachineName** property to the standard `Get-Process` output display.</span></span>

### <span data-ttu-id="cdd53-143">Exempel 6: Hämta versions information för en process</span><span class="sxs-lookup"><span data-stu-id="cdd53-143">Example 6: Get version information for a process</span></span>

```powershell
Get-Process pwsh -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.1.2            6.1.2            C:\Program Files\PowerShell\6\pwsh.exe
```

<span data-ttu-id="cdd53-144">Detta kommando använder parametern **FileVersionInfo** för att hämta versions information för den pwsh.exe-fil som är huvud-till-modul för PowerShell-processen.</span><span class="sxs-lookup"><span data-stu-id="cdd53-144">This command uses the **FileVersionInfo** parameter to get the version information for the pwsh.exe file that is the main module for the PowerShell process.</span></span>

<span data-ttu-id="cdd53-145">Om du vill köra det här kommandot med processer som du inte äger i Windows Vista och senare versioner av Windows, måste du öppna PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="cdd53-145">To run this command with processes that you do not own on Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option.</span></span>

### <span data-ttu-id="cdd53-146">Exempel 7: Hämta moduler som lästs in med den angivna processen</span><span class="sxs-lookup"><span data-stu-id="cdd53-146">Example 7: Get modules loaded with the specified process</span></span>

```powershell
Get-Process SQL* -Module
```

<span data-ttu-id="cdd53-147">Det här kommandot använder **modulen modul** för att hämta de moduler som har lästs in av processen.</span><span class="sxs-lookup"><span data-stu-id="cdd53-147">This command uses the **Module** parameter to get the modules that have been loaded by the process.</span></span>
<span data-ttu-id="cdd53-148">Det här kommandot hämtar modulerna för de processer som har namn som börjar med SQL.</span><span class="sxs-lookup"><span data-stu-id="cdd53-148">This command gets the modules for the processes that have names that begin with SQL.</span></span>

<span data-ttu-id="cdd53-149">Om du vill köra det här kommandot på Windows Vista och senare versioner av Windows med processer som du inte äger måste du starta PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="cdd53-149">To run this command on Windows Vista and later versions of Windows with processes that you do not own, you must start PowerShell with the Run as administrator option.</span></span>

### <span data-ttu-id="cdd53-150">Exempel 8: hitta ägaren till en process</span><span class="sxs-lookup"><span data-stu-id="cdd53-150">Example 8: Find the owner of a process</span></span>

```powershell
Get-Process pwsh -IncludeUserName
```

```Output
Handles      WS(K)   CPU(s)     Id UserName            ProcessName
-------      -----   ------     -- --------            -----------
    782     132080     2.08   2188 DOMAIN01\user01     pwsh
```

<span data-ttu-id="cdd53-151">Det här kommandot visar hur du hittar ägaren till en process.</span><span class="sxs-lookup"><span data-stu-id="cdd53-151">This command shows how to find the owner of a process.</span></span>
<span data-ttu-id="cdd53-152">I Windows kräver parametern **IncludeUserName** utökade användar rättigheter (kör som administratör).</span><span class="sxs-lookup"><span data-stu-id="cdd53-152">On Windows, the **IncludeUserName** parameter requires elevated user rights (Run as Administrator).</span></span>
<span data-ttu-id="cdd53-153">Utdata visar att ägaren är Domain01\user01.</span><span class="sxs-lookup"><span data-stu-id="cdd53-153">The output reveals that the owner is Domain01\user01.</span></span>

### <span data-ttu-id="cdd53-154">Exempel 9: Använd en automatisk variabel för att identifiera processen som är värd för den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="cdd53-154">Example 9: Use an automatic variable to identify the process hosting the current session</span></span>

```powershell
Get-Process pwsh
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21     105.95       4.33    1192  10 pwsh
    79    83.81     117.61       2.16   10580  10 pwsh
```

```powershell
Get-Process -Id $PID
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21      77.53       4.39    1192  10 pwsh
```

<span data-ttu-id="cdd53-155">De här kommandona visar hur du använder den `$PID` automatiska variabeln för att identifiera den process som är värd för den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="cdd53-155">These commands show how to use the `$PID` automatic variable to identify the process that is hosting the current PowerShell session.</span></span>
<span data-ttu-id="cdd53-156">Du kan använda den här metoden för att skilja värd processen från andra PowerShell-processer som du kanske vill stoppa eller stänga.</span><span class="sxs-lookup"><span data-stu-id="cdd53-156">You can use this method to distinguish the host process from other PowerShell processes that you might want to stop or close.</span></span>

<span data-ttu-id="cdd53-157">Det första kommandot hämtar alla PowerShell-processer i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="cdd53-157">The first command gets all of the PowerShell processes in the current session.</span></span>

<span data-ttu-id="cdd53-158">Det andra kommandot hämtar PowerShell-processen som är värd för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="cdd53-158">The second command gets the PowerShell process that is hosting the current session.</span></span>

### <span data-ttu-id="cdd53-159">Exempel 10: Hämta alla processer som har en huvud fönster rubrik och visa dem i en tabell</span><span class="sxs-lookup"><span data-stu-id="cdd53-159">Example 10: Get all processes that have a main window title and display them in a table</span></span>

```powershell
Get-Process | Where-Object {$_.mainWindowTitle} | Format-Table Id, Name, mainWindowtitle -AutoSize
```

<span data-ttu-id="cdd53-160">Det här kommandot hämtar alla processer som har en huvud fönster rubrik och visar dem i en tabell med process-ID och process namnet.</span><span class="sxs-lookup"><span data-stu-id="cdd53-160">This command gets all the processes that have a main window title, and it displays them in a table with the process ID and the process name.</span></span>

<span data-ttu-id="cdd53-161">Egenskapen **mainWindowTitle** är bara en av många användbara egenskaper för det **process** objekt som `Get-Process` returnerar.</span><span class="sxs-lookup"><span data-stu-id="cdd53-161">The **mainWindowTitle** property is just one of many useful properties of the **Process** object that `Get-Process` returns.</span></span>
<span data-ttu-id="cdd53-162">Om du vill visa alla egenskaper, rör du resultatet av ett `Get-Process` kommando till `Get-Member` cmdleten `Get-Process | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="cdd53-162">To view all of the properties, pipe the results of a `Get-Process` command to the `Get-Member` cmdlet `Get-Process | Get-Member`.</span></span>

## <span data-ttu-id="cdd53-163">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="cdd53-163">PARAMETERS</span></span>

### <span data-ttu-id="cdd53-164">-FileVersionInfo</span><span class="sxs-lookup"><span data-stu-id="cdd53-164">-FileVersionInfo</span></span>

<span data-ttu-id="cdd53-165">Anger att denna cmdlet hämtar fil versions information för programmet som körs i processen.</span><span class="sxs-lookup"><span data-stu-id="cdd53-165">Indicates that this cmdlet gets the file version information for the program that runs in the process.</span></span>

<span data-ttu-id="cdd53-166">I Windows Vista och senare versioner av Windows måste du öppna PowerShell med alternativet Kör som administratör för att kunna använda den här parametern på processer som du inte äger.</span><span class="sxs-lookup"><span data-stu-id="cdd53-166">On Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option to use this parameter on processes that you do not own.</span></span>

<span data-ttu-id="cdd53-167">Använd cmdleten för att hämta fil versions information för en process på en fjärrdator `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="cdd53-167">To get file version information for a process on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="cdd53-168">Att använda den här parametern motsvarar att hämta egenskapen **MainModule. FileVersionInfo** för varje process objekt.</span><span class="sxs-lookup"><span data-stu-id="cdd53-168">Using this parameter is equivalent to getting the **MainModule.FileVersionInfo** property of each process object.</span></span>
<span data-ttu-id="cdd53-169">När du använder den här parametern `Get-Process` returnerar en **FileVersionInfo** Object **system. Diagnostics. FileVersionInfo** , inte ett process objekt.</span><span class="sxs-lookup"><span data-stu-id="cdd53-169">When you use this parameter, `Get-Process` returns a **FileVersionInfo** object **System.Diagnostics.FileVersionInfo** , not a process object.</span></span>
<span data-ttu-id="cdd53-170">Därför kan du inte skicka kommandots utdata till en cmdlet som förväntar sig ett process objekt, till exempel `Stop-Process` .</span><span class="sxs-lookup"><span data-stu-id="cdd53-170">So, you cannot pipe the output of the command to a cmdlet that expects a process object, such as `Stop-Process`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases: FV, FVI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cdd53-171">-ID</span><span class="sxs-lookup"><span data-stu-id="cdd53-171">-Id</span></span>

<span data-ttu-id="cdd53-172">Anger en eller flera processer efter process-ID (PID).</span><span class="sxs-lookup"><span data-stu-id="cdd53-172">Specifies one or more processes by process ID (PID).</span></span>
<span data-ttu-id="cdd53-173">Använd kommatecken för att avgränsa ID: n för att ange flera ID: n.</span><span class="sxs-lookup"><span data-stu-id="cdd53-173">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="cdd53-174">Om du vill hitta ett process-ID skriver du `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="cdd53-174">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id, IdWithUserName
Aliases: PID

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cdd53-175">-IncludeUserName</span><span class="sxs-lookup"><span data-stu-id="cdd53-175">-IncludeUserName</span></span>

<span data-ttu-id="cdd53-176">Anger **att objektets** username-värde returneras med kommandots resultat.</span><span class="sxs-lookup"><span data-stu-id="cdd53-176">Indicates that the UserName value of the **Process** object is returned with results of the command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameWithUserName, IdWithUserName, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cdd53-177">– InputObject</span><span class="sxs-lookup"><span data-stu-id="cdd53-177">-InputObject</span></span>

<span data-ttu-id="cdd53-178">Anger ett eller flera process objekt.</span><span class="sxs-lookup"><span data-stu-id="cdd53-178">Specifies one or more process objects.</span></span>
<span data-ttu-id="cdd53-179">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="cdd53-179">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cdd53-180">– Modul</span><span class="sxs-lookup"><span data-stu-id="cdd53-180">-Module</span></span>

<span data-ttu-id="cdd53-181">Anger att denna cmdlet hämtar de moduler som har lästs in av processerna.</span><span class="sxs-lookup"><span data-stu-id="cdd53-181">Indicates that this cmdlet gets the modules that have been loaded by the processes.</span></span>

<span data-ttu-id="cdd53-182">I Windows Vista och senare versioner av Windows måste du öppna PowerShell med alternativet Kör som administratör för att kunna använda den här parametern på processer som du inte äger.</span><span class="sxs-lookup"><span data-stu-id="cdd53-182">On Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option to use this parameter on processes that you do not own.</span></span>

<span data-ttu-id="cdd53-183">Använd cmdleten för att hämta moduler som har lästs in av en process på en fjärrdator `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="cdd53-183">To get the modules that have been loaded by a process on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="cdd53-184">Den här parametern motsvarar att hämta egenskapen **modules** för varje process objekt.</span><span class="sxs-lookup"><span data-stu-id="cdd53-184">This parameter is equivalent to getting the **Modules** property of each process object.</span></span>
<span data-ttu-id="cdd53-185">När du använder den här parametern returnerar denna cmdlet en **ProcessModule** Object **system. Diagnostics. ProcessModule** , inte ett process objekt.</span><span class="sxs-lookup"><span data-stu-id="cdd53-185">When you use this parameter, this cmdlet returns a **ProcessModule** object **System.Diagnostics.ProcessModule** , not a process object.</span></span>
<span data-ttu-id="cdd53-186">Därför kan du inte skicka kommandots utdata till en cmdlet som förväntar sig ett process objekt, till exempel `Stop-Process` .</span><span class="sxs-lookup"><span data-stu-id="cdd53-186">So, you cannot pipe the output of the command to a cmdlet that expects a process object, such as `Stop-Process`.</span></span>

<span data-ttu-id="cdd53-187">När du använder både *modulen* och **FileVersionInfo** -parametrarna i samma kommando, returnerar denna cmdlet ett **FileVersionInfo** -objekt med information om fil versionen för alla moduler.</span><span class="sxs-lookup"><span data-stu-id="cdd53-187">When you use both the *Module* and **FileVersionInfo** parameters in the same command, this cmdlet returns a **FileVersionInfo** object with information about the file version of all modules.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cdd53-188">-Name</span><span class="sxs-lookup"><span data-stu-id="cdd53-188">-Name</span></span>

<span data-ttu-id="cdd53-189">Anger en eller flera processer efter process namn.</span><span class="sxs-lookup"><span data-stu-id="cdd53-189">Specifies one or more processes by process name.</span></span>
<span data-ttu-id="cdd53-190">Du kan ange flera process namn (avgränsade med kommatecken) och använda jokertecken.</span><span class="sxs-lookup"><span data-stu-id="cdd53-190">You can type multiple process names (separated by commas) and use wildcard characters.</span></span>
<span data-ttu-id="cdd53-191">Parameter namnet ("namn") är valfritt.</span><span class="sxs-lookup"><span data-stu-id="cdd53-191">The parameter name ("Name") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, NameWithUserName
Aliases: ProcessName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="cdd53-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cdd53-192">CommonParameters</span></span>

<span data-ttu-id="cdd53-193">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cdd53-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cdd53-194">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="cdd53-194">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="cdd53-195">INDATA</span><span class="sxs-lookup"><span data-stu-id="cdd53-195">INPUTS</span></span>

### <span data-ttu-id="cdd53-196">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="cdd53-196">System.Diagnostics.Process</span></span>

<span data-ttu-id="cdd53-197">Du kan skicka vidare ett process objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cdd53-197">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="cdd53-198">UTDATA</span><span class="sxs-lookup"><span data-stu-id="cdd53-198">OUTPUTS</span></span>

### <span data-ttu-id="cdd53-199">System. Diagnostics. process, system. Diagnostics. FileVersionInfo, system. Diagnostics. ProcessModule</span><span class="sxs-lookup"><span data-stu-id="cdd53-199">System.Diagnostics.Process, System.Diagnostics.FileVersionInfo, System.Diagnostics.ProcessModule</span></span>

<span data-ttu-id="cdd53-200">Som standard returnerar denna cmdlet ett **system. Diagnostics. process** -objekt.</span><span class="sxs-lookup"><span data-stu-id="cdd53-200">By default, this cmdlet returns a **System.Diagnostics.Process** object.</span></span>
<span data-ttu-id="cdd53-201">Om du använder parametern **FileVersionInfo** returneras ett **system. Diagnostics. FileVersionInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="cdd53-201">If you use the **FileVersionInfo** parameter, it returns a **System.Diagnostics.FileVersionInfo** object.</span></span>
<span data-ttu-id="cdd53-202">Om du använder parametern **modul** , utan parametern **FileVersionInfo** , returneras ett **system. Diagnostics. ProcessModule** -objekt.</span><span class="sxs-lookup"><span data-stu-id="cdd53-202">If you use the **Module** parameter, without the **FileVersionInfo** parameter, it returns a **System.Diagnostics.ProcessModule** object.</span></span>

## <span data-ttu-id="cdd53-203">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="cdd53-203">NOTES</span></span>

- <span data-ttu-id="cdd53-204">Du kan också referera till den här cmdleten med dess inbyggda alias, PS och GPS.</span><span class="sxs-lookup"><span data-stu-id="cdd53-204">You can also refer to this cmdlet by its built-in aliases, ps and gps.</span></span> <span data-ttu-id="cdd53-205">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="cdd53-205">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="cdd53-206">På datorer som kör en 64-bitars version av Windows får 64-bitars versionen av PowerShell bara 64-bitars process-moduler och 32-bitars versionen av PowerShell får bara 32-bitars process moduler.</span><span class="sxs-lookup"><span data-stu-id="cdd53-206">On computers that are running a 64-bit version of Windows, the 64-bit version of PowerShell gets only 64-bit process modules and the 32-bit version of PowerShell gets only 32-bit process modules.</span></span>
- <span data-ttu-id="cdd53-207">Du kan använda egenskaper och metoder för Win32_Process-objektet Windows Management Instrumentation (WMI) i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cdd53-207">You can use the properties and methods of the Windows Management Instrumentation (WMI) Win32_Process object in PowerShell.</span></span> <span data-ttu-id="cdd53-208">Mer information finns i `Get-WmiObject` och WMI SDK.</span><span class="sxs-lookup"><span data-stu-id="cdd53-208">For information, see `Get-WmiObject` and the WMI SDK.</span></span>
- <span data-ttu-id="cdd53-209">Standard visningen av en process är en tabell som innehåller följande kolumner.</span><span class="sxs-lookup"><span data-stu-id="cdd53-209">The default display of a process is a table that includes the following columns.</span></span> <span data-ttu-id="cdd53-210">En beskrivning av alla egenskaper för process objekt finns i [process egenskaper](/dotnet/api/system.diagnostics.process) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="cdd53-210">For a description of all of the properties of process objects, see [Process Properties](/dotnet/api/system.diagnostics.process) in the MSDN library.</span></span>
  - <span data-ttu-id="cdd53-211">Handtag: antalet referenser som processen har öppnat.</span><span class="sxs-lookup"><span data-stu-id="cdd53-211">Handles: The number of handles that the process has opened.</span></span>
  - <span data-ttu-id="cdd53-212">NPM (K): mängden icke växlings Bart minne som processen använder, i kilobyte.</span><span class="sxs-lookup"><span data-stu-id="cdd53-212">NPM(K): The amount of non-paged memory that the process is using, in kilobytes.</span></span>
  - <span data-ttu-id="cdd53-213">PM (K): hur mycket växlings Bart minne som processen använder, i kilobyte.</span><span class="sxs-lookup"><span data-stu-id="cdd53-213">PM(K): The amount of pageable memory that the process is using, in kilobytes.</span></span>
  - <span data-ttu-id="cdd53-214">WS (K): storleken på processens arbets minne i kilobyte.</span><span class="sxs-lookup"><span data-stu-id="cdd53-214">WS(K): The size of the working set of the process, in kilobytes.</span></span>
    <span data-ttu-id="cdd53-215">Den aktiva arbets minnet består av de sidor i minnet som nyligen refererats av processen.</span><span class="sxs-lookup"><span data-stu-id="cdd53-215">The working set consists of the pages of memory that were recently referenced by the process.</span></span>
  - <span data-ttu-id="cdd53-216">Virtuell dator (M): mängden virtuellt minne som processen använder, i megabyte.</span><span class="sxs-lookup"><span data-stu-id="cdd53-216">VM(M): The amount of virtual memory that the process is using, in megabytes.</span></span>
    <span data-ttu-id="cdd53-217">Virtuellt minne innehåller lagrings utrymme i växlingsfilerna på disk.</span><span class="sxs-lookup"><span data-stu-id="cdd53-217">Virtual memory includes storage in the paging files on disk.</span></span>
  - <span data-ttu-id="cdd53-218">PROCESSOR (er): mängden processor tid som processen har använt på alla processorer, i sekunder.</span><span class="sxs-lookup"><span data-stu-id="cdd53-218">CPU(s): The amount of processor time that the process has used on all processors, in seconds.</span></span>
  - <span data-ttu-id="cdd53-219">ID: process-ID (PID) för processen.</span><span class="sxs-lookup"><span data-stu-id="cdd53-219">ID: The process ID (PID) of the process.</span></span>
  - <span data-ttu-id="cdd53-220">ProcessName: namnet på processen.</span><span class="sxs-lookup"><span data-stu-id="cdd53-220">ProcessName: The name of the process.</span></span>
    <span data-ttu-id="cdd53-221">Förklaringar av begreppen som rör processer finns i ord listan i hjälp-och Support Center och i hjälpen för aktivitets hanteraren.</span><span class="sxs-lookup"><span data-stu-id="cdd53-221">For explanations of the concepts related to processes, see the Glossary in Help and Support Center and the Help for Task Manager.</span></span>
- <span data-ttu-id="cdd53-222">Du kan också använda de inbyggda alternativa vyerna för de processer som är tillgängliga med `Format-Table` , t. ex. **StartTime** och **Priority** , och du kan skapa egna vyer.</span><span class="sxs-lookup"><span data-stu-id="cdd53-222">You can also use the built-in alternate views of the processes available with `Format-Table`, such as **StartTime** and **Priority** , and you can design your own views.</span></span>

## <span data-ttu-id="cdd53-223">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="cdd53-223">RELATED LINKS</span></span>

[<span data-ttu-id="cdd53-224">Fel sökning – process</span><span class="sxs-lookup"><span data-stu-id="cdd53-224">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="cdd53-225">Hämta process</span><span class="sxs-lookup"><span data-stu-id="cdd53-225">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="cdd53-226">Start process</span><span class="sxs-lookup"><span data-stu-id="cdd53-226">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="cdd53-227">Stoppa – process</span><span class="sxs-lookup"><span data-stu-id="cdd53-227">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="cdd53-228">Vänta-process</span><span class="sxs-lookup"><span data-stu-id="cdd53-228">Wait-Process</span></span>](Wait-Process.md)

