---
description: Beskriver körnings principerna för PowerShell och förklarar hur du hanterar dem.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Execution_Policies
ms.openlocfilehash: 6c2d4b784c68649ea88e744a9cf5df6329ac897f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271070"
---
# <a name="about-execution-policies"></a><span data-ttu-id="73ae0-104">Om körnings principer</span><span class="sxs-lookup"><span data-stu-id="73ae0-104">About Execution Policies</span></span>

## <a name="short-description"></a><span data-ttu-id="73ae0-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="73ae0-105">Short Description</span></span>
<span data-ttu-id="73ae0-106">Beskriver körnings principerna för PowerShell och förklarar hur du hanterar dem.</span><span class="sxs-lookup"><span data-stu-id="73ae0-106">Describes the PowerShell execution policies and explains how to manage them.</span></span>

## <a name="long-description"></a><span data-ttu-id="73ae0-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="73ae0-107">Long Description</span></span>

<span data-ttu-id="73ae0-108">PowerShell: s körnings princip är en säkerhetsfunktion som styr de villkor under vilka PowerShell läser in konfigurationsfiler och kör skript.</span><span class="sxs-lookup"><span data-stu-id="73ae0-108">PowerShell's execution policy is a safety feature that controls the conditions under which PowerShell loads configuration files and runs scripts.</span></span> <span data-ttu-id="73ae0-109">Den här funktionen hjälper till att förhindra körning av skadliga skript.</span><span class="sxs-lookup"><span data-stu-id="73ae0-109">This feature helps prevent the execution of malicious scripts.</span></span>

<span data-ttu-id="73ae0-110">På en Windows-dator kan du ange en körnings princip för den lokala datorn, för den aktuella användaren eller för en viss session.</span><span class="sxs-lookup"><span data-stu-id="73ae0-110">On a Windows computer you can set an execution policy for the local computer, for the current user, or for a particular session.</span></span> <span data-ttu-id="73ae0-111">Du kan också använda en grupprincip inställning för att ange körnings principer för datorer och användare.</span><span class="sxs-lookup"><span data-stu-id="73ae0-111">You can also use a Group Policy setting to set execution policies for computers and users.</span></span>

<span data-ttu-id="73ae0-112">Körnings principer för den lokala datorn och den aktuella användaren lagras i registret.</span><span class="sxs-lookup"><span data-stu-id="73ae0-112">Execution policies for the local computer and current user are stored in the registry.</span></span> <span data-ttu-id="73ae0-113">Du behöver inte ange körnings principer i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="73ae0-113">You don't need to set execution policies in your PowerShell profile.</span></span>
<span data-ttu-id="73ae0-114">Körnings principen för en viss session lagras endast i minnet och går förlorad när sessionen stängs.</span><span class="sxs-lookup"><span data-stu-id="73ae0-114">The execution policy for a particular session is stored only in memory and is lost when the session is closed.</span></span>

<span data-ttu-id="73ae0-115">Körnings principen är inte ett säkerhets system som begränsar användar åtgärder.</span><span class="sxs-lookup"><span data-stu-id="73ae0-115">The execution policy isn't a security system that restricts user actions.</span></span> <span data-ttu-id="73ae0-116">Användare kan till exempel enkelt kringgå en princip genom att skriva skript innehållet på kommando raden när de inte kan köra ett skript.</span><span class="sxs-lookup"><span data-stu-id="73ae0-116">For example, users can easily bypass a policy by typing the script contents at the command line when they cannot run a script.</span></span> <span data-ttu-id="73ae0-117">I stället hjälper körnings principen användarna att ange grundläggande regler och förhindrar att de bryter mot dem.</span><span class="sxs-lookup"><span data-stu-id="73ae0-117">Instead, the execution policy helps users to set basic rules and prevents them from violating them unintentionally.</span></span>

<span data-ttu-id="73ae0-118">På datorer som inte är Windows-datorer är standard körnings principen **obegränsad** och kan inte ändras.</span><span class="sxs-lookup"><span data-stu-id="73ae0-118">On non-Windows computers, the default execution policy is **Unrestricted** and cannot be changed.</span></span> <span data-ttu-id="73ae0-119">`Set-ExecutionPolicy`Cmdleten är tillgänglig, men PowerShell visar ett konsol meddelande som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="73ae0-119">The `Set-ExecutionPolicy` cmdlet is available, but PowerShell displays a console message that it's not supported.</span></span> <span data-ttu-id="73ae0-120">Medan `Get-ExecutionPolicy` returnerar **obegränsade** på plattformar som inte är Windows-plattformar, matchar **Bypass** beteendet i själva verket eftersom dessa plattformar inte implementerar Windows-säkerhetszoner.</span><span class="sxs-lookup"><span data-stu-id="73ae0-120">While `Get-ExecutionPolicy` returns **Unrestricted** on non-Windows platforms, the behavior really matches **Bypass** because those platforms do not implement the Windows Security Zones.</span></span>

## <a name="powershell-execution-policies"></a><span data-ttu-id="73ae0-121">Körnings principer för PowerShell</span><span class="sxs-lookup"><span data-stu-id="73ae0-121">PowerShell execution policies</span></span>

