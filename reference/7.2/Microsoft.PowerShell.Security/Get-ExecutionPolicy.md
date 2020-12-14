---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExecutionPolicy
ms.openlocfilehash: d6555f1abc824add4613654461106af34045e1a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708730"
---
# <span data-ttu-id="1e868-102">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="1e868-102">Get-ExecutionPolicy</span></span>

## <span data-ttu-id="1e868-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1e868-103">SYNOPSIS</span></span>
<span data-ttu-id="1e868-104">Hämtar körnings principerna för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1e868-104">Gets the execution policies for the current session.</span></span>

## <span data-ttu-id="1e868-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1e868-105">SYNTAX</span></span>

### <span data-ttu-id="1e868-106">Alla</span><span class="sxs-lookup"><span data-stu-id="1e868-106">All</span></span>

```
Get-ExecutionPolicy [[-Scope] <ExecutionPolicyScope>] [-List] [<CommonParameters>]
```

## <span data-ttu-id="1e868-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1e868-107">DESCRIPTION</span></span>

<span data-ttu-id="1e868-108">Använd om du vill visa körnings principerna för varje omfång i prioritetsordning `Get-ExecutionPolicy -List` .</span><span class="sxs-lookup"><span data-stu-id="1e868-108">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="1e868-109">Om du vill se den effektiva körnings principen för PowerShell-sessionen använder du utan `Get-ExecutionPolicy` parametrar.</span><span class="sxs-lookup"><span data-stu-id="1e868-109">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

<span data-ttu-id="1e868-110">Den effektiva körnings principen bestäms av körnings principer som ställs in av `Set-ExecutionPolicy` och Grupprincip inställningar.</span><span class="sxs-lookup"><span data-stu-id="1e868-110">The effective execution policy is determined by execution policies that are set by `Set-ExecutionPolicy` and Group Policy settings.</span></span>

<span data-ttu-id="1e868-111">Mer information finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="1e868-111">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="1e868-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1e868-112">EXAMPLES</span></span>

### <span data-ttu-id="1e868-113">Exempel 1: Hämta alla körnings principer</span><span class="sxs-lookup"><span data-stu-id="1e868-113">Example 1: Get all execution policies</span></span>

<span data-ttu-id="1e868-114">Det här kommandot visar körnings principerna för varje omfång i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="1e868-114">This command displays the execution policies for each scope in the order of precedence.</span></span>

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

<span data-ttu-id="1e868-115">`Get-ExecutionPolicy`Cmdleten använder **list parametern List** för att visa varje omfattnings körnings princip.</span><span class="sxs-lookup"><span data-stu-id="1e868-115">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span>

### <span data-ttu-id="1e868-116">Exempel 2: Ange en körnings princip</span><span class="sxs-lookup"><span data-stu-id="1e868-116">Example 2: Set an execution policy</span></span>

<span data-ttu-id="1e868-117">I det här exemplet visas hur du anger en körnings princip för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="1e868-117">This example shows how to set an execution policy for the local computer.</span></span>

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

<span data-ttu-id="1e868-118">`Set-ExecutionPolicy`Cmdleten använder parametern **ExecutionPolicy** för att ange **RemoteSigned** -principen.</span><span class="sxs-lookup"><span data-stu-id="1e868-118">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="1e868-119">Parametern **omfattning** Anger standardvärdet för omfattning, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="1e868-119">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span> <span data-ttu-id="1e868-120">Om du vill visa inställningarna för körnings principen använder du `Get-ExecutionPolicy` cmdleten med **list** parametern.</span><span class="sxs-lookup"><span data-stu-id="1e868-120">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="1e868-121">Exempel 3: hämta den effektiva körnings principen</span><span class="sxs-lookup"><span data-stu-id="1e868-121">Example 3: Get the effective execution policy</span></span>

