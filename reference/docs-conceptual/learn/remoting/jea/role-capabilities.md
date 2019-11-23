---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA Role Capabilities
ms.openlocfilehash: 613557d03bb481f9280a06ca1506166a18b4dab2
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416798"
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="658ae-103">JEA Role Capabilities</span><span class="sxs-lookup"><span data-stu-id="658ae-103">JEA Role Capabilities</span></span>

<span data-ttu-id="658ae-104">When creating a JEA endpoint, you need to define one or more role capabilities that describe what someone can do in a JEA session.</span><span class="sxs-lookup"><span data-stu-id="658ae-104">When creating a JEA endpoint, you need to define one or more role capabilities that describe what someone can do in a JEA session.</span></span> <span data-ttu-id="658ae-105">A role capability is a PowerShell data file with the `.psrc` extension that lists all the cmdlets, functions, providers, and external programs that are made available to connecting users.</span><span class="sxs-lookup"><span data-stu-id="658ae-105">A role capability is a PowerShell data file with the `.psrc` extension that lists all the cmdlets, functions, providers, and external programs that are made available to connecting users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="658ae-106">Determine which commands to allow</span><span class="sxs-lookup"><span data-stu-id="658ae-106">Determine which commands to allow</span></span>

<span data-ttu-id="658ae-107">The first step in creating a role capability file is to consider what the users need access to.</span><span class="sxs-lookup"><span data-stu-id="658ae-107">The first step in creating a role capability file is to consider what the users need access to.</span></span> <span data-ttu-id="658ae-108">The requirements gathering process can take a while, but it's an important process.</span><span class="sxs-lookup"><span data-stu-id="658ae-108">The requirements gathering process can take a while, but it's an important process.</span></span> <span data-ttu-id="658ae-109">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span><span class="sxs-lookup"><span data-stu-id="658ae-109">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span> <span data-ttu-id="658ae-110">Allowing access to too many cmdlets and functions can allow users to do more than you intended and weaken your security stance.</span><span class="sxs-lookup"><span data-stu-id="658ae-110">Allowing access to too many cmdlets and functions can allow users to do more than you intended and weaken your security stance.</span></span>

<span data-ttu-id="658ae-111">How you go about this process depends on your organization and goals.</span><span class="sxs-lookup"><span data-stu-id="658ae-111">How you go about this process depends on your organization and goals.</span></span> <span data-ttu-id="658ae-112">The following tips can help ensure you're on the right path.</span><span class="sxs-lookup"><span data-stu-id="658ae-112">The following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="658ae-113">**Identify** the commands users are using to get their jobs done.</span><span class="sxs-lookup"><span data-stu-id="658ae-113">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="658ae-114">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts and logs.</span><span class="sxs-lookup"><span data-stu-id="658ae-114">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts and logs.</span></span>
2. <span data-ttu-id="658ae-115">**Update** use of command-line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span><span class="sxs-lookup"><span data-stu-id="658ae-115">**Update** use of command-line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="658ae-116">External programs can't be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span><span class="sxs-lookup"><span data-stu-id="658ae-116">External programs can't be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="658ae-117">**Restrict** the scope of the cmdlets to only allow specific parameters or parameter values.</span><span class="sxs-lookup"><span data-stu-id="658ae-117">**Restrict** the scope of the cmdlets to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="658ae-118">This is especially important if users should manage only part of a system.</span><span class="sxs-lookup"><span data-stu-id="658ae-118">This is especially important if users should manage only part of a system.</span></span>
4. <span data-ttu-id="658ae-119">**Create** custom functions to replace complex commands or commands that are difficult to constrain in JEA.</span><span class="sxs-lookup"><span data-stu-id="658ae-119">**Create** custom functions to replace complex commands or commands that are difficult to constrain in JEA.</span></span> <span data-ttu-id="658ae-120">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span><span class="sxs-lookup"><span data-stu-id="658ae-120">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="658ae-121">**Test** the scoped list of allowable commands with your users or automation services, and adjust as necessary.</span><span class="sxs-lookup"><span data-stu-id="658ae-121">**Test** the scoped list of allowable commands with your users or automation services, and adjust as necessary.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="658ae-122">Examples of potentially dangerous commands</span><span class="sxs-lookup"><span data-stu-id="658ae-122">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="658ae-123">Careful selection of commands is important to ensure the JEA endpoint doesn't allow the user to elevate their permissions.</span><span class="sxs-lookup"><span data-stu-id="658ae-123">Careful selection of commands is important to ensure the JEA endpoint doesn't allow the user to elevate their permissions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="658ae-124">Essential information required for user successCommands in a JEA session are often run with elevated privileges.</span><span class="sxs-lookup"><span data-stu-id="658ae-124">Essential information required for user successCommands in a JEA session are often run with elevated privileges.</span></span>

