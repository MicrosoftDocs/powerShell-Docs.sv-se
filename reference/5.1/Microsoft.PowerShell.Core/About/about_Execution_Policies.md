---
description: Beskriver körnings principerna för PowerShell och förklarar hur du hanterar dem.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Execution_Policies
ms.openlocfilehash: 3332adb76c76fa644d23060abe2af43bd45a15a6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272157"
---
# <a name="about-execution-policies"></a><span data-ttu-id="5a4c5-104">Om körnings principer</span><span class="sxs-lookup"><span data-stu-id="5a4c5-104">About Execution Policies</span></span>

## <a name="short-description"></a><span data-ttu-id="5a4c5-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="5a4c5-105">Short Description</span></span>

<span data-ttu-id="5a4c5-106">Beskriver körnings principerna för PowerShell och förklarar hur du hanterar dem.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-106">Describes the PowerShell execution policies and explains how to manage them.</span></span>

## <a name="long-description"></a><span data-ttu-id="5a4c5-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="5a4c5-107">Long Description</span></span>

<span data-ttu-id="5a4c5-108">PowerShell: s körnings princip är en säkerhetsfunktion som styr de villkor under vilka PowerShell läser in konfigurationsfiler och kör skript.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-108">PowerShell's execution policy is a safety feature that controls the conditions under which PowerShell loads configuration files and runs scripts.</span></span> <span data-ttu-id="5a4c5-109">Den här funktionen hjälper till att förhindra körning av skadliga skript.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-109">This feature helps prevent the execution of malicious scripts.</span></span>

<span data-ttu-id="5a4c5-110">På en Windows-dator kan du ange en körnings princip för den lokala datorn, för den aktuella användaren eller för en viss session.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-110">On a Windows computer you can set an execution policy for the local computer, for the current user, or for a particular session.</span></span> <span data-ttu-id="5a4c5-111">Du kan också använda en grupprincip inställning för att ange körnings principer för datorer och användare.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-111">You can also use a Group Policy setting to set execution policies for computers and users.</span></span>

<span data-ttu-id="5a4c5-112">Körnings principer för den lokala datorn och den aktuella användaren lagras i registret.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-112">Execution policies for the local computer and current user are stored in the registry.</span></span> <span data-ttu-id="5a4c5-113">Du behöver inte ange körnings principer i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-113">You don't need to set execution policies in your PowerShell profile.</span></span>
<span data-ttu-id="5a4c5-114">Körnings principen för en viss session lagras endast i minnet och går förlorad när sessionen stängs.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-114">The execution policy for a particular session is stored only in memory and is lost when the session is closed.</span></span>

<span data-ttu-id="5a4c5-115">Körnings principen är inte ett säkerhets system som begränsar användar åtgärder.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-115">The execution policy isn't a security system that restricts user actions.</span></span> <span data-ttu-id="5a4c5-116">Användare kan till exempel enkelt kringgå en princip genom att skriva skript innehållet på kommando raden när de inte kan köra ett skript.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-116">For example, users can easily bypass a policy by typing the script contents at the command line when they cannot run a script.</span></span> <span data-ttu-id="5a4c5-117">I stället hjälper körnings principen användarna att ange grundläggande regler och förhindrar att de bryter mot dem.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-117">Instead, the execution policy helps users to set basic rules and prevents them from violating them unintentionally.</span></span>

## <a name="powershell-execution-policies"></a><span data-ttu-id="5a4c5-118">Körnings principer för PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a4c5-118">PowerShell execution policies</span></span>

<span data-ttu-id="5a4c5-119">PowerShell-körnings principerna är följande:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-119">The PowerShell execution policies are as follows:</span></span>

### <a name="allsigned"></a><span data-ttu-id="5a4c5-120">AllSigned</span><span class="sxs-lookup"><span data-stu-id="5a4c5-120">AllSigned</span></span>

- <span data-ttu-id="5a4c5-121">Skript kan köras.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-121">Scripts can run.</span></span>
- <span data-ttu-id="5a4c5-122">Kräver att alla skript och konfigurationsfiler signeras av en betrodd utgivare, inklusive skript som du skriver på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-122">Requires that all scripts and configuration files be signed by a trusted publisher, including scripts that you write on the local computer.</span></span>
- <span data-ttu-id="5a4c5-123">Du får frågan innan du kör skript från utgivare som du ännu inte har klassificerat som betrott eller ej betrott.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-123">Prompts you before running scripts from publishers that you haven't yet classified as trusted or untrusted.</span></span>
- <span data-ttu-id="5a4c5-124">Risker som kör signerade, men skadliga, skript.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-124">Risks running signed, but malicious, scripts.</span></span>

