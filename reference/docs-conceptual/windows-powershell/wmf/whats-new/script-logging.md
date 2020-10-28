---
ms.date: 06/12/2017
title: Skriptspårning och -loggning
description: Windows PowerShell 5. x lägger till ny händelse loggning som gör att du kan granska skript block körning.
ms.openlocfilehash: d47fb6fdd1ee4b9372fab7b81e6dc94fb45b8880
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663123"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="fdb94-103">Skriptspårning och -loggning</span><span class="sxs-lookup"><span data-stu-id="fdb94-103">Script Tracing and Logging</span></span>

<span data-ttu-id="fdb94-104">Även om PowerShell redan har inställningen **LogPipelineExecutionDetails** grupprincip för att logga anropet av cmdlets, har PowerShell: s skript språk flera funktioner som du kanske vill logga och granska.</span><span class="sxs-lookup"><span data-stu-id="fdb94-104">While PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell's scripting language has several features that you might want to log and audit.</span></span> <span data-ttu-id="fdb94-105">Den nya detaljerade skript spårnings funktionen ger detaljerad spårning och analys av PowerShell-skript aktivitet på ett system.</span><span class="sxs-lookup"><span data-stu-id="fdb94-105">The new Detailed Script Tracing feature provides detailed tracking and analysis of PowerShell script activity on a system.</span></span> <span data-ttu-id="fdb94-106">När du har aktiverat detaljerad skript spårning loggar PowerShell alla skript block till ETW-händelseloggen, **Microsoft-Windows-PowerShell/Operational** .</span><span class="sxs-lookup"><span data-stu-id="fdb94-106">After enabling detailed script tracing, PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational** .</span></span> <span data-ttu-id="fdb94-107">Om ett skript block skapar ett annat skript block, till exempel genom `Invoke-Expression` att anropa, loggas även det anropade skript blocket.</span><span class="sxs-lookup"><span data-stu-id="fdb94-107">If a script block creates another script block, for example, by calling `Invoke-Expression`, the invoked script block also logged.</span></span>

<span data-ttu-id="fdb94-108">Loggning har Aktiver ATS med inställningen **Aktivera PowerShell-skript block loggning** Grupprincip i **administrativa mallar**  ->  **Windows-komponenter**  ->  **Windows PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="fdb94-108">Logging is enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting in **Administrative Templates** -> **Windows Components** -> **Windows PowerShell** .</span></span>

<span data-ttu-id="fdb94-109">Händelserna är:</span><span class="sxs-lookup"><span data-stu-id="fdb94-109">The events are:</span></span>

| <span data-ttu-id="fdb94-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="fdb94-110">Channel</span></span> |                               <span data-ttu-id="fdb94-111">Operativ</span><span class="sxs-lookup"><span data-stu-id="fdb94-111">Operational</span></span>                               |
| ------- | ----------------------------------------------------------------------- |
| <span data-ttu-id="fdb94-112">Nivå</span><span class="sxs-lookup"><span data-stu-id="fdb94-112">Level</span></span>   | <span data-ttu-id="fdb94-113">Verbose</span><span class="sxs-lookup"><span data-stu-id="fdb94-113">Verbose</span></span>                                                                 |
| <span data-ttu-id="fdb94-114">Opcode</span><span class="sxs-lookup"><span data-stu-id="fdb94-114">Opcode</span></span>  | <span data-ttu-id="fdb94-115">Skapa</span><span class="sxs-lookup"><span data-stu-id="fdb94-115">Create</span></span>                                                                  |
| <span data-ttu-id="fdb94-116">Uppgift</span><span class="sxs-lookup"><span data-stu-id="fdb94-116">Task</span></span>    | <span data-ttu-id="fdb94-117">CommandStart</span><span class="sxs-lookup"><span data-stu-id="fdb94-117">CommandStart</span></span>                                                            |
| <span data-ttu-id="fdb94-118">Följt</span><span class="sxs-lookup"><span data-stu-id="fdb94-118">Keyword</span></span> | <span data-ttu-id="fdb94-119">Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="fdb94-119">Runspace</span></span>                                                                |
| <span data-ttu-id="fdb94-120">EventId</span><span class="sxs-lookup"><span data-stu-id="fdb94-120">EventId</span></span> | <span data-ttu-id="fdb94-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="fdb94-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>                              |
| <span data-ttu-id="fdb94-122">Meddelande</span><span class="sxs-lookup"><span data-stu-id="fdb94-122">Message</span></span> | <span data-ttu-id="fdb94-123">Skapar script block-text (%1 av %2):</span><span class="sxs-lookup"><span data-stu-id="fdb94-123">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="fdb94-124">%3</span><span class="sxs-lookup"><span data-stu-id="fdb94-124">%3</span></span> </br> <span data-ttu-id="fdb94-125">Script block-ID: %4</span><span class="sxs-lookup"><span data-stu-id="fdb94-125">ScriptBlock ID: %4</span></span> |

