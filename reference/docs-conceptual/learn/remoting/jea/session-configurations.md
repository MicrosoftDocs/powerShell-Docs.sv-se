---
ms.date: 07/10/2019
keywords: Jea, PowerShell, säkerhet
title: JEA
description: Sessionsbaserade definierar vem som kan använda JEA-slutpunkten och vilka roller de har åtkomst till.
ms.openlocfilehash: b616d5bf260bbdfe89b6422fd4a8b4866f7fdc67
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501566"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="ebc22-104">JEA</span><span class="sxs-lookup"><span data-stu-id="ebc22-104">JEA Session Configurations</span></span>

<span data-ttu-id="ebc22-105">En JEA-slutpunkt är registrerad på ett system genom att skapa och registrera en PowerShell-sessions konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="ebc22-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="ebc22-106">Sessionsbaserade definierar vem som kan använda JEA-slutpunkten och vilka roller de har åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="ebc22-106">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="ebc22-107">De definierar också globala inställningar som gäller för alla användare av JEA-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ebc22-107">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="ebc22-108">Skapa en konfigurations fil för sessionen</span><span class="sxs-lookup"><span data-stu-id="ebc22-108">Create a session configuration file</span></span>

<span data-ttu-id="ebc22-109">För att registrera en JEA-slutpunkt måste du ange hur slut punkten ska konfigureras.</span><span class="sxs-lookup"><span data-stu-id="ebc22-109">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="ebc22-110">Det finns många alternativ att tänka på.</span><span class="sxs-lookup"><span data-stu-id="ebc22-110">There are many options to consider.</span></span> <span data-ttu-id="ebc22-111">De viktigaste alternativen är:</span><span class="sxs-lookup"><span data-stu-id="ebc22-111">The most important options are:</span></span>

- <span data-ttu-id="ebc22-112">Som har åtkomst till JEA-slutpunkten</span><span class="sxs-lookup"><span data-stu-id="ebc22-112">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="ebc22-113">Vilka roller de tilldelas</span><span class="sxs-lookup"><span data-stu-id="ebc22-113">Which roles they be assigned</span></span>
- <span data-ttu-id="ebc22-114">Vilken identitet JEA använder under försättsblad</span><span class="sxs-lookup"><span data-stu-id="ebc22-114">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="ebc22-115">Namnet på JEA-slutpunkten</span><span class="sxs-lookup"><span data-stu-id="ebc22-115">The name of the JEA endpoint</span></span>

