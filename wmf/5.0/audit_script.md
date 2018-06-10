---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: b8f175cee0a1de501b64890fdc2798f4f6421a14
ms.sourcegitcommit: 2ffb9fa92129c2001379ca2c17646466721f7165
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251491"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="a3e93-102">Skriptspårning och -loggning</span><span class="sxs-lookup"><span data-stu-id="a3e93-102">Script Tracing and Logging</span></span>

<span data-ttu-id="a3e93-103">Även om Windows PowerShell har redan den **LogPipelineExecutionDetails** Grupprincip inställningen logga anrop av cmdlets PowerShells skriptspråk har tillräckligt med funktioner som du kanske vill logga in och/eller granska.</span><span class="sxs-lookup"><span data-stu-id="a3e93-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="a3e93-104">Den nya funktionen för spårning av detaljerad skript kan du aktivera detaljerad spårning och analys av Windows PowerShell scripting används på ett system.</span><span class="sxs-lookup"><span data-stu-id="a3e93-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="a3e93-105">När du aktiverar spårning detaljerat skript, Windows PowerShell loggar alla skriptblock händelseloggen ETW **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="a3e93-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="a3e93-106">Om ett skriptblock skapar ett annat skriptblock (till exempel ett skript som anropar cmdleten Invoke-Expression på en sträng), loggas samt det resulterande skriptblocket.</span><span class="sxs-lookup"><span data-stu-id="a3e93-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="a3e93-107">Loggning av dessa händelser kan aktiveras via den **aktiverar du loggning för PowerShell-skript Block** grupprincipinställningen (i Administrationsmallar -> Windows-komponenter -> Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="a3e93-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="a3e93-108">Händelser är:</span><span class="sxs-lookup"><span data-stu-id="a3e93-108">The events are:</span></span>

| <span data-ttu-id="a3e93-109">Kanal</span><span class="sxs-lookup"><span data-stu-id="a3e93-109">Channel</span></span> | <span data-ttu-id="a3e93-110">Använd</span><span class="sxs-lookup"><span data-stu-id="a3e93-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="a3e93-111">Nivå</span><span class="sxs-lookup"><span data-stu-id="a3e93-111">Level</span></span>   | <span data-ttu-id="a3e93-112">Verbose</span><span class="sxs-lookup"><span data-stu-id="a3e93-112">Verbose</span></span>                                     |
| <span data-ttu-id="a3e93-113">OpCode</span><span class="sxs-lookup"><span data-stu-id="a3e93-113">Opcode</span></span>  | <span data-ttu-id="a3e93-114">Create</span><span class="sxs-lookup"><span data-stu-id="a3e93-114">Create</span></span>                                      |
| <span data-ttu-id="a3e93-115">Uppgift</span><span class="sxs-lookup"><span data-stu-id="a3e93-115">Task</span></span>    | <span data-ttu-id="a3e93-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="a3e93-116">CommandStart</span></span>                                |
| <span data-ttu-id="a3e93-117">Nyckelordet</span><span class="sxs-lookup"><span data-stu-id="a3e93-117">Keyword</span></span> | <span data-ttu-id="a3e93-118">Runspace</span><span class="sxs-lookup"><span data-stu-id="a3e93-118">Runspace</span></span>                                    |
| <span data-ttu-id="a3e93-119">Händelse-ID</span><span class="sxs-lookup"><span data-stu-id="a3e93-119">EventId</span></span> | <span data-ttu-id="a3e93-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="a3e93-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="a3e93-121">Meddelande</span><span class="sxs-lookup"><span data-stu-id="a3e93-121">Message</span></span> | <span data-ttu-id="a3e93-122">Skapa Scriptblock text (%1% 2):</span><span class="sxs-lookup"><span data-stu-id="a3e93-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="a3e93-123">%3</span><span class="sxs-lookup"><span data-stu-id="a3e93-123">%3</span></span> </br> <span data-ttu-id="a3e93-124">ScriptBlock-ID: %4</span><span class="sxs-lookup"><span data-stu-id="a3e93-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="a3e93-125">Den text som bifogas i meddelandet är omfattningen av skriptblocket kompileras.</span><span class="sxs-lookup"><span data-stu-id="a3e93-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="a3e93-126">ID: T är ett GUID som sparas i skriptblocket livslängd.</span><span class="sxs-lookup"><span data-stu-id="a3e93-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="a3e93-127">När du aktiverar utförlig loggning funktionen skrivningar börja och sluta markörer:</span><span class="sxs-lookup"><span data-stu-id="a3e93-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="a3e93-128">Kanal</span><span class="sxs-lookup"><span data-stu-id="a3e93-128">Channel</span></span> | <span data-ttu-id="a3e93-129">Använd</span><span class="sxs-lookup"><span data-stu-id="a3e93-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="a3e93-130">Nivå</span><span class="sxs-lookup"><span data-stu-id="a3e93-130">Level</span></span>   | <span data-ttu-id="a3e93-131">Verbose</span><span class="sxs-lookup"><span data-stu-id="a3e93-131">Verbose</span></span>                                                |
| <span data-ttu-id="a3e93-132">OpCode</span><span class="sxs-lookup"><span data-stu-id="a3e93-132">Opcode</span></span>  | <span data-ttu-id="a3e93-133">Öppna (/ Stäng)</span><span class="sxs-lookup"><span data-stu-id="a3e93-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="a3e93-134">Uppgift</span><span class="sxs-lookup"><span data-stu-id="a3e93-134">Task</span></span>    | <span data-ttu-id="a3e93-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="a3e93-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="a3e93-136">Nyckelordet</span><span class="sxs-lookup"><span data-stu-id="a3e93-136">Keyword</span></span> | <span data-ttu-id="a3e93-137">Runspace</span><span class="sxs-lookup"><span data-stu-id="a3e93-137">Runspace</span></span>                                               |
| <span data-ttu-id="a3e93-138">Händelse-ID</span><span class="sxs-lookup"><span data-stu-id="a3e93-138">EventId</span></span> | <span data-ttu-id="a3e93-139">ScriptBlock\_anropa\_starta\_detalj (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="a3e93-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="a3e93-140">ScriptBlock\_anropa\_fullständig\_detalj (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="a3e93-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="a3e93-141">Meddelande</span><span class="sxs-lookup"><span data-stu-id="a3e93-141">Message</span></span> | <span data-ttu-id="a3e93-142">Igång (/ slutförda) anrop av ScriptBlock-ID: %1</span><span class="sxs-lookup"><span data-stu-id="a3e93-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="a3e93-143">Runspace-ID: %2</span><span class="sxs-lookup"><span data-stu-id="a3e93-143">Runspace ID: %2</span></span> |

<span data-ttu-id="a3e93-144">ID: T är GUID som representerar skriptblocket (som kan korreleras med händelse-ID 0x1008) och Runspace ID representerar runspace där skriptblocket kördes.</span><span class="sxs-lookup"><span data-stu-id="a3e93-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="a3e93-145">Procenttecken i anrops-meddelandet representerar strukturerade ETW-egenskaper.</span><span class="sxs-lookup"><span data-stu-id="a3e93-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="a3e93-146">När de ersätts med de faktiska värdena i meddelandetexten är ett mer stabilt sätt att komma åt dem att hämta meddelandet med cmdleten Get-WinEvent och sedan använda den **egenskaper** matris med meddelandet.</span><span class="sxs-lookup"><span data-stu-id="a3e93-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="a3e93-147">Här är ett exempel på hur den här funktionen kan hjälpa dig att packa angripare att kryptera och obfuscate ett skript:</span><span class="sxs-lookup"><span data-stu-id="a3e93-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR “encryption”
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

<span data-ttu-id="a3e93-148">Kör detta genererar följande loggposter:</span><span class="sxs-lookup"><span data-stu-id="a3e93-148">Running this generates the following log entries:</span></span>

```
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

Om skriptet Blockets längd överskrider vad ETW kan anläggning i en enskild händelse, delar skriptet i flera delar i Windows PowerShell. <span data-ttu-id="a3e93-150">Här är exempelkod som sätter ett skript från dess loggmeddelanden:</span><span class="sxs-lookup"><span data-stu-id="a3e93-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="a3e93-151">Precis som med alla loggning system som har en begränsad kvarhållning buffert (d.v.s. ETW-loggarna) är en attack mot denna infrastruktur att översvämma logg med falska händelser att dölja tidigare bevis.</span><span class="sxs-lookup"><span data-stu-id="a3e93-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="a3e93-152">Om du vill skydda dig mot angrepp, kontrollera att du har någon form av händelseloggen samling konfigurera (d.v.s. händelse vidarebefordran av Windows, [upptäcka angriparen med övervakning av Windows händelselogg](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) att flytta loggar ut från datorn som snart som möjligt.</span><span class="sxs-lookup"><span data-stu-id="a3e93-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) to move event logs off of the computer as soon as possible.</span></span>
