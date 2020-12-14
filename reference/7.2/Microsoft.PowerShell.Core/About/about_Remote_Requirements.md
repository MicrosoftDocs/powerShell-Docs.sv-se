---
description: Beskriver system krav och konfigurations krav för att köra fjärrkommandon i PowerShell.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Requirements
ms.openlocfilehash: 4a994ded51195e5932af7bb4af0b2e6fb3a67857
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708418"
---
# <a name="about-remote-requirements"></a><span data-ttu-id="96e4f-103">Om fjär krav</span><span class="sxs-lookup"><span data-stu-id="96e4f-103">About Remote Requirements</span></span>

## <a name="short-description"></a><span data-ttu-id="96e4f-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="96e4f-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="96e4f-105">Beskriver system krav och konfigurations krav för att köra fjärrkommandon i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96e4f-105">Describes the system requirements and configuration requirements for running remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="96e4f-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="96e4f-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="96e4f-107">I det här avsnittet beskrivs system kraven, användar kraven och resurs kraven för att upprätta fjärr anslutningar och köra fjärrkommandon i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96e4f-107">This topic describes the system requirements, user requirements, and resource requirements for establishing remote connections and running remote commands in PowerShell.</span></span> <span data-ttu-id="96e4f-108">Den innehåller också instruktioner för att konfigurera fjärråtgärder.</span><span class="sxs-lookup"><span data-stu-id="96e4f-108">It also provides instructions for configuring remote operations.</span></span>

<span data-ttu-id="96e4f-109">Obs! många cmdletar (inklusive get-service, get-process, get-WMIObject, get-EventLog och Get-WinEvent cmdlets) hämtar objekt från fjärrdatorer genom att använda Microsoft .NET Ramverks metoder för att hämta objekten.</span><span class="sxs-lookup"><span data-stu-id="96e4f-109">Note: Many cmdlets (including the Get-Service, Get-Process, Get-WMIObject, Get-EventLog, and Get-WinEvent cmdlets) get objects from remote computers by using Microsoft .NET Framework methods to retrieve the objects.</span></span> <span data-ttu-id="96e4f-110">De använder inte PowerShell-infrastrukturen för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="96e4f-110">They do not use the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="96e4f-111">Kraven i det här dokumentet gäller inte för dessa cmdletar.</span><span class="sxs-lookup"><span data-stu-id="96e4f-111">The requirements in this document do not apply to these cmdlets.</span></span>

<span data-ttu-id="96e4f-112">Om du vill hitta de cmdlet: ar som har en ComputerName-parameter men inte använda PowerShell-fjärrkommunikation läser du beskrivningen av ComputerName-parametern för cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="96e4f-112">To find the cmdlets that have a ComputerName parameter but do not use PowerShell remoting, read the description of the ComputerName parameter of the cmdlets.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="96e4f-113">SYSTEM KRAV</span><span class="sxs-lookup"><span data-stu-id="96e4f-113">SYSTEM REQUIREMENTS</span></span>

<span data-ttu-id="96e4f-114">Om du vill köra fjärrsessioner på Windows PowerShell 3,0 måste lokala och fjärranslutna datorer ha följande:</span><span class="sxs-lookup"><span data-stu-id="96e4f-114">To run remote sessions on Windows PowerShell 3.0, the local and remote computers must have the following:</span></span>

- <span data-ttu-id="96e4f-115">Windows PowerShell 3,0 eller senare</span><span class="sxs-lookup"><span data-stu-id="96e4f-115">Windows PowerShell 3.0 or later</span></span>
- <span data-ttu-id="96e4f-116">Microsoft .NET Framework 4 eller senare</span><span class="sxs-lookup"><span data-stu-id="96e4f-116">The Microsoft .NET Framework 4 or later</span></span>
- <span data-ttu-id="96e4f-117">Windows Remote Management 3,0</span><span class="sxs-lookup"><span data-stu-id="96e4f-117">Windows Remote Management 3.0</span></span>

