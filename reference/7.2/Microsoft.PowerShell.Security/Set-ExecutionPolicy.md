---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ExecutionPolicy
ms.openlocfilehash: 4c45267113ff7b8a870d5a05bf3e4ab922f7e9c6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709859"
---
# <span data-ttu-id="01dbb-102">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="01dbb-102">Set-ExecutionPolicy</span></span>

## <span data-ttu-id="01dbb-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="01dbb-103">SYNOPSIS</span></span>
<span data-ttu-id="01dbb-104">Anger PowerShell-körnings principer för Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="01dbb-104">Sets the PowerShell execution policies for Windows computers.</span></span>

## <span data-ttu-id="01dbb-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="01dbb-105">SYNTAX</span></span>

### <span data-ttu-id="01dbb-106">Alla</span><span class="sxs-lookup"><span data-stu-id="01dbb-106">All</span></span>

```
Set-ExecutionPolicy [-ExecutionPolicy] <ExecutionPolicy> [[-Scope] <ExecutionPolicyScope>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="01dbb-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="01dbb-107">DESCRIPTION</span></span>

<span data-ttu-id="01dbb-108">`Set-ExecutionPolicy`Cmdleten ändrar PowerShell-körnings principer för Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="01dbb-108">The `Set-ExecutionPolicy` cmdlet changes PowerShell execution policies for Windows computers.</span></span> <span data-ttu-id="01dbb-109">Mer information finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="01dbb-109">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="01dbb-110">Från och med PowerShell 6,0 för datorer som inte är Windows-datorer är standard körnings principen **obegränsad** och kan inte ändras.</span><span class="sxs-lookup"><span data-stu-id="01dbb-110">Beginning in PowerShell 6.0 for non-Windows computers, the default execution policy is **Unrestricted** and can't be changed.</span></span> <span data-ttu-id="01dbb-111">`Set-ExecutionPolicy`Cmdleten är tillgänglig, men PowerShell visar ett konsol meddelande som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="01dbb-111">The `Set-ExecutionPolicy` cmdlet is available, but PowerShell displays a console message that it's not supported.</span></span>

<span data-ttu-id="01dbb-112">En körnings princip är en del av säkerhets strategin för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01dbb-112">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="01dbb-113">Körnings principer avgör om du kan läsa in konfigurationsfiler, till exempel din PowerShell-profil eller köra skript.</span><span class="sxs-lookup"><span data-stu-id="01dbb-113">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="01dbb-114">Och om skripten måste signeras digitalt innan de körs.</span><span class="sxs-lookup"><span data-stu-id="01dbb-114">And, whether scripts must be digitally signed before they are run.</span></span>

<span data-ttu-id="01dbb-115">`Set-ExecutionPolicy`Cmdletens standard omfång är **LocalMachine**, som påverkar alla som använder datorn.</span><span class="sxs-lookup"><span data-stu-id="01dbb-115">The `Set-ExecutionPolicy` cmdlet's default scope is **LocalMachine**, which affects everyone who uses the computer.</span></span> <span data-ttu-id="01dbb-116">Om du vill ändra körnings principen för **LocalMachine** startar du PowerShell med **Kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-116">To change the execution policy for **LocalMachine**, start PowerShell with **Run as Administrator**.</span></span>

<span data-ttu-id="01dbb-117">Använd om du vill visa körnings principerna för varje omfång i prioritetsordning `Get-ExecutionPolicy -List` .</span><span class="sxs-lookup"><span data-stu-id="01dbb-117">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="01dbb-118">Om du vill se den effektiva körnings principen för PowerShell-sessionen använder du utan `Get-ExecutionPolicy` parametrar.</span><span class="sxs-lookup"><span data-stu-id="01dbb-118">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

## <span data-ttu-id="01dbb-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="01dbb-119">EXAMPLES</span></span>

### <span data-ttu-id="01dbb-120">Exempel 1: Ange en körnings princip</span><span class="sxs-lookup"><span data-stu-id="01dbb-120">Example 1: Set an execution policy</span></span>

<span data-ttu-id="01dbb-121">I det här exemplet visas hur du anger körnings principen för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="01dbb-121">This example shows how to set the execution policy for the local computer.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="01dbb-122">`Set-ExecutionPolicy`Cmdleten använder parametern **ExecutionPolicy** för att ange **RemoteSigned** -principen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-122">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="01dbb-123">Parametern **omfattning** Anger standardvärdet för omfattning, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-123">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span> <span data-ttu-id="01dbb-124">Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.</span><span class="sxs-lookup"><span data-stu-id="01dbb-124">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="01dbb-125">Exempel 2: Ange en princip för körning som står i konflikt med en grupprincip</span><span class="sxs-lookup"><span data-stu-id="01dbb-125">Example 2: Set an execution policy that conflicts with a Group Policy</span></span>

<span data-ttu-id="01dbb-126">Med det här kommandot försöker du ange **LocalMachine** -Omfattningens körnings princip till **begränsad**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-126">This command attempts to set the **LocalMachine** scope's execution policy to **Restricted**.</span></span>
<span data-ttu-id="01dbb-127">**LocalMachine** är mer restriktiv, men är inte den effektiva principen eftersom den står i konflikt med en Grupprincip.</span><span class="sxs-lookup"><span data-stu-id="01dbb-127">**LocalMachine** is more restrictive, but isn't the effective policy because it conflicts with a Group Policy.</span></span> <span data-ttu-id="01dbb-128">Den **begränsade** principen skrivs till registrerings data filen **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-128">The **Restricted** policy is written to the registry hive **HKEY_LOCAL_MACHINE**.</span></span>

```
PS> Set-ExecutionPolicy -ExecutionPolicy Restricted -Scope LocalMachine