<span data-ttu-id="658ae-125">The following table contains examples of commands that can be used maliciously if allowed in an unconstrained state.</span><span class="sxs-lookup"><span data-stu-id="658ae-125">The following table contains examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span> <span data-ttu-id="658ae-126">This isn't an exhaustive list and should only be used as a cautionary starting point.</span><span class="sxs-lookup"><span data-stu-id="658ae-126">This isn't an exhaustive list and should only be used as a cautionary starting point.</span></span>

|                                            <span data-ttu-id="658ae-127">Risk</span><span class="sxs-lookup"><span data-stu-id="658ae-127">Risk</span></span>                                            |                                <span data-ttu-id="658ae-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="658ae-128">Example</span></span>                                |                                                                              <span data-ttu-id="658ae-129">Related commands</span><span class="sxs-lookup"><span data-stu-id="658ae-129">Related commands</span></span>                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="658ae-130">Granting the connecting user admin privileges to bypass JEA</span><span class="sxs-lookup"><span data-stu-id="658ae-130">Granting the connecting user admin privileges to bypass JEA</span></span>                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="658ae-131">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="658ae-131">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>                                                                                                        |
| <span data-ttu-id="658ae-132">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span><span class="sxs-lookup"><span data-stu-id="658ae-132">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'`                   | <span data-ttu-id="658ae-133">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="658ae-133">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span> |

## <a name="create-a-role-capability-file"></a><span data-ttu-id="658ae-134">Create a role capability file</span><span class="sxs-lookup"><span data-stu-id="658ae-134">Create a role capability file</span></span>

<span data-ttu-id="658ae-135">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="658ae-135">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="658ae-136">The resulting role capability file should be edited to allow the commands required for the role.</span><span class="sxs-lookup"><span data-stu-id="658ae-136">The resulting role capability file should be edited to allow the commands required for the role.</span></span> <span data-ttu-id="658ae-137">The PowerShell help documentation contains several examples of how you can configure the file.</span><span class="sxs-lookup"><span data-stu-id="658ae-137">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="658ae-138">Allowing PowerShell cmdlets and functions</span><span class="sxs-lookup"><span data-stu-id="658ae-138">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="658ae-139">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisibleCmdlets or VisibleFunctions fields.</span><span class="sxs-lookup"><span data-stu-id="658ae-139">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisibleCmdlets or VisibleFunctions fields.</span></span> <span data-ttu-id="658ae-140">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the **CommandType** property in the output.</span><span class="sxs-lookup"><span data-stu-id="658ae-140">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the **CommandType** property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="658ae-141">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span><span class="sxs-lookup"><span data-stu-id="658ae-141">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span> <span data-ttu-id="658ae-142">A DNS admin, for example, probably only needs access to restart the DNS service.</span><span class="sxs-lookup"><span data-stu-id="658ae-142">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span> <span data-ttu-id="658ae-143">In multi-tenant environments, tenants have access to self-service management tools.</span><span class="sxs-lookup"><span data-stu-id="658ae-143">In multi-tenant environments, tenants have access to self-service management tools.</span></span> <span data-ttu-id="658ae-144">Tenants should be limited to managing their own resources.</span><span class="sxs-lookup"><span data-stu-id="658ae-144">Tenants should be limited to managing their own resources.</span></span> <span data-ttu-id="658ae-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span><span class="sxs-lookup"><span data-stu-id="658ae-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

