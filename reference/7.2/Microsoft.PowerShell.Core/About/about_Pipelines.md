---
description: Kombinera kommandon till pipelines i PowerShell
Locale: en-US
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pipelines
ms.openlocfilehash: e4ae85fbbfe5232048a90e1fe4f62db3e95e5f1b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710980"
---
# <a name="about-pipelines"></a><span data-ttu-id="00233-103">Om pipelines</span><span class="sxs-lookup"><span data-stu-id="00233-103">About Pipelines</span></span>

## <a name="short-description"></a><span data-ttu-id="00233-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="00233-104">Short description</span></span>

<span data-ttu-id="00233-105">Kombinera kommandon till pipelines i PowerShell</span><span class="sxs-lookup"><span data-stu-id="00233-105">Combining commands into pipelines in the PowerShell</span></span>

## <a name="long-description"></a><span data-ttu-id="00233-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="00233-106">Long description</span></span>

<span data-ttu-id="00233-107">En pipeline är en serie kommandon som är anslutna av pipeline-operatorer ( `|` ) (ASCII 124).</span><span class="sxs-lookup"><span data-stu-id="00233-107">A pipeline is a series of commands connected by pipeline operators (`|`) (ASCII 124).</span></span> <span data-ttu-id="00233-108">Varje pipeline-operator skickar resultatet från föregående kommando till nästa kommando.</span><span class="sxs-lookup"><span data-stu-id="00233-108">Each pipeline operator sends the results of the preceding command to the next command.</span></span>

<span data-ttu-id="00233-109">Utdata från det första kommandot kan skickas för bearbetning som indata till det andra kommandot.</span><span class="sxs-lookup"><span data-stu-id="00233-109">The output of the first command can be sent for processing as input to the second command.</span></span> <span data-ttu-id="00233-110">Och utdata kan skickas till ännu ett annat kommando.</span><span class="sxs-lookup"><span data-stu-id="00233-110">And that output can be sent to yet another command.</span></span> <span data-ttu-id="00233-111">Resultatet är en komplex kommando kedja eller en _pipeline_ som består av en serie enkla kommandon.</span><span class="sxs-lookup"><span data-stu-id="00233-111">The result is a complex command chain or _pipeline_ that is composed of a series of simple commands.</span></span>

<span data-ttu-id="00233-112">Exempel:</span><span class="sxs-lookup"><span data-stu-id="00233-112">For example,</span></span>

```powershell
Command-1 | Command-2 | Command-3
```

<span data-ttu-id="00233-113">I det här exemplet skickas objekten som utvärderar `Command-1` till `Command-2` .</span><span class="sxs-lookup"><span data-stu-id="00233-113">In this example, the objects that `Command-1` emits are sent to `Command-2`.</span></span>
<span data-ttu-id="00233-114">`Command-2` bearbetar objekten och skickar dem till `Command-3` .</span><span class="sxs-lookup"><span data-stu-id="00233-114">`Command-2` processes the objects and sends them to `Command-3`.</span></span> <span data-ttu-id="00233-115">`Command-3` bearbetar objekten och skickar dem nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="00233-115">`Command-3` processes the objects and send them down the pipeline.</span></span> <span data-ttu-id="00233-116">Eftersom det inte finns några fler kommandon i pipelinen visas resultaten i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="00233-116">Because there are no more commands in the pipeline, the results are displayed at the console.</span></span>

<span data-ttu-id="00233-117">I en pipeline bearbetas kommandona i ordning från vänster till höger.</span><span class="sxs-lookup"><span data-stu-id="00233-117">In a pipeline, the commands are processed in order from left to right.</span></span> <span data-ttu-id="00233-118">Bearbetningen hanteras som en enda åtgärd och utdata visas när den genereras.</span><span class="sxs-lookup"><span data-stu-id="00233-118">The processing is handled as a single operation and output is displayed as it's generated.</span></span>

<span data-ttu-id="00233-119">Här är ett enkelt exempel.</span><span class="sxs-lookup"><span data-stu-id="00233-119">Here is a simple example.</span></span> <span data-ttu-id="00233-120">Följande kommando hämtar anteckningar-processen och stoppar det sedan.</span><span class="sxs-lookup"><span data-stu-id="00233-120">The following command gets the Notepad process and then stops it.</span></span>

<span data-ttu-id="00233-121">Exempel:</span><span class="sxs-lookup"><span data-stu-id="00233-121">For example,</span></span>

```powershell
Get-Process notepad | Stop-Process
```

<span data-ttu-id="00233-122">Det första kommandot använder `Get-Process` cmdleten för att hämta ett objekt som representerar anteckningar-processen.</span><span class="sxs-lookup"><span data-stu-id="00233-122">The first command uses the `Get-Process` cmdlet to get an object representing the Notepad process.</span></span> <span data-ttu-id="00233-123">Den använder en pipeline-operator ( `|` ) för att skicka processobjektet till `Stop-Process` cmdleten, vilket stoppar anteckningar-processen.</span><span class="sxs-lookup"><span data-stu-id="00233-123">It uses a pipeline operator (`|`) to send the process object to the `Stop-Process` cmdlet, which stops the Notepad process.</span></span> <span data-ttu-id="00233-124">Observera att `Stop-Process` kommandot inte har en **namn** -eller **ID-** parameter för att ange processen, eftersom den angivna processen skickas via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="00233-124">Notice that the `Stop-Process` command doesn't have a **Name** or **ID** parameter to specify the process, because the specified process is submitted through the pipeline.</span></span>