### <a name="bypass"></a><span data-ttu-id="5a4c5-125">Förbikoppling</span><span class="sxs-lookup"><span data-stu-id="5a4c5-125">Bypass</span></span>

- <span data-ttu-id="5a4c5-126">Inget blockeras och det finns inga varningar eller prompter.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-126">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="5a4c5-127">Den här körnings principen är utformad för konfigurationer där ett PowerShell-skript är inbyggt i ett större program eller för konfigurationer där PowerShell är grunden för ett program som har en egen säkerhets modell.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-127">This execution policy is designed for configurations in which a PowerShell script is built in to a larger application or for configurations in which PowerShell is the foundation for a program that has its own security model.</span></span>

### <a name="default"></a><span data-ttu-id="5a4c5-128">Default</span><span class="sxs-lookup"><span data-stu-id="5a4c5-128">Default</span></span>

- <span data-ttu-id="5a4c5-129">Anger standard körnings principen.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-129">Sets the default execution policy.</span></span>
- <span data-ttu-id="5a4c5-130">**Begränsat** för Windows-klienter.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-130">**Restricted** for Windows clients.</span></span>
- <span data-ttu-id="5a4c5-131">**RemoteSigned** för Windows-servrar.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-131">**RemoteSigned** for Windows servers.</span></span>

### <a name="remotesigned"></a><span data-ttu-id="5a4c5-132">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="5a4c5-132">RemoteSigned</span></span>

