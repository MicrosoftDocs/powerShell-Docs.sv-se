---
ms.date: 05/14/2020
keywords: powershell,cmdlet
title: Göra det andra hoppet i PowerShell-fjärrkommunikation
description: I den här artikeln beskrivs de olika metoderna för att konfigurera en andra hopp-autentisering för PowerShell-fjärrkommunikation, inklusive säkerhets aspekter och rekommendationer.
ms.openlocfilehash: 905b27b4e6c612249c945a741bbe0d2ba9ae28aa
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501379"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="24f59-104">Göra det andra hoppet i PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="24f59-104">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="24f59-105">"Andra hopp problemet" syftar på en situation som följande:</span><span class="sxs-lookup"><span data-stu-id="24f59-105">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="24f59-106">Du är inloggad på _reserverad_.</span><span class="sxs-lookup"><span data-stu-id="24f59-106">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="24f59-107">Från _ServerA_säkerhetsstartar du en fjärran sluten PowerShell-session för att ansluta till _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="24f59-107">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="24f59-108">Ett kommando som du kör på _ServerB_ via din PowerShell-fjärrsession försöker få åtkomst till en resurs på _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="24f59-108">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="24f59-109">Åtkomst till resursen på _ServerC_ nekas eftersom de autentiseringsuppgifter som du använde för att skapa PowerShell-fjärrsessionen inte skickas från _ServerB_ till _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="24f59-109">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="24f59-110">Det finns flera sätt att åtgärda problemet.</span><span class="sxs-lookup"><span data-stu-id="24f59-110">There are several ways to address this problem.</span></span> <span data-ttu-id="24f59-111">I följande tabell visas metoderna i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="24f59-111">The following table lists the methods in order of preference.</span></span>

|                      <span data-ttu-id="24f59-112">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="24f59-112">Configuration</span></span>                       |                                  <span data-ttu-id="24f59-113">Anteckning</span><span class="sxs-lookup"><span data-stu-id="24f59-113">Note</span></span>                                  |
| -------------------------------------------------------- | ---------------------------------------------------------------------- |
| <span data-ttu-id="24f59-114">CredSSP</span><span class="sxs-lookup"><span data-stu-id="24f59-114">CredSSP</span></span>                                                  | <span data-ttu-id="24f59-115">Balanserar enkelt användning och säkerhet</span><span class="sxs-lookup"><span data-stu-id="24f59-115">Balances ease of use and security</span></span>                                      |
| <span data-ttu-id="24f59-116">Resurs-baserad Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="24f59-116">Resource-based Kerberos constrained delegation</span></span>           | <span data-ttu-id="24f59-117">Högre säkerhet med enklare konfiguration</span><span class="sxs-lookup"><span data-stu-id="24f59-117">Higher security with simpler configuration</span></span>                             |
| <span data-ttu-id="24f59-118">Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="24f59-118">Kerberos constrained delegation</span></span>                          | <span data-ttu-id="24f59-119">Hög säkerhet men kräver domän administratör</span><span class="sxs-lookup"><span data-stu-id="24f59-119">High security but requires Domain Administrator</span></span>                         |
| <span data-ttu-id="24f59-120">Kerberos-delegering (obegränsad)</span><span class="sxs-lookup"><span data-stu-id="24f59-120">Kerberos delegation (unconstrained)</span></span>                      | <span data-ttu-id="24f59-121">Rekommenderas inte</span><span class="sxs-lookup"><span data-stu-id="24f59-121">Not recommended</span></span>                                                        |
| <span data-ttu-id="24f59-122">JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="24f59-122">Just Enough Administration (JEA)</span></span>                         | <span data-ttu-id="24f59-123">Kan ge bästa möjliga säkerhet men kräver mer detaljerad konfiguration</span><span class="sxs-lookup"><span data-stu-id="24f59-123">Can provide the best security but requires more detailed configuration</span></span> |
| <span data-ttu-id="24f59-124">PSSessionConfiguration med RunAs</span><span class="sxs-lookup"><span data-stu-id="24f59-124">PSSessionConfiguration using RunAs</span></span>                       | <span data-ttu-id="24f59-125">Enklare att konfigurera men kräver hantering av autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="24f59-125">Simpler to configure but requires credential management</span></span>                |
| <span data-ttu-id="24f59-126">Skicka autentiseringsuppgifter i ett `Invoke-Command` skript block</span><span class="sxs-lookup"><span data-stu-id="24f59-126">Pass credentials inside an `Invoke-Command` script block</span></span> | <span data-ttu-id="24f59-127">Enklaste att använda men du måste ange autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="24f59-127">Simplest to use but you must provide credentials</span></span>                       |

