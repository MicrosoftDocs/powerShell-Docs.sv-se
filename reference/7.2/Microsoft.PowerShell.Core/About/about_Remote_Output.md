---
description: Beskriver hur du tolkar och formaterar utdata från fjärrkommandon.
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_output?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Output
ms.openlocfilehash: 476afc62089795d22002ece05c7ce2bf53994237
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708427"
---
# <a name="about-remote-output"></a><span data-ttu-id="21d23-103">Om fjärrutdata</span><span class="sxs-lookup"><span data-stu-id="21d23-103">About Remote Output</span></span>

## <a name="short-description"></a><span data-ttu-id="21d23-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="21d23-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="21d23-105">Beskriver hur du tolkar och formaterar utdata från fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="21d23-105">Describes how to interpret and format the output of remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="21d23-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="21d23-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="21d23-107">Utdata från ett kommando som kördes på en fjärran sluten dator kan se ut som utdata av samma kommando körning på en lokal dator, men det finns några viktiga skillnader.</span><span class="sxs-lookup"><span data-stu-id="21d23-107">The output of a command that was run on a remote computer might look like output of the same command run on a local computer, but there are some significant differences.</span></span>

<span data-ttu-id="21d23-108">I det här avsnittet beskrivs hur du tolkar, formaterar och visar utdata från kommandon som körs på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="21d23-108">This topic explains how to interpret, format, and display the output of commands that are run on remote computers.</span></span>

## <a name="displaying-the-computer-name"></a><span data-ttu-id="21d23-109">VISAR DATOR NAMNET</span><span class="sxs-lookup"><span data-stu-id="21d23-109">DISPLAYING THE COMPUTER NAME</span></span>

<span data-ttu-id="21d23-110">När du använder Invoke-Command-cmdlet: en för att köra ett kommando på en fjärrdator, returnerar kommandot ett objekt som innehåller namnet på datorn som genererade data.</span><span class="sxs-lookup"><span data-stu-id="21d23-110">When you use the Invoke-Command cmdlet to run a command on a remote computer, the command returns an object that includes the name of the computer that generated the data.</span></span> <span data-ttu-id="21d23-111">Fjärrdatorns namn lagras i egenskapen PSComputerName.</span><span class="sxs-lookup"><span data-stu-id="21d23-111">The remote computer name is stored in the PSComputerName property.</span></span>

<span data-ttu-id="21d23-112">För många kommandon visas PSComputerName som standard.</span><span class="sxs-lookup"><span data-stu-id="21d23-112">For many commands, the PSComputerName is displayed by default.</span></span> <span data-ttu-id="21d23-113">Följande kommando kör till exempel ett Get-Culture-kommando på två fjärrdatorer, Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="21d23-113">For example, the following command runs a Get-Culture command on two remote computers, Server01 and Server02.</span></span> <span data-ttu-id="21d23-114">Utdata, som visas nedan, innehåller namnen på de fjärranslutna datorer där kommandot kördes.</span><span class="sxs-lookup"><span data-stu-id="21d23-114">The output, which appears below, includes the names of the remote computers on which the command ran.</span></span>

```powershell
C:\PS> invoke-command -script {get-culture} -comp Server01, Server02

LCID  Name    DisplayName                PSComputerName
----  ----    -----------                --------------
1033  en-US   English (United States)    Server01
1033  es-AR   Spanish (Argentina)        Server02
```

<span data-ttu-id="21d23-115">Du kan använda parametern HideComputerName för Invoke-Command för att dölja egenskapen PSComputerName.</span><span class="sxs-lookup"><span data-stu-id="21d23-115">You can use the HideComputerName parameter of Invoke-Command to hide the PSComputerName property.</span></span> <span data-ttu-id="21d23-116">Den här parametern är utformad för kommandon som endast samlar in data från en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="21d23-116">This parameter is designed for commands that collect data from only one remote computer.</span></span>

<span data-ttu-id="21d23-117">Följande kommando kör ett Get-Culture-kommando på den fjärranslutna Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="21d23-117">The following command runs a Get-Culture command on the Server01 remote computer.</span></span> <span data-ttu-id="21d23-118">Parametern HideComputerName används för att dölja egenskapen PSComputerName och relaterade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="21d23-118">It uses the HideComputerName parameter to hide the PSComputerName property and related properties.</span></span>

