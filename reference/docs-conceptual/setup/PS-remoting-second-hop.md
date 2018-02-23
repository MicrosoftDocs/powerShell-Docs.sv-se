---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Att göra ett andra hopp i PowerShell-fjärrkommunikation"
ms.openlocfilehash: 726b4d1b7a41e9e344347543ecde26da6547bcf3
ms.sourcegitcommit: fff6c0522508eeb408cb055ba4c9337a2759b392
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/23/2018
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="3aa88-103">Att göra ett andra hopp i PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="3aa88-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="3aa88-104">”Andra hopp problemet” refererar till en situation som liknar följande:</span><span class="sxs-lookup"><span data-stu-id="3aa88-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="3aa88-105">Du är inloggad _cypress_.</span><span class="sxs-lookup"><span data-stu-id="3aa88-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="3aa88-106">Från _cypress_, du startar en fjärrsession PowerShell att ansluta till _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="3aa88-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="3aa88-107">Ett kommando som körs på _ServerB_ via PowerShell-fjärrkommunikation session försöker få åtkomst till en resurs på _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="3aa88-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="3aa88-108">Åtkomst till resursen på _ServerC_ nekas, eftersom de autentiseringsuppgifter som du använde för att skapa PowerShell-fjärrkommunikation sessionen inte har skickats från _ServerB_ till _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="3aa88-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="3aa88-109">Det finns flera sätt att åtgärda problemet.</span><span class="sxs-lookup"><span data-stu-id="3aa88-109">There are several ways to address this problem.</span></span> <span data-ttu-id="3aa88-110">I det här avsnittet ska vi titta på flera av de mest populära lösningarna på problemet för andra hopp.</span><span class="sxs-lookup"><span data-stu-id="3aa88-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="3aa88-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="3aa88-111">CredSSP</span></span>