Set-ExecutionPolicy : PowerShell updated your local preference successfully, but the setting is
overridden by the Group Policy applied to your system. Due to the override, your shell will retain
its current effective execution policy of "AllSigned". Contact your Group Policy administrator for
more information. At line:1 char:20 + Set-ExecutionPolicy <<<< restricted

PS> Get-ChildItem -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds

Name                    Property
----                    --------
Microsoft.PowerShell    Path            : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
                        ExecutionPolicy : Restricted
ScriptedDiagnostics     ExecutionPolicy : Unrestricted
```

<span data-ttu-id="01dbb-129">`Set-ExecutionPolicy`Cmdleten använder parametern **ExecutionPolicy** för att ange den **begränsade** principen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-129">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **Restricted** policy.</span></span> <span data-ttu-id="01dbb-130">Parametern **omfattning** Anger standardvärdet för omfattning, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-130">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span>
<span data-ttu-id="01dbb-131">`Get-ChildItem`Cmdleten använder parametern **Path** med **HKLM** -providern för att ange register plats.</span><span class="sxs-lookup"><span data-stu-id="01dbb-131">The `Get-ChildItem` cmdlet uses the **Path** parameter with the **HKLM** provider to specify registry location.</span></span>

### <span data-ttu-id="01dbb-132">Exempel 3: tillämpa körnings principen från en fjärrdator på en lokal dator</span><span class="sxs-lookup"><span data-stu-id="01dbb-132">Example 3: Apply the execution policy from a remote computer to a local computer</span></span>

<span data-ttu-id="01dbb-133">Det här kommandot hämtar objektet för körnings principen från en fjärrdator och anger principen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="01dbb-133">This command gets the execution policy object from a remote computer and sets the policy on the local computer.</span></span> <span data-ttu-id="01dbb-134">`Get-ExecutionPolicy` skickar ett **Microsoft.PowerShell.ExecutionPolicy** -objekt nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-134">`Get-ExecutionPolicy` sends a **Microsoft.PowerShell.ExecutionPolicy** object down the pipeline.</span></span> <span data-ttu-id="01dbb-135">`Set-ExecutionPolicy` accepterar pipeline-ininformation och kräver inte parametern **ExecutionPolicy** .</span><span class="sxs-lookup"><span data-stu-id="01dbb-135">`Set-ExecutionPolicy` accepts pipeline input and doesn't require the **ExecutionPolicy** parameter.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -ScriptBlock { Get-ExecutionPolicy } | Set-ExecutionPolicy
```