- <span data-ttu-id="5a4c5-133">Standard körnings principen för Windows Server-datorer.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-133">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="5a4c5-134">Skript kan köras.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-134">Scripts can run.</span></span>
- <span data-ttu-id="5a4c5-135">Kräver en digital signatur från en betrodd utgivare på skript och konfigurationsfiler som hämtas från Internet, som inkluderar e-post och snabb meddelande program.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-135">Requires a digital signature from a trusted publisher on scripts and configuration files that are downloaded from the internet which includes email and instant messaging programs.</span></span>
- <span data-ttu-id="5a4c5-136">Kräver inte digitala signaturer i skript som är skrivna på den lokala datorn och som inte har hämtats från Internet.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-136">Doesn't require digital signatures on scripts that are written on the local computer and not downloaded from the internet.</span></span>
- <span data-ttu-id="5a4c5-137">Kör skript som hämtas från Internet och inte signerade, om skripten är avblockerade, till exempel genom att använda `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-137">Runs scripts that are downloaded from the internet and not signed, if the scripts are unblocked, such as by using the `Unblock-File` cmdlet.</span></span>
- <span data-ttu-id="5a4c5-138">Risker som kör osignerade skript från andra källor än Internet och signerade skript som kan vara skadliga.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-138">Risks running unsigned scripts from sources other than the internet and signed scripts that could be malicious.</span></span>

### <a name="restricted"></a><span data-ttu-id="5a4c5-139">Begränsade</span><span class="sxs-lookup"><span data-stu-id="5a4c5-139">Restricted</span></span>

- <span data-ttu-id="5a4c5-140">Standard körnings principen för Windows-klientdatorer.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-140">The default execution policy for Windows client computers.</span></span>
- <span data-ttu-id="5a4c5-141">Tillåter enskilda kommandon, men tillåter inte skript.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-141">Permits individual commands, but does not allow scripts.</span></span>
- <span data-ttu-id="5a4c5-142">Förhindrar körning av alla skriptfiler, inklusive formatering och konfigurationsfiler ( `.ps1xml` ), modulens skript fil ( `.psm1` ) och PowerShell-profiler ( `.ps1` ).</span><span class="sxs-lookup"><span data-stu-id="5a4c5-142">Prevents running of all script files, including formatting and configuration files (`.ps1xml`), module script files (`.psm1`), and PowerShell profiles (`.ps1`).</span></span>

### <a name="undefined"></a><span data-ttu-id="5a4c5-143">Undefined (Odefinierad)</span><span class="sxs-lookup"><span data-stu-id="5a4c5-143">Undefined</span></span>

- <span data-ttu-id="5a4c5-144">Ingen körnings princip har angetts i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-144">There is no execution policy set in the current scope.</span></span>
- <span data-ttu-id="5a4c5-145">Om körnings principen i alla omfattningar är **Odefinierad** , **begränsas** den effektiva körnings principen för Windows-klienter och **RemoteSigned** för Windows Server.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-145">If the execution policy in all scopes is **Undefined** , the effective execution policy is **Restricted** for Windows clients and **RemoteSigned** for Windows Server.</span></span>

### <a name="unrestricted"></a><span data-ttu-id="5a4c5-146">Obegränsat</span><span class="sxs-lookup"><span data-stu-id="5a4c5-146">Unrestricted</span></span>

- <span data-ttu-id="5a4c5-147">Osignerade skript kan köras.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-147">Unsigned scripts can run.</span></span> <span data-ttu-id="5a4c5-148">Det finns en risk för att skadliga skript körs.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-148">There is a risk of running malicious scripts.</span></span>
- <span data-ttu-id="5a4c5-149">Varnar användaren innan skript och konfigurationsfiler som inte kommer från zonen Lokalt intranät körs.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-149">Warns the user before running scripts and configuration files that are not from the local intranet zone.</span></span>

> [!NOTE]
> <span data-ttu-id="5a4c5-150">På system som inte skiljer Universal Naming Convention (UNC) sökvägar från Internet vägar kan skript som identifieras av en UNC-sökväg inte tillåtas att köras med **RemoteSigned** körnings princip.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-150">On systems that do not distinguish Universal Naming Convention (UNC) paths from internet paths, scripts that are identified by a UNC path might not be permitted to run with the **RemoteSigned** execution policy.</span></span>

## <a name="execution-policy-scope"></a><span data-ttu-id="5a4c5-151">Omfattning för körnings princip</span><span class="sxs-lookup"><span data-stu-id="5a4c5-151">Execution policy scope</span></span>

<span data-ttu-id="5a4c5-152">Du kan ange en princip för körning som bara är effektiv i ett visst omfång.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-152">You can set an execution policy that is effective only in a particular scope.</span></span>

<span data-ttu-id="5a4c5-153">Giltiga värden för **scope** är **MachinePolicy** , **UserPolicy** , **process** , **CurrentUser** och **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-153">The valid values for **Scope** are **MachinePolicy** , **UserPolicy** , **Process** , **CurrentUser** , and **LocalMachine**.</span></span> <span data-ttu-id="5a4c5-154">**LocalMachine** är standard när du anger en körnings princip.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-154">**LocalMachine** is the default when setting an execution policy.</span></span>

<span data-ttu-id="5a4c5-155">**Omfångs** värden visas i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-155">The **Scope** values are listed in precedence order.</span></span> <span data-ttu-id="5a4c5-156">Den princip som har företräde är gällande i den aktuella sessionen, även om en mer restriktiv princip har ställts in på en lägre prioritets nivå.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-156">The policy that takes precedence is effective in the current session, even if a more restrictive policy was set at a lower level of precedence.</span></span>

<span data-ttu-id="5a4c5-157">Mer information finns i [set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy).</span><span class="sxs-lookup"><span data-stu-id="5a4c5-157">For more information, see [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy).</span></span>

### <a name="machinepolicy"></a><span data-ttu-id="5a4c5-158">MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="5a4c5-158">MachinePolicy</span></span>

<span data-ttu-id="5a4c5-159">Anges av en grupprincip för alla användare av datorn.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-159">Set by a Group Policy for all users of the computer.</span></span>

### <a name="userpolicy"></a><span data-ttu-id="5a4c5-160">UserPolicy</span><span class="sxs-lookup"><span data-stu-id="5a4c5-160">UserPolicy</span></span>

<span data-ttu-id="5a4c5-161">Anges av en grupprincip för datorns aktuella användare.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-161">Set by a Group Policy for the current user of the computer.</span></span>

### <a name="process"></a><span data-ttu-id="5a4c5-162">Process</span><span class="sxs-lookup"><span data-stu-id="5a4c5-162">Process</span></span>

<span data-ttu-id="5a4c5-163">**Process** omfånget påverkar endast den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-163">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="5a4c5-164">Körnings principen sparas i miljövariabeln i `$env:PSExecutionPolicyPreference` stället för registret.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-164">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="5a4c5-165">När PowerShell-sessionen stängs raderas variabeln och värdet.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-165">When the PowerShell session is closed, the variable and value are deleted.</span></span>

### <a name="currentuser"></a><span data-ttu-id="5a4c5-166">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="5a4c5-166">CurrentUser</span></span>

<span data-ttu-id="5a4c5-167">Körnings principen påverkar endast den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-167">The execution policy affects only the current user.</span></span> <span data-ttu-id="5a4c5-168">Den lagras i **HKEY_CURRENT_USER** register under nyckel.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-168">It's stored in the **HKEY_CURRENT_USER** registry subkey.</span></span>

### <a name="localmachine"></a><span data-ttu-id="5a4c5-169">LocalMachine</span><span class="sxs-lookup"><span data-stu-id="5a4c5-169">LocalMachine</span></span>

<span data-ttu-id="5a4c5-170">Körnings principen påverkar alla användare på den aktuella datorn.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-170">The execution policy affects all users on the current computer.</span></span> <span data-ttu-id="5a4c5-171">Den lagras i **HKEY_LOCAL_MACHINE** register under nyckel.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-171">It's stored in the **HKEY_LOCAL_MACHINE** registry subkey.</span></span>

## <a name="managing-the-execution-policy-with-powershell"></a><span data-ttu-id="5a4c5-172">Hantera körnings principen med PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a4c5-172">Managing the execution policy with PowerShell</span></span>

<span data-ttu-id="5a4c5-173">Använd cmdleten för att få en effektiv körnings princip för den aktuella PowerShell-sessionen `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="5a4c5-173">To get the effective execution policy for the current PowerShell session, use the `Get-ExecutionPolicy` cmdlet.</span></span>