<span data-ttu-id="73ae0-122">Tvång av dessa principer sker endast på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="73ae0-122">Enforcement of these policies only occurs on Windows platforms.</span></span> <span data-ttu-id="73ae0-123">PowerShell-körnings principerna är följande:</span><span class="sxs-lookup"><span data-stu-id="73ae0-123">The PowerShell execution policies are as follows:</span></span>

### <a name="allsigned"></a><span data-ttu-id="73ae0-124">AllSigned</span><span class="sxs-lookup"><span data-stu-id="73ae0-124">AllSigned</span></span>

- <span data-ttu-id="73ae0-125">Skript kan köras.</span><span class="sxs-lookup"><span data-stu-id="73ae0-125">Scripts can run.</span></span>
- <span data-ttu-id="73ae0-126">Kräver att alla skript och konfigurationsfiler signeras av en betrodd utgivare, inklusive skript som du skriver på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="73ae0-126">Requires that all scripts and configuration files be signed by a trusted publisher, including scripts that you write on the local computer.</span></span>
- <span data-ttu-id="73ae0-127">Du får frågan innan du kör skript från utgivare som du ännu inte har klassificerat som betrott eller ej betrott.</span><span class="sxs-lookup"><span data-stu-id="73ae0-127">Prompts you before running scripts from publishers that you haven't yet classified as trusted or untrusted.</span></span>
- <span data-ttu-id="73ae0-128">Risker som kör signerade, men skadliga, skript.</span><span class="sxs-lookup"><span data-stu-id="73ae0-128">Risks running signed, but malicious, scripts.</span></span>

### <a name="bypass"></a><span data-ttu-id="73ae0-129">Förbikoppling</span><span class="sxs-lookup"><span data-stu-id="73ae0-129">Bypass</span></span>

- <span data-ttu-id="73ae0-130">Inget blockeras och det finns inga varningar eller prompter.</span><span class="sxs-lookup"><span data-stu-id="73ae0-130">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="73ae0-131">Den här körnings principen är utformad för konfigurationer där ett PowerShell-skript är inbyggt i ett större program eller för konfigurationer där PowerShell är grunden för ett program som har en egen säkerhets modell.</span><span class="sxs-lookup"><span data-stu-id="73ae0-131">This execution policy is designed for configurations in which a PowerShell script is built in to a larger application or for configurations in which PowerShell is the foundation for a program that has its own security model.</span></span>

### <a name="default"></a><span data-ttu-id="73ae0-132">Default</span><span class="sxs-lookup"><span data-stu-id="73ae0-132">Default</span></span>

- <span data-ttu-id="73ae0-133">Anger standard körnings principen.</span><span class="sxs-lookup"><span data-stu-id="73ae0-133">Sets the default execution policy.</span></span>
- <span data-ttu-id="73ae0-134">**Begränsat** för Windows-klienter.</span><span class="sxs-lookup"><span data-stu-id="73ae0-134">**Restricted** for Windows clients.</span></span>
- <span data-ttu-id="73ae0-135">**RemoteSigned** för Windows-servrar.</span><span class="sxs-lookup"><span data-stu-id="73ae0-135">**RemoteSigned** for Windows servers.</span></span>

### <a name="remotesigned"></a><span data-ttu-id="73ae0-136">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="73ae0-136">RemoteSigned</span></span>

