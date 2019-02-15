---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Göra det andra hoppet i PowerShell-fjärrkommunikation
ms.openlocfilehash: 1b6e5ad53346324adc7be2d013e154c8600afa4f
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265594"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="7a1f7-103">Göra det andra hoppet i PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="7a1f7-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="7a1f7-104">”Andra hopp problemet” refererar till en situation som liknar följande:</span><span class="sxs-lookup"><span data-stu-id="7a1f7-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="7a1f7-105">Du är inloggad _cypress_.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="7a1f7-106">Från _cypress_, du startar en fjärrsession PowerShell att ansluta till _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="7a1f7-107">Ett kommando som körs på _ServerB_ via PowerShell-fjärrkommunikation session försöker få åtkomst till en resurs på _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="7a1f7-108">Åtkomst till resursen på _ServerC_ nekas, eftersom de autentiseringsuppgifter som du använde för att skapa PowerShell-fjärrkommunikation sessionen inte har skickats från _ServerB_ till _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="7a1f7-109">Det finns flera sätt att åtgärda problemet.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-109">There are several ways to address this problem.</span></span> <span data-ttu-id="7a1f7-110">I det här avsnittet ska vi titta på flera av de mest populära lösningarna på problemet för andra hopp.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="7a1f7-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="7a1f7-111">CredSSP</span></span>

