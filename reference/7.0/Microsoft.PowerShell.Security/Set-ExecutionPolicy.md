---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ExecutionPolicy
ms.openlocfilehash: d3724c79f5864295c70d5addd46a8a133862d0ec
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93263031"
---
# <span data-ttu-id="dd30e-103">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="dd30e-103">Set-ExecutionPolicy</span></span>

## <span data-ttu-id="dd30e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="dd30e-104">SYNOPSIS</span></span>
<span data-ttu-id="dd30e-105">Anger PowerShell-körnings principer för Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="dd30e-105">Sets the PowerShell execution policies for Windows computers.</span></span>

## <span data-ttu-id="dd30e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dd30e-106">SYNTAX</span></span>

### <span data-ttu-id="dd30e-107">Alla</span><span class="sxs-lookup"><span data-stu-id="dd30e-107">All</span></span>

```
Set-ExecutionPolicy [-ExecutionPolicy] <ExecutionPolicy> [[-Scope] <ExecutionPolicyScope>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="dd30e-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="dd30e-108">DESCRIPTION</span></span>

<span data-ttu-id="dd30e-109">`Set-ExecutionPolicy`Cmdleten ändrar PowerShell-körnings principer för Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="dd30e-109">The `Set-ExecutionPolicy` cmdlet changes PowerShell execution policies for Windows computers.</span></span> <span data-ttu-id="dd30e-110">Mer information finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="dd30e-110">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="dd30e-111">Från och med PowerShell 6,0 för datorer som inte är Windows-datorer är standard körnings principen **obegränsad** och kan inte ändras.</span><span class="sxs-lookup"><span data-stu-id="dd30e-111">Beginning in PowerShell 6.0 for non-Windows computers, the default execution policy is **Unrestricted** and can't be changed.</span></span> <span data-ttu-id="dd30e-112">`Set-ExecutionPolicy`Cmdleten är tillgänglig, men PowerShell visar ett konsol meddelande som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="dd30e-112">The `Set-ExecutionPolicy` cmdlet is available, but PowerShell displays a console message that it's not supported.</span></span>

<span data-ttu-id="dd30e-113">En körnings princip är en del av säkerhets strategin för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd30e-113">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="dd30e-114">Körnings principer avgör om du kan läsa in konfigurationsfiler, till exempel din PowerShell-profil eller köra skript.</span><span class="sxs-lookup"><span data-stu-id="dd30e-114">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="dd30e-115">Och om skripten måste signeras digitalt innan de körs.</span><span class="sxs-lookup"><span data-stu-id="dd30e-115">And, whether scripts must be digitally signed before they are run.</span></span>

<span data-ttu-id="dd30e-116">`Set-ExecutionPolicy`Cmdletens standard omfång är **LocalMachine** , som påverkar alla som använder datorn.</span><span class="sxs-lookup"><span data-stu-id="dd30e-116">The `Set-ExecutionPolicy` cmdlet's default scope is **LocalMachine** , which affects everyone who uses the computer.</span></span> <span data-ttu-id="dd30e-117">Om du vill ändra körnings principen för **LocalMachine** startar du PowerShell med **Kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-117">To change the execution policy for **LocalMachine** , start PowerShell with **Run as Administrator**.</span></span>

<span data-ttu-id="dd30e-118">Använd om du vill visa körnings principerna för varje omfång i prioritetsordning `Get-ExecutionPolicy -List` .</span><span class="sxs-lookup"><span data-stu-id="dd30e-118">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="dd30e-119">Om du vill se den effektiva körnings principen för PowerShell-sessionen använder du utan `Get-ExecutionPolicy` parametrar.</span><span class="sxs-lookup"><span data-stu-id="dd30e-119">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

## <span data-ttu-id="dd30e-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="dd30e-120">EXAMPLES</span></span>

### <span data-ttu-id="dd30e-121">Exempel 1: Ange en körnings princip</span><span class="sxs-lookup"><span data-stu-id="dd30e-121">Example 1: Set an execution policy</span></span>

<span data-ttu-id="dd30e-122">I det här exemplet visas hur du anger körnings principen för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="dd30e-122">This example shows how to set the execution policy for the local computer.</span></span>

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

<span data-ttu-id="dd30e-123">`Set-ExecutionPolicy`Cmdleten använder parametern **ExecutionPolicy** för att ange **RemoteSigned** -principen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-123">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="dd30e-124">Parametern **omfattning** Anger standardvärdet för omfattning, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-124">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span> <span data-ttu-id="dd30e-125">Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.</span><span class="sxs-lookup"><span data-stu-id="dd30e-125">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="dd30e-126">Exempel 2: Ange en princip för körning som står i konflikt med en grupprincip</span><span class="sxs-lookup"><span data-stu-id="dd30e-126">Example 2: Set an execution policy that conflicts with a Group Policy</span></span>

<span data-ttu-id="dd30e-127">Med det här kommandot försöker du ange **LocalMachine** -Omfattningens körnings princip till **begränsad**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-127">This command attempts to set the **LocalMachine** scope's execution policy to **Restricted**.</span></span>
<span data-ttu-id="dd30e-128">**LocalMachine** är mer restriktiv, men är inte den effektiva principen eftersom den står i konflikt med en Grupprincip.</span><span class="sxs-lookup"><span data-stu-id="dd30e-128">**LocalMachine** is more restrictive, but isn't the effective policy because it conflicts with a Group Policy.</span></span> <span data-ttu-id="dd30e-129">Den **begränsade** principen skrivs till registrerings data filen **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-129">The **Restricted** policy is written to the registry hive **HKEY_LOCAL_MACHINE**.</span></span>

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

<span data-ttu-id="dd30e-130">`Set-ExecutionPolicy`Cmdleten använder parametern **ExecutionPolicy** för att ange den **begränsade** principen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-130">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **Restricted** policy.</span></span> <span data-ttu-id="dd30e-131">Parametern **omfattning** Anger standardvärdet för omfattning, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-131">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span>
<span data-ttu-id="dd30e-132">`Get-ChildItem`Cmdleten använder parametern **Path** med **HKLM** -providern för att ange register plats.</span><span class="sxs-lookup"><span data-stu-id="dd30e-132">The `Get-ChildItem` cmdlet uses the **Path** parameter with the **HKLM** provider to specify registry location.</span></span>

### <span data-ttu-id="dd30e-133">Exempel 3: tillämpa körnings principen från en fjärrdator på en lokal dator</span><span class="sxs-lookup"><span data-stu-id="dd30e-133">Example 3: Apply the execution policy from a remote computer to a local computer</span></span>

<span data-ttu-id="dd30e-134">Det här kommandot hämtar objektet för körnings principen från en fjärrdator och anger principen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="dd30e-134">This command gets the execution policy object from a remote computer and sets the policy on the local computer.</span></span> <span data-ttu-id="dd30e-135">`Get-ExecutionPolicy` skickar ett **Microsoft.PowerShell.ExecutionPolicy** -objekt nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-135">`Get-ExecutionPolicy` sends a **Microsoft.PowerShell.ExecutionPolicy** object down the pipeline.</span></span> <span data-ttu-id="dd30e-136">`Set-ExecutionPolicy` accepterar pipeline-ininformation och kräver inte parametern **ExecutionPolicy** .</span><span class="sxs-lookup"><span data-stu-id="dd30e-136">`Set-ExecutionPolicy` accepts pipeline input and doesn't require the **ExecutionPolicy** parameter.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -ScriptBlock { Get-ExecutionPolicy } | Set-ExecutionPolicy
```

