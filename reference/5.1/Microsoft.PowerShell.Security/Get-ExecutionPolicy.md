---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExecutionPolicy
ms.openlocfilehash: 4a805874c039e97574a78bb3bbc7a4d6e958d2ca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265238"
---
# <span data-ttu-id="c3377-103">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="c3377-103">Get-ExecutionPolicy</span></span>

## <span data-ttu-id="c3377-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c3377-104">SYNOPSIS</span></span>
<span data-ttu-id="c3377-105">Hämtar körnings principerna för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c3377-105">Gets the execution policies for the current session.</span></span>

## <span data-ttu-id="c3377-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c3377-106">SYNTAX</span></span>

### <span data-ttu-id="c3377-107">Alla</span><span class="sxs-lookup"><span data-stu-id="c3377-107">All</span></span>

```
Get-ExecutionPolicy [[-Scope] <ExecutionPolicyScope>] [-List] [<CommonParameters>]
```

## <span data-ttu-id="c3377-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c3377-108">DESCRIPTION</span></span>

<span data-ttu-id="c3377-109">Använd om du vill visa körnings principerna för varje omfång i prioritetsordning `Get-ExecutionPolicy -List` .</span><span class="sxs-lookup"><span data-stu-id="c3377-109">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="c3377-110">Om du vill se den effektiva körnings principen för PowerShell-sessionen använder du utan `Get-ExecutionPolicy` parametrar.</span><span class="sxs-lookup"><span data-stu-id="c3377-110">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

<span data-ttu-id="c3377-111">Den effektiva körnings principen bestäms av körnings principer som ställs in av `Set-ExecutionPolicy` och Grupprincip inställningar.</span><span class="sxs-lookup"><span data-stu-id="c3377-111">The effective execution policy is determined by execution policies that are set by `Set-ExecutionPolicy` and Group Policy settings.</span></span>

<span data-ttu-id="c3377-112">Mer information finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="c3377-112">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="c3377-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c3377-113">EXAMPLES</span></span>

### <span data-ttu-id="c3377-114">Exempel 1: Hämta alla körnings principer</span><span class="sxs-lookup"><span data-stu-id="c3377-114">Example 1: Get all execution policies</span></span>

<span data-ttu-id="c3377-115">Det här kommandot visar körnings principerna för varje omfång i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="c3377-115">This command displays the execution policies for each scope in the order of precedence.</span></span>

```powershell
Get-ExecutionPolicy -List
```

```Output
Scope          ExecutionPolicy
-----          ---------------
MachinePolicy  Undefined
UserPolicy     Undefined
Process        Undefined
CurrentUser    AllSigned
LocalMachine   Undefined
```

<span data-ttu-id="c3377-116">`Get-ExecutionPolicy`Cmdleten använder **list parametern List** för att visa varje omfattnings körnings princip.</span><span class="sxs-lookup"><span data-stu-id="c3377-116">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span>

### <span data-ttu-id="c3377-117">Exempel 2: Ange en körnings princip</span><span class="sxs-lookup"><span data-stu-id="c3377-117">Example 2: Set an execution policy</span></span>

<span data-ttu-id="c3377-118">I det här exemplet visas hur du anger en körnings princip för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c3377-118">This example shows how to set an execution policy for the local computer.</span></span>

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
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="c3377-119">`Set-ExecutionPolicy`Cmdleten använder parametern **ExecutionPolicy** för att ange **RemoteSigned** -principen.</span><span class="sxs-lookup"><span data-stu-id="c3377-119">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="c3377-120">Parametern **omfattning** Anger standardvärdet för omfattning, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="c3377-120">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span> <span data-ttu-id="c3377-121">Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.</span><span class="sxs-lookup"><span data-stu-id="c3377-121">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="c3377-122">Exempel 3: hämta den effektiva körnings principen</span><span class="sxs-lookup"><span data-stu-id="c3377-122">Example 3: Get the effective execution policy</span></span>

<span data-ttu-id="c3377-123">Det här exemplet visar hur du visar den effektiva körnings principen för en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="c3377-123">This example shows how to display the effective execution policy for a PowerShell session.</span></span>

```
PS> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned

PS> Get-ExecutionPolicy

AllSigned
```

<span data-ttu-id="c3377-124">`Get-ExecutionPolicy`Cmdleten använder **list parametern List** för att visa varje omfattnings körnings princip.</span><span class="sxs-lookup"><span data-stu-id="c3377-124">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span> <span data-ttu-id="c3377-125">`Get-ExecutionPolicy`Cmdleten körs utan en parameter för att visa den effektiva körnings principen, **AllSigned**.</span><span class="sxs-lookup"><span data-stu-id="c3377-125">The `Get-ExecutionPolicy` cmdlet is run without a parameter to display the effective execution policy, **AllSigned**.</span></span>

### <span data-ttu-id="c3377-126">Exempel 4: avblockera ett skript för att köra det utan att ändra körnings principen</span><span class="sxs-lookup"><span data-stu-id="c3377-126">Example 4: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="c3377-127">Det här exemplet visar hur **RemoteSigned** -körnings principen förhindrar att osignerade skript körs.</span><span class="sxs-lookup"><span data-stu-id="c3377-127">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="c3377-128">Vi rekommenderar att du läser skript koden och kontrollerar att den är säker **innan** du använder `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c3377-128">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="c3377-129">`Unblock-File`Cmdleten avblockerar skripten så att de kan köras, men ändrar inte körnings principen.</span><span class="sxs-lookup"><span data-stu-id="c3377-129">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

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