<span data-ttu-id="5a4c5-174">Följande kommando hämtar den effektiva körnings principen:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-174">The following command gets the effective execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="5a4c5-175">Så här hämtar du alla körnings principer som påverkar den aktuella sessionen och visar dem i prioritetsordning:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-175">To get all of the execution policies that affect the current session and display them in precedence order:</span></span>

```powershell
Get-ExecutionPolicy -List
```

<span data-ttu-id="5a4c5-176">Resultatet liknar följande exempel på utdata:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-176">The result looks similar to the following sample output:</span></span>

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       AllSigned
```

<span data-ttu-id="5a4c5-177">I det här fallet är den effektiva körnings principen **RemoteSigned** eftersom körnings principen för den aktuella användaren prioriteras över körnings principen som angetts för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-177">In this case, the effective execution policy is **RemoteSigned** because the execution policy for the current user takes precedence over the execution policy set for the local computer.</span></span>

<span data-ttu-id="5a4c5-178">Om du vill hämta körnings principen för ett visst omfång använder du **omfattnings** parametern för `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="5a4c5-178">To get the execution policy set for a particular scope, use the **Scope** parameter of `Get-ExecutionPolicy`.</span></span>

<span data-ttu-id="5a4c5-179">Följande kommando hämtar till exempel körnings principen för **CurrentUser** -omfånget:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-179">For example, the following command gets the execution policy for the **CurrentUser** scope:</span></span>

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

### <a name="change-the-execution-policy"></a><span data-ttu-id="5a4c5-180">Ändra körnings principen</span><span class="sxs-lookup"><span data-stu-id="5a4c5-180">Change the execution policy</span></span>

<span data-ttu-id="5a4c5-181">Använd cmdleten om du vill ändra körnings principen för PowerShell på Windows-datorn `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="5a4c5-181">To change the PowerShell execution policy on your Windows computer, use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="5a4c5-182">Ändringen träder i kraft omedelbart.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-182">The change is effective immediately.</span></span> <span data-ttu-id="5a4c5-183">Du behöver inte starta om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-183">You don't need to restart PowerShell.</span></span>

<span data-ttu-id="5a4c5-184">Om du anger körnings principen för omfattningarna **LocalMachine** eller **CurrentUser** sparas ändringen i registret och fortsätter att gälla tills du ändrar den igen.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-184">If you set the execution policy for the scopes **LocalMachine** or the **CurrentUser** , the change is saved in the registry and remains effective until you change it again.</span></span>

<span data-ttu-id="5a4c5-185">Om du anger körnings principen för **process** omfånget sparas den inte i registret.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-185">If you set the execution policy for the **Process** scope, it's not saved in the registry.</span></span> <span data-ttu-id="5a4c5-186">Körnings principen behålls tills den aktuella processen och eventuella underordnade processer stängs.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-186">The execution policy is retained until the current process and any child processes are closed.</span></span>

> [!NOTE]
> <span data-ttu-id="5a4c5-187">I Windows Vista och senare versioner av Windows kan du köra kommandon som ändrar körnings principen för den lokala datorn, **LocalMachine** scope, starta PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="5a4c5-187">In Windows Vista and later versions of Windows, to run commands that change the execution policy for the local computer, **LocalMachine** scope, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="5a4c5-188">Ändra körnings princip:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-188">To change your execution policy:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName>
```