## <a name="credssp"></a><span data-ttu-id="24f59-128">CredSSP</span><span class="sxs-lookup"><span data-stu-id="24f59-128">CredSSP</span></span>

<span data-ttu-id="24f59-129">Du kan använda [CredSSP (Credential Security Support Provider)][credssp] för autentisering.</span><span class="sxs-lookup"><span data-stu-id="24f59-129">You can use the [Credential Security Support Provider (CredSSP)][credssp] for authentication.</span></span>
<span data-ttu-id="24f59-130">CredSSP cachelagrar autentiseringsuppgifter på fjärrservern (_ServerB_) så att du kan använda den för att öppna autentiseringsuppgifter för stöld av autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="24f59-130">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="24f59-131">Om fjärrdatorn komprometteras har angriparen till gång till användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="24f59-131">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="24f59-132">CredSSP är inaktiverat som standard på både klient-och serverdatorer.</span><span class="sxs-lookup"><span data-stu-id="24f59-132">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="24f59-133">Du bör endast aktivera CredSSP i de mest betrodda miljöerna.</span><span class="sxs-lookup"><span data-stu-id="24f59-133">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="24f59-134">Till exempel en domän administratör som ansluter till en domänkontrollant eftersom domänkontrollanten är hög betrodd.</span><span class="sxs-lookup"><span data-stu-id="24f59-134">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="24f59-135">Mer information om säkerhets problem när du använder CredSSP för PowerShell-fjärrkommunikation finns i avsnittet [om oavsiktlig sabotage: Tänk på CredSSP][beware].</span><span class="sxs-lookup"><span data-stu-id="24f59-135">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP][beware].</span></span>

<span data-ttu-id="24f59-136">Mer information om stöld av autentiseringsuppgifter finns i [minimera pass-The-hash-attacker (PTH) och annan stöld av autentiseringsuppgifter][pth].</span><span class="sxs-lookup"><span data-stu-id="24f59-136">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft][pth].</span></span>

<span data-ttu-id="24f59-137">Ett exempel på hur du aktiverar och använder CredSSP för PowerShell-fjärrkommunikation finns i [Aktivera PowerShell-funktionen "andra hopp" med CredSSP][credssp-psblog].</span><span class="sxs-lookup"><span data-stu-id="24f59-137">For an example of how to enable and use CredSSP for PowerShell remoting, see [Enable PowerShell "Second-Hop" Functionality with CredSSP][credssp-psblog].</span></span>

<span data-ttu-id="24f59-138">**Fördelar**</span><span class="sxs-lookup"><span data-stu-id="24f59-138">**Pros**</span></span>

- <span data-ttu-id="24f59-139">Det fungerar för alla servrar med Windows Server 2008 eller senare.</span><span class="sxs-lookup"><span data-stu-id="24f59-139">It works for all servers with Windows Server 2008 or later.</span></span>

<span data-ttu-id="24f59-140">**Nackdelar**</span><span class="sxs-lookup"><span data-stu-id="24f59-140">**Cons**</span></span>

- <span data-ttu-id="24f59-141">Säkerhets problem.</span><span class="sxs-lookup"><span data-stu-id="24f59-141">Has security vulnerabilities.</span></span>
- <span data-ttu-id="24f59-142">Kräver konfiguration av både klient-och Server roller.</span><span class="sxs-lookup"><span data-stu-id="24f59-142">Requires configuration of both client and server roles.</span></span>
- <span data-ttu-id="24f59-143">Fungerar inte med gruppen skyddade användare.</span><span class="sxs-lookup"><span data-stu-id="24f59-143">Does not work with the Protected Users group.</span></span> <span data-ttu-id="24f59-144">Mer information finns i [säkerhets gruppen skyddade användare][protected-users].</span><span class="sxs-lookup"><span data-stu-id="24f59-144">For more information, see [Protected Users Security Group][protected-users].</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="24f59-145">Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="24f59-145">Kerberos constrained delegation</span></span>