```powershell
C:\PS> invoke-command -scr {get-culture} -comp Server01 -HideComputerName

LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

<span data-ttu-id="21d23-119">Du kan också visa egenskapen PSComputerName om den inte visas som standard.</span><span class="sxs-lookup"><span data-stu-id="21d23-119">You can also display the PSComputerName property if it is not displayed by default.</span></span>

<span data-ttu-id="21d23-120">Följande kommandon använder exempelvis cmdleten Format-Table för att lägga till egenskapen PSComputerName till utdata från en fjärr Get-Date kommando.</span><span class="sxs-lookup"><span data-stu-id="21d23-120">For example, the following commands use the Format-Table cmdlet to add the PSComputerName property to the output of a remote Get-Date command.</span></span>

```powershell
$dates = invoke-command -script {get-date} -computername Server01, Server02
$dates | format-table DateTime, PSComputerName -auto

DateTime                            PSComputerName
--------                            --------------
Monday, July 21, 2008 7:16:58 PM    Server01
Monday, July 21, 2008 7:16:58 PM    Server02
```

## <a name="displaying-the-machinename-property"></a><span data-ttu-id="21d23-121">VISA EGENSKAPEN MACHINENAME</span><span class="sxs-lookup"><span data-stu-id="21d23-121">DISPLAYING THE MACHINENAME PROPERTY</span></span>

<span data-ttu-id="21d23-122">Flera cmdlets, inklusive get-process, get-service och get-EventLog, har en ComputerName-parameter som hämtar objekten på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="21d23-122">Several cmdlets, including Get-Process, Get-Service, and Get-EventLog, have a ComputerName parameter that gets the objects on a remote computer.</span></span>
<span data-ttu-id="21d23-123">Dessa cmdletar använder inte PowerShell-fjärrkommunikation, så du kan använda dem även på datorer som inte har kon figurer ATS för fjärr kommunikation i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21d23-123">These cmdlets do not use PowerShell remoting, so you can use them even on computers that are not configured for remoting in Windows PowerShell.</span></span>

<span data-ttu-id="21d23-124">Objekten som dessa cmdletar returnerar lagrar namnet på fjärrdatorn i egenskapen MachineName.</span><span class="sxs-lookup"><span data-stu-id="21d23-124">The objects that these cmdlets return store the name of the remote computer in the MachineName property.</span></span> <span data-ttu-id="21d23-125">(Dessa objekt har ingen PSComputerName-egenskap.)</span><span class="sxs-lookup"><span data-stu-id="21d23-125">(These objects do not have a PSComputerName property.)</span></span>

<span data-ttu-id="21d23-126">Detta kommando hämtar till exempel PowerShell-processen på fjärrdatorerna Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="21d23-126">For example, this command gets the PowerShell process on the Server01 and Server02 remote computers.</span></span> <span data-ttu-id="21d23-127">Standard visningen inkluderar inte egenskapen MachineName.</span><span class="sxs-lookup"><span data-stu-id="21d23-127">The default display does not include the MachineName property.</span></span>

```powershell
C:\PS> get-process PowerShell -computername server01, server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
920      38    97524     114504   575     9.66   2648 PowerShell
194       6    24256      32384   142            3020 PowerShell
352      27    63472      63520   577     3.84   4796 PowerShell
```

<span data-ttu-id="21d23-128">Du kan använda Format-Table-cmdlet: en för att visa egenskapen MachineName för process objekt.</span><span class="sxs-lookup"><span data-stu-id="21d23-128">You can use the Format-Table cmdlet to display the MachineName property of the process objects.</span></span>

<span data-ttu-id="21d23-129">Följande kommando sparar till exempel processerna i variabeln $p och använder sedan en pipeline-operator (|) för att skicka processerna i $p till Format-Table kommandot.</span><span class="sxs-lookup"><span data-stu-id="21d23-129">For example, the following command saves the processes in the $p variable and then uses a pipeline operator (|) to send the processes in $p to the Format-Table command.</span></span> <span data-ttu-id="21d23-130">Kommandot använder egenskaps parametern för Format-Table för att inkludera egenskapen MachineName i visningen.</span><span class="sxs-lookup"><span data-stu-id="21d23-130">The command uses the Property parameter of Format-Table to include the MachineName property in the display.</span></span>

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02
C:\PS> $P | format-table -property ID, ProcessName, MachineName -auto

Id ProcessName MachineName
-- ----------- -----------
2648 PowerShell  Server02
3020 PowerShell  Server01
4796 PowerShell  Server02
```