- <span data-ttu-id="73ae0-137">Standard körnings principen för Windows Server-datorer.</span><span class="sxs-lookup"><span data-stu-id="73ae0-137">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="73ae0-138">Skript kan köras.</span><span class="sxs-lookup"><span data-stu-id="73ae0-138">Scripts can run.</span></span>
- <span data-ttu-id="73ae0-139">Kräver en digital signatur från en betrodd utgivare på skript och konfigurationsfiler som hämtas från Internet, som inkluderar e-post och snabb meddelande program.</span><span class="sxs-lookup"><span data-stu-id="73ae0-139">Requires a digital signature from a trusted publisher on scripts and configuration files that are downloaded from the internet which includes email and instant messaging programs.</span></span>
- <span data-ttu-id="73ae0-140">Kräver inte digitala signaturer i skript som är skrivna på den lokala datorn och som inte har hämtats från Internet.</span><span class="sxs-lookup"><span data-stu-id="73ae0-140">Doesn't require digital signatures on scripts that are written on the local computer and not downloaded from the internet.</span></span>
- <span data-ttu-id="73ae0-141">Kör skript som hämtas från Internet och inte signerade, om skripten är avblockerade, till exempel genom att använda `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="73ae0-141">Runs scripts that are downloaded from the internet and not signed, if the scripts are unblocked, such as by using the `Unblock-File` cmdlet.</span></span>
- <span data-ttu-id="73ae0-142">Risker som kör osignerade skript från andra källor än Internet och signerade skript som kan vara skadliga.</span><span class="sxs-lookup"><span data-stu-id="73ae0-142">Risks running unsigned scripts from sources other than the internet and signed scripts that could be malicious.</span></span>

### <a name="restricted"></a><span data-ttu-id="73ae0-143">Begränsade</span><span class="sxs-lookup"><span data-stu-id="73ae0-143">Restricted</span></span>

- <span data-ttu-id="73ae0-144">Standard körnings principen för Windows-klientdatorer.</span><span class="sxs-lookup"><span data-stu-id="73ae0-144">The default execution policy for Windows client computers.</span></span>
- <span data-ttu-id="73ae0-145">Tillåter enskilda kommandon, men tillåter inte skript.</span><span class="sxs-lookup"><span data-stu-id="73ae0-145">Permits individual commands, but does not allow scripts.</span></span>
- <span data-ttu-id="73ae0-146">Förhindrar körning av alla skriptfiler, inklusive formatering och konfigurationsfiler ( `.ps1xml` ), modulens skript fil ( `.psm1` ) och PowerShell-profiler ( `.ps1` ).</span><span class="sxs-lookup"><span data-stu-id="73ae0-146">Prevents running of all script files, including formatting and configuration files (`.ps1xml`), module script files (`.psm1`), and PowerShell profiles (`.ps1`).</span></span>

### <a name="undefined"></a><span data-ttu-id="73ae0-147">Undefined (Odefinierad)</span><span class="sxs-lookup"><span data-stu-id="73ae0-147">Undefined</span></span>

- <span data-ttu-id="73ae0-148">Ingen körnings princip har angetts i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="73ae0-148">There is no execution policy set in the current scope.</span></span>
- <span data-ttu-id="73ae0-149">Om körnings principen i alla omfattningar är **Odefinierad** , **begränsas** den effektiva körnings principen för Windows-klienter och **RemoteSigned** för Windows Server.</span><span class="sxs-lookup"><span data-stu-id="73ae0-149">If the execution policy in all scopes is **Undefined** , the effective execution policy is **Restricted** for Windows clients and **RemoteSigned** for Windows Server.</span></span>

### <a name="unrestricted"></a><span data-ttu-id="73ae0-150">Obegränsat</span><span class="sxs-lookup"><span data-stu-id="73ae0-150">Unrestricted</span></span>

- <span data-ttu-id="73ae0-151">Standard körnings principen för datorer som inte är Windows-datorer och inte kan ändras.</span><span class="sxs-lookup"><span data-stu-id="73ae0-151">The default execution policy for non-Windows computers and cannot be changed.</span></span>
- <span data-ttu-id="73ae0-152">Osignerade skript kan köras.</span><span class="sxs-lookup"><span data-stu-id="73ae0-152">Unsigned scripts can run.</span></span> <span data-ttu-id="73ae0-153">Det finns en risk för att skadliga skript körs.</span><span class="sxs-lookup"><span data-stu-id="73ae0-153">There is a risk of running malicious scripts.</span></span>
- <span data-ttu-id="73ae0-154">Varnar användaren innan skript och konfigurationsfiler som inte kommer från zonen Lokalt intranät körs.</span><span class="sxs-lookup"><span data-stu-id="73ae0-154">Warns the user before running scripts and configuration files that are not from the local intranet zone.</span></span>

> [!NOTE]
> <span data-ttu-id="73ae0-155">På system som inte skiljer Universal Naming Convention (UNC) sökvägar från Internet vägar kan skript som identifieras av en UNC-sökväg inte tillåtas att köras med **RemoteSigned** körnings princip.</span><span class="sxs-lookup"><span data-stu-id="73ae0-155">On systems that do not distinguish Universal Naming Convention (UNC) paths from internet paths, scripts that are identified by a UNC path might not be permitted to run with the **RemoteSigned** execution policy.</span></span>

## <a name="execution-policy-scope"></a><span data-ttu-id="73ae0-156">Omfattning för körnings princip</span><span class="sxs-lookup"><span data-stu-id="73ae0-156">Execution policy scope</span></span>

<span data-ttu-id="73ae0-157">Du kan ange en princip för körning som bara är effektiv i ett visst omfång.</span><span class="sxs-lookup"><span data-stu-id="73ae0-157">You can set an execution policy that is effective only in a particular scope.</span></span>

<span data-ttu-id="73ae0-158">Giltiga värden för **scope** är **MachinePolicy** , **UserPolicy** , **process** , **CurrentUser** och **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="73ae0-158">The valid values for **Scope** are **MachinePolicy** , **UserPolicy** , **Process** , **CurrentUser** , and **LocalMachine**.</span></span> <span data-ttu-id="73ae0-159">**LocalMachine** är standard när du anger en körnings princip.</span><span class="sxs-lookup"><span data-stu-id="73ae0-159">**LocalMachine** is the default when setting an execution policy.</span></span>

<span data-ttu-id="73ae0-160">**Omfångs** värden visas i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="73ae0-160">The **Scope** values are listed in precedence order.</span></span> <span data-ttu-id="73ae0-161">Den princip som har företräde är gällande i den aktuella sessionen, även om en mer restriktiv princip har ställts in på en lägre prioritets nivå.</span><span class="sxs-lookup"><span data-stu-id="73ae0-161">The policy that takes precedence is effective in the current session, even if a more restrictive policy was set at a lower level of precedence.</span></span>

<span data-ttu-id="73ae0-162">Mer information finns i [set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy).</span><span class="sxs-lookup"><span data-stu-id="73ae0-162">For more information, see [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy).</span></span>

### <a name="machinepolicy"></a><span data-ttu-id="73ae0-163">MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="73ae0-163">MachinePolicy</span></span>

<span data-ttu-id="73ae0-164">Anges av en grupprincip för alla användare av datorn.</span><span class="sxs-lookup"><span data-stu-id="73ae0-164">Set by a Group Policy for all users of the computer.</span></span>

### <a name="userpolicy"></a><span data-ttu-id="73ae0-165">UserPolicy</span><span class="sxs-lookup"><span data-stu-id="73ae0-165">UserPolicy</span></span>

<span data-ttu-id="73ae0-166">Anges av en grupprincip för datorns aktuella användare.</span><span class="sxs-lookup"><span data-stu-id="73ae0-166">Set by a Group Policy for the current user of the computer.</span></span>

### <a name="process"></a><span data-ttu-id="73ae0-167">Process</span><span class="sxs-lookup"><span data-stu-id="73ae0-167">Process</span></span>

<span data-ttu-id="73ae0-168">**Process** omfånget påverkar endast den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="73ae0-168">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="73ae0-169">Körnings principen sparas i miljövariabeln i `$env:PSExecutionPolicyPreference` stället för registret.</span><span class="sxs-lookup"><span data-stu-id="73ae0-169">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="73ae0-170">När PowerShell-sessionen stängs raderas variabeln och värdet.</span><span class="sxs-lookup"><span data-stu-id="73ae0-170">When the PowerShell session is closed, the variable and value are deleted.</span></span>

### <a name="currentuser"></a><span data-ttu-id="73ae0-171">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="73ae0-171">CurrentUser</span></span>

<span data-ttu-id="73ae0-172">Körnings principen påverkar endast den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="73ae0-172">The execution policy affects only the current user.</span></span> <span data-ttu-id="73ae0-173">Den lagras i **HKEY_CURRENT_USER** register under nyckel.</span><span class="sxs-lookup"><span data-stu-id="73ae0-173">It's stored in the **HKEY_CURRENT_USER** registry subkey.</span></span>

### <a name="localmachine"></a><span data-ttu-id="73ae0-174">LocalMachine</span><span class="sxs-lookup"><span data-stu-id="73ae0-174">LocalMachine</span></span>

<span data-ttu-id="73ae0-175">Körnings principen påverkar alla användare på den aktuella datorn.</span><span class="sxs-lookup"><span data-stu-id="73ae0-175">The execution policy affects all users on the current computer.</span></span> <span data-ttu-id="73ae0-176">Den lagras i **HKEY_LOCAL_MACHINE** register under nyckel.</span><span class="sxs-lookup"><span data-stu-id="73ae0-176">It's stored in the **HKEY_LOCAL_MACHINE** registry subkey.</span></span>

## <a name="managing-the-execution-policy-with-powershell"></a><span data-ttu-id="73ae0-177">Hantera körnings principen med PowerShell</span><span class="sxs-lookup"><span data-stu-id="73ae0-177">Managing the execution policy with PowerShell</span></span>

<span data-ttu-id="73ae0-178">Använd cmdleten för att få en effektiv körnings princip för den aktuella PowerShell-sessionen `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="73ae0-178">To get the effective execution policy for the current PowerShell session, use the `Get-ExecutionPolicy` cmdlet.</span></span>