<span data-ttu-id="5a4c5-189">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-189">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="5a4c5-190">Ange körnings principen i ett visst omfång:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-190">To set the execution policy in a particular scope:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName> -Scope <scope>
```

<span data-ttu-id="5a4c5-191">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-191">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

<span data-ttu-id="5a4c5-192">Ett kommando för att ändra en körnings princip kan lyckas men ändå inte ändra den effektiva körnings principen.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-192">A command to change an execution policy can succeed but still not change the effective execution policy.</span></span>

<span data-ttu-id="5a4c5-193">Till exempel kan ett kommando som anger körnings principen för den lokala datorn lyckas, men åsidosätts av körnings principen för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-193">For example, a command that sets the execution policy for the local computer can succeed but be overridden by the execution policy for the current user.</span></span>

### <a name="remove-the-execution-policy"></a><span data-ttu-id="5a4c5-194">Ta bort körnings principen</span><span class="sxs-lookup"><span data-stu-id="5a4c5-194">Remove the execution policy</span></span>

<span data-ttu-id="5a4c5-195">Om du vill ta bort körnings principen för ett visst omfång anger du att körnings principen ska vara **Odefinierad**.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-195">To remove the execution policy for a particular scope, set the execution policy to **Undefined**.</span></span>

<span data-ttu-id="5a4c5-196">Till exempel för att ta bort körnings principen för alla användare av den lokala datorn:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-196">For example, to remove the execution policy for all the users of the local computer:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope LocalMachine
```

<span data-ttu-id="5a4c5-197">Ta bort körnings principen för ett **omfång** :</span><span class="sxs-lookup"><span data-stu-id="5a4c5-197">To remove the execution policy for a **Scope** :</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

<span data-ttu-id="5a4c5-198">Om ingen körnings princip anges i någon omfattning är den effektiva körnings principen **begränsad** , vilket är standardinställningen för Windows-klienter.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-198">If no execution policy is set in any scope, the effective execution policy is **Restricted** , which is the default for Windows clients.</span></span>

### <a name="set-a-different-policy-for-one-session"></a><span data-ttu-id="5a4c5-199">Ange en annan princip för en session</span><span class="sxs-lookup"><span data-stu-id="5a4c5-199">Set a different policy for one session</span></span>

<span data-ttu-id="5a4c5-200">Du kan använda parametern **ExecutionPolicy** för **powershell.exe** om du vill ange en körnings princip för en ny PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-200">You can use the **ExecutionPolicy** parameter of **powershell.exe** to set an execution policy for a new PowerShell session.</span></span> <span data-ttu-id="5a4c5-201">Principen påverkar endast den aktuella sessionen och de underordnade sessionerna.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-201">The policy affects only the current session and child sessions.</span></span>

<span data-ttu-id="5a4c5-202">Ange körnings principen för en ny session genom att starta PowerShell på kommando raden, till exempel **cmd.exe** eller från PowerShell, och sedan använda parametern **ExecutionPolicy** för **powershell.exe** för att ange körnings principen.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-202">To set the execution policy for a new session, start PowerShell at the command line, such as **cmd.exe** or from PowerShell, and then use the **ExecutionPolicy** parameter of **powershell.exe** to set the execution policy.</span></span>

<span data-ttu-id="5a4c5-203">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-203">For example:</span></span>

```powershell
powershell.exe -ExecutionPolicy AllSigned
```

<span data-ttu-id="5a4c5-204">Den körnings princip som du anger lagras inte i registret.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-204">The execution policy that you set isn't stored in the registry.</span></span> <span data-ttu-id="5a4c5-205">I stället lagras den i `$env:PSExecutionPolicyPreference` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-205">Instead, it's stored in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="5a4c5-206">Variabeln tas bort när du stänger sessionen där principen har angetts.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-206">The variable is deleted when you close the session in which the policy is set.</span></span> <span data-ttu-id="5a4c5-207">Du kan inte ändra principen genom att redigera variabelvärdet.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-207">You cannot change the policy by editing the variable value.</span></span>

