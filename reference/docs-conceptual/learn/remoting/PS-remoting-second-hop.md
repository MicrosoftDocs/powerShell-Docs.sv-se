---
ms.date: 05/14/2020
keywords: powershell,cmdlet
title: Göra det andra hoppet i PowerShell-fjärrkommunikation
ms.openlocfilehash: 3a9db11726d4c02dc69e52c45da304f7422def39
ms.sourcegitcommit: 843756c8277e7afb874867703963248abc8a6c91
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2020
ms.locfileid: "83439384"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="9bfab-103">Göra det andra hoppet i PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="9bfab-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="9bfab-104">"Andra hopp problemet" syftar på en situation som följande:</span><span class="sxs-lookup"><span data-stu-id="9bfab-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="9bfab-105">Du är inloggad på _reserverad_.</span><span class="sxs-lookup"><span data-stu-id="9bfab-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="9bfab-106">Från _ServerA_säkerhetsstartar du en fjärran sluten PowerShell-session för att ansluta till _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="9bfab-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="9bfab-107">Ett kommando som du kör på _ServerB_ via din PowerShell-fjärrsession försöker få åtkomst till en resurs på _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="9bfab-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="9bfab-108">Åtkomst till resursen på _ServerC_ nekas eftersom de autentiseringsuppgifter som du använde för att skapa PowerShell-fjärrsessionen inte skickas från _ServerB_ till _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="9bfab-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="9bfab-109">Det finns flera sätt att åtgärda problemet.</span><span class="sxs-lookup"><span data-stu-id="9bfab-109">There are several ways to address this problem.</span></span> <span data-ttu-id="9bfab-110">I följande tabell visas metoderna i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="9bfab-110">The following table lists the methods in order of preference.</span></span>

|                      <span data-ttu-id="9bfab-111">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="9bfab-111">Configuration</span></span>                       |                                  <span data-ttu-id="9bfab-112">Anteckning</span><span class="sxs-lookup"><span data-stu-id="9bfab-112">Note</span></span>                                  |
| -------------------------------------------------------- | ---------------------------------------------------------------------- |
| <span data-ttu-id="9bfab-113">CredSSP</span><span class="sxs-lookup"><span data-stu-id="9bfab-113">CredSSP</span></span>                                                  | <span data-ttu-id="9bfab-114">Balanserar enkelt användning och säkerhet</span><span class="sxs-lookup"><span data-stu-id="9bfab-114">Balances ease of use and security</span></span>                                      |
| <span data-ttu-id="9bfab-115">Resurs-baserad Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="9bfab-115">Resource-based Kerberos constrained delegation</span></span>           | <span data-ttu-id="9bfab-116">Högre säkerhet med enklare konfiguration</span><span class="sxs-lookup"><span data-stu-id="9bfab-116">Higher security with simpler configuration</span></span>                             |
| <span data-ttu-id="9bfab-117">Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="9bfab-117">Kerberos constrained delegation</span></span>                          | <span data-ttu-id="9bfab-118">Hög säkerhet men kräver domän administratör</span><span class="sxs-lookup"><span data-stu-id="9bfab-118">High security but requires Domain Administrator</span></span>                         |
| <span data-ttu-id="9bfab-119">Kerberos-delegering (obegränsad)</span><span class="sxs-lookup"><span data-stu-id="9bfab-119">Kerberos delegation (unconstrained)</span></span>                      | <span data-ttu-id="9bfab-120">Rekommenderas inte</span><span class="sxs-lookup"><span data-stu-id="9bfab-120">Not recommended</span></span>                                                        |
| <span data-ttu-id="9bfab-121">JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="9bfab-121">Just Enough Administration (JEA)</span></span>                         | <span data-ttu-id="9bfab-122">Kan ge bästa möjliga säkerhet men kräver mer detaljerad konfiguration</span><span class="sxs-lookup"><span data-stu-id="9bfab-122">Can provide the best security but requires more detailed configuration</span></span> |
| <span data-ttu-id="9bfab-123">PSSessionConfiguration med RunAs</span><span class="sxs-lookup"><span data-stu-id="9bfab-123">PSSessionConfiguration using RunAs</span></span>                       | <span data-ttu-id="9bfab-124">Enklare att konfigurera men kräver hantering av autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="9bfab-124">Simpler to configure but requires credential management</span></span>                |
| <span data-ttu-id="9bfab-125">Skicka autentiseringsuppgifter i ett `Invoke-Command` skript block</span><span class="sxs-lookup"><span data-stu-id="9bfab-125">Pass credentials inside an `Invoke-Command` script block</span></span> | <span data-ttu-id="9bfab-126">Enklaste att använda men du måste ange autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="9bfab-126">Simplest to use but you must provide credentials</span></span>                       |

