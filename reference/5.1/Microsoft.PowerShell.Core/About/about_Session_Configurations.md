---
description: Beskriver sessionsinställningar, som bestämmer vilka användare som kan fjärrans luta till datorn och de kommandon som de kan köra.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configurations
ms.openlocfilehash: 5dd13107396aa7d908fe8224e3de35571b73fae7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271964"
---
# <a name="about-session-configurations"></a><span data-ttu-id="a910e-104">Om sessionsbaserade</span><span class="sxs-lookup"><span data-stu-id="a910e-104">About Session Configurations</span></span>

## <a name="short-description"></a><span data-ttu-id="a910e-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a910e-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a910e-106">Beskriver sessionsinställningar, som bestämmer vilka användare som kan fjärrans luta till datorn och de kommandon som de kan köra.</span><span class="sxs-lookup"><span data-stu-id="a910e-106">Describes session configurations, which determine the users who can connect to the computer remotely and the commands they can run.</span></span>

## <a name="long-description"></a><span data-ttu-id="a910e-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a910e-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="a910e-108">En sessionsinformation, som även kallas "slut punkt", är en grupp inställningar på den lokala datorn som definierar miljön för PowerShell-sessioner som skapas när fjärranslutna eller lokala användare ansluter till PowerShell på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-108">A session configuration, also known as an "endpoint" is a group of settings on the local computer that define the environment for the PowerShell sessions that are created when remote or local users connect to PowerShell on the local computer.</span></span>

<span data-ttu-id="a910e-109">Administratörer på datorn kan använda sessionsbaserade för att skydda datorn och definiera anpassade miljöer för användare som ansluter till datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-109">Administrators of the computer can use session configurations to protect the computer and to define custom environments for users who connect to the computer.</span></span>

<span data-ttu-id="a910e-110">Administratörer kan också använda sessionsbaserade för att avgöra vilka behörigheter som krävs för att fjärrans luta till datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-110">Administrators can also use session configurations to determine the permissions that are required to connect to the computer remotely.</span></span> <span data-ttu-id="a910e-111">Som standard har bara medlemmar i gruppen Administratörer behörighet att använda sessionen för att fjärrans luta, men du kan ändra standardinställningarna så att alla användare eller valda användare kan fjärrans luta till din dator.</span><span class="sxs-lookup"><span data-stu-id="a910e-111">By default, only members of the Administrators group have permission to use the session configuration to connect remotely, but you can change the default settings to allow all users, or selected users, to connect remotely to your computer.</span></span>

