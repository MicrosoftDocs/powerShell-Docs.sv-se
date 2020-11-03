---
description: Beskriver hur du tolkar och formaterar utdata från fjärrkommandon.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_output?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Output
ms.openlocfilehash: 14e4f8f2d3edf5c171a8ae743392b23fc0d057f9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271688"
---
# <a name="about-remote-output"></a><span data-ttu-id="a5d7f-104">Om fjärrutdata</span><span class="sxs-lookup"><span data-stu-id="a5d7f-104">About Remote Output</span></span>

## <a name="short-description"></a><span data-ttu-id="a5d7f-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a5d7f-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a5d7f-106">Beskriver hur du tolkar och formaterar utdata från fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-106">Describes how to interpret and format the output of remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="a5d7f-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a5d7f-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="a5d7f-108">Utdata från ett kommando som kördes på en fjärran sluten dator kan se ut som utdata av samma kommando körning på en lokal dator, men det finns några viktiga skillnader.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-108">The output of a command that was run on a remote computer might look like output of the same command run on a local computer, but there are some significant differences.</span></span>

<span data-ttu-id="a5d7f-109">I det här avsnittet beskrivs hur du tolkar, formaterar och visar utdata från kommandon som körs på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-109">This topic explains how to interpret, format, and display the output of commands that are run on remote computers.</span></span>

## <a name="displaying-the-computer-name"></a><span data-ttu-id="a5d7f-110">VISAR DATOR NAMNET</span><span class="sxs-lookup"><span data-stu-id="a5d7f-110">DISPLAYING THE COMPUTER NAME</span></span>

<span data-ttu-id="a5d7f-111">När du använder Invoke-Command-cmdlet: en för att köra ett kommando på en fjärrdator, returnerar kommandot ett objekt som innehåller namnet på datorn som genererade data.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-111">When you use the Invoke-Command cmdlet to run a command on a remote computer, the command returns an object that includes the name of the computer that generated the data.</span></span> <span data-ttu-id="a5d7f-112">Fjärrdatorns namn lagras i egenskapen PSComputerName.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-112">The remote computer name is stored in the PSComputerName property.</span></span>

<span data-ttu-id="a5d7f-113">För många kommandon visas PSComputerName som standard.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-113">For many commands, the PSComputerName is displayed by default.</span></span> <span data-ttu-id="a5d7f-114">Följande kommando kör till exempel ett Get-Culture-kommando på två fjärrdatorer, Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-114">For example, the following command runs a Get-Culture command on two remote computers, Server01 and Server02.</span></span> <span data-ttu-id="a5d7f-115">Utdata, som visas nedan, innehåller namnen på de fjärranslutna datorer där kommandot kördes.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-115">The output, which appears below, includes the names of the remote computers on which the command ran.</span></span>

```powershell
C:\PS> invoke-command -script {get-culture} -comp Server01, Server02

LCID  Name    DisplayName                PSComputerName
----  ----    -----------                --------------
1033  en-US   English (United States)    Server01
1033  es-AR   Spanish (Argentina)        Server02
```

<span data-ttu-id="a5d7f-116">Du kan använda parametern HideComputerName för Invoke-Command för att dölja egenskapen PSComputerName.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-116">You can use the HideComputerName parameter of Invoke-Command to hide the PSComputerName property.</span></span> <span data-ttu-id="a5d7f-117">Den här parametern är utformad för kommandon som endast samlar in data från en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-117">This parameter is designed for commands that collect data from only one remote computer.</span></span>

<span data-ttu-id="a5d7f-118">Följande kommando kör ett Get-Culture-kommando på den fjärranslutna Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-118">The following command runs a Get-Culture command on the Server01 remote computer.</span></span> <span data-ttu-id="a5d7f-119">Parametern HideComputerName används för att dölja egenskapen PSComputerName och relaterade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-119">It uses the HideComputerName parameter to hide the PSComputerName property and related properties.</span></span>

```powershell
C:\PS> invoke-command -scr {get-culture} -comp Server01 -HideComputerName

LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

<span data-ttu-id="a5d7f-120">Du kan också visa egenskapen PSComputerName om den inte visas som standard.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-120">You can also display the PSComputerName property if it is not displayed by default.</span></span>

<span data-ttu-id="a5d7f-121">Följande kommandon använder exempelvis cmdleten Format-Table för att lägga till egenskapen PSComputerName till utdata från en fjärr Get-Date kommando.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-121">For example, the following commands use the Format-Table cmdlet to add the PSComputerName property to the output of a remote Get-Date command.</span></span>

```powershell
$dates = invoke-command -script {get-date} -computername Server01, Server02
$dates | format-table DateTime, PSComputerName -auto

