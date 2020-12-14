---
description: Beskriver sessionsinställningar, som bestämmer vilka användare som kan fjärrans luta till datorn och de kommandon som de kan köra.
Locale: en-US
ms.date: 12/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configurations
ms.openlocfilehash: 4c6d5494f49bc271a7fe128fbce7b27c9d1f675f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710548"
---
# <a name="about-session-configurations"></a><span data-ttu-id="58c93-103">Om sessionsbaserade</span><span class="sxs-lookup"><span data-stu-id="58c93-103">About Session Configurations</span></span>

## <a name="short-description"></a><span data-ttu-id="58c93-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="58c93-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="58c93-105">Beskriver sessionsinställningar, som bestämmer vilka användare som kan fjärrans luta till datorn och de kommandon som de kan köra.</span><span class="sxs-lookup"><span data-stu-id="58c93-105">Describes session configurations, which determine the users who can connect to the computer remotely and the commands they can run.</span></span>

## <a name="long-description"></a><span data-ttu-id="58c93-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="58c93-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="58c93-107">En sessionsinformation, som även kallas "slut punkt", är en grupp inställningar på den lokala datorn som definierar miljön för PowerShell-sessioner som skapas när fjärranslutna eller lokala användare ansluter till PowerShell på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-107">A session configuration, also known as an "endpoint" is a group of settings on the local computer that define the environment for the PowerShell sessions that are created when remote or local users connect to PowerShell on the local computer.</span></span>

<span data-ttu-id="58c93-108">Administratörer på datorn kan använda sessionsbaserade för att skydda datorn och definiera anpassade miljöer för användare som ansluter till datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-108">Administrators of the computer can use session configurations to protect the computer and to define custom environments for users who connect to the computer.</span></span>

<span data-ttu-id="58c93-109">Administratörer kan också använda sessionsbaserade för att avgöra vilka behörigheter som krävs för att fjärrans luta till datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-109">Administrators can also use session configurations to determine the permissions that are required to connect to the computer remotely.</span></span> <span data-ttu-id="58c93-110">Som standard har bara medlemmar i gruppen Administratörer behörighet att använda sessionen för att fjärrans luta, men du kan ändra standardinställningarna så att alla användare eller valda användare kan fjärrans luta till din dator.</span><span class="sxs-lookup"><span data-stu-id="58c93-110">By default, only members of the Administrators group have permission to use the session configuration to connect remotely, but you can change the default settings to allow all users, or selected users, to connect remotely to your computer.</span></span>