<span data-ttu-id="01dbb-136">`Invoke-Command`Cmdleten körs på den lokala datorn och skickar **script block** till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="01dbb-136">The `Invoke-Command` cmdlet is executed at the local computer and sends the **ScriptBlock** to the remote computer.</span></span> <span data-ttu-id="01dbb-137">Parametern **computername** anger fjärran sluten dator, **Server01**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-137">The **ComputerName** parameter specifies the remote computer, **Server01**.</span></span> <span data-ttu-id="01dbb-138">Parametern **script block** körs `Get-ExecutionPolicy` på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="01dbb-138">The **ScriptBlock** parameter runs `Get-ExecutionPolicy` on the remote computer.</span></span> <span data-ttu-id="01dbb-139">`Get-ExecutionPolicy`Objektet skickas ned pipelinen till `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="01dbb-139">The `Get-ExecutionPolicy` object is sent down the pipeline to the `Set-ExecutionPolicy`.</span></span>
<span data-ttu-id="01dbb-140">`Set-ExecutionPolicy` tillämpar körnings principen på den lokala datorns standard omfång, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-140">`Set-ExecutionPolicy` applies the execution policy to the local computer's default scope, **LocalMachine**.</span></span>

### <span data-ttu-id="01dbb-141">Exempel 4: ange omfånget för en körnings princip</span><span class="sxs-lookup"><span data-stu-id="01dbb-141">Example 4: Set the scope for an execution policy</span></span>

<span data-ttu-id="01dbb-142">I det här exemplet visas hur du anger en körnings princip för en angiven omfattning, **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-142">This example shows how to set an execution policy for a specified scope, **CurrentUser**.</span></span> <span data-ttu-id="01dbb-143">**CurrentUser** -omfånget påverkar endast den användare som anger det här omfånget.</span><span class="sxs-lookup"><span data-stu-id="01dbb-143">The **CurrentUser** scope only affects the user who sets this scope.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="01dbb-144">`Set-ExecutionPolicy` använder parametern **ExecutionPolicy** för att ange **AllSigned** -principen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-144">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span>
<span data-ttu-id="01dbb-145">Parametern **omfattning** anger **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-145">The **Scope** parameter specifies the **CurrentUser**.</span></span> <span data-ttu-id="01dbb-146">Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.</span><span class="sxs-lookup"><span data-stu-id="01dbb-146">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

<span data-ttu-id="01dbb-147">Den effektiva körnings principen för användaren blir **AllSigned**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-147">The effective execution policy for the user becomes **AllSigned**.</span></span>

### <span data-ttu-id="01dbb-148">Exempel 5: ta bort körnings principen för den aktuella användaren</span><span class="sxs-lookup"><span data-stu-id="01dbb-148">Example 5: Remove the execution policy for the current user</span></span>