<span data-ttu-id="24f59-146">Du kan använda en äldre begränsad delegering (inte resurs baserad) för att göra det andra hoppet.</span><span class="sxs-lookup"><span data-stu-id="24f59-146">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="24f59-147">Konfigurera Kerberos-begränsad delegering med alternativet "Använd valfria autentiseringsprotokoll" för att tillåta protokoll över gång.</span><span class="sxs-lookup"><span data-stu-id="24f59-147">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

<span data-ttu-id="24f59-148">**Fördelar**</span><span class="sxs-lookup"><span data-stu-id="24f59-148">**Pros**</span></span>

- <span data-ttu-id="24f59-149">Kräver ingen särskild kodning</span><span class="sxs-lookup"><span data-stu-id="24f59-149">Requires no special coding</span></span>
- <span data-ttu-id="24f59-150">Autentiseringsuppgifterna lagras inte.</span><span class="sxs-lookup"><span data-stu-id="24f59-150">Credentials are not stored.</span></span>

<span data-ttu-id="24f59-151">**Nackdelar**</span><span class="sxs-lookup"><span data-stu-id="24f59-151">**Cons**</span></span>

- <span data-ttu-id="24f59-152">Har inte stöd för det andra hoppet för WinRM.</span><span class="sxs-lookup"><span data-stu-id="24f59-152">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="24f59-153">Kräver domän administratörs behörighet för att konfigurera.</span><span class="sxs-lookup"><span data-stu-id="24f59-153">Requires Domain Administrator access to configure.</span></span>
- <span data-ttu-id="24f59-154">Måste konfigureras på Active Directory-objektet på fjärrservern (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="24f59-154">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="24f59-155">Begränsad till en domän.</span><span class="sxs-lookup"><span data-stu-id="24f59-155">Limited to one domain.</span></span> <span data-ttu-id="24f59-156">Det går inte att korsa domäner eller skogar.</span><span class="sxs-lookup"><span data-stu-id="24f59-156">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="24f59-157">Kräver behörighet att uppdatera objekt och SPN-namn (Service Principal Names).</span><span class="sxs-lookup"><span data-stu-id="24f59-157">Requires rights to update objects and Service Principal Names (SPNs).</span></span>
- <span data-ttu-id="24f59-158">_ServerB_ kan hämta en Kerberos-biljett till _ServerC_ för användarens räkning utan att användaren behöver göra något.</span><span class="sxs-lookup"><span data-stu-id="24f59-158">_ServerB_ can acquire a Kerberos ticket to _ServerC_ on behalf of the user without user intervention.</span></span>

> [!NOTE]
> <span data-ttu-id="24f59-159">Active Directory konton som har **kontot känsligt och det inte går** att delegera egenskaps uppsättningen kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="24f59-159">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="24f59-160">Mer information finns i [säkerhets fokus: analys av kontot är känsligt och kan inte delegeras för privilegierade konton][blog] och [verktyg och inställningar för Kerberos-autentisering][ktools].</span><span class="sxs-lookup"><span data-stu-id="24f59-160">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog] and [Kerberos Authentication Tools and Settings][ktools].</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="24f59-161">Resurs-baserad Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="24f59-161">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="24f59-162">Med hjälp av resurs baserad Kerberos-begränsad delegering (som introducerades i Windows Server 2012) konfigurerar du delegering av autentiseringsuppgifter på det Server objekt där resurserna finns.</span><span class="sxs-lookup"><span data-stu-id="24f59-162">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span> <span data-ttu-id="24f59-163">I det andra hopp scenariot som beskrivs ovan konfigurerar du _ServerC_ för att ange från vilken den accepterar delegerade autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="24f59-163">In the second hop scenario described above, you configure _ServerC_ to specify from where it accepts delegated credentials.</span></span>