<span data-ttu-id="73ae0-179">Följande kommando hämtar den effektiva körnings principen:</span><span class="sxs-lookup"><span data-stu-id="73ae0-179">The following command gets the effective execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="73ae0-180">Så här hämtar du alla körnings principer som påverkar den aktuella sessionen och visar dem i prioritetsordning:</span><span class="sxs-lookup"><span data-stu-id="73ae0-180">To get all of the execution policies that affect the current session and display them in precedence order:</span></span>

```powershell
Get-ExecutionPolicy -List
```

<span data-ttu-id="73ae0-181">Resultatet liknar följande exempel på utdata:</span><span class="sxs-lookup"><span data-stu-id="73ae0-181">The result looks similar to the following sample output:</span></span>

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       AllSigned
```

<span data-ttu-id="73ae0-182">I det här fallet är den effektiva körnings principen **RemoteSigned** eftersom körnings principen för den aktuella användaren prioriteras över körnings principen som angetts för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="73ae0-182">In this case, the effective execution policy is **RemoteSigned** because the execution policy for the current user takes precedence over the execution policy set for the local computer.</span></span>

<span data-ttu-id="73ae0-183">Om du vill hämta körnings principen för ett visst omfång använder du **omfattnings** parametern för `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="73ae0-183">To get the execution policy set for a particular scope, use the **Scope** parameter of `Get-ExecutionPolicy`.</span></span>

<span data-ttu-id="73ae0-184">Följande kommando hämtar till exempel körnings principen för **CurrentUser** -omfånget:</span><span class="sxs-lookup"><span data-stu-id="73ae0-184">For example, the following command gets the execution policy for the **CurrentUser** scope:</span></span>

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

### <a name="change-the-execution-policy"></a><span data-ttu-id="73ae0-185">Ändra körnings principen</span><span class="sxs-lookup"><span data-stu-id="73ae0-185">Change the execution policy</span></span>