<span data-ttu-id="dd30e-137">`Invoke-Command`Cmdleten körs på den lokala datorn och skickar **script block** till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="dd30e-137">The `Invoke-Command` cmdlet is executed at the local computer and sends the **ScriptBlock** to the remote computer.</span></span> <span data-ttu-id="dd30e-138">Parametern **computername** anger fjärran sluten dator, **Server01**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-138">The **ComputerName** parameter specifies the remote computer, **Server01**.</span></span> <span data-ttu-id="dd30e-139">Parametern **script block** körs `Get-ExecutionPolicy` på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="dd30e-139">The **ScriptBlock** parameter runs `Get-ExecutionPolicy` on the remote computer.</span></span> <span data-ttu-id="dd30e-140">`Get-ExecutionPolicy`Objektet skickas ned pipelinen till `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="dd30e-140">The `Get-ExecutionPolicy` object is sent down the pipeline to the `Set-ExecutionPolicy`.</span></span>
<span data-ttu-id="dd30e-141">`Set-ExecutionPolicy` tillämpar körnings principen på den lokala datorns standard omfång, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-141">`Set-ExecutionPolicy` applies the execution policy to the local computer's default scope, **LocalMachine**.</span></span>

### <span data-ttu-id="dd30e-142">Exempel 4: ange omfånget för en körnings princip</span><span class="sxs-lookup"><span data-stu-id="dd30e-142">Example 4: Set the scope for an execution policy</span></span>

