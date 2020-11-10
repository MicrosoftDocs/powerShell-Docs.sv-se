---
description: Innehåller en översikt över hantering av webb tjänster (WS-Management) som bakgrund för att använda WS-Management-cmdlets i Windows PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WS Management_Cmdlets
ms.openlocfilehash: c9d89d0559bf844927976c78bde6fca58ffa8855
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390515"
---
# <a name="about-ws-management-cmdlets"></a><span data-ttu-id="dc577-104">Om WS-Management-cmdletar</span><span class="sxs-lookup"><span data-stu-id="dc577-104">About WS-Management Cmdlets</span></span>

## <a name="short-description"></a><span data-ttu-id="dc577-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="dc577-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="dc577-106">Innehåller en översikt över hantering av webb tjänster (WS-Management) som bakgrund för att använda WS-Management-cmdlets i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc577-106">Provides an overview of Web Services for Management (WS-Management) as background for using the WS-Management cmdlets in Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="dc577-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="dc577-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="dc577-108">Det här avsnittet innehåller en översikt över hantering av webb tjänster (WS-Management) som bakgrund för att använda WS-Management-cmdlets i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc577-108">This topic provides an overview of Web Services for Management (WS-Management) as background for using the WS-Management cmdlets in Windows PowerShell.</span></span> <span data-ttu-id="dc577-109">Det här avsnittet innehåller också länkar till mer information om WS-Management.</span><span class="sxs-lookup"><span data-stu-id="dc577-109">This topic also provides links to more information about WS-Management.</span></span> <span data-ttu-id="dc577-110">Microsoft-implementeringen av WS-Management kallas även Windows Remote Management (WinRM).</span><span class="sxs-lookup"><span data-stu-id="dc577-110">The Microsoft implementation of WS-Management is also known as Windows Remote Management (WinRM).</span></span>

## <a name="about-ws-management"></a><span data-ttu-id="dc577-111">Om WS-Management</span><span class="sxs-lookup"><span data-stu-id="dc577-111">About WS-Management</span></span>

<span data-ttu-id="dc577-112">Windows Remote Management är Microsofts implementering av WS-Management protokoll, ett standardiserat SOAP-baserat, brand Väggs vänligt protokoll som gör det möjligt för maskin vara och operativ system från olika leverantörer att samverka.</span><span class="sxs-lookup"><span data-stu-id="dc577-112">Windows Remote Management is the Microsoft implementation of the WS-Management protocol, a standard SOAP-based, firewall-friendly protocol that allows hardware and operating systems from different vendors to interoperate.</span></span> <span data-ttu-id="dc577-113">WS-Management protokoll specifikationen är ett vanligt sätt för system att komma åt och utbyta hanterings information över en IT-infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="dc577-113">The WS-Management protocol specification provides a common way for systems to access and exchange management information across an information technology (IT) infrastructure.</span></span> <span data-ttu-id="dc577-114">WS-Management och Intelligent Platform Management Interface (IPMI) tillsammans med händelse insamlaren är komponenter i Windows Hardware Management-funktioner.</span><span class="sxs-lookup"><span data-stu-id="dc577-114">WS-Management and Intelligent Platform Management Interface (IPMI), along with the Event Collector, are components of the Windows Hardware Management features.</span></span>

<span data-ttu-id="dc577-115">WS-Management protokollet baseras på följande standard-webb tjänst specifikationer: HTTPS, SOAP över HTTP (WS-I-profil), SOAP 1,2, WS-Addressing, WS-transfer, WS-Enumeration och WS-Eventing.</span><span class="sxs-lookup"><span data-stu-id="dc577-115">The WS-Management protocol is based on the following standard Web service specifications: HTTPS, SOAP over HTTP (WS-I profile), SOAP 1.2, WS-Addressing, WS-Transfer, WS-Enumeration, and WS-Eventing.</span></span>

## <a name="ws-management-and-wmi"></a><span data-ttu-id="dc577-116">WS-Management och WMI</span><span class="sxs-lookup"><span data-stu-id="dc577-116">WS-Management and WMI</span></span>