<span data-ttu-id="73ae0-186">Använd cmdleten om du vill ändra körnings principen för PowerShell på Windows-datorn `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="73ae0-186">To change the PowerShell execution policy on your Windows computer, use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="73ae0-187">Ändringen träder i kraft omedelbart.</span><span class="sxs-lookup"><span data-stu-id="73ae0-187">The change is effective immediately.</span></span> <span data-ttu-id="73ae0-188">Du behöver inte starta om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73ae0-188">You don't need to restart PowerShell.</span></span>

<span data-ttu-id="73ae0-189">Om du anger körnings principen för omfattningarna **LocalMachine** eller **CurrentUser** sparas ändringen i registret och fortsätter att gälla tills du ändrar den igen.</span><span class="sxs-lookup"><span data-stu-id="73ae0-189">If you set the execution policy for the scopes **LocalMachine** or the **CurrentUser** , the change is saved in the registry and remains effective until you change it again.</span></span>

<span data-ttu-id="73ae0-190">Om du anger körnings principen för **process** omfånget sparas den inte i registret.</span><span class="sxs-lookup"><span data-stu-id="73ae0-190">If you set the execution policy for the **Process** scope, it's not saved in the registry.</span></span> <span data-ttu-id="73ae0-191">Körnings principen behålls tills den aktuella processen och eventuella underordnade processer stängs.</span><span class="sxs-lookup"><span data-stu-id="73ae0-191">The execution policy is retained until the current process and any child processes are closed.</span></span>

> [!NOTE]
> <span data-ttu-id="73ae0-192">I Windows Vista och senare versioner av Windows kan du köra kommandon som ändrar körnings principen för den lokala datorn, **LocalMachine** scope, starta PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="73ae0-192">In Windows Vista and later versions of Windows, to run commands that change the execution policy for the local computer, **LocalMachine** scope, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="73ae0-193">Ändra körnings princip:</span><span class="sxs-lookup"><span data-stu-id="73ae0-193">To change your execution policy:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName>
```

<span data-ttu-id="73ae0-194">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="73ae0-194">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="73ae0-195">Ange körnings principen i ett visst omfång:</span><span class="sxs-lookup"><span data-stu-id="73ae0-195">To set the execution policy in a particular scope:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName> -Scope <scope>
```

<span data-ttu-id="73ae0-196">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="73ae0-196">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

<span data-ttu-id="73ae0-197">Ett kommando för att ändra en körnings princip kan lyckas men ändå inte ändra den effektiva körnings principen.</span><span class="sxs-lookup"><span data-stu-id="73ae0-197">A command to change an execution policy can succeed but still not change the effective execution policy.</span></span>

<span data-ttu-id="73ae0-198">Till exempel kan ett kommando som anger körnings principen för den lokala datorn lyckas, men åsidosätts av körnings principen för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="73ae0-198">For example, a command that sets the execution policy for the local computer can succeed but be overridden by the execution policy for the current user.</span></span>

### <a name="remove-the-execution-policy"></a><span data-ttu-id="73ae0-199">Ta bort körnings principen</span><span class="sxs-lookup"><span data-stu-id="73ae0-199">Remove the execution policy</span></span>

<span data-ttu-id="73ae0-200">Om du vill ta bort körnings principen för ett visst omfång anger du att körnings principen ska vara **Odefinierad**.</span><span class="sxs-lookup"><span data-stu-id="73ae0-200">To remove the execution policy for a particular scope, set the execution policy to **Undefined**.</span></span>

<span data-ttu-id="73ae0-201">Till exempel för att ta bort körnings principen för alla användare av den lokala datorn:</span><span class="sxs-lookup"><span data-stu-id="73ae0-201">For example, to remove the execution policy for all the users of the local computer:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope LocalMachine
```

<span data-ttu-id="73ae0-202">Ta bort körnings principen för ett **omfång** :</span><span class="sxs-lookup"><span data-stu-id="73ae0-202">To remove the execution policy for a **Scope** :</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

<span data-ttu-id="73ae0-203">Om ingen körnings princip anges i någon omfattning är den effektiva körnings principen **begränsad** , vilket är standardinställningen för Windows-klienter.</span><span class="sxs-lookup"><span data-stu-id="73ae0-203">If no execution policy is set in any scope, the effective execution policy is **Restricted** , which is the default for Windows clients.</span></span>

### <a name="set-a-different-policy-for-one-session"></a><span data-ttu-id="73ae0-204">Ange en annan princip för en session</span><span class="sxs-lookup"><span data-stu-id="73ae0-204">Set a different policy for one session</span></span>

<span data-ttu-id="73ae0-205">Du kan använda parametern **ExecutionPolicy** för **pwsh.exe** om du vill ange en körnings princip för en ny PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="73ae0-205">You can use the **ExecutionPolicy** parameter of **pwsh.exe** to set an execution policy for a new PowerShell session.</span></span> <span data-ttu-id="73ae0-206">Principen påverkar endast den aktuella sessionen och de underordnade sessionerna.</span><span class="sxs-lookup"><span data-stu-id="73ae0-206">The policy affects only the current session and child sessions.</span></span>

<span data-ttu-id="73ae0-207">Ange körnings principen för en ny session genom att starta PowerShell på kommando raden, till exempel **cmd.exe** eller från PowerShell, och sedan använda parametern **ExecutionPolicy** för **pwsh.exe** för att ange körnings principen.</span><span class="sxs-lookup"><span data-stu-id="73ae0-207">To set the execution policy for a new session, start PowerShell at the command line, such as **cmd.exe** or from PowerShell, and then use the **ExecutionPolicy** parameter of **pwsh.exe** to set the execution policy.</span></span>

<span data-ttu-id="73ae0-208">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="73ae0-208">For example:</span></span>