<span data-ttu-id="7a1f7-112">Du kan använda den [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) för autentisering.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="7a1f7-113">CredSSP cachelagrar autentiseringsuppgifter på fjärrservern (_ServerB_), så använder den öppnar du upp till attacker för stöld av autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="7a1f7-114">Om fjärrdatorn äventyras, har angriparen tillgång till användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="7a1f7-115">CredSSP är inaktiverat som standard på datorer som både klienten och servern.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="7a1f7-116">Du bör aktivera CredSSP bara i de mest betrodda miljöerna.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="7a1f7-117">Till exempel en domänadministratör ansluter till en domänkontrollant, eftersom domänkontrollanten som är betrodda.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="7a1f7-118">Mer information om säkerhetsfrågor när du använder CredSSP för PowerShell-fjärrkommunikation finns [oavsiktliga Sabotage: Varning för CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="7a1f7-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="7a1f7-119">Läs mer om autentiseringsuppgifter stöld attacker [Mitigating Pass-the-Hash (PtH)-attacker och annan stöld av autentiseringsuppgifter](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="7a1f7-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="7a1f7-120">Ett exempel på hur du aktiverar och använder CredSSP för PowerShell-fjärrkommunikation finns [med CredSSP för att lösa problemet andra hopp](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="7a1f7-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="7a1f7-121">Fördelar</span><span class="sxs-lookup"><span data-stu-id="7a1f7-121">Pros</span></span>

- <span data-ttu-id="7a1f7-122">Den fungerar för alla servrar med Windows Server 2008 eller senare.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="7a1f7-123">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="7a1f7-123">Cons</span></span>

- <span data-ttu-id="7a1f7-124">Har säkerhetsrisker.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="7a1f7-125">Kräver konfiguration av både klient och server-roller.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="7a1f7-126">Kerberos-delegering (obegränsad)</span><span class="sxs-lookup"><span data-stu-id="7a1f7-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="7a1f7-127">Du kan också användas obegränsad Kerberos-delegering för att göra ett andra hopp.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="7a1f7-128">Den här metoden finns dock ingen kontroll över där delegerade autentiseringsuppgifter används.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="7a1f7-129">**Obs:** Active Directory-konton som har den **kontot är känsligt och kan inte delegeras** egenskapsuppsättningen kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="7a1f7-130">Mer information finns i [säkerhet fokus: Analys-kontot är känsligt och kan inte delegeras' för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [Kerberos-autentisering verktyg och inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="7a1f7-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="7a1f7-131">Fördelar</span><span class="sxs-lookup"><span data-stu-id="7a1f7-131">Pros</span></span>

- <span data-ttu-id="7a1f7-132">Kräver inga särskilda kodning.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="7a1f7-133">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="7a1f7-133">Cons</span></span>

- <span data-ttu-id="7a1f7-134">Stöder inte ett andra hopp för WinRM.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="7a1f7-135">Innehåller ingen kontroll över där autentiseringsuppgifter som ska användas, skapa en säkerhetsrisk.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="7a1f7-136">Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="7a1f7-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="7a1f7-137">Du kan använda äldre begränsad delegering (inte resurs-baserat) för att göra ett andra hopp.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="7a1f7-138">Konfigurera Kerberos-begränsad delegering med alternativet ”Använd valfritt autentiseringsprotokoll” så att protokollövergång.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

> [!NOTE]
> <span data-ttu-id="7a1f7-139">Active Directory-konton som har den **kontot är känsligt och kan inte delegeras** egenskapsuppsättningen kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="7a1f7-140">Mer information finns i [säkerhet fokus: Analys-kontot är känsligt och kan inte delegeras' för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [Kerberos-autentisering verktyg och inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="7a1f7-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="7a1f7-141">Fördelar</span><span class="sxs-lookup"><span data-stu-id="7a1f7-141">Pros</span></span>

- <span data-ttu-id="7a1f7-142">Kräver inga särskilda kodning</span><span class="sxs-lookup"><span data-stu-id="7a1f7-142">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="7a1f7-143">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="7a1f7-143">Cons</span></span>

- <span data-ttu-id="7a1f7-144">Stöder inte ett andra hopp för WinRM.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-144">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="7a1f7-145">Måste vara konfigurerad på Active Directory-objekt för fjärrservern (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="7a1f7-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="7a1f7-146">Begränsad till en domän.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-146">Limited to one domain.</span></span> <span data-ttu-id="7a1f7-147">Det går inte att mellan domäner eller skogar.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-147">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="7a1f7-148">Kräver behörighet att uppdatera objekt och tjänstens huvudnamn (SPN).</span><span class="sxs-lookup"><span data-stu-id="7a1f7-148">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="7a1f7-149">Resursbaserade Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="7a1f7-149">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="7a1f7-150">Använder resursbaserade Kerberos-begränsad delegering (introducerades i Windows Server 2012) måste du konfigurera delegering av autentiseringsuppgifter på serverobjektet där resurserna finns.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="7a1f7-151">I det andra hopp scenariot som beskrivs ovan, konfigurerar du _ServerC_ ange från där du ska ta emot delegerade autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="7a1f7-152">**Obs:** Active Directory-konton som har den **kontot är känsligt och kan inte delegeras** egenskapsuppsättningen kan inte delegeras.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-152">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="7a1f7-153">Mer information finns i [säkerhet fokus: Analys-kontot är känsligt och kan inte delegeras' för privilegierade konton](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) och [Kerberos-autentisering verktyg och inställningar](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="7a1f7-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="7a1f7-154">Fördelar</span><span class="sxs-lookup"><span data-stu-id="7a1f7-154">Pros</span></span>

- <span data-ttu-id="7a1f7-155">Autentiseringsuppgifterna lagras inte.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-155">Credentials are not stored.</span></span>
- <span data-ttu-id="7a1f7-156">Relativt enkelt att konfigurera med PowerShell-cmdlets--inga särskilda kodning krävs.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="7a1f7-157">Ingen speciell domänåtkomst krävs.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-157">No special domain access is required.</span></span>
- <span data-ttu-id="7a1f7-158">Fungerar över domäner och skogar.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-158">Works across domains and forests.</span></span>
- <span data-ttu-id="7a1f7-159">PowerShell-koden.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-159">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="7a1f7-160">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="7a1f7-160">Cons</span></span>

- <span data-ttu-id="7a1f7-161">Kräver Windows Server 2012 eller senare.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-161">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="7a1f7-162">Stöder inte ett andra hopp för WinRM.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-162">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="7a1f7-163">Kräver behörighet att uppdatera objekt och tjänstens huvudnamn (SPN).</span><span class="sxs-lookup"><span data-stu-id="7a1f7-163">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="7a1f7-164">Exempel</span><span class="sxs-lookup"><span data-stu-id="7a1f7-164">Example</span></span>

<span data-ttu-id="7a1f7-165">Nu ska vi titta på en PowerShell exempel som konfigurerar resurs utifrån begränsad delegering _ServerC_ att delegerade autentiseringsuppgifter från en _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="7a1f7-166">Det här exemplet förutsätter att alla servrar som kör Windows Server 2012 eller senare, och att det finns minst en domänkontrollant för Windows Server 2012 varje domän där någon av servrarna tillhör.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="7a1f7-167">Innan du kan konfigurera begränsad delegering måste du lägga till den `RSAT-AD-PowerShell` funktion för att installera Active Directory PowerShell-modulen och sedan importera modulen till sessionen:</span><span class="sxs-lookup"><span data-stu-id="7a1f7-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="7a1f7-168">Nu har flera tillgängliga cmdlet: en **PrincipalsAllowedToDelegateToAccount** parameter:</span><span class="sxs-lookup"><span data-stu-id="7a1f7-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

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

<span data-ttu-id="7a1f7-169">Den **PrincipalsAllowedToDelegateToAccount** parameteruppsättningar Active Directory-objektattribut **msDS-AllowedToActOnBehalfOfOtherIdentity**, som innehåller en åtkomstkontrollista (ACL) som Anger vilka konton som har behörighet att delegera autentiseringsuppgifter för det tillhörande kontot (i vårt exempel blir datorkontot för _Server_).</span><span class="sxs-lookup"><span data-stu-id="7a1f7-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="7a1f7-170">Nu ska vi ställa in de variabler som vi använder för att representera servrar:</span><span class="sxs-lookup"><span data-stu-id="7a1f7-170">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="7a1f7-171">WinRM (och därför PowerShell-fjärrkommunikation) körs som datorkontot som standard.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="7a1f7-172">Du kan se detta genom att titta på den **Referensdimensionerna** -egenskapen för den `winrm` tjänsten:</span><span class="sxs-lookup"><span data-stu-id="7a1f7-172">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="7a1f7-173">För _ServerC_ att tillåta delegering från en PowerShell-fjärrkommunikation-session på _ServerB_, vi kommer ge åtkomst genom att ange den **PrincipalsAllowedToDelegateToAccount** parametern på _ServerC_ till datorobjekt _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="7a1f7-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="7a1f7-174">Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) cacheminnen nekad åtkomstförsök (negativ cache) i 15 minuter.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-174">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="7a1f7-175">Om _ServerB_ tidigare har försökt få åtkomst till _ServerC_, måste du rensa cachen på _ServerB_ genom att anropa följande kommando:</span><span class="sxs-lookup"><span data-stu-id="7a1f7-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="7a1f7-176">Du kan också starta om datorn eller vänta minst 15 minuter för att rensa cachen.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="7a1f7-177">Efter att rensa cacheminnet, du kan köra koden från _cypress_ via _ServerB_ till _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="7a1f7-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="7a1f7-178">I det här exemplet i `$using` variabeln används för att göra den `$ServerC` variabeln som är synliga för _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="7a1f7-179">Mer information om den `$using` variabel, se [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="7a1f7-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="7a1f7-180">Gör att flera servrar att delegera autentiseringsuppgifter för att _ServerC_, ange värdet för den **PrincipalsAllowedToDelegateToAccount** parameter på _ServerC_ till en matris som:</span><span class="sxs-lookup"><span data-stu-id="7a1f7-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="7a1f7-181">Om du vill göra ett andra hopp över domäner lägger du till fullständigt kvalificerat domännamn (FQDN) på domänkontrollanten i domänen som _ServerB_ tillhör:</span><span class="sxs-lookup"><span data-stu-id="7a1f7-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="7a1f7-182">Ta bort möjligheten att delegera autentiseringsuppgifter till ServerC genom att ange värdet för den **PrincipalsAllowedToDelegateToAccount** parameter på _ServerC_ till `$null`:</span><span class="sxs-lookup"><span data-stu-id="7a1f7-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="7a1f7-183">Information om resursbaserade Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="7a1f7-183">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="7a1f7-184">Vad är nytt i Kerberos-autentisering</span><span class="sxs-lookup"><span data-stu-id="7a1f7-184">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="7a1f7-185">Hur Windows Server 2012 övergångar efter Kerberos-begränsad delegering, del 1</span><span class="sxs-lookup"><span data-stu-id="7a1f7-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="7a1f7-186">Hur Windows Server 2012 övergångar efter Kerberos-begränsad delegering, del 2</span><span class="sxs-lookup"><span data-stu-id="7a1f7-186">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="7a1f7-187">Så här fungerar Kerberos-begränsad delegering för Azure Active Directory Application Proxy-distributioner med integrerad Windows-autentisering</span><span class="sxs-lookup"><span data-stu-id="7a1f7-187">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](https://aka.ms/kcdpaper)
- <span data-ttu-id="7a1f7-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span><span class="sxs-lookup"><span data-stu-id="7a1f7-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span></span>
- <span data-ttu-id="7a1f7-189">[[MS-SFU]: Tillägg för Kerberos-protokollet: Tjänst för användare och begränsad delegering protokollet 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span><span class="sxs-lookup"><span data-stu-id="7a1f7-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="7a1f7-190">Resursen baserat Kerberos-begränsad delegering</span><span class="sxs-lookup"><span data-stu-id="7a1f7-190">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="7a1f7-191">Fjärradministration utan begränsad delegering med PrincipalsAllowedToDelegateToAccount</span><span class="sxs-lookup"><span data-stu-id="7a1f7-191">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="7a1f7-192">PSSessionConfiguration med RunAs</span><span class="sxs-lookup"><span data-stu-id="7a1f7-192">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="7a1f7-193">Du kan skapa en sessionskonfiguration på _ServerB_ och ange dess **RunAsCredential** parameter.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-193">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="7a1f7-194">Information om hur du använder PSSessionConfiguration och RunAs lösa andra hopp problemet finns i [en annan lösning för flera hopp PowerShell-fjärrkommunikation](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="7a1f7-194">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="7a1f7-195">Fördelar</span><span class="sxs-lookup"><span data-stu-id="7a1f7-195">Pros</span></span>

- <span data-ttu-id="7a1f7-196">Fungerar med alla servrar med WMF 3.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-196">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="7a1f7-197">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="7a1f7-197">Cons</span></span>

- <span data-ttu-id="7a1f7-198">Kräver konfiguration av **PSSessionConfiguration** och **RunAs** på varje server som mellanliggande (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="7a1f7-198">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="7a1f7-199">Kräver lösenord Underhåll när du använder en domän **RunAs** konto</span><span class="sxs-lookup"><span data-stu-id="7a1f7-199">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="7a1f7-200">JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="7a1f7-200">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="7a1f7-201">JEA kan du begränsa vilka kommandon som en administratör kan köras under en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-201">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="7a1f7-202">Den kan användas för att lösa problemet för andra hopp.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-202">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="7a1f7-203">Information om JEA finns [bara tillräckligt Administration](https://docs.microsoft.com/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="7a1f7-203">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="7a1f7-204">Fördelar</span><span class="sxs-lookup"><span data-stu-id="7a1f7-204">Pros</span></span>

- <span data-ttu-id="7a1f7-205">Inget lösenord Underhåll när du använder ett virtuellt konto.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-205">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="7a1f7-206">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="7a1f7-206">Cons</span></span>

- <span data-ttu-id="7a1f7-207">Kräver WMF 5.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-207">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="7a1f7-208">Kräver konfiguration på varje server som mellanliggande (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="7a1f7-208">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="7a1f7-209">Skicka autentiseringsuppgifterna inuti en Invoke-Command-skriptblock</span><span class="sxs-lookup"><span data-stu-id="7a1f7-209">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="7a1f7-210">Du kan skicka autentiseringsuppgifter i den **ScriptBlock** parametern för ett anrop till den [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-210">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="7a1f7-211">Fördelar</span><span class="sxs-lookup"><span data-stu-id="7a1f7-211">Pros</span></span>

- <span data-ttu-id="7a1f7-212">Kräver inte särskild serverkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-212">Does not require special server configuration.</span></span>
- <span data-ttu-id="7a1f7-213">Fungerar på en server som kör WMF 2.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-213">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="7a1f7-214">Nackdelar</span><span class="sxs-lookup"><span data-stu-id="7a1f7-214">Cons</span></span>

- <span data-ttu-id="7a1f7-215">Kräver en olämpliga kod-teknik.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-215">Requires an awkward code technique.</span></span>
- <span data-ttu-id="7a1f7-216">Om du kör WMF 2.0 kräver olika syntax för att överföra argument till en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="7a1f7-216">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="7a1f7-217">Exempel</span><span class="sxs-lookup"><span data-stu-id="7a1f7-217">Example</span></span>

<span data-ttu-id="7a1f7-218">I följande exempel visas hur du skickar autentiseringsuppgifter i en **Invoke-Command** skriptblock:</span><span class="sxs-lookup"><span data-stu-id="7a1f7-218">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="7a1f7-219">Se även</span><span class="sxs-lookup"><span data-stu-id="7a1f7-219">See also</span></span>

[<span data-ttu-id="7a1f7-220">Säkerhetsöverväganden för PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="7a1f7-220">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)
