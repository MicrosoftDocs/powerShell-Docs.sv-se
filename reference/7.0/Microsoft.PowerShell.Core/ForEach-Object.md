---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/18/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 584ca877cedfe1494f8386af75f9f1911a5b8f15
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685641"
---
# <span data-ttu-id="6a571-103">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="6a571-103">ForEach-Object</span></span>

## <span data-ttu-id="6a571-104">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="6a571-104">Synopsis</span></span>
<span data-ttu-id="6a571-105">Utför en åtgärd mot varje objekt i en samling inobjekt.</span><span class="sxs-lookup"><span data-stu-id="6a571-105">Performs an operation against each item in a collection of input objects.</span></span>

## <span data-ttu-id="6a571-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6a571-106">Syntax</span></span>

### <span data-ttu-id="6a571-107">ScriptBlockSet (standard)</span><span class="sxs-lookup"><span data-stu-id="6a571-107">ScriptBlockSet (Default)</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6a571-108">PropertyAndMethodSet</span><span class="sxs-lookup"><span data-stu-id="6a571-108">PropertyAndMethodSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6a571-109">ParallelParameterSet</span><span class="sxs-lookup"><span data-stu-id="6a571-109">ParallelParameterSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] -Parallel <ScriptBlock> [-ThrottleLimit <Int32>]
 [-TimeoutSeconds <Int32>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6a571-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6a571-110">Description</span></span>

<span data-ttu-id="6a571-111">`ForEach-Object`Cmdleten utför en åtgärd på varje objekt i en samling inobjekt.</span><span class="sxs-lookup"><span data-stu-id="6a571-111">The `ForEach-Object` cmdlet performs an operation on each item in a collection of input objects.</span></span> <span data-ttu-id="6a571-112">Objekten kan skickas till cmdleten eller anges med parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="6a571-112">The input objects can be piped to the cmdlet or specified by using the **InputObject** parameter.</span></span>

<span data-ttu-id="6a571-113">Från och med Windows PowerShell 3,0 finns det två olika sätt att skapa ett `ForEach-Object` kommando.</span><span class="sxs-lookup"><span data-stu-id="6a571-113">Starting in Windows PowerShell 3.0, there are two different ways to construct a `ForEach-Object` command.</span></span>

- <span data-ttu-id="6a571-114">**Skript block**.</span><span class="sxs-lookup"><span data-stu-id="6a571-114">**Script block**.</span></span> <span data-ttu-id="6a571-115">Du kan använda ett-skript block för att ange åtgärden.</span><span class="sxs-lookup"><span data-stu-id="6a571-115">You can use a script block to specify the operation.</span></span> <span data-ttu-id="6a571-116">I-skript blocket använder du `$_` variabeln för att representera det aktuella objektet.</span><span class="sxs-lookup"><span data-stu-id="6a571-116">Within the script block, use the `$_` variable to represent the current object.</span></span> <span data-ttu-id="6a571-117">Skript blocket är värdet för **process** parametern.</span><span class="sxs-lookup"><span data-stu-id="6a571-117">The script block is the value of the **Process** parameter.</span></span> <span data-ttu-id="6a571-118">Skript blocket kan innehålla alla PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="6a571-118">The script block can contain any PowerShell script.</span></span>

  <span data-ttu-id="6a571-119">Till exempel hämtar följande kommando värdet för egenskapen **processname** för varje process på datorn.</span><span class="sxs-lookup"><span data-stu-id="6a571-119">For example, the following command gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object {$_.ProcessName}`

  <span data-ttu-id="6a571-120">`ForEach-Object` stöder `begin` -, `process` -och- `end` blocken enligt beskrivningen i [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="6a571-120">`ForEach-Object` supports the `begin`, `process`, and `end` blocks as described in [about_functions](about/about_functions.md#piping-objects-to-functions).</span></span>

  > [!NOTE]
  > <span data-ttu-id="6a571-121">Skript blocken körs i anroparens omfång.</span><span class="sxs-lookup"><span data-stu-id="6a571-121">The script blocks run in the caller's scope.</span></span> <span data-ttu-id="6a571-122">Därför har blocken åtkomst till variabler i det omfånget och kan skapa nya variabler som finns kvar i det omfånget när cmdleten har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6a571-122">Therefore the blocks have access to variables in that scope and can create new variables that persist in that scope after the cmdlet completes.</span></span>

- <span data-ttu-id="6a571-123">**Åtgärds uttryck**.</span><span class="sxs-lookup"><span data-stu-id="6a571-123">**Operation statement**.</span></span> <span data-ttu-id="6a571-124">Du kan också skriva en åtgärds instruktion, som är mycket mer likt naturligt språk.</span><span class="sxs-lookup"><span data-stu-id="6a571-124">You can also write an operation statement, which is much more like natural language.</span></span> <span data-ttu-id="6a571-125">Du kan använda instruktionen operation för att ange ett egenskaps värde eller anropa en metod.</span><span class="sxs-lookup"><span data-stu-id="6a571-125">You can use the operation statement to specify a property value or call a method.</span></span> <span data-ttu-id="6a571-126">Åtgärds instruktioner introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a571-126">Operation statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="6a571-127">Följande kommando hämtar till exempel också värdet för egenskapen **processname** för varje process på datorn.</span><span class="sxs-lookup"><span data-stu-id="6a571-127">For example, the following command also gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object ProcessName`

- <span data-ttu-id="6a571-128">**Parallellt skript block som körs**.</span><span class="sxs-lookup"><span data-stu-id="6a571-128">**Parallel running script block**.</span></span> <span data-ttu-id="6a571-129">Från och med PowerShell 7,0 är en tredje parameter uppsättning tillgänglig som kör varje skript block parallellt.</span><span class="sxs-lookup"><span data-stu-id="6a571-129">Beginning with PowerShell 7.0, a third parameter set is available that runs each script block in parallel.</span></span> <span data-ttu-id="6a571-130">Parametern **ThrottleLimit** begränsar antalet parallella skript som körs i taget.</span><span class="sxs-lookup"><span data-stu-id="6a571-130">The **ThrottleLimit** parameter limits the number of parallel scripts running at a time.</span></span> <span data-ttu-id="6a571-131">Som tidigare använder du `$_` variabeln för att representera det aktuella inobjektet i skript blocket.</span><span class="sxs-lookup"><span data-stu-id="6a571-131">As before, use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="6a571-132">Använd `$using:` nyckelordet för att skicka variabel referenser till skriptet som körs.</span><span class="sxs-lookup"><span data-stu-id="6a571-132">Use the `$using:` keyword to pass variable references to the running script.</span></span>

  <span data-ttu-id="6a571-133">I PowerShell 7 skapas en ny körnings utrymme för varje upprepnings slinga för att säkerställa maximal isolering.</span><span class="sxs-lookup"><span data-stu-id="6a571-133">In PowerShell 7, a new runspace is created for each loop iteration to ensure maximum isolation.</span></span>
  <span data-ttu-id="6a571-134">Detta kan vara en stor prestanda-och resurs träff om det arbete du gör är litet jämfört med att skapa nya körnings utrymmen eller om det finns många iterationer som utför betydande arbete.</span><span class="sxs-lookup"><span data-stu-id="6a571-134">This can be a large performance and resource hit if the work you are doing is small compared to creating new runspaces or if there are a lot of iterations performing significant work.</span></span>

  <span data-ttu-id="6a571-135">Som standard använder parallell scriptblocks den aktuella arbets katalogen för den anropare som startade parallell aktiviteterna.</span><span class="sxs-lookup"><span data-stu-id="6a571-135">By default, the parallel scriptblocks use the current working directory of the caller that started the parallel tasks.</span></span>

  <span data-ttu-id="6a571-136">Icke-avslutande fel skrivs till cmdlet: en fel ström när de inträffar parallellt med scriptblocks.</span><span class="sxs-lookup"><span data-stu-id="6a571-136">Non-terminating errors are written to the cmdlet error stream as they occur in parallel running scriptblocks.</span></span> <span data-ttu-id="6a571-137">Eftersom parallell script block inte kan fastställas, är ordningen i vilken fel visas i fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="6a571-137">Because parallel scriptblock execution order cannot be determined, the order in which errors appear in the error stream is random.</span></span> <span data-ttu-id="6a571-138">På samma sätt skrivs meddelanden som skrivs till andra data strömmar som varning, utförligt eller information till dessa data strömmar i en obestämd ordning.</span><span class="sxs-lookup"><span data-stu-id="6a571-138">Likewise, messages written to other data streams, like warning, verbose, or information are written to those data streams in an indeterminate order.</span></span>

  <span data-ttu-id="6a571-139">Om du avslutar fel, till exempel undantag, avslutar du den enskilda parallella instansen av scriptblocks där de förekommer.</span><span class="sxs-lookup"><span data-stu-id="6a571-139">Terminating errors, such as exceptions, terminate the individual parallel instance of the scriptblocks in which they occur.</span></span> <span data-ttu-id="6a571-140">Ett avslutande fel i en scriptblocks kan inte leda till att `Foreach-Object` cmdleten avslutas.</span><span class="sxs-lookup"><span data-stu-id="6a571-140">A terminating error in one scriptblocks may not cause the termination of the `Foreach-Object` cmdlet.</span></span> <span data-ttu-id="6a571-141">De andra scriptblocks, som körs parallellt, fortsätter att köras om de inte också påträffar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="6a571-141">The other scriptblocks, running in parallel, continue to run unless they also encounter a terminating error.</span></span> <span data-ttu-id="6a571-142">Det avslutande felet skrivs till fel data strömmen som en **ErrorRecord** med **FullyQualifiedErrorId** `PSTaskException` .</span><span class="sxs-lookup"><span data-stu-id="6a571-142">The terminating error is written to the error data stream as an **ErrorRecord** with a **FullyQualifiedErrorId** of `PSTaskException`.</span></span>
  <span data-ttu-id="6a571-143">Avslutande fel kan konverteras till icke-avslutande fel med hjälp av PowerShell-try/catch-eller trap-block.</span><span class="sxs-lookup"><span data-stu-id="6a571-143">Terminating errors can be converted to non-terminating errors using PowerShell try/catch or trap blocks.</span></span>

## <span data-ttu-id="6a571-144">Exempel</span><span class="sxs-lookup"><span data-stu-id="6a571-144">Examples</span></span>

### <span data-ttu-id="6a571-145">Exempel 1: dividera heltal i en matris</span><span class="sxs-lookup"><span data-stu-id="6a571-145">Example 1: Divide integers in an array</span></span>

<span data-ttu-id="6a571-146">Det här exemplet tar en matris med tre heltal och dividerar var och en av dem med 1024.</span><span class="sxs-lookup"><span data-stu-id="6a571-146">This example takes an array of three integers and divides each one of them by 1024.</span></span>

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### <span data-ttu-id="6a571-147">Exempel 2: Hämta längden på alla filer i en katalog</span><span class="sxs-lookup"><span data-stu-id="6a571-147">Example 2: Get the length of all the files in a directory</span></span>

<span data-ttu-id="6a571-148">I det här exemplet behandlas filerna och katalogerna i installations katalogen för PowerShell `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="6a571-148">This example processes the files and directories in the PowerShell installation directory `$PSHOME`.</span></span>

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

<span data-ttu-id="6a571-149">Om objektet inte är en katalog får skript blocket namnet på filen, dividerar värdet för egenskapen **length** med 1024 och lägger till ett blank steg ("") för att skilja det från nästa post.</span><span class="sxs-lookup"><span data-stu-id="6a571-149">If the object is not a directory, the script block gets the name of the file, divides the value of its **Length** property by 1024, and adds a space (" ") to separate it from the next entry.</span></span> <span data-ttu-id="6a571-150">Cmdleten använder egenskapen **PSISContainer** för att avgöra om ett objekt är en katalog.</span><span class="sxs-lookup"><span data-stu-id="6a571-150">The cmdlet uses the **PSISContainer** property to determine whether an object is a directory.</span></span>

### <span data-ttu-id="6a571-151">Exempel 3: arbeta med de senaste system händelserna</span><span class="sxs-lookup"><span data-stu-id="6a571-151">Example 3: Operate on the most recent System events</span></span>

<span data-ttu-id="6a571-152">Det här exemplet skriver de senaste 1000 händelserna från systemets händelse logg till en textfil.</span><span class="sxs-lookup"><span data-stu-id="6a571-152">This example writes the 1000 most recent events from the System event log to a text file.</span></span> <span data-ttu-id="6a571-153">Aktuell tid visas före och efter bearbetning av händelser.</span><span class="sxs-lookup"><span data-stu-id="6a571-153">The current time is displayed before and after processing the events.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

<span data-ttu-id="6a571-154">`Get-EventLog` hämtar de senaste 1000 händelserna från system händelse loggen och lagrar dem i `$Events` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6a571-154">`Get-EventLog` gets the 1000 most recent events from the System event log and stores them in the `$Events` variable.</span></span> <span data-ttu-id="6a571-155">`$Events` skickas sedan till `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a571-155">`$Events` is then piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="6a571-156">Parametern **BEGIN** visar aktuellt datum och tid.</span><span class="sxs-lookup"><span data-stu-id="6a571-156">The **Begin** parameter displays the current date and time.</span></span> <span data-ttu-id="6a571-157">Därefter använder **process** -parametern `Out-File` cmdleten för att skapa en textfil med namnet events.txt och lagrar meddelande egenskapen för varje händelse i filen.</span><span class="sxs-lookup"><span data-stu-id="6a571-157">Next, the **Process** parameter uses the `Out-File` cmdlet to create a text file that is named events.txt and stores the message property of each of the events in that file.</span></span> <span data-ttu-id="6a571-158">Sist används parametern **End** för att visa datum och tid när all bearbetning har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6a571-158">Last, the **End** parameter is used to display the date and time after all of the processing has completed.</span></span>

### <span data-ttu-id="6a571-159">Exempel 4: ändra värdet för en register nyckel</span><span class="sxs-lookup"><span data-stu-id="6a571-159">Example 4: Change the value of a Registry key</span></span>

<span data-ttu-id="6a571-160">Det här exemplet ändrar värdet för register posten **remotePath** i alla under nycklar under `HKCU:\Network` nyckeln till versal text.</span><span class="sxs-lookup"><span data-stu-id="6a571-160">This example changes the value of the **RemotePath** registry entry in all of the subkeys under the `HKCU:\Network` key to uppercase text.</span></span>

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

<span data-ttu-id="6a571-161">Du kan använda det här formatet för att ändra formuläret eller innehållet i ett register post värde.</span><span class="sxs-lookup"><span data-stu-id="6a571-161">You can use this format to change the form or content of a registry entry value.</span></span>

<span data-ttu-id="6a571-162">Varje under nyckel i **nätverks** nyckeln representerar en mappad nätverks enhet som återansluter vid inloggning.</span><span class="sxs-lookup"><span data-stu-id="6a571-162">Each subkey in the **Network** key represents a mapped network drive that reconnects at sign on.</span></span> <span data-ttu-id="6a571-163">**RemotePath** -posten innehåller UNC-sökvägen till den anslutna enheten.</span><span class="sxs-lookup"><span data-stu-id="6a571-163">The **RemotePath** entry contains the UNC path of the connected drive.</span></span> <span data-ttu-id="6a571-164">Om du till exempel mappar E: enheten till `\\Server\Share` skapas en **E** -postnyckel i `HKCU:\Network` med register värde för **remotePath** inställt på `\\Server\Share` .</span><span class="sxs-lookup"><span data-stu-id="6a571-164">For example, if you map the E: drive to `\\Server\Share`, an **E** subkey is created in `HKCU:\Network` with the **RemotePath** registry value set to `\\Server\Share`.</span></span>

<span data-ttu-id="6a571-165">Kommandot använder `Get-ItemProperty` cmdleten för att hämta alla under nycklar för **nätverks** nyckeln och `Set-ItemProperty` cmdleten för att ändra värdet för register posten **remotePath** i varje nyckel.</span><span class="sxs-lookup"><span data-stu-id="6a571-165">The command uses the `Get-ItemProperty` cmdlet to get all of the subkeys of the **Network** key and the `Set-ItemProperty` cmdlet to change the value of the **RemotePath** registry entry in each key.</span></span>
<span data-ttu-id="6a571-166">I `Set-ItemProperty` kommandot är sökvägen värdet för egenskapen **PSPath** i register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="6a571-166">In the `Set-ItemProperty` command, the path is the value of the **PSPath** property of the registry key.</span></span> <span data-ttu-id="6a571-167">Detta är en egenskap för det Microsoft .NET Framework-objekt som representerar register nyckeln, inte en register post.</span><span class="sxs-lookup"><span data-stu-id="6a571-167">This is a property of the Microsoft .NET Framework object that represents the registry key, not a registry entry.</span></span> <span data-ttu-id="6a571-168">Kommandot använder metoden **ToUpper ()** i **remotePath** -värdet, som är en sträng (REG_SZ).</span><span class="sxs-lookup"><span data-stu-id="6a571-168">The command uses the **ToUpper()** method of the **RemotePath** value, which is a string (REG_SZ).</span></span>

<span data-ttu-id="6a571-169">Eftersom `Set-ItemProperty` ändrar egenskapen för varje nyckel, `ForEach-Object` krävs cmdleten för att komma åt egenskapen.</span><span class="sxs-lookup"><span data-stu-id="6a571-169">Because `Set-ItemProperty` is changing the property of each key, the `ForEach-Object` cmdlet is required to access the property.</span></span>

### <span data-ttu-id="6a571-170">Exempel 5: Använd den automatiska variabeln $Null</span><span class="sxs-lookup"><span data-stu-id="6a571-170">Example 5: Use the $Null automatic variable</span></span>

<span data-ttu-id="6a571-171">I det här exemplet visas en funktion för att skicka den `$Null` automatiska variabeln till `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a571-171">This example shows the effect of piping the `$Null` automatic variable to the `ForEach-Object` cmdlet.</span></span>

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

<span data-ttu-id="6a571-172">Eftersom PowerShell behandlar null som en explicit plats hållare, `ForEach-Object` genererar cmdleten ett värde för `$Null` , precis som för andra objekt som du skickar till den.</span><span class="sxs-lookup"><span data-stu-id="6a571-172">Because PowerShell treats null as an explicit placeholder, the `ForEach-Object` cmdlet generates a value for `$Null`, just as it does for other objects that you pipe to it.</span></span>

### <span data-ttu-id="6a571-173">Exempel 6: Hämta egenskaps värden</span><span class="sxs-lookup"><span data-stu-id="6a571-173">Example 6: Get property values</span></span>

<span data-ttu-id="6a571-174">I det här exemplet hämtas värdet för egenskapen **sökväg** för alla installerade PowerShell-moduler med hjälp av parametern **MemberName** för `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a571-174">This example gets the value of the **Path** property of all installed PowerShell modules by using the **MemberName** parameter of the `ForEach-Object` cmdlet.</span></span>

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

<span data-ttu-id="6a571-175">Det andra kommandot motsvarar det första.</span><span class="sxs-lookup"><span data-stu-id="6a571-175">The second command is equivalent to the first.</span></span> <span data-ttu-id="6a571-176">Det använder `Foreach` aliaset för `ForEach-Object` cmdleten och utelämnar namnet på parametern **MemberName** , som är valfritt.</span><span class="sxs-lookup"><span data-stu-id="6a571-176">It uses the `Foreach` alias of the `ForEach-Object` cmdlet and omits the name of the **MemberName** parameter, which is optional.</span></span>

<span data-ttu-id="6a571-177">`ForEach-Object`Cmdleten är användbar för att hämta egenskaps värden, eftersom den hämtar värdet utan att ändra typen, till skillnad från **format** -cmdletar eller `Select-Object` cmdleten, som ändrar värde typen för egenskapen.</span><span class="sxs-lookup"><span data-stu-id="6a571-177">The `ForEach-Object` cmdlet is useful for getting property values, because it gets the value without changing the type, unlike the **Format** cmdlets or the `Select-Object` cmdlet, which change the property value type.</span></span>

### <span data-ttu-id="6a571-178">Exempel 7: dela Modulnamn i namn på komponenter</span><span class="sxs-lookup"><span data-stu-id="6a571-178">Example 7: Split module names into component names</span></span>

<span data-ttu-id="6a571-179">Det här exemplet visar tre sätt att dela två punktavgränsade modulnamn till sina komponent namn.</span><span class="sxs-lookup"><span data-stu-id="6a571-179">This example shows three ways to split two dot-separated module names into their component names.</span></span>

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

<span data-ttu-id="6a571-180">Kommandona anropar **delnings** metoden för strängar.</span><span class="sxs-lookup"><span data-stu-id="6a571-180">The commands call the **Split** method of strings.</span></span> <span data-ttu-id="6a571-181">De tre kommandona använder olika syntax, men de är likvärdiga och utbytbara.</span><span class="sxs-lookup"><span data-stu-id="6a571-181">The three commands use different syntax, but they are equivalent and interchangeable.</span></span>

<span data-ttu-id="6a571-182">Det första kommandot använder den traditionella syntaxen, som innehåller ett skript block och den aktuella objekt operatorn `$_` .</span><span class="sxs-lookup"><span data-stu-id="6a571-182">The first command uses the traditional syntax, which includes a script block and the current object operator `$_`.</span></span> <span data-ttu-id="6a571-183">Den använder punktsyntax för att ange den metod och den parentes som ska omges av argumentet avgränsnings uttryck.</span><span class="sxs-lookup"><span data-stu-id="6a571-183">It uses the dot syntax to specify the method and parentheses to enclose the delimiter argument.</span></span>

<span data-ttu-id="6a571-184">Det andra kommandot använder parametern **MemberName** för att ange metoden **Split** och parametern **ArgumentName** för att identifiera punkten (".") som uppdelnings avgränsare.</span><span class="sxs-lookup"><span data-stu-id="6a571-184">The second command uses the **MemberName** parameter to specify the **Split** method and the **ArgumentName** parameter to identify the dot (".") as the split delimiter.</span></span>

<span data-ttu-id="6a571-185">Det tredje kommandot använder **förgrunds** Ali Aset för `ForEach-Object` cmdleten och utelämnar Namnen på parametrarna **MemberName** och **argument List** , som är valfria.</span><span class="sxs-lookup"><span data-stu-id="6a571-185">The third command uses the **Foreach** alias of the `ForEach-Object` cmdlet and omits the names of the **MemberName** and **ArgumentList** parameters, which are optional.</span></span>

### <span data-ttu-id="6a571-186">Exempel 8: använda ForEach-Object med två skript block</span><span class="sxs-lookup"><span data-stu-id="6a571-186">Example 8: Using ForEach-Object with two script blocks</span></span>

<span data-ttu-id="6a571-187">I det här exemplet skickar vi två skript block i position.</span><span class="sxs-lookup"><span data-stu-id="6a571-187">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="6a571-188">Alla skript block binder till **process** parametern.</span><span class="sxs-lookup"><span data-stu-id="6a571-188">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="6a571-189">De behandlas dock som om de hade skickats till parametrarna **BEGIN** och **process** .</span><span class="sxs-lookup"><span data-stu-id="6a571-189">However, they are treated as if they had been passed to the **Begin** and **Process** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### <span data-ttu-id="6a571-190">Exempel 9: använda ForEach-Object med fler än två skript block</span><span class="sxs-lookup"><span data-stu-id="6a571-190">Example 9: Using ForEach-Object with more than two script blocks</span></span>

<span data-ttu-id="6a571-191">I det här exemplet skickar vi två skript block i position.</span><span class="sxs-lookup"><span data-stu-id="6a571-191">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="6a571-192">Alla skript block binder till **process** parametern.</span><span class="sxs-lookup"><span data-stu-id="6a571-192">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="6a571-193">De behandlas dock som om de hade skickats till parametrarna **BEGIN**, **process** och **End** .</span><span class="sxs-lookup"><span data-stu-id="6a571-193">However, they are treated as if they had been passed to the **Begin**, **Process**, and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> <span data-ttu-id="6a571-194">Det första skript blocket mappas alltid till `begin` blocket, det sista blocket mappas till `end` blocket och blocken mellan är alla mappade till `process` blocket.</span><span class="sxs-lookup"><span data-stu-id="6a571-194">The first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

### <span data-ttu-id="6a571-195">Exempel 10: kör flera skript block för varje pipeline-objekt</span><span class="sxs-lookup"><span data-stu-id="6a571-195">Example 10: Run multiple script blocks for each pipeline item</span></span>

<span data-ttu-id="6a571-196">Som du ser i det föregående exemplet har flera skript block som skickas med **process** parametern mappats till **Start** -och **slut** parametrarna.</span><span class="sxs-lookup"><span data-stu-id="6a571-196">As shown in the previous example, multiple script blocks passed using the **Process** parameter get mapped to the **Begin** and **End** parameters.</span></span> <span data-ttu-id="6a571-197">För att undvika den här mappningen måste du ange explicita värden för **Start** -och **slut** parametrarna.</span><span class="sxs-lookup"><span data-stu-id="6a571-197">To avoid this mapping, you must provide explicit values for the **Begin** and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

### <span data-ttu-id="6a571-198">Exempel 11: kör långsamt skript i parallella batchar</span><span class="sxs-lookup"><span data-stu-id="6a571-198">Example 11: Run slow script in parallel batches</span></span>

<span data-ttu-id="6a571-199">I det här exemplet körs ett enkelt skript block som utvärderar en sträng och vilo läge för en sekund.</span><span class="sxs-lookup"><span data-stu-id="6a571-199">This example runs a simple script block that evaluates a string and sleeps for one second.</span></span>

```powershell
$Message = "Output:"

1..8 | ForEach-Object -Parallel {
    "$using:Message $_"
    Start-Sleep 1
} -ThrottleLimit 4
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
```

<span data-ttu-id="6a571-200">Värdet för parametern **ThrottleLimit** anges till 4 så att indatamängden bearbetas i batchar med fyra.</span><span class="sxs-lookup"><span data-stu-id="6a571-200">The **ThrottleLimit** parameter value is set to 4 so that the input is processed in batches of four.</span></span>
<span data-ttu-id="6a571-201">`$using:`Nyckelordet används för att skicka `$Message` variabeln till varje parallellt skript block.</span><span class="sxs-lookup"><span data-stu-id="6a571-201">The `$using:` keyword is used to pass the `$Message` variable into each parallel script block.</span></span>

### <span data-ttu-id="6a571-202">Exempel 12: Hämta logg poster parallellt</span><span class="sxs-lookup"><span data-stu-id="6a571-202">Example 12: Retrieve log entries in parallel</span></span>

<span data-ttu-id="6a571-203">I det här exemplet hämtas logg poster 50 000 från 5 system loggar på en lokal Windows-dator.</span><span class="sxs-lookup"><span data-stu-id="6a571-203">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine.</span></span>

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count
```

```Output
50000
```

<span data-ttu-id="6a571-204">Den **parallella** parametern anger det skript block som körs parallellt för varje logg namn.</span><span class="sxs-lookup"><span data-stu-id="6a571-204">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span> <span data-ttu-id="6a571-205">Parametern **ThrottleLimit** säkerställer att alla fem skript block körs samtidigt.</span><span class="sxs-lookup"><span data-stu-id="6a571-205">The **ThrottleLimit** parameter ensures that all five script blocks run at the same time.</span></span>

### <span data-ttu-id="6a571-206">Exempel 13: kör parallellt som ett jobb</span><span class="sxs-lookup"><span data-stu-id="6a571-206">Example 13: Run in parallel as a job</span></span>

<span data-ttu-id="6a571-207">I det här exemplet körs ett enkelt skript block parallellt, vilket skapar två bakgrunds jobb i taget.</span><span class="sxs-lookup"><span data-stu-id="6a571-207">This example runs a simple script block in parallel, creating two background jobs at a time.</span></span>

```powershell
$job = 1..10 | ForEach-Object -Parallel {
    "Output: $_"
    Start-Sleep 1
} -ThrottleLimit 2 -AsJob

$job | Receive-Job -Wait
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
Output: 9
Output: 10
```

<span data-ttu-id="6a571-208">`$job`variabeln tar emot jobbobjektet som samlar in utmatnings data och övervakar körnings tillstånd.</span><span class="sxs-lookup"><span data-stu-id="6a571-208">the `$job` variable receives the job object that collects output data and monitors running state.</span></span>
<span data-ttu-id="6a571-209">Jobbobjektet är skickas till `Receive-Job` med parametern **väntande** switch.</span><span class="sxs-lookup"><span data-stu-id="6a571-209">The job object is piped to `Receive-Job` with the **Wait** switch parameter.</span></span> <span data-ttu-id="6a571-210">Och detta strömmar utdata till-konsolen, precis som om `ForEach-Object -Parallel` kördes utan **AsJob**.</span><span class="sxs-lookup"><span data-stu-id="6a571-210">And this streams output to the console, just as if `ForEach-Object -Parallel` was run without **AsJob**.</span></span>

### <span data-ttu-id="6a571-211">Exempel 14: använda tråd säkra variabel referenser</span><span class="sxs-lookup"><span data-stu-id="6a571-211">Example 14: Using thread safe variable references</span></span>

<span data-ttu-id="6a571-212">I det här exemplet anropas skript block parallellt för att samla in unika namngivna process objekt.</span><span class="sxs-lookup"><span data-stu-id="6a571-212">This example invokes script blocks in parallel to collect uniquely named Process objects.</span></span>

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
Get-Process | ForEach-Object -Parallel {
    $dict = $using:threadSafeDictionary
    $dict.TryAdd($_.ProcessName, $_)
}

$threadSafeDictionary["pwsh"]
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     82    82.87     130.85      15.55    2808   2 pwsh
```

<span data-ttu-id="6a571-213">En enda instans av ett **ConcurrentDictionary** -objekt skickas till varje skript block för att samla in objekten.</span><span class="sxs-lookup"><span data-stu-id="6a571-213">A single instance of a **ConcurrentDictionary** object is passed to each script block to collect the objects.</span></span> <span data-ttu-id="6a571-214">Eftersom **ConcurrentDictionary** är tråd säker, är det säkert att modifieras av varje parallellt skript.</span><span class="sxs-lookup"><span data-stu-id="6a571-214">Since the **ConcurrentDictionary** is thread safe, it is safe to be modified by each parallel script.</span></span> <span data-ttu-id="6a571-215">Ett icke-tråd säkert objekt, t. ex **. system. Collections. Generic. Dictionary**, är inte säkert att använda här.</span><span class="sxs-lookup"><span data-stu-id="6a571-215">A non-thread-safe object, such as **System.Collections.Generic.Dictionary**, would not be safe to use here.</span></span>

> [!NOTE]
> <span data-ttu-id="6a571-216">Det här exemplet är en mycket ineffektiv användning av **parallell** parameter.</span><span class="sxs-lookup"><span data-stu-id="6a571-216">This example is a very inefficient use of **Parallel** parameter.</span></span> <span data-ttu-id="6a571-217">Skriptet lägger bara till inobjektet i ett objekt i en samtidig ord lista.</span><span class="sxs-lookup"><span data-stu-id="6a571-217">The script simply adds the input object to a concurrent dictionary object.</span></span> <span data-ttu-id="6a571-218">Det är enkelt och inte värt omkostnaderna för att anropa varje skript i en separat tråd.</span><span class="sxs-lookup"><span data-stu-id="6a571-218">It is trivial and not worth the overhead of invoking each script in a separate thread.</span></span> <span data-ttu-id="6a571-219">`ForEach-Object`Att köras normalt utan att den **parallella** växeln är mycket effektivare och snabbare.</span><span class="sxs-lookup"><span data-stu-id="6a571-219">Running `ForEach-Object` normally without the **Parallel** switch is much more efficient and faster.</span></span> <span data-ttu-id="6a571-220">Det här exemplet är endast avsett för att visa hur du använder tråd säkra variabler.</span><span class="sxs-lookup"><span data-stu-id="6a571-220">This example is only intended to demonstrate how to use thread safe variables.</span></span>

### <span data-ttu-id="6a571-221">Exempel 15: skrivfel med parallell körning</span><span class="sxs-lookup"><span data-stu-id="6a571-221">Example 15: Writing errors with parallel execution</span></span>

<span data-ttu-id="6a571-222">Det här exemplet skriver till fel strömmen parallellt, där ordningen på skrivna fel är slumpmässig.</span><span class="sxs-lookup"><span data-stu-id="6a571-222">This example writes to the error stream in parallel, where the order of written errors is random.</span></span>

```powershell
1..3 | ForEach-Object -Parallel {
    Write-Error "Error: $_"
}
```

```Output
Write-Error: Error: 1
Write-Error: Error: 3
Write-Error: Error: 2
```

### <span data-ttu-id="6a571-223">Exempel 16: avbryta fel vid parallell körning</span><span class="sxs-lookup"><span data-stu-id="6a571-223">Example 16: Terminating errors in parallel execution</span></span>

<span data-ttu-id="6a571-224">Det här exemplet visar ett avslutande fel i en parallell script block.</span><span class="sxs-lookup"><span data-stu-id="6a571-224">This example demonstrates a terminating error in one parallel running scriptblock.</span></span>

```powershell
1..5 | ForEach-Object -Parallel {
    if ($_ -eq 3)
    {
        throw "Terminating Error: $_"
    }

    Write-Output "Output: $_"
}
```

```Output
Exception: Terminating Error: 3
Output: 1
Output: 4
Output: 2
Output: 5
```

<span data-ttu-id="6a571-225">`Output: 3` skrivs aldrig eftersom parallellt script block för den iterationen avbröts.</span><span class="sxs-lookup"><span data-stu-id="6a571-225">`Output: 3` is never written because the parallel scriptblock for that iteration was terminated.</span></span>

### <span data-ttu-id="6a571-226">Exempel 17: skicka variabler i kapslade parallella skript ScriptBlockSet</span><span class="sxs-lookup"><span data-stu-id="6a571-226">Example 17: Passing variables in nested parallel script ScriptBlockSet</span></span>

<span data-ttu-id="6a571-227">Du kan skapa en variabel utanför en `Foreach-Object -Parallel` omfångs script block och använda den inuti script block med `$using` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="6a571-227">You can create a variable outside a `Foreach-Object -Parallel` scoped scriptblock and use it inside the scriptblock with the `$using` keyword.</span></span>

```powershell
$test1 = 'TestA'
1..2 | Foreach-Object -Parallel {
    $using:test1
}
```

```Output
TestA
TestA
```

```powershell
# You CANNOT create a variable inside a scoped scriptblock
# to be used in a nested foreach parallel scriptblock.
$test1 = 'TestA'
1..2 | Foreach-Object -Parallel {
    $using:test1
    $test2 = 'TestB'
    1..2 | Foreach-Object -Parallel {
        $using:test2
    }
}
```

```Output
Line |
   2 |  1..2 | Foreach-Object -Parallel {
     |         ~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The value of the using variable '$using:test2' cannot be retrieved because it has not been set in the local session.
```

<span data-ttu-id="6a571-228">Den kapslade script block kan inte komma åt `$test2` variabeln och ett fel genereras.</span><span class="sxs-lookup"><span data-stu-id="6a571-228">The nested scriptblock can't access the `$test2` variable and an error is thrown.</span></span>

## <span data-ttu-id="6a571-229">Parametrar</span><span class="sxs-lookup"><span data-stu-id="6a571-229">Parameters</span></span>

### <span data-ttu-id="6a571-230">– Argument List</span><span class="sxs-lookup"><span data-stu-id="6a571-230">-ArgumentList</span></span>

<span data-ttu-id="6a571-231">Anger en matris med argument till ett metod anrop.</span><span class="sxs-lookup"><span data-stu-id="6a571-231">Specifies an array of arguments to a method call.</span></span> <span data-ttu-id="6a571-232">Mer information om beteendet för **argument List** finns [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="6a571-232">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="6a571-233">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a571-233">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a571-234">– Börja</span><span class="sxs-lookup"><span data-stu-id="6a571-234">-Begin</span></span>

<span data-ttu-id="6a571-235">Anger ett skript block som körs innan denna cmdlet bearbetar eventuella inobjekt.</span><span class="sxs-lookup"><span data-stu-id="6a571-235">Specifies a script block that runs before this cmdlet processes any input objects.</span></span> <span data-ttu-id="6a571-236">Det här skript blocket körs bara en gång för hela pipelinen.</span><span class="sxs-lookup"><span data-stu-id="6a571-236">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="6a571-237">Mer information om `begin` blocket finns [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="6a571-237">For more information about the `begin` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a571-238">-Slut</span><span class="sxs-lookup"><span data-stu-id="6a571-238">-End</span></span>

<span data-ttu-id="6a571-239">Anger ett skript block som körs när denna cmdlet bearbetar alla inobjekt.</span><span class="sxs-lookup"><span data-stu-id="6a571-239">Specifies a script block that runs after this cmdlet processes all input objects.</span></span> <span data-ttu-id="6a571-240">Det här skript blocket körs bara en gång för hela pipelinen.</span><span class="sxs-lookup"><span data-stu-id="6a571-240">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="6a571-241">Mer information om `end` blocket finns [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="6a571-241">For more information about the `end` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a571-242">– InputObject</span><span class="sxs-lookup"><span data-stu-id="6a571-242">-InputObject</span></span>

<span data-ttu-id="6a571-243">Anger ingående objekt.</span><span class="sxs-lookup"><span data-stu-id="6a571-243">Specifies the input objects.</span></span> <span data-ttu-id="6a571-244">`ForEach-Object` Kör skript blocket eller instruktions satsen för varje indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="6a571-244">`ForEach-Object` runs the script block or operation statement on each input object.</span></span> <span data-ttu-id="6a571-245">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="6a571-245">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="6a571-246">När du använder parametern **InputObject** i `ForEach-Object` , i stället för Skicka kommando resultat till `ForEach-Object` , behandlas **InputObject** -värdet som ett enskilt objekt.</span><span class="sxs-lookup"><span data-stu-id="6a571-246">When you use the **InputObject** parameter with `ForEach-Object`, instead of piping command results to `ForEach-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="6a571-247">Detta gäller även om värdet är en samling som är resultatet av ett kommando, till exempel `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="6a571-247">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span>
<span data-ttu-id="6a571-248">Eftersom **InputObject** inte kan returnera enskilda egenskaper från en matris eller samling objekt, rekommenderar vi att om du använder `ForEach-Object` för att utföra åtgärder på en samling objekt för de objekt som har specifika värden i definierade egenskaper, använder du `ForEach-Object` i pipelinen, som du ser i exemplen i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="6a571-248">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that if you use `ForEach-Object` to perform operations on a collection of objects for those objects that have specific values in defined properties, you use `ForEach-Object` in the pipeline, as shown in the examples in this topic.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6a571-249">– MemberName</span><span class="sxs-lookup"><span data-stu-id="6a571-249">-MemberName</span></span>

<span data-ttu-id="6a571-250">Anger den egenskap som ska hämtas eller metoden som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="6a571-250">Specifies the property to get or the method to call.</span></span>

<span data-ttu-id="6a571-251">Jokertecken är tillåtna men fungerar bara om den resulterande strängen matchar ett unikt värde.</span><span class="sxs-lookup"><span data-stu-id="6a571-251">Wildcard characters are permitted, but work only if the resulting string resolves to a unique value.</span></span>
<span data-ttu-id="6a571-252">Om du t. ex. kör `Get-Process | ForEach -MemberName *Name` , matchar jokertecken fler än en medlem som orsakar att kommandot kraschar.</span><span class="sxs-lookup"><span data-stu-id="6a571-252">For example, if you run `Get-Process | ForEach -MemberName *Name`, the wildcard pattern matches more than one member causing the command to fail.</span></span>

<span data-ttu-id="6a571-253">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a571-253">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6a571-254">– Process</span><span class="sxs-lookup"><span data-stu-id="6a571-254">-Process</span></span>

<span data-ttu-id="6a571-255">Anger den åtgärd som ska utföras för varje indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="6a571-255">Specifies the operation that is performed on each input object.</span></span> <span data-ttu-id="6a571-256">Det här skript blocket körs för varje objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="6a571-256">This script block is run for every object in the pipeline.</span></span> <span data-ttu-id="6a571-257">Mer information om `process` blocket finns [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="6a571-257">For more information about the `process` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

<span data-ttu-id="6a571-258">När du anger flera skript block till **process** parametern, mappas det första skript blocket alltid till `begin` blocket.</span><span class="sxs-lookup"><span data-stu-id="6a571-258">When you provide multiple script blocks to the **Process** parameter, the first script block is always mapped to the `begin` block.</span></span> <span data-ttu-id="6a571-259">Om det bara finns två skript block mappas det andra blocket till `process` blocket.</span><span class="sxs-lookup"><span data-stu-id="6a571-259">If there are only two script blocks, the second block is mapped to the `process` block.</span></span> <span data-ttu-id="6a571-260">Om det finns tre eller fler skript block mappas det första skript blocket alltid till `begin` blocket, det sista blocket mappas till `end` blocket och blocken mellan är alla mappade till `process` blocket.</span><span class="sxs-lookup"><span data-stu-id="6a571-260">If there are three or more script blocks, first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a571-261">-RemainingScripts</span><span class="sxs-lookup"><span data-stu-id="6a571-261">-RemainingScripts</span></span>

<span data-ttu-id="6a571-262">Anger alla skript block som inte tas av **process** parametern.</span><span class="sxs-lookup"><span data-stu-id="6a571-262">Specifies all script blocks that are not taken by the **Process** parameter.</span></span>

<span data-ttu-id="6a571-263">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a571-263">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a571-264">– Parallell</span><span class="sxs-lookup"><span data-stu-id="6a571-264">-Parallel</span></span>

<span data-ttu-id="6a571-265">Anger det skript block som ska användas för parallell bearbetning av indata-objekt.</span><span class="sxs-lookup"><span data-stu-id="6a571-265">Specifies the script block to be used for parallel processing of input objects.</span></span> <span data-ttu-id="6a571-266">Ange ett skript block som beskriver åtgärden.</span><span class="sxs-lookup"><span data-stu-id="6a571-266">Enter a script block that describes the operation.</span></span>

<span data-ttu-id="6a571-267">Den här parametern introducerades i PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="6a571-267">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ParallelParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a571-268">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6a571-268">-ThrottleLimit</span></span>

<span data-ttu-id="6a571-269">Anger antalet skript block parallellt.</span><span class="sxs-lookup"><span data-stu-id="6a571-269">Specifies the number of script blocks that in parallel.</span></span> <span data-ttu-id="6a571-270">Inmatade objekt blockeras tills det antal som körs är under **ThrottleLimit**.</span><span class="sxs-lookup"><span data-stu-id="6a571-270">Input objects are blocked until the running script block count falls below the **ThrottleLimit**.</span></span> <span data-ttu-id="6a571-271">Standardvärdet är `5`.</span><span class="sxs-lookup"><span data-stu-id="6a571-271">The default value is `5`.</span></span>

<span data-ttu-id="6a571-272">Den här parametern introducerades i PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="6a571-272">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a571-273">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="6a571-273">-TimeoutSeconds</span></span>

<span data-ttu-id="6a571-274">Anger antalet sekunder som ska förflyta för att alla inloggade inloggade ska bearbetas parallellt.</span><span class="sxs-lookup"><span data-stu-id="6a571-274">Specifies the number of seconds to wait for all input to be processed in parallel.</span></span> <span data-ttu-id="6a571-275">När tids gränsen har angetts stoppas alla skript som körs.</span><span class="sxs-lookup"><span data-stu-id="6a571-275">After the specified timeout time, all running scripts are stopped.</span></span> <span data-ttu-id="6a571-276">Och eventuella kvarvarande inobjekt som ska bearbetas ignoreras.</span><span class="sxs-lookup"><span data-stu-id="6a571-276">And any remaining input objects to be processed are ignored.</span></span> <span data-ttu-id="6a571-277">Standardvärdet `0` inaktiverar tids gränsen och `ForEach-Object -Parallel` kan köras på obestämd tid.</span><span class="sxs-lookup"><span data-stu-id="6a571-277">Default value of `0` disables the timeout, and `ForEach-Object -Parallel` can run indefinitely.</span></span> <span data-ttu-id="6a571-278">Om du skriver <kbd>CTRL</kbd> + <kbd>C</kbd> på kommando raden stoppas ett kommando som körs `ForEach-Object -Parallel` .</span><span class="sxs-lookup"><span data-stu-id="6a571-278">Typing <kbd>Ctrl</kbd>+<kbd>C</kbd> at the command line stops a running `ForEach-Object -Parallel` command.</span></span> <span data-ttu-id="6a571-279">Den här parametern kan inte användas tillsammans med parametern **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="6a571-279">This parameter cannot be used along with the **AsJob** parameter.</span></span>

<span data-ttu-id="6a571-280">Den här parametern introducerades i PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="6a571-280">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a571-281">– AsJob</span><span class="sxs-lookup"><span data-stu-id="6a571-281">-AsJob</span></span>

<span data-ttu-id="6a571-282">Orsakar parallell anrop att köras som ett PowerShell-jobb.</span><span class="sxs-lookup"><span data-stu-id="6a571-282">Causes the parallel invocation to run as a PowerShell job.</span></span> <span data-ttu-id="6a571-283">Ett enskilt jobb objekt returneras i stället för utdata från skript blocken som körs.</span><span class="sxs-lookup"><span data-stu-id="6a571-283">A single job object is returned instead of output from the running script blocks.</span></span> <span data-ttu-id="6a571-284">Jobbobjektet innehåller underordnade jobb för varje parallellt skript block som körs.</span><span class="sxs-lookup"><span data-stu-id="6a571-284">The job object contains child jobs for each parallel script block that runs.</span></span> <span data-ttu-id="6a571-285">Jobbobjektet kan användas av alla PowerShell-jobb-cmdletar för att övervaka körnings tillstånd och hämta data.</span><span class="sxs-lookup"><span data-stu-id="6a571-285">The job object can be used by all PowerShell job cmdlets, to monitor running state and retrieve data.</span></span>

<span data-ttu-id="6a571-286">Den här parametern introducerades i PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="6a571-286">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a571-287">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6a571-287">-Confirm</span></span>

<span data-ttu-id="6a571-288">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a571-288">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a571-289">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6a571-289">-WhatIf</span></span>

<span data-ttu-id="6a571-290">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="6a571-290">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6a571-291">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="6a571-291">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a571-292">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6a571-292">CommonParameters</span></span>

<span data-ttu-id="6a571-293">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6a571-293">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6a571-294">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6a571-294">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6a571-295">Indata</span><span class="sxs-lookup"><span data-stu-id="6a571-295">Inputs</span></span>

### <span data-ttu-id="6a571-296">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="6a571-296">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="6a571-297">Du kan skicka alla objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6a571-297">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="6a571-298">Utdata</span><span class="sxs-lookup"><span data-stu-id="6a571-298">Outputs</span></span>

### <span data-ttu-id="6a571-299">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="6a571-299">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="6a571-300">Denna cmdlet returnerar objekt som bestäms av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="6a571-300">This cmdlet returns objects that are determined by the input.</span></span>

## <span data-ttu-id="6a571-301">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="6a571-301">Notes</span></span>

- <span data-ttu-id="6a571-302">`ForEach-Object`Cmdleten fungerar ungefär som en **förgrunds** instruktion, förutom att du inte kan skicka vidare indatamängdar till en **förgrunds** deklaration.</span><span class="sxs-lookup"><span data-stu-id="6a571-302">The `ForEach-Object` cmdlet works much like the **Foreach** statement, except that you cannot pipe input to a **Foreach** statement.</span></span> <span data-ttu-id="6a571-303">Mer information om den **förgrunds** instruktionen finns [about_Foreach](./About/about_Foreach.md).</span><span class="sxs-lookup"><span data-stu-id="6a571-303">For more information about the **Foreach** statement, see [about_Foreach](./About/about_Foreach.md).</span></span>

- <span data-ttu-id="6a571-304">Med början i PowerShell 4,0 `Where` och `ForEach` metoder har lagts till för användning med samlingar.</span><span class="sxs-lookup"><span data-stu-id="6a571-304">Starting in PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span> <span data-ttu-id="6a571-305">Du kan läsa mer om de här nya metoderna här [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="6a571-305">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

- <span data-ttu-id="6a571-306">`ForEach-Object -Parallel`Parameter uppsättningen använder PowerShell: s interna API för att köra varje skript block.</span><span class="sxs-lookup"><span data-stu-id="6a571-306">The `ForEach-Object -Parallel` parameter set uses PowerShell's internal API to run each script block.</span></span> <span data-ttu-id="6a571-307">Detta är betydligt mer arbete än att köra `ForEach-Object` normalt med sekventiell bearbetning.</span><span class="sxs-lookup"><span data-stu-id="6a571-307">This is significantly more overhead than running `ForEach-Object` normally with sequential processing.</span></span> <span data-ttu-id="6a571-308">Det är viktigt att använda **parallellt** där behovet av att köra parallellt är litet jämfört med det arbete som skript blocket utför.</span><span class="sxs-lookup"><span data-stu-id="6a571-308">It is important to use **Parallel** where the overhead of running in parallel is small compared to work the script block performs.</span></span> <span data-ttu-id="6a571-309">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6a571-309">For example:</span></span>

  - <span data-ttu-id="6a571-310">Beräknings intensiva skript på datorer med flera kärnor</span><span class="sxs-lookup"><span data-stu-id="6a571-310">Compute intensive scripts on multi-core machines</span></span>
  - <span data-ttu-id="6a571-311">Skript som tillbringar tid i väntan på resultat eller utför fil åtgärder</span><span class="sxs-lookup"><span data-stu-id="6a571-311">Scripts that spend time waiting for results or doing file operations</span></span>

  <span data-ttu-id="6a571-312">Om du använder den **parallella** parametern kan skript köras mycket långsammare än normalt.</span><span class="sxs-lookup"><span data-stu-id="6a571-312">Using the **Parallel** parameter can cause scripts to run much slower than normal.</span></span> <span data-ttu-id="6a571-313">Särskilt om de parallella skripten är enkla.</span><span class="sxs-lookup"><span data-stu-id="6a571-313">Especially if the parallel scripts are trivial.</span></span> <span data-ttu-id="6a571-314">Experimentera med **parallellt** för att upptäcka var det kan vara bra.</span><span class="sxs-lookup"><span data-stu-id="6a571-314">Experiment with **Parallel** to discover where it can be beneficial.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="6a571-315">`ForEach-Object -Parallel`Parameter uppsättningen kör skript block parallellt på separata process trådar.</span><span class="sxs-lookup"><span data-stu-id="6a571-315">The `ForEach-Object -Parallel` parameter set runs script blocks in parallel on separate process threads.</span></span> <span data-ttu-id="6a571-316">Med `$using:` nyckelordet kan du skicka variabel referenser från cmdlet anrops tråden till varje skript block tråd som körs.</span><span class="sxs-lookup"><span data-stu-id="6a571-316">The `$using:` keyword allows passing variable references from the cmdlet invocation thread to each running script block thread.</span></span> <span data-ttu-id="6a571-317">Eftersom skript block körs i olika trådar måste de objektvariabler som skickas av referensen användas på ett säkert sätt.</span><span class="sxs-lookup"><span data-stu-id="6a571-317">Since the script blocks run in different threads, the object variables passed by reference must be used safely.</span></span> <span data-ttu-id="6a571-318">Vanligt vis är det säkert att läsa från refererade objekt som inte ändras.</span><span class="sxs-lookup"><span data-stu-id="6a571-318">Generally it is safe to read from referenced objects that don't change.</span></span> <span data-ttu-id="6a571-319">Men om objektets status ändras måste du använda tråd säkra objekt, till exempel .net **system. Collection.** desamma typer (se exempel 11).</span><span class="sxs-lookup"><span data-stu-id="6a571-319">But if the object state is being modified then you must used thread safe objects, such as .Net **System.Collection.Concurrent** types (See Example 11).</span></span>

## <span data-ttu-id="6a571-320">Relaterade länkar</span><span class="sxs-lookup"><span data-stu-id="6a571-320">Related links</span></span>

[<span data-ttu-id="6a571-321">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="6a571-321">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="6a571-322">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="6a571-322">Where-Object</span></span>](Where-Object.md)

[<span data-ttu-id="6a571-323">Gruppera objekt</span><span class="sxs-lookup"><span data-stu-id="6a571-323">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="6a571-324">Mått – objekt</span><span class="sxs-lookup"><span data-stu-id="6a571-324">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="6a571-325">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="6a571-325">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="6a571-326">Select-Object</span><span class="sxs-lookup"><span data-stu-id="6a571-326">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="6a571-327">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="6a571-327">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="6a571-328">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="6a571-328">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