```powershell
pwsh.exe -ExecutionPolicy AllSigned
```

<span data-ttu-id="73ae0-209">Den körnings princip som du anger lagras inte i registret.</span><span class="sxs-lookup"><span data-stu-id="73ae0-209">The execution policy that you set isn't stored in the registry.</span></span> <span data-ttu-id="73ae0-210">I stället lagras den i `$env:PSExecutionPolicyPreference` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="73ae0-210">Instead, it's stored in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="73ae0-211">Variabeln tas bort när du stänger sessionen där principen har angetts.</span><span class="sxs-lookup"><span data-stu-id="73ae0-211">The variable is deleted when you close the session in which the policy is set.</span></span> <span data-ttu-id="73ae0-212">Du kan inte ändra principen genom att redigera variabelvärdet.</span><span class="sxs-lookup"><span data-stu-id="73ae0-212">You cannot change the policy by editing the variable value.</span></span>

<span data-ttu-id="73ae0-213">Under sessionen har körnings principen som ställts in för sessionen företräde framför en körnings princip som anges i registret för den lokala datorn eller den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="73ae0-213">During the session, the execution policy that is set for the session takes precedence over an execution policy that is set in the registry for the local computer or current user.</span></span> <span data-ttu-id="73ae0-214">Den har dock inte företräde framför körnings principen som angetts med hjälp av en grupprincip.</span><span class="sxs-lookup"><span data-stu-id="73ae0-214">However, it doesn't take precedence over the execution policy set by using a Group Policy.</span></span>

## <a name="use-group-policy-to-manage-execution-policy"></a><span data-ttu-id="73ae0-215">Använd grupprincip för att hantera körnings principen</span><span class="sxs-lookup"><span data-stu-id="73ae0-215">Use Group Policy to Manage Execution Policy</span></span>

<span data-ttu-id="73ae0-216">Du kan använda inställningen **Aktivera** körning av skript grupprincip för att hantera körnings principen för datorer i företaget.</span><span class="sxs-lookup"><span data-stu-id="73ae0-216">You can use the **Turn on Script Execution** Group Policy setting to manage the execution policy of computers in your enterprise.</span></span> <span data-ttu-id="73ae0-217">Inställningen grupprincip åsidosätter körnings principerna som angetts i PowerShell i alla omfång.</span><span class="sxs-lookup"><span data-stu-id="73ae0-217">The Group Policy setting overrides the execution policies set in PowerShell in all scopes.</span></span>

<span data-ttu-id="73ae0-218">Inställningarna för att **Aktivera skript körnings** principer är följande:</span><span class="sxs-lookup"><span data-stu-id="73ae0-218">The **Turn on Script Execution** policy settings are as follows:</span></span>

- <span data-ttu-id="73ae0-219">Om du inaktiverar **Aktivera skript körning** körs inte skripten.</span><span class="sxs-lookup"><span data-stu-id="73ae0-219">If you disable **Turn on Script Execution** , scripts do not run.</span></span> <span data-ttu-id="73ae0-220">Detta motsvarar principen för **begränsade** körningar.</span><span class="sxs-lookup"><span data-stu-id="73ae0-220">This is equivalent to the **Restricted** execution policy.</span></span>
- <span data-ttu-id="73ae0-221">Om du aktiverar **Aktivera skript körning** kan du välja en körnings princip.</span><span class="sxs-lookup"><span data-stu-id="73ae0-221">If you enable **Turn on Script Execution** , you can select an execution policy.</span></span> <span data-ttu-id="73ae0-222">Grupprincip inställningarna motsvarar följande princip inställningar för körning:</span><span class="sxs-lookup"><span data-stu-id="73ae0-222">The Group Policy settings are equivalent to the following execution policy settings:</span></span>

  | <span data-ttu-id="73ae0-223">Grupprincip</span><span class="sxs-lookup"><span data-stu-id="73ae0-223">Group Policy</span></span>                                  | <span data-ttu-id="73ae0-224">Körnings princip</span><span class="sxs-lookup"><span data-stu-id="73ae0-224">Execution Policy</span></span> |
  | --------------------------------------------- | ---------------- |
  | <span data-ttu-id="73ae0-225">Tillåt alla skript</span><span class="sxs-lookup"><span data-stu-id="73ae0-225">Allow all scripts</span></span>                             | <span data-ttu-id="73ae0-226">Obegränsat</span><span class="sxs-lookup"><span data-stu-id="73ae0-226">Unrestricted</span></span>     |
  | <span data-ttu-id="73ae0-227">Tillåt lokala skript och fjärrsignerade skript</span><span class="sxs-lookup"><span data-stu-id="73ae0-227">Allow local scripts and remote signed scripts</span></span> | <span data-ttu-id="73ae0-228">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="73ae0-228">RemoteSigned</span></span>     |
  | <span data-ttu-id="73ae0-229">Tillåt endast signerade skript</span><span class="sxs-lookup"><span data-stu-id="73ae0-229">Allow only signed scripts</span></span>                     | <span data-ttu-id="73ae0-230">AllSigned</span><span class="sxs-lookup"><span data-stu-id="73ae0-230">AllSigned</span></span>        |