<span data-ttu-id="24f59-164">**Fördelar**</span><span class="sxs-lookup"><span data-stu-id="24f59-164">**Pros**</span></span>

- <span data-ttu-id="24f59-165">Autentiseringsuppgifterna lagras inte.</span><span class="sxs-lookup"><span data-stu-id="24f59-165">Credentials are not stored.</span></span>
- <span data-ttu-id="24f59-166">Konfigurerad med PowerShell-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="24f59-166">Configured using PowerShell cmdlets.</span></span> <span data-ttu-id="24f59-167">Ingen särskild kod krävs.</span><span class="sxs-lookup"><span data-stu-id="24f59-167">No special coding required.</span></span>
- <span data-ttu-id="24f59-168">Kräver inte domän administratörs behörighet för att konfigurera.</span><span class="sxs-lookup"><span data-stu-id="24f59-168">Does not require Domain Administrator access to configure.</span></span>
- <span data-ttu-id="24f59-169">Fungerar över domäner och skogar.</span><span class="sxs-lookup"><span data-stu-id="24f59-169">Works across domains and forests.</span></span>

<span data-ttu-id="24f59-170">**Nackdelar**</span><span class="sxs-lookup"><span data-stu-id="24f59-170">**Cons**</span></span>

- <span data-ttu-id="24f59-171">Kräver Windows Server 2012 eller senare.</span><span class="sxs-lookup"><span data-stu-id="24f59-171">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="24f59-172">Har inte stöd för det andra hoppet för WinRM.</span><span class="sxs-lookup"><span data-stu-id="24f59-172">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="24f59-173">Kräver behörighet att uppdatera objekt och SPN-namn (Service Principal Names).</span><span class="sxs-lookup"><span data-stu-id="24f59-173">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

> [!NOTE]
> <span data-ttu-id="24f59-174">Active Directory konton som har **kontot känsligt och det inte går** att delegera egenskaps uppsättningen kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="24f59-174">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="24f59-175">Mer information finns i [säkerhets fokus: analys av kontot är känsligt och kan inte delegeras för privilegierade konton][blog] och [verktyg och inställningar för Kerberos-autentisering][ktools].</span><span class="sxs-lookup"><span data-stu-id="24f59-175">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog] and [Kerberos Authentication Tools and Settings][ktools].</span></span>

### <a name="example"></a><span data-ttu-id="24f59-176">Exempel</span><span class="sxs-lookup"><span data-stu-id="24f59-176">Example</span></span>

<span data-ttu-id="24f59-177">Nu ska vi titta på ett PowerShell-exempel som konfigurerar resurs-baserad begränsad delegering på _ServerC_ för att tillåta delegerade autentiseringsuppgifter från en _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="24f59-177">Let's look at a PowerShell example that configures resource-based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span> <span data-ttu-id="24f59-178">I det här exemplet förutsätts att alla servrar kör Windows Server 2012 eller senare och att det finns minst en Windows Server 2012-domänkontrollant varje domän som någon av servrarna tillhör.</span><span class="sxs-lookup"><span data-stu-id="24f59-178">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="24f59-179">Innan du kan konfigurera begränsad delegering måste du lägga till `RSAT-AD-PowerShell` funktionen för att installera Active Directory PowerShell-modulen och sedan importera modulen till sessionen:</span><span class="sxs-lookup"><span data-stu-id="24f59-179">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
Add-WindowsFeature RSAT-AD-PowerShell
Import-Module ActiveDirectory
Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="24f59-180">Flera tillgängliga cmdlets har nu en **PrincipalsAllowedToDelegateToAccount** -parameter:</span><span class="sxs-lookup"><span data-stu-id="24f59-180">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```Output
CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="24f59-181">Parametern **PrincipalsAllowedToDelegateToAccount** anger attributet **msDS-AllowedToActOnBehalfOfOtherIdentity**för Active Directory Object, som innehåller en åtkomst kontrol lista (ACL) som anger vilka konton som har behörighet att delegera autentiseringsuppgifter till det associerade kontot (i vårt exempel är det dator kontot för den server som är _reserverad_).</span><span class="sxs-lookup"><span data-stu-id="24f59-181">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _ServerA_).</span></span>

<span data-ttu-id="24f59-182">Nu ska vi ställa in variablerna som ska användas för att representera servrarna:</span><span class="sxs-lookup"><span data-stu-id="24f59-182">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="24f59-183">WinRM (och därmed PowerShell-fjärrkommunikation) körs som dator kontot som standard.</span><span class="sxs-lookup"><span data-stu-id="24f59-183">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="24f59-184">Du kan se detta genom att titta på **StartName** `winrm` tjänstens StartName-egenskap:</span><span class="sxs-lookup"><span data-stu-id="24f59-184">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name="winrm"' | Select-Object StartName
```