<span data-ttu-id="1e868-122">Det här exemplet visar hur du visar den effektiva körnings principen för en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="1e868-122">This example shows how to display the effective execution policy for a PowerShell session.</span></span>

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

<span data-ttu-id="1e868-123">`Get-ExecutionPolicy`Cmdleten använder **list parametern List** för att visa varje omfattnings körnings princip.</span><span class="sxs-lookup"><span data-stu-id="1e868-123">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span> <span data-ttu-id="1e868-124">`Get-ExecutionPolicy`Cmdleten körs utan en parameter för att visa den effektiva körnings principen, **AllSigned**.</span><span class="sxs-lookup"><span data-stu-id="1e868-124">The `Get-ExecutionPolicy` cmdlet is run without a parameter to display the effective execution policy, **AllSigned**.</span></span>

### <span data-ttu-id="1e868-125">Exempel 4: avblockera ett skript för att köra det utan att ändra körnings principen</span><span class="sxs-lookup"><span data-stu-id="1e868-125">Example 4: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="1e868-126">Det här exemplet visar hur **RemoteSigned** -körnings principen förhindrar att osignerade skript körs.</span><span class="sxs-lookup"><span data-stu-id="1e868-126">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="1e868-127">Vi rekommenderar att du läser skript koden och kontrollerar att den är säker **innan** du använder `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1e868-127">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="1e868-128">`Unblock-File`Cmdleten avblockerar skripten så att de kan köras, men ändrar inte körnings principen.</span><span class="sxs-lookup"><span data-stu-id="1e868-128">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

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

<span data-ttu-id="1e868-129">`Set-ExecutionPolicy`Använder parametern **ExecutionPolicy** för att ange **RemoteSigned** -principen.</span><span class="sxs-lookup"><span data-stu-id="1e868-129">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="1e868-130">Principen har angetts för standard omfånget, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="1e868-130">The policy is set for the default scope, **LocalMachine**.</span></span>

<span data-ttu-id="1e868-131">`Get-ExecutionPolicy`Cmdleten visar att **RemoteSigned** är den effektiva körnings principen för den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="1e868-131">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="1e868-132">**Start-ActivityTracker.ps1** skriptet körs från den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="1e868-132">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="1e868-133">Skriptet blockeras av **RemoteSigned** eftersom skriptet inte har signerats digitalt.</span><span class="sxs-lookup"><span data-stu-id="1e868-133">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="1e868-134">I det här exemplet har skript koden granskats och verifierats som säker för körning.</span><span class="sxs-lookup"><span data-stu-id="1e868-134">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="1e868-135">`Unblock-File`Cmdleten använder parametern **Path** för att avblockera skriptet.</span><span class="sxs-lookup"><span data-stu-id="1e868-135">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="1e868-136">För att kontrol lera att `Unblock-File` inte har ändrat körnings principen, `Get-ExecutionPolicy` visar den effektiva körnings principen, **RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="1e868-136">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned**.</span></span>