<span data-ttu-id="96e4f-118">Om du vill köra fjärrsessioner på Windows PowerShell 2,0 måste lokala och fjärranslutna datorer ha följande:</span><span class="sxs-lookup"><span data-stu-id="96e4f-118">To run remote sessions on Windows PowerShell 2.0, the local and remote computers must have the following:</span></span>

- <span data-ttu-id="96e4f-119">Windows PowerShell 2,0 eller senare</span><span class="sxs-lookup"><span data-stu-id="96e4f-119">Windows PowerShell 2.0 or later</span></span>
- <span data-ttu-id="96e4f-120">Microsoft .NET Framework 2,0 eller senare</span><span class="sxs-lookup"><span data-stu-id="96e4f-120">The Microsoft .NET Framework 2.0 or later</span></span>
- <span data-ttu-id="96e4f-121">Windows Remote Management 2,0</span><span class="sxs-lookup"><span data-stu-id="96e4f-121">Windows Remote Management 2.0</span></span>

<span data-ttu-id="96e4f-122">Du kan skapa fjärrsessioner mellan datorer som kör Windows PowerShell 2,0 och Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="96e4f-122">You can create remote sessions between computers running Windows PowerShell 2.0 and Windows PowerShell 3.0.</span></span> <span data-ttu-id="96e4f-123">Funktioner som bara körs på Windows PowerShell 3,0, till exempel möjligheten att koppla från och återansluta till sessioner, är bara tillgängliga när båda datorerna kör Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="96e4f-123">However, features that run only on Windows PowerShell 3.0, such as the ability to disconnect and reconnect to sessions, are available only when both computers are running Windows PowerShell 3.0.</span></span>

<span data-ttu-id="96e4f-124">Du hittar versions numret för en installerad version av PowerShell med hjälp av den automatiska variabeln $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="96e4f-124">To find the version number of an installed version of PowerShell, use the $PSVersionTable automatic variable.</span></span>

<span data-ttu-id="96e4f-125">Windows Remote Management (WinRM) 3,0 och Microsoft .NET Framework 4 ingår i Windows 8, Windows Server 2012 och senare versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="96e4f-125">Windows Remote Management (WinRM) 3.0 and Microsoft .NET Framework 4 are included in Windows 8, Windows Server 2012, and newer releases of the Windows operating system.</span></span> <span data-ttu-id="96e4f-126">WinRM 3,0 ingår i Windows Management Framework 3,0 för äldre operativ system.</span><span class="sxs-lookup"><span data-stu-id="96e4f-126">WinRM 3.0 is included in Windows Management Framework 3.0 for older operating systems.</span></span> <span data-ttu-id="96e4f-127">Installationen Miss lyckas om datorn inte har den version av WinRM eller Microsoft .NET Framework som krävs.</span><span class="sxs-lookup"><span data-stu-id="96e4f-127">If the computer does not have the required version of WinRM or the Microsoft .NET Framework, the installation fails.</span></span>

## <a name="user-permissions"></a><span data-ttu-id="96e4f-128">ANVÄNDARBEHÖRIGHETER</span><span class="sxs-lookup"><span data-stu-id="96e4f-128">USER PERMISSIONS</span></span>

<span data-ttu-id="96e4f-129">Om du vill skapa fjärrsessioner och köra fjärrkommandon måste den aktuella användaren som standard vara medlem i gruppen Administratörer på fjärrdatorn eller ange autentiseringsuppgifter för en administratör.</span><span class="sxs-lookup"><span data-stu-id="96e4f-129">To create remote sessions and run remote commands, by default, the current user must be a member of the Administrators group on the remote computer or provide the credentials of an administrator.</span></span> <span data-ttu-id="96e4f-130">Annars Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="96e4f-130">Otherwise, the command fails.</span></span>