<span data-ttu-id="01dbb-149">Det här exemplet visar hur använder den **odefinierade** körnings principen för att ta bort en körnings princip för en angiven omfattning.</span><span class="sxs-lookup"><span data-stu-id="01dbb-149">This example shows how use the **Undefined** execution policy to remove an execution policy for a specified scope.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned
```

<span data-ttu-id="01dbb-150">`Set-ExecutionPolicy` använder parametern **ExecutionPolicy** för att ange den **odefinierade** principen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-150">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **Undefined** policy.</span></span>
<span data-ttu-id="01dbb-151">Parametern **omfattning** anger **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-151">The **Scope** parameter specifies the **CurrentUser**.</span></span> <span data-ttu-id="01dbb-152">Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.</span><span class="sxs-lookup"><span data-stu-id="01dbb-152">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="01dbb-153">Exempel 6: Ange körnings principen för den aktuella PowerShell-sessionen</span><span class="sxs-lookup"><span data-stu-id="01dbb-153">Example 6: Set the execution policy for the current PowerShell session</span></span>

<span data-ttu-id="01dbb-154">**Process** omfånget påverkar endast den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-154">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="01dbb-155">Körnings principen sparas i miljö variabeln `$env:PSExecutionPolicyPreference` och tas bort när sessionen stängs.</span><span class="sxs-lookup"><span data-stu-id="01dbb-155">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference` and is deleted when the session is closed.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope Process
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       AllSigned
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="01dbb-156">`Set-ExecutionPolicy`Använder parametern **ExecutionPolicy** för att ange **AllSigned** -principen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-156">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span> <span data-ttu-id="01dbb-157">Parametern **omfattning** anger värde **processen**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-157">The **Scope** parameter specifies the value **Process**.</span></span> <span data-ttu-id="01dbb-158">Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.</span><span class="sxs-lookup"><span data-stu-id="01dbb-158">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="01dbb-159">Exempel 7: avblockera ett skript för att köra det utan att ändra körnings principen</span><span class="sxs-lookup"><span data-stu-id="01dbb-159">Example 7: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="01dbb-160">Det här exemplet visar hur **RemoteSigned** -körnings principen förhindrar att osignerade skript körs.</span><span class="sxs-lookup"><span data-stu-id="01dbb-160">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="01dbb-161">Vi rekommenderar att du läser skript koden och kontrollerar att den är säker **innan** du använder `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="01dbb-161">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="01dbb-162">`Unblock-File`Cmdleten avblockerar skripten så att de kan köras, men ändrar inte körnings principen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-162">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

```
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

.\Start-ActivityTracker.ps1 : File .\Start-ActivityTracker.ps1 cannot be loaded.
The file .\Start-ActivityTracker.ps1 is not digitally signed.
The script will not execute on the system.
For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess

PS> Unblock-File -Path .\Start-ActivityTracker.ps1

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

Task 1:
```

<span data-ttu-id="01dbb-163">`Set-ExecutionPolicy`Använder parametern **ExecutionPolicy** för att ange **RemoteSigned** -principen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-163">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="01dbb-164">Principen har angetts för standard omfånget, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-164">The policy is set for the default scope, **LocalMachine**.</span></span>

<span data-ttu-id="01dbb-165">`Get-ExecutionPolicy`Cmdleten visar att **RemoteSigned** är den effektiva körnings principen för den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-165">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="01dbb-166">**Start-ActivityTracker.ps1** skriptet körs från den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-166">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="01dbb-167">Skriptet blockeras av **RemoteSigned** eftersom skriptet inte har signerats digitalt.</span><span class="sxs-lookup"><span data-stu-id="01dbb-167">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="01dbb-168">I det här exemplet har skript koden granskats och verifierats som säker för körning.</span><span class="sxs-lookup"><span data-stu-id="01dbb-168">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="01dbb-169">`Unblock-File`Cmdleten använder parametern **Path** för att avblockera skriptet.</span><span class="sxs-lookup"><span data-stu-id="01dbb-169">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="01dbb-170">För att kontrol lera att `Unblock-File` inte har ändrat körnings principen, `Get-ExecutionPolicy` visar den effektiva körnings principen, **RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-170">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned**.</span></span>

<span data-ttu-id="01dbb-171">Skriptet **Start-ActivityTracker.ps1** köras från den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-171">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="01dbb-172">Skriptet börjar köras eftersom det har avblockerats av `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="01dbb-172">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="01dbb-173">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="01dbb-173">PARAMETERS</span></span>

### <span data-ttu-id="01dbb-174">-Confirm</span><span class="sxs-lookup"><span data-stu-id="01dbb-174">-Confirm</span></span>

<span data-ttu-id="01dbb-175">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="01dbb-175">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01dbb-176">– ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="01dbb-176">-ExecutionPolicy</span></span>

