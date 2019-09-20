---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Förbättringar i JEA (Just Enough Administration)
ms.openlocfilehash: 847ae92a6225023bcd0ee3dfe7c7058bdc356836
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71145035"
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="1f4cd-103">Förbättringar i JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="1f4cd-103">Improvements to Just Enough Administration (JEA)</span></span>

<span data-ttu-id="1f4cd-104">Bara tillräckligt med administration är en ny funktion i WMF 5,0 som möjliggör rollbaserad administration via PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-104">Just Enough Administration is a new feature in WMF 5.0 that enables role-based administration through PowerShell remoting.</span></span> <span data-ttu-id="1f4cd-105">Den utökar den befintliga begränsade slut punkts infrastrukturen genom att tillåta icke-administratörer att köra vissa kommandon, skript och körbara filer som administratör.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-105">It extends the existing constrained endpoint infrastructure by allowing non-administrators to run specific commands, scripts, and executables as an administrator.</span></span> <span data-ttu-id="1f4cd-106">På så sätt kan du minska antalet fullständiga administratörer i din miljö och förbättra säkerheten.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-106">This enables you to reduce the number of full administrators in your environment and improve security.</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="1f4cd-107">Begränsad fil kopiering till/från JEA-slutpunkter</span><span class="sxs-lookup"><span data-stu-id="1f4cd-107">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="1f4cd-108">Du kan nu fjärrkopiera filer till/från en JEA-slutpunkt och vara säker på att den anslutande användaren inte kan kopiera bara *några* filer i systemet.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-108">You can now remotely copy files to/from a JEA endpoint and be assured that the connecting user can't copy just *any* file on your system.</span></span> <span data-ttu-id="1f4cd-109">Detta är möjligt genom att konfigurera din PSSC-fil för att montera en användar enhet för att ansluta användare.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-109">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span> <span data-ttu-id="1f4cd-110">Användar enheten är en ny PSDrive som är unik för varje användare som ansluter och behålls mellan sessioner.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-110">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span> <span data-ttu-id="1f4cd-111">När `Copy-Item` används för att kopiera filer till eller från en Jea-session är det begränsat att endast tillåta åtkomst till användar enheten.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-111">When `Copy-Item` is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span> <span data-ttu-id="1f4cd-112">Försök att kopiera filer till andra PSDrive kommer att Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-112">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="1f4cd-113">Använd följande nya fält för att konfigurera användar enheten i JEA-sessionens konfigurations fil:</span><span class="sxs-lookup"><span data-stu-id="1f4cd-113">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="1f4cd-114">Mappen som används för att återställa användar enheten skapas på`$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="1f4cd-114">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="1f4cd-115">Om du vill använda användar enheten och kopiera filer till/från en Jea-slutpunkt som kon figurer ATS för att exponera `-ToSession` användar `-FromSession` enheten använder `Copy-Item`du parametrarna och på.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-115">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on `Copy-Item`.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="1f4cd-116">Du kan sedan skriva anpassade funktioner för att bearbeta de data som lagras i användar enheten och göra dem tillgängliga för användare i din roll funktions fil.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-116">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="1f4cd-117">Stöd för grupphanterade tjänst konton</span><span class="sxs-lookup"><span data-stu-id="1f4cd-117">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="1f4cd-118">I vissa fall kan en uppgift som en användare behöver utföra i en JEA-session behöva komma åt resurser bortom den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-118">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span> <span data-ttu-id="1f4cd-119">När en JEA-session har kon figurer ATS för att använda ett virtuellt konto, kommer alla försök att komma åt sådana resurser att komma från den lokala datorns identitet, inte det virtuella kontot eller den anslutna användaren.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-119">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span> <span data-ttu-id="1f4cd-120">I TP5 har vi aktiverat stöd för att köra JEA under kontexten för ett [grupphanterat tjänst konto](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), vilket gör det mycket enklare att komma åt nätverks resurser med hjälp av en domän identitet.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-120">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="1f4cd-121">Om du vill konfigurera en JEA-session att köras under ett gMSA-konto, använder du följande nya nyckel i din PSSC-fil:</span><span class="sxs-lookup"><span data-stu-id="1f4cd-121">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> <span data-ttu-id="1f4cd-122">Grupphanterade tjänst konton ger inte isolering eller begränsat omfång för virtuella konton.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-122">Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="1f4cd-123">Alla anslutna användare delar samma gMSA-identitet, som kan ha behörigheter i hela företaget.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-123">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span> <span data-ttu-id="1f4cd-124">Var försiktig när du väljer att använda en gMSA och föredra alltid virtuella konton som är begränsade till den lokala datorn när det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-124">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="1f4cd-125">Principer för villkorlig åtkomst</span><span class="sxs-lookup"><span data-stu-id="1f4cd-125">Conditional access policies</span></span>

<span data-ttu-id="1f4cd-126">JEA är bra om du begränsar vad någon kan göra när de har anslutit till ett system för att hantera det, men vad du vill begränsa *när* någon kan använda Jea?</span><span class="sxs-lookup"><span data-stu-id="1f4cd-126">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span> <span data-ttu-id="1f4cd-127">Vi har lagt till konfigurations alternativen i sessionens konfigurationsfiler (. PSSC) så att du kan ange säkerhets grupper som en användare måste tillhöra för att kunna upprätta en JEA-session.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-127">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span> <span data-ttu-id="1f4cd-128">Detta är särskilt användbart om du har ett JIT-system (just in Time) i din miljö och vill göra det möjligt för dina användare att öka sina privilegier innan de får åtkomst till en JEA-slutpunkt med hög privilegier.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-128">This is especially helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="1f4cd-129">I fältet nytt *RequiredGroups* i PSSC-filen kan du ange logiken för att avgöra om en användare kan ansluta till Jea.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-129">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span> <span data-ttu-id="1f4cd-130">Det består av att ange en hash (eventuellt kapslad) som använder-och-och-eller-nycklar för att skapa regler.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-130">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="1f4cd-131">Här följer några exempel på hur du använder det här fältet:</span><span class="sxs-lookup"><span data-stu-id="1f4cd-131">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="1f4cd-132">Fastsatt Virtuella konton stöds nu på Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="1f4cd-132">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>

<span data-ttu-id="1f4cd-133">I WMF 5,1 kan du nu använda virtuella konton på Windows Server 2008 R2, vilket möjliggör konsekventa konfigurationer och funktions paritet över Windows Server 2008 R2-2016.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-133">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span> <span data-ttu-id="1f4cd-134">Virtuella konton är inte stödda när du använder JEA i Windows 7.</span><span class="sxs-lookup"><span data-stu-id="1f4cd-134">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>