<span data-ttu-id="dd30e-143">I det här exemplet visas hur du anger en körnings princip för en angiven omfattning, **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-143">This example shows how to set an execution policy for a specified scope, **CurrentUser**.</span></span> <span data-ttu-id="dd30e-144">**CurrentUser** -omfånget påverkar endast den användare som anger det här omfånget.</span><span class="sxs-lookup"><span data-stu-id="dd30e-144">The **CurrentUser** scope only affects the user who sets this scope.</span></span>

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

<span data-ttu-id="dd30e-145">`Set-ExecutionPolicy` använder parametern **ExecutionPolicy** för att ange **AllSigned** -principen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-145">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span>
<span data-ttu-id="dd30e-146">Parametern **omfattning** anger **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-146">The **Scope** parameter specifies the **CurrentUser**.</span></span> <span data-ttu-id="dd30e-147">Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.</span><span class="sxs-lookup"><span data-stu-id="dd30e-147">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

<span data-ttu-id="dd30e-148">Den effektiva körnings principen för användaren blir **AllSigned**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-148">The effective execution policy for the user becomes **AllSigned**.</span></span>

### <span data-ttu-id="dd30e-149">Exempel 5: ta bort körnings principen för den aktuella användaren</span><span class="sxs-lookup"><span data-stu-id="dd30e-149">Example 5: Remove the execution policy for the current user</span></span>

<span data-ttu-id="dd30e-150">Det här exemplet visar hur använder den **odefinierade** körnings principen för att ta bort en körnings princip för en angiven omfattning.</span><span class="sxs-lookup"><span data-stu-id="dd30e-150">This example shows how use the **Undefined** execution policy to remove an execution policy for a specified scope.</span></span>

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

<span data-ttu-id="dd30e-151">`Set-ExecutionPolicy` använder parametern **ExecutionPolicy** för att ange den **odefinierade** principen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-151">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **Undefined** policy.</span></span>
<span data-ttu-id="dd30e-152">Parametern **omfattning** anger **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-152">The **Scope** parameter specifies the **CurrentUser**.</span></span> <span data-ttu-id="dd30e-153">Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.</span><span class="sxs-lookup"><span data-stu-id="dd30e-153">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="dd30e-154">Exempel 6: Ange körnings principen för den aktuella PowerShell-sessionen</span><span class="sxs-lookup"><span data-stu-id="dd30e-154">Example 6: Set the execution policy for the current PowerShell session</span></span>

<span data-ttu-id="dd30e-155">**Process** omfånget påverkar endast den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-155">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="dd30e-156">Körnings principen sparas i miljö variabeln `$env:PSExecutionPolicyPreference` och tas bort när sessionen stängs.</span><span class="sxs-lookup"><span data-stu-id="dd30e-156">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference` and is deleted when the session is closed.</span></span>

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

<span data-ttu-id="dd30e-157">`Set-ExecutionPolicy`Använder parametern **ExecutionPolicy** för att ange **AllSigned** -principen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-157">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span> <span data-ttu-id="dd30e-158">Parametern **omfattning** anger värde **processen**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-158">The **Scope** parameter specifies the value **Process**.</span></span> <span data-ttu-id="dd30e-159">Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.</span><span class="sxs-lookup"><span data-stu-id="dd30e-159">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="dd30e-160">Exempel 7: avblockera ett skript för att köra det utan att ändra körnings principen</span><span class="sxs-lookup"><span data-stu-id="dd30e-160">Example 7: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="dd30e-161">Det här exemplet visar hur **RemoteSigned** -körnings principen förhindrar att osignerade skript körs.</span><span class="sxs-lookup"><span data-stu-id="dd30e-161">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="dd30e-162">Vi rekommenderar att du läser skript koden och kontrollerar att den är säker **innan** du använder `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dd30e-162">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="dd30e-163">`Unblock-File`Cmdleten avblockerar skripten så att de kan köras, men ändrar inte körnings principen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-163">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

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

<span data-ttu-id="dd30e-164">`Set-ExecutionPolicy`Använder parametern **ExecutionPolicy** för att ange **RemoteSigned** -principen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-164">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="dd30e-165">Principen har angetts för standard omfånget, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-165">The policy is set for the default scope, **LocalMachine**.</span></span>

<span data-ttu-id="dd30e-166">`Get-ExecutionPolicy`Cmdleten visar att **RemoteSigned** är den effektiva körnings principen för den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-166">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="dd30e-167">**Start-ActivityTracker.ps1** skriptet körs från den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-167">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="dd30e-168">Skriptet blockeras av **RemoteSigned** eftersom skriptet inte har signerats digitalt.</span><span class="sxs-lookup"><span data-stu-id="dd30e-168">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="dd30e-169">I det här exemplet har skript koden granskats och verifierats som säker för körning.</span><span class="sxs-lookup"><span data-stu-id="dd30e-169">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="dd30e-170">`Unblock-File`Cmdleten använder parametern **Path** för att avblockera skriptet.</span><span class="sxs-lookup"><span data-stu-id="dd30e-170">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="dd30e-171">För att kontrol lera att `Unblock-File` inte har ändrat körnings principen, `Get-ExecutionPolicy` visar den effektiva körnings principen, **RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-171">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned**.</span></span>

<span data-ttu-id="dd30e-172">Skriptet **Start-ActivityTracker.ps1** köras från den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-172">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="dd30e-173">Skriptet börjar köras eftersom det har avblockerats av `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dd30e-173">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="dd30e-174">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="dd30e-174">PARAMETERS</span></span>