<span data-ttu-id="00233-125">Detta pipeline-exempel hämtar textfilerna i den aktuella katalogen, väljer bara de filer som är större än 10 000 byte långa, sorterar dem efter längd och visar namn och längd för varje fil i en tabell.</span><span class="sxs-lookup"><span data-stu-id="00233-125">This pipeline example gets the text files in the current directory, selects only the files that are more than 10,000 bytes long, sorts them by length, and displays the name and length of each file in a table.</span></span>

```powershell
Get-ChildItem -Path *.txt |
  Where-Object {$_.length -gt 10000} |
    Sort-Object -Property length |
      Format-Table -Property name, length
```

<span data-ttu-id="00233-126">Den här pipelinen består av fyra kommandon i den angivna ordningen.</span><span class="sxs-lookup"><span data-stu-id="00233-126">This pipeline consists of four commands in the specified order.</span></span> <span data-ttu-id="00233-127">Följande bild visar utdata från varje kommando när de skickas till nästa kommando i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="00233-127">The following illustration shows the output from each command as it's passed to the next command in the pipeline.</span></span>

```
Get-ChildItem -Path *.txt
| (FileInfo objects for *.txt)
V
Where-Object {$_.length -gt 10000}
| (FileInfo objects for *.txt)
| (      Length > 10000      )
V
Sort-Object -Property Length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
V
Format-Table -Property name, length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
| (   Formatted in a table   )
V

Name                       Length
----                       ------
tmp1.txt                    82920
tmp2.txt                   114000
tmp3.txt                   114000
```

## <a name="using-pipelines"></a><span data-ttu-id="00233-128">Använda pipelines</span><span class="sxs-lookup"><span data-stu-id="00233-128">Using pipelines</span></span>

<span data-ttu-id="00233-129">De flesta PowerShell-cmdletar har utformats för att stödja pipeliner.</span><span class="sxs-lookup"><span data-stu-id="00233-129">Most PowerShell cmdlets are designed to support pipelines.</span></span> <span data-ttu-id="00233-130">I de flesta _fall kan du_ skicka vidare resultatet av en **Get** -cmdlet till en annan cmdlet av samma substantiv.</span><span class="sxs-lookup"><span data-stu-id="00233-130">In most cases, you can _pipe_ the results of a **Get** cmdlet to another cmdlet of the same noun.</span></span>
<span data-ttu-id="00233-131">Du kan till exempel skicka utdata från `Get-Service` cmdleten till `Start-Service` `Stop-Service` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="00233-131">For example, you can pipe the output of the `Get-Service` cmdlet to the `Start-Service` or `Stop-Service` cmdlets.</span></span>

<span data-ttu-id="00233-132">Den här exempel tjänsten startar WMI-tjänsten på datorn:</span><span class="sxs-lookup"><span data-stu-id="00233-132">This example pipeline starts the WMI service on the computer:</span></span>

```powershell
Get-Service wmi | Start-Service
```

<span data-ttu-id="00233-133">Du kan till exempel skicka vidare utdata från `Get-Item` eller `Get-ChildItem` i PowerShell-registernyckeln till `New-ItemProperty` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="00233-133">For another example, you can pipe the output of `Get-Item` or `Get-ChildItem` within the PowerShell registry provider to the `New-ItemProperty` cmdlet.</span></span> <span data-ttu-id="00233-134">I det här exemplet lägger du till en ny register post, **NoOfEmployees**, med värdet **8124** till **företagets** register nyckel.</span><span class="sxs-lookup"><span data-stu-id="00233-134">This example adds a new registry entry, **NoOfEmployees**, with a value of **8124**, to the **MyCompany** registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany |
  New-ItemProperty -Name NoOfEmployees -Value 8124
```

<span data-ttu-id="00233-135">Många av verktygs-cmdletarna, till exempel `Get-Member` ,,, `Where-Object` `Sort-Object` `Group-Object` och `Measure-Object` används nästan uteslutande i pipeliner.</span><span class="sxs-lookup"><span data-stu-id="00233-135">Many of the utility cmdlets, such as `Get-Member`, `Where-Object`, `Sort-Object`, `Group-Object`, and `Measure-Object` are used almost exclusively in pipelines.</span></span> <span data-ttu-id="00233-136">Du kan skicka vidare valfri objekt typ till dessa cmdletar.</span><span class="sxs-lookup"><span data-stu-id="00233-136">You can pipe any object type to these cmdlets.</span></span> <span data-ttu-id="00233-137">Det här exemplet visar hur du sorterar alla processer på datorn med antalet öppna referenser i varje process.</span><span class="sxs-lookup"><span data-stu-id="00233-137">This example shows how to sort all the processes on the computer by the number of open handles in each process.</span></span>

```powershell
Get-Process | Sort-Object -Property handles
```

<span data-ttu-id="00233-138">Du kan skicka pipe-objekt till formaterings-, export-och utdata-cmdletar, till exempel,,, `Format-List` `Format-Table` `Export-Clixml` `Export-CSV` och `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="00233-138">You can pipe objects to the formatting, export, and output cmdlets, such as `Format-List`, `Format-Table`, `Export-Clixml`, `Export-CSV`, and `Out-File`.</span></span>