<span data-ttu-id="96e4f-131">De behörigheter som krävs för att skapa sessioner och köra kommandon på en fjärrdator (eller i en fjärran sluten session på den lokala datorn) upprättas av konfigurationen av sessionen (även kallat "slut punkt") på den fjärrdator som sessionen ansluter till.</span><span class="sxs-lookup"><span data-stu-id="96e4f-131">The permissions required to create sessions and run commands on a remote computer (or in a remote session on the local computer) are established by the session configuration (also known as an "endpoint") on the remote computer to which the session connects.</span></span> <span data-ttu-id="96e4f-132">Mer specifikt bestämmer säkerhets beskrivningen i konfigurationen vem som har åtkomst till sessionen och vem som kan använda den för att ansluta.</span><span class="sxs-lookup"><span data-stu-id="96e4f-132">Specifically, the security descriptor on the session configuration determines who has access to the session configuration and who can use it to connect.</span></span>

<span data-ttu-id="96e4f-133">Säkerhets beskrivarna på standardkonfigurationerna för sessioner, Microsoft. PowerShell, Microsoft. PowerShell32 och Microsoft. PowerShell. workflow, tillåter endast åtkomst till medlemmar i gruppen Administratörer.</span><span class="sxs-lookup"><span data-stu-id="96e4f-133">The security descriptors on the default session configurations, Microsoft.PowerShell, Microsoft.PowerShell32, and Microsoft.PowerShell.Workflow, allow access only to members of the Administrators group.</span></span>

<span data-ttu-id="96e4f-134">Om den aktuella användaren inte har behörighet att använda-sessionen, kan kommandot för att köra ett kommando (som använder en tillfällig session) eller skapa en beständig session på fjärrdatorn Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="96e4f-134">If the current user doesn't have permission to use the session configuration, the command to run a command (which uses a temporary session) or create a persistent session on the remote computer fails.</span></span> <span data-ttu-id="96e4f-135">Användaren kan använda parametern ConfigurationName för cmdletar som skapar sessioner för att välja en annan sessionsinformation, om en sådan finns tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="96e4f-135">The user can use the ConfigurationName parameter of cmdlets that create sessions to select a different session configuration, if one is available.</span></span>

<span data-ttu-id="96e4f-136">Medlemmar i gruppen Administratörer på en dator kan bestämma vem som har behörighet att fjärrans luta till datorn genom att ändra säkerhets beskrivarna på standardkonfigurationerna för sessioner och genom att skapa nya sessionsinställningar med olika säkerhets beskrivningar.</span><span class="sxs-lookup"><span data-stu-id="96e4f-136">Members of the Administrators group on a computer can determine who has permission to connect to the computer remotely by changing the security descriptors on the default session configurations and by creating new session configurations with different security descriptors.</span></span>

<span data-ttu-id="96e4f-137">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="96e4f-137">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

## <a name="windows-network-locations"></a><span data-ttu-id="96e4f-138">WINDOWS NÄTVERKS PLATSER</span><span class="sxs-lookup"><span data-stu-id="96e4f-138">WINDOWS NETWORK LOCATIONS</span></span>

<span data-ttu-id="96e4f-139">Från och med Windows PowerShell 3,0 kan Enable-PSRemoting cmdlet aktivera fjärr kommunikation på klient-och Server versioner av Windows i privata, domän och offentliga nätverk.</span><span class="sxs-lookup"><span data-stu-id="96e4f-139">Beginning in Windows PowerShell 3.0, the Enable-PSRemoting cmdlet can enable remoting on client and server versions of Windows on private, domain, and public networks.</span></span>

