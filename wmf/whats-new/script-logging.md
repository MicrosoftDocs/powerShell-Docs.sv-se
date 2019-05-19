---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Skriptspårning och -loggning
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856156"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="64af0-103">Skriptspårning och -loggning</span><span class="sxs-lookup"><span data-stu-id="64af0-103">Script Tracing and Logging</span></span>

<span data-ttu-id="64af0-104">Medan PowerShell har redan den **LogPipelineExecutionDetails** grupprinciper för att ställa in logga av cmdlet: ar, PowerShell-skriptspråket har flera funktioner som du kan logga in och granska.</span><span class="sxs-lookup"><span data-stu-id="64af0-104">While PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell's scripting language has several features that you might want to log and audit.</span></span> <span data-ttu-id="64af0-105">Den nya funktionen för detaljerad spårning av skriptet ger detaljerad spårning och analys av PowerShell-skript-aktivitet på ett system.</span><span class="sxs-lookup"><span data-stu-id="64af0-105">The new Detailed Script Tracing feature provides detailed tracking and analysis of PowerShell script activity on a system.</span></span> <span data-ttu-id="64af0-106">När du har aktiverat detaljerad skriptet spårning PowerShell loggar alla skriptblocken händelseloggen ETW **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="64af0-106">After enabling detailed script tracing, PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="64af0-107">Om ett skriptblock skapar en annan skriptblocket, till exempel genom att anropa `Invoke-Expression`, anropade skriptblocket även.</span><span class="sxs-lookup"><span data-stu-id="64af0-107">If a script block creates another script block, for example, by calling `Invoke-Expression`, the invoked script block also logged.</span></span>

<span data-ttu-id="64af0-108">Loggning är aktiverat via den **aktiverar loggning för PowerShell-skript Block** gruppolicy-inställningen i **Administrationsmallar** -> **Windows-komponenter**  ->  **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="64af0-108">Logging is enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting in **Administrative Templates** -> **Windows Components** -> **Windows PowerShell**.</span></span>

<span data-ttu-id="64af0-109">Händelserna är:</span><span class="sxs-lookup"><span data-stu-id="64af0-109">The events are:</span></span>

