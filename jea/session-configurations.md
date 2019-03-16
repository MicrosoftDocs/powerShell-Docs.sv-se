---
ms.date: 06/12/2017
keywords: jea, powershell, säkerhet
title: JEA Sessionskonfigurationer
ms.openlocfilehash: b98726ea7ed3aabdfd05034c3b70118e327160cd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056608"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="22f69-103">JEA Sessionskonfigurationer</span><span class="sxs-lookup"><span data-stu-id="22f69-103">JEA Session Configurations</span></span>

> <span data-ttu-id="22f69-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="22f69-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="22f69-105">En JEA-slutpunkt har registrerats i ett system genom att skapa och registrera en konfigurationsfil för PowerShell-session på ett visst sätt.</span><span class="sxs-lookup"><span data-stu-id="22f69-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="22f69-106">Sessionskonfigurationer fastställa *som* kan använda JEA-slutpunkt och vilka roller de har åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="22f69-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="22f69-107">De kan också definiera globala inställningar som gäller för användare av en roll i JEA-session.</span><span class="sxs-lookup"><span data-stu-id="22f69-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="22f69-108">Det här avsnittet beskriver hur du skapar en konfigurationsfil för PowerShell-session och registrera en JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="22f69-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="22f69-109">Skapa en konfigurationsfil för session</span><span class="sxs-lookup"><span data-stu-id="22f69-109">Create a session configuration file</span></span>