- <span data-ttu-id="73ae0-231">Om **Aktivera skript körning** inte har kon figurer ATS har det ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="73ae0-231">If **Turn on Script Execution** is not configured, it has no effect.</span></span> <span data-ttu-id="73ae0-232">Körnings principen som angetts i PowerShell är effektiv.</span><span class="sxs-lookup"><span data-stu-id="73ae0-232">The execution policy set in PowerShell is effective.</span></span>

<span data-ttu-id="73ae0-233">Filerna PowerShellExecutionPolicy. adm och PowerShellExecutionPolicy. admx lägger till **Aktivera skript körnings** principen i noderna dator konfiguration och användar konfiguration i grupprincip redigeraren i följande sökvägar.</span><span class="sxs-lookup"><span data-stu-id="73ae0-233">The PowerShellExecutionPolicy.adm and PowerShellExecutionPolicy.admx files add the **Turn on Script Execution** policy to the Computer Configuration and User Configuration nodes in Group Policy Editor in the following paths.</span></span>

<span data-ttu-id="73ae0-234">För Windows XP och Windows Server 2003:</span><span class="sxs-lookup"><span data-stu-id="73ae0-234">For Windows XP and Windows Server 2003:</span></span>

<span data-ttu-id="73ae0-235">Administrativa Mallar\windows-komponenter\Windows-PowerShell</span><span class="sxs-lookup"><span data-stu-id="73ae0-235">Administrative Templates\Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="73ae0-236">För Windows Vista och senare versioner av Windows:</span><span class="sxs-lookup"><span data-stu-id="73ae0-236">For Windows Vista and later versions of Windows:</span></span>

<span data-ttu-id="73ae0-237">Administrativ Templates\Classic Administrativa mallar </span><span class="sxs-lookup"><span data-stu-id="73ae0-237">Administrative Templates\Classic Administrative Templates</span></span>\
<span data-ttu-id="73ae0-238">Windows Mallar\windows-komponenter\Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="73ae0-238">Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="73ae0-239">Principer som anges i noden dator konfiguration åsidosätter principer som angetts i noden användar konfiguration.</span><span class="sxs-lookup"><span data-stu-id="73ae0-239">Policies set in the Computer Configuration node take precedence over policies set in the User Configuration node.</span></span>