<span data-ttu-id="dc577-117">WS-Management kan användas för att hämta data som exponeras av Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="dc577-117">WS-Management can be used to retrieve data exposed by Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="dc577-118">Du kan hämta WMI-data med skript eller program som använder skript-API: et för WS-Management eller via kommando rads verktyget WinRM.</span><span class="sxs-lookup"><span data-stu-id="dc577-118">You can obtain WMI data with scripts or applications that use the WS-Management Scripting API or through the WinRM command-line tool.</span></span> <span data-ttu-id="dc577-119">WS-Management stöder de flesta välkända WMI-klasser och-åtgärder, inklusive inbäddade objekt.</span><span class="sxs-lookup"><span data-stu-id="dc577-119">WS-Management supports most of the familiar WMI classes and operations, including embedded objects.</span></span> <span data-ttu-id="dc577-120">WS-Management kan utnyttja WMI för att samla in data om resurser eller hantera resurser på en Windows-baserad dator.</span><span class="sxs-lookup"><span data-stu-id="dc577-120">WS-Management can leverage WMI to collect data about resources or to manage resources on a Windows-based computers.</span></span> <span data-ttu-id="dc577-121">Det innebär att du kan hämta data om objekt som diskar, nätverkskort, tjänster eller processer i företaget via den befintliga uppsättningen WMI-klasser.</span><span class="sxs-lookup"><span data-stu-id="dc577-121">That means that you can obtain data about objects such as disks, network adapters, services, or processes in your enterprise through the existing set of WMI classes.</span></span> <span data-ttu-id="dc577-122">Du kan också komma åt de maskin varu data som är tillgängliga från standard-WMI IPMI-providern.</span><span class="sxs-lookup"><span data-stu-id="dc577-122">You can also access the hardware data that is available from the standard WMI IPMI provider.</span></span>

## <a name="ws-management-windows-powershell-provider-wsman"></a><span data-ttu-id="dc577-123">WS-Management Windows PowerShell-Provider (WSMan)</span><span class="sxs-lookup"><span data-stu-id="dc577-123">WS-Management Windows PowerShell Provider (WSMan)</span></span>

<span data-ttu-id="dc577-124">WSMan-providern tillhandahåller en hierarkisk vy över tillgängliga WS-Management konfigurations inställningar.</span><span class="sxs-lookup"><span data-stu-id="dc577-124">The WSMan provider provides a hierarchical view into the available WS-Management configuration settings.</span></span> <span data-ttu-id="dc577-125">Med providern kan du utforska och ange de olika WS-Management konfigurations alternativen.</span><span class="sxs-lookup"><span data-stu-id="dc577-125">The provider allows you to explore and set the various WS-Management configuration options.</span></span>

## <a name="ws-management-configuration"></a><span data-ttu-id="dc577-126">WS-Management konfiguration</span><span class="sxs-lookup"><span data-stu-id="dc577-126">WS-Management Configuration</span></span>

<span data-ttu-id="dc577-127">Om WS-Management inte har installerats och kon figurer ATS är Windows PowerShell-fjärrkommunikation inte tillgänglig, WS-Management-cmdletarna inte körs, WS-Management skript inte körs och WSMan-providern kan inte utföra data åtgärder.</span><span class="sxs-lookup"><span data-stu-id="dc577-127">If WS-Management is not installed and configured, Windows PowerShell remoting is not available, the WS-Management cmdlets do not run, WS-Management scripts do not run, and the WSMan provider cannot perform data operations.</span></span> <span data-ttu-id="dc577-128">Kommando rads verktyget WS-Management, WinRM och event Forwarding är också beroende av WS-Management-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="dc577-128">The WS-Management command-line tool, WinRM, and event forwarding also depend on the WS-Management configuration.</span></span>

## <a name="ws-management-cmdlets"></a><span data-ttu-id="dc577-129">WS-Management-cmdletar</span><span class="sxs-lookup"><span data-stu-id="dc577-129">WS-Management Cmdlets</span></span>