<span data-ttu-id="00233-139">Det här exemplet visar hur du använder `Format-List` cmdleten för att visa en lista över egenskaper för ett process objekt.</span><span class="sxs-lookup"><span data-stu-id="00233-139">This example shows how to use the `Format-List` cmdlet to display a list of properties for a process object.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="00233-140">Med lite praxis kan du se att kombinerar enkla kommandon i pipelines sparar tid och skriver och gör skripten mer effektiv.</span><span class="sxs-lookup"><span data-stu-id="00233-140">With a bit of practice, you'll find that combining simple commands into pipelines saves time and typing, and makes your scripting more efficient.</span></span>

## <a name="how-pipelines-work"></a><span data-ttu-id="00233-141">Så här fungerar pipeliner</span><span class="sxs-lookup"><span data-stu-id="00233-141">How pipelines work</span></span>

<span data-ttu-id="00233-142">I det här avsnittet beskrivs hur inobjekten binds till cmdlet-parametrar och bearbetas under pipeline-körning.</span><span class="sxs-lookup"><span data-stu-id="00233-142">This section explains how input objects are bound to cmdlet parameters and processed during pipeline execution.</span></span>

### <a name="accepts-pipeline-input"></a><span data-ttu-id="00233-143">Accepterar inmatade pipelines</span><span class="sxs-lookup"><span data-stu-id="00233-143">Accepts pipeline input</span></span>

<span data-ttu-id="00233-144">För att stödja pipelinen måste den mottagande cmdleten ha en parameter som godkänner pipeline-inflöden.</span><span class="sxs-lookup"><span data-stu-id="00233-144">To support pipelining, the receiving cmdlet must have a parameter that accepts pipeline input.</span></span> <span data-ttu-id="00233-145">Använd `Get-Help` kommandot med alternativen **fullständig** eller **parameter** för att avgöra vilka parametrar i en cmdlet som accepterar pipeline-inflöden.</span><span class="sxs-lookup"><span data-stu-id="00233-145">Use the `Get-Help` command with the **Full** or **Parameter** options to determine which parameters of a cmdlet accept pipeline input.</span></span>

<span data-ttu-id="00233-146">Om du till exempel vill ta reda på vilken av parametrarna i `Start-Service` cmdleten som accepterar pipeline-Indatatyp, skriver du:</span><span class="sxs-lookup"><span data-stu-id="00233-146">For example, to determine which of the parameters of the `Start-Service` cmdlet accepts pipeline input, type:</span></span>

```powershell
Get-Help Start-Service -Full
```

<span data-ttu-id="00233-147">eller</span><span class="sxs-lookup"><span data-stu-id="00233-147">or</span></span>

```powershell
Get-Help Start-Service -Parameter *
```

<span data-ttu-id="00233-148">Hjälpen för `Start-Service` cmdleten visar att endast **InputObject** och **namn** parametrarna accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="00233-148">The help for the `Start-Service` cmdlet shows that only the **InputObject** and **Name** parameters accept pipeline input.</span></span>

```Output
-InputObject <ServiceController[]>
Specifies ServiceController objects representing the services to be started.
Enter a variable that contains the objects, or type a command or expression
that gets the objects.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByValue)
Accept wildcard characters?  false

-Name <String[]>
Specifies the service names for the service to be started.

The parameter name is optional. You can use Name or its alias, ServiceName,
or you can omit the parameter name.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByPropertyName, ByValue)
Accept wildcard characters?  false
```

<span data-ttu-id="00233-149">När du skickar objekt via pipeline till `Start-Service` försöker PowerShell koppla objekten till parametrarna **InputObject** och **Name** .</span><span class="sxs-lookup"><span data-stu-id="00233-149">When you send objects through the pipeline to `Start-Service`, PowerShell attempts to associate the objects with the **InputObject** and **Name** parameters.</span></span>

### <a name="methods-of-accepting-pipeline-input"></a><span data-ttu-id="00233-150">Metoder för att godkänna pipeline-inflöden</span><span class="sxs-lookup"><span data-stu-id="00233-150">Methods of accepting pipeline input</span></span>

<span data-ttu-id="00233-151">Cmdlets-parametrar kan acceptera pipeline-inmatade på ett av två olika sätt:</span><span class="sxs-lookup"><span data-stu-id="00233-151">Cmdlets parameters can accept pipeline input in one of two different ways:</span></span>

