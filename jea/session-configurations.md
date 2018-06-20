---
ms.date: 06/12/2017
keywords: jea powershell säkerhet
title: JEA Sessionskonfigurationer
ms.openlocfilehash: 3e5a663be8e7aba09a2592c278224cd892c89a20
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190102"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="6aa15-103">JEA Sessionskonfigurationer</span><span class="sxs-lookup"><span data-stu-id="6aa15-103">JEA Session Configurations</span></span>

> <span data-ttu-id="6aa15-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6aa15-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="6aa15-105">En slutpunkt för JEA är registrerad på en dator genom att skapa och registrera en konfigurationsfil för PowerShell-session på ett visst sätt.</span><span class="sxs-lookup"><span data-stu-id="6aa15-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="6aa15-106">Fastställa sessionskonfigurationer *som* kan använda JEA slutpunkt och vilka roller de har åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="6aa15-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="6aa15-107">De kan också definiera globala inställningar som gäller för användare av en roll i JEA-sessionen.</span><span class="sxs-lookup"><span data-stu-id="6aa15-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="6aa15-108">Det här avsnittet beskriver hur du skapar en konfigurationsfil för PowerShell-session och registrera en JEA slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="6aa15-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="6aa15-109">Skapa en konfigurationsfil för session</span><span class="sxs-lookup"><span data-stu-id="6aa15-109">Create a session configuration file</span></span>