DateTime                            PSComputerName
--------                            --------------
Monday, July 21, 2008 7:16:58 PM    Server01
Monday, July 21, 2008 7:16:58 PM    Server02
```

## <a name="displaying-the-machinename-property"></a><span data-ttu-id="a5d7f-122">VISA EGENSKAPEN MACHINENAME</span><span class="sxs-lookup"><span data-stu-id="a5d7f-122">DISPLAYING THE MACHINENAME PROPERTY</span></span>

<span data-ttu-id="a5d7f-123">Flera cmdlets, inklusive get-process, get-service och get-EventLog, har en ComputerName-parameter som hämtar objekten på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-123">Several cmdlets, including Get-Process, Get-Service, and Get-EventLog, have a ComputerName parameter that gets the objects on a remote computer.</span></span>
<span data-ttu-id="a5d7f-124">Dessa cmdletar använder inte PowerShell-fjärrkommunikation, så du kan använda dem även på datorer som inte har kon figurer ATS för fjärr kommunikation i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-124">These cmdlets do not use PowerShell remoting, so you can use them even on computers that are not configured for remoting in Windows PowerShell.</span></span>

<span data-ttu-id="a5d7f-125">Objekten som dessa cmdletar returnerar lagrar namnet på fjärrdatorn i egenskapen MachineName.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-125">The objects that these cmdlets return store the name of the remote computer in the MachineName property.</span></span> <span data-ttu-id="a5d7f-126">(Dessa objekt har ingen PSComputerName-egenskap.)</span><span class="sxs-lookup"><span data-stu-id="a5d7f-126">(These objects do not have a PSComputerName property.)</span></span>

<span data-ttu-id="a5d7f-127">Detta kommando hämtar till exempel PowerShell-processen på fjärrdatorerna Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-127">For example, this command gets the PowerShell process on the Server01 and Server02 remote computers.</span></span> <span data-ttu-id="a5d7f-128">Standard visningen inkluderar inte egenskapen MachineName.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-128">The default display does not include the MachineName property.</span></span>

```powershell
C:\PS> get-process PowerShell -computername server01, server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
920      38    97524     114504   575     9.66   2648 PowerShell
194       6    24256      32384   142            3020 PowerShell
352      27    63472      63520   577     3.84   4796 PowerShell
```

<span data-ttu-id="a5d7f-129">Du kan använda Format-Table-cmdlet: en för att visa egenskapen MachineName för process objekt.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-129">You can use the Format-Table cmdlet to display the MachineName property of the process objects.</span></span>

<span data-ttu-id="a5d7f-130">Följande kommando sparar till exempel processerna i variabeln $p och använder sedan en pipeline-operator (|) för att skicka processerna i $p till Format-Table kommandot.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-130">For example, the following command saves the processes in the $p variable and then uses a pipeline operator (|) to send the processes in $p to the Format-Table command.</span></span> <span data-ttu-id="a5d7f-131">Kommandot använder egenskaps parametern för Format-Table för att inkludera egenskapen MachineName i visningen.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-131">The command uses the Property parameter of Format-Table to include the MachineName property in the display.</span></span>

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02
C:\PS> $P | format-table -property ID, ProcessName, MachineName -auto

Id ProcessName MachineName
-- ----------- -----------
2648 PowerShell  Server02
3020 PowerShell  Server01
4796 PowerShell  Server02
```

<span data-ttu-id="a5d7f-132">Följande mer komplexa kommando lägger till egenskapen MachineName till standard process visningen.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-132">The following more complex command adds the MachineName property to the default process display.</span></span> <span data-ttu-id="a5d7f-133">Den använder hash-tabeller för att ange beräknade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-133">It uses hash tables to specify calculated properties.</span></span> <span data-ttu-id="a5d7f-134">Lyckligt vis behöver du inte förstå den för att använda den.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-134">Fortunately, you do not have to understand it to use it.</span></span>