- <span data-ttu-id="00233-152">**ByValue**: parametern accepterar värden som matchar den förväntade .net-typen eller som kan konverteras till den typen.</span><span class="sxs-lookup"><span data-stu-id="00233-152">**ByValue**: The parameter accepts values that match the expected .NET type or that can be converted to that type.</span></span>

  <span data-ttu-id="00233-153">Till exempel är **namn** parametern för `Start-Service` accepterar pipeline-inmatade med värde.</span><span class="sxs-lookup"><span data-stu-id="00233-153">For example, the **Name** parameter of `Start-Service` accepts pipeline input by value.</span></span> <span data-ttu-id="00233-154">Det kan ta emot sträng objekt eller objekt som kan konverteras till strängar.</span><span class="sxs-lookup"><span data-stu-id="00233-154">It can accept string objects or objects that can be converted to strings.</span></span>

- <span data-ttu-id="00233-155">**ByPropertyName**: parametern accepterar endast inmatade objekt när indatamängden har en egenskap med samma namn som parametern.</span><span class="sxs-lookup"><span data-stu-id="00233-155">**ByPropertyName**: The parameter accepts input only when the input object has a property of the same name as the parameter.</span></span>

  <span data-ttu-id="00233-156">Namn parametern för kan till exempel `Start-Service` ta emot objekt som har egenskapen **Name** .</span><span class="sxs-lookup"><span data-stu-id="00233-156">For example, the Name parameter of `Start-Service` can accept objects that have a **Name** property.</span></span> <span data-ttu-id="00233-157">Om du vill visa en lista över egenskaperna för ett objekt, rör du det `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="00233-157">To list the properties of an object, pipe it to `Get-Member`.</span></span>

<span data-ttu-id="00233-158">Vissa parametrar kan acceptera objekt med både värde-eller egenskaps namn, vilket gör det lättare att ta emot inmatade objekt från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="00233-158">Some parameters can accept objects by both value or property name, making it easier to take input from the pipeline.</span></span>

### <a name="parameter-binding"></a><span data-ttu-id="00233-159">Parameter bindning</span><span class="sxs-lookup"><span data-stu-id="00233-159">Parameter binding</span></span>

<span data-ttu-id="00233-160">När du rör objekt från ett kommando till ett annat kommando försöker PowerShell associera skickas-objekt med en parameter för den mottagande cmdleten.</span><span class="sxs-lookup"><span data-stu-id="00233-160">When you pipe objects from one command to another command, PowerShell attempts to associate the piped objects with a parameter of the receiving cmdlet.</span></span>

<span data-ttu-id="00233-161">PowerShell: s parameter bindnings komponent associerar inobjekten med cmdlet-parametrar enligt följande kriterier:</span><span class="sxs-lookup"><span data-stu-id="00233-161">PowerShell's parameter binding component associates the input objects with cmdlet parameters according to the following criteria:</span></span>

- <span data-ttu-id="00233-162">Parametern måste acceptera inmatade värden från en pipeline.</span><span class="sxs-lookup"><span data-stu-id="00233-162">The parameter must accept input from a pipeline.</span></span>
- <span data-ttu-id="00233-163">Parametern måste godkänna vilken typ av objekt som skickas eller en typ som kan konverteras till den förväntade typen.</span><span class="sxs-lookup"><span data-stu-id="00233-163">The parameter must accept the type of object being sent or a type that can be converted to the expected type.</span></span>
- <span data-ttu-id="00233-164">Parametern användes inte i kommandot.</span><span class="sxs-lookup"><span data-stu-id="00233-164">The parameter wasn't used in the command.</span></span>

<span data-ttu-id="00233-165">Till exempel `Start-Service` har cmdleten många parametrar, men endast två av dem, **namn** och **InputObject** accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="00233-165">For example, the `Start-Service` cmdlet has many parameters, but only two of them, **Name** and **InputObject** accept pipeline input.</span></span> <span data-ttu-id="00233-166">Parametern **Name** tar strängar och **InputObject** -parametern använder tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="00233-166">The **Name** parameter takes strings and the **InputObject** parameter takes service objects.</span></span> <span data-ttu-id="00233-167">Därför kan du skicka pipe-strängar, service objekt och objekt med egenskaper som kan konverteras till sträng-eller tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="00233-167">Therefore, you can pipe strings, service objects, and objects with properties that can be converted to string or service objects.</span></span>

<span data-ttu-id="00233-168">PowerShell hanterar parameter bindning så effektivt som möjligt.</span><span class="sxs-lookup"><span data-stu-id="00233-168">PowerShell manages parameter binding as efficiently as possible.</span></span> <span data-ttu-id="00233-169">Du kan inte föreslå eller tvinga PowerShell att binda till en angiven parameter.</span><span class="sxs-lookup"><span data-stu-id="00233-169">You can't suggest or force the PowerShell to bind to a specific parameter.</span></span> <span data-ttu-id="00233-170">Kommandot Miss lyckas om PowerShell inte kan binda skickas-objekten.</span><span class="sxs-lookup"><span data-stu-id="00233-170">The command fails if PowerShell can't bind the piped objects.</span></span>

<span data-ttu-id="00233-171">Mer information om fel sökning av bindnings fel finns i [undersöka pipeline-fel](#investigating-pipeline-errors) senare i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="00233-171">For more information about troubleshooting binding errors, see [Investigating Pipeline Errors](#investigating-pipeline-errors) later in this article.</span></span>

### <a name="one-at-a-time-processing"></a><span data-ttu-id="00233-172">En-vid-tidpunkt-bearbetning</span><span class="sxs-lookup"><span data-stu-id="00233-172">One-at-a-time processing</span></span>

<span data-ttu-id="00233-173">Överföring av objekt till ett kommando är ungefär som att använda en parameter för kommandot för att skicka objekten.</span><span class="sxs-lookup"><span data-stu-id="00233-173">Piping objects to a command is much like using a parameter of the command to submit the objects.</span></span> <span data-ttu-id="00233-174">Nu ska vi titta på ett pipeline-exempel.</span><span class="sxs-lookup"><span data-stu-id="00233-174">Let's look at a pipeline example.</span></span> <span data-ttu-id="00233-175">I det här exemplet använder vi en pipeline för att visa en tabell med tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="00233-175">In this example, we use a pipeline to display a table of service objects.</span></span>

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

<span data-ttu-id="00233-176">Funktions sätt är att använda **InputObject** -parametern för `Format-Table` för att skicka objekt samlingen.</span><span class="sxs-lookup"><span data-stu-id="00233-176">Functionally, this is like using the **InputObject** parameter of `Format-Table` to submit the object collection.</span></span>

<span data-ttu-id="00233-177">Vi kan till exempel spara samlingen med tjänster till en variabel som skickas med parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="00233-177">For example, we can save the collection of services to a variable that is passed using the **InputObject** parameter.</span></span>

```powershell
$services = Get-Service
Format-Table -InputObject $services -Property Name, DependentServices
```

<span data-ttu-id="00233-178">Eller så kan vi bädda in kommandot i parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="00233-178">Or we can embed the command in the **InputObject** parameter.</span></span>

```powershell
Format-Table -InputObject (Get-Service) -Property Name, DependentServices
```

<span data-ttu-id="00233-179">Det finns dock en viktig skillnad.</span><span class="sxs-lookup"><span data-stu-id="00233-179">However, there's an important difference.</span></span> <span data-ttu-id="00233-180">När du rör flera objekt till ett kommando skickar PowerShell objekten till kommandot ett i taget.</span><span class="sxs-lookup"><span data-stu-id="00233-180">When you pipe multiple objects to a command, PowerShell sends the objects to the command one at a time.</span></span> <span data-ttu-id="00233-181">När du använder en kommando parameter skickas objekten som ett enda mat ris objekt.</span><span class="sxs-lookup"><span data-stu-id="00233-181">When you use a command parameter, the objects are sent as a single array object.</span></span> <span data-ttu-id="00233-182">Den här mindre skillnaden har betydande konsekvenser.</span><span class="sxs-lookup"><span data-stu-id="00233-182">This minor difference has significant consequences.</span></span>

<span data-ttu-id="00233-183">Vid körning av en pipeline räknar PowerShell automatiskt upp alla typer som implementerar `IEnumerable` gränssnittet och skickar medlemmar via pipelinen en i taget.</span><span class="sxs-lookup"><span data-stu-id="00233-183">When executing a pipeline, PowerShell automatically enumerates any type that implements the `IEnumerable` interface and sends the members through the pipeline one at a time.</span></span> <span data-ttu-id="00233-184">Undantaget är `[hashtable]` , vilket kräver ett anrop till `GetEnumerator()` metoden.</span><span class="sxs-lookup"><span data-stu-id="00233-184">The exception is `[hashtable]`, which requires a call to the `GetEnumerator()` method.</span></span>

<span data-ttu-id="00233-185">I följande exempel är en matris och en hash-tabell skickas till `Measure-Object` cmdleten för att räkna antalet objekt som tas emot från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="00233-185">In the following examples, an array and a hashtable are piped to the `Measure-Object` cmdlet to count the number of objects received from the pipeline.</span></span> <span data-ttu-id="00233-186">Matrisen har flera medlemmar och hash-tabellen innehåller flera nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="00233-186">The array has multiple members, and the hashtable has multiple key-value pairs.</span></span> <span data-ttu-id="00233-187">Endast matrisen räknas upp en i taget.</span><span class="sxs-lookup"><span data-stu-id="00233-187">Only the array is enumerated one at a time.</span></span>

```powershell
@(1,2,3) | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