<span data-ttu-id="22f69-110">Du måste ange hur att slutpunkten ska konfigureras för att registrera en JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="22f69-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="22f69-111">Det finns många alternativ att överväga här det viktigaste för vilka som ska ha åtkomst till JEA-slutpunkt, vilka roller kommer de tilldelas, vilken identitet JEA använder under försättsbladen och vad är namnet på JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="22f69-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="22f69-112">Dessa definieras i en PowerShell-session konfigurationsfil, vilket är en PowerShell-datafil som slutar med filnamnstillägget .pssc.</span><span class="sxs-lookup"><span data-stu-id="22f69-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="22f69-113">Kör följande kommando för att skapa en konfigurationsfil för stommen session för JEA-slutpunkter.</span><span class="sxs-lookup"><span data-stu-id="22f69-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="22f69-114">Endast de vanligaste konfigurationsalternativ som ingår i filen stommen som standard.</span><span class="sxs-lookup"><span data-stu-id="22f69-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="22f69-115">Använd den `-Full` växel för att ta med alla tillämpliga inställningar i den genererade PSSC.</span><span class="sxs-lookup"><span data-stu-id="22f69-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="22f69-116">Du kan öppna konfigurationsfilen session i en textredigerare.</span><span class="sxs-lookup"><span data-stu-id="22f69-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="22f69-117">Den `-SessionType RestrictedRemoteServer` fält anger att sessionskonfigurationen ska användas av JEA för säker hantering.</span><span class="sxs-lookup"><span data-stu-id="22f69-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="22f69-118">Sessioner som konfigureras på det här sättet kommer att fungera i [NoLanguage läge](https://technet.microsoft.com/library/dn433292.aspx) och får bara innehålla följande standardkommandon för 8 (och alias) tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="22f69-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="22f69-119">Clear-värd (cls, rensa)</span><span class="sxs-lookup"><span data-stu-id="22f69-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="22f69-120">Avsluta-PSSession (exsn, avsluta)</span><span class="sxs-lookup"><span data-stu-id="22f69-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="22f69-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="22f69-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="22f69-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="22f69-122">Get-FormatData</span></span>
- <span data-ttu-id="22f69-123">Get-Help</span><span class="sxs-lookup"><span data-stu-id="22f69-123">Get-Help</span></span>
- <span data-ttu-id="22f69-124">Måttobjektet (mått)</span><span class="sxs-lookup"><span data-stu-id="22f69-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="22f69-125">Out-Default</span><span class="sxs-lookup"><span data-stu-id="22f69-125">Out-Default</span></span>
- <span data-ttu-id="22f69-126">Select-Object (Välj)</span><span class="sxs-lookup"><span data-stu-id="22f69-126">Select-Object (select)</span></span>

<span data-ttu-id="22f69-127">Inga PowerShell-providers är tillgängliga, och inte heller några externa program (körbara filer, skript osv.).</span><span class="sxs-lookup"><span data-stu-id="22f69-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="22f69-128">Det finns flera andra fält som du vill konfigurera för JEA-sessionen.</span><span class="sxs-lookup"><span data-stu-id="22f69-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="22f69-129">De beskrivs i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="22f69-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="22f69-130">Välj JEA-identitet</span><span class="sxs-lookup"><span data-stu-id="22f69-130">Choose the JEA identity</span></span>

<span data-ttu-id="22f69-131">JEA måste en identitet (konto) du använder när du kör en anslutna användare kommandon i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="22f69-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="22f69-132">Du bestämmer dig för vilken identitet JEA används i konfigurationsfilen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="22f69-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="22f69-133">Lokala virtuellt konto</span><span class="sxs-lookup"><span data-stu-id="22f69-133">Local Virtual Account</span></span>

<span data-ttu-id="22f69-134">Om de roller som stöds av den här JEA-slutpunkt används för att hantera den lokala datorn och ett lokalt administratörskonto räcker för att köra kommandona har, bör du konfigurera JEA om du vill använda ett lokalt virtuellt konto.</span><span class="sxs-lookup"><span data-stu-id="22f69-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands successfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="22f69-135">Virtuella konton är tillfälliga konton som är unika för en viss användare och endast senaste under av sina PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="22f69-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="22f69-136">På en medlemsserver eller arbetsstation virtuella konton som hör till den lokala datorn **administratörer** gruppen och har åtkomst till de flesta systemresurser.</span><span class="sxs-lookup"><span data-stu-id="22f69-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="22f69-137">På en Active Directory-domänkontrollant, virtuella konton tillhör domänens **Domänadministratörer** grupp.</span><span class="sxs-lookup"><span data-stu-id="22f69-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="22f69-138">Om de roller som stöds av sessionskonfigurationen inte behöver sådan bred privilegier, kan du ange de säkerhetsgrupper som virtuellt konto ska tillhöra.</span><span class="sxs-lookup"><span data-stu-id="22f69-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="22f69-139">De angivna säkerhetsgrupperna måste vara lokala grupper, inte grupper från en domän på en medlemsserver eller arbetsstation.</span><span class="sxs-lookup"><span data-stu-id="22f69-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="22f69-140">När du anger en eller flera säkerhetsgrupper virtuellt konto kommer inte längre tillhör gruppen lokala administratörer.</span><span class="sxs-lookup"><span data-stu-id="22f69-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="22f69-141">Virtuella konton beviljas tillfälligt inloggningen som en tjänst direkt i den lokala server säkerhetsprincipen.</span><span class="sxs-lookup"><span data-stu-id="22f69-141">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span>  <span data-ttu-id="22f69-142">Om en av VirtualAccountGroups som angetts har redan beviljats den här behörigheten i principen, kommer inte längre individuella virtuella konto har lagts till och tas bort från principen.</span><span class="sxs-lookup"><span data-stu-id="22f69-142">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span>  <span data-ttu-id="22f69-143">Detta kan vara användbart i scenarier, till exempel domänkontrollanter där ändringar i den säkerhetsprincip för domänkontrollanter granskas noggrant.</span><span class="sxs-lookup"><span data-stu-id="22f69-143">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span>  <span data-ttu-id="22f69-144">Detta är endast tillgängligt i Windows Server 2016 med November 2018 eller senare samlad och Windows Server 2019 med januari 2019 eller senare samlad.</span><span class="sxs-lookup"><span data-stu-id="22f69-144">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="22f69-145">Grupphanterat tjänstkonto</span><span class="sxs-lookup"><span data-stu-id="22f69-145">Group Managed Service Account</span></span>


<span data-ttu-id="22f69-146">För scenarier som kräver JEA-användare att komma åt nätverksresurser, till exempel andra datorer eller webbtjänster, är ett grupphanterade tjänstkonto (gMSA) en lämpligare identitet för att använda.</span><span class="sxs-lookup"><span data-stu-id="22f69-146">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="22f69-147">gMSA-konton får du en domänidentitet som kan användas för att autentisera mot resurser på en dator i domänen.</span><span class="sxs-lookup"><span data-stu-id="22f69-147">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="22f69-148">Rättigheterna i gMSA ger du bestäms av resurserna som du ansluter till.</span><span class="sxs-lookup"><span data-stu-id="22f69-148">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="22f69-149">Du har automatiskt inte administratörsrättigheter på alla datorer eller tjänster, såvida inte datorn/tjänstadministratören har uttryckligen beviljat gMSA-kontot administratörsprivilegier.</span><span class="sxs-lookup"><span data-stu-id="22f69-149">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="22f69-150">gMSA-konton bör endast användas när åtkomst till nätverksresurser krävs olika orsaker:</span><span class="sxs-lookup"><span data-stu-id="22f69-150">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="22f69-151">Det är svårare att spåra tillbaka åtgärder för att en användare när du använder ett konto för gMSA eftersom alla användare delar samma kör som-identitet.</span><span class="sxs-lookup"><span data-stu-id="22f69-151">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="22f69-152">Behöver du PowerShell-session betyg och loggar för att korrelera användare med sina åtgärder.</span><span class="sxs-lookup"><span data-stu-id="22f69-152">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="22f69-153">GMSA-kontot kan ha åtkomst till många nätverksresurser som anslutande användaren inte behöver åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="22f69-153">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="22f69-154">Försök alltid att begränsa gällande behörigheter i en JEA-session för att följa principen om lägsta behörighet.</span><span class="sxs-lookup"><span data-stu-id="22f69-154">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="22f69-155">Gruppen hanterade tjänstkonton är endast tillgängliga i Windows PowerShell 5.1 eller senare och på domänanslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="22f69-155">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>

#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="22f69-156">Mer information om Kör som-användare</span><span class="sxs-lookup"><span data-stu-id="22f69-156">More information about run as users</span></span>

<span data-ttu-id="22f69-157">Mer information om Kör som identiteter och hur de ta med i säkerheten i en JEA-session finns i den [säkerhetsöverväganden](security-considerations.md) artikeln.</span><span class="sxs-lookup"><span data-stu-id="22f69-157">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="22f69-158">Sessionen avskrifter</span><span class="sxs-lookup"><span data-stu-id="22f69-158">Session transcripts</span></span>

<span data-ttu-id="22f69-159">Vi rekommenderar att du konfigurerar en konfigurationsfil för JEA-sessionen att registreras automatiskt avskrifter av användarnas sessioner.</span><span class="sxs-lookup"><span data-stu-id="22f69-159">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="22f69-160">PowerShell-session avskrifter innehåller information om den anslutande användaren, kör som-identiteten som tilldelats dem, och kommandona som körs av användaren.</span><span class="sxs-lookup"><span data-stu-id="22f69-160">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="22f69-161">De kan vara praktiskt att en granskning team som behöver förstå vem som utförde en viss ändring av ett system.</span><span class="sxs-lookup"><span data-stu-id="22f69-161">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="22f69-162">Ange en sökväg till en mapp där avskrifter ska sparas för att konfigurera automatisk avskrift i konfigurationsfilen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="22f69-162">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="22f69-163">Den angivna mappen ska konfigureras för att hindra användare från att ändra eller ta bort alla data i den.</span><span class="sxs-lookup"><span data-stu-id="22f69-163">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="22f69-164">Avskrifter skrivs till mappen som kontot Lokalt System, vilket kräver Läs- och skrivåtkomst till katalogen.</span><span class="sxs-lookup"><span data-stu-id="22f69-164">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="22f69-165">Vanliga användare bör inte ha åtkomst till mappen och en begränsad uppsättning säkerhetsadministratörer ska ha åtkomst till att granska avskrifter.</span><span class="sxs-lookup"><span data-stu-id="22f69-165">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="22f69-166">Enheten</span><span class="sxs-lookup"><span data-stu-id="22f69-166">User drive</span></span>

<span data-ttu-id="22f69-167">Om dina anslutande användare behöver att kopiera filer till och från JEA-slutpunkt för att köra ett kommando, kan du aktivera enheten i konfigurationsfilen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="22f69-167">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="22f69-168">Användare-enheten är en [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) som är mappad till en unik mapp för varje anslutande användaren.</span><span class="sxs-lookup"><span data-stu-id="22f69-168">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="22f69-169">Den här mappen fungerar som ett utrymme att kopiera filer till och från systemet, utan att ge dem åtkomst till filsystemet fullständig eller exponera filsystem-providern.</span><span class="sxs-lookup"><span data-stu-id="22f69-169">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="22f69-170">Användarens enhet innehållet är beständiga mellan sessioner för situationer där nätverksanslutningen kan avbrytas.</span><span class="sxs-lookup"><span data-stu-id="22f69-170">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="22f69-171">Som standard kan på enheten du lagra upp till 50MB data per användare.</span><span class="sxs-lookup"><span data-stu-id="22f69-171">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="22f69-172">Du kan begränsa mängden data som en användare kan använda med den *UserDriveMaximumSize* fält.</span><span class="sxs-lookup"><span data-stu-id="22f69-172">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="22f69-173">Om du inte vill att data i användarens enhet ska vara beständig, kan du konfigurera en schemalagd aktivitet på systemet att automatiskt Rensa mappen varje natt.</span><span class="sxs-lookup"><span data-stu-id="22f69-173">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="22f69-174">Användare-enheten är endast tillgängliga i Windows PowerShell 5.1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="22f69-174">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="22f69-175">Rolldefinitioner</span><span class="sxs-lookup"><span data-stu-id="22f69-175">Role definitions</span></span>

<span data-ttu-id="22f69-176">Rolldefinitioner i en konfigurationsfil för sessionen definierar mappningen av *användare* till *roller*.</span><span class="sxs-lookup"><span data-stu-id="22f69-176">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="22f69-177">Varje användare eller grupp som ingår i det här fältet kommer automatiskt att beviljas behörighet att JEA-slutpunkt när den är registrerad.</span><span class="sxs-lookup"><span data-stu-id="22f69-177">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="22f69-178">Varje användare eller grupp kan ingå som en nyckel i hash-tabellen bara en gång, men kan tilldelas flera roller.</span><span class="sxs-lookup"><span data-stu-id="22f69-178">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="22f69-179">Namnet på rollen funktionen ska vara namnet på rollen kapaciteten för filen, utan tillägget .psrc.</span><span class="sxs-lookup"><span data-stu-id="22f69-179">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="22f69-180">Om en användare tillhör mer än en grupp i rolldefinitionen kan får de åtkomst till roller för var och en.</span><span class="sxs-lookup"><span data-stu-id="22f69-180">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="22f69-181">Om två roller ger åtkomst till samma cmdlets kan beviljas den mest Tillåtande parameteruppsättningen för användaren.</span><span class="sxs-lookup"><span data-stu-id="22f69-181">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="22f69-182">När du anger lokala användare eller grupper i rollen definitioner fältet, måste du använda namnet på datorn (inte *localhost* eller *.*) innan den omvänt snedstrecken.</span><span class="sxs-lookup"><span data-stu-id="22f69-182">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="22f69-183">Du hittar namnet på datorn genom att kontrollera den `$env:computername` variabeln.</span><span class="sxs-lookup"><span data-stu-id="22f69-183">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="22f69-184">Sökordning för roll-funktion</span><span class="sxs-lookup"><span data-stu-id="22f69-184">Role capability search order</span></span>

<span data-ttu-id="22f69-185">I exemplet ovan visas rollfunktioner refereras av filens roll funktionen fast namn (filnamn utan filtillägget).</span><span class="sxs-lookup"><span data-stu-id="22f69-185">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="22f69-186">Om flera rollfunktioner är tillgängliga på datorn med samma fast namn, använder PowerShell dess implicita ordning för att markera filen effektiva roll funktionen.</span><span class="sxs-lookup"><span data-stu-id="22f69-186">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="22f69-187">Kommer det att **inte** ge åtkomst till alla roll funktionsfiler med samma namn.</span><span class="sxs-lookup"><span data-stu-id="22f69-187">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="22f69-188">JEA använder den `$env:PSModulePath` miljövariabeln för att avgöra vilka sökvägar kan du söka efter roll funktionsfiler.</span><span class="sxs-lookup"><span data-stu-id="22f69-188">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="22f69-189">I var och en av dessa sökvägar söker JEA efter giltiga PowerShell-moduler som innehåller en undermapp som ”RoleCapabilities”.</span><span class="sxs-lookup"><span data-stu-id="22f69-189">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="22f69-190">Precis som med importerar moduler, föredrar JEA rollfunktioner som medföljer Windows till den anpassade rollen funktionerna med samma namn.</span><span class="sxs-lookup"><span data-stu-id="22f69-190">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="22f69-191">För andra namnkonflikter bestäms prioritet av den ordning som räknar Windows upp filerna i katalogen (inte nödvändigtvis i alfabetisk ordning).</span><span class="sxs-lookup"><span data-stu-id="22f69-191">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="22f69-192">Den första roll funktionen filen hittades som matchar önskat namn ska användas för den anslutande användaren.</span><span class="sxs-lookup"><span data-stu-id="22f69-192">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="22f69-193">Eftersom sökordningen för roll-funktionen är inte deterministisk när två eller fler rollfunktioner har samma namn, är det **rekommenderar vi** du se till rollfunktioner har unika namn på din dator.</span><span class="sxs-lookup"><span data-stu-id="22f69-193">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="22f69-194">Regler för villkorlig åtkomst</span><span class="sxs-lookup"><span data-stu-id="22f69-194">Conditional access rules</span></span>

<span data-ttu-id="22f69-195">Alla användare och grupper som ingår i fältet RoleDefinitions beviljas automatiskt åtkomst till JEA-slutpunkter.</span><span class="sxs-lookup"><span data-stu-id="22f69-195">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="22f69-196">Regler för villkorlig åtkomst kan du förfina den här åtkomsten och Kräv att användare ska tillhöra ytterligare säkerhetsgrupper som inte påverkar de roller som de är tilldelade.</span><span class="sxs-lookup"><span data-stu-id="22f69-196">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="22f69-197">Detta kan vara användbart om du vill integrera ”just in-time” privilegierad åtkomst till hanteringslösningen, autentisering med smartkort eller andra Multi-Factor authentication-lösning med JEA.</span><span class="sxs-lookup"><span data-stu-id="22f69-197">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="22f69-198">Regler för villkorlig åtkomst har definierats i fältet RequiredGroups i en konfigurationsfil för sessionen.</span><span class="sxs-lookup"><span data-stu-id="22f69-198">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="22f69-199">Där kan du ange en hash-tabell (du kan också kapslade) som använder ”och” och ”eller” för att skapa dina regler.</span><span class="sxs-lookup"><span data-stu-id="22f69-199">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="22f69-200">Här följer några exempel på hur du kan använda det här fältet:</span><span class="sxs-lookup"><span data-stu-id="22f69-200">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> <span data-ttu-id="22f69-201">Regler för villkorlig åtkomst är bara tillgängliga i Windows PowerShell 5.1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="22f69-201">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="22f69-202">Andra egenskaper</span><span class="sxs-lookup"><span data-stu-id="22f69-202">Other properties</span></span>

<span data-ttu-id="22f69-203">Sessionen konfigurationsfiler kan också göra allt en roll funktionen fil kan göra, men utan möjlighet att ge den anslutande användare åtkomst till olika kommandon.</span><span class="sxs-lookup"><span data-stu-id="22f69-203">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="22f69-204">Om du vill tillåta alla användare åtkomst till specifika cmdlet: ar, funktioner eller leverantörer kan du göra det direkt i konfigurationsfilen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="22f69-204">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="22f69-205">En fullständig lista över egenskaper som stöds i konfigurationsfilen session kör `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="22f69-205">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="22f69-206">Testa en konfigurationsfil för session</span><span class="sxs-lookup"><span data-stu-id="22f69-206">Testing a session configuration file</span></span>

<span data-ttu-id="22f69-207">Du kan testa en session konfiguration med hjälp av den [Test PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="22f69-207">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="22f69-208">Vi rekommenderar starkt att du testar din session-konfigurationsfil om du har redigerat filen pssc manuellt med hjälp av en textredigerare så syntaxen är korrekt.</span><span class="sxs-lookup"><span data-stu-id="22f69-208">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="22f69-209">Om en session konfigurationsfil inte skickar det här testet, kan den inte har registreras i systemet.</span><span class="sxs-lookup"><span data-stu-id="22f69-209">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="22f69-210">Exempelkonfigurationsfil för session</span><span class="sxs-lookup"><span data-stu-id="22f69-210">Sample session configuration file</span></span>

<span data-ttu-id="22f69-211">Nedan visas ett komplett exempel som visar hur du skapar och validerar en sessionskonfiguration för JEA.</span><span class="sxs-lookup"><span data-stu-id="22f69-211">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="22f69-212">Observera att rolldefinitionerna skapas och lagras i den `$roles` variabeln för bekvämlighets skull och läsbarhet.</span><span class="sxs-lookup"><span data-stu-id="22f69-212">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="22f69-213">Det är inte ett krav att göra detta.</span><span class="sxs-lookup"><span data-stu-id="22f69-213">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="22f69-214">Uppdaterar sessionen konfigurationsfiler</span><span class="sxs-lookup"><span data-stu-id="22f69-214">Updating session configuration files</span></span>

<span data-ttu-id="22f69-215">Om du behöver ändra egenskaperna för en JEA-sessionskonfiguration, inklusive mappningen av användare till roller måste du [avregistrera](register-jea.md#unregistering-jea-configurations) och [Omregistrera](register-jea.md) JEA-sessionskonfiguration.</span><span class="sxs-lookup"><span data-stu-id="22f69-215">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="22f69-216">När du registrera JEA sessionskonfigurationen kan du använda en uppdaterad PowerShell-session configuration-fil som innehåller dina önskade ändringar.</span><span class="sxs-lookup"><span data-stu-id="22f69-216">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="22f69-217">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="22f69-217">Next steps</span></span>

- [<span data-ttu-id="22f69-218">Registrera en JEA-konfiguration</span><span class="sxs-lookup"><span data-stu-id="22f69-218">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="22f69-219">Författare JEA roller</span><span class="sxs-lookup"><span data-stu-id="22f69-219">Author JEA roles</span></span>](role-capabilities.md)