<span data-ttu-id="a5d7f-135">(Observera att bakticket ['] är det fortsättnings tecknen.)</span><span class="sxs-lookup"><span data-stu-id="a5d7f-135">(Note that the backtick [\`] is the continuation character.)</span></span>

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02

C:\PS> $p | format-table -property Handles, `
@{Label="NPM(K)";Expression={int}}, `
@{Label="PM(K)";Expression={int}}, `
@{Label="WS(K)";Expression={int}}, `
@{Label="VM(M)";Expression={int}}, `
@{Label="CPU(s)";Expression={if ($.CPU -ne $()){ $.CPU.ToString("N")}}}, `
Id, ProcessName, MachineName -auto

Handles NPM(K) PM(K)  WS(K) VM(M) CPU(s)   Id ProcessName MachineName
------- ------ -----  ----- ----- ------   -- ----------- -----------
920     38 97560 114532   576        2648 PowerShell  Server02
192      6 24132  32028   140        3020 PowerShell  Server01
438     26 48436  59132   565        4796 PowerShell  Server02

```

## <a name="deserialized-objects"></a><span data-ttu-id="a5d7f-136">AVSERIALISERADE OBJEKT</span><span class="sxs-lookup"><span data-stu-id="a5d7f-136">DESERIALIZED OBJECTS</span></span>

<span data-ttu-id="a5d7f-137">När du kör fjärrkommandon som genererar utdata skickas kommandots utdata över nätverket tillbaka till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-137">When you run remote commands that generate output, the command output is transmitted across the network back to the local computer.</span></span>

<span data-ttu-id="a5d7f-138">Eftersom de flesta aktiva Microsoft .NET Ramverks objekt (till exempel objekt som PowerShell-cmdlet returnerar) inte kan överföras via nätverket, är de aktiva objekten "serialiserade".</span><span class="sxs-lookup"><span data-stu-id="a5d7f-138">Because most live Microsoft .NET Framework objects (such as the objects that PowerShell cmdlets return) cannot be transmitted over the network, the live objects are "serialized".</span></span> <span data-ttu-id="a5d7f-139">Med andra ord konverteras aktiva objekt till XML-representationer av objektet och dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-139">In other words, the live objects are converted into XML representations of the object and its properties.</span></span> <span data-ttu-id="a5d7f-140">Sedan överförs det XML-baserade serialiserade objektet över nätverket.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-140">Then, the XML-based serialized object is transmitted across the network.</span></span>

<span data-ttu-id="a5d7f-141">På den lokala datorn tar PowerShell emot det XML-baserade serialiserade objektet och Avserialiserar det genom att konvertera det XML-baserade objektet till ett standard .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-141">On the local computer, PowerShell receives the XML-based serialized object and "deserializes" it by converting the XML-based object into a standard .NET Framework object.</span></span>

<span data-ttu-id="a5d7f-142">Det avserialiserade objektet är dock inte ett aktivt objekt.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-142">However, the deserialized object is not a live object.</span></span> <span data-ttu-id="a5d7f-143">Det är en ögonblicks bild av objektet vid den tidpunkt då den serialiserades och innehåller egenskaper men inga metoder.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-143">It is a snapshot of the object at the time that it was serialized, and it includes properties but no methods.</span></span> <span data-ttu-id="a5d7f-144">Du kan använda och hantera dessa objekt i PowerShell, inklusive skicka dem i pipeliner, Visa valda egenskaper och formatera dem.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-144">You can use and manage these objects in PowerShell, including passing them in pipelines, displaying selected properties, and formatting them.</span></span>

<span data-ttu-id="a5d7f-145">De flesta avserialiserade objekt formateras automatiskt för visning efter poster i XML-Types.ps1XML eller Format.ps1XML-filer.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-145">Most deserialized objects are automatically formatted for display by entries in the Types.ps1xml or Format.ps1xml files.</span></span> <span data-ttu-id="a5d7f-146">Den lokala datorn kanske inte har filer som har formaterats för alla avserialiserade objekt som genererades på en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-146">However, the local computer might not have formatting files for all of the deserialized objects that were generated on a remote computer.</span></span> <span data-ttu-id="a5d7f-147">När objekt inte är formaterade visas alla egenskaper för varje objekt i-konsolen i en strömmande lista.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-147">When objects are not formatted, all of the properties of each object appear in the console in a streaming list.</span></span>

<span data-ttu-id="a5d7f-148">När objekt inte formateras automatiskt kan du använda cmdletarna för formatering, till exempel Format-Table eller format-lista, för att formatera och Visa valda egenskaper.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-148">When objects are not formatted automatically, you can use the formatting cmdlets, such as Format-Table or Format-List, to format and display selected properties.</span></span> <span data-ttu-id="a5d7f-149">Du kan också använda Out-GridView-cmdleten för att visa objekten i en tabell.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-149">Or, you can use the Out-GridView cmdlet to display the objects in a table.</span></span>

<span data-ttu-id="a5d7f-150">Om du kör ett kommando på en fjärrdator som använder cmdletar som du inte har på din lokala dator, kan det hända att de objekt som kommandot returnerar inte är korrekt formaterade eftersom du inte har formateringsattribut för dessa objekt på din dator.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-150">Also, if you run a command on a remote computer that uses cmdlets that you do not have on your local computer, the objects that the command returns might not be formatted properly because you do not have the formatting files for those objects on your computer.</span></span> <span data-ttu-id="a5d7f-151">Om du vill hämta formatering av data från en annan dator använder du Get-FormatData och Export-FormatData-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-151">To get formatting data from another computer, use the Get-FormatData and Export-FormatData cmdlets.</span></span>

<span data-ttu-id="a5d7f-152">Vissa objekt typer, till exempel DirectoryInfo-objekt och GUID, konverteras tillbaka till aktiva objekt när de tas emot.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-152">Some object types, such as DirectoryInfo objects and GUIDs, are converted back into live objects when they are received.</span></span> <span data-ttu-id="a5d7f-153">Dessa objekt behöver inte någon särskild hantering eller formatering.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-153">These objects do not need any special handling or formatting.</span></span>

## <a name="ordering-the-results"></a><span data-ttu-id="a5d7f-154">SORTERA RESULTATEN</span><span class="sxs-lookup"><span data-stu-id="a5d7f-154">ORDERING THE RESULTS</span></span>

<span data-ttu-id="a5d7f-155">Ordningen på dator namnen i parametern ComputerName i cmdlets bestämmer i vilken ordning PowerShell ansluter till fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-155">The order of the computer names in the ComputerName parameter of cmdlets determines the order in which PowerShell connects to the remote computers.</span></span> <span data-ttu-id="a5d7f-156">Resultaten visas dock i den ordning som den lokala datorn får dem, vilket kan vara en annan ordning.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-156">However, the results appear in the order in which the local computer receives them, which might be a different order.</span></span>

<span data-ttu-id="a5d7f-157">Om du vill ändra ordningen på resultaten använder du Sort-Object-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-157">To change the order of the results, use the Sort-Object cmdlet.</span></span> <span data-ttu-id="a5d7f-158">Du kan sortera på egenskapen PSComputerName eller MachineName.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-158">You can sort on the PSComputerName or MachineName property.</span></span> <span data-ttu-id="a5d7f-159">Du kan också sortera efter en annan egenskap i objektet så att resultatet från olika datorer läggs till i gruppen.</span><span class="sxs-lookup"><span data-stu-id="a5d7f-159">You can also sort on another property of the object so that the results from different computers are interspersed.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5d7f-160">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="a5d7f-160">SEE ALSO</span></span>

[<span data-ttu-id="a5d7f-161">about_Remote</span><span class="sxs-lookup"><span data-stu-id="a5d7f-161">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="a5d7f-162">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="a5d7f-162">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="a5d7f-163">Format-Table</span><span class="sxs-lookup"><span data-stu-id="a5d7f-163">Format-Table</span></span>](xref:Microsoft.PowerShell.Utility.Format-Table)

[<span data-ttu-id="a5d7f-164">Hämta process</span><span class="sxs-lookup"><span data-stu-id="a5d7f-164">Get-Process</span></span>](xref:Microsoft.PowerShell.Management.Get-Process)

[<span data-ttu-id="a5d7f-165">Get-Service</span><span class="sxs-lookup"><span data-stu-id="a5d7f-165">Get-Service</span></span>](xref:Microsoft.PowerShell.Management.Get-Service)

[<span data-ttu-id="a5d7f-166">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="a5d7f-166">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="a5d7f-167">Select-Object</span><span class="sxs-lookup"><span data-stu-id="a5d7f-167">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