<span data-ttu-id="6aa15-110">Du måste ange hur den slutpunkten ska konfigureras för att kunna registrera en JEA slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="6aa15-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="6aa15-111">Det finns många alternativ att överväga här är det viktigaste att vilka som ska ha åtkomst till slutpunkten JEA, vilka roller kommer de tilldelas, vilken identitet JEA används under försättsbladen och vad ska vara namnet på slutpunkten JEA.</span><span class="sxs-lookup"><span data-stu-id="6aa15-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="6aa15-112">Dessa definieras i konfigurationsfilen en PowerShell-session som är en PowerShell-datafil som slutar med filnamnstillägget .pssc.</span><span class="sxs-lookup"><span data-stu-id="6aa15-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="6aa15-113">Kör följande kommando för att skapa en konfigurationsfil för stommen sessionen för JEA slutpunkter.</span><span class="sxs-lookup"><span data-stu-id="6aa15-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="6aa15-114">Endast de vanligaste konfigurationsalternativ ingår i filen stommen som standard.</span><span class="sxs-lookup"><span data-stu-id="6aa15-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="6aa15-115">Använd den `-Full` växel om du vill inkludera alla tillämpliga inställningar i den genererade PSSC.</span><span class="sxs-lookup"><span data-stu-id="6aa15-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="6aa15-116">Du kan öppna konfigurationsfilen session i en textredigerare.</span><span class="sxs-lookup"><span data-stu-id="6aa15-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="6aa15-117">Den `-SessionType RestrictedRemoteServer` fältet som anger att sessionskonfigurationen kommer att användas av JEA för säker hantering.</span><span class="sxs-lookup"><span data-stu-id="6aa15-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="6aa15-118">Sessioner som konfigureras på det här sättet kommer att fungera i [NoLanguage läge](https://technet.microsoft.com/library/dn433292.aspx) och får bara innehålla följande 8 standardkommandon (och alias) tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="6aa15-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="6aa15-119">Rensa-värden (cls, rensa)</span><span class="sxs-lookup"><span data-stu-id="6aa15-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="6aa15-120">Avsluta-PSSession (exsn, avsluta)</span><span class="sxs-lookup"><span data-stu-id="6aa15-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="6aa15-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="6aa15-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="6aa15-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="6aa15-122">Get-FormatData</span></span>
- <span data-ttu-id="6aa15-123">Get-Help</span><span class="sxs-lookup"><span data-stu-id="6aa15-123">Get-Help</span></span>
- <span data-ttu-id="6aa15-124">Måttobjekt (mått)</span><span class="sxs-lookup"><span data-stu-id="6aa15-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="6aa15-125">Standard ut</span><span class="sxs-lookup"><span data-stu-id="6aa15-125">Out-Default</span></span>
- <span data-ttu-id="6aa15-126">Select-Object (Välj)</span><span class="sxs-lookup"><span data-stu-id="6aa15-126">Select-Object (select)</span></span>

<span data-ttu-id="6aa15-127">Inga PowerShell-providers är tillgängliga, inte heller några externa program (körbara filer, skript osv.).</span><span class="sxs-lookup"><span data-stu-id="6aa15-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="6aa15-128">Det finns flera andra fält som du vill konfigurera för JEA-sessionen.</span><span class="sxs-lookup"><span data-stu-id="6aa15-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="6aa15-129">De beskrivs i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="6aa15-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="6aa15-130">Välj JEA identitet</span><span class="sxs-lookup"><span data-stu-id="6aa15-130">Choose the JEA identity</span></span>

<span data-ttu-id="6aa15-131">JEA måste en identitet (konto) ska användas när en användare som ansluten kommandon körs i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="6aa15-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="6aa15-132">Du bestämmer vilken identitet JEA används i konfigurationsfilen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6aa15-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="6aa15-133">Lokala virtuellt konto</span><span class="sxs-lookup"><span data-stu-id="6aa15-133">Local Virtual Account</span></span>

<span data-ttu-id="6aa15-134">Om de roller som stöds av den här slutpunkten JEA används för att hantera den lokala datorn, och ett lokalt administratörskonto är tillräckligt för att köra kommandon har, bör du konfigurera JEA om du vill använda ett virtuellt lokalt konto.</span><span class="sxs-lookup"><span data-stu-id="6aa15-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands succesfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="6aa15-135">Virtuella konton är tillfälliga konton som är unik för en viss användare och endast senaste under hela sin PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="6aa15-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="6aa15-136">På en medlemsserver eller arbetsstation virtuella konton som hör till den lokala datorn **administratörer** grupp och har åtkomst till de flesta systemresurser.</span><span class="sxs-lookup"><span data-stu-id="6aa15-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="6aa15-137">På en Active Directory-domänkontrollant virtuella konton tillhör domänens **Domänadministratörer** grupp.</span><span class="sxs-lookup"><span data-stu-id="6aa15-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="6aa15-138">Om roller som stöds av sessionskonfigurationen inte kräver dessa breda behörigheter, kan du alternativt ange de säkerhetsgrupper som virtuellt konto ska tillhöra.</span><span class="sxs-lookup"><span data-stu-id="6aa15-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="6aa15-139">De angivna säkerhetsgrupperna måste vara lokala grupper, inte grupper från en domän på en medlemsserver eller en arbetsstation.</span><span class="sxs-lookup"><span data-stu-id="6aa15-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="6aa15-140">När en eller flera säkerhetsgrupper anges virtuellt konto kommer inte längre tillhör administratörsgruppen lokalt eller via domänadministratör.</span><span class="sxs-lookup"><span data-stu-id="6aa15-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a><span data-ttu-id="6aa15-141">Grupphanterat tjänstkonto</span><span class="sxs-lookup"><span data-stu-id="6aa15-141">Group Managed Service Account</span></span>


<span data-ttu-id="6aa15-142">För scenarier som kräver JEA användare att komma åt nätverksresurser, till exempel andra datorer eller webbtjänster, är en grupp Hanterat tjänstkonto (gMSA) en lämpligare identitet ska användas.</span><span class="sxs-lookup"><span data-stu-id="6aa15-142">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="6aa15-143">gMSA-konton får du en domän-identitet som kan användas för att autentisera mot resurser på en dator i domänen.</span><span class="sxs-lookup"><span data-stu-id="6aa15-143">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="6aa15-144">Rättigheter i gMSA ger du bestäms av resurserna som du ansluter till.</span><span class="sxs-lookup"><span data-stu-id="6aa15-144">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="6aa15-145">Du har automatiskt inte administratörsrättigheter på alla datorer eller tjänster om inte datorn/service uttryckligen tilldelats gMSA-kontot admin-privilegier.</span><span class="sxs-lookup"><span data-stu-id="6aa15-145">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="6aa15-146">gMSA konton bör endast användas när åtkomst till nätverksresurser krävs på olika orsaker:</span><span class="sxs-lookup"><span data-stu-id="6aa15-146">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="6aa15-147">Det är svårare att spåra tillbaka åtgärder för att en användare när du använder ett konto för gMSA eftersom alla användare delar samma kör som-identitet.</span><span class="sxs-lookup"><span data-stu-id="6aa15-147">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="6aa15-148">Du måste kontakta PowerShell-session betyg och loggfilerna för att korrelera användare med sina åtgärder.</span><span class="sxs-lookup"><span data-stu-id="6aa15-148">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="6aa15-149">GMSA-kontot kan ha åtkomst till många nätverksresurser som anslutande användaren inte behöver åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="6aa15-149">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="6aa15-150">Alltid ett försök att begränsa gällande behörigheter i en JEA session att följa principen om minsta behörighet.</span><span class="sxs-lookup"><span data-stu-id="6aa15-150">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="6aa15-151">Gruppen hanterade tjänstkonton är bara tillgängliga i Windows PowerShell 5.1 eller nyare och på domänanslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="6aa15-151">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>


#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="6aa15-152">Mer information om Kör som-användare</span><span class="sxs-lookup"><span data-stu-id="6aa15-152">More information about run as users</span></span>

<span data-ttu-id="6aa15-153">Mer information om Kör som identiteter och hur de factor i säkerheten för en JEA session kan hittas i den [säkerhetsaspekter](security-considerations.md) artikel.</span><span class="sxs-lookup"><span data-stu-id="6aa15-153">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="6aa15-154">Sessionen betyg</span><span class="sxs-lookup"><span data-stu-id="6aa15-154">Session transcripts</span></span>

<span data-ttu-id="6aa15-155">Vi rekommenderar att du konfigurerar en JEA session konfigurationsfil att registreras automatiskt betyg användarnas sessioner.</span><span class="sxs-lookup"><span data-stu-id="6aa15-155">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="6aa15-156">PowerShell-session betyg innehåller information om den anslutande användaren kör som-identitet som har tilldelats dem, och kommandon som körs av användaren.</span><span class="sxs-lookup"><span data-stu-id="6aa15-156">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="6aa15-157">De kan vara användbara för en granskning team som behöver förstå vem som utförde en viss ändring i ett system.</span><span class="sxs-lookup"><span data-stu-id="6aa15-157">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="6aa15-158">Ange en sökväg till en mapp där betyg ska lagras för att konfigurera automatisk skrivfel i konfigurationsfilen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6aa15-158">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="6aa15-159">Den angivna mappen ska konfigureras för att förhindra att användare kan ändra eller ta bort alla data i den.</span><span class="sxs-lookup"><span data-stu-id="6aa15-159">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="6aa15-160">Betyg skrivs till mappen som kontot Lokalt System som kräver Läs- och skrivbehörighet till katalogen.</span><span class="sxs-lookup"><span data-stu-id="6aa15-160">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="6aa15-161">Vanliga användare bör ha ingen åtkomst till mappen och en begränsad uppsättning säkerhetsadministratörer ska ha åtkomst till att granska betyg.</span><span class="sxs-lookup"><span data-stu-id="6aa15-161">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="6aa15-162">Enheten</span><span class="sxs-lookup"><span data-stu-id="6aa15-162">User drive</span></span>

<span data-ttu-id="6aa15-163">Om du ansluter användarna kommer att behöva kopiera filer till eller från JEA slutpunkten för att köra ett kommando, kan du aktivera enhetens användare i konfigurationsfilen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6aa15-163">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="6aa15-164">Användarens enhet är en [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) som är mappad till en unik mapp för varje anslutning användare.</span><span class="sxs-lookup"><span data-stu-id="6aa15-164">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="6aa15-165">Den här mappen fungerar som ett utrymme att kopiera filer till eller från systemet, utan att ge dem åtkomst till fullständig filsystemet eller exponera filsystem-providern.</span><span class="sxs-lookup"><span data-stu-id="6aa15-165">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="6aa15-166">Användarens enhet innehållet är beständiga mellan sessioner för situationer där nätverksanslutningen kan avbrytas.</span><span class="sxs-lookup"><span data-stu-id="6aa15-166">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="6aa15-167">Som standard kan enhetens användare du lagra upp till 50MB data per användare.</span><span class="sxs-lookup"><span data-stu-id="6aa15-167">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="6aa15-168">Du kan begränsa mängden data som en användare kan använda med den *UserDriveMaximumSize* fältet.</span><span class="sxs-lookup"><span data-stu-id="6aa15-168">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="6aa15-169">Om du inte vill att data på enheten för användaren ska vara beständig kan du konfigurera en schemalagd aktivitet på systemet att automatiskt Rensa mappen varje natt.</span><span class="sxs-lookup"><span data-stu-id="6aa15-169">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="6aa15-170">Enhetens användare är endast tillgänglig i Windows PowerShell 5.1 eller nyare.</span><span class="sxs-lookup"><span data-stu-id="6aa15-170">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="6aa15-171">Rolldefinitioner</span><span class="sxs-lookup"><span data-stu-id="6aa15-171">Role definitions</span></span>

<span data-ttu-id="6aa15-172">Rolldefinitioner i en session konfigurationsfil definierar mappningen av *användare* till *roller*.</span><span class="sxs-lookup"><span data-stu-id="6aa15-172">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="6aa15-173">Alla användare eller grupp som ingår i det här fältet beviljas automatiskt behörighet till slutpunkten JEA när den är registrerad.</span><span class="sxs-lookup"><span data-stu-id="6aa15-173">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="6aa15-174">Varje användare eller grupp kan ingå som en nyckel i hashtabellen bara en gång, men kan tilldelas flera roller.</span><span class="sxs-lookup"><span data-stu-id="6aa15-174">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="6aa15-175">Namnet på rollen funktionen ska vara namnet på filen rollen kapaciteten utan .psrc filnamnstillägget.</span><span class="sxs-lookup"><span data-stu-id="6aa15-175">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="6aa15-176">Om en användare tillhör mer än en grupp i rolldefinitionen, kommer de att få åtkomst till roller för varje.</span><span class="sxs-lookup"><span data-stu-id="6aa15-176">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="6aa15-177">Om två roller ger åtkomst till samma cmdletar kan beviljas den mest Tillåtande parameteruppsättningen för användaren.</span><span class="sxs-lookup"><span data-stu-id="6aa15-177">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="6aa15-178">När du anger för lokala användare eller grupper i fältet roll definitioner, måste du använda datornamnet (inte *localhost* eller *.*) innan ett omvänt snedstreck.</span><span class="sxs-lookup"><span data-stu-id="6aa15-178">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="6aa15-179">Du kan kontrollera namnet på datorn genom att kontrollera den `$env:computername` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6aa15-179">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="6aa15-180">Sökordning för rollen kapaciteten</span><span class="sxs-lookup"><span data-stu-id="6aa15-180">Role capability search order</span></span>
<span data-ttu-id="6aa15-181">I exemplet ovan visas roll funktioner refereras av enkla namnet (filnamn utan filtillägget) i filen rollen kapaciteten.</span><span class="sxs-lookup"><span data-stu-id="6aa15-181">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="6aa15-182">Om flera rollen funktioner är tillgängliga på datorn med samma enkla namn, använder PowerShell dess implicit Sökordning för att välja filen effektiva rollen kapaciteten.</span><span class="sxs-lookup"><span data-stu-id="6aa15-182">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="6aa15-183">Kommer det att **inte** ge åtkomst till alla rollen kapaciteten för filer med samma namn.</span><span class="sxs-lookup"><span data-stu-id="6aa15-183">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="6aa15-184">JEA använder den `$env:PSModulePath` miljövariabeln för att avgöra vilka sökvägar för att söka efter roll funktionsfiler.</span><span class="sxs-lookup"><span data-stu-id="6aa15-184">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="6aa15-185">I var och en av dessa sökvägar söker JEA efter giltig PowerShell-modulerna som innehåller en undermapp ”RoleCapabilities”.</span><span class="sxs-lookup"><span data-stu-id="6aa15-185">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="6aa15-186">Precis som med importerar moduler föredrar JEA roll-funktioner som levereras med Windows till anpassad roll funktionerna med samma namn.</span><span class="sxs-lookup"><span data-stu-id="6aa15-186">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="6aa15-187">För andra namnkonflikter bestäms prioritet av den ordning som räknar Windows upp filer i katalogen (inte garanterat i alfabetisk ordning).</span><span class="sxs-lookup"><span data-stu-id="6aa15-187">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="6aa15-188">Den första roll kapaciteten filen hittades som matchar den önskade namn kommer att användas för den anslutande användaren.</span><span class="sxs-lookup"><span data-stu-id="6aa15-188">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="6aa15-189">Eftersom sökordningen för roll-funktionen är inte deterministisk när två eller flera funktioner för rollen har samma namn, är det **rekommenderar** som kontrollerar funktioner för rollen har unika namn på din dator.</span><span class="sxs-lookup"><span data-stu-id="6aa15-189">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="6aa15-190">Regler för villkorlig åtkomst</span><span class="sxs-lookup"><span data-stu-id="6aa15-190">Conditional access rules</span></span>

<span data-ttu-id="6aa15-191">Alla användare och grupper som ingår i fältet RoleDefinitions beviljas automatiskt åtkomst till JEA slutpunkter.</span><span class="sxs-lookup"><span data-stu-id="6aa15-191">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="6aa15-192">Regler för villkorlig åtkomst kan du förfina åtkomst och användaren måste tillhöra ytterligare säkerhetsgrupper som inte påverkar de roller som de har tilldelats.</span><span class="sxs-lookup"><span data-stu-id="6aa15-192">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="6aa15-193">Detta kan vara användbart om du vill integrera ”bara i tiden” privilegierad åtkomst lösning, autentisering med smartkort eller andra flerfunktionsautentisering lösning med JEA.</span><span class="sxs-lookup"><span data-stu-id="6aa15-193">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="6aa15-194">Regler för villkorlig åtkomst har definierats i fältet RequiredGroups i en konfigurationsfil för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6aa15-194">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="6aa15-195">Det, kan du ange en hash-tabell (du kan också kapslade) som använder 'Och' och 'Eller' för att skapa dina regler.</span><span class="sxs-lookup"><span data-stu-id="6aa15-195">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="6aa15-196">Här följer några exempel på hur du använder det här fältet:</span><span class="sxs-lookup"><span data-stu-id="6aa15-196">Here are some examples of how to leverage this field:</span></span>

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
> <span data-ttu-id="6aa15-197">Regler för villkorlig åtkomst är bara tillgängliga i Windows PowerShell 5.1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="6aa15-197">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="6aa15-198">Andra egenskaper</span><span class="sxs-lookup"><span data-stu-id="6aa15-198">Other properties</span></span>
<span data-ttu-id="6aa15-199">Sessionen konfigurationsfiler kan också göra allt en roll kapaciteten fil kan göra, men utan möjlighet att ge anslutande användare åtkomst till olika kommandon.</span><span class="sxs-lookup"><span data-stu-id="6aa15-199">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="6aa15-200">Om du vill tillåta alla användare åtkomst till specifika cmdlet: ar, funktioner och leverantörer kan du göra det direkt i konfigurationsfilen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6aa15-200">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="6aa15-201">En fullständig lista över egenskaper som stöds i konfigurationsfilen session kör `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="6aa15-201">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="6aa15-202">Testa en session-konfigurationsfil</span><span class="sxs-lookup"><span data-stu-id="6aa15-202">Testing a session configuration file</span></span>

<span data-ttu-id="6aa15-203">Du kan testa en session konfigurationen med hjälp av den [Test PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6aa15-203">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="6aa15-204">Det rekommenderas starkt att du testar din session-konfigurationsfil om du har redigerat filen pssc manuellt med hjälp av en textredigerare så syntax är korrekt.</span><span class="sxs-lookup"><span data-stu-id="6aa15-204">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="6aa15-205">Om en session konfigurationsfil inte klarar det här testet, kan den inte registrerats på datorn.</span><span class="sxs-lookup"><span data-stu-id="6aa15-205">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="6aa15-206">Exempelkonfigurationsfilen för session</span><span class="sxs-lookup"><span data-stu-id="6aa15-206">Sample session configuration file</span></span>

<span data-ttu-id="6aa15-207">Nedan visas en komplett exempel som visar hur du skapar och validera en sessionskonfiguration för JEA.</span><span class="sxs-lookup"><span data-stu-id="6aa15-207">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="6aa15-208">Observera att rolldefinitioner skapas och lagras i den `$roles` variabel för bekvämlighets skull och läsbarhet.</span><span class="sxs-lookup"><span data-stu-id="6aa15-208">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="6aa15-209">Det är inte ett krav att göra detta.</span><span class="sxs-lookup"><span data-stu-id="6aa15-209">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="6aa15-210">Uppdatera session konfigurationsfiler</span><span class="sxs-lookup"><span data-stu-id="6aa15-210">Updating session configuration files</span></span>

<span data-ttu-id="6aa15-211">Om du behöver ändra egenskaperna för en sessionskonfiguration JEA, inklusive koppling av användare till roller, måste du [avregistrera](register-jea.md#unregistering-jea-configurations) och [Omregistrera](register-jea.md) JEA sessionskonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6aa15-211">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="6aa15-212">När du registrera JEA sessionskonfigurationen kan du använda en uppdaterad PowerShell-session konfigurationsfil som innehåller dina önskade ändringar.</span><span class="sxs-lookup"><span data-stu-id="6aa15-212">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6aa15-213">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="6aa15-213">Next steps</span></span>

- [<span data-ttu-id="6aa15-214">Registrera en JEA-konfiguration</span><span class="sxs-lookup"><span data-stu-id="6aa15-214">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="6aa15-215">Författare JEA roller</span><span class="sxs-lookup"><span data-stu-id="6aa15-215">Author JEA roles</span></span>](role-capabilities.md)