```Output
StartName
---------
NT AUTHORITY\NetworkService
```

<span data-ttu-id="24f59-185">För att _ServerC_ ska kunna tillåta delegering från en PowerShell-fjärrsession på _ServerB_, måste du ange parametern **PrincipalsAllowedToDelegateToAccount** på _ServerC_ till datorobjektet för _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="24f59-185">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we must set the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="24f59-186">Kerberos- [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) nekar åtkomst försök (negativ cache) i 15 minuter.</span><span class="sxs-lookup"><span data-stu-id="24f59-186">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied-access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="24f59-187">Om _ServerB_ tidigare har försökt få åtkomst till _ServerC_måste du rensa cacheminnet på _ServerB_ genom att anropa följande kommando:</span><span class="sxs-lookup"><span data-stu-id="24f59-187">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="24f59-188">Du kan också starta om datorn eller vänta minst 15 minuter för att rensa cacheminnet.</span><span class="sxs-lookup"><span data-stu-id="24f59-188">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="24f59-189">När du har rensat cacheminnet kan du köra kod från _reserverad_ till _ServerB_ till _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="24f59-189">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="24f59-190">I det här exemplet `$using` används variabeln för att göra `$ServerC` variabeln synlig för _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="24f59-190">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span>
<span data-ttu-id="24f59-191">Mer information om `$using` variabeln finns i [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables).</span><span class="sxs-lookup"><span data-stu-id="24f59-191">For more information about the `$using` variable, see [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables).</span></span>

<span data-ttu-id="24f59-192">Om du vill tillåta att flera servrar delegerar autentiseringsuppgifter till _ServerC_anger du värdet för parametern **PrincipalsAllowedToDelegateToAccount** på _ServerC_ till en matris:</span><span class="sxs-lookup"><span data-stu-id="24f59-192">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="24f59-193">Om du vill göra det andra hoppet över domäner lägger du till fullständigt kvalificerat domän namn (FQDN) för domän kontrol Lanterna för den domän som _ServerB_ tillhör:</span><span class="sxs-lookup"><span data-stu-id="24f59-193">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="24f59-194">Om du vill ta bort möjligheten att delegera autentiseringsuppgifter till ServerC anger du värdet för parametern **PrincipalsAllowedToDelegateToAccount** på _ServerC_ till `$null` :</span><span class="sxs-lookup"><span data-stu-id="24f59-194">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="24f59-195">Information om Resource-baserad Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="24f59-195">Information on resource-based Kerberos constrained delegation</span></span>