<span data-ttu-id="3aa88-112">Du kan använda den [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) för autentisering.</span><span class="sxs-lookup"><span data-stu-id="3aa88-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="3aa88-113">CredSSP cachelagrar autentiseringsuppgifter på fjärrservern (_ServerB_), så använder den öppnar du upp till attacker för stöld av autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="3aa88-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="3aa88-114">Om fjärrdatorn äventyras, har angriparen tillgång till användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="3aa88-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="3aa88-115">CredSSP är inaktiverat som standard på datorer som både klienten och servern.</span><span class="sxs-lookup"><span data-stu-id="3aa88-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="3aa88-116">Du bör aktivera CredSSP bara i de mest betrodda miljöerna.</span><span class="sxs-lookup"><span data-stu-id="3aa88-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="3aa88-117">Till exempel en domänadministratör ansluter till en domänkontrollant, eftersom domänkontrollanten som är betrodda.</span><span class="sxs-lookup"><span data-stu-id="3aa88-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="3aa88-118">Mer information om säkerhetsfrågor när du använder CredSSP för PowerShell-fjärrkommunikation finns [oavsiktliga Sabotage: var uppmärksam på CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="3aa88-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="3aa88-119">Läs mer om autentiseringsuppgifter stöld attacker [Mitigating Pass-the-Hash (PtH)-attacker och annan stöld av autentiseringsuppgifter](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="3aa88-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="3aa88-120">Ett exempel på hur du aktiverar och använder CredSSP för PowerShell-fjärrkommunikation finns [med CredSSP för att lösa problemet andra hopp](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="3aa88-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="3aa88-121">Fördelar</span><span class="sxs-lookup"><span data-stu-id="3aa88-121">Pros</span></span>

- <span data-ttu-id="3aa88-122">Den fungerar för alla servrar med Windows Server 2008 eller senare.</span><span class="sxs-lookup"><span data-stu-id="3aa88-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="3aa88-123">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="3aa88-123">Cons</span></span>

- <span data-ttu-id="3aa88-124">Har säkerhetsrisker.</span><span class="sxs-lookup"><span data-stu-id="3aa88-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="3aa88-125">Kräver konfiguration av både klient och server-roller.</span><span class="sxs-lookup"><span data-stu-id="3aa88-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="3aa88-126">Kerberos-delegering (obegränsad)</span><span class="sxs-lookup"><span data-stu-id="3aa88-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="3aa88-127">Du kan också användas obegränsad Kerberos-delegering för att göra ett andra hopp.</span><span class="sxs-lookup"><span data-stu-id="3aa88-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="3aa88-128">Den här metoden finns dock ingen kontroll över där delegerade autentiseringsuppgifter används.</span><span class="sxs-lookup"><span data-stu-id="3aa88-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="3aa88-129">**Obs:** Active Directory-konton som har den **kontot är känsligt och kan inte delegeras** egenskapsuppsättningen kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="3aa88-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="3aa88-130">Mer information finns i [säkerhet fokus: analys-kontot är känsligt och kan inte delegeras' för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [Kerberos-autentisering verktyg och inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="3aa88-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="3aa88-131">Fördelar</span><span class="sxs-lookup"><span data-stu-id="3aa88-131">Pros</span></span>

- <span data-ttu-id="3aa88-132">Kräver inga särskilda kodning.</span><span class="sxs-lookup"><span data-stu-id="3aa88-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="3aa88-133">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="3aa88-133">Cons</span></span>

- <span data-ttu-id="3aa88-134">Stöder inte ett andra hopp för WinRM.</span><span class="sxs-lookup"><span data-stu-id="3aa88-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="3aa88-135">Innehåller ingen kontroll över där autentiseringsuppgifter som ska användas, skapa en säkerhetsrisk.</span><span class="sxs-lookup"><span data-stu-id="3aa88-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="3aa88-136">Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="3aa88-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="3aa88-137">Du kan använda äldre begränsad delegering (inte resurs-baserat) för att göra ett andra hopp.</span><span class="sxs-lookup"><span data-stu-id="3aa88-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> 

><span data-ttu-id="3aa88-138">**Obs:** Active Directory-konton som har den **kontot är känsligt och kan inte delegeras** egenskapsuppsättningen kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="3aa88-138">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="3aa88-139">Mer information finns i [säkerhet fokus: analys-kontot är känsligt och kan inte delegeras' för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [Kerberos-autentisering verktyg och inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="3aa88-139">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="3aa88-140">Fördelar</span><span class="sxs-lookup"><span data-stu-id="3aa88-140">Pros</span></span>

- <span data-ttu-id="3aa88-141">Kräver inga särskilda kodning</span><span class="sxs-lookup"><span data-stu-id="3aa88-141">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="3aa88-142">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="3aa88-142">Cons</span></span>

- <span data-ttu-id="3aa88-143">Stöder inte ett andra hopp för WinRM.</span><span class="sxs-lookup"><span data-stu-id="3aa88-143">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="3aa88-144">Måste vara konfigurerad på Active Directory-objekt för fjärrservern (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="3aa88-144">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="3aa88-145">Begränsad till en domän.</span><span class="sxs-lookup"><span data-stu-id="3aa88-145">Limited to one domain.</span></span> <span data-ttu-id="3aa88-146">Det går inte att mellan domäner eller skogar.</span><span class="sxs-lookup"><span data-stu-id="3aa88-146">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="3aa88-147">Kräver behörighet att uppdatera objekt och tjänstens huvudnamn (SPN).</span><span class="sxs-lookup"><span data-stu-id="3aa88-147">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="3aa88-148">Resursbaserade Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="3aa88-148">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="3aa88-149">Använder resursbaserade Kerberos-begränsad delegering (introducerades i Windows Server 2012) måste du konfigurera delegering av autentiseringsuppgifter på serverobjektet där resurserna finns.</span><span class="sxs-lookup"><span data-stu-id="3aa88-149">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="3aa88-150">I det andra hopp scenariot som beskrivs ovan, konfigurerar du _ServerC_ ange från där du ska ta emot delegerade autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="3aa88-150">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="3aa88-151">**Obs:** Active Directory-konton som har den **kontot är känsligt och kan inte delegeras** egenskapsuppsättningen kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="3aa88-151">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="3aa88-152">Mer information finns i [säkerhet fokus: analys-kontot är känsligt och kan inte delegeras' för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [Kerberos-autentisering verktyg och inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="3aa88-152">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="3aa88-153">Fördelar</span><span class="sxs-lookup"><span data-stu-id="3aa88-153">Pros</span></span>

- <span data-ttu-id="3aa88-154">Autentiseringsuppgifterna lagras inte.</span><span class="sxs-lookup"><span data-stu-id="3aa88-154">Credentials are not stored.</span></span>
- <span data-ttu-id="3aa88-155">Relativt enkelt att konfigurera med PowerShell-cmdlets--inga särskilda kodning krävs.</span><span class="sxs-lookup"><span data-stu-id="3aa88-155">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="3aa88-156">Ingen speciell domänåtkomst krävs.</span><span class="sxs-lookup"><span data-stu-id="3aa88-156">No special domain access is required.</span></span>
- <span data-ttu-id="3aa88-157">Fungerar över domäner och skogar.</span><span class="sxs-lookup"><span data-stu-id="3aa88-157">Works across domains and forests.</span></span>
- <span data-ttu-id="3aa88-158">PowerShell-koden.</span><span class="sxs-lookup"><span data-stu-id="3aa88-158">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="3aa88-159">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="3aa88-159">Cons</span></span>

- <span data-ttu-id="3aa88-160">Kräver Windows Server 2012 eller senare.</span><span class="sxs-lookup"><span data-stu-id="3aa88-160">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="3aa88-161">Stöder inte ett andra hopp för WinRM.</span><span class="sxs-lookup"><span data-stu-id="3aa88-161">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="3aa88-162">Kräver behörighet att uppdatera objekt och tjänstens huvudnamn (SPN).</span><span class="sxs-lookup"><span data-stu-id="3aa88-162">Requires rights to update objects and Service Principal Names (SPNs).</span></span> 

### <a name="example"></a><span data-ttu-id="3aa88-163">Exempel</span><span class="sxs-lookup"><span data-stu-id="3aa88-163">Example</span></span>

<span data-ttu-id="3aa88-164">Nu ska vi titta på en PowerShell exempel som konfigurerar resurs utifrån begränsad delegering _ServerC_ att delegerade autentiseringsuppgifter från en _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="3aa88-164">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="3aa88-165">Det här exemplet förutsätter att alla servrar som kör Windows Server 2012 eller senare, och att det finns minst en domänkontrollant för Windows Server 2012 varje domän där någon av servrarna tillhör.</span><span class="sxs-lookup"><span data-stu-id="3aa88-165">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="3aa88-166">Innan du kan konfigurera begränsad delegering måste du lägga till den `RSAT-AD-PowerShell` funktion för att installera Active Directory PowerShell-modulen och sedan importera modulen till sessionen:</span><span class="sxs-lookup"><span data-stu-id="3aa88-166">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="3aa88-167">Nu har flera tillgängliga cmdlet: en **PrincipalsAllowedToDelegateToAccount** parameter:</span><span class="sxs-lookup"><span data-stu-id="3aa88-167">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

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

<span data-ttu-id="3aa88-168">Den **PrincipalsAllowedToDelegateToAccount** parameteruppsättningar Active Directory-objektattribut **msDS-AllowedToActOnBehalfOfOtherIdentity**, som innehåller en åtkomstkontrollista (ACL) som Anger vilka konton som har behörighet att delegera autentiseringsuppgifter för det tillhörande kontot (i vårt exempel blir datorkontot för _Server_).</span><span class="sxs-lookup"><span data-stu-id="3aa88-168">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="3aa88-169">Nu ska vi ställa in de variabler som vi använder för att representera servrar:</span><span class="sxs-lookup"><span data-stu-id="3aa88-169">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse            
$ServerA = $env:COMPUTERNAME            
$ServerB = Get-ADComputer -Identity ServerB            
$ServerC = Get-ADComputer -Identity ServerC            
```

<span data-ttu-id="3aa88-170">WinRM (och därför PowerShell-fjärrkommunikation) körs som datorkontot som standard.</span><span class="sxs-lookup"><span data-stu-id="3aa88-170">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="3aa88-171">Du kan se detta genom att titta på den **Referensdimensionerna** -egenskapen för den `winrm` tjänsten:</span><span class="sxs-lookup"><span data-stu-id="3aa88-171">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="3aa88-172">För _ServerC_ att tillåta delegering från en PowerShell-fjärrkommunikation-session på _ServerB_, vi kommer ge åtkomst genom att ange den **PrincipalsAllowedToDelegateToAccount** parametern på _ServerC_ till datorobjekt _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="3aa88-172">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation            
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB            
            
# Check the value of the attribute directly            
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity            
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access            
            
# Check the value of the attribute indirectly            
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="3aa88-173">Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) cacheminnen nekad åtkomstförsök (negativ cache) i 15 minuter.</span><span class="sxs-lookup"><span data-stu-id="3aa88-173">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="3aa88-174">Om _ServerB_ tidigare har försökt få åtkomst till _ServerC_, måste du rensa cachen på _ServerB_ genom att anropa följande kommando:</span><span class="sxs-lookup"><span data-stu-id="3aa88-174">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {            
    klist purge -li 0x3e7            
}
```

<span data-ttu-id="3aa88-175">Du kan också starta om datorn eller vänta minst 15 minuter för att rensa cachen.</span><span class="sxs-lookup"><span data-stu-id="3aa88-175">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="3aa88-176">Efter att rensa cacheminnet, du kan köra koden från _cypress_ via _ServerB_ till _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="3aa88-176">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="3aa88-177">I det här exemplet i `$using` variabeln används för att göra den `$ServerC` variabeln som är synliga för _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="3aa88-177">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="3aa88-178">Mer information om den `$using` variabel, se [about_Remote_Variables](https://technet.microsoft.com/en-us/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="3aa88-178">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/en-us/library/jj149005.aspx).</span></span>

<span data-ttu-id="3aa88-179">Gör att flera servrar att delegera autentiseringsuppgifter för att _ServerC_, ange värdet för den **PrincipalsAllowedToDelegateToAccount** parameter på _ServerC_ till en matris som:</span><span class="sxs-lookup"><span data-stu-id="3aa88-179">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="3aa88-180">Om du vill göra ett andra hopp över domäner lägger du till fullständigt kvalificerat domännamn (FQDN) på domänkontrollanten i domänen som _ServerB_ tillhör:</span><span class="sxs-lookup"><span data-stu-id="3aa88-180">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain            
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com            
$ServerC = Get-ADComputer -Identity ServerC            
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="3aa88-181">Ta bort möjligheten att delegera autentiseringsuppgifter till ServerC genom att ange värdet för den **PrincipalsAllowedToDelegateToAccount** parameter på _ServerC_ till `$null`:</span><span class="sxs-lookup"><span data-stu-id="3aa88-181">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="3aa88-182">Information om resursbaserade Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="3aa88-182">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="3aa88-183">Vad är nytt i Kerberos-autentisering</span><span class="sxs-lookup"><span data-stu-id="3aa88-183">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="3aa88-184">Hur Windows Server 2012 övergångar efter Kerberos-begränsad delegering, del 1</span><span class="sxs-lookup"><span data-stu-id="3aa88-184">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="3aa88-185">Hur Windows Server 2012 övergångar efter Kerberos-begränsad delegering, del 2</span><span class="sxs-lookup"><span data-stu-id="3aa88-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="3aa88-186">Så här fungerar Kerberos-begränsad delegering för Azure Active Directory Application Proxy-distributioner med integrerad Windows-autentisering</span><span class="sxs-lookup"><span data-stu-id="3aa88-186">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](http://aka.ms/kcdpaper)
- <span data-ttu-id="3aa88-187">[[MS-ADA2]: Active Directory-schemat attribut M2.210 attributet msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/en-us/library/hh554126.aspx)</span><span class="sxs-lookup"><span data-stu-id="3aa88-187">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/en-us/library/hh554126.aspx)</span></span>
- <span data-ttu-id="3aa88-188">[[MS-SFU]: tillägg för Kerberos-protokollet: tjänst för användare och begränsad delegering protokollet 1.3.2 S4U2proxy](https://msdn.microsoft.com/en-us/library/cc246079.aspx)</span><span class="sxs-lookup"><span data-stu-id="3aa88-188">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/en-us/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="3aa88-189">Resursen baserat Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="3aa88-189">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="3aa88-190">Fjärradministration utan begränsad delegering med PrincipalsAllowedToDelegateToAccount</span><span class="sxs-lookup"><span data-stu-id="3aa88-190">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="3aa88-191">PSSessionConfiguration med RunAs</span><span class="sxs-lookup"><span data-stu-id="3aa88-191">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="3aa88-192">Du kan skapa en sessionskonfiguration på _ServerB_ och ange dess **RunAsCredential** parameter.</span><span class="sxs-lookup"><span data-stu-id="3aa88-192">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="3aa88-193">Information om hur du använder PSSessionConfiguration och RunAs lösa andra hopp problemet finns i [en annan lösning för flera hopp PowerShell-fjärrkommunikation](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="3aa88-193">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="3aa88-194">Fördelar</span><span class="sxs-lookup"><span data-stu-id="3aa88-194">Pros</span></span>

- <span data-ttu-id="3aa88-195">Fungerar med alla servrar med WMF 3.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="3aa88-195">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="3aa88-196">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="3aa88-196">Cons</span></span>

- <span data-ttu-id="3aa88-197">Kräver konfiguration av **PSSessionConfiguration** och **RunAs** på varje server som mellanliggande (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="3aa88-197">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="3aa88-198">Kräver lösenord Underhåll när du använder en domän **RunAs** konto</span><span class="sxs-lookup"><span data-stu-id="3aa88-198">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="3aa88-199">Just Enough Administration JEA)</span><span class="sxs-lookup"><span data-stu-id="3aa88-199">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="3aa88-200">JEA kan du begränsa vilka kommandon som en administratör kan köras under en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="3aa88-200">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="3aa88-201">Den kan användas för att lösa problemet för andra hopp.</span><span class="sxs-lookup"><span data-stu-id="3aa88-201">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="3aa88-202">Information om JEA finns [bara tillräckligt Administration](https://docs.microsoft.com/en-us/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="3aa88-202">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/en-us/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="3aa88-203">Fördelar</span><span class="sxs-lookup"><span data-stu-id="3aa88-203">Pros</span></span>

- <span data-ttu-id="3aa88-204">Inget lösenord Underhåll när du använder ett virtuellt konto.</span><span class="sxs-lookup"><span data-stu-id="3aa88-204">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="3aa88-205">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="3aa88-205">Cons</span></span>

- <span data-ttu-id="3aa88-206">Kräver WMF 5.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="3aa88-206">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="3aa88-207">Kräver konfiguration på varje server som mellanliggande (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="3aa88-207">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="3aa88-208">Skicka autentiseringsuppgifterna inuti en Invoke-Command-skriptblock</span><span class="sxs-lookup"><span data-stu-id="3aa88-208">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="3aa88-209">Du kan skicka autentiseringsuppgifter i den **ScriptBlock** parametern för ett anrop till den [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3aa88-209">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="3aa88-210">Fördelar</span><span class="sxs-lookup"><span data-stu-id="3aa88-210">Pros</span></span>

- <span data-ttu-id="3aa88-211">Kräver inte särskild serverkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="3aa88-211">Does not require special server configuration.</span></span>
- <span data-ttu-id="3aa88-212">Fungerar på en server som kör WMF 2.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="3aa88-212">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="3aa88-213">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="3aa88-213">Cons</span></span>

- <span data-ttu-id="3aa88-214">Kräver en olämpliga kod-teknik.</span><span class="sxs-lookup"><span data-stu-id="3aa88-214">Requires an awkward code technique.</span></span>
- <span data-ttu-id="3aa88-215">Om du kör WMF 2.0 kräver olika syntax för att överföra argument till en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="3aa88-215">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="3aa88-216">Exempel</span><span class="sxs-lookup"><span data-stu-id="3aa88-216">Example</span></span>

<span data-ttu-id="3aa88-217">I följande exempel visas hur du skickar autentiseringsuppgifter i en **Invoke-Command** skriptblock:</span><span class="sxs-lookup"><span data-stu-id="3aa88-217">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds            
# Note $Using:Cred in nested request            
$cred = Get-Credential Contoso\Administrator            
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {            
    hostname            
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}            
}
```

## <a name="see-also"></a><span data-ttu-id="3aa88-218">Se även</span><span class="sxs-lookup"><span data-stu-id="3aa88-218">See also</span></span>

[<span data-ttu-id="3aa88-219">Säkerhetsöverväganden för PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="3aa88-219">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)








 
