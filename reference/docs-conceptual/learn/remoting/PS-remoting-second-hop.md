---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Göra det andra hoppet i PowerShell-fjärrkommunikation
ms.openlocfilehash: 1b6e5ad53346324adc7be2d013e154c8600afa4f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086348"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="17cc5-103">Göra det andra hoppet i PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="17cc5-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="17cc5-104">”Andra hopp problemet” avser en situation som liknar följande:</span><span class="sxs-lookup"><span data-stu-id="17cc5-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="17cc5-105">Du är inloggad _cypress_.</span><span class="sxs-lookup"><span data-stu-id="17cc5-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="17cc5-106">Från _cypress_, du startar en fjärrsession PowerShell till att ansluta till _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="17cc5-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="17cc5-107">Ett kommando som du kör på _ServerB_ via PowerShell-fjärrkommunikation session försöker få åtkomst till en resurs på _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="17cc5-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="17cc5-108">Åtkomst till resursen på _ServerC_ nekas, eftersom de autentiseringsuppgifter som du använde för att skapa PowerShell-fjärrkommunikation sessionen inte skickas från _ServerB_ till _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="17cc5-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="17cc5-109">Det finns flera sätt att åtgärda problemet.</span><span class="sxs-lookup"><span data-stu-id="17cc5-109">There are several ways to address this problem.</span></span> <span data-ttu-id="17cc5-110">I det här avsnittet ska vi titta på flera av de mest populära lösningarna på problemet för andra hopp.</span><span class="sxs-lookup"><span data-stu-id="17cc5-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="17cc5-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="17cc5-111">CredSSP</span></span>

