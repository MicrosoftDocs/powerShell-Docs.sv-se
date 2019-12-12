---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Göra det andra hoppet i PowerShell-fjärrkommunikation
ms.openlocfilehash: 567d75009f7d53e9e95e5480b275ec3991cfb9f5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417627"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="88086-103">Göra det andra hoppet i PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="88086-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="88086-104">"Andra hopp problemet" syftar på en situation som följande:</span><span class="sxs-lookup"><span data-stu-id="88086-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="88086-105">Du är inloggad på _reserverad_.</span><span class="sxs-lookup"><span data-stu-id="88086-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="88086-106">Frånsäkerhetsstartar du en fjärran sluten PowerShell-session för att ansluta till _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="88086-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="88086-107">Ett kommando som du kör på _ServerB_ via din PowerShell-fjärrsession försöker få åtkomst till en resurs på _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="88086-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="88086-108">Åtkomst till resursen på _ServerC_ nekas eftersom de autentiseringsuppgifter som du använde för att skapa PowerShell-fjärrsessionen inte skickas från _ServerB_ till _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="88086-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="88086-109">Det finns flera sätt att åtgärda problemet.</span><span class="sxs-lookup"><span data-stu-id="88086-109">There are several ways to address this problem.</span></span> <span data-ttu-id="88086-110">I det här avsnittet ska vi titta på flera av de mest populära lösningarna för det andra hopp problemet.</span><span class="sxs-lookup"><span data-stu-id="88086-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="88086-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="88086-111">CredSSP</span></span>