## <a name="credssp"></a><span data-ttu-id="9bfab-127">CredSSP</span><span class="sxs-lookup"><span data-stu-id="9bfab-127">CredSSP</span></span>

<span data-ttu-id="9bfab-128">Du kan använda [CredSSP (Credential Security Support Provider)][credssp] för autentisering.</span><span class="sxs-lookup"><span data-stu-id="9bfab-128">You can use the [Credential Security Support Provider (CredSSP)][credssp] for authentication.</span></span>
<span data-ttu-id="9bfab-129">CredSSP cachelagrar autentiseringsuppgifter på fjärrservern (_ServerB_) så att du kan använda den för att öppna autentiseringsuppgifter för stöld av autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="9bfab-129">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="9bfab-130">Om fjärrdatorn komprometteras har angriparen till gång till användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="9bfab-130">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="9bfab-131">CredSSP är inaktiverat som standard på både klient-och serverdatorer.</span><span class="sxs-lookup"><span data-stu-id="9bfab-131">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="9bfab-132">Du bör endast aktivera CredSSP i de mest betrodda miljöerna.</span><span class="sxs-lookup"><span data-stu-id="9bfab-132">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="9bfab-133">Till exempel en domän administratör som ansluter till en domänkontrollant eftersom domänkontrollanten är hög betrodd.</span><span class="sxs-lookup"><span data-stu-id="9bfab-133">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="9bfab-134">Mer information om säkerhets problem när du använder CredSSP för PowerShell-fjärrkommunikation finns i avsnittet [om oavsiktlig sabotage: Tänk på CredSSP][beware].</span><span class="sxs-lookup"><span data-stu-id="9bfab-134">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP][beware].</span></span>

<span data-ttu-id="9bfab-135">Mer information om stöld av autentiseringsuppgifter finns i [minimera pass-The-hash-attacker (PTH) och annan stöld av autentiseringsuppgifter][pth].</span><span class="sxs-lookup"><span data-stu-id="9bfab-135">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft][pth].</span></span>

<span data-ttu-id="9bfab-136">Ett exempel på hur du aktiverar och använder CredSSP för PowerShell-fjärrkommunikation finns i [Aktivera PowerShell-funktionen "andra hopp" med CredSSP][credssp-psblog].</span><span class="sxs-lookup"><span data-stu-id="9bfab-136">For an example of how to enable and use CredSSP for PowerShell remoting, see [Enable PowerShell "Second-Hop" Functionality with CredSSP][credssp-psblog].</span></span>

<span data-ttu-id="9bfab-137">**Fördelar**</span><span class="sxs-lookup"><span data-stu-id="9bfab-137">**Pros**</span></span>

- <span data-ttu-id="9bfab-138">Det fungerar för alla servrar med Windows Server 2008 eller senare.</span><span class="sxs-lookup"><span data-stu-id="9bfab-138">It works for all servers with Windows Server 2008 or later.</span></span>

<span data-ttu-id="9bfab-139">**Nack delar**</span><span class="sxs-lookup"><span data-stu-id="9bfab-139">**Cons**</span></span>