<span data-ttu-id="ebc22-116">De här alternativen definieras i en PowerShell-datafil med ett `.pssc` tillägg som kallas för en PowerShell-sessions konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="ebc22-116">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="ebc22-117">Konfigurations filen för sessionen kan redige ras med valfri text redigerare.</span><span class="sxs-lookup"><span data-stu-id="ebc22-117">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="ebc22-118">Kör följande kommando för att skapa en tom mall konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="ebc22-118">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="ebc22-119">Endast de vanligaste konfigurations alternativen ingår i mallfilen som standard.</span><span class="sxs-lookup"><span data-stu-id="ebc22-119">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="ebc22-120">Använd `-Full` växeln för att inkludera alla tillämpliga inställningar i den genererade PSSC.</span><span class="sxs-lookup"><span data-stu-id="ebc22-120">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="ebc22-121">`-SessionType RestrictedRemoteServer`Fältet indikerar att konfigurationen av sessionen används av Jea för säker hantering.</span><span class="sxs-lookup"><span data-stu-id="ebc22-121">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="ebc22-122">Sessioner av den här typen körs i **Nolanguage** -läge och har bara åtkomst till följande standard kommandon (och alias):</span><span class="sxs-lookup"><span data-stu-id="ebc22-122">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="ebc22-123">Clear-Host (CLS, Clear)</span><span class="sxs-lookup"><span data-stu-id="ebc22-123">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="ebc22-124">Exit-PSSession (exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="ebc22-124">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="ebc22-125">Get-Command (GCM)</span><span class="sxs-lookup"><span data-stu-id="ebc22-125">Get-Command (gcm)</span></span>
- <span data-ttu-id="ebc22-126">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="ebc22-126">Get-FormatData</span></span>
- <span data-ttu-id="ebc22-127">Get-Help</span><span class="sxs-lookup"><span data-stu-id="ebc22-127">Get-Help</span></span>
- <span data-ttu-id="ebc22-128">Measure-Object (mått)</span><span class="sxs-lookup"><span data-stu-id="ebc22-128">Measure-Object (measure)</span></span>
- <span data-ttu-id="ebc22-129">Out-Default</span><span class="sxs-lookup"><span data-stu-id="ebc22-129">Out-Default</span></span>
- <span data-ttu-id="ebc22-130">Select-Object (Välj)</span><span class="sxs-lookup"><span data-stu-id="ebc22-130">Select-Object (select)</span></span>

<span data-ttu-id="ebc22-131">Det finns inga tillgängliga PowerShell-providrar eller externa program (körbara filer eller skript).</span><span class="sxs-lookup"><span data-stu-id="ebc22-131">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="ebc22-132">Mer information om språk lägen finns [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span><span class="sxs-lookup"><span data-stu-id="ebc22-132">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="ebc22-133">Välj identiteten JEA</span><span class="sxs-lookup"><span data-stu-id="ebc22-133">Choose the JEA identity</span></span>

<span data-ttu-id="ebc22-134">JEA behöver en identitet (konto) som ska användas för att köra en ansluten användares kommandon i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="ebc22-134">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="ebc22-135">Du definierar vilka identiteter JEA som används i sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="ebc22-135">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="ebc22-136">Lokalt virtuellt konto</span><span class="sxs-lookup"><span data-stu-id="ebc22-136">Local Virtual Account</span></span>

<span data-ttu-id="ebc22-137">Lokala virtuella konton är användbara när alla roller som definierats för JEA-slutpunkten används för att hantera den lokala datorn och ett lokalt administratörs konto räcker för att köra kommandona.</span><span class="sxs-lookup"><span data-stu-id="ebc22-137">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="ebc22-138">Virtuella konton är tillfälliga konton som är unika för en speciell användare och som endast är under den tid som PowerShell-sessionen varar.</span><span class="sxs-lookup"><span data-stu-id="ebc22-138">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="ebc22-139">På en medlems Server eller arbets Station tillhör virtuella konton den lokala datorns **Administratörs** grupp.</span><span class="sxs-lookup"><span data-stu-id="ebc22-139">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="ebc22-140">På en Active Directory-domän kontroll hör virtuella konton till domänens **domän administratörs** grupp.</span><span class="sxs-lookup"><span data-stu-id="ebc22-140">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="ebc22-141">Om rollerna som definieras av konfigurationen av sessionen inte kräver fullständig administratörs behörighet kan du ange de säkerhets grupper som det virtuella kontot ska tillhöra.</span><span class="sxs-lookup"><span data-stu-id="ebc22-141">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="ebc22-142">På en medlems Server eller arbets Station måste de angivna säkerhets grupperna vara lokala grupper, inte grupper från en domän.</span><span class="sxs-lookup"><span data-stu-id="ebc22-142">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="ebc22-143">När en eller flera säkerhets grupper har angetts är det virtuella kontot inte tilldelat till den lokala gruppen eller domän administratörs gruppen.</span><span class="sxs-lookup"><span data-stu-id="ebc22-143">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="ebc22-144">Virtuella konton beviljas tillfälligt inloggningen som en tjänst direkt i säkerhets principen för den lokala servern.</span><span class="sxs-lookup"><span data-stu-id="ebc22-144">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="ebc22-145">Om ett av de VirtualAccountGroups som har angetts redan har beviljats rätt i principen, läggs det enskilda virtuella kontot inte längre till och tas bort från principen.</span><span class="sxs-lookup"><span data-stu-id="ebc22-145">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="ebc22-146">Detta kan vara användbart i scenarier som domänkontrollanter där ändringar av säkerhets principen för domänkontrollanten granskas noga.</span><span class="sxs-lookup"><span data-stu-id="ebc22-146">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="ebc22-147">Detta är endast tillgängligt i Windows Server 2016 med Samlad uppdatering för 2018 eller senare och Windows Server 2019 med den samlade uppdateringen från januari 2019 eller senare.</span><span class="sxs-lookup"><span data-stu-id="ebc22-147">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="ebc22-148">Grupphanterat tjänst konto</span><span class="sxs-lookup"><span data-stu-id="ebc22-148">Group-managed service account</span></span>

<span data-ttu-id="ebc22-149">Ett grupphanterat tjänst konto (GMSA) är en lämplig identitet som används när JEA-användare behöver åtkomst till nätverks resurser, till exempel fil resurser och webb tjänster.</span><span class="sxs-lookup"><span data-stu-id="ebc22-149">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="ebc22-150">GMSAs ger dig en domän identitet som används för att autentisera med resurser på valfri dator i domänen.</span><span class="sxs-lookup"><span data-stu-id="ebc22-150">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="ebc22-151">De rättigheter som en GMSA tillhandahåller bestäms av de resurser som du har åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="ebc22-151">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="ebc22-152">Du har inte administratörs behörighet på alla datorer eller tjänster om inte datorn eller tjänst administratören uttryckligen har beviljat dessa rättigheter till GMSA.</span><span class="sxs-lookup"><span data-stu-id="ebc22-152">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="ebc22-153">GMSAs bör endast användas när det behövs:</span><span class="sxs-lookup"><span data-stu-id="ebc22-153">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="ebc22-154">Det är svårt att spåra åtgärder till en användare när du använder en GMSA.</span><span class="sxs-lookup"><span data-stu-id="ebc22-154">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="ebc22-155">Varje användare delar samma kör som-identitet.</span><span class="sxs-lookup"><span data-stu-id="ebc22-155">Every user shares the same run-as identity.</span></span> <span data-ttu-id="ebc22-156">Du måste granska avskrifter och loggar för PowerShell-sessionen för att korrelera enskilda användare med sina åtgärder.</span><span class="sxs-lookup"><span data-stu-id="ebc22-156">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="ebc22-157">GMSA kan ha åtkomst till många nätverks resurser som den anslutande användaren inte behöver åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="ebc22-157">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="ebc22-158">Försök alltid att begränsa gällande behörigheter i en JEA-session så att de följer principen om minsta behörighet.</span><span class="sxs-lookup"><span data-stu-id="ebc22-158">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="ebc22-159">Grupphanterade tjänst konton är bara tillgängliga på domänanslutna datorer med PowerShell 5,1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="ebc22-159">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="ebc22-160">Mer information om hur du skyddar en JEA-session finns i artikeln [säkerhets överväganden](security-considerations.md) .</span><span class="sxs-lookup"><span data-stu-id="ebc22-160">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="ebc22-161">Avskrifter för session</span><span class="sxs-lookup"><span data-stu-id="ebc22-161">Session transcripts</span></span>

<span data-ttu-id="ebc22-162">Vi rekommenderar att du konfigurerar en JEA-slutpunkt för att automatiskt registrera avskrifter av användarnas sessioner.</span><span class="sxs-lookup"><span data-stu-id="ebc22-162">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="ebc22-163">Avskrifter i PowerShell-sessionen innehåller information om den anslutande användaren, kör som-identiteten som tilldelats dem och kommandona som körs av användaren.</span><span class="sxs-lookup"><span data-stu-id="ebc22-163">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="ebc22-164">De kan vara användbara för ett gransknings team som behöver förstå vem som har gjort en speciell ändring i ett system.</span><span class="sxs-lookup"><span data-stu-id="ebc22-164">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="ebc22-165">Om du vill konfigurera automatisk avskrift i sessionens konfigurations fil anger du en sökväg till en mapp där avskrifterna ska lagras.</span><span class="sxs-lookup"><span data-stu-id="ebc22-165">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="ebc22-166">Avskrifter skrivs till mappen av det **lokala system** kontot, som kräver Läs-och Skriv behörighet till katalogen.</span><span class="sxs-lookup"><span data-stu-id="ebc22-166">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="ebc22-167">Standard användare får inte ha åtkomst till mappen.</span><span class="sxs-lookup"><span data-stu-id="ebc22-167">Standard users should have no access to the folder.</span></span> <span data-ttu-id="ebc22-168">Begränsa antalet säkerhets administratörer som har åtkomst till granskning av avskrifter.</span><span class="sxs-lookup"><span data-stu-id="ebc22-168">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="ebc22-169">Användar enhet</span><span class="sxs-lookup"><span data-stu-id="ebc22-169">User drive</span></span>

<span data-ttu-id="ebc22-170">Om dina anslutna användare behöver kopiera filer till eller från JEA-slutpunkten kan du aktivera användar enheten i sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="ebc22-170">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="ebc22-171">Användar enheten är en **PSDrive** som är mappad till en unik mapp för varje anslutning användare.</span><span class="sxs-lookup"><span data-stu-id="ebc22-171">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="ebc22-172">Med den här mappen kan användare kopiera filer till eller från systemet utan att ge dem till gång till det fullständiga fil systemet eller exponera fil Systems leverantören.</span><span class="sxs-lookup"><span data-stu-id="ebc22-172">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="ebc22-173">Innehållet i användar enheten är beständigt i sessioner för att hantera situationer där nätverks anslutningen kan avbrytas.</span><span class="sxs-lookup"><span data-stu-id="ebc22-173">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="ebc22-174">Som standard tillåter användar enheten att du lagrar maximalt 50 MB data per användare.</span><span class="sxs-lookup"><span data-stu-id="ebc22-174">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="ebc22-175">Du kan begränsa mängden data som en användare kan använda med fältet *UserDriveMaximumSize* .</span><span class="sxs-lookup"><span data-stu-id="ebc22-175">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="ebc22-176">Om du inte vill att data i användar enheten ska vara beständiga kan du konfigurera en schemalagd aktivitet på systemet så att den automatiskt rensar mappen varje natt.</span><span class="sxs-lookup"><span data-stu-id="ebc22-176">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="ebc22-177">Användar enheten är bara tillgänglig i PowerShell 5,1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="ebc22-177">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="ebc22-178">Mer information om PSDrives finns i [Hantera PowerShell-enheter](/powershell/scripting/samples/managing-windows-powershell-drives).</span><span class="sxs-lookup"><span data-stu-id="ebc22-178">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="ebc22-179">Rolldefinitioner</span><span class="sxs-lookup"><span data-stu-id="ebc22-179">Role definitions</span></span>

<span data-ttu-id="ebc22-180">Roll definitioner i en sessions konfigurations fil definierar mappningen av **användare** till **roller**.</span><span class="sxs-lookup"><span data-stu-id="ebc22-180">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="ebc22-181">Varje användare eller grupp som ingår i det här fältet beviljas behörighet till JEA-slutpunkten när den har registrerats.</span><span class="sxs-lookup"><span data-stu-id="ebc22-181">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="ebc22-182">Varje användare eller grupp kan endast inkluderas som en nyckel i hash-tabellen en gång, men de kan tilldelas flera roller.</span><span class="sxs-lookup"><span data-stu-id="ebc22-182">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="ebc22-183">Namnet på roll kapaciteten bör vara namnet på roll funktions filen, utan `.psrc` tillägget.</span><span class="sxs-lookup"><span data-stu-id="ebc22-183">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="ebc22-184">Om en användare tillhör fler än en grupp i roll definitionen får de åtkomst till rollerna för var och en.</span><span class="sxs-lookup"><span data-stu-id="ebc22-184">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="ebc22-185">När två roller beviljar åtkomst till samma cmdletar beviljas användaren den mest tillåtna parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="ebc22-185">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="ebc22-186">När du anger lokala användare eller grupper i fältet roll definitioner, se till att använda dator namnet, inte **localhost** eller jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ebc22-186">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="ebc22-187">Du kan kontrol lera dator namnet genom att inspektera `$env:COMPUTERNAME` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ebc22-187">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="ebc22-188">Sök ordning för roll kapacitet</span><span class="sxs-lookup"><span data-stu-id="ebc22-188">Role capability search order</span></span>

<span data-ttu-id="ebc22-189">Som du ser i exemplet ovan refereras roll funktioner av bas namnet för roll funktions filen.</span><span class="sxs-lookup"><span data-stu-id="ebc22-189">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="ebc22-190">Bas namnet för en fil är fil namnet utan fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="ebc22-190">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="ebc22-191">Om flera roll funktioner är tillgängliga i systemet med samma namn, använder PowerShell den implicita Sök ordningen för att välja den effektiva roll kapacitets filen.</span><span class="sxs-lookup"><span data-stu-id="ebc22-191">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="ebc22-192">JEA ger **inte** åtkomst till alla roll kapacitets filer med samma namn.</span><span class="sxs-lookup"><span data-stu-id="ebc22-192">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="ebc22-193">JEA använder `$env:PSModulePath` miljövariabeln för att avgöra vilka sökvägar som ska genomsökas efter roll kapacitets filer.</span><span class="sxs-lookup"><span data-stu-id="ebc22-193">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="ebc22-194">I var och en av dessa sökvägar söker JEA efter giltiga PowerShell-moduler som innehåller undermappen "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="ebc22-194">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="ebc22-195">Precis som med importera moduler föredrar JEA roll funktioner som medföljer Windows till anpassade roll funktioner med samma namn.</span><span class="sxs-lookup"><span data-stu-id="ebc22-195">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="ebc22-196">För alla andra namn konflikter bestäms prioriteten i den ordning som Windows räknar upp filerna i katalogen.</span><span class="sxs-lookup"><span data-stu-id="ebc22-196">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="ebc22-197">Ordningen är inte garanterat alfabetisk.</span><span class="sxs-lookup"><span data-stu-id="ebc22-197">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="ebc22-198">Den första roll funktions filen som matchar det angivna namnet används för den anslutande användaren.</span><span class="sxs-lookup"><span data-stu-id="ebc22-198">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="ebc22-199">Eftersom Sök ordningen för roll funktioner inte är deterministisk, rekommenderar vi **starkt** att roll funktionerna har unika fil namn.</span><span class="sxs-lookup"><span data-stu-id="ebc22-199">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="ebc22-200">Regler för villkorlig åtkomst</span><span class="sxs-lookup"><span data-stu-id="ebc22-200">Conditional access rules</span></span>

<span data-ttu-id="ebc22-201">Alla användare och grupper som ingår i fältet **RoleDefinitions** beviljas automatiskt åtkomst till Jea-slutpunkter.</span><span class="sxs-lookup"><span data-stu-id="ebc22-201">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="ebc22-202">Med regler för villkorlig åtkomst kan du förfina den här åtkomsten och kräva att användare tillhöra ytterligare säkerhets grupper som inte påverkar de roller som de är tilldelade till.</span><span class="sxs-lookup"><span data-stu-id="ebc22-202">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="ebc22-203">Detta är användbart när du vill integrera en just-in-Time-hanterings lösning för privilegie rad åtkomst, autentisering av smartkort eller någon annan lösning för multifaktorautentisering med JEA.</span><span class="sxs-lookup"><span data-stu-id="ebc22-203">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="ebc22-204">Regler för villkorlig åtkomst definieras i fältet RequiredGroups i en sessions konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="ebc22-204">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="ebc22-205">Där kan du ange en hash (eventuellt kapslad) som använder "och" och "eller" nycklar för att skapa regler.</span><span class="sxs-lookup"><span data-stu-id="ebc22-205">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="ebc22-206">Här följer några exempel på hur du använder det här fältet:</span><span class="sxs-lookup"><span data-stu-id="ebc22-206">Here are some examples of how to use this field:</span></span>

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
> <span data-ttu-id="ebc22-207">Regler för villkorlig åtkomst är bara tillgängliga i PowerShell 5,1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="ebc22-207">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="ebc22-208">Andra egenskaper</span><span class="sxs-lookup"><span data-stu-id="ebc22-208">Other properties</span></span>

<span data-ttu-id="ebc22-209">Konfigurationsfiler för sessioner kan också göra allt en roll funktions fil kan göra, precis utan möjligheten att ge användarna åtkomst till olika kommandon.</span><span class="sxs-lookup"><span data-stu-id="ebc22-209">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="ebc22-210">Om du vill ge alla användare åtkomst till vissa cmdletar, funktioner eller providrar kan du göra det direkt i konfigurations filen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="ebc22-210">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="ebc22-211">En fullständig lista över vilka egenskaper som stöds i konfigurations filen för sessionen körs `Get-Help New-PSSessionConfigurationFile -Full` .</span><span class="sxs-lookup"><span data-stu-id="ebc22-211">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="ebc22-212">Testa en konfigurations fil för sessionen</span><span class="sxs-lookup"><span data-stu-id="ebc22-212">Testing a session configuration file</span></span>

<span data-ttu-id="ebc22-213">Du kan testa en sessions konfiguration med cmdleten [test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) .</span><span class="sxs-lookup"><span data-stu-id="ebc22-213">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="ebc22-214">Vi rekommenderar att du testar din konfigurations fil för sessionen om du har redigerat `.pssc` filen manuellt.</span><span class="sxs-lookup"><span data-stu-id="ebc22-214">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="ebc22-215">Testet ser till att syntaxen är korrekt.</span><span class="sxs-lookup"><span data-stu-id="ebc22-215">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="ebc22-216">Om en sessions konfigurations fil Miss lyckas med det här testet kan den inte registreras i systemet.</span><span class="sxs-lookup"><span data-stu-id="ebc22-216">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="ebc22-217">Exempel på konfigurations fil för sessionen</span><span class="sxs-lookup"><span data-stu-id="ebc22-217">Sample session configuration file</span></span>

<span data-ttu-id="ebc22-218">I följande exempel visas hur du skapar och validerar en sessionshantering för JEA.</span><span class="sxs-lookup"><span data-stu-id="ebc22-218">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="ebc22-219">Roll definitionerna skapas och lagras i `$roles` variabeln för bekvämlighet och läsbarhet.</span><span class="sxs-lookup"><span data-stu-id="ebc22-219">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="ebc22-220">Det är inte nödvändigt att göra det.</span><span class="sxs-lookup"><span data-stu-id="ebc22-220">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="ebc22-221">Uppdaterar sessionens konfigurationsfiler</span><span class="sxs-lookup"><span data-stu-id="ebc22-221">Updating session configuration files</span></span>

<span data-ttu-id="ebc22-222">Om du vill ändra egenskaperna för en JEA, inklusive mappningen av användare till roller, måste du [avregistrera](register-jea.md#unregistering-jea-configurations)dig.</span><span class="sxs-lookup"><span data-stu-id="ebc22-222">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="ebc22-223">Registrera sedan JEA [-](register-jea.md) sessionen med en uppdaterad sessions konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="ebc22-223">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ebc22-224">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="ebc22-224">Next steps</span></span>

- [<span data-ttu-id="ebc22-225">Registrera en JEA-konfiguration</span><span class="sxs-lookup"><span data-stu-id="ebc22-225">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="ebc22-226">Redigera JEA-roller</span><span class="sxs-lookup"><span data-stu-id="ebc22-226">Author JEA roles</span></span>](role-capabilities.md)