<span data-ttu-id="fdb94-126">Texten som är inbäddad i meddelandet är den kompilerade skript blockets omfattning.</span><span class="sxs-lookup"><span data-stu-id="fdb94-126">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="fdb94-127">ID är ett GUID som behålls för skript blockets livs längd.</span><span class="sxs-lookup"><span data-stu-id="fdb94-127">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="fdb94-128">När du aktiverar utförlig loggning skriver funktionen start-och slut markörer:</span><span class="sxs-lookup"><span data-stu-id="fdb94-128">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="fdb94-129">Kanal</span><span class="sxs-lookup"><span data-stu-id="fdb94-129">Channel</span></span> |                                 <span data-ttu-id="fdb94-130">Operativ</span><span class="sxs-lookup"><span data-stu-id="fdb94-130">Operational</span></span>                                |
| ------- | -------------------------------------------------------------------------- |
| <span data-ttu-id="fdb94-131">Nivå</span><span class="sxs-lookup"><span data-stu-id="fdb94-131">Level</span></span>   | <span data-ttu-id="fdb94-132">Verbose</span><span class="sxs-lookup"><span data-stu-id="fdb94-132">Verbose</span></span>                                                                    |
| <span data-ttu-id="fdb94-133">Opcode</span><span class="sxs-lookup"><span data-stu-id="fdb94-133">Opcode</span></span>  | <span data-ttu-id="fdb94-134">Öppna/Stäng</span><span class="sxs-lookup"><span data-stu-id="fdb94-134">Open / Close</span></span>                                                               |
| <span data-ttu-id="fdb94-135">Uppgift</span><span class="sxs-lookup"><span data-stu-id="fdb94-135">Task</span></span>    | <span data-ttu-id="fdb94-136">CommandStart / CommandStop</span><span class="sxs-lookup"><span data-stu-id="fdb94-136">CommandStart / CommandStop</span></span>                                                 |
| <span data-ttu-id="fdb94-137">Följt</span><span class="sxs-lookup"><span data-stu-id="fdb94-137">Keyword</span></span> | <span data-ttu-id="fdb94-138">Körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="fdb94-138">Runspace</span></span>                                                                   |
| <span data-ttu-id="fdb94-139">EventId</span><span class="sxs-lookup"><span data-stu-id="fdb94-139">EventId</span></span> | <span data-ttu-id="fdb94-140">\_Start information för script block Invoke \_ \_ (0x1009 = 4105)/</span><span class="sxs-lookup"><span data-stu-id="fdb94-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="fdb94-141">Script block \_ anropa \_ fullständig \_ detalj (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="fdb94-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="fdb94-142">Meddelande</span><span class="sxs-lookup"><span data-stu-id="fdb94-142">Message</span></span> | <span data-ttu-id="fdb94-143">Startade/slutfört anrop av script block-ID: %1</span><span class="sxs-lookup"><span data-stu-id="fdb94-143">Started / Completed invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="fdb94-144">Körnings utrymme-ID: %2</span><span class="sxs-lookup"><span data-stu-id="fdb94-144">Runspace ID: %2</span></span> |

<span data-ttu-id="fdb94-145">ID: t är det GUID som representerar skript blocket (som kan korreleras med händelse-ID 0x1008) och körnings utrymme-ID: t representerar den körnings utrymme som det här skript blocket kördes i.</span><span class="sxs-lookup"><span data-stu-id="fdb94-145">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="fdb94-146">Procent tecken i anrops meddelandet representerar strukturerade ETW-egenskaper.</span><span class="sxs-lookup"><span data-stu-id="fdb94-146">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="fdb94-147">Medan de ersätts med de faktiska värdena i meddelande texten, är ett mer robust sätt att komma åt dem att hämta meddelandet med Get-WinEvent-cmdlet och sedan använda meddelandets **egenskaps** mat ris.</span><span class="sxs-lookup"><span data-stu-id="fdb94-147">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="fdb94-148">Här är ett exempel på hur den här funktionen kan hjälpa dig att packa upp ett skadligt försök att kryptera och obfuscate ett skript:</span><span class="sxs-lookup"><span data-stu-id="fdb94-148">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

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

<span data-ttu-id="fdb94-149">Om du kör detta genereras följande logg poster:</span><span class="sxs-lookup"><span data-stu-id="fdb94-149">Running this generates the following log entries:</span></span>

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

Om skript blockets längd överskrider kapaciteten för en enskild händelse, bryter PowerShell skriptet till flera delar. <span data-ttu-id="fdb94-151">Här är exempel kod för att kombinera ett skript från dess logg meddelanden:</span><span class="sxs-lookup"><span data-stu-id="fdb94-151">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="fdb94-152">Precis som med alla loggnings system som har en begränsad kvarhållning, är ett sätt att attackera den här infrastrukturen att överbelasta loggen med spurious-händelser för att dölja tidigare bevis.</span><span class="sxs-lookup"><span data-stu-id="fdb94-152">As with all logging systems that have a limited retention buffer, one way to attack this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="fdb94-153">Om du vill skydda dig från den här angreppet måste du se till att du har en viss typ av händelse logg samling konfigurera vidarebefordring av Windows-händelser.</span><span class="sxs-lookup"><span data-stu-id="fdb94-153">To protect yourself from this attack, ensure that you have some form of event log collection set up Windows Event Forwarding.</span></span> <span data-ttu-id="fdb94-154">Mer information finns i [upptäcka angripare med Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span><span class="sxs-lookup"><span data-stu-id="fdb94-154">For more information, see [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span></span>