```powershell
@{"One"=1;"Two"=2} | Measure-Object
```

```Output
Count    : 1
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

<span data-ttu-id="00233-188">Om du dessutom skickar flera process objekt från `Get-Process` cmdlet `Get-Member` : en till cmdleten skickar PowerShell varje process objekt, ett i taget, till `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="00233-188">Similarly, if you pipe multiple process objects from the `Get-Process` cmdlet to the `Get-Member` cmdlet, PowerShell sends each process object, one at a time, to `Get-Member`.</span></span> <span data-ttu-id="00233-189">`Get-Member` visar process objektens .NET-klass (typ) och deras egenskaper och metoder.</span><span class="sxs-lookup"><span data-stu-id="00233-189">`Get-Member` displays the .NET class (type) of the process objects, and their properties and methods.</span></span>

```powershell
Get-Process | Get-Member
```

```Output
TypeName: System.Diagnostics.Process

Name      MemberType     Definition
----      ----------     ----------
Handles   AliasProperty  Handles = Handlecount
Name      AliasProperty  Name = ProcessName
NPM       AliasProperty  NPM = NonpagedSystemMemorySize
...
```

> [!NOTE]
> <span data-ttu-id="00233-190">`Get-Member` eliminerar dubbletter, så om objekten är av samma typ visas bara en objekt typ.</span><span class="sxs-lookup"><span data-stu-id="00233-190">`Get-Member` eliminates duplicates, so if the objects are all of the same type, it only displays one object type.</span></span>