### <span data-ttu-id="dd30e-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dd30e-175">-Confirm</span></span>

<span data-ttu-id="dd30e-176">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dd30e-176">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="dd30e-177">– ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="dd30e-177">-ExecutionPolicy</span></span>

<span data-ttu-id="dd30e-178">Anger körnings principen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-178">Specifies the execution policy.</span></span> <span data-ttu-id="dd30e-179">Om det inte finns några grup principer och varje omfattnings körnings princip är inställd på **Odefinierad** , blir det **begränsade** principen för alla användare.</span><span class="sxs-lookup"><span data-stu-id="dd30e-179">If there are no Group Policies and each scope's execution policy is set to **Undefined** , then **Restricted** becomes the effective policy for all users.</span></span>

<span data-ttu-id="dd30e-180">De acceptabla värdena för körnings principen är följande:</span><span class="sxs-lookup"><span data-stu-id="dd30e-180">The acceptable execution policy values are as follows:</span></span>

- <span data-ttu-id="dd30e-181">**AllSigned**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-181">**AllSigned**.</span></span> <span data-ttu-id="dd30e-182">Kräver att alla skript och konfigurationsfiler signeras av en betrodd utgivare, inklusive skript som skrivits på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="dd30e-182">Requires that all scripts and configuration files are signed by a trusted publisher, including scripts written on the local computer.</span></span>
- <span data-ttu-id="dd30e-183">**Kringgå**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-183">**Bypass**.</span></span> <span data-ttu-id="dd30e-184">Inget blockeras och det finns inga varningar eller prompter.</span><span class="sxs-lookup"><span data-stu-id="dd30e-184">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="dd30e-185">**Standard**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-185">**Default**.</span></span> <span data-ttu-id="dd30e-186">Anger standard körnings principen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-186">Sets the default execution policy.</span></span> <span data-ttu-id="dd30e-187">**Begränsat** för Windows-klienter eller **RemoteSigned** för Windows-servrar.</span><span class="sxs-lookup"><span data-stu-id="dd30e-187">**Restricted** for Windows clients or **RemoteSigned** for Windows servers.</span></span>
- <span data-ttu-id="dd30e-188">**RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-188">**RemoteSigned**.</span></span> <span data-ttu-id="dd30e-189">Kräver att alla skript och konfigurationsfiler som hämtas från Internet signeras av en betrodd utgivare.</span><span class="sxs-lookup"><span data-stu-id="dd30e-189">Requires that all scripts and configuration files downloaded from the Internet are signed by a trusted publisher.</span></span> <span data-ttu-id="dd30e-190">Standard körnings principen för Windows Server-datorer.</span><span class="sxs-lookup"><span data-stu-id="dd30e-190">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="dd30e-191">**Begränsad**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-191">**Restricted**.</span></span> <span data-ttu-id="dd30e-192">Läser inte in konfigurationsfiler eller kör skript.</span><span class="sxs-lookup"><span data-stu-id="dd30e-192">Doesn't load configuration files or run scripts.</span></span> <span data-ttu-id="dd30e-193">Standard körnings principen för Windows-klientdatorer.</span><span class="sxs-lookup"><span data-stu-id="dd30e-193">The default execution policy Windows client computers.</span></span>
- <span data-ttu-id="dd30e-194">**Odefinierat**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-194">**Undefined**.</span></span> <span data-ttu-id="dd30e-195">Ingen körnings princip har angetts för omfånget.</span><span class="sxs-lookup"><span data-stu-id="dd30e-195">No execution policy is set for the scope.</span></span> <span data-ttu-id="dd30e-196">Tar bort en tilldelad körnings princip från en omfattning som inte har angetts av en grupprincip.</span><span class="sxs-lookup"><span data-stu-id="dd30e-196">Removes an assigned execution policy from a scope that is not set by a Group Policy.</span></span> <span data-ttu-id="dd30e-197">Om körnings principen i alla omfattningar är **Odefinierad** är den effektiva körnings principen **begränsad**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-197">If the execution policy in all scopes is **Undefined** , the effective execution policy is **Restricted**.</span></span>
- <span data-ttu-id="dd30e-198">**Obegränsad**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-198">**Unrestricted**.</span></span> <span data-ttu-id="dd30e-199">Från och med PowerShell 6,0 är detta standard körnings principen för datorer som inte är Windows-datorer och kan inte ändras.</span><span class="sxs-lookup"><span data-stu-id="dd30e-199">Beginning in PowerShell 6.0, this is the default execution policy for non-Windows computers and can't be changed.</span></span> <span data-ttu-id="dd30e-200">Läser in alla konfigurationsfiler och kör alla skript.</span><span class="sxs-lookup"><span data-stu-id="dd30e-200">Loads all configuration files and runs all scripts.</span></span> <span data-ttu-id="dd30e-201">Om du kör ett osignerat skript som hämtades från Internet tillfrågas du om behörighet innan det körs.</span><span class="sxs-lookup"><span data-stu-id="dd30e-201">If you run an unsigned script that was downloaded from the internet, you're prompted for permission before it runs.</span></span>

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