<span data-ttu-id="96e4f-140">I Server versioner av Windows med privata nätverk och domän nätverk skapar cmdleten Enable-PSRemoting brand Väggs regler som tillåter obegränsad fjärråtkomst.</span><span class="sxs-lookup"><span data-stu-id="96e4f-140">On server versions of Windows with private and domain networks, the Enable-PSRemoting cmdlet creates firewall rules that allow unrestricted remote access.</span></span> <span data-ttu-id="96e4f-141">Det skapar också en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät.</span><span class="sxs-lookup"><span data-stu-id="96e4f-141">It also creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span> <span data-ttu-id="96e4f-142">Den här brand Väggs regeln för lokalt undernät är aktive rad som standard på Server versioner av Windows i offentliga nätverk, men Enable-PSRemoting tillämpar regeln på om den har ändrats eller tagits bort.</span><span class="sxs-lookup"><span data-stu-id="96e4f-142">This local subnet firewall rule is enabled by default on server versions of Windows on public networks, but Enable-PSRemoting reapplies the rule in case it was changed or deleted.</span></span>

<span data-ttu-id="96e4f-143">I klient versioner av Windows med privata nätverk och domän nätverk, skapar Enable-PSRemoting-cmdlet som standard brand Väggs regler som tillåter obegränsad fjärråtkomst.</span><span class="sxs-lookup"><span data-stu-id="96e4f-143">On client versions of Windows with private and domain networks, by default, the Enable-PSRemoting cmdlet creates firewall rules that allow unrestricted remote access.</span></span>

<span data-ttu-id="96e4f-144">Om du vill aktivera fjärr kommunikation på klient versioner av Windows med offentliga nätverk använder du parametern SkipNetworkProfileCheck i Enable-PSRemoting-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="96e4f-144">To enable remoting on client versions of Windows with public networks, use the SkipNetworkProfileCheck parameter of the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="96e4f-145">Den skapar en brand Väggs regel som endast tillåter fjärråtkomst från datorer i samma lokala undernät.</span><span class="sxs-lookup"><span data-stu-id="96e4f-145">It creates a firewall rule that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="96e4f-146">Om du vill ta bort begränsningen för lokal undernät i offentliga nätverk och tillåta fjärråtkomst från alla platser på klient-och Server versioner av Windows, använder du Set-NetFirewallRule cmdlet i modulen netsecurity.</span><span class="sxs-lookup"><span data-stu-id="96e4f-146">To remove the local subnet restriction on public networks and allow remote access from all locations on client and server versions of Windows, use the Set-NetFirewallRule cmdlet in the NetSecurity module.</span></span> <span data-ttu-id="96e4f-147">Kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="96e4f-147">Run the following command:</span></span>

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

<span data-ttu-id="96e4f-148">I Windows PowerShell 2,0, i Server versioner av Windows, skapar Enable-PSRemoting brand Väggs regler som tillåter fjärråtkomst i alla nätverk.</span><span class="sxs-lookup"><span data-stu-id="96e4f-148">In Windows PowerShell 2.0, on server versions of Windows, Enable-PSRemoting creates firewall rules that permit remote access on all networks.</span></span>

<span data-ttu-id="96e4f-149">I Windows PowerShell 2,0 skapar Enable-PSRemoting brand Väggs regler endast för privata nätverk och domän nätverk på klient versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="96e4f-149">In Windows PowerShell 2.0, on client versions of Windows, Enable-PSRemoting creates firewall rules only on private and domain networks.</span></span> <span data-ttu-id="96e4f-150">Om nätverks platsen är offentlig Enable-PSRemoting Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="96e4f-150">If the network location is public, Enable-PSRemoting fails.</span></span>

## <a name="run-as-administrator"></a><span data-ttu-id="96e4f-151">KÖR SOM ADMINISTRATÖR</span><span class="sxs-lookup"><span data-stu-id="96e4f-151">RUN AS ADMINISTRATOR</span></span>

<span data-ttu-id="96e4f-152">Administratörs behörighet krävs för följande fjärr kommunikations åtgärder:</span><span class="sxs-lookup"><span data-stu-id="96e4f-152">Administrator privileges are required for the following remoting operations:</span></span>

