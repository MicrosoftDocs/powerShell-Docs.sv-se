---
description: Förklarar hur du använder funktionen "kör med PowerShell" för att köra ett skript från en fil system enhet.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_run_with_powershell?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Run_With_PowerShell
ms.openlocfilehash: 83931fcfcc89340b1d4958e41cb182642a554737
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272312"
---
# <a name="about-run-with-powershell"></a><span data-ttu-id="15623-104">Om att köra med PowerShell</span><span class="sxs-lookup"><span data-stu-id="15623-104">About Run With PowerShell</span></span>

## <a name="short-description"></a><span data-ttu-id="15623-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="15623-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="15623-106">Förklarar hur du använder funktionen "kör med PowerShell" för att köra ett skript från en fil system enhet.</span><span class="sxs-lookup"><span data-stu-id="15623-106">Explains how to use the "Run with PowerShell" feature to run a script from a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="15623-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="15623-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="15623-108">Från och med Windows PowerShell 3,0 kan du använda funktionen "kör med PowerShell" för att köra skript från Utforskaren i Windows 8 och Windows Server 2012 och från Utforskaren i tidigare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="15623-108">Beginning in Windows PowerShell 3.0, you can use the "Run with PowerShell" feature to run scripts from File Explorer in Windows 8 and Windows Server 2012 and from Windows Explorer in earlier versions of Windows.</span></span>

<span data-ttu-id="15623-109">Funktionen "kör med PowerShell" är utformad för att köra skript som inte har nödvändiga parametrar och som inte returnerar utdata till kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="15623-109">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="15623-110">När du använder funktionen "kör med PowerShell" visas fönstret PowerShell-konsol bara kort, om det finns.</span><span class="sxs-lookup"><span data-stu-id="15623-110">When you use the "Run with PowerShell" feature, the PowerShell console window appears only briefly, if at all.</span></span> <span data-ttu-id="15623-111">Du kan inte interagera med den.</span><span class="sxs-lookup"><span data-stu-id="15623-111">You cannot interact with it.</span></span>

<span data-ttu-id="15623-112">Använda funktionen "kör med PowerShell":</span><span class="sxs-lookup"><span data-stu-id="15623-112">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="15623-113">I Utforskaren (eller Utforskaren) högerklickar du på skript filens namn och väljer sedan kör med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15623-113">In File Explorer (or Windows Explorer), right-click the script file name and then select "Run with PowerShell".</span></span>

<span data-ttu-id="15623-114">Funktionen "kör med PowerShell" startar en PowerShell-session som har en körnings princip som kringgås, kör skriptet och stänger sessionen.</span><span class="sxs-lookup"><span data-stu-id="15623-114">The "Run with PowerShell" feature starts a PowerShell session that has an execution policy of Bypass, runs the script, and closes the session.</span></span>

<span data-ttu-id="15623-115">Det kör ett kommando med följande format:</span><span class="sxs-lookup"><span data-stu-id="15623-115">It runs a command that has the following format:</span></span>

```
PowerShell.exe -File <FileName> -ExecutionPolicy Bypass
```

<span data-ttu-id="15623-116">"Kör med PowerShell" ställer bara in principen för att kringgå körning för sessionen (den aktuella instansen av PowerShell-processen) som skriptet körs i.</span><span class="sxs-lookup"><span data-stu-id="15623-116">"Run with PowerShell" sets the Bypass execution policy only for the session (the current instance of the PowerShell process) in which the script runs.</span></span>
<span data-ttu-id="15623-117">Den här funktionen ändrar inte körnings principen för datorn eller användaren.</span><span class="sxs-lookup"><span data-stu-id="15623-117">This feature does not change the execution policy for the computer or the user.</span></span>

<span data-ttu-id="15623-118">Funktionen "kör med PowerShell" påverkas bara av AllSigned-körnings principen.</span><span class="sxs-lookup"><span data-stu-id="15623-118">The "Run with PowerShell" feature is affected only by the AllSigned execution policy.</span></span> <span data-ttu-id="15623-119">Om körnings principen för AllSigned är effektiv för datorn eller användaren, kör med PowerShell bara signerade skript.</span><span class="sxs-lookup"><span data-stu-id="15623-119">If the AllSigned execution policy is effective for the computer or the user, "Run with PowerShell" runs only signed scripts.</span></span> <span data-ttu-id="15623-120">"Kör med PowerShell" påverkas inte av någon annan körnings princip.</span><span class="sxs-lookup"><span data-stu-id="15623-120">"Run with PowerShell" is not affected by any other execution policy.</span></span> <span data-ttu-id="15623-121">Mer information finns i [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="15623-121">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="15623-122">Fel söknings meddelande: kör med PowerShell kommando kan du uppmanas att bekräfta körnings princip ändringen.</span><span class="sxs-lookup"><span data-stu-id="15623-122">Troubleshooting Note: Run with PowerShell command might prompt you to confirm the execution policy change.</span></span>

## <a name="see-also"></a><span data-ttu-id="15623-123">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="15623-123">SEE ALSO</span></span>

[<span data-ttu-id="15623-124">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="15623-124">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="15623-125">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="15623-125">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="15623-126">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="15623-126">about_Scripts</span></span>](about_Scripts.md)