<span data-ttu-id="a910e-112">Från och med PowerShell 3,0 kan du använda en konfigurations fil för sessionen för att definiera elementen i en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a910e-112">Beginning in PowerShell 3.0, you can use a session configuration file to define the elements of a session configuration.</span></span> <span data-ttu-id="a910e-113">Den här funktionen gör det enkelt att anpassa sessioner utan att skriva kod och identifiera egenskaperna för en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a910e-113">This feature makes it easy to customize sessions without writing code and to discover the properties of a session configuration.</span></span> <span data-ttu-id="a910e-114">Använd New-PSSessionConfiguration-cmdleten om du vill skapa en konfigurations fil för sessionen.</span><span class="sxs-lookup"><span data-stu-id="a910e-114">To create a session configuration file, use the New-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="a910e-115">Mer information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="a910e-115">For more information about session configuration files, see [about_Session_Configuration_Files](about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="a910e-116">Sessionsbaserade är en funktion i WS-Management-baserad (Web Services for Management), PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="a910e-116">Session configurations are a feature of Web Services for Management (WS-Management) based PowerShell remoting.</span></span> <span data-ttu-id="a910e-117">De används endast när du använder cmdletarna New-PSSession, Invoke-Command eller Enter-PSSession för att ansluta till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="a910e-117">They are used only when you use the New-PSSession, Invoke-Command, or Enter-PSSession cmdlets to connect to a remote computer.</span></span>

<span data-ttu-id="a910e-118">Obs: om du vill hantera sessionens konfigurationer startar du PowerShell med alternativet "kör som administratör".</span><span class="sxs-lookup"><span data-stu-id="a910e-118">Note: To manage the session configurations, start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="a910e-119">Om sessionsbaserade</span><span class="sxs-lookup"><span data-stu-id="a910e-119">About Session Configurations</span></span>

<span data-ttu-id="a910e-120">Varje PowerShell-session använder en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a910e-120">Every PowerShell session uses a session configuration.</span></span> <span data-ttu-id="a910e-121">Detta omfattar permanenta sessioner som du skapar med hjälp av New-PSSession-eller Enter-PSSession-cmdletar och de tillfälliga sessioner som PowerShell skapar när du använder parametern ComputerName för en cmdlet som använder WS-Management-baserad fjärr kommunikations teknik, till exempel Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="a910e-121">This includes persistent sessions that you create by using the New-PSSession or Enter-PSSession cmdlets, and the temporary sessions that PowerShell creates when you use the ComputerName parameter of a cmdlet that uses WS-Management-based remoting technology, such as Invoke-Command.</span></span>

<span data-ttu-id="a910e-122">Administratörer kan använda sessionsbaserade för att skydda datorns resurser och skapa anpassade miljöer för användare som ansluter till datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-122">Administrators can use session configurations to protect the resources of the computer and to create custom environments for users who connect to the computer.</span></span> <span data-ttu-id="a910e-123">Du kan till exempel använda en sessionshantering för att begränsa storleken på objekt som datorn tar emot i sessionen, för att definiera språk läge för sessionen och för att ange vilka cmdlets, providers och funktioner som är tillgängliga i sessionen.</span><span class="sxs-lookup"><span data-stu-id="a910e-123">For example, you can use a session configuration to limit the size of objects that the computer receives in the session, to define the language mode of the session, and to specify the cmdlets, providers, and functions that are available in the session.</span></span>

<span data-ttu-id="a910e-124">Genom att konfigurera säkerhets beskrivningen för en konfiguration av sessionen bestämmer du vem som kan använda sessionen för att ansluta till datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-124">By configuring the security descriptor of a session configuration, you determine who can use the session configuration to connect to the computer.</span></span>
<span data-ttu-id="a910e-125">Användarna måste ha behörigheten Kör för att kunna använda den i en session.</span><span class="sxs-lookup"><span data-stu-id="a910e-125">Users must have Execute permission to a session configuration to use it in a session.</span></span> <span data-ttu-id="a910e-126">Om en användare inte har de behörigheter som krävs för att använda någon av sessionens konfigurationer på en dator, kan användaren inte fjärrans luta till datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-126">If a user does not have the required permissions to use any of the session configurations on a computer, the user cannot connect to the computer remotely.</span></span>

<span data-ttu-id="a910e-127">Som standard har bara administratörer på datorn behörighet att använda standardkonfigurationerna för sessioner.</span><span class="sxs-lookup"><span data-stu-id="a910e-127">By default, only Administrators of the computer have permission to use the default session configurations.</span></span> <span data-ttu-id="a910e-128">Men du kan ändra säkerhets beskrivarna så att alla, ingen eller bara valda användare kan använda dem på din dator.</span><span class="sxs-lookup"><span data-stu-id="a910e-128">But, you can change the security descriptors to allow everyone, no one, or only selected users to use the session configurations on your computer.</span></span>

<span data-ttu-id="a910e-129">Inbyggda sessionsbaserade konfigurationer</span><span class="sxs-lookup"><span data-stu-id="a910e-129">Built-in Session Configurations</span></span>

<span data-ttu-id="a910e-130">PowerShell 3,0 innehåller inbyggda sessionsinställningar som heter Microsoft. PowerShell och Microsoft. PowerShell. Workflow.</span><span class="sxs-lookup"><span data-stu-id="a910e-130">PowerShell 3.0 includes built-in session configurations named Microsoft.PowerShell and Microsoft.PowerShell.Workflow.</span></span> <span data-ttu-id="a910e-131">På datorer som kör 64-bitars versioner av Windows tillhandahåller PowerShell även Microsoft. PowerShell32, en 32-bitars konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a910e-131">On computers running 64-bit versions of Windows, PowerShell also provides Microsoft.PowerShell32, a 32-bit session configuration.</span></span>

<span data-ttu-id="a910e-132">Konfigurationen av Microsoft. PowerShell-sessionen används för sessioner som standard, det vill säga när ett kommando för att skapa en session inte innehåller parametern ConfigurationName för cmdleten New-PSSession, retur-PSSession eller Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="a910e-132">The Microsoft.PowerShell session configuration is used for sessions by default, that is, when a command to create a session does not include the ConfigurationName parameter of the New-PSSession, Enter-PSSession, or Invoke-Command cmdlet.</span></span>

<span data-ttu-id="a910e-133">Säkerhets beskrivningarna för standardsessions-konfigurationerna tillåter bara medlemmar i gruppen Administratörer på den lokala datorn att använda dem.</span><span class="sxs-lookup"><span data-stu-id="a910e-133">The security descriptors for the default session configurations allow only members of the Administrators group on the local computer to use them.</span></span> <span data-ttu-id="a910e-134">Därför kan endast medlemmar i gruppen Administratörer fjärrans luta till datorn om du inte ändrar standardinställningarna.</span><span class="sxs-lookup"><span data-stu-id="a910e-134">As such, only members of the Administrators group can connect to the computer remotely unless you change the default settings.</span></span>

<span data-ttu-id="a910e-135">Du kan ändra standardkonfigurationerna för sessioner med hjälp av $PSSessionConfigurationName Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="a910e-135">You can change the default session configurations by using the $PSSessionConfigurationName preference variable.</span></span> <span data-ttu-id="a910e-136">Mer information finns i about_Preference_Variables.</span><span class="sxs-lookup"><span data-stu-id="a910e-136">For more information, see about_Preference_Variables.</span></span>

<span data-ttu-id="a910e-137">Visa sessionsinställningar på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="a910e-137">Viewing Session Configurations on the Local Computer</span></span>

<span data-ttu-id="a910e-138">Använd Get-PSSessionConfiguration-cmdleten för att hämta sessionsinställningar på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-138">To get the session configurations on your local computer, use the Get-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="a910e-139">Skriv till exempel:</span><span class="sxs-lookup"><span data-stu-id="a910e-139">For example, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property Name, Permission

Name       : microsoft.powershell
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell.workflow
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell32
Permission : BUILTIN\Administrators AccessAllowed
```

<span data-ttu-id="a910e-140">Konfigurationsobjektet för sessionen expanderas i PowerShell 3,0 för att visa egenskaperna för den konfiguration av sessionen som konfigureras med hjälp av en konfigurations fil för sessionen.</span><span class="sxs-lookup"><span data-stu-id="a910e-140">The session configuration object is expanded in PowerShell 3.0 to display the properties of the session configuration that are configured by using a session configuration file.</span></span>

<span data-ttu-id="a910e-141">Om du till exempel vill visa alla egenskaper för ett konfigurations objekt för session skriver du:</span><span class="sxs-lookup"><span data-stu-id="a910e-141">For example, to see all of the properties of a session configuration object, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property *
```

<span data-ttu-id="a910e-142">Du kan också använda WSMan-providern i PowerShell för att Visa sessionsinställningar.</span><span class="sxs-lookup"><span data-stu-id="a910e-142">You can also use the WSMan provider in PowerShell to view session configurations.</span></span> <span data-ttu-id="a910e-143">WSMan-providern skapar en WSMAN:-enhet i sessionen.</span><span class="sxs-lookup"><span data-stu-id="a910e-143">The WSMan provider creates a WSMAN: drive in your session.</span></span>

<span data-ttu-id="a910e-144">I WSMAN:-enheten finns sessionens konfigurationer i noden plugin-program.</span><span class="sxs-lookup"><span data-stu-id="a910e-144">In the WSMAN: drive, session configurations are in the Plugin node.</span></span> <span data-ttu-id="a910e-145">(Alla användarsessioner finns i plugin-noden, men det finns objekt i noden plugin-program som inte är sessionsbaserade.)</span><span class="sxs-lookup"><span data-stu-id="a910e-145">(All session configurations are in the Plugin node, but there are items in the Plugin node that are not session configurations.)</span></span>

<span data-ttu-id="a910e-146">Om du till exempel vill visa sessionens konfigurationer på den lokala datorn skriver du:</span><span class="sxs-lookup"><span data-stu-id="a910e-146">For example, to view the session configurations on the local computer, type:</span></span>

```powershell
PS C:> dir wsman:\localhost\plugin\microsoft*

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

<span data-ttu-id="a910e-147">Visa sessionsinställningar på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="a910e-147">Viewing Session Configurations on a Remote Computer</span></span>

<span data-ttu-id="a910e-148">Om du vill visa sessionsinställningar på en fjärrdator använder du cmdleten Connect-WSMan för att lägga till en anteckning för fjärrdatorn på WSMAN:-enheten på den lokala datorn och använder sedan WSMAN:-enheten för att Visa sessionens konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="a910e-148">To view the session configurations on a remote computer, use the Connect-WSMan cmdlet to add a note for the remote computer to the WSMAN: drive on your local computer, and then use the WSMAN: drive to view the session configurations.</span></span>

<span data-ttu-id="a910e-149">Följande kommando lägger till exempel till en nod för fjärrdatorn Server01 till WSMAN: Drive på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-149">For example, the following command adds a node for the Server01 remote computer to the WSMAN: drive on the local computer.</span></span>

```powershell
PS C:> Connect-WSMan server01.corp.fabrikam.com
```

<span data-ttu-id="a910e-150">När kommandot har slutförts kan du navigera till noden för Server01-datorn för att Visa sessionens konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="a910e-150">When the command is complete, you can navigate to the node for the Server01 computer to view the session configurations.</span></span>

<span data-ttu-id="a910e-151">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="a910e-151">For example:</span></span>

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

<span data-ttu-id="a910e-152">Ändra säkerhets beskrivningen för en sessions konfiguration</span><span class="sxs-lookup"><span data-stu-id="a910e-152">Changing the Security Descriptor of a Session Configuration</span></span>

<span data-ttu-id="a910e-153">I Windows Server 2012 och senare versioner av Windows Server, aktive ras de inbyggda sessionerna för fjärran vändare som standard.</span><span class="sxs-lookup"><span data-stu-id="a910e-153">In Windows Server 2012 and newer releases of Windows Server, the built-in session configurations are enabled for remote users by default.</span></span> <span data-ttu-id="a910e-154">I andra versioner av Windows som stöds måste du ändra säkerhets beskrivarna för sessionens konfigurationer för att tillåta fjärråtkomst.</span><span class="sxs-lookup"><span data-stu-id="a910e-154">In other supported versions of Windows, you must change the security descriptors of the session configurations to allow remote access.</span></span>

<span data-ttu-id="a910e-155">Använd Enable-PSRemoting-cmdleten om du vill aktivera fjärråtkomst till sessionsbaserade på datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-155">To enable remote access to the session configurations on the computer, use the Enable-PSRemoting cmdlet.</span></span>

<span data-ttu-id="a910e-156">Som standard har bara medlemmar i gruppen Administratörer på datorn behörigheten Kör för standardsession-konfigurationerna, men du kan ändra säkerhets beskrivarna på standardkonfigurationerna för sessioner och eventuella sessionsinställningar som du skapar.</span><span class="sxs-lookup"><span data-stu-id="a910e-156">Also, by default, only members of the Administrators group on the computer have Execute permission to the default session configurations, but you can change the security descriptors on the default session configurations and on any session configurations that you create.</span></span>

<span data-ttu-id="a910e-157">Om du vill ge andra användare behörighet att fjärrans luta till datorn använder du Set-PSSessionConfiguration-cmdleten för att lägga till "kör"-behörigheter för dessa användare till säkerhets beskrivarna i Microsoft. PowerShell-och Microsoft. PowerShell32-sessionens konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="a910e-157">To give other users permission to connect to the computer remotely, use the Set-PSSessionConfiguration cmdlet to add "Execute" permissions for those users to the security descriptors of the Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span>

<span data-ttu-id="a910e-158">Följande kommando öppnar exempelvis en egenskaps sida där du kan ändra säkerhets beskrivningen för standardsessions-konfigurationen i Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a910e-158">For example, the following command opens a property page that lets you change the security descriptor for the Microsoft.PowerShell default session configuration.</span></span>

```powershell
Set-PSSessionConfiguration -name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="a910e-159">Använd Disable-PSSessionConfiguration-cmdleten om du vill neka alla behörighet till alla sessioner på datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-159">To deny everyone permission to all the session configurations on the computer, use the Disable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="a910e-160">Följande kommando inaktiverar till exempel standardkonfigurationerna för sessioner på datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-160">For example, the following command disables the default session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSSessionConfiguration -Name Microsoft.PowerShell
```

<span data-ttu-id="a910e-161">För att förhindra att fjärran vändare ansluter till datorn, men Tillåt att lokala användare ansluter, använder du Disable-PSRemoting-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a910e-161">To prevent remote users from connecting to the computer, but allow local users to connect, use the Disable-PSRemoting cmdlet.</span></span> <span data-ttu-id="a910e-162">Disable-PSRemoting lägger till en "Network_Deny_All"-post till alla sessionsinställningar på datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-162">Disable-PSRemoting adds a "Network_Deny_All" entry to all session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSRemoting
```

<span data-ttu-id="a910e-163">Om du vill tillåta fjärran vändare att använda alla sessionsinställningar på datorn använder du Enable-PSRemoting-eller Enable-PSSessionConfiguration-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a910e-163">To allow remote users to use all session configurations on the computer, use the Enable-PSRemoting or Enable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="a910e-164">Följande kommando ger till exempel fjärråtkomst till de inbyggda session-konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="a910e-164">For example, the following command enables remote access to the built-in session configurations.</span></span>

```powershell
PS C:> Enable-PSSessionConfiguration -name Microsoft.Power*
```

<span data-ttu-id="a910e-165">Använd Set-PSSessionConfiguration-cmdleten om du vill göra andra ändringar i säkerhets beskrivningen för en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a910e-165">To make other changes to the security descriptor of a session configuration, use the Set-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="a910e-166">Använd parametern SecurityDescriptorSDDL för att skicka ett SDDL-sträng värde.</span><span class="sxs-lookup"><span data-stu-id="a910e-166">Use the SecurityDescriptorSDDL parameter to submit an SDDL string value.</span></span> <span data-ttu-id="a910e-167">Använd parametern ShowSecurityDescriptorUI för att visa en egenskaps sida för användar gränssnitt som hjälper dig att skapa en ny SDDL.</span><span class="sxs-lookup"><span data-stu-id="a910e-167">Use the ShowSecurityDescriptorUI parameter to display a user interface property sheet that helps you to create a new SDDL.</span></span>

<span data-ttu-id="a910e-168">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="a910e-168">For example:</span></span>

```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="a910e-169">Skapa en ny konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="a910e-169">Creating a New Session Configuration</span></span>

<span data-ttu-id="a910e-170">Använd Register-PSSessionConfiguration-cmdleten om du vill skapa en ny sessionsinformation på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-170">To create a new session configuration on the local computer, use the Register-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="a910e-171">Om du vill definiera den nya konfigurationen av sessionen kan du använda en C#-sammansättning, ett PowerShell-skript och parametrarna för Register-PSSessionConfiguration-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a910e-171">To define the new session configuration, you can use a C# assembly, a PowerShell script, and the parameters of the Register-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="a910e-172">Följande kommando skapar till exempel en sessionsnyckel som är identisk med konfigurationen av Microsoft. PowerShell-sessionen, förutom att den begränsar de data som tas emot från ett fjärrkommando till 20 megabyte (MB).</span><span class="sxs-lookup"><span data-stu-id="a910e-172">For example, the following command creates a session configuration that is identical the Microsoft.PowerShell session configuration, except that it limits the data received from a remote command to 20 megabytes (MB).</span></span> <span data-ttu-id="a910e-173">(Standardvärdet är 50 MB).</span><span class="sxs-lookup"><span data-stu-id="a910e-173">(The default is 50 MB).</span></span>

```powershell
Register-PSSessionConfiguration -Name NewConfig `
  -MaximumReceivedDataSizePerCommandMB 20
```

<span data-ttu-id="a910e-174">När du skapar en sessionsnyckel kan du hantera den med hjälp av de andra cmdletarna för sessions konfiguration och visas i filen WSMAN: Drive.</span><span class="sxs-lookup"><span data-stu-id="a910e-174">When you create a session configuration, you can manage it by using the other session configuration cmdlets, and it appears in the WSMAN: drive.</span></span>

<span data-ttu-id="a910e-175">Mer information finns i register-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="a910e-175">For more information, see Register-PSSessionConfiguration.</span></span>

<span data-ttu-id="a910e-176">Tar bort en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="a910e-176">Removing a Session Configuration</span></span>

<span data-ttu-id="a910e-177">Använd Unregister-PSSessionConfiguration-cmdleten om du vill ta bort en sessionsinformation från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-177">To remove a session configuration from the local computer, use the Unregister-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="a910e-178">Följande kommando tar till exempel bort konfigurationen av NewConfig-sessionen från datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-178">For example, the following command removes the NewConfig session configuration from the computer.</span></span>

```powershell
PS C:> Unregister-PSSessionConfiguration -Name NewConfig
```

<span data-ttu-id="a910e-179">Mer information finns i unregister-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="a910e-179">For more information, see Unregister-PSSessionConfiguration.</span></span>

<span data-ttu-id="a910e-180">Återställa en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="a910e-180">Restoring a Session Configuration</span></span>

<span data-ttu-id="a910e-181">Använd Enable-PSRemoting-cmdleten om du vill återställa en standardsessions-konfiguration som har tagits bort (avregistreras) av misstag.</span><span class="sxs-lookup"><span data-stu-id="a910e-181">To restore a default session configuration that was deleted (unregistered) accidentally, use the Enable-PSRemoting cmdlet.</span></span>

<span data-ttu-id="a910e-182">Enable-PSRemoting-cmdleten återskapar alla standardkonfigurationer för sessioner som inte finns på datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-182">The Enable-PSRemoting cmdlet recreates all default sessions configurations that do not exist on the computer.</span></span> <span data-ttu-id="a910e-183">Den skriver inte över eller ändrar egenskapsvärdena för befintliga sessioner.</span><span class="sxs-lookup"><span data-stu-id="a910e-183">It does not overwrite or change the property values of existing session configurations.</span></span>

<span data-ttu-id="a910e-184">Om du vill återställa de ursprungliga egenskapsvärdena för en standardsessions-konfiguration använder du Unregister-PSSessionConfiguration för att ta bort konfigurationen och använder sedan Enable-PSRemoting-cmdlet för att återskapa den.</span><span class="sxs-lookup"><span data-stu-id="a910e-184">To restore the original property values of a default session configuration, use the Unregister-PSSessionConfiguration to delete the session configuration and then use the Enable-PSRemoting cmdlet to recreate it.</span></span>

<span data-ttu-id="a910e-185">Välja en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="a910e-185">Selecting a Session Configuration</span></span>

<span data-ttu-id="a910e-186">Om du vill välja en viss sessionsinformation för en session använder du parametern ConfigurationName för New-PSSession, retur-PSSession eller Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="a910e-186">To select a particular session configuration for a session, use the ConfigurationName parameter of New-PSSession, Enter-PSSession, or Invoke-Command.</span></span>

<span data-ttu-id="a910e-187">Detta kommando använder till exempel cmdleten New-PSSession för att starta en PSSession på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-187">For example, this command uses the New-PSSession cmdlet to start a PSSession on the Server01 computer.</span></span> <span data-ttu-id="a910e-188">Kommandot använder parametern ConfigurationName för att välja WithProfile-konfigurationen på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-188">The command uses the ConfigurationName parameter to select the WithProfile configuration on the Server01 computer.</span></span>

```powershell
PS C:> New-PSSession -ComputerName Server01 -ConfigurationName WithProfile
```

<span data-ttu-id="a910e-189">Kommandot fungerar bara om den aktuella användaren har behörighet att använda WithProfile-sessionen eller kan ange autentiseringsuppgifterna för en användare som har de behörigheter som krävs.</span><span class="sxs-lookup"><span data-stu-id="a910e-189">This command will succeed only if the current user has permission to use the WithProfile session configuration or can supply the credentials of a user who has the required permissions.</span></span>

<span data-ttu-id="a910e-190">Du kan också använda variabeln $PSSessionConfigurationName för att ändra standard konfigurationen för sessionen på datorn.</span><span class="sxs-lookup"><span data-stu-id="a910e-190">You can also use the $PSSessionConfigurationName preference variable to change the default session configuration on the computer.</span></span> <span data-ttu-id="a910e-191">Mer information om variabeln $PSSessionConfigurationName finns about_Preference_Variables.</span><span class="sxs-lookup"><span data-stu-id="a910e-191">For more information about the $PSSessionConfigurationName preference variable, see about_Preference_Variables.</span></span>

## <a name="keywords"></a><span data-ttu-id="a910e-192">RESERVERADE</span><span class="sxs-lookup"><span data-stu-id="a910e-192">KEYWORDS</span></span>

<span data-ttu-id="a910e-193">about_Endpoints about_SessionConfigurations</span><span class="sxs-lookup"><span data-stu-id="a910e-193">about_Endpoints about_SessionConfigurations</span></span>

## <a name="see-also"></a><span data-ttu-id="a910e-194">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="a910e-194">SEE ALSO</span></span>

[<span data-ttu-id="a910e-195">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="a910e-195">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="a910e-196">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="a910e-196">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="a910e-197">about_Remote</span><span class="sxs-lookup"><span data-stu-id="a910e-197">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="a910e-198">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="a910e-198">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)

[<span data-ttu-id="a910e-199">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="a910e-199">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="a910e-200">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a910e-200">Disable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[<span data-ttu-id="a910e-201">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a910e-201">Enable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[<span data-ttu-id="a910e-202">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a910e-202">Get-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[<span data-ttu-id="a910e-203">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="a910e-203">New-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[<span data-ttu-id="a910e-204">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a910e-204">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[<span data-ttu-id="a910e-205">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a910e-205">Set-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[<span data-ttu-id="a910e-206">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="a910e-206">Test-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[<span data-ttu-id="a910e-207">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a910e-207">Unregister-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)