### <span data-ttu-id="dd30e-202">-Force</span><span class="sxs-lookup"><span data-stu-id="dd30e-202">-Force</span></span>

<span data-ttu-id="dd30e-203">Ignorerar alla bekräftelse meddelanden.</span><span class="sxs-lookup"><span data-stu-id="dd30e-203">Suppresses all the confirmation prompts.</span></span> <span data-ttu-id="dd30e-204">Använd försiktighet med den här parametern för att undvika oväntade resultat.</span><span class="sxs-lookup"><span data-stu-id="dd30e-204">Use caution with this parameter to avoid unexpected results.</span></span>

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

### <span data-ttu-id="dd30e-205">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="dd30e-205">-Scope</span></span>

<span data-ttu-id="dd30e-206">Anger det omfång som påverkas av en körnings princip.</span><span class="sxs-lookup"><span data-stu-id="dd30e-206">Specifies the scope that is affected by an execution policy.</span></span> <span data-ttu-id="dd30e-207">Standard omfånget är **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-207">The default scope is **LocalMachine**.</span></span>

<span data-ttu-id="dd30e-208">Den gällande körnings principen bestäms av prioritetsordningen enligt följande:</span><span class="sxs-lookup"><span data-stu-id="dd30e-208">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="dd30e-209">**MachinePolicy**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-209">**MachinePolicy**.</span></span> <span data-ttu-id="dd30e-210">Anges av en grupprincip för alla användare av datorn.</span><span class="sxs-lookup"><span data-stu-id="dd30e-210">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="dd30e-211">**UserPolicy**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-211">**UserPolicy**.</span></span> <span data-ttu-id="dd30e-212">Anges av en grupprincip för datorns aktuella användare.</span><span class="sxs-lookup"><span data-stu-id="dd30e-212">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="dd30e-213">**Processen**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-213">**Process**.</span></span> <span data-ttu-id="dd30e-214">Påverkar endast den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-214">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="dd30e-215">**CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-215">**CurrentUser**.</span></span> <span data-ttu-id="dd30e-216">Påverkar endast den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="dd30e-216">Affects only the current user.</span></span>
- <span data-ttu-id="dd30e-217">**LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-217">**LocalMachine**.</span></span> <span data-ttu-id="dd30e-218">Standard omfattning som påverkar alla användare av datorn.</span><span class="sxs-lookup"><span data-stu-id="dd30e-218">Default scope that affects all users of the computer.</span></span>

<span data-ttu-id="dd30e-219">**Process** omfånget påverkar endast den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-219">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="dd30e-220">Körnings principen sparas i miljövariabeln i `$env:PSExecutionPolicyPreference` stället för registret.</span><span class="sxs-lookup"><span data-stu-id="dd30e-220">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="dd30e-221">När PowerShell-sessionen stängs raderas variabeln och värdet.</span><span class="sxs-lookup"><span data-stu-id="dd30e-221">When the PowerShell session is closed, the variable and value are deleted.</span></span>