- <span data-ttu-id="9bfab-140">Säkerhets problem.</span><span class="sxs-lookup"><span data-stu-id="9bfab-140">Has security vulnerabilities.</span></span>
- <span data-ttu-id="9bfab-141">Kräver konfiguration av både klient-och Server roller.</span><span class="sxs-lookup"><span data-stu-id="9bfab-141">Requires configuration of both client and server roles.</span></span>
- <span data-ttu-id="9bfab-142">Fungerar inte med gruppen skyddade användare.</span><span class="sxs-lookup"><span data-stu-id="9bfab-142">Does not work with the Protected Users group.</span></span> <span data-ttu-id="9bfab-143">Mer information finns i [säkerhets gruppen skyddade användare][protected-users].</span><span class="sxs-lookup"><span data-stu-id="9bfab-143">For more information, see [Protected Users Security Group][protected-users].</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="9bfab-144">Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="9bfab-144">Kerberos constrained delegation</span></span>

<span data-ttu-id="9bfab-145">Du kan använda en äldre begränsad delegering (inte resurs baserad) för att göra det andra hoppet.</span><span class="sxs-lookup"><span data-stu-id="9bfab-145">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="9bfab-146">Konfigurera Kerberos-begränsad delegering med alternativet "Använd valfria autentiseringsprotokoll" för att tillåta protokoll över gång.</span><span class="sxs-lookup"><span data-stu-id="9bfab-146">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

<span data-ttu-id="9bfab-147">**Fördelar**</span><span class="sxs-lookup"><span data-stu-id="9bfab-147">**Pros**</span></span>

- <span data-ttu-id="9bfab-148">Kräver ingen särskild kodning</span><span class="sxs-lookup"><span data-stu-id="9bfab-148">Requires no special coding</span></span>
- <span data-ttu-id="9bfab-149">Autentiseringsuppgifterna lagras inte.</span><span class="sxs-lookup"><span data-stu-id="9bfab-149">Credentials are not stored.</span></span>

<span data-ttu-id="9bfab-150">**Nack delar**</span><span class="sxs-lookup"><span data-stu-id="9bfab-150">**Cons**</span></span>

- <span data-ttu-id="9bfab-151">Har inte stöd för det andra hoppet för WinRM.</span><span class="sxs-lookup"><span data-stu-id="9bfab-151">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="9bfab-152">Kräver domän administratörs behörighet för att konfigurera.</span><span class="sxs-lookup"><span data-stu-id="9bfab-152">Requires Domain Administrator access to configure.</span></span>
- <span data-ttu-id="9bfab-153">Måste konfigureras på Active Directory-objektet på fjärrservern (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="9bfab-153">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="9bfab-154">Begränsad till en domän.</span><span class="sxs-lookup"><span data-stu-id="9bfab-154">Limited to one domain.</span></span> <span data-ttu-id="9bfab-155">Det går inte att korsa domäner eller skogar.</span><span class="sxs-lookup"><span data-stu-id="9bfab-155">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="9bfab-156">Kräver behörighet att uppdatera objekt och SPN-namn (Service Principal Names).</span><span class="sxs-lookup"><span data-stu-id="9bfab-156">Requires rights to update objects and Service Principal Names (SPNs).</span></span>
- <span data-ttu-id="9bfab-157">_ServerB_ kan hämta en Kerberos-biljett till _ServerC_ för användarens räkning utan att användaren behöver göra något.</span><span class="sxs-lookup"><span data-stu-id="9bfab-157">_ServerB_ can acquire a Kerberos ticket to _ServerC_ on behalf of the user without user intervention.</span></span>

> [!NOTE]
> <span data-ttu-id="9bfab-158">Active Directory konton som har **kontot känsligt och det inte går** att delegera egenskaps uppsättningen kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="9bfab-158">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="9bfab-159">Mer information finns i [säkerhets fokus: analys av kontot är känsligt och kan inte delegeras för privilegierade konton][blog] och [verktyg och inställningar för Kerberos-autentisering][ktools].</span><span class="sxs-lookup"><span data-stu-id="9bfab-159">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog] and [Kerberos Authentication Tools and Settings][ktools].</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="9bfab-160">Resurs-baserad Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="9bfab-160">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="9bfab-161">Med hjälp av resurs baserad Kerberos-begränsad delegering (som introducerades i Windows Server 2012) konfigurerar du delegering av autentiseringsuppgifter på det Server objekt där resurserna finns.</span><span class="sxs-lookup"><span data-stu-id="9bfab-161">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span> <span data-ttu-id="9bfab-162">I det andra hopp scenariot som beskrivs ovan konfigurerar du _ServerC_ för att ange från vilken den accepterar delegerade autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="9bfab-162">In the second hop scenario described above, you configure _ServerC_ to specify from where it accepts delegated credentials.</span></span>