<span data-ttu-id="c3377-130">`Set-ExecutionPolicy`Använder parametern **ExecutionPolicy** för att ange **RemoteSigned** -principen.</span><span class="sxs-lookup"><span data-stu-id="c3377-130">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="c3377-131">Principen har angetts för standard omfånget, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="c3377-131">The policy is set for the default scope, **LocalMachine**.</span></span>

<span data-ttu-id="c3377-132">`Get-ExecutionPolicy`Cmdleten visar att **RemoteSigned** är den effektiva körnings principen för den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c3377-132">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="c3377-133">**Start-ActivityTracker.ps1** skriptet körs från den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c3377-133">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="c3377-134">Skriptet blockeras av **RemoteSigned** eftersom skriptet inte har signerats digitalt.</span><span class="sxs-lookup"><span data-stu-id="c3377-134">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="c3377-135">I det här exemplet har skript koden granskats och verifierats som säker för körning.</span><span class="sxs-lookup"><span data-stu-id="c3377-135">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="c3377-136">`Unblock-File`Cmdleten använder parametern **Path** för att avblockera skriptet.</span><span class="sxs-lookup"><span data-stu-id="c3377-136">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="c3377-137">För att kontrol lera att `Unblock-File` inte har ändrat körnings principen, `Get-ExecutionPolicy` visar den effektiva körnings principen, **RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="c3377-137">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned**.</span></span>

<span data-ttu-id="c3377-138">Skriptet **Start-ActivityTracker.ps1** köras från den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c3377-138">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="c3377-139">Skriptet börjar köras eftersom det har avblockerats av `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c3377-139">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="c3377-140">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c3377-140">PARAMETERS</span></span>

### <span data-ttu-id="c3377-141">– Lista</span><span class="sxs-lookup"><span data-stu-id="c3377-141">-List</span></span>

<span data-ttu-id="c3377-142">Hämtar alla körnings princip värden för sessionen som anges i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="c3377-142">Gets all execution policy values for the session listed in precedence order.</span></span> <span data-ttu-id="c3377-143">Som standard `Get-ExecutionPolicy` hämtar endast den gällande körnings principen.</span><span class="sxs-lookup"><span data-stu-id="c3377-143">By default, `Get-ExecutionPolicy` gets only the effective execution policy.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3377-144">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="c3377-144">-Scope</span></span>

<span data-ttu-id="c3377-145">Anger det omfång som påverkas av en körnings princip.</span><span class="sxs-lookup"><span data-stu-id="c3377-145">Specifies the scope that is affected by an execution policy.</span></span>

<span data-ttu-id="c3377-146">Den gällande körnings principen bestäms av prioritetsordningen enligt följande:</span><span class="sxs-lookup"><span data-stu-id="c3377-146">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="c3377-147">**MachinePolicy**.</span><span class="sxs-lookup"><span data-stu-id="c3377-147">**MachinePolicy**.</span></span> <span data-ttu-id="c3377-148">Anges av en grupprincip för alla användare av datorn.</span><span class="sxs-lookup"><span data-stu-id="c3377-148">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="c3377-149">**UserPolicy**.</span><span class="sxs-lookup"><span data-stu-id="c3377-149">**UserPolicy**.</span></span> <span data-ttu-id="c3377-150">Anges av en grupprincip för datorns aktuella användare.</span><span class="sxs-lookup"><span data-stu-id="c3377-150">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="c3377-151">**Processen**.</span><span class="sxs-lookup"><span data-stu-id="c3377-151">**Process**.</span></span> <span data-ttu-id="c3377-152">Påverkar endast den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c3377-152">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="c3377-153">**CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="c3377-153">**CurrentUser**.</span></span> <span data-ttu-id="c3377-154">Påverkar endast den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="c3377-154">Affects only the current user.</span></span>
- <span data-ttu-id="c3377-155">**LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="c3377-155">**LocalMachine**.</span></span> <span data-ttu-id="c3377-156">Standard omfattning som påverkar alla användare av datorn.</span><span class="sxs-lookup"><span data-stu-id="c3377-156">Default scope that affects all users of the computer.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 0
Default value: Effective execution policy
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c3377-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c3377-157">CommonParameters</span></span>

<span data-ttu-id="c3377-158">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c3377-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c3377-159">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c3377-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c3377-160">INDATA</span><span class="sxs-lookup"><span data-stu-id="c3377-160">INPUTS</span></span>

### <span data-ttu-id="c3377-161">Inget</span><span class="sxs-lookup"><span data-stu-id="c3377-161">None</span></span>

<span data-ttu-id="c3377-162">`Get-ExecutionPolicy` accepterar inte ininformation från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="c3377-162">`Get-ExecutionPolicy` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="c3377-163">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c3377-163">OUTPUTS</span></span>

### <span data-ttu-id="c3377-164">Microsoft.PowerShell.ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="c3377-164">Microsoft.PowerShell.ExecutionPolicy</span></span>

## <span data-ttu-id="c3377-165">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c3377-165">NOTES</span></span>

<span data-ttu-id="c3377-166">En körnings princip är en del av säkerhets strategin för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3377-166">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="c3377-167">Körnings principer avgör om du kan läsa in konfigurationsfiler, till exempel din PowerShell-profil eller köra skript.</span><span class="sxs-lookup"><span data-stu-id="c3377-167">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="c3377-168">Och om skripten måste signeras digitalt innan de körs.</span><span class="sxs-lookup"><span data-stu-id="c3377-168">And, whether scripts must be digitally signed before they are run.</span></span>

## <span data-ttu-id="c3377-169">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c3377-169">RELATED LINKS</span></span>

[<span data-ttu-id="c3377-170">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="c3377-170">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)

[<span data-ttu-id="c3377-171">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="c3377-171">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="c3377-172">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="c3377-172">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="c3377-173">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="c3377-173">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="c3377-174">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="c3377-174">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)
