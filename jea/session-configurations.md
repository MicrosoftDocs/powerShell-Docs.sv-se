---
ms.date: 07/10/2019
keywords: jea, powershell, säkerhet
title: JEA Sessionskonfigurationer
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726544"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="39ac6-103">JEA Sessionskonfigurationer</span><span class="sxs-lookup"><span data-stu-id="39ac6-103">JEA Session Configurations</span></span>

<span data-ttu-id="39ac6-104">En JEA-slutpunkt har registrerats i ett system genom att skapa och registrera en konfigurationsfil för PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="39ac6-104">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="39ac6-105">Sessionskonfigurationer definierar vem som kan använda JEA-slutpunkt och vilka roller som de har åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="39ac6-105">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="39ac6-106">De kan också definiera globala inställningar som gäller för alla användare av den JEA-sessionen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-106">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="39ac6-107">Skapa en konfigurationsfil för session</span><span class="sxs-lookup"><span data-stu-id="39ac6-107">Create a session configuration file</span></span>

<span data-ttu-id="39ac6-108">Du måste ange hur att slutpunkten är konfigurerad för att registrera en JEA-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="39ac6-108">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="39ac6-109">Det finns många alternativ att överväga.</span><span class="sxs-lookup"><span data-stu-id="39ac6-109">There are many options to consider.</span></span> <span data-ttu-id="39ac6-110">De viktigaste alternativen är:</span><span class="sxs-lookup"><span data-stu-id="39ac6-110">The most important options are:</span></span>

- <span data-ttu-id="39ac6-111">Vem har tillgång till JEA-slutpunkt</span><span class="sxs-lookup"><span data-stu-id="39ac6-111">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="39ac6-112">Vilka roller som de tilldelas</span><span class="sxs-lookup"><span data-stu-id="39ac6-112">Which roles they be assigned</span></span>
- <span data-ttu-id="39ac6-113">Vilken identitet JEA använder under försättsbladen</span><span class="sxs-lookup"><span data-stu-id="39ac6-113">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="39ac6-114">Namnet på JEA-slutpunkt</span><span class="sxs-lookup"><span data-stu-id="39ac6-114">The name of the JEA endpoint</span></span>

<span data-ttu-id="39ac6-115">De här alternativen har definierats i en PowerShell-datafilen med en `.pssc` tillägg som kallas en konfigurationsfil för PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="39ac6-115">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="39ac6-116">Konfigurationsfilen session kan redigeras med valfri textredigerare.</span><span class="sxs-lookup"><span data-stu-id="39ac6-116">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="39ac6-117">Kör följande kommando för att skapa en tom mall-konfigurationsfil.</span><span class="sxs-lookup"><span data-stu-id="39ac6-117">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="39ac6-118">Endast de vanligaste konfigurationsalternativ ingår i mallfilen som standard.</span><span class="sxs-lookup"><span data-stu-id="39ac6-118">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="39ac6-119">Använd den `-Full` växel för att ta med alla tillämpliga inställningar i den genererade PSSC.</span><span class="sxs-lookup"><span data-stu-id="39ac6-119">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="39ac6-120">Den `-SessionType RestrictedRemoteServer` fält anger att sessionskonfigurationen används av JEA för säker hantering.</span><span class="sxs-lookup"><span data-stu-id="39ac6-120">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="39ac6-121">Sessioner av den här typen fungera i **NoLanguage** läge och endast har åtkomst till följande standardkommandon för (och alias):</span><span class="sxs-lookup"><span data-stu-id="39ac6-121">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="39ac6-122">Clear-värd (cls, rensa)</span><span class="sxs-lookup"><span data-stu-id="39ac6-122">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="39ac6-123">Avsluta-PSSession (exsn, avsluta)</span><span class="sxs-lookup"><span data-stu-id="39ac6-123">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="39ac6-124">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="39ac6-124">Get-Command (gcm)</span></span>
- <span data-ttu-id="39ac6-125">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="39ac6-125">Get-FormatData</span></span>
- <span data-ttu-id="39ac6-126">Get-Help</span><span class="sxs-lookup"><span data-stu-id="39ac6-126">Get-Help</span></span>
- <span data-ttu-id="39ac6-127">Måttobjektet (mått)</span><span class="sxs-lookup"><span data-stu-id="39ac6-127">Measure-Object (measure)</span></span>
- <span data-ttu-id="39ac6-128">Out-Default</span><span class="sxs-lookup"><span data-stu-id="39ac6-128">Out-Default</span></span>
- <span data-ttu-id="39ac6-129">Select-Object (Välj)</span><span class="sxs-lookup"><span data-stu-id="39ac6-129">Select-Object (select)</span></span>