<span data-ttu-id="9bfab-163">**Fördelar**</span><span class="sxs-lookup"><span data-stu-id="9bfab-163">**Pros**</span></span>

- <span data-ttu-id="9bfab-164">Autentiseringsuppgifterna lagras inte.</span><span class="sxs-lookup"><span data-stu-id="9bfab-164">Credentials are not stored.</span></span>
- <span data-ttu-id="9bfab-165">Konfigurerad med PowerShell-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="9bfab-165">Configured using PowerShell cmdlets.</span></span> <span data-ttu-id="9bfab-166">Ingen särskild kod krävs.</span><span class="sxs-lookup"><span data-stu-id="9bfab-166">No special coding required.</span></span>
- <span data-ttu-id="9bfab-167">Kräver inte domän administratörs behörighet för att konfigurera.</span><span class="sxs-lookup"><span data-stu-id="9bfab-167">Does not require Domain Administrator access to configure.</span></span>
- <span data-ttu-id="9bfab-168">Fungerar över domäner och skogar.</span><span class="sxs-lookup"><span data-stu-id="9bfab-168">Works across domains and forests.</span></span>

<span data-ttu-id="9bfab-169">**Nack delar**</span><span class="sxs-lookup"><span data-stu-id="9bfab-169">**Cons**</span></span>

- <span data-ttu-id="9bfab-170">Kräver Windows Server 2012 eller senare.</span><span class="sxs-lookup"><span data-stu-id="9bfab-170">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="9bfab-171">Har inte stöd för det andra hoppet för WinRM.</span><span class="sxs-lookup"><span data-stu-id="9bfab-171">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="9bfab-172">Kräver behörighet att uppdatera objekt och SPN-namn (Service Principal Names).</span><span class="sxs-lookup"><span data-stu-id="9bfab-172">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

> [!NOTE]
> <span data-ttu-id="9bfab-173">Active Directory konton som har **kontot känsligt och det inte går** att delegera egenskaps uppsättningen kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="9bfab-173">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="9bfab-174">Mer information finns i [säkerhets fokus: analys av kontot är känsligt och kan inte delegeras för privilegierade konton][blog] och [verktyg och inställningar för Kerberos-autentisering][ktools].</span><span class="sxs-lookup"><span data-stu-id="9bfab-174">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog] and [Kerberos Authentication Tools and Settings][ktools].</span></span>

### <a name="example"></a><span data-ttu-id="9bfab-175">Exempel</span><span class="sxs-lookup"><span data-stu-id="9bfab-175">Example</span></span>

<span data-ttu-id="9bfab-176">Nu ska vi titta på ett PowerShell-exempel som konfigurerar resurs-baserad begränsad delegering på _ServerC_ för att tillåta delegerade autentiseringsuppgifter från en _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="9bfab-176">Let's look at a PowerShell example that configures resource-based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span> <span data-ttu-id="9bfab-177">I det här exemplet förutsätts att alla servrar kör Windows Server 2012 eller senare och att det finns minst en Windows Server 2012-domänkontrollant varje domän som någon av servrarna tillhör.</span><span class="sxs-lookup"><span data-stu-id="9bfab-177">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="9bfab-178">Innan du kan konfigurera begränsad delegering måste du lägga till `RSAT-AD-PowerShell` funktionen för att installera Active Directory PowerShell-modulen och sedan importera modulen till sessionen:</span><span class="sxs-lookup"><span data-stu-id="9bfab-178">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
Add-WindowsFeature RSAT-AD-PowerShell
Import-Module ActiveDirectory
Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="9bfab-179">Flera tillgängliga cmdlets har nu en **PrincipalsAllowedToDelegateToAccount** -parameter:</span><span class="sxs-lookup"><span data-stu-id="9bfab-179">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

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