<span data-ttu-id="01dbb-177">Anger körnings principen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-177">Specifies the execution policy.</span></span> <span data-ttu-id="01dbb-178">Om det inte finns några grup principer och varje omfattnings körnings princip är inställd på **Odefinierad**, blir det **begränsade** principen för alla användare.</span><span class="sxs-lookup"><span data-stu-id="01dbb-178">If there are no Group Policies and each scope's execution policy is set to **Undefined**, then **Restricted** becomes the effective policy for all users.</span></span>

<span data-ttu-id="01dbb-179">De acceptabla värdena för körnings principen är följande:</span><span class="sxs-lookup"><span data-stu-id="01dbb-179">The acceptable execution policy values are as follows:</span></span>

- <span data-ttu-id="01dbb-180">**AllSigned**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-180">**AllSigned**.</span></span> <span data-ttu-id="01dbb-181">Kräver att alla skript och konfigurationsfiler signeras av en betrodd utgivare, inklusive skript som skrivits på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="01dbb-181">Requires that all scripts and configuration files are signed by a trusted publisher, including scripts written on the local computer.</span></span>
- <span data-ttu-id="01dbb-182">**Kringgå**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-182">**Bypass**.</span></span> <span data-ttu-id="01dbb-183">Inget blockeras och det finns inga varningar eller prompter.</span><span class="sxs-lookup"><span data-stu-id="01dbb-183">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="01dbb-184">**Standard**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-184">**Default**.</span></span> <span data-ttu-id="01dbb-185">Anger standard körnings principen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-185">Sets the default execution policy.</span></span> <span data-ttu-id="01dbb-186">**Begränsat** för Windows-klienter eller **RemoteSigned** för Windows-servrar.</span><span class="sxs-lookup"><span data-stu-id="01dbb-186">**Restricted** for Windows clients or **RemoteSigned** for Windows servers.</span></span>
- <span data-ttu-id="01dbb-187">**RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-187">**RemoteSigned**.</span></span> <span data-ttu-id="01dbb-188">Kräver att alla skript och konfigurationsfiler som hämtas från Internet signeras av en betrodd utgivare.</span><span class="sxs-lookup"><span data-stu-id="01dbb-188">Requires that all scripts and configuration files downloaded from the Internet are signed by a trusted publisher.</span></span> <span data-ttu-id="01dbb-189">Standard körnings principen för Windows Server-datorer.</span><span class="sxs-lookup"><span data-stu-id="01dbb-189">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="01dbb-190">**Begränsad**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-190">**Restricted**.</span></span> <span data-ttu-id="01dbb-191">Läser inte in konfigurationsfiler eller kör skript.</span><span class="sxs-lookup"><span data-stu-id="01dbb-191">Doesn't load configuration files or run scripts.</span></span> <span data-ttu-id="01dbb-192">Standard körnings principen för Windows-klientdatorer.</span><span class="sxs-lookup"><span data-stu-id="01dbb-192">The default execution policy Windows client computers.</span></span>
- <span data-ttu-id="01dbb-193">**Odefinierat**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-193">**Undefined**.</span></span> <span data-ttu-id="01dbb-194">Ingen körnings princip har angetts för omfånget.</span><span class="sxs-lookup"><span data-stu-id="01dbb-194">No execution policy is set for the scope.</span></span> <span data-ttu-id="01dbb-195">Tar bort en tilldelad körnings princip från en omfattning som inte har angetts av en grupprincip.</span><span class="sxs-lookup"><span data-stu-id="01dbb-195">Removes an assigned execution policy from a scope that is not set by a Group Policy.</span></span> <span data-ttu-id="01dbb-196">Om körnings principen i alla omfattningar är **Odefinierad** är den effektiva körnings principen **begränsad**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-196">If the execution policy in all scopes is **Undefined**, the effective execution policy is **Restricted**.</span></span>
- <span data-ttu-id="01dbb-197">**Obegränsad**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-197">**Unrestricted**.</span></span> <span data-ttu-id="01dbb-198">Från och med PowerShell 6,0 är detta standard körnings principen för datorer som inte är Windows-datorer och kan inte ändras.</span><span class="sxs-lookup"><span data-stu-id="01dbb-198">Beginning in PowerShell 6.0, this is the default execution policy for non-Windows computers and can't be changed.</span></span> <span data-ttu-id="01dbb-199">Läser in alla konfigurationsfiler och kör alla skript.</span><span class="sxs-lookup"><span data-stu-id="01dbb-199">Loads all configuration files and runs all scripts.</span></span> <span data-ttu-id="01dbb-200">Om du kör ett osignerat skript som hämtades från Internet tillfrågas du om behörighet innan det körs.</span><span class="sxs-lookup"><span data-stu-id="01dbb-200">If you run an unsigned script that was downloaded from the internet, you're prompted for permission before it runs.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: AllSigned, Bypass, Default, RemoteSigned, Restricted, Undefined, Unrestricted

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="01dbb-201">-Force</span><span class="sxs-lookup"><span data-stu-id="01dbb-201">-Force</span></span>

