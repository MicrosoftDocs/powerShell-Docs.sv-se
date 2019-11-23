---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Göra det andra hoppet i PowerShell-fjärrkommunikation
ms.openlocfilehash: 567d75009f7d53e9e95e5480b275ec3991cfb9f5
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417627"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="0c6ee-103">Göra det andra hoppet i PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="0c6ee-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="0c6ee-104">The "second hop problem" refers to a situation like the following:</span><span class="sxs-lookup"><span data-stu-id="0c6ee-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="0c6ee-105">You are logged in to _ServerA_.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="0c6ee-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="0c6ee-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="0c6ee-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="0c6ee-109">There are several ways to address this problem.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-109">There are several ways to address this problem.</span></span> <span data-ttu-id="0c6ee-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="0c6ee-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="0c6ee-111">CredSSP</span></span>

<span data-ttu-id="0c6ee-112">You can use the [Credential Security Support Provider (CredSSP)](/windows/win32/secauthn/credential-security-support-provider) for authentication.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-112">You can use the [Credential Security Support Provider (CredSSP)](/windows/win32/secauthn/credential-security-support-provider) for authentication.</span></span> <span data-ttu-id="0c6ee-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="0c6ee-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="0c6ee-115">CredSSP is disabled by default on both client and server computers.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="0c6ee-116">You should enable CredSSP only in the most trusted environments.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="0c6ee-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="0c6ee-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="0c6ee-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="0c6ee-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="0c6ee-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="0c6ee-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="0c6ee-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="0c6ee-121">Fördelar</span><span class="sxs-lookup"><span data-stu-id="0c6ee-121">Pros</span></span>

- <span data-ttu-id="0c6ee-122">It works for all servers with Windows Server 2008 or later.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="0c6ee-123">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="0c6ee-123">Cons</span></span>

- <span data-ttu-id="0c6ee-124">Has security vulnerabilities.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="0c6ee-125">Requires configuration of both client and server roles.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="0c6ee-126">Kerberos delegation (unconstrained)</span><span class="sxs-lookup"><span data-stu-id="0c6ee-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="0c6ee-127">You can also used Kerberos unconstrained delegation to make the second hop.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="0c6ee-128">However, this method provides no control of where delegated credentials are used.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="0c6ee-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="0c6ee-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="0c6ee-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="0c6ee-131">Fördelar</span><span class="sxs-lookup"><span data-stu-id="0c6ee-131">Pros</span></span>

- <span data-ttu-id="0c6ee-132">Requires no special coding.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="0c6ee-133">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="0c6ee-133">Cons</span></span>

- <span data-ttu-id="0c6ee-134">Does not support the second hop for WinRM.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="0c6ee-135">Provides no control over where credentials are used, creating a security vulnerability.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="0c6ee-136">Kerberos constrained delegation</span><span class="sxs-lookup"><span data-stu-id="0c6ee-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="0c6ee-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="0c6ee-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

> [!NOTE]
> <span data-ttu-id="0c6ee-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="0c6ee-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="0c6ee-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="0c6ee-141">Fördelar</span><span class="sxs-lookup"><span data-stu-id="0c6ee-141">Pros</span></span>

- <span data-ttu-id="0c6ee-142">Requires no special coding</span><span class="sxs-lookup"><span data-stu-id="0c6ee-142">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="0c6ee-143">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="0c6ee-143">Cons</span></span>

- <span data-ttu-id="0c6ee-144">Does not support the second hop for WinRM.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-144">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="0c6ee-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="0c6ee-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="0c6ee-146">Limited to one domain.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-146">Limited to one domain.</span></span> <span data-ttu-id="0c6ee-147">Cannot cross domains or forests.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-147">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="0c6ee-148">Requires rights to update objects and Service Principal Names (SPNs).</span><span class="sxs-lookup"><span data-stu-id="0c6ee-148">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="0c6ee-149">Resource-based Kerberos constrained delegation</span><span class="sxs-lookup"><span data-stu-id="0c6ee-149">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="0c6ee-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="0c6ee-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="0c6ee-152">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-152">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="0c6ee-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="0c6ee-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="0c6ee-154">Fördelar</span><span class="sxs-lookup"><span data-stu-id="0c6ee-154">Pros</span></span>

- <span data-ttu-id="0c6ee-155">Credentials are not stored.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-155">Credentials are not stored.</span></span>
- <span data-ttu-id="0c6ee-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="0c6ee-157">No special domain access is required.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-157">No special domain access is required.</span></span>
- <span data-ttu-id="0c6ee-158">Works across domains and forests.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-158">Works across domains and forests.</span></span>
- <span data-ttu-id="0c6ee-159">PowerShell code.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-159">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="0c6ee-160">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="0c6ee-160">Cons</span></span>

- <span data-ttu-id="0c6ee-161">Requires Windows Server 2012 or later.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-161">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="0c6ee-162">Does not support the second hop for WinRM.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-162">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="0c6ee-163">Requires rights to update objects and Service Principal Names (SPNs).</span><span class="sxs-lookup"><span data-stu-id="0c6ee-163">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="0c6ee-164">Exempel</span><span class="sxs-lookup"><span data-stu-id="0c6ee-164">Example</span></span>