<span data-ttu-id="73ae0-240">Mer information finns i [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span><span class="sxs-lookup"><span data-stu-id="73ae0-240">For more information, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

### <a name="execution-policy-precedence"></a><span data-ttu-id="73ae0-241">Princip prioritet för körning</span><span class="sxs-lookup"><span data-stu-id="73ae0-241">Execution policy precedence</span></span>

<span data-ttu-id="73ae0-242">När du bestämmer den effektiva körnings principen för en session, utvärderar PowerShell körnings principerna i följande prioritetsordning:</span><span class="sxs-lookup"><span data-stu-id="73ae0-242">When determining the effective execution policy for a session, PowerShell evaluates the execution policies in the following precedence order:</span></span>

- <span data-ttu-id="73ae0-243">Grupprincip: MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="73ae0-243">Group Policy: MachinePolicy</span></span>
- <span data-ttu-id="73ae0-244">Grupprincip: UserPolicy</span><span class="sxs-lookup"><span data-stu-id="73ae0-244">Group Policy: UserPolicy</span></span>
- <span data-ttu-id="73ae0-245">Körnings princip: process (eller `pwsh.exe -ExecutionPolicy` )</span><span class="sxs-lookup"><span data-stu-id="73ae0-245">Execution Policy: Process (or `pwsh.exe -ExecutionPolicy`)</span></span>
- <span data-ttu-id="73ae0-246">Körnings princip: CurrentUser</span><span class="sxs-lookup"><span data-stu-id="73ae0-246">Execution Policy: CurrentUser</span></span>
- <span data-ttu-id="73ae0-247">Körnings princip: LocalMachine</span><span class="sxs-lookup"><span data-stu-id="73ae0-247">Execution Policy: LocalMachine</span></span>

## <a name="manage-signed-and-unsigned-scripts"></a><span data-ttu-id="73ae0-248">Hantera signerade och osignerade skript</span><span class="sxs-lookup"><span data-stu-id="73ae0-248">Manage signed and unsigned scripts</span></span>

<span data-ttu-id="73ae0-249">I Windows lägger program som Internet Explorer och Microsoft Edge till en alternativ data ström till filer som hämtas.</span><span class="sxs-lookup"><span data-stu-id="73ae0-249">In Windows, programs like Internet Explorer and Microsoft Edge add an alternate data stream to files that are downloaded.</span></span> <span data-ttu-id="73ae0-250">Detta markerar filen som "kommer från Internet".</span><span class="sxs-lookup"><span data-stu-id="73ae0-250">This marks the file as "coming from the Internet".</span></span> <span data-ttu-id="73ae0-251">Om din PowerShell-körnings princip är **RemoteSigned** kör PowerShell inte osignerade skript som hämtas från Internet, som innehåller e-post och snabb meddelande program.</span><span class="sxs-lookup"><span data-stu-id="73ae0-251">If your PowerShell execution policy is **RemoteSigned** , PowerShell won't run unsigned scripts that are downloaded from the internet which includes email and instant messaging programs.</span></span>

<span data-ttu-id="73ae0-252">Du kan signera skriptet eller välja att köra ett osignerat skript utan att ändra körnings principen.</span><span class="sxs-lookup"><span data-stu-id="73ae0-252">You can sign the script or elect to run an unsigned script without changing the execution policy.</span></span>

<span data-ttu-id="73ae0-253">Från och med PowerShell 3,0 kan du använda cmdleten **Stream** för `Get-Item` att identifiera filer som blockeras eftersom de har hämtats från Internet.</span><span class="sxs-lookup"><span data-stu-id="73ae0-253">Beginning in PowerShell 3.0, you can use the **Stream** parameter of the `Get-Item` cmdlet to detect files that are blocked because they were downloaded from the internet.</span></span> <span data-ttu-id="73ae0-254">Använd `Unblock-File` cmdleten för att avblockera skripten så att du kan köra dem i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73ae0-254">Use the `Unblock-File` cmdlet to unblock the scripts so that you can run them in PowerShell.</span></span>

<span data-ttu-id="73ae0-255">Mer information finns i [about_Signing](about_Signing.md), [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)och [unblock-File](xref:Microsoft.PowerShell.Utility.Unblock-File).</span><span class="sxs-lookup"><span data-stu-id="73ae0-255">For more information, see [about_Signing](about_Signing.md), [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item), and [Unblock-File](xref:Microsoft.PowerShell.Utility.Unblock-File).</span></span>

> [!NOTE]
> <span data-ttu-id="73ae0-256">Andra metoder för att hämta filer kanske inte markerar filerna som de kommer från zonen Internet.</span><span class="sxs-lookup"><span data-stu-id="73ae0-256">Other methods of downloading files may not mark the files as coming from the Internet Zone.</span></span> <span data-ttu-id="73ae0-257">Några exempel är:</span><span class="sxs-lookup"><span data-stu-id="73ae0-257">Some examples include:</span></span>
>
> - `curl.exe`
> - `Invoke-RestMethod`
> - `Invoke-WebRequest`

## <a name="execution-policy-on-windows-server-core-and-window-nano-server"></a><span data-ttu-id="73ae0-258">Körnings princip på Windows Server Core och Window Nano Server</span><span class="sxs-lookup"><span data-stu-id="73ae0-258">Execution policy on Windows Server Core and Window Nano Server</span></span>

<span data-ttu-id="73ae0-259">När PowerShell 6 körs på Windows Server Core eller Windows Nano Server under vissa förhållanden, kan körnings principer inte utföras med följande fel:</span><span class="sxs-lookup"><span data-stu-id="73ae0-259">When PowerShell 6 is run on Windows Server Core or Windows Nano Server under certain conditions, execution policies can fail with the following error:</span></span>

```Output
AuthorizationManager check failed.
At line:1 char:1
+ C:\scriptpath\scriptname.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<span data-ttu-id="73ae0-260">PowerShell använder API: er i Windows Skriv bords gränssnitt ( `explorer.exe` ) för att verifiera zonen i en skript fil.</span><span class="sxs-lookup"><span data-stu-id="73ae0-260">PowerShell uses APIs in the Windows Desktop Shell (`explorer.exe`) to validate the Zone of a script file.</span></span> <span data-ttu-id="73ae0-261">Windows-gränssnittet är inte tillgängligt på Windows Server Core och Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="73ae0-261">The Windows Shell is not available on Windows Server Core and Windows Nano Server.</span></span>

<span data-ttu-id="73ae0-262">Du kan också få det här felet på ett Windows-system om Windows Desktop Shell inte är tillgänglig eller inte svarar.</span><span class="sxs-lookup"><span data-stu-id="73ae0-262">You could also get this error on any Windows system if the Windows Desktop Shell is unavailable or unresponsive.</span></span> <span data-ttu-id="73ae0-263">Vid inloggning kan exempelvis ett PowerShell-inloggningsnamn starta körningen innan Windows-skrivbordet är klart, vilket resulterar i ett haveri.</span><span class="sxs-lookup"><span data-stu-id="73ae0-263">For example, during sign on, a PowerShell logon script could start execution before the Windows Desktop is ready, resulting in failure.</span></span>

<span data-ttu-id="73ae0-264">Om du använder en körnings princip för **bypass** eller **AllSigned** krävs ingen zon kontroll som undviker problemet.</span><span class="sxs-lookup"><span data-stu-id="73ae0-264">Using an execution policy of **ByPass** or **AllSigned** does not require a Zone check which avoids the problem.</span></span>

## <a name="see-also"></a><span data-ttu-id="73ae0-265">Se även</span><span class="sxs-lookup"><span data-stu-id="73ae0-265">See Also</span></span>

[<span data-ttu-id="73ae0-266">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="73ae0-266">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="73ae0-267">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="73ae0-267">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="73ae0-268">about_Signing</span><span class="sxs-lookup"><span data-stu-id="73ae0-268">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="73ae0-269">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="73ae0-269">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="73ae0-270">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="73ae0-270">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

[<span data-ttu-id="73ae0-271">Hjälp om Pwsh-konsolen</span><span class="sxs-lookup"><span data-stu-id="73ae0-271">Pwsh Console Help</span></span>](about_pwsh.md)

[<span data-ttu-id="73ae0-272">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="73ae0-272">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="73ae0-273">Avblockera – fil</span><span class="sxs-lookup"><span data-stu-id="73ae0-273">Unblock-File</span></span>](xref:Microsoft.PowerShell.Utility.Unblock-File)