<span data-ttu-id="21d23-131">Följande mer komplexa kommando lägger till egenskapen MachineName till standard process visningen.</span><span class="sxs-lookup"><span data-stu-id="21d23-131">The following more complex command adds the MachineName property to the default process display.</span></span> <span data-ttu-id="21d23-132">Den använder hash-tabeller för att ange beräknade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="21d23-132">It uses hash tables to specify calculated properties.</span></span> <span data-ttu-id="21d23-133">Lyckligt vis behöver du inte förstå den för att använda den.</span><span class="sxs-lookup"><span data-stu-id="21d23-133">Fortunately, you do not have to understand it to use it.</span></span>

<span data-ttu-id="21d23-134">(Observera att bakticket ['] är det fortsättnings tecknen.)</span><span class="sxs-lookup"><span data-stu-id="21d23-134">(Note that the backtick [\`] is the continuation character.)</span></span>

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

## <a name="deserialized-objects"></a><span data-ttu-id="21d23-135">AVSERIALISERADE OBJEKT</span><span class="sxs-lookup"><span data-stu-id="21d23-135">DESERIALIZED OBJECTS</span></span>

<span data-ttu-id="21d23-136">När du kör fjärrkommandon som genererar utdata skickas kommandots utdata över nätverket tillbaka till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="21d23-136">When you run remote commands that generate output, the command output is transmitted across the network back to the local computer.</span></span>

<span data-ttu-id="21d23-137">Eftersom de flesta aktiva Microsoft .NET Ramverks objekt (till exempel objekt som PowerShell-cmdlet returnerar) inte kan överföras via nätverket, är de aktiva objekten "serialiserade".</span><span class="sxs-lookup"><span data-stu-id="21d23-137">Because most live Microsoft .NET Framework objects (such as the objects that PowerShell cmdlets return) cannot be transmitted over the network, the live objects are "serialized".</span></span> <span data-ttu-id="21d23-138">Med andra ord konverteras aktiva objekt till XML-representationer av objektet och dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="21d23-138">In other words, the live objects are converted into XML representations of the object and its properties.</span></span> <span data-ttu-id="21d23-139">Sedan överförs det XML-baserade serialiserade objektet över nätverket.</span><span class="sxs-lookup"><span data-stu-id="21d23-139">Then, the XML-based serialized object is transmitted across the network.</span></span>

<span data-ttu-id="21d23-140">På den lokala datorn tar PowerShell emot det XML-baserade serialiserade objektet och Avserialiserar det genom att konvertera det XML-baserade objektet till ett standard .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="21d23-140">On the local computer, PowerShell receives the XML-based serialized object and "deserializes" it by converting the XML-based object into a standard .NET Framework object.</span></span>

<span data-ttu-id="21d23-141">Det avserialiserade objektet är dock inte ett aktivt objekt.</span><span class="sxs-lookup"><span data-stu-id="21d23-141">However, the deserialized object is not a live object.</span></span> <span data-ttu-id="21d23-142">Det är en ögonblicks bild av objektet vid den tidpunkt då den serialiserades och innehåller egenskaper men inga metoder.</span><span class="sxs-lookup"><span data-stu-id="21d23-142">It is a snapshot of the object at the time that it was serialized, and it includes properties but no methods.</span></span> <span data-ttu-id="21d23-143">Du kan använda och hantera dessa objekt i PowerShell, inklusive skicka dem i pipeliner, Visa valda egenskaper och formatera dem.</span><span class="sxs-lookup"><span data-stu-id="21d23-143">You can use and manage these objects in PowerShell, including passing them in pipelines, displaying selected properties, and formatting them.</span></span>

<span data-ttu-id="21d23-144">De flesta avserialiserade objekt formateras automatiskt för visning efter poster i XML-Types.ps1XML eller Format.ps1XML-filer.</span><span class="sxs-lookup"><span data-stu-id="21d23-144">Most deserialized objects are automatically formatted for display by entries in the Types.ps1xml or Format.ps1xml files.</span></span> <span data-ttu-id="21d23-145">Den lokala datorn kanske inte har filer som har formaterats för alla avserialiserade objekt som genererades på en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="21d23-145">However, the local computer might not have formatting files for all of the deserialized objects that were generated on a remote computer.</span></span> <span data-ttu-id="21d23-146">När objekt inte är formaterade visas alla egenskaper för varje objekt i-konsolen i en strömmande lista.</span><span class="sxs-lookup"><span data-stu-id="21d23-146">When objects are not formatted, all of the properties of each object appear in the console in a streaming list.</span></span>

<span data-ttu-id="21d23-147">När objekt inte formateras automatiskt kan du använda cmdletarna för formatering, till exempel Format-Table eller format-lista, för att formatera och Visa valda egenskaper.</span><span class="sxs-lookup"><span data-stu-id="21d23-147">When objects are not formatted automatically, you can use the formatting cmdlets, such as Format-Table or Format-List, to format and display selected properties.</span></span> <span data-ttu-id="21d23-148">Du kan också använda Out-GridView-cmdleten för att visa objekten i en tabell.</span><span class="sxs-lookup"><span data-stu-id="21d23-148">Or, you can use the Out-GridView cmdlet to display the objects in a table.</span></span>

<span data-ttu-id="21d23-149">Om du kör ett kommando på en fjärrdator som använder cmdletar som du inte har på din lokala dator, kan det hända att de objekt som kommandot returnerar inte är korrekt formaterade eftersom du inte har formateringsattribut för dessa objekt på din dator.</span><span class="sxs-lookup"><span data-stu-id="21d23-149">Also, if you run a command on a remote computer that uses cmdlets that you do not have on your local computer, the objects that the command returns might not be formatted properly because you do not have the formatting files for those objects on your computer.</span></span> <span data-ttu-id="21d23-150">Om du vill hämta formatering av data från en annan dator använder du Get-FormatData och Export-FormatData-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="21d23-150">To get formatting data from another computer, use the Get-FormatData and Export-FormatData cmdlets.</span></span>

<span data-ttu-id="21d23-151">Vissa objekt typer, till exempel DirectoryInfo-objekt och GUID, konverteras tillbaka till aktiva objekt när de tas emot.</span><span class="sxs-lookup"><span data-stu-id="21d23-151">Some object types, such as DirectoryInfo objects and GUIDs, are converted back into live objects when they are received.</span></span> <span data-ttu-id="21d23-152">Dessa objekt behöver inte någon särskild hantering eller formatering.</span><span class="sxs-lookup"><span data-stu-id="21d23-152">These objects do not need any special handling or formatting.</span></span>

## <a name="ordering-the-results"></a><span data-ttu-id="21d23-153">SORTERA RESULTATEN</span><span class="sxs-lookup"><span data-stu-id="21d23-153">ORDERING THE RESULTS</span></span>

<span data-ttu-id="21d23-154">Ordningen på dator namnen i parametern ComputerName i cmdlets bestämmer i vilken ordning PowerShell ansluter till fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="21d23-154">The order of the computer names in the ComputerName parameter of cmdlets determines the order in which PowerShell connects to the remote computers.</span></span> <span data-ttu-id="21d23-155">Resultaten visas dock i den ordning som den lokala datorn får dem, vilket kan vara en annan ordning.</span><span class="sxs-lookup"><span data-stu-id="21d23-155">However, the results appear in the order in which the local computer receives them, which might be a different order.</span></span>

<span data-ttu-id="21d23-156">Om du vill ändra ordningen på resultaten använder du Sort-Object-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="21d23-156">To change the order of the results, use the Sort-Object cmdlet.</span></span> <span data-ttu-id="21d23-157">Du kan sortera på egenskapen PSComputerName eller MachineName.</span><span class="sxs-lookup"><span data-stu-id="21d23-157">You can sort on the PSComputerName or MachineName property.</span></span> <span data-ttu-id="21d23-158">Du kan också sortera efter en annan egenskap i objektet så att resultatet från olika datorer läggs till i gruppen.</span><span class="sxs-lookup"><span data-stu-id="21d23-158">You can also sort on another property of the object so that the results from different computers are interspersed.</span></span>

## <a name="see-also"></a><span data-ttu-id="21d23-159">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="21d23-159">SEE ALSO</span></span>

[<span data-ttu-id="21d23-160">about_Remote</span><span class="sxs-lookup"><span data-stu-id="21d23-160">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="21d23-161">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="21d23-161">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="21d23-162">Format-Table</span><span class="sxs-lookup"><span data-stu-id="21d23-162">Format-Table</span></span>](xref:Microsoft.PowerShell.Utility.Format-Table)

[<span data-ttu-id="21d23-163">Hämta process</span><span class="sxs-lookup"><span data-stu-id="21d23-163">Get-Process</span></span>](xref:Microsoft.PowerShell.Management.Get-Process)

[<span data-ttu-id="21d23-164">Get-Service</span><span class="sxs-lookup"><span data-stu-id="21d23-164">Get-Service</span></span>](xref:Microsoft.PowerShell.Management.Get-Service)

[<span data-ttu-id="21d23-165">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="21d23-165">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="21d23-166">Select-Object</span><span class="sxs-lookup"><span data-stu-id="21d23-166">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