<span data-ttu-id="5a4c5-208">Under sessionen har körnings principen som ställts in för sessionen företräde framför en körnings princip som anges i registret för den lokala datorn eller den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-208">During the session, the execution policy that is set for the session takes precedence over an execution policy that is set in the registry for the local computer or current user.</span></span> <span data-ttu-id="5a4c5-209">Den har dock inte företräde framför körnings principen som angetts med hjälp av en grupprincip.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-209">However, it doesn't take precedence over the execution policy set by using a Group Policy.</span></span>

## <a name="use-group-policy-to-manage-execution-policy"></a><span data-ttu-id="5a4c5-210">Använd grupprincip för att hantera körnings principen</span><span class="sxs-lookup"><span data-stu-id="5a4c5-210">Use Group Policy to Manage Execution Policy</span></span>

<span data-ttu-id="5a4c5-211">Du kan använda inställningen **Aktivera** körning av skript grupprincip för att hantera körnings principen för datorer i företaget.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-211">You can use the **Turn on Script Execution** Group Policy setting to manage the execution policy of computers in your enterprise.</span></span> <span data-ttu-id="5a4c5-212">Inställningen grupprincip åsidosätter körnings principerna som angetts i PowerShell i alla omfång.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-212">The Group Policy setting overrides the execution policies set in PowerShell in all scopes.</span></span>

<span data-ttu-id="5a4c5-213">Inställningarna för att **Aktivera skript körnings** principer är följande:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-213">The **Turn on Script Execution** policy settings are as follows:</span></span>

- <span data-ttu-id="5a4c5-214">Om du inaktiverar **Aktivera skript körning** körs inte skripten.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-214">If you disable **Turn on Script Execution** , scripts do not run.</span></span> <span data-ttu-id="5a4c5-215">Detta motsvarar principen för **begränsade** körningar.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-215">This is equivalent to the **Restricted** execution policy.</span></span>
- <span data-ttu-id="5a4c5-216">Om du aktiverar **Aktivera skript körning** kan du välja en körnings princip.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-216">If you enable **Turn on Script Execution** , you can select an execution policy.</span></span> <span data-ttu-id="5a4c5-217">Grupprincip inställningarna motsvarar följande princip inställningar för körning:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-217">The Group Policy settings are equivalent to the following execution policy settings:</span></span>

  | <span data-ttu-id="5a4c5-218">Grupprincip</span><span class="sxs-lookup"><span data-stu-id="5a4c5-218">Group Policy</span></span>                                  | <span data-ttu-id="5a4c5-219">Körnings princip</span><span class="sxs-lookup"><span data-stu-id="5a4c5-219">Execution Policy</span></span> |
  | --------------------------------------------- | ---------------- |
  | <span data-ttu-id="5a4c5-220">Tillåt alla skript</span><span class="sxs-lookup"><span data-stu-id="5a4c5-220">Allow all scripts</span></span>                             | <span data-ttu-id="5a4c5-221">Obegränsat</span><span class="sxs-lookup"><span data-stu-id="5a4c5-221">Unrestricted</span></span>     |
  | <span data-ttu-id="5a4c5-222">Tillåt lokala skript och fjärrsignerade skript</span><span class="sxs-lookup"><span data-stu-id="5a4c5-222">Allow local scripts and remote signed scripts</span></span> | <span data-ttu-id="5a4c5-223">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="5a4c5-223">RemoteSigned</span></span>     |
  | <span data-ttu-id="5a4c5-224">Tillåt endast signerade skript</span><span class="sxs-lookup"><span data-stu-id="5a4c5-224">Allow only signed scripts</span></span>                     | <span data-ttu-id="5a4c5-225">AllSigned</span><span class="sxs-lookup"><span data-stu-id="5a4c5-225">AllSigned</span></span>        |

- <span data-ttu-id="5a4c5-226">Om **Aktivera skript körning** inte har kon figurer ATS har det ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-226">If **Turn on Script Execution** is not configured, it has no effect.</span></span> <span data-ttu-id="5a4c5-227">Körnings principen som angetts i PowerShell är effektiv.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-227">The execution policy set in PowerShell is effective.</span></span>

<span data-ttu-id="5a4c5-228">Filerna PowerShellExecutionPolicy. adm och PowerShellExecutionPolicy. admx lägger till **Aktivera skript körnings** principen i noderna dator konfiguration och användar konfiguration i grupprincip redigeraren i följande sökvägar.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-228">The PowerShellExecutionPolicy.adm and PowerShellExecutionPolicy.admx files add the **Turn on Script Execution** policy to the Computer Configuration and User Configuration nodes in Group Policy Editor in the following paths.</span></span>