| <span data-ttu-id="64af0-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="64af0-110">Channel</span></span> |                               <span data-ttu-id="64af0-111">Operativa</span><span class="sxs-lookup"><span data-stu-id="64af0-111">Operational</span></span>                               |
| ------- | ----------------------------------------------------------------------- |
| <span data-ttu-id="64af0-112">Nivå</span><span class="sxs-lookup"><span data-stu-id="64af0-112">Level</span></span>   | <span data-ttu-id="64af0-113">Verbose</span><span class="sxs-lookup"><span data-stu-id="64af0-113">Verbose</span></span>                                                                 |
| <span data-ttu-id="64af0-114">OpCode</span><span class="sxs-lookup"><span data-stu-id="64af0-114">Opcode</span></span>  | <span data-ttu-id="64af0-115">Create</span><span class="sxs-lookup"><span data-stu-id="64af0-115">Create</span></span>                                                                  |
| <span data-ttu-id="64af0-116">Uppgift</span><span class="sxs-lookup"><span data-stu-id="64af0-116">Task</span></span>    | <span data-ttu-id="64af0-117">CommandStart</span><span class="sxs-lookup"><span data-stu-id="64af0-117">CommandStart</span></span>                                                            |
| <span data-ttu-id="64af0-118">Nyckelord</span><span class="sxs-lookup"><span data-stu-id="64af0-118">Keyword</span></span> | <span data-ttu-id="64af0-119">körningsutrymme</span><span class="sxs-lookup"><span data-stu-id="64af0-119">Runspace</span></span>                                                                |
| <span data-ttu-id="64af0-120">EventId</span><span class="sxs-lookup"><span data-stu-id="64af0-120">EventId</span></span> | <span data-ttu-id="64af0-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="64af0-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>                              |
| <span data-ttu-id="64af0-122">Meddelande</span><span class="sxs-lookup"><span data-stu-id="64af0-122">Message</span></span> | <span data-ttu-id="64af0-123">Skapa Scriptblock text (%1% 2):</span><span class="sxs-lookup"><span data-stu-id="64af0-123">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="64af0-124">%3</span><span class="sxs-lookup"><span data-stu-id="64af0-124">%3</span></span> </br> <span data-ttu-id="64af0-125">ScriptBlock ID: %4</span><span class="sxs-lookup"><span data-stu-id="64af0-125">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="64af0-126">Den text som bifogas i meddelandet är omfattningen av skriptblocket kompileras.</span><span class="sxs-lookup"><span data-stu-id="64af0-126">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="64af0-127">ID: T är ett GUID som finns kvar för resten av skriptblocket.</span><span class="sxs-lookup"><span data-stu-id="64af0-127">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="64af0-128">När du aktiverar utförlig loggning kan funktionen skrivningar börja och sluta markörer:</span><span class="sxs-lookup"><span data-stu-id="64af0-128">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="64af0-129">Kanal</span><span class="sxs-lookup"><span data-stu-id="64af0-129">Channel</span></span> |                                 <span data-ttu-id="64af0-130">Operativa</span><span class="sxs-lookup"><span data-stu-id="64af0-130">Operational</span></span>                                |
| ------- | -------------------------------------------------------------------------- |
| <span data-ttu-id="64af0-131">Nivå</span><span class="sxs-lookup"><span data-stu-id="64af0-131">Level</span></span>   | <span data-ttu-id="64af0-132">Verbose</span><span class="sxs-lookup"><span data-stu-id="64af0-132">Verbose</span></span>                                                                    |
| <span data-ttu-id="64af0-133">OpCode</span><span class="sxs-lookup"><span data-stu-id="64af0-133">Opcode</span></span>  | <span data-ttu-id="64af0-134">Öppna / Stäng</span><span class="sxs-lookup"><span data-stu-id="64af0-134">Open / Close</span></span>                                                               |
| <span data-ttu-id="64af0-135">Uppgift</span><span class="sxs-lookup"><span data-stu-id="64af0-135">Task</span></span>    | <span data-ttu-id="64af0-136">CommandStart / CommandStop</span><span class="sxs-lookup"><span data-stu-id="64af0-136">CommandStart / CommandStop</span></span>                                                 |
| <span data-ttu-id="64af0-137">Nyckelord</span><span class="sxs-lookup"><span data-stu-id="64af0-137">Keyword</span></span> | <span data-ttu-id="64af0-138">körningsutrymme</span><span class="sxs-lookup"><span data-stu-id="64af0-138">Runspace</span></span>                                                                   |
| <span data-ttu-id="64af0-139">EventId</span><span class="sxs-lookup"><span data-stu-id="64af0-139">EventId</span></span> | <span data-ttu-id="64af0-140">ScriptBlock\_anropa\_starta\_detalj (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="64af0-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="64af0-141">ScriptBlock\_anropa\_fullständig\_detalj (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="64af0-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="64af0-142">Meddelande</span><span class="sxs-lookup"><span data-stu-id="64af0-142">Message</span></span> | <span data-ttu-id="64af0-143">Igång / slutfört anrop av ScriptBlock-ID: %1</span><span class="sxs-lookup"><span data-stu-id="64af0-143">Started / Completed invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="64af0-144">Runspace ID: %2</span><span class="sxs-lookup"><span data-stu-id="64af0-144">Runspace ID: %2</span></span> |

<span data-ttu-id="64af0-145">ID: T är GUID som representerar skriptblocket (som kan korreleras med händelse-ID 0x1008) och Körningsutrymme-ID representerar runspace där skriptblocket kördes.</span><span class="sxs-lookup"><span data-stu-id="64af0-145">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="64af0-146">Procenttecken i anrop meddelandet representerar strukturerade ETW-egenskaper.</span><span class="sxs-lookup"><span data-stu-id="64af0-146">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="64af0-147">När de ersätts med de faktiska värdena i meddelandetexten, ett mer robust sätt att komma åt dem är att hämta meddelandet med cmdleten Get-WinEvent och sedan använda den **egenskaper** matris med meddelandet.</span><span class="sxs-lookup"><span data-stu-id="64af0-147">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="64af0-148">Här är ett exempel på hur den här funktionen kan hjälpa dig att packa upp angripare att kryptera och Förvräng ett skript:</span><span class="sxs-lookup"><span data-stu-id="64af0-148">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

<span data-ttu-id="64af0-149">Kör detta genererar följande loggposter:</span><span class="sxs-lookup"><span data-stu-id="64af0-149">Running this generates the following log entries:</span></span>

```Output
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

Om skriptet Blockets längd överskrider kapaciteten för en enskild händelse, delar PowerShell-skriptet i flera delar. <span data-ttu-id="64af0-151">Här är exempelkod för att kombinera ett skript från dess loggmeddelanden:</span><span class="sxs-lookup"><span data-stu-id="64af0-151">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="64af0-152">Precis som med alla loggningssystem som har en begränsad kvarhållning buffert, är ett sätt att attackera denna infrastruktur att göra loggen med falska händelser att dölja tidigare bevis.</span><span class="sxs-lookup"><span data-stu-id="64af0-152">As with all logging systems that have a limited retention buffer, one way to attack this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="64af0-153">Se till att du har någon form av händelseloggen samling konfigurera vidarebefordran av Windows-händelser för att skydda dig mot angrepp.</span><span class="sxs-lookup"><span data-stu-id="64af0-153">To protect yourself from this attack, ensure that you have some form of event log collection set up Windows Event Forwarding.</span></span> <span data-ttu-id="64af0-154">Mer information finns i [upptäcka angriparen med övervakning av Windows-händelseloggen](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span><span class="sxs-lookup"><span data-stu-id="64af0-154">For more information, see [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span></span>