<span data-ttu-id="dd30e-222">Körnings principer för **CurrentUser** -omfånget skrivs till registrerings data filen **HKEY_LOCAL_USER**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-222">Execution policies for the **CurrentUser** scope are written to the registry hive **HKEY_LOCAL_USER**.</span></span>

<span data-ttu-id="dd30e-223">Körnings principer för **LocalMachine** -omfånget skrivs till registrerings data filen **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="dd30e-223">Execution policies for the **LocalMachine** scope are written to the registry hive **HKEY_LOCAL_MACHINE**.</span></span>

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

### <span data-ttu-id="dd30e-224">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dd30e-224">-WhatIf</span></span>

<span data-ttu-id="dd30e-225">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="dd30e-225">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="dd30e-226">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="dd30e-226">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="dd30e-227">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dd30e-227">CommonParameters</span></span>

<span data-ttu-id="dd30e-228">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dd30e-228">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dd30e-229">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="dd30e-229">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dd30e-230">INDATA</span><span class="sxs-lookup"><span data-stu-id="dd30e-230">INPUTS</span></span>

### <span data-ttu-id="dd30e-231">Microsoft.PowerShell.ExecutionPolicy, system. String</span><span class="sxs-lookup"><span data-stu-id="dd30e-231">Microsoft.PowerShell.ExecutionPolicy, System.String</span></span>

<span data-ttu-id="dd30e-232">Du kan skicka vidare ett körnings princip objekt eller en sträng som innehåller namnet på en körnings princip till `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="dd30e-232">You can pipe an execution policy object or a string that contains the name of an execution policy to `Set-ExecutionPolicy`.</span></span>

## <span data-ttu-id="dd30e-233">UTDATA</span><span class="sxs-lookup"><span data-stu-id="dd30e-233">OUTPUTS</span></span>

### <span data-ttu-id="dd30e-234">Inget</span><span class="sxs-lookup"><span data-stu-id="dd30e-234">None</span></span>

<span data-ttu-id="dd30e-235">`Set-ExecutionPolicy` returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="dd30e-235">`Set-ExecutionPolicy` doesn't return any output.</span></span>

## <span data-ttu-id="dd30e-236">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="dd30e-236">NOTES</span></span>

<span data-ttu-id="dd30e-237">`Set-ExecutionPolicy` ändrar inte **MachinePolicy** -och **UserPolicy** -omfattningarna eftersom de anges av grup principer.</span><span class="sxs-lookup"><span data-stu-id="dd30e-237">`Set-ExecutionPolicy` doesn't change the **MachinePolicy** and **UserPolicy** scopes because they are set by Group Policies.</span></span>

<span data-ttu-id="dd30e-238">`Set-ExecutionPolicy` åsidosätter inte en grupprincip, även om användar preferensen är mer restriktiv än principen.</span><span class="sxs-lookup"><span data-stu-id="dd30e-238">`Set-ExecutionPolicy` doesn't override a Group Policy, even if the user preference is more restrictive than the policy.</span></span>

<span data-ttu-id="dd30e-239">Om grupprincip **Aktivera skript körning** har Aktiver ATS för datorn eller användaren, sparas användar inställningen, men den är inte effektiv.</span><span class="sxs-lookup"><span data-stu-id="dd30e-239">If the Group Policy **Turn on Script Execution** is enabled for the computer or user, the user preference is saved, but it is not effective.</span></span> <span data-ttu-id="dd30e-240">PowerShell visar ett meddelande som förklarar konflikten.</span><span class="sxs-lookup"><span data-stu-id="dd30e-240">PowerShell displays a message that explains the conflict.</span></span>

## <span data-ttu-id="dd30e-241">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="dd30e-241">RELATED LINKS</span></span>

[<span data-ttu-id="dd30e-242">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="dd30e-242">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="dd30e-243">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="dd30e-243">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="dd30e-244">about_Providers</span><span class="sxs-lookup"><span data-stu-id="dd30e-244">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="dd30e-245">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="dd30e-245">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="dd30e-246">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="dd30e-246">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="dd30e-247">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="dd30e-247">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="dd30e-248">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="dd30e-248">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="dd30e-249">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="dd30e-249">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="dd30e-250">Avblockera – fil</span><span class="sxs-lookup"><span data-stu-id="dd30e-250">Unblock-File</span></span>](../Microsoft.PowerShell.Utility/Unblock-File.md)