<span data-ttu-id="0c6ee-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="0c6ee-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="0c6ee-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span><span class="sxs-lookup"><span data-stu-id="0c6ee-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="0c6ee-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span><span class="sxs-lookup"><span data-stu-id="0c6ee-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="0c6ee-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span><span class="sxs-lookup"><span data-stu-id="0c6ee-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="0c6ee-170">Now let's set up the variables we'll use to represent the servers:</span><span class="sxs-lookup"><span data-stu-id="0c6ee-170">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="0c6ee-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="0c6ee-172">You can see this by looking at the **StartName** property of the `winrm` service:</span><span class="sxs-lookup"><span data-stu-id="0c6ee-172">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="0c6ee-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="0c6ee-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="0c6ee-174">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied access attempts (negative cache) for 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-174">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="0c6ee-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span><span class="sxs-lookup"><span data-stu-id="0c6ee-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="0c6ee-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="0c6ee-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="0c6ee-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

<span data-ttu-id="0c6ee-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="0c6ee-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="0c6ee-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="0c6ee-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span><span class="sxs-lookup"><span data-stu-id="0c6ee-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

<span data-ttu-id="0c6ee-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span><span class="sxs-lookup"><span data-stu-id="0c6ee-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="0c6ee-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span><span class="sxs-lookup"><span data-stu-id="0c6ee-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="0c6ee-183">Information on resource-based Kerberos constrained delegation</span><span class="sxs-lookup"><span data-stu-id="0c6ee-183">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="0c6ee-184">What's New in Kerberos Authentication</span><span class="sxs-lookup"><span data-stu-id="0c6ee-184">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="0c6ee-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span><span class="sxs-lookup"><span data-stu-id="0c6ee-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="0c6ee-186">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span><span class="sxs-lookup"><span data-stu-id="0c6ee-186">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="0c6ee-187">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span><span class="sxs-lookup"><span data-stu-id="0c6ee-187">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](https://aka.ms/kcdpaper)
- <span data-ttu-id="0c6ee-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405)</span><span class="sxs-lookup"><span data-stu-id="0c6ee-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405)</span></span>
- <span data-ttu-id="0c6ee-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a)</span><span class="sxs-lookup"><span data-stu-id="0c6ee-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a)</span></span>
- [<span data-ttu-id="0c6ee-190">Resource Based Kerberos Constrained Delegation</span><span class="sxs-lookup"><span data-stu-id="0c6ee-190">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="0c6ee-191">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span><span class="sxs-lookup"><span data-stu-id="0c6ee-191">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="0c6ee-192">PSSessionConfiguration using RunAs</span><span class="sxs-lookup"><span data-stu-id="0c6ee-192">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="0c6ee-193">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-193">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="0c6ee-194">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="0c6ee-194">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="0c6ee-195">Fördelar</span><span class="sxs-lookup"><span data-stu-id="0c6ee-195">Pros</span></span>

- <span data-ttu-id="0c6ee-196">Works with any server with WMF 3.0 or later.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-196">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="0c6ee-197">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="0c6ee-197">Cons</span></span>

- <span data-ttu-id="0c6ee-198">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="0c6ee-198">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="0c6ee-199">Requires password maintenance when using a domain **RunAs** account</span><span class="sxs-lookup"><span data-stu-id="0c6ee-199">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="0c6ee-200">JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="0c6ee-200">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="0c6ee-201">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-201">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="0c6ee-202">It can be used to solve the second hop problem.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-202">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="0c6ee-203">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="0c6ee-203">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="0c6ee-204">Fördelar</span><span class="sxs-lookup"><span data-stu-id="0c6ee-204">Pros</span></span>

- <span data-ttu-id="0c6ee-205">No password maintenance when using a virtual account.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-205">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="0c6ee-206">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="0c6ee-206">Cons</span></span>

- <span data-ttu-id="0c6ee-207">Requires WMF 5.0 or later.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-207">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="0c6ee-208">Requires configuration on every intermediate server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="0c6ee-208">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="0c6ee-209">Pass credentials inside an Invoke-Command script block</span><span class="sxs-lookup"><span data-stu-id="0c6ee-209">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="0c6ee-210">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-210">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="0c6ee-211">Fördelar</span><span class="sxs-lookup"><span data-stu-id="0c6ee-211">Pros</span></span>

- <span data-ttu-id="0c6ee-212">Does not require special server configuration.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-212">Does not require special server configuration.</span></span>
- <span data-ttu-id="0c6ee-213">Works on any server running WMF 2.0 or later.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-213">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="0c6ee-214">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="0c6ee-214">Cons</span></span>

- <span data-ttu-id="0c6ee-215">Requires an awkward code technique.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-215">Requires an awkward code technique.</span></span>
- <span data-ttu-id="0c6ee-216">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span><span class="sxs-lookup"><span data-stu-id="0c6ee-216">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="0c6ee-217">Exempel</span><span class="sxs-lookup"><span data-stu-id="0c6ee-217">Example</span></span>

<span data-ttu-id="0c6ee-218">The following example shows how to pass credentials in an **Invoke-Command** script block:</span><span class="sxs-lookup"><span data-stu-id="0c6ee-218">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="0c6ee-219">Se även</span><span class="sxs-lookup"><span data-stu-id="0c6ee-219">See also</span></span>

[<span data-ttu-id="0c6ee-220">Säkerhetsöverväganden för PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="0c6ee-220">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)