<span data-ttu-id="dc577-130">WS-Management funktioner implementeras i Windows PowerShell via en modul som innehåller en uppsättning cmdlets och WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="dc577-130">WS-Management functionality is implemented in Windows PowerShell through a module that contains a set of cmdlets and the WSMan provider.</span></span> <span data-ttu-id="dc577-131">Du kan använda dessa cmdletar för att slutföra de slut punkt till slut punkts aktiviteter som krävs för att hantera WS-Management inställningar på lokala datorer och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="dc577-131">You can use these cmdlets to complete the end-to-end tasks necessary to manage WS-Management settings on local and remote computers.</span></span>

<span data-ttu-id="dc577-132">Följande WS-Management-cmdletar är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="dc577-132">The following WS-Management cmdlets are available.</span></span>

## <a name="connection-cmdlets"></a><span data-ttu-id="dc577-133">Anslutnings-cmdletar</span><span class="sxs-lookup"><span data-stu-id="dc577-133">Connection Cmdlets</span></span>

- <span data-ttu-id="dc577-134">Connect-WSMan: ansluter den lokala datorn till tjänsten WS-Management (WinRM) på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="dc577-134">Connect-WSMan: Connects the local computer to the WS-Management (WinRM) service on a remote computer.</span></span>

- <span data-ttu-id="dc577-135">Koppla från-WSMan: kopplar från den lokala datorn från tjänsten WS-Management (WinRM) på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="dc577-135">Disconnect-WSMan: Disconnects the local computer from the WS-Management (WinRM) service on a remote computer.</span></span>

## <a name="management-data-cmdlets"></a><span data-ttu-id="dc577-136">Management-Data-cmdletar</span><span class="sxs-lookup"><span data-stu-id="dc577-136">Management-Data Cmdlets</span></span>

- <span data-ttu-id="dc577-137">Get-WSManInstance: visar hanterings information för en resurs instans som anges av en resurs-URI.</span><span class="sxs-lookup"><span data-stu-id="dc577-137">Get-WSManInstance: Displays management information for a resource instance that is specified by a resource URI.</span></span>

- <span data-ttu-id="dc577-138">Invoke-WSManAction: anropar en åtgärd på målobjektet som anges av resurs-URI och av väljare.</span><span class="sxs-lookup"><span data-stu-id="dc577-138">Invoke-WSManAction: Invokes an action on the target object that is specified by the resource URI and by the selectors.</span></span>

- <span data-ttu-id="dc577-139">New-WSManInstance: skapar en ny hanterings resurs instans.</span><span class="sxs-lookup"><span data-stu-id="dc577-139">New-WSManInstance: Creates a new management resource instance.</span></span>

- <span data-ttu-id="dc577-140">Remove-WSManInstance: tar bort en hanterings resurs instans.</span><span class="sxs-lookup"><span data-stu-id="dc577-140">Remove-WSManInstance: Deletes a management resource instance.</span></span>

- <span data-ttu-id="dc577-141">Set-WSManInstance: ändrar hanterings information som är relaterad till en resurs.</span><span class="sxs-lookup"><span data-stu-id="dc577-141">Set-WSManInstance: Modifies the management information that is related to a resource.</span></span>

## <a name="setup-and-configuration-cmdlets"></a><span data-ttu-id="dc577-142">Installations-och konfigurations-cmdletar</span><span class="sxs-lookup"><span data-stu-id="dc577-142">Setup and Configuration Cmdlets</span></span>