- <span data-ttu-id="96e4f-153">Upprätta en fjärr anslutning till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="96e4f-153">Establishing a remote connection to the local computer.</span></span> <span data-ttu-id="96e4f-154">Detta kallas ofta "loopback"-scenario.</span><span class="sxs-lookup"><span data-stu-id="96e4f-154">This is commonly known as a "loopback" scenario.</span></span>

- <span data-ttu-id="96e4f-155">Hantera sessionsinställningar på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="96e4f-155">Managing session configurations on the local computer.</span></span>

- <span data-ttu-id="96e4f-156">Visa och ändra WS-Management inställningar på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="96e4f-156">Viewing and changing WS-Management settings on the local computer.</span></span> <span data-ttu-id="96e4f-157">Detta är inställningarna i noden LocalHost för kommandot WSMAN: Drive.</span><span class="sxs-lookup"><span data-stu-id="96e4f-157">These are the settings in the LocalHost node of the WSMAN: drive.</span></span>

<span data-ttu-id="96e4f-158">Om du vill utföra dessa uppgifter måste du starta PowerShell med alternativet "kör som administratör" även om du är medlem i gruppen Administratörer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="96e4f-158">To perform these tasks, you must start PowerShell with the "Run as administrator" option even if you are a member of the Administrators group on the local computer.</span></span>

<span data-ttu-id="96e4f-159">Starta Windows PowerShell med alternativet "kör som administratör" i Windows 7 och Windows Server 2008 R2:</span><span class="sxs-lookup"><span data-stu-id="96e4f-159">In Windows 7 and in Windows Server 2008 R2, to start Windows PowerShell with the "Run as administrator" option:</span></span>

1. <span data-ttu-id="96e4f-160">Klicka på Start, klicka på alla program, klicka på tillbehör och klicka sedan på Windows PowerShell-mappen.</span><span class="sxs-lookup"><span data-stu-id="96e4f-160">Click Start, click All Programs, click Accessories, and then click the Windows PowerShell folder.</span></span>
2. <span data-ttu-id="96e4f-161">Högerklicka på Windows PowerShell och klicka sedan på Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="96e4f-161">Right-click Windows PowerShell, and then click "Run as administrator".</span></span>

<span data-ttu-id="96e4f-162">Starta Windows PowerShell med alternativet "kör som administratör":</span><span class="sxs-lookup"><span data-stu-id="96e4f-162">To start Windows PowerShell with the "Run as administrator" option:</span></span>

1. <span data-ttu-id="96e4f-163">Klicka på Start, klicka på alla program och klicka sedan på Windows PowerShell-mappen.</span><span class="sxs-lookup"><span data-stu-id="96e4f-163">Click Start, click All Programs, and then click the Windows PowerShell folder.</span></span>
2. <span data-ttu-id="96e4f-164">Högerklicka på Windows PowerShell och klicka sedan på Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="96e4f-164">Right-click Windows PowerShell, and then click "Run as administrator".</span></span>

<span data-ttu-id="96e4f-165">Alternativet "kör som administratör" är också tillgängligt i andra Windows Explorer-poster för Windows PowerShell, inklusive genvägar.</span><span class="sxs-lookup"><span data-stu-id="96e4f-165">The "Run as administrator" option is also available in other Windows Explorer entries for Windows PowerShell, including shortcuts.</span></span> <span data-ttu-id="96e4f-166">Högerklicka bara på objektet och klicka sedan på Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="96e4f-166">Just right-click the item, and then click "Run as administrator".</span></span>

<span data-ttu-id="96e4f-167">När du startar Windows PowerShell från ett annat program, till exempel Cmd.exe, använder du alternativet "kör som administratör" för att starta programmet.</span><span class="sxs-lookup"><span data-stu-id="96e4f-167">When you start Windows PowerShell from another program such as Cmd.exe, use the "Run as administrator" option to start the program.</span></span>

