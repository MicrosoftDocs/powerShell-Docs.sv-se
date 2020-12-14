---
description: Förklarar hur du använder funktionen kör med PowerShell för att köra ett skript från en fil system enhet.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_run_with_powershell?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Run_With_PowerShell
ms.openlocfilehash: 7070fa2bc8bb30e83f59e3d1193faa3a8495f109
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710969"
---
# <a name="about-run-with-powershell"></a><span data-ttu-id="2ce38-103">Om att köra med PowerShell</span><span class="sxs-lookup"><span data-stu-id="2ce38-103">About Run With PowerShell</span></span>

## <a name="short-description"></a><span data-ttu-id="2ce38-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2ce38-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="2ce38-105">Förklarar hur du använder funktionen "kör med PowerShell" för att köra ett skript från en fil system enhet.</span><span class="sxs-lookup"><span data-stu-id="2ce38-105">Explains how to use the "Run with PowerShell" feature to run a script from a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="2ce38-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2ce38-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="2ce38-107">Från och med Windows PowerShell 3,0 kan du använda funktionen "kör med PowerShell" för att köra skript från Utforskaren i Windows 8 och Windows Server 2012 och från Utforskaren i tidigare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="2ce38-107">Beginning in Windows PowerShell 3.0, you can use the "Run with PowerShell" feature to run scripts from File Explorer in Windows 8 and Windows Server 2012 and from Windows Explorer in earlier versions of Windows.</span></span>

<span data-ttu-id="2ce38-108">Funktionen "kör med PowerShell" är utformad för att köra skript som inte har nödvändiga parametrar och som inte returnerar utdata till kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="2ce38-108">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="2ce38-109">När du använder funktionen "kör med PowerShell" visas fönstret PowerShell-konsol bara kort, om det finns.</span><span class="sxs-lookup"><span data-stu-id="2ce38-109">When you use the "Run with PowerShell" feature, the PowerShell console window appears only briefly, if at all.</span></span> <span data-ttu-id="2ce38-110">Du kan inte interagera med den.</span><span class="sxs-lookup"><span data-stu-id="2ce38-110">You cannot interact with it.</span></span>

<span data-ttu-id="2ce38-111">Använda funktionen "kör med PowerShell":</span><span class="sxs-lookup"><span data-stu-id="2ce38-111">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="2ce38-112">I Utforskaren (eller Utforskaren) högerklickar du på skript filens namn och väljer sedan kör med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ce38-112">In File Explorer (or Windows Explorer), right-click the script file name and then select "Run with PowerShell".</span></span>

<span data-ttu-id="2ce38-113">Funktionen "kör med PowerShell" startar en PowerShell-session som har en körnings princip som kringgås, kör skriptet och stänger sessionen.</span><span class="sxs-lookup"><span data-stu-id="2ce38-113">The "Run with PowerShell" feature starts a PowerShell session that has an execution policy of Bypass, runs the script, and closes the session.</span></span>

<span data-ttu-id="2ce38-114">Det kör ett kommando med följande format:</span><span class="sxs-lookup"><span data-stu-id="2ce38-114">It runs a command that has the following format:</span></span>

```
PowerShell.exe -File <FileName> -ExecutionPolicy Bypass
```

<span data-ttu-id="2ce38-115">"Kör med PowerShell" ställer bara in principen för att kringgå körning för sessionen (den aktuella instansen av PowerShell-processen) som skriptet körs i.</span><span class="sxs-lookup"><span data-stu-id="2ce38-115">"Run with PowerShell" sets the Bypass execution policy only for the session (the current instance of the PowerShell process) in which the script runs.</span></span>
<span data-ttu-id="2ce38-116">Den här funktionen ändrar inte körnings principen för datorn eller användaren.</span><span class="sxs-lookup"><span data-stu-id="2ce38-116">This feature does not change the execution policy for the computer or the user.</span></span>

<span data-ttu-id="2ce38-117">Funktionen "kör med PowerShell" påverkas bara av AllSigned-körnings principen.</span><span class="sxs-lookup"><span data-stu-id="2ce38-117">The "Run with PowerShell" feature is affected only by the AllSigned execution policy.</span></span> <span data-ttu-id="2ce38-118">Om körnings principen för AllSigned är effektiv för datorn eller användaren, kör med PowerShell bara signerade skript.</span><span class="sxs-lookup"><span data-stu-id="2ce38-118">If the AllSigned execution policy is effective for the computer or the user, "Run with PowerShell" runs only signed scripts.</span></span> <span data-ttu-id="2ce38-119">"Kör med PowerShell" påverkas inte av någon annan körnings princip.</span><span class="sxs-lookup"><span data-stu-id="2ce38-119">"Run with PowerShell" is not affected by any other execution policy.</span></span> <span data-ttu-id="2ce38-120">Mer information finns i [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="2ce38-120">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="2ce38-121">Fel söknings meddelande: kör med PowerShell kommando kan du uppmanas att bekräfta körnings princip ändringen.</span><span class="sxs-lookup"><span data-stu-id="2ce38-121">Troubleshooting Note: Run with PowerShell command might prompt you to confirm the execution policy change.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ce38-122">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="2ce38-122">SEE ALSO</span></span>

[<span data-ttu-id="2ce38-123">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="2ce38-123">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="2ce38-124">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="2ce38-124">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="2ce38-125">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="2ce38-125">about_Scripts</span></span>](about_Scripts.md)

