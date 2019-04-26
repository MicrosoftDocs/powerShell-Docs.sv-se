---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 28cd186ab3a08a0da4ff81f5a21514f239770d13
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058088"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="dde0d-102">Skriptspårning och -loggning</span><span class="sxs-lookup"><span data-stu-id="dde0d-102">Script Tracing and Logging</span></span>

<span data-ttu-id="dde0d-103">Även om Windows PowerShell har redan den **LogPipelineExecutionDetails** Grupprincip att ställa in logga av cmdlet: ar, PowerShell-skriptspråket massor av funktioner som du kanske vill logga in och/eller granska.</span><span class="sxs-lookup"><span data-stu-id="dde0d-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="dde0d-104">Den nya funktionen för detaljerad spårning av skriptet kan du aktivera detaljerad spårning och analys av Windows PowerShell skript används på ett system.</span><span class="sxs-lookup"><span data-stu-id="dde0d-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="dde0d-105">När du har aktiverat detaljerad skriptet spårning av Windows PowerShell loggar alla skriptblocken händelseloggen ETW **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="dde0d-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="dde0d-106">Om ett skriptblock skapar ett annat skriptblock (till exempel ett skript som anropar cmdleten Invoke-Expression på en sträng), loggas samt det resulterande skriptblocket.</span><span class="sxs-lookup"><span data-stu-id="dde0d-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="dde0d-107">Loggning av dessa händelser kan aktiveras via den **aktiverar loggning för PowerShell-skript Block** grupprincipinställningen (i Administrationsmallar -> Windows-komponenter -> Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="dde0d-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="dde0d-108">Händelserna är:</span><span class="sxs-lookup"><span data-stu-id="dde0d-108">The events are:</span></span>

| <span data-ttu-id="dde0d-109">Kanal</span><span class="sxs-lookup"><span data-stu-id="dde0d-109">Channel</span></span> | <span data-ttu-id="dde0d-110">Operativa</span><span class="sxs-lookup"><span data-stu-id="dde0d-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="dde0d-111">Nivå</span><span class="sxs-lookup"><span data-stu-id="dde0d-111">Level</span></span>   | <span data-ttu-id="dde0d-112">Utförlig</span><span class="sxs-lookup"><span data-stu-id="dde0d-112">Verbose</span></span>                                     |
| <span data-ttu-id="dde0d-113">OpCode</span><span class="sxs-lookup"><span data-stu-id="dde0d-113">Opcode</span></span>  | <span data-ttu-id="dde0d-114">Create</span><span class="sxs-lookup"><span data-stu-id="dde0d-114">Create</span></span>                                      |
| <span data-ttu-id="dde0d-115">Uppgift</span><span class="sxs-lookup"><span data-stu-id="dde0d-115">Task</span></span>    | <span data-ttu-id="dde0d-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="dde0d-116">CommandStart</span></span>                                |
| <span data-ttu-id="dde0d-117">Nyckelord</span><span class="sxs-lookup"><span data-stu-id="dde0d-117">Keyword</span></span> | <span data-ttu-id="dde0d-118">körningsutrymme</span><span class="sxs-lookup"><span data-stu-id="dde0d-118">Runspace</span></span>                                    |
| <span data-ttu-id="dde0d-119">EventId</span><span class="sxs-lookup"><span data-stu-id="dde0d-119">EventId</span></span> | <span data-ttu-id="dde0d-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="dde0d-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="dde0d-121">Meddelande</span><span class="sxs-lookup"><span data-stu-id="dde0d-121">Message</span></span> | <span data-ttu-id="dde0d-122">Skapa Scriptblock text (%1% 2):</span><span class="sxs-lookup"><span data-stu-id="dde0d-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="dde0d-123">%3</span><span class="sxs-lookup"><span data-stu-id="dde0d-123">%3</span></span> </br> <span data-ttu-id="dde0d-124">ScriptBlock ID: %4</span><span class="sxs-lookup"><span data-stu-id="dde0d-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="dde0d-125">Den text som bifogas i meddelandet är omfattningen av skriptblocket kompileras.</span><span class="sxs-lookup"><span data-stu-id="dde0d-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="dde0d-126">ID: T är ett GUID som finns kvar för resten av skriptblocket.</span><span class="sxs-lookup"><span data-stu-id="dde0d-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="dde0d-127">När du aktiverar utförlig loggning kan funktionen skrivningar börja och sluta markörer:</span><span class="sxs-lookup"><span data-stu-id="dde0d-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="dde0d-128">Kanal</span><span class="sxs-lookup"><span data-stu-id="dde0d-128">Channel</span></span> | <span data-ttu-id="dde0d-129">Operativa</span><span class="sxs-lookup"><span data-stu-id="dde0d-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="dde0d-130">Nivå</span><span class="sxs-lookup"><span data-stu-id="dde0d-130">Level</span></span>   | <span data-ttu-id="dde0d-131">Utförlig</span><span class="sxs-lookup"><span data-stu-id="dde0d-131">Verbose</span></span>                                                |
| <span data-ttu-id="dde0d-132">OpCode</span><span class="sxs-lookup"><span data-stu-id="dde0d-132">Opcode</span></span>  | <span data-ttu-id="dde0d-133">Öppna (/ Stäng)</span><span class="sxs-lookup"><span data-stu-id="dde0d-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="dde0d-134">Uppgift</span><span class="sxs-lookup"><span data-stu-id="dde0d-134">Task</span></span>    | <span data-ttu-id="dde0d-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="dde0d-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="dde0d-136">Nyckelord</span><span class="sxs-lookup"><span data-stu-id="dde0d-136">Keyword</span></span> | <span data-ttu-id="dde0d-137">körningsutrymme</span><span class="sxs-lookup"><span data-stu-id="dde0d-137">Runspace</span></span>                                               |
| <span data-ttu-id="dde0d-138">EventId</span><span class="sxs-lookup"><span data-stu-id="dde0d-138">EventId</span></span> | <span data-ttu-id="dde0d-139">ScriptBlock\_anropa\_starta\_detalj (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="dde0d-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="dde0d-140">ScriptBlock\_anropa\_fullständig\_detalj (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="dde0d-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="dde0d-141">Meddelande</span><span class="sxs-lookup"><span data-stu-id="dde0d-141">Message</span></span> | <span data-ttu-id="dde0d-142">Igång (/ slutförda) anrop av ScriptBlock-ID: %1</span><span class="sxs-lookup"><span data-stu-id="dde0d-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="dde0d-143">Runspace ID: %2</span><span class="sxs-lookup"><span data-stu-id="dde0d-143">Runspace ID: %2</span></span> |

<span data-ttu-id="dde0d-144">ID: T är GUID som representerar skriptblocket (som kan korreleras med händelse-ID 0x1008) och Körningsutrymme-ID representerar runspace där skriptblocket kördes.</span><span class="sxs-lookup"><span data-stu-id="dde0d-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="dde0d-145">Procenttecken i anrop meddelandet representerar strukturerade ETW-egenskaper.</span><span class="sxs-lookup"><span data-stu-id="dde0d-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="dde0d-146">När de ersätts med de faktiska värdena i meddelandetexten, ett mer robust sätt att komma åt dem är att hämta meddelandet med cmdleten Get-WinEvent och sedan använda den **egenskaper** matris med meddelandet.</span><span class="sxs-lookup"><span data-stu-id="dde0d-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="dde0d-147">Här är ett exempel på hur den här funktionen kan hjälpa dig att packa upp angripare att kryptera och Förvräng ett skript:</span><span class="sxs-lookup"><span data-stu-id="dde0d-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

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

<span data-ttu-id="dde0d-148">Kör detta genererar följande loggposter:</span><span class="sxs-lookup"><span data-stu-id="dde0d-148">Running this generates the following log entries:</span></span>

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

Om skriptet Blockets längd överskrider vad ETW klarar av anläggning i en enda händelse, delar Windows PowerShell-skriptet i flera delar. <span data-ttu-id="dde0d-150">Här är exempelkod för att kombinera ett skript från dess loggmeddelanden:</span><span class="sxs-lookup"><span data-stu-id="dde0d-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="dde0d-151">Precis som med alla loggningssystem som har en begränsad kvarhållning buffert (d.v.s. ETW-loggar) är ett angrepp mot den här infrastrukturen att göra loggen med falska händelser att dölja tidigare bevis.</span><span class="sxs-lookup"><span data-stu-id="dde0d-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="dde0d-152">Om du vill skydda dig mot angrepp, kontrollera att du har någon form av händelseloggen samling konfigurera (t.ex, Windows vidarebefordran av händelser, [upptäcka angriparen med övervakning av Windows-händelseloggen](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) att flytta händelseloggar från datorn som snart som möjligt.</span><span class="sxs-lookup"><span data-stu-id="dde0d-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) to move event logs off of the computer as soon as possible.</span></span>