<span data-ttu-id="00233-191">Men om du använder parametern **InputObject** i `Get-Member` , `Get-Member` tar emot en matris med **system. Diagnostics. bearbeta** objekt som en enda enhet.</span><span class="sxs-lookup"><span data-stu-id="00233-191">However, if you use the **InputObject** parameter of `Get-Member`, then `Get-Member` receives an array of **System.Diagnostics.Process** objects as a single unit.</span></span> <span data-ttu-id="00233-192">Den visar egenskaperna för en objekt mat ris.</span><span class="sxs-lookup"><span data-stu-id="00233-192">It displays the properties of an array of objects.</span></span> <span data-ttu-id="00233-193">(Observera mat ris symbolen ( `[]` ) efter **systemets. objekt** typ namn.)</span><span class="sxs-lookup"><span data-stu-id="00233-193">(Note the array symbol (`[]`) after the **System.Object** type name.)</span></span>

<span data-ttu-id="00233-194">Exempel:</span><span class="sxs-lookup"><span data-stu-id="00233-194">For example,</span></span>

```powershell
Get-Member -InputObject (Get-Process)
```

```Output
TypeName: System.Object[]

Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
Address            Method        System.Object& Address(Int32 )
Clone              Method        System.Object Clone()
...
```

<span data-ttu-id="00233-195">Det är inte säkert att det här resultatet är det du avsåg.</span><span class="sxs-lookup"><span data-stu-id="00233-195">This result might not be what you intended.</span></span> <span data-ttu-id="00233-196">Men när du förstår det kan du använda det.</span><span class="sxs-lookup"><span data-stu-id="00233-196">But after you understand it, you can use it.</span></span> <span data-ttu-id="00233-197">Alla mat ris objekt har till exempel egenskapen **Count** .</span><span class="sxs-lookup"><span data-stu-id="00233-197">For example, all array objects have a **Count** property.</span></span> <span data-ttu-id="00233-198">Du kan använda det för att räkna antalet processer som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="00233-198">You can use that to count the number of processes running on the computer.</span></span>

<span data-ttu-id="00233-199">Exempel:</span><span class="sxs-lookup"><span data-stu-id="00233-199">For example,</span></span>

```powershell
(Get-Process).count
```

<span data-ttu-id="00233-200">Det är viktigt att komma ihåg att objekt som skickas ned pipelinen levereras en i taget.</span><span class="sxs-lookup"><span data-stu-id="00233-200">It's important to remember that objects sent down the pipeline are delivered one at a time.</span></span>

## <a name="investigating-pipeline-errors"></a><span data-ttu-id="00233-201">Undersöka pipeline-fel</span><span class="sxs-lookup"><span data-stu-id="00233-201">Investigating pipeline errors</span></span>

<span data-ttu-id="00233-202">När PowerShell inte kan associera skickas-objekt med en parameter för den mottagande cmdleten Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="00233-202">When PowerShell can't associate the piped objects with a parameter of the receiving cmdlet, the command fails.</span></span>