<span data-ttu-id="58c93-111">Från och med PowerShell 3,0 kan du använda en konfigurations fil för sessionen för att definiera elementen i en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="58c93-111">Beginning in PowerShell 3.0, you can use a session configuration file to define the elements of a session configuration.</span></span> <span data-ttu-id="58c93-112">Den här funktionen gör det enkelt att anpassa sessioner utan att skriva kod och identifiera egenskaperna för en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="58c93-112">This feature makes it easy to customize sessions without writing code and to discover the properties of a session configuration.</span></span> <span data-ttu-id="58c93-113">Använd New-PSSessionConfiguration-cmdleten om du vill skapa en konfigurations fil för sessionen.</span><span class="sxs-lookup"><span data-stu-id="58c93-113">To create a session configuration file, use the New-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="58c93-114">Mer information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="58c93-114">For more information about session configuration files, see [about_Session_Configuration_Files](about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="58c93-115">Sessionsbaserade är en funktion i WS-Management-baserad (Web Services for Management), PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="58c93-115">Session configurations are a feature of Web Services for Management (WS-Management) based PowerShell remoting.</span></span> <span data-ttu-id="58c93-116">De används endast när du använder cmdletarna New-PSSession, Invoke-Command eller Enter-PSSession för att ansluta till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="58c93-116">They are used only when you use the New-PSSession, Invoke-Command, or Enter-PSSession cmdlets to connect to a remote computer.</span></span>

<span data-ttu-id="58c93-117">Obs: om du vill hantera sessionens konfigurationer startar du PowerShell med alternativet "kör som administratör".</span><span class="sxs-lookup"><span data-stu-id="58c93-117">Note: To manage the session configurations, start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="58c93-118">Om sessionsbaserade</span><span class="sxs-lookup"><span data-stu-id="58c93-118">About Session Configurations</span></span>

<span data-ttu-id="58c93-119">Varje PowerShell-session använder en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="58c93-119">Every PowerShell session uses a session configuration.</span></span> <span data-ttu-id="58c93-120">Detta omfattar permanenta sessioner som du skapar med hjälp av New-PSSession-eller Enter-PSSession-cmdletar och de tillfälliga sessioner som PowerShell skapar när du använder parametern ComputerName för en cmdlet som använder WS-Management-baserad fjärr kommunikations teknik, till exempel Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="58c93-120">This includes persistent sessions that you create by using the New-PSSession or Enter-PSSession cmdlets, and the temporary sessions that PowerShell creates when you use the ComputerName parameter of a cmdlet that uses WS-Management-based remoting technology, such as Invoke-Command.</span></span>

<span data-ttu-id="58c93-121">Administratörer kan använda sessionsbaserade för att skydda datorns resurser och skapa anpassade miljöer för användare som ansluter till datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-121">Administrators can use session configurations to protect the resources of the computer and to create custom environments for users who connect to the computer.</span></span> <span data-ttu-id="58c93-122">Du kan till exempel använda en sessionshantering för att begränsa storleken på objekt som datorn tar emot i sessionen, för att definiera språk läge för sessionen och för att ange vilka cmdlets, providers och funktioner som är tillgängliga i sessionen.</span><span class="sxs-lookup"><span data-stu-id="58c93-122">For example, you can use a session configuration to limit the size of objects that the computer receives in the session, to define the language mode of the session, and to specify the cmdlets, providers, and functions that are available in the session.</span></span>

<span data-ttu-id="58c93-123">Genom att konfigurera säkerhets beskrivningen för en konfiguration av sessionen bestämmer du vem som kan använda sessionen för att ansluta till datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-123">By configuring the security descriptor of a session configuration, you determine who can use the session configuration to connect to the computer.</span></span>
<span data-ttu-id="58c93-124">Användarna måste ha behörigheten Kör för att kunna använda den i en session.</span><span class="sxs-lookup"><span data-stu-id="58c93-124">Users must have Execute permission to a session configuration to use it in a session.</span></span> <span data-ttu-id="58c93-125">Om en användare inte har de behörigheter som krävs för att använda någon av sessionens konfigurationer på en dator, kan användaren inte fjärrans luta till datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-125">If a user does not have the required permissions to use any of the session configurations on a computer, the user cannot connect to the computer remotely.</span></span>

<span data-ttu-id="58c93-126">Som standard har bara administratörer på datorn behörighet att använda standardkonfigurationerna för sessioner.</span><span class="sxs-lookup"><span data-stu-id="58c93-126">By default, only Administrators of the computer have permission to use the default session configurations.</span></span> <span data-ttu-id="58c93-127">Men du kan ändra säkerhets beskrivarna så att alla, ingen eller bara valda användare kan använda dem på din dator.</span><span class="sxs-lookup"><span data-stu-id="58c93-127">But, you can change the security descriptors to allow everyone, no one, or only selected users to use the session configurations on your computer.</span></span>

<span data-ttu-id="58c93-128">Inbyggda sessionsbaserade konfigurationer</span><span class="sxs-lookup"><span data-stu-id="58c93-128">Built-in Session Configurations</span></span>

<span data-ttu-id="58c93-129">PowerShell 3,0 innehåller inbyggda sessionsinställningar som heter Microsoft. PowerShell och Microsoft. PowerShell. Workflow.</span><span class="sxs-lookup"><span data-stu-id="58c93-129">PowerShell 3.0 includes built-in session configurations named Microsoft.PowerShell and Microsoft.PowerShell.Workflow.</span></span> <span data-ttu-id="58c93-130">På datorer som kör 64-bitars versioner av Windows tillhandahåller PowerShell även Microsoft. PowerShell32, en 32-bitars konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="58c93-130">On computers running 64-bit versions of Windows, PowerShell also provides Microsoft.PowerShell32, a 32-bit session configuration.</span></span>

<span data-ttu-id="58c93-131">Konfigurationen av Microsoft. PowerShell-sessionen används för sessioner som standard, det vill säga när ett kommando för att skapa en session inte innehåller parametern ConfigurationName för cmdleten New-PSSession, retur-PSSession eller Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="58c93-131">The Microsoft.PowerShell session configuration is used for sessions by default, that is, when a command to create a session does not include the ConfigurationName parameter of the New-PSSession, Enter-PSSession, or Invoke-Command cmdlet.</span></span>

<span data-ttu-id="58c93-132">Säkerhets beskrivningarna för standardsessions-konfigurationerna tillåter bara medlemmar i gruppen Administratörer på den lokala datorn att använda dem.</span><span class="sxs-lookup"><span data-stu-id="58c93-132">The security descriptors for the default session configurations allow only members of the Administrators group on the local computer to use them.</span></span> <span data-ttu-id="58c93-133">Därför kan endast medlemmar i gruppen Administratörer fjärrans luta till datorn om du inte ändrar standardinställningarna.</span><span class="sxs-lookup"><span data-stu-id="58c93-133">As such, only members of the Administrators group can connect to the computer remotely unless you change the default settings.</span></span>

<span data-ttu-id="58c93-134">Du kan ändra standardkonfigurationerna för sessioner med hjälp av $PSSessionConfigurationName Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="58c93-134">You can change the default session configurations by using the $PSSessionConfigurationName preference variable.</span></span> <span data-ttu-id="58c93-135">Mer information finns i about_Preference_Variables.</span><span class="sxs-lookup"><span data-stu-id="58c93-135">For more information, see about_Preference_Variables.</span></span>

<span data-ttu-id="58c93-136">Visa sessionsinställningar på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="58c93-136">Viewing Session Configurations on the Local Computer</span></span>

<span data-ttu-id="58c93-137">Använd Get-PSSessionConfiguration-cmdleten för att hämta sessionsinställningar på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-137">To get the session configurations on your local computer, use the Get-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="58c93-138">Skriv till exempel:</span><span class="sxs-lookup"><span data-stu-id="58c93-138">For example, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property Name, Permission

Name       : microsoft.powershell
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell.workflow
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell32
Permission : BUILTIN\Administrators AccessAllowed
```

<span data-ttu-id="58c93-139">Konfigurationsobjektet för sessionen expanderas i PowerShell 3,0 för att visa egenskaperna för den konfiguration av sessionen som konfigureras med hjälp av en konfigurations fil för sessionen.</span><span class="sxs-lookup"><span data-stu-id="58c93-139">The session configuration object is expanded in PowerShell 3.0 to display the properties of the session configuration that are configured by using a session configuration file.</span></span>

<span data-ttu-id="58c93-140">Om du till exempel vill visa alla egenskaper för ett konfigurations objekt för session skriver du:</span><span class="sxs-lookup"><span data-stu-id="58c93-140">For example, to see all of the properties of a session configuration object, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property *
```

<span data-ttu-id="58c93-141">Du kan också använda WSMan-providern i PowerShell för att Visa sessionsinställningar.</span><span class="sxs-lookup"><span data-stu-id="58c93-141">You can also use the WSMan provider in PowerShell to view session configurations.</span></span> <span data-ttu-id="58c93-142">WSMan-providern skapar en WSMAN:-enhet i sessionen.</span><span class="sxs-lookup"><span data-stu-id="58c93-142">The WSMan provider creates a WSMAN: drive in your session.</span></span>

<span data-ttu-id="58c93-143">I WSMAN:-enheten finns sessionens konfigurationer i noden plugin-program.</span><span class="sxs-lookup"><span data-stu-id="58c93-143">In the WSMAN: drive, session configurations are in the Plugin node.</span></span> <span data-ttu-id="58c93-144">(Alla användarsessioner finns i plugin-noden, men det finns objekt i noden plugin-program som inte är sessionsbaserade.)</span><span class="sxs-lookup"><span data-stu-id="58c93-144">(All session configurations are in the Plugin node, but there are items in the Plugin node that are not session configurations.)</span></span>

<span data-ttu-id="58c93-145">Om du till exempel vill visa sessionens konfigurationer på den lokala datorn skriver du:</span><span class="sxs-lookup"><span data-stu-id="58c93-145">For example, to view the session configurations on the local computer, type:</span></span>

```powershell
PS C:> dir wsman:\localhost\plugin\microsoft*

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

<span data-ttu-id="58c93-146">Visa sessionsinställningar på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="58c93-146">Viewing Session Configurations on a Remote Computer</span></span>

<span data-ttu-id="58c93-147">Om du vill visa sessionsinställningar på en fjärrdator använder du cmdleten Connect-WSMan för att lägga till en anteckning för fjärrdatorn på WSMAN:-enheten på den lokala datorn och använder sedan WSMAN:-enheten för att Visa sessionens konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="58c93-147">To view the session configurations on a remote computer, use the Connect-WSMan cmdlet to add a note for the remote computer to the WSMAN: drive on your local computer, and then use the WSMAN: drive to view the session configurations.</span></span>

<span data-ttu-id="58c93-148">Följande kommando lägger till exempel till en nod för fjärrdatorn Server01 till WSMAN: Drive på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-148">For example, the following command adds a node for the Server01 remote computer to the WSMAN: drive on the local computer.</span></span>

```powershell
PS C:> Connect-WSMan server01.corp.fabrikam.com
```

<span data-ttu-id="58c93-149">När kommandot har slutförts kan du navigera till noden för Server01-datorn för att Visa sessionens konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="58c93-149">When the command is complete, you can navigate to the node for the Server01 computer to view the session configurations.</span></span>

<span data-ttu-id="58c93-150">Exempel:</span><span class="sxs-lookup"><span data-stu-id="58c93-150">For example:</span></span>

```powershell
PS C:> cd wsman:

PS WSMan:> dir

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01.corp.fabrikam.com                    Container

PS WSMan:> dir server01\plugin\

WSManConfig: Microsoft.WSMan.Management\WSMan::server01.corp.fabrikam.com\Pl
ugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

<span data-ttu-id="58c93-151">Ändra säkerhets beskrivningen för en sessions konfiguration</span><span class="sxs-lookup"><span data-stu-id="58c93-151">Changing the Security Descriptor of a Session Configuration</span></span>

<span data-ttu-id="58c93-152">I Windows Server 2012 och senare versioner av Windows Server, aktive ras de inbyggda sessionerna för fjärran vändare som standard.</span><span class="sxs-lookup"><span data-stu-id="58c93-152">In Windows Server 2012 and newer releases of Windows Server, the built-in session configurations are enabled for remote users by default.</span></span> <span data-ttu-id="58c93-153">I andra versioner av Windows som stöds måste du ändra säkerhets beskrivarna för sessionens konfigurationer för att tillåta fjärråtkomst.</span><span class="sxs-lookup"><span data-stu-id="58c93-153">In other supported versions of Windows, you must change the security descriptors of the session configurations to allow remote access.</span></span>

<span data-ttu-id="58c93-154">Använd Enable-PSRemoting-cmdleten om du vill aktivera fjärråtkomst till sessionsbaserade på datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-154">To enable remote access to the session configurations on the computer, use the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="58c93-155">Den här cmdleten skapar två sessionsbaserade konfigurationer:</span><span class="sxs-lookup"><span data-stu-id="58c93-155">This cmdlet creates two session configurations:</span></span>

- <span data-ttu-id="58c93-156">med namnet definierat som: "PowerShell."</span><span class="sxs-lookup"><span data-stu-id="58c93-156">with the name defined as: "PowerShell."</span></span> <span data-ttu-id="58c93-157">+ "aktuell PowerShell-version"</span><span class="sxs-lookup"><span data-stu-id="58c93-157">+ "current PowerShell version"</span></span>
- <span data-ttu-id="58c93-158">med namnet "PowerShell. 6", som inte är knutet till någon speciell PowerShell-version.</span><span class="sxs-lookup"><span data-stu-id="58c93-158">with name "PowerShell.6", untied to any specific PowerShell version.</span></span>

<span data-ttu-id="58c93-159">Som standard har bara medlemmar i gruppen Administratörer på datorn behörigheten Kör för standardsession-konfigurationerna, men du kan ändra säkerhets beskrivarna på standardkonfigurationerna för sessioner och eventuella sessionsinställningar som du skapar.</span><span class="sxs-lookup"><span data-stu-id="58c93-159">Also, by default, only members of the Administrators group on the computer have Execute permission to the default session configurations, but you can change the security descriptors on the default session configurations and on any session configurations that you create.</span></span>

<span data-ttu-id="58c93-160">Om du vill ge andra användare behörighet att fjärrans luta till datorn använder du Set-PSSessionConfiguration-cmdleten för att lägga till "kör"-behörigheter för dessa användare till säkerhets beskrivarna i Microsoft. PowerShell-och Microsoft. PowerShell32-sessionens konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="58c93-160">To give other users permission to connect to the computer remotely, use the Set-PSSessionConfiguration cmdlet to add "Execute" permissions for those users to the security descriptors of the Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span>

<span data-ttu-id="58c93-161">Följande kommando öppnar exempelvis en egenskaps sida där du kan ändra säkerhets beskrivningen för standardsessions-konfigurationen i Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58c93-161">For example, the following command opens a property page that lets you change the security descriptor for the Microsoft.PowerShell default session configuration.</span></span>

```powershell
Set-PSSessionConfiguration -name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="58c93-162">Använd Disable-PSSessionConfiguration-cmdleten om du vill neka alla behörighet till alla sessioner på datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-162">To deny everyone permission to all the session configurations on the computer, use the Disable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="58c93-163">Följande kommando inaktiverar till exempel standardkonfigurationerna för sessioner på datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-163">For example, the following command disables the default session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSSessionConfiguration -Name Microsoft.PowerShell
```

<span data-ttu-id="58c93-164">För att förhindra att fjärran vändare ansluter till datorn, men Tillåt att lokala användare ansluter, använder du Disable-PSRemoting-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="58c93-164">To prevent remote users from connecting to the computer, but allow local users to connect, use the Disable-PSRemoting cmdlet.</span></span> <span data-ttu-id="58c93-165">Disable-PSRemoting lägger till en "Network_Deny_All"-post till alla sessionsinställningar på datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-165">Disable-PSRemoting adds a "Network_Deny_All" entry to all session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSRemoting
```

<span data-ttu-id="58c93-166">Om du vill tillåta fjärran vändare att använda alla sessionsinställningar på datorn använder du Enable-PSRemoting-eller Enable-PSSessionConfiguration-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="58c93-166">To allow remote users to use all session configurations on the computer, use the Enable-PSRemoting or Enable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="58c93-167">Följande kommando ger till exempel fjärråtkomst till de inbyggda session-konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="58c93-167">For example, the following command enables remote access to the built-in session configurations.</span></span>

```powershell
PS C:> Enable-PSSessionConfiguration -name Microsoft.Power*
```

<span data-ttu-id="58c93-168">Använd Set-PSSessionConfiguration-cmdleten om du vill göra andra ändringar i säkerhets beskrivningen för en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="58c93-168">To make other changes to the security descriptor of a session configuration, use the Set-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="58c93-169">Använd parametern SecurityDescriptorSDDL för att skicka ett SDDL-sträng värde.</span><span class="sxs-lookup"><span data-stu-id="58c93-169">Use the SecurityDescriptorSDDL parameter to submit an SDDL string value.</span></span> <span data-ttu-id="58c93-170">Använd parametern ShowSecurityDescriptorUI för att visa en egenskaps sida för användar gränssnitt som hjälper dig att skapa en ny SDDL.</span><span class="sxs-lookup"><span data-stu-id="58c93-170">Use the ShowSecurityDescriptorUI parameter to display a user interface property sheet that helps you to create a new SDDL.</span></span>

<span data-ttu-id="58c93-171">Exempel:</span><span class="sxs-lookup"><span data-stu-id="58c93-171">For example:</span></span>

```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="58c93-172">Skapa en ny konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="58c93-172">Creating a New Session Configuration</span></span>

<span data-ttu-id="58c93-173">Använd Register-PSSessionConfiguration-cmdleten om du vill skapa en ny sessionsinformation på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-173">To create a new session configuration on the local computer, use the Register-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="58c93-174">Om du vill definiera den nya konfigurationen av sessionen kan du använda en C#-sammansättning, ett PowerShell-skript och parametrarna för Register-PSSessionConfiguration-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="58c93-174">To define the new session configuration, you can use a C# assembly, a PowerShell script, and the parameters of the Register-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="58c93-175">Följande kommando skapar till exempel en sessionsnyckel som är identisk med konfigurationen av Microsoft. PowerShell-sessionen, förutom att den begränsar de data som tas emot från ett fjärrkommando till 20 megabyte (MB).</span><span class="sxs-lookup"><span data-stu-id="58c93-175">For example, the following command creates a session configuration that is identical the Microsoft.PowerShell session configuration, except that it limits the data received from a remote command to 20 megabytes (MB).</span></span> <span data-ttu-id="58c93-176">(Standardvärdet är 50 MB).</span><span class="sxs-lookup"><span data-stu-id="58c93-176">(The default is 50 MB).</span></span>

```powershell
Register-PSSessionConfiguration -Name NewConfig `
  -MaximumReceivedDataSizePerCommandMB 20
```

<span data-ttu-id="58c93-177">När du skapar en sessionsnyckel kan du hantera den med hjälp av de andra cmdletarna för sessions konfiguration och visas i filen WSMAN: Drive.</span><span class="sxs-lookup"><span data-stu-id="58c93-177">When you create a session configuration, you can manage it by using the other session configuration cmdlets, and it appears in the WSMAN: drive.</span></span>

<span data-ttu-id="58c93-178">Mer information finns i register-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="58c93-178">For more information, see Register-PSSessionConfiguration.</span></span>

<span data-ttu-id="58c93-179">Tar bort en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="58c93-179">Removing a Session Configuration</span></span>

<span data-ttu-id="58c93-180">Använd Unregister-PSSessionConfiguration-cmdleten om du vill ta bort en sessionsinformation från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-180">To remove a session configuration from the local computer, use the Unregister-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="58c93-181">Följande kommando tar till exempel bort konfigurationen av NewConfig-sessionen från datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-181">For example, the following command removes the NewConfig session configuration from the computer.</span></span>

```powershell
PS C:> Unregister-PSSessionConfiguration -Name NewConfig
```

<span data-ttu-id="58c93-182">Mer information finns i unregister-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="58c93-182">For more information, see Unregister-PSSessionConfiguration.</span></span>

<span data-ttu-id="58c93-183">Återställa en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="58c93-183">Restoring a Session Configuration</span></span>

<span data-ttu-id="58c93-184">Använd Enable-PSRemoting-cmdleten om du vill återställa en standardsessions-konfiguration som har tagits bort (avregistreras) av misstag.</span><span class="sxs-lookup"><span data-stu-id="58c93-184">To restore a default session configuration that was deleted (unregistered) accidentally, use the Enable-PSRemoting cmdlet.</span></span>

<span data-ttu-id="58c93-185">Enable-PSRemoting-cmdleten återskapar alla standardkonfigurationer för sessioner som inte finns på datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-185">The Enable-PSRemoting cmdlet recreates all default sessions configurations that do not exist on the computer.</span></span> <span data-ttu-id="58c93-186">Den skriver inte över eller ändrar egenskapsvärdena för befintliga sessioner.</span><span class="sxs-lookup"><span data-stu-id="58c93-186">It does not overwrite or change the property values of existing session configurations.</span></span>

<span data-ttu-id="58c93-187">Om du vill återställa de ursprungliga egenskapsvärdena för en standardsessions-konfiguration använder du Unregister-PSSessionConfiguration för att ta bort konfigurationen och använder sedan Enable-PSRemoting-cmdlet för att återskapa den.</span><span class="sxs-lookup"><span data-stu-id="58c93-187">To restore the original property values of a default session configuration, use the Unregister-PSSessionConfiguration to delete the session configuration and then use the Enable-PSRemoting cmdlet to recreate it.</span></span>

<span data-ttu-id="58c93-188">Välja en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="58c93-188">Selecting a Session Configuration</span></span>

<span data-ttu-id="58c93-189">Om du vill välja en viss sessionsinformation för en session använder du parametern ConfigurationName för New-PSSession, retur-PSSession eller Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="58c93-189">To select a particular session configuration for a session, use the ConfigurationName parameter of New-PSSession, Enter-PSSession, or Invoke-Command.</span></span>

<span data-ttu-id="58c93-190">Detta kommando använder till exempel cmdleten New-PSSession för att starta en PSSession på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-190">For example, this command uses the New-PSSession cmdlet to start a PSSession on the Server01 computer.</span></span> <span data-ttu-id="58c93-191">Kommandot använder parametern ConfigurationName för att välja WithProfile-konfigurationen på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-191">The command uses the ConfigurationName parameter to select the WithProfile configuration on the Server01 computer.</span></span>

```powershell
PS C:> New-PSSession -ComputerName Server01 -ConfigurationName WithProfile
```

<span data-ttu-id="58c93-192">Kommandot fungerar bara om den aktuella användaren har behörighet att använda WithProfile-sessionen eller kan ange autentiseringsuppgifterna för en användare som har de behörigheter som krävs.</span><span class="sxs-lookup"><span data-stu-id="58c93-192">This command will succeed only if the current user has permission to use the WithProfile session configuration or can supply the credentials of a user who has the required permissions.</span></span>

<span data-ttu-id="58c93-193">Du kan också använda variabeln $PSSessionConfigurationName för att ändra standard konfigurationen för sessionen på datorn.</span><span class="sxs-lookup"><span data-stu-id="58c93-193">You can also use the $PSSessionConfigurationName preference variable to change the default session configuration on the computer.</span></span> <span data-ttu-id="58c93-194">Mer information om variabeln $PSSessionConfigurationName finns about_Preference_Variables.</span><span class="sxs-lookup"><span data-stu-id="58c93-194">For more information about the $PSSessionConfigurationName preference variable, see about_Preference_Variables.</span></span>

## <a name="keywords"></a><span data-ttu-id="58c93-195">RESERVERADE</span><span class="sxs-lookup"><span data-stu-id="58c93-195">KEYWORDS</span></span>

<span data-ttu-id="58c93-196">about_Endpoints about_SessionConfigurations</span><span class="sxs-lookup"><span data-stu-id="58c93-196">about_Endpoints about_SessionConfigurations</span></span>

## <a name="see-also"></a><span data-ttu-id="58c93-197">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="58c93-197">SEE ALSO</span></span>

[<span data-ttu-id="58c93-198">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="58c93-198">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="58c93-199">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="58c93-199">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="58c93-200">about_Remote</span><span class="sxs-lookup"><span data-stu-id="58c93-200">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="58c93-201">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="58c93-201">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)

[<span data-ttu-id="58c93-202">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="58c93-202">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="58c93-203">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="58c93-203">Disable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[<span data-ttu-id="58c93-204">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="58c93-204">Enable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[<span data-ttu-id="58c93-205">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="58c93-205">Get-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[<span data-ttu-id="58c93-206">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="58c93-206">New-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[<span data-ttu-id="58c93-207">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="58c93-207">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[<span data-ttu-id="58c93-208">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="58c93-208">Set-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[<span data-ttu-id="58c93-209">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="58c93-209">Test-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[<span data-ttu-id="58c93-210">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="58c93-210">Unregister-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