<span data-ttu-id="1e868-137">Skriptet **Start-ActivityTracker.ps1** köras från den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="1e868-137">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="1e868-138">Skriptet börjar köras eftersom det har avblockerats av `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1e868-138">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="1e868-139">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1e868-139">PARAMETERS</span></span>

### <span data-ttu-id="1e868-140">– Lista</span><span class="sxs-lookup"><span data-stu-id="1e868-140">-List</span></span>

<span data-ttu-id="1e868-141">Hämtar alla körnings princip värden för sessionen som anges i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="1e868-141">Gets all execution policy values for the session listed in precedence order.</span></span> <span data-ttu-id="1e868-142">Som standard `Get-ExecutionPolicy` hämtar endast den gällande körnings principen.</span><span class="sxs-lookup"><span data-stu-id="1e868-142">By default, `Get-ExecutionPolicy` gets only the effective execution policy.</span></span>

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

### <span data-ttu-id="1e868-143">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="1e868-143">-Scope</span></span>

<span data-ttu-id="1e868-144">Anger det omfång som påverkas av en körnings princip.</span><span class="sxs-lookup"><span data-stu-id="1e868-144">Specifies the scope that is affected by an execution policy.</span></span>

<span data-ttu-id="1e868-145">Den gällande körnings principen bestäms av prioritetsordningen enligt följande:</span><span class="sxs-lookup"><span data-stu-id="1e868-145">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="1e868-146">**MachinePolicy**.</span><span class="sxs-lookup"><span data-stu-id="1e868-146">**MachinePolicy**.</span></span> <span data-ttu-id="1e868-147">Anges av en grupprincip för alla användare av datorn.</span><span class="sxs-lookup"><span data-stu-id="1e868-147">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="1e868-148">**UserPolicy**.</span><span class="sxs-lookup"><span data-stu-id="1e868-148">**UserPolicy**.</span></span> <span data-ttu-id="1e868-149">Anges av en grupprincip för datorns aktuella användare.</span><span class="sxs-lookup"><span data-stu-id="1e868-149">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="1e868-150">**Processen**.</span><span class="sxs-lookup"><span data-stu-id="1e868-150">**Process**.</span></span> <span data-ttu-id="1e868-151">Påverkar endast den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="1e868-151">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="1e868-152">**CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="1e868-152">**CurrentUser**.</span></span> <span data-ttu-id="1e868-153">Påverkar endast den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="1e868-153">Affects only the current user.</span></span>
- <span data-ttu-id="1e868-154">**LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="1e868-154">**LocalMachine**.</span></span> <span data-ttu-id="1e868-155">Standard omfattning som påverkar alla användare av datorn.</span><span class="sxs-lookup"><span data-stu-id="1e868-155">Default scope that affects all users of the computer.</span></span>

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

### <span data-ttu-id="1e868-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1e868-156">CommonParameters</span></span>

<span data-ttu-id="1e868-157">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1e868-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1e868-158">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1e868-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1e868-159">INDATA</span><span class="sxs-lookup"><span data-stu-id="1e868-159">INPUTS</span></span>

### <span data-ttu-id="1e868-160">Inga</span><span class="sxs-lookup"><span data-stu-id="1e868-160">None</span></span>

<span data-ttu-id="1e868-161">`Get-ExecutionPolicy` accepterar inte ininformation från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="1e868-161">`Get-ExecutionPolicy` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="1e868-162">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1e868-162">OUTPUTS</span></span>

### <span data-ttu-id="1e868-163">Microsoft.PowerShell.ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="1e868-163">Microsoft.PowerShell.ExecutionPolicy</span></span>

<span data-ttu-id="1e868-164">Cmdleten returnerar alltid **obegränsade** på Linux-och MacOS-plattformar.</span><span class="sxs-lookup"><span data-stu-id="1e868-164">The cmdlet always returns **Unrestricted** on Linux and macOS platforms.</span></span>

## <span data-ttu-id="1e868-165">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1e868-165">NOTES</span></span>

<span data-ttu-id="1e868-166">En körnings princip är en del av säkerhets strategin för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1e868-166">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="1e868-167">Körnings principer avgör om du kan läsa in konfigurationsfiler, till exempel din PowerShell-profil eller köra skript.</span><span class="sxs-lookup"><span data-stu-id="1e868-167">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="1e868-168">Och om skripten måste signeras digitalt innan de körs.</span><span class="sxs-lookup"><span data-stu-id="1e868-168">And, whether scripts must be digitally signed before they are run.</span></span>

## <span data-ttu-id="1e868-169">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1e868-169">RELATED LINKS</span></span>

[<span data-ttu-id="1e868-170">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="1e868-170">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)

[<span data-ttu-id="1e868-171">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="1e868-171">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="1e868-172">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="1e868-172">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="1e868-173">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="1e868-173">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="1e868-174">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="1e868-174">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)