<span data-ttu-id="00233-203">I följande exempel försöker vi flytta en register post från en register nyckel till en annan.</span><span class="sxs-lookup"><span data-stu-id="00233-203">In the following example, we try to move a registry entry from one registry key to another.</span></span> <span data-ttu-id="00233-204">Cmdlet: en `Get-Item` hämtar mål Sök vägen, som sedan skickas till `Move-ItemProperty` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="00233-204">The `Get-Item` cmdlet gets the destination path, which is then piped to the `Move-ItemProperty` cmdlet.</span></span> <span data-ttu-id="00233-205">`Move-ItemProperty`Kommandot anger den aktuella sökvägen till och namnet på den register post som ska flyttas.</span><span class="sxs-lookup"><span data-stu-id="00233-205">The `Move-ItemProperty` command specifies the current path and name of the registry entry to be moved.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales |
Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
```

<span data-ttu-id="00233-206">Kommandot Miss lyckas och PowerShell visar följande fel meddelande:</span><span class="sxs-lookup"><span data-stu-id="00233-206">The command fails and PowerShell displays the following error message:</span></span>

```Output
Move-ItemProperty : The input object can't be bound to any parameters for
the command either because the command doesn't take pipeline input or the
input and its properties do not match any of the parameters that take
pipeline input.
At line:1 char:23
+ $a | Move-ItemProperty <<<<  -Path HKLM:\Software\MyCompany\design -Name p
```

<span data-ttu-id="00233-207">Använd cmdleten för att `Trace-Command` spåra parameter bindnings komponenten i PowerShell för att undersöka.</span><span class="sxs-lookup"><span data-stu-id="00233-207">To investigate, use the `Trace-Command` cmdlet to trace the parameter binding component of PowerShell.</span></span> <span data-ttu-id="00233-208">I följande exempel kalkeras parameter bindning medan pipelinen körs.</span><span class="sxs-lookup"><span data-stu-id="00233-208">The following example traces parameter binding while the pipeline is executing.</span></span> <span data-ttu-id="00233-209">Parametern **PSHost** visar spårnings resultatet i-konsolen och parametern **fil Sök väg** skickar spårnings resultatet till `debug.txt` filen för senare referens.</span><span class="sxs-lookup"><span data-stu-id="00233-209">The **PSHost** parameter displays the trace results in the console and the **FilePath** parameter send the trace results to the `debug.txt` file for later reference.</span></span>

```powershell
Trace-Command -Name ParameterBinding -PSHost -FilePath debug.txt -Expression {
  Get-Item -Path HKLM:\Software\MyCompany\sales |
    Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
}
```

<span data-ttu-id="00233-210">Resultatet av spårningen är långvarigt, men de visar värdena som binds till `Get-Item` cmdleten och sedan de namngivna värdena binds till `Move-ItemProperty` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="00233-210">The results of the trace are lengthy, but they show the values being bound to the `Get-Item` cmdlet and then the named values being bound to the `Move-ItemProperty` cmdlet.</span></span>

```Output
...
BIND NAMED cmd line args [`Move-ItemProperty`]
BIND arg [HKLM:\Software\MyCompany\design] to parameter [Path]
...
BIND arg [product] to parameter [Name]
...
BIND POSITIONAL cmd line args [`Move-ItemProperty`]
...
```

<span data-ttu-id="00233-211">Slutligen visar det att försöket att binda sökvägen till **mål** parametern för `Move-ItemProperty` misslyckades.</span><span class="sxs-lookup"><span data-stu-id="00233-211">Finally, it shows that the attempt to bind the path to the **Destination** parameter of `Move-ItemProperty` failed.</span></span>

```Output
...
BIND PIPELINE object to parameters: [`Move-ItemProperty`]
PIPELINE object TYPE = [Microsoft.Win32.RegistryKey]
RESTORING pipeline parameter's original values
Parameter [Destination] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
Parameter [Credential] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
...
```

<span data-ttu-id="00233-212">Använd `Get-Help` cmdleten för att visa attributen för **mål** parametern.</span><span class="sxs-lookup"><span data-stu-id="00233-212">Use the `Get-Help` cmdlet to view the attributes of the **Destination** parameter.</span></span>

```Output
Get-Help Move-ItemProperty -Parameter Destination

-Destination <String>
    Specifies the path to the destination location.

    Required?                    true
    Position?                    1
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  false
```

<span data-ttu-id="00233-213">Resultatet visar att **målet** endast tar emot pipelinen genom att skriva in egenskaps namn.</span><span class="sxs-lookup"><span data-stu-id="00233-213">The results show that **Destination** takes pipeline input only "by property name".</span></span> <span data-ttu-id="00233-214">Därför måste skickas-objektet ha en egenskap med namnet **destination**.</span><span class="sxs-lookup"><span data-stu-id="00233-214">Therefore, the piped object must have a property named **Destination**.</span></span>

<span data-ttu-id="00233-215">Används `Get-Member` för att visa egenskaperna för objektet som kommer från `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="00233-215">Use `Get-Member` to see the properties of the object coming from `Get-Item`.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales | Get-Member
```

<span data-ttu-id="00233-216">Utdata visar att objektet är ett **Microsoft. Win32. RegistryKey** -objekt som inte har en **mål** egenskap.</span><span class="sxs-lookup"><span data-stu-id="00233-216">The output shows that the item is a **Microsoft.Win32.RegistryKey** object that doesn't have a **Destination** property.</span></span> <span data-ttu-id="00233-217">Det förklarar varför kommandot misslyckades.</span><span class="sxs-lookup"><span data-stu-id="00233-217">That explains why the command failed.</span></span>

<span data-ttu-id="00233-218">Parametern **Path** godkänner pipeline-inmatade efter namn eller värde.</span><span class="sxs-lookup"><span data-stu-id="00233-218">The **Path** parameter accepts pipeline input by name or by value.</span></span>

```Output
Get-Help Move-ItemProperty -Parameter Path

-Path <String[]>
    Specifies the path to the current location of the property. Wildcard
    characters are permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  true
```

<span data-ttu-id="00233-219">För att åtgärda kommandot måste vi ange målet i `Move-ItemProperty` cmdleten och använda `Get-Item` för att hämta **sökvägen** till det objekt som vi vill flytta.</span><span class="sxs-lookup"><span data-stu-id="00233-219">To fix the command, we must specify the destination in the `Move-ItemProperty` cmdlet and use `Get-Item` to get the **Path** of the item we want to move.</span></span>

<span data-ttu-id="00233-220">Exempel:</span><span class="sxs-lookup"><span data-stu-id="00233-220">For example,</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\design |
Move-ItemProperty -Destination HKLM:\Software\MyCompany\sales -Name product
```