- <span data-ttu-id="24f59-196">[Nyheter i Kerberos-autentisering][whats-new]</span><span class="sxs-lookup"><span data-stu-id="24f59-196">[What's New in Kerberos Authentication][whats-new]</span></span>
- <span data-ttu-id="24f59-197">[Hur Windows Server 2012 underlättar smärta hos Kerberos-begränsad delegering, del 1][kcd2012-1]</span><span class="sxs-lookup"><span data-stu-id="24f59-197">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1][kcd2012-1]</span></span>
- <span data-ttu-id="24f59-198">[Hur Windows Server 2012 underlättar smärta hos Kerberos-begränsad delegering, del 2][kcd2012-2]</span><span class="sxs-lookup"><span data-stu-id="24f59-198">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2][kcd2012-2]</span></span>
- <span data-ttu-id="24f59-199">[Förstå Kerberos-begränsad delegering för Azure Active Directory-programproxy distributioner med integrerad Windows-autentisering][kcdpaper]</span><span class="sxs-lookup"><span data-stu-id="24f59-199">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication][kcdpaper]</span></span>
- <span data-ttu-id="24f59-200">[[MS-ADA2] Active Directory schemaattributet M 2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]</span><span class="sxs-lookup"><span data-stu-id="24f59-200">[[MS-ADA2] Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]</span></span>
- <span data-ttu-id="24f59-201">[[MS-SFU] Kerberos-protokoll tillägg: tjänst för användare och begränsad Delegerings protokoll 1.3.2 S4U2proxy][MS-SFU]</span><span class="sxs-lookup"><span data-stu-id="24f59-201">[[MS-SFU] Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy][MS-SFU]</span></span>
- <span data-ttu-id="24f59-202">[Fjärr administration utan begränsad delegering med PrincipalsAllowedToDelegateToAccount][remote-admin]</span><span class="sxs-lookup"><span data-stu-id="24f59-202">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount][remote-admin]</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="24f59-203">Kerberos-delegering (obegränsad)</span><span class="sxs-lookup"><span data-stu-id="24f59-203">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="24f59-204">Du kan också använda Kerberos-obegränsad delegering för att göra det andra hoppet.</span><span class="sxs-lookup"><span data-stu-id="24f59-204">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="24f59-205">Precis som alla Kerberos-scenarier lagras inga autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="24f59-205">Like all Kerberos scenarios, credentials are not stored.</span></span> <span data-ttu-id="24f59-206">Den här metoden stöder inte det andra hoppet för WinRM.</span><span class="sxs-lookup"><span data-stu-id="24f59-206">This method does not support the second hop for WinRM.</span></span>

> [!WARNING]
> <span data-ttu-id="24f59-207">Den här metoden ger ingen kontroll över var delegerade autentiseringsuppgifter används.</span><span class="sxs-lookup"><span data-stu-id="24f59-207">This method provides no control of where delegated credentials are used.</span></span> <span data-ttu-id="24f59-208">Den är mindre säker än CredSSP.</span><span class="sxs-lookup"><span data-stu-id="24f59-208">It is less secure than CredSSP.</span></span> <span data-ttu-id="24f59-209">Den här metoden bör endast användas för testnings scenarier.</span><span class="sxs-lookup"><span data-stu-id="24f59-209">This method should only be used for testing scenarios.</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="24f59-210">JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="24f59-210">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="24f59-211">Med JEA kan du begränsa vilka kommandon en administratör kan köra under en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="24f59-211">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="24f59-212">Det kan användas för att lösa det andra hopp problemet.</span><span class="sxs-lookup"><span data-stu-id="24f59-212">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="24f59-213">Mer information om JEA finns i [tillräckligt med administration](/powershell/scripting/learn/remoting/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="24f59-213">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span></span>

<span data-ttu-id="24f59-214">**Fördelar**</span><span class="sxs-lookup"><span data-stu-id="24f59-214">**Pros**</span></span>

- <span data-ttu-id="24f59-215">Inget lösen ords underhåll när du använder ett virtuellt konto.</span><span class="sxs-lookup"><span data-stu-id="24f59-215">No password maintenance when using a virtual account.</span></span>

<span data-ttu-id="24f59-216">**Nackdelar**</span><span class="sxs-lookup"><span data-stu-id="24f59-216">**Cons**</span></span>

- <span data-ttu-id="24f59-217">Kräver WMF 5,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="24f59-217">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="24f59-218">Kräver konfiguration på varje mellanliggande server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="24f59-218">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="24f59-219">PSSessionConfiguration med RunAs</span><span class="sxs-lookup"><span data-stu-id="24f59-219">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="24f59-220">Du kan skapa en sessionshantering på _ServerB_ och ange dess **RunAsCredential** -parameter.</span><span class="sxs-lookup"><span data-stu-id="24f59-220">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="24f59-221">Information om hur du använder **PSSessionConfiguration** och **runas** för att lösa det andra hopp problemet finns i [en annan lösning på multi-hop PowerShell-fjärrkommunikation][pssessionconfig].</span><span class="sxs-lookup"><span data-stu-id="24f59-221">For information about using **PSSessionConfiguration** and **RunAs** to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting][pssessionconfig].</span></span>

