---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
contributor: ryanpu
title: "Förbättringar av Just Enough Administration JEA)"
ms.openlocfilehash: 2811b4deb3f4fca513791c7389ee5f9f877dbfe8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="6826a-103">Förbättringar av Just Enough Administration JEA)</span><span class="sxs-lookup"><span data-stu-id="6826a-103">Improvements to Just Enough Administration (JEA)</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="6826a-104">Begränsad filkopiering till eller från JEA slutpunkter</span><span class="sxs-lookup"><span data-stu-id="6826a-104">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="6826a-105">Du kan nu via fjärranslutning kopiera filer till/från en JEA slutpunkt och resten vara säker på att den anslutande användaren inte kan kopiera bara *alla* filen på datorn.</span><span class="sxs-lookup"><span data-stu-id="6826a-105">You can now remotely copy files to/from a JEA endpoint and rest assured that the connecting user can't copy just *any* file on your system.</span></span>
<span data-ttu-id="6826a-106">Detta är möjligt genom att konfigurera din PSSC fil om du vill montera en enhet för användaren för att ansluta användare.</span><span class="sxs-lookup"><span data-stu-id="6826a-106">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span>
<span data-ttu-id="6826a-107">Användarens enhet är en ny PSDrive som är unik för varje anslutande användaren och kvarstår mellan sessioner.</span><span class="sxs-lookup"><span data-stu-id="6826a-107">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span>
<span data-ttu-id="6826a-108">När du kopiera objekt för att kopiera filer till eller från en JEA session, är den begränsad till att bara tillåta åtkomst till användarens enhet.</span><span class="sxs-lookup"><span data-stu-id="6826a-108">When Copy-Item is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span>
<span data-ttu-id="6826a-109">Försök att kopiera filer till andra PSDrive misslyckas.</span><span class="sxs-lookup"><span data-stu-id="6826a-109">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="6826a-110">Använd följande nya fält om du vill konfigurera enheten för användaren i konfigurationsfilen JEA session:</span><span class="sxs-lookup"><span data-stu-id="6826a-110">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="6826a-111">Mappen säkerhetskopiering enhetens användare kommer att skapas på`$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="6826a-111">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="6826a-112">Om du vill använda enheten och kopiera filer till/från en JEA slutpunkt som konfigurerats för att exponera enhetens användare, Använd den `-ToSession` och `-FromSession` parametrar på Kopiera-objekt.</span><span class="sxs-lookup"><span data-stu-id="6826a-112">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on Copy-Item.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="6826a-113">Du kan sedan skriva anpassade funktioner för att bearbeta de data som lagras i enhetens användare och göra dem tillgängliga för användare i rollen kapaciteten filen.</span><span class="sxs-lookup"><span data-stu-id="6826a-113">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="6826a-114">Stöd för gruppen hanterade konton</span><span class="sxs-lookup"><span data-stu-id="6826a-114">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="6826a-115">I vissa fall kan en aktivitet som en användare behöver genomföra i en session JEA behöver åtkomst till resurser utanför den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6826a-115">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span>
<span data-ttu-id="6826a-116">När en session JEA är konfigurerad för att använda ett virtuellt konto, visas alla försök att nå dessa resurser kan komma från den lokala datorns identitet, inte virtuellt konto eller anslutna användaren.</span><span class="sxs-lookup"><span data-stu-id="6826a-116">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span>
<span data-ttu-id="6826a-117">I TP5, finns det stöd för att köra JEA et i sammanhang med en [Grupphanterat tjänstkonto] (https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), vilket gör det enklare att komma åt nätverksresurser med hjälp av en domän identitet.</span><span class="sxs-lookup"><span data-stu-id="6826a-117">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="6826a-118">Om du vill konfigurera en JEA session ska köras under ett konto för gMSA använder du följande nya nyckel i filen PSSC:</span><span class="sxs-lookup"><span data-stu-id="6826a-118">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> <span data-ttu-id="6826a-119">**Obs:** Grupphanterade tjänstkonton som inte ger isolering eller begränsad omfattning virtuella konton.</span><span class="sxs-lookup"><span data-stu-id="6826a-119">**Note:** Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="6826a-120">Varje anslutande användaren kommer att dela samma gMSA-identitet som kan ha behörigheter för hela företaget.</span><span class="sxs-lookup"><span data-stu-id="6826a-120">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span>
> <span data-ttu-id="6826a-121">Var försiktig när du väljer att använda ett gMSA och föredrar alltid virtuella konton som är begränsade till den lokala datorn när det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="6826a-121">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="6826a-122">Principer för villkorlig åtkomst</span><span class="sxs-lookup"><span data-stu-id="6826a-122">Conditional access policies</span></span>

<span data-ttu-id="6826a-123">JEA är bra på att begränsa vad någon kan göra när de har anslutit till ett system för att hantera den, men vad händer om du även vill begränsa *när* någon kan använda JEA?</span><span class="sxs-lookup"><span data-stu-id="6826a-123">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span>
<span data-ttu-id="6826a-124">Vi har lagt till konfigurationsalternativ i sessionen configuration-filer (.pssc) så att du kan ange säkerhetsgrupper som en användare måste tillhöra för att upprätta en session JEA.</span><span class="sxs-lookup"><span data-stu-id="6826a-124">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span>
<span data-ttu-id="6826a-125">Detta kan vara särskilt användbart om du har ett precis i tid (JIT) i din miljö och vill göra användarna Windows innan du använder en hög behörighetsnivå JEA slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="6826a-125">This can be particularly helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="6826a-126">Den nya *RequiredGroups* fält i PSSC-filen kan du ange logik för att avgöra om en användare kan ansluta till JEA.</span><span class="sxs-lookup"><span data-stu-id="6826a-126">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span>
<span data-ttu-id="6826a-127">Det består av att ange en hash-tabell (du kan också kapslade) som använder den 'Och' och 'Eller' för att skapa dina regler.</span><span class="sxs-lookup"><span data-stu-id="6826a-127">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="6826a-128">Här följer några exempel på hur du använder det här fältet:</span><span class="sxs-lookup"><span data-stu-id="6826a-128">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="6826a-129">Fast: Virtuella konton stöds nu i Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="6826a-129">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>
<span data-ttu-id="6826a-130">I WMF 5.1 är du nu kunna använda virtuella konton på Windows Server 2008 R2, aktivera konsekventa konfigurationer och funktionsparitet via Windows Server 2008 R2 - 2016.</span><span class="sxs-lookup"><span data-stu-id="6826a-130">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span>
<span data-ttu-id="6826a-131">Virtuella konton förblir stöds inte när du använder JEA i Windows 7.</span><span class="sxs-lookup"><span data-stu-id="6826a-131">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>