## <a name="intrinsic-line-continuation"></a><span data-ttu-id="00233-221">Fortsättning på inre rad</span><span class="sxs-lookup"><span data-stu-id="00233-221">Intrinsic line continuation</span></span>

<span data-ttu-id="00233-222">Som redan diskuterats är en pipeline en serie kommandon som är anslutna via pipeline-operatorer ( `|` ), vanligt vis skrivna på en enda rad.</span><span class="sxs-lookup"><span data-stu-id="00233-222">As already discussed, a pipeline is a series of commands connected by pipeline operators (`|`), usually written on a single line.</span></span> <span data-ttu-id="00233-223">Med hjälp av PowerShell kan du dock dela upp pipelinen över flera rader.</span><span class="sxs-lookup"><span data-stu-id="00233-223">However, for readability, PowerShell allows you to split the pipeline across multiple lines.</span></span>
<span data-ttu-id="00233-224">När en pipe-operator är den sista token på raden, kopplas PowerShell-parsern till nästa rad till aktuellt kommando för att fortsätta att bygga pipelinen.</span><span class="sxs-lookup"><span data-stu-id="00233-224">When a pipe operator is the last token on the line, the PowerShell parser joins the next line to current command to continue the construction of the pipeline.</span></span>

<span data-ttu-id="00233-225">Till exempel följande enradig pipeline:</span><span class="sxs-lookup"><span data-stu-id="00233-225">For example, the following single-line pipeline:</span></span>

```powershell
Command-1 | Command-2 | Command-3
```

<span data-ttu-id="00233-226">kan skrivas som:</span><span class="sxs-lookup"><span data-stu-id="00233-226">can be written as:</span></span>

```powershell
Command-1 |
  Command-2 |
    Command-3
```

<span data-ttu-id="00233-227">De inledande blank stegen på de efterföljande raderna är inte signifikanta.</span><span class="sxs-lookup"><span data-stu-id="00233-227">The leading spaces on the subsequent lines are not significant.</span></span> <span data-ttu-id="00233-228">Indraget ökar läsbarheten.</span><span class="sxs-lookup"><span data-stu-id="00233-228">The indentation enhances readability.</span></span>

<span data-ttu-id="00233-229">PowerShell 7 lägger till stöd för fortsättning av pipeliner med pipelinen i början av en rad.</span><span class="sxs-lookup"><span data-stu-id="00233-229">PowerShell 7 adds support for continuation of pipelines with the pipeline character at the beginning of a line.</span></span> <span data-ttu-id="00233-230">I följande exempel visas hur du kan använda den här nya funktionen.</span><span class="sxs-lookup"><span data-stu-id="00233-230">The following examples show how you could use this new functionality.</span></span>

```powershell
# Wrapping with a pipe at the beginning of a line (no backtick required)
Get-Process | Where-Object CPU | Where-Object Path
    | Get-Item | Where-Object FullName -match "AppData"
    | Sort-Object FullName -Unique

# Wrapping with a pipe on a line by itself
Get-Process | Where-Object CPU | Where-Object Path
    |
    Get-Item | Where-Object FullName -match "AppData"
    |
    Sort-Object FullName -Unique
```

> [!IMPORTANT]
> <span data-ttu-id="00233-231">När du arbetar interaktivt i gränssnittet, klistrar du in kod med pipelines i början av en rad endast när du använder <kbd>CTRL</kbd> + <kbd>V</kbd> för att klistra in.</span><span class="sxs-lookup"><span data-stu-id="00233-231">When working interactively in the shell, pasting code with pipelines at the beginning of a line only when using <kbd>Ctrl</kbd>+<kbd>V</kbd> to paste.</span></span>
> <span data-ttu-id="00233-232">Högerklicka på Klistra in åtgärder infoga raderna en i taget.</span><span class="sxs-lookup"><span data-stu-id="00233-232">Right-click paste operations insert the lines one at a time.</span></span> <span data-ttu-id="00233-233">Eftersom raden inte avslutas med ett pipeline-värde, ser PowerShell ut som att de är inaktuella och kör den raden som anges.</span><span class="sxs-lookup"><span data-stu-id="00233-233">Since the line does not end with a pipeline character, PowerShell considers the input to be complete and executes that line as entered.</span></span>

## <a name="see-also"></a><span data-ttu-id="00233-234">Se även</span><span class="sxs-lookup"><span data-stu-id="00233-234">See Also</span></span>

[<span data-ttu-id="00233-235">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="00233-235">about_PSReadLine</span></span>](../../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="00233-236">about_Objects</span><span class="sxs-lookup"><span data-stu-id="00233-236">about_Objects</span></span>](about_objects.md)

[<span data-ttu-id="00233-237">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="00233-237">about_Parameters</span></span>](about_parameters.md)

[<span data-ttu-id="00233-238">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="00233-238">about_Command_Syntax</span></span>](about_command_syntax.md)

[<span data-ttu-id="00233-239">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="00233-239">about_ForEach</span></span>](about_foreach.md)