<span data-ttu-id="24f59-222">**Fördelar**</span><span class="sxs-lookup"><span data-stu-id="24f59-222">**Pros**</span></span>

- <span data-ttu-id="24f59-223">Fungerar med valfri server med WMF 3,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="24f59-223">Works with any server with WMF 3.0 or later.</span></span>

<span data-ttu-id="24f59-224">**Nackdelar**</span><span class="sxs-lookup"><span data-stu-id="24f59-224">**Cons**</span></span>

- <span data-ttu-id="24f59-225">Kräver konfiguration av **PSSessionConfiguration** och **runas** på varje mellanliggande server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="24f59-225">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="24f59-226">Kräver lösen ords underhåll när du använder ett domän konto för **runas**</span><span class="sxs-lookup"><span data-stu-id="24f59-226">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="24f59-227">Skicka autentiseringsuppgifter i ett Invoke-Command-skript block</span><span class="sxs-lookup"><span data-stu-id="24f59-227">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="24f59-228">Du kan skicka autentiseringsuppgifter i **script block** -parametern för ett anrop till cmdleten [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) .</span><span class="sxs-lookup"><span data-stu-id="24f59-228">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

<span data-ttu-id="24f59-229">**Fördelar**</span><span class="sxs-lookup"><span data-stu-id="24f59-229">**Pros**</span></span>

- <span data-ttu-id="24f59-230">Kräver ingen särskild Server konfiguration.</span><span class="sxs-lookup"><span data-stu-id="24f59-230">Does not require special server configuration.</span></span>
- <span data-ttu-id="24f59-231">Fungerar på alla servrar som kör WMF 2,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="24f59-231">Works on any server running WMF 2.0 or later.</span></span>

<span data-ttu-id="24f59-232">**Nackdelar**</span><span class="sxs-lookup"><span data-stu-id="24f59-232">**Cons**</span></span>

- <span data-ttu-id="24f59-233">Kräver en olämplig kod teknik.</span><span class="sxs-lookup"><span data-stu-id="24f59-233">Requires an awkward code technique.</span></span>
- <span data-ttu-id="24f59-234">Om du kör WMF 2,0 krävs en annan syntax för att skicka argument till en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="24f59-234">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="24f59-235">Exempel</span><span class="sxs-lookup"><span data-stu-id="24f59-235">Example</span></span>

<span data-ttu-id="24f59-236">I följande exempel visas hur du skickar autentiseringsuppgifter i ett **Invoke-kommando** skript block:</span><span class="sxs-lookup"><span data-stu-id="24f59-236">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="24f59-237">Se även</span><span class="sxs-lookup"><span data-stu-id="24f59-237">See also</span></span>

[<span data-ttu-id="24f59-238">Säkerhetsöverväganden för PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="24f59-238">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)

<!-- link references -->
[blog]: /archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts
[ktools]: /previous-versions/windows/it-pro/windows-server-2003/cc738673(v=ws.10)
[credssp]: /windows/win32/secauthn/credential-security-support-provider
[beware]: https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp
[pth]: https://www.microsoft.com/download/details.aspx?id=36036
[credssp-psblog]: https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/
[whats-new]: /previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831747(v=ws.11)
[kcd2012-1]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1
[kcd2012-2]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2
[kcdpaper]: https://aka.ms/kcdpaper
[MS-ADA2]: /openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405
[MS-SFU]: /openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a
[remote-admin]: /archive/blogs/taylorb/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount
[pssessionconfig]: /archive/blogs/sergey_babkins_blog/another-solution-to-multi-hop-powershell-remoting
[protected-users]: /windows-server/security/credentials-protection-and-management/protected-users-security-group