<span data-ttu-id="9bfab-180">Parametern **PrincipalsAllowedToDelegateToAccount** anger attributet **msDS-AllowedToActOnBehalfOfOtherIdentity**för Active Directory Object, som innehåller en åtkomst kontrol lista (ACL) som anger vilka konton som har behörighet att delegera autentiseringsuppgifter till det associerade kontot (i vårt exempel är det dator kontot för den server som är _reserverad_).</span><span class="sxs-lookup"><span data-stu-id="9bfab-180">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _ServerA_).</span></span>

<span data-ttu-id="9bfab-181">Nu ska vi ställa in variablerna som ska användas för att representera servrarna:</span><span class="sxs-lookup"><span data-stu-id="9bfab-181">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="9bfab-182">WinRM (och därmed PowerShell-fjärrkommunikation) körs som dator kontot som standard.</span><span class="sxs-lookup"><span data-stu-id="9bfab-182">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="9bfab-183">Du kan se detta genom att titta på **StartName** `winrm` tjänstens StartName-egenskap:</span><span class="sxs-lookup"><span data-stu-id="9bfab-183">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name="winrm"' | Select-Object StartName
```

```Output
StartName
---------
NT AUTHORITY\NetworkService
```

<span data-ttu-id="9bfab-184">För att _ServerC_ ska kunna tillåta delegering från en PowerShell-fjärrsession på _ServerB_, måste du ange parametern **PrincipalsAllowedToDelegateToAccount** på _ServerC_ till datorobjektet för _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="9bfab-184">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we must set the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="9bfab-185">Kerberos- [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) nekar åtkomst försök (negativ cache) i 15 minuter.</span><span class="sxs-lookup"><span data-stu-id="9bfab-185">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied-access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="9bfab-186">Om _ServerB_ tidigare har försökt få åtkomst till _ServerC_måste du rensa cacheminnet på _ServerB_ genom att anropa följande kommando:</span><span class="sxs-lookup"><span data-stu-id="9bfab-186">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="9bfab-187">Du kan också starta om datorn eller vänta minst 15 minuter för att rensa cacheminnet.</span><span class="sxs-lookup"><span data-stu-id="9bfab-187">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="9bfab-188">När du har rensat cacheminnet kan du köra kod från _reserverad_ till _ServerB_ till _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="9bfab-188">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="9bfab-189">I det här exemplet `$using` används variabeln för att göra `$ServerC` variabeln synlig för _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="9bfab-189">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span>
<span data-ttu-id="9bfab-190">Mer information om `$using` variabeln finns i [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables).</span><span class="sxs-lookup"><span data-stu-id="9bfab-190">For more information about the `$using` variable, see [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables).</span></span>

<span data-ttu-id="9bfab-191">Om du vill tillåta att flera servrar delegerar autentiseringsuppgifter till _ServerC_anger du värdet för parametern **PrincipalsAllowedToDelegateToAccount** på _ServerC_ till en matris:</span><span class="sxs-lookup"><span data-stu-id="9bfab-191">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="9bfab-192">Om du vill göra det andra hoppet över domäner lägger du till fullständigt kvalificerat domän namn (FQDN) för domän kontrol Lanterna för den domän som _ServerB_ tillhör:</span><span class="sxs-lookup"><span data-stu-id="9bfab-192">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="9bfab-193">Om du vill ta bort möjligheten att delegera autentiseringsuppgifter till ServerC anger du värdet för parametern **PrincipalsAllowedToDelegateToAccount** på _ServerC_ till `$null` :</span><span class="sxs-lookup"><span data-stu-id="9bfab-193">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="9bfab-194">Information om Resource-baserad Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="9bfab-194">Information on resource-based Kerberos constrained delegation</span></span>

- <span data-ttu-id="9bfab-195">[Nyheter i Kerberos-autentisering][whats-new]</span><span class="sxs-lookup"><span data-stu-id="9bfab-195">[What's New in Kerberos Authentication][whats-new]</span></span>
- <span data-ttu-id="9bfab-196">[Hur Windows Server 2012 underlättar smärta hos Kerberos-begränsad delegering, del 1][kcd2012-1]</span><span class="sxs-lookup"><span data-stu-id="9bfab-196">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1][kcd2012-1]</span></span>
- <span data-ttu-id="9bfab-197">[Hur Windows Server 2012 underlättar smärta hos Kerberos-begränsad delegering, del 2][kcd2012-2]</span><span class="sxs-lookup"><span data-stu-id="9bfab-197">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2][kcd2012-2]</span></span>
- <span data-ttu-id="9bfab-198">[Förstå Kerberos-begränsad delegering för Azure Active Directory-programproxy distributioner med integrerad Windows-autentisering][kcdpaper]</span><span class="sxs-lookup"><span data-stu-id="9bfab-198">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication][kcdpaper]</span></span>
- <span data-ttu-id="9bfab-199">[[MS-ADA2] Active Directory schemaattributet M 2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]</span><span class="sxs-lookup"><span data-stu-id="9bfab-199">[[MS-ADA2] Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]</span></span>
- <span data-ttu-id="9bfab-200">[[MS-SFU] Kerberos-protokoll tillägg: tjänst för användare och begränsad Delegerings protokoll 1.3.2 S4U2proxy][MS-SFU]</span><span class="sxs-lookup"><span data-stu-id="9bfab-200">[[MS-SFU] Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy][MS-SFU]</span></span>
- <span data-ttu-id="9bfab-201">[Fjärr administration utan begränsad delegering med PrincipalsAllowedToDelegateToAccount][remote-admin]</span><span class="sxs-lookup"><span data-stu-id="9bfab-201">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount][remote-admin]</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="9bfab-202">Kerberos-delegering (obegränsad)</span><span class="sxs-lookup"><span data-stu-id="9bfab-202">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="9bfab-203">Du kan också använda Kerberos-obegränsad delegering för att göra det andra hoppet.</span><span class="sxs-lookup"><span data-stu-id="9bfab-203">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="9bfab-204">Precis som alla Kerberos-scenarier lagras inga autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="9bfab-204">Like all Kerberos scenarios, credentials are not stored.</span></span> <span data-ttu-id="9bfab-205">Den här metoden stöder inte det andra hoppet för WinRM.</span><span class="sxs-lookup"><span data-stu-id="9bfab-205">This method does not support the second hop for WinRM.</span></span>

> [!WARNING]
> <span data-ttu-id="9bfab-206">Den här metoden ger ingen kontroll över var delegerade autentiseringsuppgifter används.</span><span class="sxs-lookup"><span data-stu-id="9bfab-206">This method provides no control of where delegated credentials are used.</span></span> <span data-ttu-id="9bfab-207">Den är mindre säker än CredSSP.</span><span class="sxs-lookup"><span data-stu-id="9bfab-207">It is less secure than CredSSP.</span></span> <span data-ttu-id="9bfab-208">Den här metoden bör endast användas för testnings scenarier.</span><span class="sxs-lookup"><span data-stu-id="9bfab-208">This method should only be used for testing scenarios.</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="9bfab-209">JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="9bfab-209">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="9bfab-210">Med JEA kan du begränsa vilka kommandon en administratör kan köra under en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="9bfab-210">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="9bfab-211">Det kan användas för att lösa det andra hopp problemet.</span><span class="sxs-lookup"><span data-stu-id="9bfab-211">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="9bfab-212">Mer information om JEA finns i [tillräckligt med administration](/powershell/scripting/learn/remoting/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="9bfab-212">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span></span>

<span data-ttu-id="9bfab-213">**Fördelar**</span><span class="sxs-lookup"><span data-stu-id="9bfab-213">**Pros**</span></span>

- <span data-ttu-id="9bfab-214">Inget lösen ords underhåll när du använder ett virtuellt konto.</span><span class="sxs-lookup"><span data-stu-id="9bfab-214">No password maintenance when using a virtual account.</span></span>

<span data-ttu-id="9bfab-215">**Nack delar**</span><span class="sxs-lookup"><span data-stu-id="9bfab-215">**Cons**</span></span>

- <span data-ttu-id="9bfab-216">Kräver WMF 5,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="9bfab-216">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="9bfab-217">Kräver konfiguration på varje mellanliggande server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="9bfab-217">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="9bfab-218">PSSessionConfiguration med RunAs</span><span class="sxs-lookup"><span data-stu-id="9bfab-218">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="9bfab-219">Du kan skapa en sessionshantering på _ServerB_ och ange dess **RunAsCredential** -parameter.</span><span class="sxs-lookup"><span data-stu-id="9bfab-219">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="9bfab-220">Information om hur du använder **PSSessionConfiguration** och **runas** för att lösa det andra hopp problemet finns i [en annan lösning på multi-hop PowerShell-fjärrkommunikation][pssessionconfig].</span><span class="sxs-lookup"><span data-stu-id="9bfab-220">For information about using **PSSessionConfiguration** and **RunAs** to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting][pssessionconfig].</span></span>

<span data-ttu-id="9bfab-221">**Fördelar**</span><span class="sxs-lookup"><span data-stu-id="9bfab-221">**Pros**</span></span>

- <span data-ttu-id="9bfab-222">Fungerar med valfri server med WMF 3,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="9bfab-222">Works with any server with WMF 3.0 or later.</span></span>

<span data-ttu-id="9bfab-223">**Nack delar**</span><span class="sxs-lookup"><span data-stu-id="9bfab-223">**Cons**</span></span>

- <span data-ttu-id="9bfab-224">Kräver konfiguration av **PSSessionConfiguration** och **runas** på varje mellanliggande server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="9bfab-224">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="9bfab-225">Kräver lösen ords underhåll när du använder ett domän konto för **runas**</span><span class="sxs-lookup"><span data-stu-id="9bfab-225">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="9bfab-226">Skicka autentiseringsuppgifter i ett Invoke-kommando skript block</span><span class="sxs-lookup"><span data-stu-id="9bfab-226">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="9bfab-227">Du kan skicka autentiseringsuppgifter i **script block** -parametern för ett anrop till cmdleten [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) .</span><span class="sxs-lookup"><span data-stu-id="9bfab-227">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

<span data-ttu-id="9bfab-228">**Fördelar**</span><span class="sxs-lookup"><span data-stu-id="9bfab-228">**Pros**</span></span>

- <span data-ttu-id="9bfab-229">Kräver ingen särskild Server konfiguration.</span><span class="sxs-lookup"><span data-stu-id="9bfab-229">Does not require special server configuration.</span></span>
- <span data-ttu-id="9bfab-230">Fungerar på alla servrar som kör WMF 2,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="9bfab-230">Works on any server running WMF 2.0 or later.</span></span>

<span data-ttu-id="9bfab-231">**Nack delar**</span><span class="sxs-lookup"><span data-stu-id="9bfab-231">**Cons**</span></span>

- <span data-ttu-id="9bfab-232">Kräver en olämplig kod teknik.</span><span class="sxs-lookup"><span data-stu-id="9bfab-232">Requires an awkward code technique.</span></span>
- <span data-ttu-id="9bfab-233">Om du kör WMF 2,0 krävs en annan syntax för att skicka argument till en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="9bfab-233">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="9bfab-234">Exempel</span><span class="sxs-lookup"><span data-stu-id="9bfab-234">Example</span></span>

<span data-ttu-id="9bfab-235">I följande exempel visas hur du skickar autentiseringsuppgifter i ett **Invoke-kommando** skript block:</span><span class="sxs-lookup"><span data-stu-id="9bfab-235">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="9bfab-236">Se även</span><span class="sxs-lookup"><span data-stu-id="9bfab-236">See also</span></span>

[<span data-ttu-id="9bfab-237">Säkerhetsöverväganden för PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="9bfab-237">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)

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