<span data-ttu-id="39ac6-130">Inga PowerShell-providers är tillgängliga, och inte heller några externa program (körbara filer eller skript).</span><span class="sxs-lookup"><span data-stu-id="39ac6-130">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="39ac6-131">Mer information om lägena för språk finns i [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span><span class="sxs-lookup"><span data-stu-id="39ac6-131">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="39ac6-132">Välj JEA-identitet</span><span class="sxs-lookup"><span data-stu-id="39ac6-132">Choose the JEA identity</span></span>

<span data-ttu-id="39ac6-133">JEA måste en identitet (konto) du använder när du kör en anslutna användare kommandon i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="39ac6-133">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="39ac6-134">Du definierar vilken identitet JEA används i konfigurationsfilen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-134">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="39ac6-135">Lokala virtuellt konto</span><span class="sxs-lookup"><span data-stu-id="39ac6-135">Local Virtual Account</span></span>

<span data-ttu-id="39ac6-136">Lokala virtuella konton är användbara när alla roller som definierats för JEA-slutpunkt som används för att hantera den lokala datorn och ett lokalt administratörskonto räcker för att köra kommandona har.</span><span class="sxs-lookup"><span data-stu-id="39ac6-136">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="39ac6-137">Virtuella konton är tillfälliga konton som är unika för en viss användare och endast senaste under av sina PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="39ac6-137">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="39ac6-138">På en medlemsserver eller arbetsstation virtuella konton som hör till den lokala datorn **administratörer** grupp.</span><span class="sxs-lookup"><span data-stu-id="39ac6-138">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="39ac6-139">På en Active Directory-domänkontrollant, virtuella konton tillhör domänens **Domänadministratörer** grupp.</span><span class="sxs-lookup"><span data-stu-id="39ac6-139">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="39ac6-140">Om de roller som definieras av sessionskonfigurationen inte kräver administratörsprivilegier, kan du ange de säkerhetsgrupper som virtuellt konto ska tillhöra.</span><span class="sxs-lookup"><span data-stu-id="39ac6-140">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="39ac6-141">De angivna säkerhetsgrupperna måste vara lokala grupper, inte grupper från en domän på en medlemsserver eller arbetsstation.</span><span class="sxs-lookup"><span data-stu-id="39ac6-141">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="39ac6-142">När en eller flera säkerhetsgrupper anges, inte är virtuellt konto tilldelad till den lokala administratörsgruppen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-142">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="39ac6-143">Virtuella konton beviljas tillfälligt inloggningen som en tjänst direkt i den lokala server säkerhetsprincipen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-143">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="39ac6-144">Om en av VirtualAccountGroups som angetts har redan beviljats den här behörigheten i principen, kommer inte längre individuella virtuella konto har lagts till och tas bort från principen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-144">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="39ac6-145">Detta kan vara användbart i scenarier, till exempel domänkontrollanter där ändringar i den säkerhetsprincip för domänkontrollanter granskas noggrant.</span><span class="sxs-lookup"><span data-stu-id="39ac6-145">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="39ac6-146">Detta är endast tillgängligt i Windows Server 2016 med November 2018 eller senare samlad och Windows Server 2019 med januari 2019 eller senare samlad.</span><span class="sxs-lookup"><span data-stu-id="39ac6-146">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="39ac6-147">Grupphanterat tjänstkonto</span><span class="sxs-lookup"><span data-stu-id="39ac6-147">Group-managed service account</span></span>

<span data-ttu-id="39ac6-148">Ett-grupphanterat tjänstkonto (GMSA) är rätt identitet ska användas när JEA-användare behöver åtkomst till nätverksresurser, till exempel filresurser och webbtjänster.</span><span class="sxs-lookup"><span data-stu-id="39ac6-148">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="39ac6-149">GMSAs ger dig en domänidentitet som används för att autentisera med resurser på en dator i domänen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-149">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="39ac6-150">De rättigheter som ett GMSA ger bestäms av resurserna som du försöker komma åt.</span><span class="sxs-lookup"><span data-stu-id="39ac6-150">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="39ac6-151">Du har inte administratörsrättigheter på alla datorer eller tjänster, såvida inte den maskin- eller administratören uttryckligen har gett dessa rättigheter till GMSA.</span><span class="sxs-lookup"><span data-stu-id="39ac6-151">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="39ac6-152">GMSAs bör endast användas när det behövs:</span><span class="sxs-lookup"><span data-stu-id="39ac6-152">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="39ac6-153">Det är svårt att spåra tillbaka åtgärder för att en användare när du använder ett GMSA.</span><span class="sxs-lookup"><span data-stu-id="39ac6-153">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="39ac6-154">Varje användare delar samma kör som-identitet.</span><span class="sxs-lookup"><span data-stu-id="39ac6-154">Every user shares the same run-as identity.</span></span> <span data-ttu-id="39ac6-155">Du måste granska PowerShell-session betyg och loggfiler för att korrelera enskilda användare med sina åtgärder.</span><span class="sxs-lookup"><span data-stu-id="39ac6-155">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="39ac6-156">GMSA kan ha åtkomst till många nätverksresurser som anslutande användaren inte behöver åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="39ac6-156">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="39ac6-157">Försök alltid att begränsa gällande behörigheter i en JEA-session för att följa principen om lägsta behörighet.</span><span class="sxs-lookup"><span data-stu-id="39ac6-157">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="39ac6-158">Gruppen hanterade tjänstkonton är endast tillgänglig på domänanslutna datorer med hjälp av PowerShell 5.1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="39ac6-158">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="39ac6-159">Mer information om hur du skyddar en JEA-session finns i den [säkerhetsöverväganden](security-considerations.md) artikeln.</span><span class="sxs-lookup"><span data-stu-id="39ac6-159">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="39ac6-160">Sessionen avskrifter</span><span class="sxs-lookup"><span data-stu-id="39ac6-160">Session transcripts</span></span>

<span data-ttu-id="39ac6-161">Vi rekommenderar att du konfigurerar en JEA-slutpunkt för att registreras automatiskt avskrifter av användarnas sessioner.</span><span class="sxs-lookup"><span data-stu-id="39ac6-161">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="39ac6-162">PowerShell-session avskrifter innehåller information om den anslutande användaren, kör som-identiteten som tilldelats dem, och kommandona som körs av användaren.</span><span class="sxs-lookup"><span data-stu-id="39ac6-162">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="39ac6-163">De kan vara praktiskt att en granskning team som behöver förstå vem som har gjort en ändring av specifika till ett system.</span><span class="sxs-lookup"><span data-stu-id="39ac6-163">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="39ac6-164">Ange en sökväg till en mapp där avskrifter ska sparas för att konfigurera automatisk avskrift i konfigurationsfilen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-164">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="39ac6-165">Avskrifter skrivs till mappen som den **lokalt System** konto, vilket kräver Läs- och skrivåtkomst till katalogen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-165">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="39ac6-166">Vanliga användare bör ha någon åtkomst till mappen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-166">Standard users should have no access to the folder.</span></span> <span data-ttu-id="39ac6-167">Begränsa antalet administratörer av informationssäkerhet som har åtkomst till att granska avskrifter.</span><span class="sxs-lookup"><span data-stu-id="39ac6-167">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="39ac6-168">Enheten</span><span class="sxs-lookup"><span data-stu-id="39ac6-168">User drive</span></span>

<span data-ttu-id="39ac6-169">Om anslutande användarna behöver för att kopiera filer till eller från JEA-slutpunkt, kan du aktivera enheten i konfigurationsfilen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-169">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="39ac6-170">Användare-enheten är en **PSDrive** som är mappad till en unik mapp för varje anslutande användaren.</span><span class="sxs-lookup"><span data-stu-id="39ac6-170">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="39ac6-171">Den här mappen kan du kopiera filer till eller från systemet utan att ge dem åtkomst till filsystemet fullständig eller exponera filsystem-providern.</span><span class="sxs-lookup"><span data-stu-id="39ac6-171">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="39ac6-172">Användarens enhet innehållet är beständiga mellan sessioner för situationer där nätverksanslutningen kan avbrytas.</span><span class="sxs-lookup"><span data-stu-id="39ac6-172">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="39ac6-173">Som standard kan på enheten du lagra upp till 50MB data per användare.</span><span class="sxs-lookup"><span data-stu-id="39ac6-173">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="39ac6-174">Du kan begränsa mängden data som en användare kan använda med den *UserDriveMaximumSize* fält.</span><span class="sxs-lookup"><span data-stu-id="39ac6-174">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="39ac6-175">Om du inte vill att data i användarens enhet ska vara beständig, kan du konfigurera en schemalagd aktivitet för att automatiskt Rensa mappen varje natt.</span><span class="sxs-lookup"><span data-stu-id="39ac6-175">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="39ac6-176">Användare-enheten är endast tillgängliga i PowerShell 5.1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="39ac6-176">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="39ac6-177">Läs mer om PSDrives [hantera PowerShell enheter](/powershell/scripting/samples/managing-windows-powershell-drives).</span><span class="sxs-lookup"><span data-stu-id="39ac6-177">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="39ac6-178">Rolldefinitioner</span><span class="sxs-lookup"><span data-stu-id="39ac6-178">Role definitions</span></span>

<span data-ttu-id="39ac6-179">Rolldefinitioner i en konfigurationsfil för sessionen definierar mappningen av **användare** till **roller**.</span><span class="sxs-lookup"><span data-stu-id="39ac6-179">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="39ac6-180">Varje användare eller grupp som ingår i det här fältet har beviljats behörighet att JEA-slutpunkt när den är registrerad.</span><span class="sxs-lookup"><span data-stu-id="39ac6-180">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="39ac6-181">Varje användare eller grupp kan ingå som en nyckel i hash-tabellen bara en gång, men kan tilldelas flera roller.</span><span class="sxs-lookup"><span data-stu-id="39ac6-181">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="39ac6-182">Namnet på funktionen roll bör vara namnet på filen roll funktionen utan den `.psrc` tillägget.</span><span class="sxs-lookup"><span data-stu-id="39ac6-182">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="39ac6-183">Om en användare tillhör mer än en grupp i rolldefinitionen kan få de åtkomst till rollerna för var och en.</span><span class="sxs-lookup"><span data-stu-id="39ac6-183">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="39ac6-184">När två roller bevilja åtkomst till samma cmdlets, beviljas den mest Tillåtande parameteruppsättningen för användaren.</span><span class="sxs-lookup"><span data-stu-id="39ac6-184">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="39ac6-185">När du anger lokala användare eller grupper i rollen definitioner fältet, måste du använda namnet på datorn, inte **localhost** eller jokertecken.</span><span class="sxs-lookup"><span data-stu-id="39ac6-185">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="39ac6-186">Du hittar namnet på datorn genom att kontrollera den `$env:COMPUTERNAME` variabeln.</span><span class="sxs-lookup"><span data-stu-id="39ac6-186">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="39ac6-187">Sökordning för roll-funktion</span><span class="sxs-lookup"><span data-stu-id="39ac6-187">Role capability search order</span></span>

<span data-ttu-id="39ac6-188">I exemplet ovan visas rollfunktioner refererar till det grundläggande namnet på rollen kapaciteten för filen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-188">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="39ac6-189">Det grundläggande namnet på en fil är filnamn utan filtillägget.</span><span class="sxs-lookup"><span data-stu-id="39ac6-189">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="39ac6-190">Om flera rollfunktioner är tillgängliga på datorn med samma namn, använder PowerShell dess implicita ordning för att markera filen effektiva roll funktionen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-190">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="39ac6-191">JEA har **inte** ge åtkomst till alla roll funktionsfiler med samma namn.</span><span class="sxs-lookup"><span data-stu-id="39ac6-191">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="39ac6-192">JEA använder den `$env:PSModulePath` miljövariabeln för att avgöra vilka sökvägar kan du söka efter roll funktionsfiler.</span><span class="sxs-lookup"><span data-stu-id="39ac6-192">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="39ac6-193">JEA söker efter giltiga PowerShell-moduler som innehåller en ”RoleCapabilities” undermapp i var och en av dessa sökvägar.</span><span class="sxs-lookup"><span data-stu-id="39ac6-193">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="39ac6-194">Precis som med importerar moduler, föredrar JEA rollfunktioner som medföljer Windows till den anpassade rollen funktionerna med samma namn.</span><span class="sxs-lookup"><span data-stu-id="39ac6-194">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="39ac6-195">För andra namnkonflikter bestäms prioritet av den ordning som räknar Windows upp filerna i katalogen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-195">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="39ac6-196">Ordningen är inte garanterat som alfabetisk.</span><span class="sxs-lookup"><span data-stu-id="39ac6-196">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="39ac6-197">Den första roll funktionen filen hittades som matchar det angivna namnet används för anslutande användaren.</span><span class="sxs-lookup"><span data-stu-id="39ac6-197">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="39ac6-198">Sedan rollen funktionen search ordning är inte deterministisk, är det **rekommenderar vi** att rollfunktioner har unika filnamn.</span><span class="sxs-lookup"><span data-stu-id="39ac6-198">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="39ac6-199">Regler för villkorlig åtkomst</span><span class="sxs-lookup"><span data-stu-id="39ac6-199">Conditional access rules</span></span>

<span data-ttu-id="39ac6-200">Alla användare och grupper som ingår i den **RoleDefinitions** fältet beviljas automatiskt åtkomst till JEA-slutpunkter.</span><span class="sxs-lookup"><span data-stu-id="39ac6-200">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="39ac6-201">Regler för villkorlig åtkomst kan du förfina den här åtkomsten och Kräv att användare ska tillhöra ytterligare säkerhetsgrupper som inte påverkar de roller som de tilldelats.</span><span class="sxs-lookup"><span data-stu-id="39ac6-201">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="39ac6-202">Detta är användbart när du vill integrera en hanteringslösning för privilegierad just-in-time-åtkomst, autentisering med smartkort eller andra Multi-Factor authentication-lösning med JEA.</span><span class="sxs-lookup"><span data-stu-id="39ac6-202">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="39ac6-203">Regler för villkorlig åtkomst har definierats i fältet RequiredGroups i en konfigurationsfil för sessionen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-203">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="39ac6-204">Där kan du ange en hash-tabell (du kan också kapslade) som använder ”och” och ”eller” för att skapa dina regler.</span><span class="sxs-lookup"><span data-stu-id="39ac6-204">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="39ac6-205">Här följer några exempel på hur du använder det här fältet:</span><span class="sxs-lookup"><span data-stu-id="39ac6-205">Here are some examples of how to use this field:</span></span>

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
> <span data-ttu-id="39ac6-206">Regler för villkorlig åtkomst är bara tillgängliga i PowerShell 5.1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="39ac6-206">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="39ac6-207">Andra egenskaper</span><span class="sxs-lookup"><span data-stu-id="39ac6-207">Other properties</span></span>

<span data-ttu-id="39ac6-208">Sessionen konfigurationsfiler kan också göra allt en roll funktionen fil kan göra, men utan möjlighet att ge den anslutande användare åtkomst till olika kommandon.</span><span class="sxs-lookup"><span data-stu-id="39ac6-208">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="39ac6-209">Om du vill tillåta alla användare åtkomst till specifika cmdlet: ar, funktioner eller leverantörer kan du göra det direkt i konfigurationsfilen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-209">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="39ac6-210">En fullständig lista över egenskaper som stöds i konfigurationsfilen session kör `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="39ac6-210">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="39ac6-211">Testa en konfigurationsfil för session</span><span class="sxs-lookup"><span data-stu-id="39ac6-211">Testing a session configuration file</span></span>

<span data-ttu-id="39ac6-212">Du kan testa en session konfiguration med hjälp av den [Test PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="39ac6-212">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="39ac6-213">Vi rekommenderar att du testar din session-konfigurationsfil om du manuellt har redigerat den `.pssc` filen.</span><span class="sxs-lookup"><span data-stu-id="39ac6-213">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="39ac6-214">Testa säkerställer syntaxen är korrekt.</span><span class="sxs-lookup"><span data-stu-id="39ac6-214">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="39ac6-215">Om en konfigurationsfil för sessionen inte det här testet, kan den inte registreras i systemet.</span><span class="sxs-lookup"><span data-stu-id="39ac6-215">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="39ac6-216">Exempelkonfigurationsfil för session</span><span class="sxs-lookup"><span data-stu-id="39ac6-216">Sample session configuration file</span></span>

<span data-ttu-id="39ac6-217">I följande exempel visas hur du skapar och validera en sessionskonfiguration för JEA.</span><span class="sxs-lookup"><span data-stu-id="39ac6-217">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="39ac6-218">Rolldefinitionerna skapas och lagras i den `$roles` variabeln för bekvämlighets skull och läsbarhet.</span><span class="sxs-lookup"><span data-stu-id="39ac6-218">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="39ac6-219">Det är inte ett krav att göra detta.</span><span class="sxs-lookup"><span data-stu-id="39ac6-219">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="39ac6-220">Uppdaterar sessionen konfigurationsfiler</span><span class="sxs-lookup"><span data-stu-id="39ac6-220">Updating session configuration files</span></span>

<span data-ttu-id="39ac6-221">Om du vill ändra egenskaperna för en JEA-sessionskonfiguration, inklusive mappningen av användare till roller måste du [avregistrera](register-jea.md#unregistering-jea-configurations).</span><span class="sxs-lookup"><span data-stu-id="39ac6-221">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="39ac6-222">Sedan [Omregistrera](register-jea.md) JEA-sessionskonfiguration som använder en konfigurationsfil för uppdaterade session.</span><span class="sxs-lookup"><span data-stu-id="39ac6-222">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="39ac6-223">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="39ac6-223">Next steps</span></span>

- [<span data-ttu-id="39ac6-224">Registrera en JEA-konfiguration</span><span class="sxs-lookup"><span data-stu-id="39ac6-224">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="39ac6-225">Författare JEA roller</span><span class="sxs-lookup"><span data-stu-id="39ac6-225">Author JEA roles</span></span>](role-capabilities.md)