<span data-ttu-id="17cc5-112">Du kan använda den [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) för autentisering.</span><span class="sxs-lookup"><span data-stu-id="17cc5-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="17cc5-113">CredSSP cachelagrar autentiseringsuppgifter på fjärrservern (_ServerB_), så använder det öppnar du upp till stöldattacker av autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="17cc5-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="17cc5-114">Om fjärrdatorn komprometteras har angriparen tillgång till användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="17cc5-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="17cc5-115">CredSSP är inaktiverad som standard på både klienten och servern datorer.</span><span class="sxs-lookup"><span data-stu-id="17cc5-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="17cc5-116">Endast i de mest tillförlitliga miljöerna bör du aktivera CredSSP.</span><span class="sxs-lookup"><span data-stu-id="17cc5-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="17cc5-117">Till exempel en domänadministratör ansluter till en domänkontrollant, eftersom domänkontrollanten är betrodda.</span><span class="sxs-lookup"><span data-stu-id="17cc5-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="17cc5-118">Mer information om säkerhetsfrågor när du använder CredSSP för PowerShell-fjärrkommunikation finns [oavsiktlig Sabotage: Håll CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="17cc5-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="17cc5-119">Mer information om stöldattacker av autentiseringsuppgifter finns i [Mitigating Pass-the-Hash (PtH)-attacker och annan stöld](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="17cc5-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="17cc5-120">Ett exempel på hur du aktiverar och använder CredSSP för PowerShell-fjärrkommunikation finns i [med CredSSP för att lösa problemet andra hopp](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="17cc5-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="17cc5-121">Experter</span><span class="sxs-lookup"><span data-stu-id="17cc5-121">Pros</span></span>

- <span data-ttu-id="17cc5-122">Den fungerar för alla servrar med Windows Server 2008 eller senare.</span><span class="sxs-lookup"><span data-stu-id="17cc5-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="17cc5-123">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="17cc5-123">Cons</span></span>

- <span data-ttu-id="17cc5-124">Har säkerhetsrisker.</span><span class="sxs-lookup"><span data-stu-id="17cc5-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="17cc5-125">Kräver konfiguration av både klient och server-roller.</span><span class="sxs-lookup"><span data-stu-id="17cc5-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="17cc5-126">Kerberos-delegering (obegränsad)</span><span class="sxs-lookup"><span data-stu-id="17cc5-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="17cc5-127">Du kan också använda obegränsad Kerberos-delegering för att göra det andra hoppet.</span><span class="sxs-lookup"><span data-stu-id="17cc5-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="17cc5-128">Den här metoden ger dock ingen kontroll över där delegerade autentiseringsuppgifter används.</span><span class="sxs-lookup"><span data-stu-id="17cc5-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="17cc5-129">**Obs:** Active Directory-konton som har den **kontot är känsligt och kan inte delegeras** egenskapsuppsättning kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="17cc5-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="17cc5-130">Mer information finns i [Security fokus: Analys ”kontot är känsligt och kan inte delegeras” för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [Kerberos-autentisering verktyg och inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="17cc5-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="17cc5-131">Experter</span><span class="sxs-lookup"><span data-stu-id="17cc5-131">Pros</span></span>

- <span data-ttu-id="17cc5-132">Kräver ingen särskild kodning.</span><span class="sxs-lookup"><span data-stu-id="17cc5-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="17cc5-133">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="17cc5-133">Cons</span></span>

- <span data-ttu-id="17cc5-134">Stöder inte det andra hoppet för WinRM.</span><span class="sxs-lookup"><span data-stu-id="17cc5-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="17cc5-135">Innehåller ingen kontroll över där autentiseringsuppgifter används, skapar en säkerhetsrisk.</span><span class="sxs-lookup"><span data-stu-id="17cc5-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="17cc5-136">Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="17cc5-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="17cc5-137">Du kan använda äldre begränsad delegering (inte Resursbaserad) för att göra det andra hoppet.</span><span class="sxs-lookup"><span data-stu-id="17cc5-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="17cc5-138">Konfigurera Kerberos-begränsad delegering med alternativet ”Använd valfritt autentiseringsprotokoll” så att protokollövergång.</span><span class="sxs-lookup"><span data-stu-id="17cc5-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

> [!NOTE]
> <span data-ttu-id="17cc5-139">Active Directory-konton som har den **kontot är känsligt och kan inte delegeras** egenskapsuppsättning kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="17cc5-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="17cc5-140">Mer information finns i [Security fokus: Analys ”kontot är känsligt och kan inte delegeras” för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [Kerberos-autentisering verktyg och inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="17cc5-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="17cc5-141">Experter</span><span class="sxs-lookup"><span data-stu-id="17cc5-141">Pros</span></span>

- <span data-ttu-id="17cc5-142">Kräver ingen särskild kodning</span><span class="sxs-lookup"><span data-stu-id="17cc5-142">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="17cc5-143">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="17cc5-143">Cons</span></span>

- <span data-ttu-id="17cc5-144">Stöder inte det andra hoppet för WinRM.</span><span class="sxs-lookup"><span data-stu-id="17cc5-144">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="17cc5-145">Måste konfigureras på Active Directory-objekt på fjärrservern (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="17cc5-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="17cc5-146">Begränsad till en domän.</span><span class="sxs-lookup"><span data-stu-id="17cc5-146">Limited to one domain.</span></span> <span data-ttu-id="17cc5-147">Det går inte att mellan domäner eller skogar.</span><span class="sxs-lookup"><span data-stu-id="17cc5-147">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="17cc5-148">Kräver behörighet att uppdatera objekt och tjänsthuvudnamn (SPN).</span><span class="sxs-lookup"><span data-stu-id="17cc5-148">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="17cc5-149">Resursbaserade Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="17cc5-149">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="17cc5-150">Använder resursbaserade Kerberos-begränsad delegering (introducerades i Windows Server 2012) måste du konfigurera delegering av autentiseringsuppgifter på server-objekt där resurserna finns.</span><span class="sxs-lookup"><span data-stu-id="17cc5-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="17cc5-151">I det andra hopp scenariot som beskrivs ovan, konfigurerar du _ServerC_ ange från där du ska ta emot delegerade autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="17cc5-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="17cc5-152">**Obs:** Active Directory-konton som har den **kontot är känsligt och kan inte delegeras** egenskapsuppsättning kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="17cc5-152">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="17cc5-153">Mer information finns i [Security fokus: Analys ”kontot är känsligt och kan inte delegeras” för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [Kerberos-autentisering verktyg och inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="17cc5-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="17cc5-154">Experter</span><span class="sxs-lookup"><span data-stu-id="17cc5-154">Pros</span></span>

- <span data-ttu-id="17cc5-155">Autentiseringsuppgifterna har inte sparats.</span><span class="sxs-lookup"><span data-stu-id="17cc5-155">Credentials are not stored.</span></span>
- <span data-ttu-id="17cc5-156">Relativt enkelt att konfigurera med hjälp av PowerShell-cmdlets – ingen särskild kodning krävs.</span><span class="sxs-lookup"><span data-stu-id="17cc5-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="17cc5-157">Ingen åtkomst till särskilda domänen krävs.</span><span class="sxs-lookup"><span data-stu-id="17cc5-157">No special domain access is required.</span></span>
- <span data-ttu-id="17cc5-158">Arbeta över domäner och skogar.</span><span class="sxs-lookup"><span data-stu-id="17cc5-158">Works across domains and forests.</span></span>
- <span data-ttu-id="17cc5-159">PowerShell-kod.</span><span class="sxs-lookup"><span data-stu-id="17cc5-159">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="17cc5-160">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="17cc5-160">Cons</span></span>

- <span data-ttu-id="17cc5-161">Kräver Windows Server 2012 eller senare.</span><span class="sxs-lookup"><span data-stu-id="17cc5-161">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="17cc5-162">Stöder inte det andra hoppet för WinRM.</span><span class="sxs-lookup"><span data-stu-id="17cc5-162">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="17cc5-163">Kräver behörighet att uppdatera objekt och tjänsthuvudnamn (SPN).</span><span class="sxs-lookup"><span data-stu-id="17cc5-163">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="17cc5-164">Exempel</span><span class="sxs-lookup"><span data-stu-id="17cc5-164">Example</span></span>

<span data-ttu-id="17cc5-165">Låt oss titta på ett exempel som konfigurerar resursen begränsad delegering som baseras på PowerShell _ServerC_ att tillåta delegerade autentiseringsuppgifter från en _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="17cc5-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="17cc5-166">Det här exemplet förutsätts att alla servrar som kör Windows Server 2012 eller senare, och att det finns minst en domänkontrollant för Windows Server 2012 varje domän till där någon av servrarna tillhör.</span><span class="sxs-lookup"><span data-stu-id="17cc5-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="17cc5-167">Innan du kan konfigurera begränsad delegering, måste du lägga till den `RSAT-AD-PowerShell` för att installera Active Directory PowerShell-modulen och importera sedan modulen till sessionen:</span><span class="sxs-lookup"><span data-stu-id="17cc5-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="17cc5-168">Flera tillgängliga cmdlet: ar har nu en **PrincipalsAllowedToDelegateToAccount** parameter:</span><span class="sxs-lookup"><span data-stu-id="17cc5-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

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

<span data-ttu-id="17cc5-169">Den **PrincipalsAllowedToDelegateToAccount** parametern anger Active Directory-objektattribut **msDS-AllowedToActOnBehalfOfOtherIdentity**, som innehåller en åtkomstkontrollista (ACL) som Anger vilka konton som har behörighet att delegera autentiseringsuppgifter till det associerade kontot (i vårt exempel, kommer den att datorkontot för _Server_).</span><span class="sxs-lookup"><span data-stu-id="17cc5-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="17cc5-170">Nu ska vi konfigurera de variabler som vi använder för att representera servrar:</span><span class="sxs-lookup"><span data-stu-id="17cc5-170">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="17cc5-171">WinRM (och därför PowerShell-fjärrkommunikation) körs som datorkontot som standard.</span><span class="sxs-lookup"><span data-stu-id="17cc5-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="17cc5-172">Du kan se detta genom att titta på den **Referensdimensionerna** egenskapen för den `winrm` service:</span><span class="sxs-lookup"><span data-stu-id="17cc5-172">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="17cc5-173">För _ServerC_ att tillåta delegering från en PowerShell-fjärrkommunikation-session på _ServerB_, så vi beviljas åtkomst genom att ange den **PrincipalsAllowedToDelegateToAccount** parametern på _ServerC_ till datorobjekt _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="17cc5-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="17cc5-174">Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) cacheminnen nekas åtkomstförsök (negativ cache) i 15 minuter.</span><span class="sxs-lookup"><span data-stu-id="17cc5-174">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="17cc5-175">Om _ServerB_ har tidigare försökte komma åt _ServerC_, måste du rensa cacheminnet på _ServerB_ genom att aktivera följande kommando:</span><span class="sxs-lookup"><span data-stu-id="17cc5-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="17cc5-176">Du kan också starta om datorn eller vänta minst 15 minuter för att rensa cacheminnet.</span><span class="sxs-lookup"><span data-stu-id="17cc5-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="17cc5-177">Efter att rensa cacheminnet, kan du köra kod från _cypress_ via _ServerB_ till _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="17cc5-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="17cc5-178">I det här exemplet på `$using` variabeln används för att göra den `$ServerC` variabeln som är synliga för _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="17cc5-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="17cc5-179">Mer information om den `$using` variabel, se [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="17cc5-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="17cc5-180">Gör att flera servrar att delegera autentiseringsuppgifter för att _ServerC_, ange värdet för den **PrincipalsAllowedToDelegateToAccount** parametern på _ServerC_ till en matris:</span><span class="sxs-lookup"><span data-stu-id="17cc5-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="17cc5-181">Om du vill göra det andra hoppet i flera domäner lägger du till fullständigt kvalificerade domännamnet (FQDN) på domänkontrollanten för domänen som _ServerB_ tillhör:</span><span class="sxs-lookup"><span data-stu-id="17cc5-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="17cc5-182">Om du vill ta bort möjligheten att delegera ServerC autentiseringsuppgifter, ange värdet för den **PrincipalsAllowedToDelegateToAccount** parametern på _ServerC_ till `$null`:</span><span class="sxs-lookup"><span data-stu-id="17cc5-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="17cc5-183">Information om resursbaserade Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="17cc5-183">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="17cc5-184">Vad är nytt i Kerberos-autentisering</span><span class="sxs-lookup"><span data-stu-id="17cc5-184">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="17cc5-185">Hur Windows Server 2012 övergångar enkelt Kerberos-begränsad delegering, del 1</span><span class="sxs-lookup"><span data-stu-id="17cc5-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="17cc5-186">Hur Windows Server 2012 övergångar enkelt Kerberos-begränsad delegering, del 2</span><span class="sxs-lookup"><span data-stu-id="17cc5-186">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="17cc5-187">Förstå Kerberos-begränsad delegering för Azure Active Directory Application Proxy-distributioner med integrerad Windows-autentisering</span><span class="sxs-lookup"><span data-stu-id="17cc5-187">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](https://aka.ms/kcdpaper)
- <span data-ttu-id="17cc5-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span><span class="sxs-lookup"><span data-stu-id="17cc5-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span></span>
- <span data-ttu-id="17cc5-189">[[MS-SFU]: Tillägg för Kerberos-protokollet: Tjänst för användare och begränsad delegering protokollet 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span><span class="sxs-lookup"><span data-stu-id="17cc5-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="17cc5-190">Resursen baserat Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="17cc5-190">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="17cc5-191">Fjärradministration utan begränsad delegering med hjälp av PrincipalsAllowedToDelegateToAccount</span><span class="sxs-lookup"><span data-stu-id="17cc5-191">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="17cc5-192">PSSessionConfiguration med RunAs</span><span class="sxs-lookup"><span data-stu-id="17cc5-192">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="17cc5-193">Du kan skapa en sessionskonfiguration på _ServerB_ och Ställ in dess **RunAsCredential** parametern.</span><span class="sxs-lookup"><span data-stu-id="17cc5-193">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="17cc5-194">Information om hur du använder PSSessionConfiguration och RunAs lösa andra hopp problemet finns i [en annan lösning till Multi-hop PowerShell-fjärrkommunikation](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="17cc5-194">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="17cc5-195">Experter</span><span class="sxs-lookup"><span data-stu-id="17cc5-195">Pros</span></span>

- <span data-ttu-id="17cc5-196">Fungerar med servrar med WMF 3.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="17cc5-196">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="17cc5-197">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="17cc5-197">Cons</span></span>

- <span data-ttu-id="17cc5-198">Kräver konfiguration av **PSSessionConfiguration** och **RunAs** på varje mellanliggande server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="17cc5-198">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="17cc5-199">Kräver lösenord Underhåll när du använder en domän **RunAs** konto</span><span class="sxs-lookup"><span data-stu-id="17cc5-199">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="17cc5-200">JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="17cc5-200">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="17cc5-201">JEA kan du begränsa vilka kommandon som en administratör kan köras under en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="17cc5-201">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="17cc5-202">Det kan användas för att lösa problemet med andra hopp.</span><span class="sxs-lookup"><span data-stu-id="17cc5-202">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="17cc5-203">Läs om hur JEA [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="17cc5-203">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="17cc5-204">Experter</span><span class="sxs-lookup"><span data-stu-id="17cc5-204">Pros</span></span>

- <span data-ttu-id="17cc5-205">Inget lösenord Underhåll när du använder ett virtuellt konto.</span><span class="sxs-lookup"><span data-stu-id="17cc5-205">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="17cc5-206">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="17cc5-206">Cons</span></span>

- <span data-ttu-id="17cc5-207">Kräver WMF 5.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="17cc5-207">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="17cc5-208">Kräver konfiguration på varje mellanliggande server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="17cc5-208">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="17cc5-209">Skicka autentiseringsuppgifter inuti en Invoke-Command-skriptblock</span><span class="sxs-lookup"><span data-stu-id="17cc5-209">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="17cc5-210">Du kan skicka autentiseringsuppgifter i den **ScriptBlock** parameter för ett anrop till den [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="17cc5-210">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="17cc5-211">Experter</span><span class="sxs-lookup"><span data-stu-id="17cc5-211">Pros</span></span>

- <span data-ttu-id="17cc5-212">Kräver inte särskild serverkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="17cc5-212">Does not require special server configuration.</span></span>
- <span data-ttu-id="17cc5-213">Fungerar på en server som kör WMF 2.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="17cc5-213">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="17cc5-214">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="17cc5-214">Cons</span></span>

- <span data-ttu-id="17cc5-215">Kräver en olämpliga kod-teknik.</span><span class="sxs-lookup"><span data-stu-id="17cc5-215">Requires an awkward code technique.</span></span>
- <span data-ttu-id="17cc5-216">Om kör WMF 2.0, kräver olika syntax för att skicka argument till en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="17cc5-216">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="17cc5-217">Exempel</span><span class="sxs-lookup"><span data-stu-id="17cc5-217">Example</span></span>

<span data-ttu-id="17cc5-218">I följande exempel visas hur du skickar autentiseringsuppgifter i en **Invoke-Command** skriptblock:</span><span class="sxs-lookup"><span data-stu-id="17cc5-218">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="17cc5-219">Se även</span><span class="sxs-lookup"><span data-stu-id="17cc5-219">See also</span></span>

[<span data-ttu-id="17cc5-220">Säkerhetsöverväganden för PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="17cc5-220">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)