<span data-ttu-id="01dbb-202">Ignorerar alla bekräftelse meddelanden.</span><span class="sxs-lookup"><span data-stu-id="01dbb-202">Suppresses all the confirmation prompts.</span></span> <span data-ttu-id="01dbb-203">Använd försiktighet med den här parametern för att undvika oväntade resultat.</span><span class="sxs-lookup"><span data-stu-id="01dbb-203">Use caution with this parameter to avoid unexpected results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01dbb-204">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="01dbb-204">-Scope</span></span>

<span data-ttu-id="01dbb-205">Anger det omfång som påverkas av en körnings princip.</span><span class="sxs-lookup"><span data-stu-id="01dbb-205">Specifies the scope that is affected by an execution policy.</span></span> <span data-ttu-id="01dbb-206">Standard omfånget är **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-206">The default scope is **LocalMachine**.</span></span>

<span data-ttu-id="01dbb-207">Den gällande körnings principen bestäms av prioritetsordningen enligt följande:</span><span class="sxs-lookup"><span data-stu-id="01dbb-207">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="01dbb-208">**MachinePolicy**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-208">**MachinePolicy**.</span></span> <span data-ttu-id="01dbb-209">Anges av en grupprincip för alla användare av datorn.</span><span class="sxs-lookup"><span data-stu-id="01dbb-209">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="01dbb-210">**UserPolicy**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-210">**UserPolicy**.</span></span> <span data-ttu-id="01dbb-211">Anges av en grupprincip för datorns aktuella användare.</span><span class="sxs-lookup"><span data-stu-id="01dbb-211">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="01dbb-212">**Processen**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-212">**Process**.</span></span> <span data-ttu-id="01dbb-213">Påverkar endast den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-213">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="01dbb-214">**CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-214">**CurrentUser**.</span></span> <span data-ttu-id="01dbb-215">Påverkar endast den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="01dbb-215">Affects only the current user.</span></span>
- <span data-ttu-id="01dbb-216">**LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-216">**LocalMachine**.</span></span> <span data-ttu-id="01dbb-217">Standard omfattning som påverkar alla användare av datorn.</span><span class="sxs-lookup"><span data-stu-id="01dbb-217">Default scope that affects all users of the computer.</span></span>

<span data-ttu-id="01dbb-218">**Process** omfånget påverkar endast den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-218">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="01dbb-219">Körnings principen sparas i miljövariabeln i `$env:PSExecutionPolicyPreference` stället för registret.</span><span class="sxs-lookup"><span data-stu-id="01dbb-219">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="01dbb-220">När PowerShell-sessionen stängs raderas variabeln och värdet.</span><span class="sxs-lookup"><span data-stu-id="01dbb-220">When the PowerShell session is closed, the variable and value are deleted.</span></span>

<span data-ttu-id="01dbb-221">Körnings principer för **CurrentUser** -omfånget skrivs till registrerings data filen **HKEY_LOCAL_USER**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-221">Execution policies for the **CurrentUser** scope are written to the registry hive **HKEY_LOCAL_USER**.</span></span>