<span data-ttu-id="88086-112">Du kan använda [CredSSP (Credential Security Support Provider)](/windows/win32/secauthn/credential-security-support-provider) för autentisering.</span><span class="sxs-lookup"><span data-stu-id="88086-112">You can use the [Credential Security Support Provider (CredSSP)](/windows/win32/secauthn/credential-security-support-provider) for authentication.</span></span> <span data-ttu-id="88086-113">CredSSP cachelagrar autentiseringsuppgifter på fjärrservern (_ServerB_) så att du kan använda den för att öppna autentiseringsuppgifter för stöld av autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="88086-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="88086-114">Om fjärrdatorn komprometteras har angriparen till gång till användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="88086-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="88086-115">CredSSP är inaktiverat som standard på både klient-och serverdatorer.</span><span class="sxs-lookup"><span data-stu-id="88086-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="88086-116">Du bör endast aktivera CredSSP i de mest betrodda miljöerna.</span><span class="sxs-lookup"><span data-stu-id="88086-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="88086-117">Till exempel en domän administratör som ansluter till en domänkontrollant eftersom domänkontrollanten är hög betrodd.</span><span class="sxs-lookup"><span data-stu-id="88086-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="88086-118">Mer information om säkerhets problem när du använder CredSSP för PowerShell-fjärrkommunikation finns i avsnittet [om oavsiktlig sabotage: Tänk på CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="88086-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="88086-119">Mer information om stöld av autentiseringsuppgifter finns i [minimera pass-The-hash-attacker (PTH) och annan stöld av autentiseringsuppgifter](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="88086-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="88086-120">Ett exempel på hur du aktiverar och använder CredSSP för PowerShell-fjärrkommunikation finns i [använda CredSSP för att lösa det andra hopp problemet](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="88086-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="88086-121">Fördelar</span><span class="sxs-lookup"><span data-stu-id="88086-121">Pros</span></span>

- <span data-ttu-id="88086-122">Det fungerar för alla servrar med Windows Server 2008 eller senare.</span><span class="sxs-lookup"><span data-stu-id="88086-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="88086-123">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="88086-123">Cons</span></span>

- <span data-ttu-id="88086-124">Säkerhets problem.</span><span class="sxs-lookup"><span data-stu-id="88086-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="88086-125">Kräver konfiguration av både klient-och Server roller.</span><span class="sxs-lookup"><span data-stu-id="88086-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="88086-126">Kerberos-delegering (obegränsad)</span><span class="sxs-lookup"><span data-stu-id="88086-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="88086-127">Du kan också använda Kerberos-obegränsad delegering för att göra det andra hoppet.</span><span class="sxs-lookup"><span data-stu-id="88086-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="88086-128">Den här metoden ger dock ingen kontroll över var delegerade autentiseringsuppgifter används.</span><span class="sxs-lookup"><span data-stu-id="88086-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="88086-129">**Obs:** Active Directory konton som har **kontot känsligt och det inte går** att delegera egenskaps uppsättningen kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="88086-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="88086-130">Mer information finns i [säkerhets fokus: analys av kontot är känsligt och kan inte delegeras för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [verktyg och inställningar för Kerberos-autentisering](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="88086-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="88086-131">Fördelar</span><span class="sxs-lookup"><span data-stu-id="88086-131">Pros</span></span>

- <span data-ttu-id="88086-132">Kräver ingen särskild kodning.</span><span class="sxs-lookup"><span data-stu-id="88086-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="88086-133">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="88086-133">Cons</span></span>

- <span data-ttu-id="88086-134">Har inte stöd för det andra hoppet för WinRM.</span><span class="sxs-lookup"><span data-stu-id="88086-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="88086-135">Ger ingen kontroll över var autentiseringsuppgifter används, vilket skapar en säkerhets risk.</span><span class="sxs-lookup"><span data-stu-id="88086-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="88086-136">Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="88086-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="88086-137">Du kan använda en äldre begränsad delegering (inte resurs baserad) för att göra det andra hoppet.</span><span class="sxs-lookup"><span data-stu-id="88086-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="88086-138">Konfigurera Kerberos-begränsad delegering med alternativet "Använd valfria autentiseringsprotokoll" för att tillåta protokoll över gång.</span><span class="sxs-lookup"><span data-stu-id="88086-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

> [!NOTE]
> <span data-ttu-id="88086-139">Active Directory konton som har **kontot känsligt och det inte går** att delegera egenskaps uppsättningen kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="88086-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="88086-140">Mer information finns i [säkerhets fokus: analys av kontot är känsligt och kan inte delegeras för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [verktyg och inställningar för Kerberos-autentisering](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="88086-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="88086-141">Fördelar</span><span class="sxs-lookup"><span data-stu-id="88086-141">Pros</span></span>

- <span data-ttu-id="88086-142">Kräver ingen särskild kodning</span><span class="sxs-lookup"><span data-stu-id="88086-142">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="88086-143">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="88086-143">Cons</span></span>

- <span data-ttu-id="88086-144">Har inte stöd för det andra hoppet för WinRM.</span><span class="sxs-lookup"><span data-stu-id="88086-144">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="88086-145">Måste konfigureras på Active Directory-objektet på fjärrservern (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="88086-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="88086-146">Begränsad till en domän.</span><span class="sxs-lookup"><span data-stu-id="88086-146">Limited to one domain.</span></span> <span data-ttu-id="88086-147">Det går inte att korsa domäner eller skogar.</span><span class="sxs-lookup"><span data-stu-id="88086-147">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="88086-148">Kräver behörighet att uppdatera objekt och SPN-namn (Service Principal Names).</span><span class="sxs-lookup"><span data-stu-id="88086-148">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="88086-149">Resurs-baserad Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="88086-149">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="88086-150">Med hjälp av resurs baserad Kerberos-begränsad delegering (som introducerades i Windows Server 2012) konfigurerar du delegering av autentiseringsuppgifter på det Server objekt där resurserna finns.</span><span class="sxs-lookup"><span data-stu-id="88086-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="88086-151">I det andra hopp scenariot som beskrivs ovan konfigurerar du _ServerC_ för att ange från vilken den ska acceptera delegerade autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="88086-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="88086-152">**Obs:** Active Directory konton som har **kontot känsligt och det inte går** att delegera egenskaps uppsättningen kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="88086-152">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="88086-153">Mer information finns i [säkerhets fokus: analys av kontot är känsligt och kan inte delegeras för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [verktyg och inställningar för Kerberos-autentisering](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="88086-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="88086-154">Fördelar</span><span class="sxs-lookup"><span data-stu-id="88086-154">Pros</span></span>

- <span data-ttu-id="88086-155">Autentiseringsuppgifterna lagras inte.</span><span class="sxs-lookup"><span data-stu-id="88086-155">Credentials are not stored.</span></span>
- <span data-ttu-id="88086-156">Relativt enkelt att konfigurera med hjälp av PowerShell-cmdletar – ingen särskild kod krävs.</span><span class="sxs-lookup"><span data-stu-id="88086-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="88086-157">Ingen särskild domän åtkomst krävs.</span><span class="sxs-lookup"><span data-stu-id="88086-157">No special domain access is required.</span></span>
- <span data-ttu-id="88086-158">Fungerar över domäner och skogar.</span><span class="sxs-lookup"><span data-stu-id="88086-158">Works across domains and forests.</span></span>
- <span data-ttu-id="88086-159">PowerShell-kod.</span><span class="sxs-lookup"><span data-stu-id="88086-159">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="88086-160">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="88086-160">Cons</span></span>

- <span data-ttu-id="88086-161">Kräver Windows Server 2012 eller senare.</span><span class="sxs-lookup"><span data-stu-id="88086-161">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="88086-162">Har inte stöd för det andra hoppet för WinRM.</span><span class="sxs-lookup"><span data-stu-id="88086-162">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="88086-163">Kräver behörighet att uppdatera objekt och SPN-namn (Service Principal Names).</span><span class="sxs-lookup"><span data-stu-id="88086-163">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="88086-164">Exempel</span><span class="sxs-lookup"><span data-stu-id="88086-164">Example</span></span>

<span data-ttu-id="88086-165">Nu ska vi titta på ett PowerShell-exempel som konfigurerar resurs baserad begränsad delegering på _ServerC_ för att tillåta delegerade autentiseringsuppgifter från en _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="88086-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="88086-166">I det här exemplet förutsätts att alla servrar kör Windows Server 2012 eller senare och att det finns minst en Windows Server 2012-domänkontrollant varje domän som någon av servrarna tillhör.</span><span class="sxs-lookup"><span data-stu-id="88086-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="88086-167">Innan du kan konfigurera begränsad delegering måste du lägga till funktionen `RSAT-AD-PowerShell` för att installera Active Directory PowerShell-modulen och sedan importera modulen till sessionen:</span><span class="sxs-lookup"><span data-stu-id="88086-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="88086-168">Flera tillgängliga cmdlets har nu en **PrincipalsAllowedToDelegateToAccount** -parameter:</span><span class="sxs-lookup"><span data-stu-id="88086-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

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

<span data-ttu-id="88086-169">Parametern **PrincipalsAllowedToDelegateToAccount** anger attributet **msDS-AllowedToActOnBehalfOfOtherIdentity**för Active Directory Object som innehåller en åtkomst kontrol lista (ACL) som anger vilka konton som har behörighet att delegera autentiseringsuppgifter till det associerade kontot (i vårt exempel är det dator kontot för _servern_).</span><span class="sxs-lookup"><span data-stu-id="88086-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="88086-170">Nu ska vi ställa in variablerna som ska användas för att representera servrarna:</span><span class="sxs-lookup"><span data-stu-id="88086-170">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="88086-171">WinRM (och därmed PowerShell-fjärrkommunikation) körs som dator kontot som standard.</span><span class="sxs-lookup"><span data-stu-id="88086-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="88086-172">Du kan se detta genom att titta på egenskapen **StartName** för tjänsten `winrm`:</span><span class="sxs-lookup"><span data-stu-id="88086-172">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="88086-173">För att _ServerC_ ska kunna tillåta delegering från en PowerShell-fjärrsession på _ServerB_kommer vi att bevilja åtkomst genom att ställa in **PrincipalsAllowedToDelegateToAccount** -parametern på _ServerC_ till datorobjektet för _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="88086-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="88086-174">Kerberos [-Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) nekade åtkomst försök (negativt cacheminne) i 15 minuter.</span><span class="sxs-lookup"><span data-stu-id="88086-174">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="88086-175">Om _ServerB_ tidigare har försökt få åtkomst till _ServerC_måste du rensa cacheminnet på _ServerB_ genom att anropa följande kommando:</span><span class="sxs-lookup"><span data-stu-id="88086-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="88086-176">Du kan också starta om datorn eller vänta minst 15 minuter för att rensa cacheminnet.</span><span class="sxs-lookup"><span data-stu-id="88086-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="88086-177">När du har rensat cacheminnet kan du köra kod från _reserverad_ till _ServerB_ till _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="88086-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="88086-178">I det här exemplet används variabeln `$using` för att göra `$ServerC`-variabeln synlig för _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="88086-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="88086-179">Mer information om variabeln `$using` finns [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="88086-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="88086-180">Om du vill tillåta att flera servrar delegerar autentiseringsuppgifter till _ServerC_anger du värdet för parametern **PrincipalsAllowedToDelegateToAccount** på _ServerC_ till en matris:</span><span class="sxs-lookup"><span data-stu-id="88086-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="88086-181">Om du vill göra det andra hoppet över domäner lägger du till fullständigt kvalificerat domän namn (FQDN) för domän kontrol Lanterna för den domän som _ServerB_ tillhör:</span><span class="sxs-lookup"><span data-stu-id="88086-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="88086-182">Om du vill ta bort möjligheten att delegera autentiseringsuppgifter till ServerC anger du värdet för parametern **PrincipalsAllowedToDelegateToAccount** på _ServerC_ för att `$null`:</span><span class="sxs-lookup"><span data-stu-id="88086-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="88086-183">Information om Resource-baserad Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="88086-183">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="88086-184">Vad är nytt i Kerberos-autentisering</span><span class="sxs-lookup"><span data-stu-id="88086-184">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="88086-185">Hur Windows Server 2012 underlättar smärta hos Kerberos-begränsad delegering, del 1</span><span class="sxs-lookup"><span data-stu-id="88086-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="88086-186">Hur Windows Server 2012 underlättar smärta hos Kerberos-begränsad delegering, del 2</span><span class="sxs-lookup"><span data-stu-id="88086-186">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="88086-187">Förstå Kerberos-begränsad delegering för Azure Active Directory-programproxy distributioner med integrerad Windows-autentisering</span><span class="sxs-lookup"><span data-stu-id="88086-187">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](https://aka.ms/kcdpaper)
- <span data-ttu-id="88086-188">[[MS-ADA2]: Active Directory schema attribut M 2.210 attribut msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405)</span><span class="sxs-lookup"><span data-stu-id="88086-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405)</span></span>
- <span data-ttu-id="88086-189">[[MS-SFU]: Kerberos-protokoll tillägg: tjänst för användare och begränsad Delegerings protokoll 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a)</span><span class="sxs-lookup"><span data-stu-id="88086-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a)</span></span>
- [<span data-ttu-id="88086-190">Resurs baserad Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="88086-190">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="88086-191">Fjärr administration utan begränsad delegering med PrincipalsAllowedToDelegateToAccount</span><span class="sxs-lookup"><span data-stu-id="88086-191">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="88086-192">PSSessionConfiguration med RunAs</span><span class="sxs-lookup"><span data-stu-id="88086-192">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="88086-193">Du kan skapa en sessionshantering på _ServerB_ och ange dess **RunAsCredential** -parameter.</span><span class="sxs-lookup"><span data-stu-id="88086-193">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="88086-194">Information om hur du använder PSSessionConfiguration och RunAs för att lösa det andra hopp problemet finns i [en annan lösning på multi-hop PowerShell-fjärrkommunikation](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="88086-194">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="88086-195">Fördelar</span><span class="sxs-lookup"><span data-stu-id="88086-195">Pros</span></span>

- <span data-ttu-id="88086-196">Fungerar med valfri server med WMF 3,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="88086-196">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="88086-197">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="88086-197">Cons</span></span>

- <span data-ttu-id="88086-198">Kräver konfiguration av **PSSessionConfiguration** och **runas** på varje mellanliggande server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="88086-198">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="88086-199">Kräver lösen ords underhåll när du använder ett domän konto för **runas**</span><span class="sxs-lookup"><span data-stu-id="88086-199">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="88086-200">JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="88086-200">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="88086-201">Med JEA kan du begränsa vilka kommandon en administratör kan köra under en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="88086-201">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="88086-202">Det kan användas för att lösa det andra hopp problemet.</span><span class="sxs-lookup"><span data-stu-id="88086-202">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="88086-203">Mer information om JEA finns i [tillräckligt med administration](/powershell/scripting/learn/remoting/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="88086-203">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="88086-204">Fördelar</span><span class="sxs-lookup"><span data-stu-id="88086-204">Pros</span></span>

- <span data-ttu-id="88086-205">Inget lösen ords underhåll när du använder ett virtuellt konto.</span><span class="sxs-lookup"><span data-stu-id="88086-205">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="88086-206">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="88086-206">Cons</span></span>

- <span data-ttu-id="88086-207">Kräver WMF 5,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="88086-207">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="88086-208">Kräver konfiguration på varje mellanliggande server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="88086-208">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="88086-209">Skicka autentiseringsuppgifter i ett Invoke-kommando skript block</span><span class="sxs-lookup"><span data-stu-id="88086-209">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="88086-210">Du kan skicka autentiseringsuppgifter i **script block** -parametern för ett anrop till cmdleten [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) .</span><span class="sxs-lookup"><span data-stu-id="88086-210">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="88086-211">Fördelar</span><span class="sxs-lookup"><span data-stu-id="88086-211">Pros</span></span>

- <span data-ttu-id="88086-212">Kräver ingen särskild Server konfiguration.</span><span class="sxs-lookup"><span data-stu-id="88086-212">Does not require special server configuration.</span></span>
- <span data-ttu-id="88086-213">Fungerar på alla servrar som kör WMF 2,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="88086-213">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="88086-214">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="88086-214">Cons</span></span>

- <span data-ttu-id="88086-215">Kräver en olämplig kod teknik.</span><span class="sxs-lookup"><span data-stu-id="88086-215">Requires an awkward code technique.</span></span>
- <span data-ttu-id="88086-216">Om du kör WMF 2,0 krävs en annan syntax för att skicka argument till en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="88086-216">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="88086-217">Exempel</span><span class="sxs-lookup"><span data-stu-id="88086-217">Example</span></span>

<span data-ttu-id="88086-218">I följande exempel visas hur du skickar autentiseringsuppgifter i ett **Invoke-kommando** skript block:</span><span class="sxs-lookup"><span data-stu-id="88086-218">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="88086-219">Se även</span><span class="sxs-lookup"><span data-stu-id="88086-219">See also</span></span>

[<span data-ttu-id="88086-220">Säkerhetsöverväganden för PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="88086-220">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)