<span data-ttu-id="5a4c5-229">För Windows XP och Windows Server 2003:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-229">For Windows XP and Windows Server 2003:</span></span>

<span data-ttu-id="5a4c5-230">Administrativa Mallar\windows-komponenter\Windows-PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a4c5-230">Administrative Templates\Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="5a4c5-231">För Windows Vista och senare versioner av Windows:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-231">For Windows Vista and later versions of Windows:</span></span>

<span data-ttu-id="5a4c5-232">Administrativ Templates\Classic Administrativa mallar </span><span class="sxs-lookup"><span data-stu-id="5a4c5-232">Administrative Templates\Classic Administrative Templates</span></span>\
<span data-ttu-id="5a4c5-233">Windows Mallar\windows-komponenter\Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a4c5-233">Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="5a4c5-234">Principer som anges i noden dator konfiguration åsidosätter principer som angetts i noden användar konfiguration.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-234">Policies set in the Computer Configuration node take precedence over policies set in the User Configuration node.</span></span>

<span data-ttu-id="5a4c5-235">Mer information finns i [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span><span class="sxs-lookup"><span data-stu-id="5a4c5-235">For more information, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

### <a name="execution-policy-precedence"></a><span data-ttu-id="5a4c5-236">Princip prioritet för körning</span><span class="sxs-lookup"><span data-stu-id="5a4c5-236">Execution policy precedence</span></span>

<span data-ttu-id="5a4c5-237">När du bestämmer den effektiva körnings principen för en session, utvärderar PowerShell körnings principerna i följande prioritetsordning:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-237">When determining the effective execution policy for a session, PowerShell evaluates the execution policies in the following precedence order:</span></span>

- <span data-ttu-id="5a4c5-238">Grupprincip: MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="5a4c5-238">Group Policy: MachinePolicy</span></span>
- <span data-ttu-id="5a4c5-239">Grupprincip: UserPolicy</span><span class="sxs-lookup"><span data-stu-id="5a4c5-239">Group Policy: UserPolicy</span></span>
- <span data-ttu-id="5a4c5-240">Körnings princip: process (eller `powershell.exe -ExecutionPolicy` )</span><span class="sxs-lookup"><span data-stu-id="5a4c5-240">Execution Policy: Process (or `powershell.exe -ExecutionPolicy`)</span></span>
- <span data-ttu-id="5a4c5-241">Körnings princip: CurrentUser</span><span class="sxs-lookup"><span data-stu-id="5a4c5-241">Execution Policy: CurrentUser</span></span>
- <span data-ttu-id="5a4c5-242">Körnings princip: LocalMachine</span><span class="sxs-lookup"><span data-stu-id="5a4c5-242">Execution Policy: LocalMachine</span></span>

## <a name="manage-signed-and-unsigned-scripts"></a><span data-ttu-id="5a4c5-243">Hantera signerade och osignerade skript</span><span class="sxs-lookup"><span data-stu-id="5a4c5-243">Manage signed and unsigned scripts</span></span>

<span data-ttu-id="5a4c5-244">I Windows lägger program som Internet Explorer och Microsoft Edge till en alternativ data ström till filer som hämtas.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-244">In Windows, programs like Internet Explorer and Microsoft Edge add an alternate data stream to files that are downloaded.</span></span> <span data-ttu-id="5a4c5-245">Detta markerar filen som "kommer från Internet".</span><span class="sxs-lookup"><span data-stu-id="5a4c5-245">This marks the file as "coming from the Internet".</span></span> <span data-ttu-id="5a4c5-246">Om din PowerShell-körnings princip är **RemoteSigned** kör PowerShell inte osignerade skript som hämtas från Internet, som innehåller e-post och snabb meddelande program.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-246">If your PowerShell execution policy is **RemoteSigned** , PowerShell won't run unsigned scripts that are downloaded from the internet which includes email and instant messaging programs.</span></span>

<span data-ttu-id="5a4c5-247">Du kan signera skriptet eller välja att köra ett osignerat skript utan att ändra körnings principen.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-247">You can sign the script or elect to run an unsigned script without changing the execution policy.</span></span>

<span data-ttu-id="5a4c5-248">Från och med PowerShell 3,0 kan du använda cmdleten **Stream** för `Get-Item` att identifiera filer som blockeras eftersom de har hämtats från Internet.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-248">Beginning in PowerShell 3.0, you can use the **Stream** parameter of the `Get-Item` cmdlet to detect files that are blocked because they were downloaded from the internet.</span></span> <span data-ttu-id="5a4c5-249">Använd `Unblock-File` cmdleten för att avblockera skripten så att du kan köra dem i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-249">Use the `Unblock-File` cmdlet to unblock the scripts so that you can run them in PowerShell.</span></span>

<span data-ttu-id="5a4c5-250">Mer information finns i [about_Signing](about_Signing.md), [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)och [unblock-File](xref:Microsoft.PowerShell.Utility.Unblock-File).</span><span class="sxs-lookup"><span data-stu-id="5a4c5-250">For more information, see [about_Signing](about_Signing.md), [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item), and [Unblock-File](xref:Microsoft.PowerShell.Utility.Unblock-File).</span></span>

> [!NOTE]
> <span data-ttu-id="5a4c5-251">Andra metoder för att hämta filer kanske inte markerar filerna som de kommer från zonen Internet.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-251">Other methods of downloading files may not mark the files as coming from the Internet Zone.</span></span> <span data-ttu-id="5a4c5-252">Några exempel är:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-252">Some examples include:</span></span>
>
> - `curl.exe`
> - `Invoke-RestMethod`
> - `Invoke-WebRequest`

## <a name="execution-policy-on-windows-server-core-and-window-nano-server"></a><span data-ttu-id="5a4c5-253">Körnings princip på Windows Server Core och Window Nano Server</span><span class="sxs-lookup"><span data-stu-id="5a4c5-253">Execution policy on Windows Server Core and Window Nano Server</span></span>

<span data-ttu-id="5a4c5-254">När PowerShell 5,1 körs på Windows Server Core eller Windows Nano Server under vissa förhållanden, kan körnings principer inte köras med följande fel:</span><span class="sxs-lookup"><span data-stu-id="5a4c5-254">When PowerShell 5.1 is run on Windows Server Core or Windows Nano Server under certain conditions, execution policies can fail with the following error:</span></span>

```Output
AuthorizationManager check failed.
At line:1 char:1
+ C:\scriptpath\scriptname.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<span data-ttu-id="5a4c5-255">PowerShell använder API: er i Windows Skriv bords gränssnitt ( `explorer.exe` ) för att verifiera zonen i en skript fil.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-255">PowerShell uses APIs in the Windows Desktop Shell (`explorer.exe`) to validate the Zone of a script file.</span></span> <span data-ttu-id="5a4c5-256">Windows-gränssnittet är inte tillgängligt på Windows Server Core och Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-256">The Windows Shell is not available on Windows Server Core and Windows Nano Server.</span></span>

<span data-ttu-id="5a4c5-257">Du kan också få det här felet på ett Windows-system om Windows Desktop Shell inte är tillgänglig eller inte svarar.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-257">You could also get this error on any Windows system if the Windows Desktop Shell is unavailable or unresponsive.</span></span> <span data-ttu-id="5a4c5-258">Vid inloggning kan exempelvis ett PowerShell-inloggningsnamn starta körningen innan Windows-skrivbordet är klart, vilket resulterar i ett haveri.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-258">For example, during sign on, a PowerShell logon script could start execution before the Windows Desktop is ready, resulting in failure.</span></span>

<span data-ttu-id="5a4c5-259">Om du använder en körnings princip för **bypass** eller **AllSigned** krävs ingen zon kontroll som undviker problemet.</span><span class="sxs-lookup"><span data-stu-id="5a4c5-259">Using an execution policy of **ByPass** or **AllSigned** does not require a Zone check which avoids the problem.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a4c5-260">Se även</span><span class="sxs-lookup"><span data-stu-id="5a4c5-260">See Also</span></span>

[<span data-ttu-id="5a4c5-261">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="5a4c5-261">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="5a4c5-262">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="5a4c5-262">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="5a4c5-263">about_Signing</span><span class="sxs-lookup"><span data-stu-id="5a4c5-263">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="5a4c5-264">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="5a4c5-264">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="5a4c5-265">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="5a4c5-265">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

[<span data-ttu-id="5a4c5-266">PowerShell.exe Command-Line hjälp</span><span class="sxs-lookup"><span data-stu-id="5a4c5-266">PowerShell.exe Command-Line Help</span></span>](about_PowerShell_exe.md)

[<span data-ttu-id="5a4c5-267">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="5a4c5-267">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="5a4c5-268">Avblockera – fil</span><span class="sxs-lookup"><span data-stu-id="5a4c5-268">Unblock-File</span></span>](xref:Microsoft.PowerShell.Utility.Unblock-File)