<span data-ttu-id="01dbb-222">Körnings principer för **LocalMachine** -omfånget skrivs till registrerings data filen **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="01dbb-222">Execution policies for the **LocalMachine** scope are written to the registry hive **HKEY_LOCAL_MACHINE**.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 1
Default value: LocalMachine
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="01dbb-223">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="01dbb-223">-WhatIf</span></span>

<span data-ttu-id="01dbb-224">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="01dbb-224">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="01dbb-225">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="01dbb-225">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01dbb-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="01dbb-226">CommonParameters</span></span>

<span data-ttu-id="01dbb-227">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="01dbb-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="01dbb-228">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="01dbb-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="01dbb-229">INDATA</span><span class="sxs-lookup"><span data-stu-id="01dbb-229">INPUTS</span></span>

### <span data-ttu-id="01dbb-230">Microsoft.PowerShell.ExecutionPolicy, system. String</span><span class="sxs-lookup"><span data-stu-id="01dbb-230">Microsoft.PowerShell.ExecutionPolicy, System.String</span></span>

<span data-ttu-id="01dbb-231">Du kan skicka vidare ett körnings princip objekt eller en sträng som innehåller namnet på en körnings princip till `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="01dbb-231">You can pipe an execution policy object or a string that contains the name of an execution policy to `Set-ExecutionPolicy`.</span></span>

## <span data-ttu-id="01dbb-232">UTDATA</span><span class="sxs-lookup"><span data-stu-id="01dbb-232">OUTPUTS</span></span>

### <span data-ttu-id="01dbb-233">Inga</span><span class="sxs-lookup"><span data-stu-id="01dbb-233">None</span></span>

<span data-ttu-id="01dbb-234">`Set-ExecutionPolicy` returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="01dbb-234">`Set-ExecutionPolicy` doesn't return any output.</span></span>

## <span data-ttu-id="01dbb-235">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="01dbb-235">NOTES</span></span>

<span data-ttu-id="01dbb-236">`Set-ExecutionPolicy` ändrar inte **MachinePolicy** -och **UserPolicy** -omfattningarna eftersom de anges av grup principer.</span><span class="sxs-lookup"><span data-stu-id="01dbb-236">`Set-ExecutionPolicy` doesn't change the **MachinePolicy** and **UserPolicy** scopes because they are set by Group Policies.</span></span>

<span data-ttu-id="01dbb-237">`Set-ExecutionPolicy` åsidosätter inte en grupprincip, även om användar preferensen är mer restriktiv än principen.</span><span class="sxs-lookup"><span data-stu-id="01dbb-237">`Set-ExecutionPolicy` doesn't override a Group Policy, even if the user preference is more restrictive than the policy.</span></span>

<span data-ttu-id="01dbb-238">Om grupprincip **Aktivera skript körning** har Aktiver ATS för datorn eller användaren, sparas användar inställningen, men den är inte effektiv.</span><span class="sxs-lookup"><span data-stu-id="01dbb-238">If the Group Policy **Turn on Script Execution** is enabled for the computer or user, the user preference is saved, but it is not effective.</span></span> <span data-ttu-id="01dbb-239">PowerShell visar ett meddelande som förklarar konflikten.</span><span class="sxs-lookup"><span data-stu-id="01dbb-239">PowerShell displays a message that explains the conflict.</span></span>

## <span data-ttu-id="01dbb-240">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="01dbb-240">RELATED LINKS</span></span>

[<span data-ttu-id="01dbb-241">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="01dbb-241">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="01dbb-242">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="01dbb-242">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="01dbb-243">about_Providers</span><span class="sxs-lookup"><span data-stu-id="01dbb-243">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="01dbb-244">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="01dbb-244">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="01dbb-245">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="01dbb-245">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="01dbb-246">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="01dbb-246">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="01dbb-247">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="01dbb-247">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="01dbb-248">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="01dbb-248">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="01dbb-249">Avblockera – fil</span><span class="sxs-lookup"><span data-stu-id="01dbb-249">Unblock-File</span></span>](../Microsoft.PowerShell.Utility/Unblock-File.md)