## <a name="how-to-configure-your-computer-for-remoting"></a><span data-ttu-id="96e4f-168">SÅ HÄR KONFIGURERAR DU DIN DATOR FÖR FJÄRR KOMMUNIKATION</span><span class="sxs-lookup"><span data-stu-id="96e4f-168">HOW TO CONFIGURE YOUR COMPUTER FOR REMOTING</span></span>

<span data-ttu-id="96e4f-169">Datorer som kör alla Windows-versioner som stöds kan upprätta fjärr anslutningar till och köra fjärrkommandon i PowerShell utan någon konfiguration.</span><span class="sxs-lookup"><span data-stu-id="96e4f-169">Computers running all supported versions of Windows can establish remote connections to and run remote commands in PowerShell without any configuration.</span></span> <span data-ttu-id="96e4f-170">Men om du vill ta emot anslutningar och tillåta användare att skapa lokala och fjärranslutna användar hanterade PowerShell-sessioner ("PSSessions") och köra kommandon på den lokala datorn måste du aktivera PowerShell-fjärrkommunikation på datorn.</span><span class="sxs-lookup"><span data-stu-id="96e4f-170">However, to receive connections, and allow users to create local and remote user-managed PowerShell sessions ("PSSessions") and run commands on the local computer, you must enable PowerShell remoting on the computer.</span></span>

<span data-ttu-id="96e4f-171">Windows Server 2012 och nyare versioner av Windows Server är aktiverade för PowerShell-fjärrkommunikation som standard.</span><span class="sxs-lookup"><span data-stu-id="96e4f-171">Windows Server 2012 and newer releases of Windows Server are enabled for PowerShell remoting by default.</span></span> <span data-ttu-id="96e4f-172">Om inställningarna har ändrats kan du återställa standardinställningarna genom att köra cmdleten Enable-PSRemoting.</span><span class="sxs-lookup"><span data-stu-id="96e4f-172">If the settings are changed, you can restore the default settings by running the Enable-PSRemoting cmdlet.</span></span>

<span data-ttu-id="96e4f-173">I alla andra versioner av Windows som stöds måste du köra cmdleten Enable-PSRemoting för att aktivera PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="96e4f-173">On all other supported versions of Windows, you need to run the Enable-PSRemoting cmdlet to enable PowerShell remoting.</span></span>

<span data-ttu-id="96e4f-174">Funktionerna för fjärr kommunikation i PowerShell stöds av WinRM-tjänsten, som är Microsofts implementering av protokollet webb tjänster för hantering (WS-Management).</span><span class="sxs-lookup"><span data-stu-id="96e4f-174">The remoting features of PowerShell are supported by the WinRM service, which is the Microsoft implementation of the Web Services for Management (WS-Management) protocol.</span></span> <span data-ttu-id="96e4f-175">När du aktiverar PowerShell-fjärrkommunikation ändrar du standard konfigurationen för WS-Management och lägger till system konfiguration som tillåter användare att ansluta till WS-Management.</span><span class="sxs-lookup"><span data-stu-id="96e4f-175">When you enable PowerShell remoting, you change the default configuration of WS-Management and add system configuration that allow users to connect to WS-Management.</span></span>

<span data-ttu-id="96e4f-176">Så här konfigurerar du PowerShell för att ta emot fjärrkommandon:</span><span class="sxs-lookup"><span data-stu-id="96e4f-176">To configure PowerShell to receive remote commands:</span></span>

1. <span data-ttu-id="96e4f-177">Starta PowerShell med alternativet "kör som administratör".</span><span class="sxs-lookup"><span data-stu-id="96e4f-177">Start PowerShell with the "Run as administrator" option.</span></span>
2. <span data-ttu-id="96e4f-178">Skriv `Enable-PSRemoting` i kommandotolken</span><span class="sxs-lookup"><span data-stu-id="96e4f-178">At the command prompt, type: `Enable-PSRemoting`</span></span>