- <span data-ttu-id="dc577-143">Set-WSManQuickConfig: konfigurerar den lokala datorn för fjärrhantering.</span><span class="sxs-lookup"><span data-stu-id="dc577-143">Set-WSManQuickConfig: Configures the local computer for remote management.</span></span>
  <span data-ttu-id="dc577-144">Du kan använda Set-WSManQuickConfig-cmdlet för att konfigurera WS-Management för att tillåta fjärr anslutningar till tjänsten WS-Management (WinRM).</span><span class="sxs-lookup"><span data-stu-id="dc577-144">You can use the Set-WSManQuickConfig cmdlet to configure WS-Management to allow remote connections to the WS-Management (WinRM) service.</span></span> <span data-ttu-id="dc577-145">Set-WSManQuickConfig cmdlet utför följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="dc577-145">The Set-WSManQuickConfig cmdlet performs the following operations:</span></span>
  - <span data-ttu-id="dc577-146">Den avgör om tjänsten WS-Management (WinRM) körs.</span><span class="sxs-lookup"><span data-stu-id="dc577-146">It determines whether the WS-Management (WinRM) service is running.</span></span> <span data-ttu-id="dc577-147">Om WinRM-tjänsten inte körs startar Set-WSManQuickConfig cmdleten tjänsten.</span><span class="sxs-lookup"><span data-stu-id="dc577-147">If the WinRM service is not running, the Set-WSManQuickConfig cmdlet starts the service.</span></span>
  - <span data-ttu-id="dc577-148">Den anger start typen för tjänsten WS-Management (WinRM) till automatisk.</span><span class="sxs-lookup"><span data-stu-id="dc577-148">It sets the WS-Management (WinRM) service startup type to automatic.</span></span>
  - <span data-ttu-id="dc577-149">Den skapar en lyssnare som accepterar begär Anden från alla IP-adresser.</span><span class="sxs-lookup"><span data-stu-id="dc577-149">It creates a listener that accepts requests from any IP address.</span></span> <span data-ttu-id="dc577-150">Standard transport protokollet är HTTP.</span><span class="sxs-lookup"><span data-stu-id="dc577-150">The default transport protocol is HTTP.</span></span>
  - <span data-ttu-id="dc577-151">Det aktiverar ett brand Väggs undantag för WS-Management trafik.</span><span class="sxs-lookup"><span data-stu-id="dc577-151">It enables a firewall exception for WS-Management traffic.</span></span>

  <span data-ttu-id="dc577-152">Obs! Om du vill köra den här cmdleten i Windows Vista, Windows Server 2008 och senare versioner av Windows, måste du starta Windows PowerShell med alternativet "kör som administratör".</span><span class="sxs-lookup"><span data-stu-id="dc577-152">Note: To run this cmdlet in Windows Vista, Windows Server 2008, and later versions of Windows, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

- <span data-ttu-id="dc577-153">Test-WSMan: verifierar att WS-Management har installerats och kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="dc577-153">Test-WSMan: Verifies that WS-Management is installed and configured.</span></span> <span data-ttu-id="dc577-154">Test-WSMan-cmdleten testar om tjänsten WS-Management (WinRM) körs och är konfigurerad på en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="dc577-154">The Test-WSMan cmdlet tests whether the WS-Management (WinRM) service is running and configured on a local or remote computer.</span></span>

- <span data-ttu-id="dc577-155">Disable-WSManCredSSP: inaktiverar CredSSP-autentisering på en klient dator.</span><span class="sxs-lookup"><span data-stu-id="dc577-155">Disable-WSManCredSSP: Disables CredSSP authentication on a client computer.</span></span>

- <span data-ttu-id="dc577-156">Enable-WSManCredSSP: aktiverar CredSSP-autentisering på en klient dator.</span><span class="sxs-lookup"><span data-stu-id="dc577-156">Enable-WSManCredSSP: Enables CredSSP authentication on a client computer.</span></span>

- <span data-ttu-id="dc577-157">Get-WSManCredSSP: hämtar den CredSSP-relaterade konfigurationen för en klient dator.</span><span class="sxs-lookup"><span data-stu-id="dc577-157">Get-WSManCredSSP: Gets the CredSSP-related configuration for a client computer.</span></span>

## <a name="ws-management-specific-cmdlets"></a><span data-ttu-id="dc577-158">WS-Management-Specific-cmdletar</span><span class="sxs-lookup"><span data-stu-id="dc577-158">WS-Management-Specific Cmdlets</span></span>

- <span data-ttu-id="dc577-159">New-WSManSessionOption: skapar ett WSManSessionOption-objekt som ska användas som inmatat för en eller flera parametrar för en WS-Management-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dc577-159">New-WSManSessionOption: Creates a WSManSessionOption object to use as input to one or more parameters of a WS-Management cmdlet.</span></span>