<span data-ttu-id="658ae-146">In more advanced scenarios, you may also need to restrict the values a user may use with these parameters.</span><span class="sxs-lookup"><span data-stu-id="658ae-146">In more advanced scenarios, you may also need to restrict the values a user may use with these parameters.</span></span> <span data-ttu-id="658ae-147">Role capabilities let you define a set of values or a regular expression pattern that determine what input is allowed.</span><span class="sxs-lookup"><span data-stu-id="658ae-147">Role capabilities let you define a set of values or a regular expression pattern that determine what input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="658ae-148">The [common PowerShell parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters) are always allowed, even if you restrict the available parameters.</span><span class="sxs-lookup"><span data-stu-id="658ae-148">The [common PowerShell parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="658ae-149">You should not explicitly list them in the Parameters field.</span><span class="sxs-lookup"><span data-stu-id="658ae-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="658ae-150">The table below describes the various ways you can customize a visible cmdlet or function.</span><span class="sxs-lookup"><span data-stu-id="658ae-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="658ae-151">You can mix and match any of the below in the **VisibleCmdlets** field.</span><span class="sxs-lookup"><span data-stu-id="658ae-151">You can mix and match any of the below in the **VisibleCmdlets** field.</span></span>

|                                           <span data-ttu-id="658ae-152">Exempel</span><span class="sxs-lookup"><span data-stu-id="658ae-152">Example</span></span>                                           |                                                             <span data-ttu-id="658ae-153">Use case</span><span class="sxs-lookup"><span data-stu-id="658ae-153">Use case</span></span>                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="658ae-154">`'My-Func'` eller `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="658ae-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                      | <span data-ttu-id="658ae-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span><span class="sxs-lookup"><span data-stu-id="658ae-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>                                                      |
| `'MyModule\My-Func'`                                                                        | <span data-ttu-id="658ae-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span><span class="sxs-lookup"><span data-stu-id="658ae-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>                           |
| `'My-*'`                                                                                    | <span data-ttu-id="658ae-157">Allows the user to run any cmdlet or function with the verb `My`.</span><span class="sxs-lookup"><span data-stu-id="658ae-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>                                                                 |
| `'*-Func'`                                                                                  | <span data-ttu-id="658ae-158">Allows the user to run any cmdlet or function with the noun `Func`.</span><span class="sxs-lookup"><span data-stu-id="658ae-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | <span data-ttu-id="658ae-159">Allows the user to run `My-Func` with the `Param1` and `Param2` parameters.</span><span class="sxs-lookup"><span data-stu-id="658ae-159">Allows the user to run `My-Func` with the `Param1` and `Param2` parameters.</span></span> <span data-ttu-id="658ae-160">Any value can be supplied to the parameters.</span><span class="sxs-lookup"><span data-stu-id="658ae-160">Any value can be supplied to the parameters.</span></span>          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | <span data-ttu-id="658ae-161">Allows the user to run `My-Func` with the `Param1` parameter.</span><span class="sxs-lookup"><span data-stu-id="658ae-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="658ae-162">Only "Value1" and "Value2" can be supplied to the parameter.</span><span class="sxs-lookup"><span data-stu-id="658ae-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | <span data-ttu-id="658ae-163">Allows the user to run `My-Func` with the `Param1` parameter.</span><span class="sxs-lookup"><span data-stu-id="658ae-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="658ae-164">Any value starting with "contoso" can be supplied to the parameter.</span><span class="sxs-lookup"><span data-stu-id="658ae-164">Any value starting with "contoso" can be supplied to the parameter.</span></span> |

> [!WARNING]
> <span data-ttu-id="658ae-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span><span class="sxs-lookup"><span data-stu-id="658ae-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span> <span data-ttu-id="658ae-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span><span class="sxs-lookup"><span data-stu-id="658ae-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="658ae-167">You can't apply both a **ValidatePattern** and **ValidateSet** to the same cmdlet or function.</span><span class="sxs-lookup"><span data-stu-id="658ae-167">You can't apply both a **ValidatePattern** and **ValidateSet** to the same cmdlet or function.</span></span>

<span data-ttu-id="658ae-168">If you do, the **ValidatePattern** overrides the **ValidateSet**.</span><span class="sxs-lookup"><span data-stu-id="658ae-168">If you do, the **ValidatePattern** overrides the **ValidateSet**.</span></span>

<span data-ttu-id="658ae-169">For more information about **ValidatePattern**, check out [this *Hey, Scripting Guy!* post](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](/powershell/module/microsoft.powershell.core/about/about_regular_expressions) reference content.</span><span class="sxs-lookup"><span data-stu-id="658ae-169">For more information about **ValidatePattern**, check out [this *Hey, Scripting Guy!* post](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](/powershell/module/microsoft.powershell.core/about/about_regular_expressions) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="658ae-170">Allowing external commands and PowerShell scripts</span><span class="sxs-lookup"><span data-stu-id="658ae-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="658ae-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the **VisibleExternalCommands** field.</span><span class="sxs-lookup"><span data-stu-id="658ae-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the **VisibleExternalCommands** field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="658ae-172">Where possible, to use PowerShell cmdlet or function equivalents for any external executables you authorize since you have control over the parameters allowed with PowerShell cmdlets and functions.</span><span class="sxs-lookup"><span data-stu-id="658ae-172">Where possible, to use PowerShell cmdlet or function equivalents for any external executables you authorize since you have control over the parameters allowed with PowerShell cmdlets and functions.</span></span>

<span data-ttu-id="658ae-173">Many executables allow you to read the current state and then change it by providing different parameters.</span><span class="sxs-lookup"><span data-stu-id="658ae-173">Many executables allow you to read the current state and then change it by providing different parameters.</span></span>

<span data-ttu-id="658ae-174">For example, consider the role of a file server admin that manages network shares hosted on a system.</span><span class="sxs-lookup"><span data-stu-id="658ae-174">For example, consider the role of a file server admin that manages network shares hosted on a system.</span></span> <span data-ttu-id="658ae-175">One way of managing shares is to use `net share`.</span><span class="sxs-lookup"><span data-stu-id="658ae-175">One way of managing shares is to use `net share`.</span></span> <span data-ttu-id="658ae-176">However, allowing **net.exe** is dangerous because the user could use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span><span class="sxs-lookup"><span data-stu-id="658ae-176">However, allowing **net.exe** is dangerous because the user could use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span> <span data-ttu-id="658ae-177">A more secure option is to allow [Get-SmbShare](/powershell/module/smbshare/get-smbshare), which achieves the same result but has a much more limited scope.</span><span class="sxs-lookup"><span data-stu-id="658ae-177">A more secure option is to allow [Get-SmbShare](/powershell/module/smbshare/get-smbshare), which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="658ae-178">When making external commands available to users in a JEA session, always specify the complete path to the executable.</span><span class="sxs-lookup"><span data-stu-id="658ae-178">When making external commands available to users in a JEA session, always specify the complete path to the executable.</span></span> <span data-ttu-id="658ae-179">This prevents the execution of similarly named and potentially malicious programs located elsewhere on the system.</span><span class="sxs-lookup"><span data-stu-id="658ae-179">This prevents the execution of similarly named and potentially malicious programs located elsewhere on the system.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="658ae-180">Allowing access to PowerShell providers</span><span class="sxs-lookup"><span data-stu-id="658ae-180">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="658ae-181">By default, no PowerShell providers are available in JEA sessions.</span><span class="sxs-lookup"><span data-stu-id="658ae-181">By default, no PowerShell providers are available in JEA sessions.</span></span> <span data-ttu-id="658ae-182">This reduces the risk of sensitive information and configuration settings being disclosed to the connecting user.</span><span class="sxs-lookup"><span data-stu-id="658ae-182">This reduces the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="658ae-183">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span><span class="sxs-lookup"><span data-stu-id="658ae-183">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span> <span data-ttu-id="658ae-184">For a full list of providers, run `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="658ae-184">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="658ae-185">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, consider writing a custom function that works with the provider on the user's behalf.</span><span class="sxs-lookup"><span data-stu-id="658ae-185">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, consider writing a custom function that works with the provider on the user's behalf.</span></span> <span data-ttu-id="658ae-186">The functions, cmdlets, and external programs available in a JEA session aren't subject to the same constraints as JEA.</span><span class="sxs-lookup"><span data-stu-id="658ae-186">The functions, cmdlets, and external programs available in a JEA session aren't subject to the same constraints as JEA.</span></span> <span data-ttu-id="658ae-187">They can access any provider by default.</span><span class="sxs-lookup"><span data-stu-id="658ae-187">They can access any provider by default.</span></span> <span data-ttu-id="658ae-188">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to or from a JEA endpoint is required.</span><span class="sxs-lookup"><span data-stu-id="658ae-188">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to or from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="658ae-189">Creating custom functions</span><span class="sxs-lookup"><span data-stu-id="658ae-189">Creating custom functions</span></span>

<span data-ttu-id="658ae-190">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span><span class="sxs-lookup"><span data-stu-id="658ae-190">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span> <span data-ttu-id="658ae-191">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span><span class="sxs-lookup"><span data-stu-id="658ae-191">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span> <span data-ttu-id="658ae-192">You can write simple functions in the **FunctionDefinitions** field:</span><span class="sxs-lookup"><span data-stu-id="658ae-192">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending |
            Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="658ae-193">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span><span class="sxs-lookup"><span data-stu-id="658ae-193">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>

<span data-ttu-id="658ae-194">The body (script block) of custom functions runs in the default language mode for the system and isn't subject to JEA's language constraints.</span><span class="sxs-lookup"><span data-stu-id="658ae-194">The body (script block) of custom functions runs in the default language mode for the system and isn't subject to JEA's language constraints.</span></span> <span data-ttu-id="658ae-195">This means that functions can access the file system and registry, and run commands that weren't made visible in the role capability file.</span><span class="sxs-lookup"><span data-stu-id="658ae-195">This means that functions can access the file system and registry, and run commands that weren't made visible in the role capability file.</span></span> <span data-ttu-id="658ae-196">Take care to avoid running arbitrary code when using parameters.</span><span class="sxs-lookup"><span data-stu-id="658ae-196">Take care to avoid running arbitrary code when using parameters.</span></span> <span data-ttu-id="658ae-197">Avoid piping user input directly into cmdlets like `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="658ae-197">Avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="658ae-198">In the above example, notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="658ae-198">In the above example, notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="658ae-199">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span><span class="sxs-lookup"><span data-stu-id="658ae-199">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="658ae-200">By default, `Select-Object` is a constrained cmdlet in all JEA sessions that doesn't allow the selection of arbitrary properties on objects.</span><span class="sxs-lookup"><span data-stu-id="658ae-200">By default, `Select-Object` is a constrained cmdlet in all JEA sessions that doesn't allow the selection of arbitrary properties on objects.</span></span> <span data-ttu-id="658ae-201">To use the unconstrained `Select-Object` in functions, you must explicitly request the full implementation using the FQMN.</span><span class="sxs-lookup"><span data-stu-id="658ae-201">To use the unconstrained `Select-Object` in functions, you must explicitly request the full implementation using the FQMN.</span></span> <span data-ttu-id="658ae-202">Any constrained cmdlet in a JEA session has the same constraints when invoked from a function.</span><span class="sxs-lookup"><span data-stu-id="658ae-202">Any constrained cmdlet in a JEA session has the same constraints when invoked from a function.</span></span> <span data-ttu-id="658ae-203">For more information, see [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).</span><span class="sxs-lookup"><span data-stu-id="658ae-203">For more information, see [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="658ae-204">If you're writing several custom functions, it's more convenient to put them in a PowerShell script module.</span><span class="sxs-lookup"><span data-stu-id="658ae-204">If you're writing several custom functions, it's more convenient to put them in a PowerShell script module.</span></span> <span data-ttu-id="658ae-205">You make those functions visible in the JEA session using the **VisibleFunctions** field like you would with built-in and third-party modules.</span><span class="sxs-lookup"><span data-stu-id="658ae-205">You make those functions visible in the JEA session using the **VisibleFunctions** field like you would with built-in and third-party modules.</span></span>

<span data-ttu-id="658ae-206">For tab completion to work properly in JEA sessions you must include the built-in function `tabexpansion2` in the **VisibleFunctions** list.</span><span class="sxs-lookup"><span data-stu-id="658ae-206">For tab completion to work properly in JEA sessions you must include the built-in function `tabexpansion2` in the **VisibleFunctions** list.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="658ae-207">Place role capabilities in a module</span><span class="sxs-lookup"><span data-stu-id="658ae-207">Place role capabilities in a module</span></span>

<span data-ttu-id="658ae-208">In order for PowerShell to find a role capability file, it must be stored in a **RoleCapabilities** folder in a PowerShell module.</span><span class="sxs-lookup"><span data-stu-id="658ae-208">In order for PowerShell to find a role capability file, it must be stored in a **RoleCapabilities** folder in a PowerShell module.</span></span> <span data-ttu-id="658ae-209">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you shouldn't place it in System32 or a folder where the untrusted, connecting users could modify the files.</span><span class="sxs-lookup"><span data-stu-id="658ae-209">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you shouldn't place it in System32 or a folder where the untrusted, connecting users could modify the files.</span></span> <span data-ttu-id="658ae-210">Below is an example of creating a basic PowerShell script module called **ContosoJEA** in the `$env:ProgramFiles` path.</span><span class="sxs-lookup"><span data-stu-id="658ae-210">Below is an example of creating a basic PowerShell script module called **ContosoJEA** in the `$env:ProgramFiles` path.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest.
# At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="658ae-211">For more information about PowerShell modules, see [Understanding a PowerShell Module](/powershell/scripting/developer/windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="658ae-211">For more information about PowerShell modules, see [Understanding a PowerShell Module](/powershell/scripting/developer/windows-powershell).</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="658ae-212">Updating role capabilities</span><span class="sxs-lookup"><span data-stu-id="658ae-212">Updating role capabilities</span></span>

<span data-ttu-id="658ae-213">You can edit a role capability file to update the settings at any time.</span><span class="sxs-lookup"><span data-stu-id="658ae-213">You can edit a role capability file to update the settings at any time.</span></span> <span data-ttu-id="658ae-214">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span><span class="sxs-lookup"><span data-stu-id="658ae-214">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="658ae-215">This is why controlling access to the role capabilities folder is so important.</span><span class="sxs-lookup"><span data-stu-id="658ae-215">This is why controlling access to the role capabilities folder is so important.</span></span> <span data-ttu-id="658ae-216">Only highly trusted administrators should be allowed to change role capability files.</span><span class="sxs-lookup"><span data-stu-id="658ae-216">Only highly trusted administrators should be allowed to change role capability files.</span></span> <span data-ttu-id="658ae-217">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets that allow them to elevate their privileges.</span><span class="sxs-lookup"><span data-stu-id="658ae-217">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets that allow them to elevate their privileges.</span></span>

<span data-ttu-id="658ae-218">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span><span class="sxs-lookup"><span data-stu-id="658ae-218">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="658ae-219">How role capabilities are merged</span><span class="sxs-lookup"><span data-stu-id="658ae-219">How role capabilities are merged</span></span>

<span data-ttu-id="658ae-220">Users are granted access to all matching role capabilities in the [session configuration file](session-configurations.md) when they enter a JEA session.</span><span class="sxs-lookup"><span data-stu-id="658ae-220">Users are granted access to all matching role capabilities in the [session configuration file](session-configurations.md) when they enter a JEA session.</span></span> <span data-ttu-id="658ae-221">JEA tries to give the user the most permissive set of commands allowed by any of the roles.</span><span class="sxs-lookup"><span data-stu-id="658ae-221">JEA tries to give the user the most permissive set of commands allowed by any of the roles.</span></span>

### <a name="visiblecmdlets-and-visiblefunctions"></a><span data-ttu-id="658ae-222">VisibleCmdlets and VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="658ae-222">VisibleCmdlets and VisibleFunctions</span></span>

<span data-ttu-id="658ae-223">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span><span class="sxs-lookup"><span data-stu-id="658ae-223">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="658ae-224">The rules are as follows:</span><span class="sxs-lookup"><span data-stu-id="658ae-224">The rules are as follows:</span></span>

1. <span data-ttu-id="658ae-225">If a cmdlet is only made visible in one role, it is visible to the user with any applicable parameter constraints.</span><span class="sxs-lookup"><span data-stu-id="658ae-225">If a cmdlet is only made visible in one role, it is visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="658ae-226">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet is visible to the user with those constraints.</span><span class="sxs-lookup"><span data-stu-id="658ae-226">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet is visible to the user with those constraints.</span></span>
3. <span data-ttu-id="658ae-227">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all the parameters defined across every role are visible to the user.</span><span class="sxs-lookup"><span data-stu-id="658ae-227">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all the parameters defined across every role are visible to the user.</span></span>
   <span data-ttu-id="658ae-228">If one role doesn't have constraints on the parameters, all parameters are allowed.</span><span class="sxs-lookup"><span data-stu-id="658ae-228">If one role doesn't have constraints on the parameters, all parameters are allowed.</span></span>
4. <span data-ttu-id="658ae-229">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern is ignored.</span><span class="sxs-lookup"><span data-stu-id="658ae-229">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern is ignored.</span></span>
5. <span data-ttu-id="658ae-230">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets are allowed.</span><span class="sxs-lookup"><span data-stu-id="658ae-230">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets are allowed.</span></span>
6. <span data-ttu-id="658ae-231">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns are allowed.</span><span class="sxs-lookup"><span data-stu-id="658ae-231">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns are allowed.</span></span>
7. <span data-ttu-id="658ae-232">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span><span class="sxs-lookup"><span data-stu-id="658ae-232">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="658ae-233">Below is an example of how roles are merged according to these rules:</span><span class="sxs-lookup"><span data-stu-id="658ae-233">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service
#   is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use
#   ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a><span data-ttu-id="658ae-234">VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="658ae-234">VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess</span></span>

<span data-ttu-id="658ae-235">All other fields in the role capability file are added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span><span class="sxs-lookup"><span data-stu-id="658ae-235">All other fields in the role capability file are added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span> <span data-ttu-id="658ae-236">Any command, alias, provider, or script available in one role capability is available to the JEA user.</span><span class="sxs-lookup"><span data-stu-id="658ae-236">Any command, alias, provider, or script available in one role capability is available to the JEA user.</span></span>

<span data-ttu-id="658ae-237">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another don't allow users unintentional access to system resources.</span><span class="sxs-lookup"><span data-stu-id="658ae-237">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another don't allow users unintentional access to system resources.</span></span>
<span data-ttu-id="658ae-238">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span><span class="sxs-lookup"><span data-stu-id="658ae-238">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span> <span data-ttu-id="658ae-239">Additional information about identifying users' effective permissions can be found in the [auditing JEA](audit-and-report.md) article.</span><span class="sxs-lookup"><span data-stu-id="658ae-239">Additional information about identifying users' effective permissions can be found in the [auditing JEA](audit-and-report.md) article.</span></span>

## <a name="next-steps"></a><span data-ttu-id="658ae-240">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="658ae-240">Next steps</span></span>

[<span data-ttu-id="658ae-241">Create a session configuration file</span><span class="sxs-lookup"><span data-stu-id="658ae-241">Create a session configuration file</span></span>](session-configurations.md)