<span data-ttu-id="96e4f-179">Kontrol lera att fjärr kommunikation är korrekt konfigurerad genom att köra ett test kommando, till exempel följande kommando, som skapar en fjärrsession på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="96e4f-179">To verify that remoting is configured correctly, run a test command such as the following command, which creates a remote session on the local computer.</span></span>

```powershell
New-PSSession
```

<span data-ttu-id="96e4f-180">Om fjärr kommunikation har kon figurer ATS korrekt skapar kommandot en session på den lokala datorn och returnerar ett objekt som representerar sessionen.</span><span class="sxs-lookup"><span data-stu-id="96e4f-180">If remoting is configured correctly, the command will create a session on the local computer and return an object that represents the session.</span></span> <span data-ttu-id="96e4f-181">Utdata bör likna följande exempel på utdata:</span><span class="sxs-lookup"><span data-stu-id="96e4f-181">The output should resemble the following sample output:</span></span>

```output
Id Name        ComputerName    State    ConfigurationName
-- ----        ------------    -----    -----
1  Session1    localhost       Opened   Microsoft.PowerShell
```

<span data-ttu-id="96e4f-182">Om kommandot Miss lyckas finns mer information i [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="96e4f-182">If the command fails, for assistance, see [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md).</span></span>

## <a name="understand-policies"></a><span data-ttu-id="96e4f-183">FÖRSTÅ PRINCIPER</span><span class="sxs-lookup"><span data-stu-id="96e4f-183">UNDERSTAND POLICIES</span></span>

<span data-ttu-id="96e4f-184">När du arbetar på distans använder du två instanser av PowerShell, en på den lokala datorn och en på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="96e4f-184">When you work remotely, you use two instances of PowerShell, one on the local computer and one on the remote computer.</span></span> <span data-ttu-id="96e4f-185">Resultatet blir att ditt arbete påverkas av Windows-principerna och PowerShell-principerna på lokala datorer och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="96e4f-185">As a result, your work is affected by the Windows policies and the PowerShell policies on the local and remote computers.</span></span>

<span data-ttu-id="96e4f-186">I allmänhet gäller att innan du ansluter och när du upprättar anslutningen, gäller principerna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="96e4f-186">In general, before you connect and as you are establishing the connection, the policies on the local computer are in effect.</span></span> <span data-ttu-id="96e4f-187">När du använder anslutningen gäller principerna på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="96e4f-187">When you are using the connection, the policies on the remote computer are in effect.</span></span>

## <a name="basic-authentication-limitations-on-linux-and-macos"></a><span data-ttu-id="96e4f-188">Grundläggande begränsningar för autentisering på Linux och macOS</span><span class="sxs-lookup"><span data-stu-id="96e4f-188">Basic Authentication Limitations on Linux and macOS</span></span>

<span data-ttu-id="96e4f-189">Vid anslutning från ett Linux-eller macOS-system till Windows stöds inte grundläggande autentisering över HTTP.</span><span class="sxs-lookup"><span data-stu-id="96e4f-189">When connecting from a Linux or macOS system to Windows, Basic Authentication over HTTP is not supported.</span></span> <span data-ttu-id="96e4f-190">Grundläggande autentisering kan användas över HTTPS genom att installera ett certifikat på mål servern.</span><span class="sxs-lookup"><span data-stu-id="96e4f-190">Basic Authentication can be used over HTTPS by installing a certificate on the target server.</span></span> <span data-ttu-id="96e4f-191">Certifikatet måste ha ett CN-namn som matchar värd namnet, har inte gått ut eller återkallats.</span><span class="sxs-lookup"><span data-stu-id="96e4f-191">The certificate must have a CN name that matches the hostname, is not expired or revoked.</span></span> <span data-ttu-id="96e4f-192">Ett självsignerat certifikat kan användas i test syfte.</span><span class="sxs-lookup"><span data-stu-id="96e4f-192">A self-signed certificate may be used for testing purposes.</span></span>

<span data-ttu-id="96e4f-193">Mer information finns i [så här gör du: Konfigurera WINRM för https](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https) .</span><span class="sxs-lookup"><span data-stu-id="96e4f-193">See [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https) for additional details.</span></span>

<span data-ttu-id="96e4f-194">Följande kommando, som körs från en upphöjd kommando tolk, konfigurerar HTTPS-lyssnaren på Windows med det installerade certifikatet.</span><span class="sxs-lookup"><span data-stu-id="96e4f-194">The following command, run from an elevated command prompt, will configure the HTTPS listener on Windows with the installed certificate.</span></span>

```powershell
$hostinfo = '@{Hostname="<DNS_NAME>"; CertificateThumbprint="<THUMBPRINT>"}'
winrm create winrm/config/Listener?Address=*+Transport=HTTPS $hostinfo
```

<span data-ttu-id="96e4f-195">På Linux-eller macOS-sidan väljer du Basic för autentisering och-UseSSl.</span><span class="sxs-lookup"><span data-stu-id="96e4f-195">On the Linux or macOS side, select Basic for authentication and -UseSSl.</span></span>

> <span data-ttu-id="96e4f-196">Obs! grundläggande autentisering kan inte användas med domän konton. ett lokalt konto krävs och kontot måste vara i gruppen Administratörer.</span><span class="sxs-lookup"><span data-stu-id="96e4f-196">NOTE: Basic authentication cannot be used with domain accounts; a local account is required and the account must be in the Administrators group.</span></span>

```powershell
# The specified local user must have administrator rights on the target machine.
# Specify the unqualified username.
$cred = Get-Credential username
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Basic -UseSSL
```

<span data-ttu-id="96e4f-197">Ett alternativ till grundläggande autentisering över HTTPS är Negotiate.</span><span class="sxs-lookup"><span data-stu-id="96e4f-197">An alternative to Basic Authentication over HTTPS is Negotiate.</span></span> <span data-ttu-id="96e4f-198">Detta resulterar i att NTLM-autentisering mellan klienten och servern och nytto lasten krypteras över HTTP.</span><span class="sxs-lookup"><span data-stu-id="96e4f-198">This results in NTLM authentication between the client and server and payload is encrypted over HTTP.</span></span>

<span data-ttu-id="96e4f-199">Följande exempel visar hur du använder Negotiate med New-PSSession:</span><span class="sxs-lookup"><span data-stu-id="96e4f-199">The following illustrates using Negotiate with New-PSSession:</span></span>

```powershell
# The specified user must have administrator rights on the target machine.
$cred = Get-Credential username@hostname
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Negotiate
```

> [!NOTE]
> <span data-ttu-id="96e4f-200">Windows Server kräver ytterligare en register inställning för att göra det möjligt för administratörer, förutom den inbyggda administratören, att ansluta med hjälp av NTLM.</span><span class="sxs-lookup"><span data-stu-id="96e4f-200">Windows Server requires an additional registry setting to enable administrators, other than the built in administrator, to connect using NTLM.</span></span>
> <span data-ttu-id="96e4f-201">Läs register inställningen LocalAccountTokenFilterPolicy under förhandla autentisering i [autentisering för fjärr anslutningar](/windows/win32/winrm/authentication-for-remote-connections)</span><span class="sxs-lookup"><span data-stu-id="96e4f-201">Refer to the LocalAccountTokenFilterPolicy registry setting under Negotiate Authentication in [Authentication for Remote Connections](/windows/win32/winrm/authentication-for-remote-connections)</span></span>

## <a name="see-also"></a><span data-ttu-id="96e4f-202">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="96e4f-202">SEE ALSO</span></span>

[<span data-ttu-id="96e4f-203">about_Remote</span><span class="sxs-lookup"><span data-stu-id="96e4f-203">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="96e4f-204">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="96e4f-204">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="96e4f-205">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="96e4f-205">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="96e4f-206">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="96e4f-206">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="96e4f-207">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="96e4f-207">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="96e4f-208">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="96e4f-208">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