## <a name="additional-ws-management-information"></a><span data-ttu-id="dc577-160">Ytterligare WS-Management information</span><span class="sxs-lookup"><span data-stu-id="dc577-160">Additional WS-Management Information</span></span>

<span data-ttu-id="dc577-161">Mer information om WS-Management finns i följande avsnitt i Windows-dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="dc577-161">For more information about WS-Management, see the following topics in the Windows documentation.</span></span>

[<span data-ttu-id="dc577-162">Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="dc577-162">Windows Remote Management</span></span>](/windows/win32/winrm/portal)

[<span data-ttu-id="dc577-163">Om Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="dc577-163">About Windows Remote Management</span></span>](/windows/win32/winrm/about-windows-remote-management)

[<span data-ttu-id="dc577-164">Installation och konfigurering för Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="dc577-164">Installation and Configuration for Windows Remote Management</span></span>](/windows/win32/winrm/installation-and-configuration-for-windows-remote-management)

[<span data-ttu-id="dc577-165">Windows Remote Management-arkitektur</span><span class="sxs-lookup"><span data-stu-id="dc577-165">Windows Remote Management Architecture</span></span>](/windows/win32/winrm/windows-remote-management-architecture)

[<span data-ttu-id="dc577-166">WS-Managementprotokollet</span><span class="sxs-lookup"><span data-stu-id="dc577-166">WS-Management Protocol</span></span>](/windows/win32/winrm/ws-management-protocol)

[<span data-ttu-id="dc577-167">Windows Remote Management och WMI</span><span class="sxs-lookup"><span data-stu-id="dc577-167">Windows Remote Management and WMI</span></span>](/windows/win32/winrm/windows-remote-management-and-wmi)

[<span data-ttu-id="dc577-168">Resurs-URI: er</span><span class="sxs-lookup"><span data-stu-id="dc577-168">Resource URIs</span></span>](/windows/win32/winrm/resource-uris)

[<span data-ttu-id="dc577-169">Hantering av fjärrmaskinvara</span><span class="sxs-lookup"><span data-stu-id="dc577-169">Remote Hardware Management</span></span>](/windows/win32/winrm/remote-hardware-management)

[<span data-ttu-id="dc577-170">Händelser</span><span class="sxs-lookup"><span data-stu-id="dc577-170">Events</span></span>](/windows/win32/winrm/events)

## <a name="see-also"></a><span data-ttu-id="dc577-171">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="dc577-171">SEE ALSO</span></span>

[<span data-ttu-id="dc577-172">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="dc577-172">Connect-WSMan</span></span>](xref:Microsoft.WSMan.Management.Connect-WSMan)

[<span data-ttu-id="dc577-173">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="dc577-173">Disable-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Disable-WSManCredSSP)

[<span data-ttu-id="dc577-174">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="dc577-174">Disconnect-WSMan</span></span>](xref:Microsoft.WSMan.Management.Disconnect-WSMan)

[<span data-ttu-id="dc577-175">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="dc577-175">Enable-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Enable-WSManCredSSP)

[<span data-ttu-id="dc577-176">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="dc577-176">Get-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Get-WSManCredSSP)

[<span data-ttu-id="dc577-177">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="dc577-177">Get-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Get-WSManInstance)

[<span data-ttu-id="dc577-178">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="dc577-178">Invoke-WSManAction</span></span>](xref:Microsoft.WSMan.Management.Invoke-WSManAction)

[<span data-ttu-id="dc577-179">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="dc577-179">New-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.New-WSManInstance)

[<span data-ttu-id="dc577-180">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="dc577-180">Remove-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Remove-WSManInstance)

[<span data-ttu-id="dc577-181">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="dc577-181">Set-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Set-WSManInstance)

[<span data-ttu-id="dc577-182">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="dc577-182">Set-WSManQuickConfig</span></span>](xref:Microsoft.WSMan.Management.Set-WSManQuickConfig)

[<span data-ttu-id="dc577-183">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="dc577-183">Test-WSMan</span></span>](xref:Microsoft.WSMan.Management.Test-WSMan)
