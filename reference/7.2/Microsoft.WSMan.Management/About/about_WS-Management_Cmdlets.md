---
description: Innehåller en översikt över hantering av webb tjänster (WS-Management) som bakgrund för att använda WS-Management-cmdlets i Windows PowerShell.
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WS Management_Cmdlets
ms.openlocfilehash: faf0f0b08d604f7568ac316557788eea21feea8d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710332"
---
# <a name="about-ws-management-cmdlets"></a><span data-ttu-id="2086c-103">Om WS-Management-cmdletar</span><span class="sxs-lookup"><span data-stu-id="2086c-103">About WS-Management Cmdlets</span></span>

## <a name="short-description"></a><span data-ttu-id="2086c-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2086c-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="2086c-105">Innehåller en översikt över hantering av webb tjänster (WS-Management) som bakgrund för att använda WS-Management-cmdlets i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2086c-105">Provides an overview of Web Services for Management (WS-Management) as background for using the WS-Management cmdlets in Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="2086c-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2086c-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="2086c-107">Det här avsnittet innehåller en översikt över hantering av webb tjänster (WS-Management) som bakgrund för att använda WS-Management-cmdlets i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2086c-107">This topic provides an overview of Web Services for Management (WS-Management) as background for using the WS-Management cmdlets in Windows PowerShell.</span></span> <span data-ttu-id="2086c-108">Det här avsnittet innehåller också länkar till mer information om WS-Management.</span><span class="sxs-lookup"><span data-stu-id="2086c-108">This topic also provides links to more information about WS-Management.</span></span> <span data-ttu-id="2086c-109">Microsoft-implementeringen av WS-Management kallas även Windows Remote Management (WinRM).</span><span class="sxs-lookup"><span data-stu-id="2086c-109">The Microsoft implementation of WS-Management is also known as Windows Remote Management (WinRM).</span></span>

## <a name="about-ws-management"></a><span data-ttu-id="2086c-110">Om WS-Management</span><span class="sxs-lookup"><span data-stu-id="2086c-110">About WS-Management</span></span>

<span data-ttu-id="2086c-111">Windows Remote Management är Microsofts implementering av WS-Management protokoll, ett standardiserat SOAP-baserat, brand Väggs vänligt protokoll som gör det möjligt för maskin vara och operativ system från olika leverantörer att samverka.</span><span class="sxs-lookup"><span data-stu-id="2086c-111">Windows Remote Management is the Microsoft implementation of the WS-Management protocol, a standard SOAP-based, firewall-friendly protocol that allows hardware and operating systems from different vendors to interoperate.</span></span> <span data-ttu-id="2086c-112">WS-Management protokoll specifikationen är ett vanligt sätt för system att komma åt och utbyta hanterings information över en IT-infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="2086c-112">The WS-Management protocol specification provides a common way for systems to access and exchange management information across an information technology (IT) infrastructure.</span></span> <span data-ttu-id="2086c-113">WS-Management och Intelligent Platform Management Interface (IPMI) tillsammans med händelse insamlaren är komponenter i Windows Hardware Management-funktioner.</span><span class="sxs-lookup"><span data-stu-id="2086c-113">WS-Management and Intelligent Platform Management Interface (IPMI), along with the Event Collector, are components of the Windows Hardware Management features.</span></span>

<span data-ttu-id="2086c-114">WS-Management protokollet baseras på följande standard-webb tjänst specifikationer: HTTPS, SOAP över HTTP (WS-I-profil), SOAP 1,2, WS-Addressing, WS-transfer, WS-Enumeration och WS-Eventing.</span><span class="sxs-lookup"><span data-stu-id="2086c-114">The WS-Management protocol is based on the following standard Web service specifications: HTTPS, SOAP over HTTP (WS-I profile), SOAP 1.2, WS-Addressing, WS-Transfer, WS-Enumeration, and WS-Eventing.</span></span>

## <a name="ws-management-and-wmi"></a><span data-ttu-id="2086c-115">WS-Management och WMI</span><span class="sxs-lookup"><span data-stu-id="2086c-115">WS-Management and WMI</span></span>

<span data-ttu-id="2086c-116">WS-Management kan användas för att hämta data som exponeras av Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="2086c-116">WS-Management can be used to retrieve data exposed by Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="2086c-117">Du kan hämta WMI-data med skript eller program som använder skript-API: et för WS-Management eller via kommando rads verktyget WinRM.</span><span class="sxs-lookup"><span data-stu-id="2086c-117">You can obtain WMI data with scripts or applications that use the WS-Management Scripting API or through the WinRM command-line tool.</span></span> <span data-ttu-id="2086c-118">WS-Management stöder de flesta välkända WMI-klasser och-åtgärder, inklusive inbäddade objekt.</span><span class="sxs-lookup"><span data-stu-id="2086c-118">WS-Management supports most of the familiar WMI classes and operations, including embedded objects.</span></span> <span data-ttu-id="2086c-119">WS-Management kan utnyttja WMI för att samla in data om resurser eller hantera resurser på en Windows-baserad dator.</span><span class="sxs-lookup"><span data-stu-id="2086c-119">WS-Management can leverage WMI to collect data about resources or to manage resources on a Windows-based computers.</span></span> <span data-ttu-id="2086c-120">Det innebär att du kan hämta data om objekt som diskar, nätverkskort, tjänster eller processer i företaget via den befintliga uppsättningen WMI-klasser.</span><span class="sxs-lookup"><span data-stu-id="2086c-120">That means that you can obtain data about objects such as disks, network adapters, services, or processes in your enterprise through the existing set of WMI classes.</span></span> <span data-ttu-id="2086c-121">Du kan också komma åt de maskin varu data som är tillgängliga från standard-WMI IPMI-providern.</span><span class="sxs-lookup"><span data-stu-id="2086c-121">You can also access the hardware data that is available from the standard WMI IPMI provider.</span></span>

## <a name="ws-management-windows-powershell-provider-wsman"></a><span data-ttu-id="2086c-122">WS-Management Windows PowerShell-Provider (WSMan)</span><span class="sxs-lookup"><span data-stu-id="2086c-122">WS-Management Windows PowerShell Provider (WSMan)</span></span>

<span data-ttu-id="2086c-123">WSMan-providern tillhandahåller en hierarkisk vy över tillgängliga WS-Management konfigurations inställningar.</span><span class="sxs-lookup"><span data-stu-id="2086c-123">The WSMan provider provides a hierarchical view into the available WS-Management configuration settings.</span></span> <span data-ttu-id="2086c-124">Med providern kan du utforska och ange de olika WS-Management konfigurations alternativen.</span><span class="sxs-lookup"><span data-stu-id="2086c-124">The provider allows you to explore and set the various WS-Management configuration options.</span></span>

## <a name="ws-management-configuration"></a><span data-ttu-id="2086c-125">WS-Management konfiguration</span><span class="sxs-lookup"><span data-stu-id="2086c-125">WS-Management Configuration</span></span>

<span data-ttu-id="2086c-126">Om WS-Management inte har installerats och kon figurer ATS är Windows PowerShell-fjärrkommunikation inte tillgänglig, WS-Management-cmdletarna inte körs, WS-Management skript inte körs och WSMan-providern kan inte utföra data åtgärder.</span><span class="sxs-lookup"><span data-stu-id="2086c-126">If WS-Management is not installed and configured, Windows PowerShell remoting is not available, the WS-Management cmdlets do not run, WS-Management scripts do not run, and the WSMan provider cannot perform data operations.</span></span> <span data-ttu-id="2086c-127">Kommando rads verktyget WS-Management, WinRM och event Forwarding är också beroende av WS-Management-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="2086c-127">The WS-Management command-line tool, WinRM, and event forwarding also depend on the WS-Management configuration.</span></span>

## <a name="ws-management-cmdlets"></a><span data-ttu-id="2086c-128">WS-Management-cmdletar</span><span class="sxs-lookup"><span data-stu-id="2086c-128">WS-Management Cmdlets</span></span>

<span data-ttu-id="2086c-129">WS-Management funktioner implementeras i Windows PowerShell via en modul som innehåller en uppsättning cmdlets och WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="2086c-129">WS-Management functionality is implemented in Windows PowerShell through a module that contains a set of cmdlets and the WSMan provider.</span></span> <span data-ttu-id="2086c-130">Du kan använda dessa cmdletar för att slutföra de slut punkt till slut punkts aktiviteter som krävs för att hantera WS-Management inställningar på lokala datorer och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="2086c-130">You can use these cmdlets to complete the end-to-end tasks necessary to manage WS-Management settings on local and remote computers.</span></span>

<span data-ttu-id="2086c-131">Följande WS-Management-cmdletar är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="2086c-131">The following WS-Management cmdlets are available.</span></span>

## <a name="connection-cmdlets"></a><span data-ttu-id="2086c-132">Anslutnings-cmdletar</span><span class="sxs-lookup"><span data-stu-id="2086c-132">Connection Cmdlets</span></span>

- <span data-ttu-id="2086c-133">Connect-WSMan: ansluter den lokala datorn till tjänsten WS-Management (WinRM) på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="2086c-133">Connect-WSMan: Connects the local computer to the WS-Management (WinRM) service on a remote computer.</span></span>

- <span data-ttu-id="2086c-134">Koppla från-WSMan: kopplar från den lokala datorn från tjänsten WS-Management (WinRM) på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="2086c-134">Disconnect-WSMan: Disconnects the local computer from the WS-Management (WinRM) service on a remote computer.</span></span>

## <a name="management-data-cmdlets"></a><span data-ttu-id="2086c-135">Management-Data-cmdletar</span><span class="sxs-lookup"><span data-stu-id="2086c-135">Management-Data Cmdlets</span></span>

- <span data-ttu-id="2086c-136">Get-WSManInstance: visar hanterings information för en resurs instans som anges av en resurs-URI.</span><span class="sxs-lookup"><span data-stu-id="2086c-136">Get-WSManInstance: Displays management information for a resource instance that is specified by a resource URI.</span></span>

- <span data-ttu-id="2086c-137">Invoke-WSManAction: anropar en åtgärd på målobjektet som anges av resurs-URI och av väljare.</span><span class="sxs-lookup"><span data-stu-id="2086c-137">Invoke-WSManAction: Invokes an action on the target object that is specified by the resource URI and by the selectors.</span></span>

- <span data-ttu-id="2086c-138">New-WSManInstance: skapar en ny hanterings resurs instans.</span><span class="sxs-lookup"><span data-stu-id="2086c-138">New-WSManInstance: Creates a new management resource instance.</span></span>

- <span data-ttu-id="2086c-139">Remove-WSManInstance: tar bort en hanterings resurs instans.</span><span class="sxs-lookup"><span data-stu-id="2086c-139">Remove-WSManInstance: Deletes a management resource instance.</span></span>

- <span data-ttu-id="2086c-140">Set-WSManInstance: ändrar hanterings information som är relaterad till en resurs.</span><span class="sxs-lookup"><span data-stu-id="2086c-140">Set-WSManInstance: Modifies the management information that is related to a resource.</span></span>

## <a name="setup-and-configuration-cmdlets"></a><span data-ttu-id="2086c-141">Installations-och konfigurations-cmdletar</span><span class="sxs-lookup"><span data-stu-id="2086c-141">Setup and Configuration Cmdlets</span></span>

- <span data-ttu-id="2086c-142">Set-WSManQuickConfig: konfigurerar den lokala datorn för fjärrhantering.</span><span class="sxs-lookup"><span data-stu-id="2086c-142">Set-WSManQuickConfig: Configures the local computer for remote management.</span></span>
  <span data-ttu-id="2086c-143">Du kan använda Set-WSManQuickConfig-cmdlet för att konfigurera WS-Management för att tillåta fjärr anslutningar till tjänsten WS-Management (WinRM).</span><span class="sxs-lookup"><span data-stu-id="2086c-143">You can use the Set-WSManQuickConfig cmdlet to configure WS-Management to allow remote connections to the WS-Management (WinRM) service.</span></span> <span data-ttu-id="2086c-144">Set-WSManQuickConfig cmdlet utför följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="2086c-144">The Set-WSManQuickConfig cmdlet performs the following operations:</span></span>
  - <span data-ttu-id="2086c-145">Den avgör om tjänsten WS-Management (WinRM) körs.</span><span class="sxs-lookup"><span data-stu-id="2086c-145">It determines whether the WS-Management (WinRM) service is running.</span></span> <span data-ttu-id="2086c-146">Om WinRM-tjänsten inte körs startar Set-WSManQuickConfig cmdleten tjänsten.</span><span class="sxs-lookup"><span data-stu-id="2086c-146">If the WinRM service is not running, the Set-WSManQuickConfig cmdlet starts the service.</span></span>
  - <span data-ttu-id="2086c-147">Den anger start typen för tjänsten WS-Management (WinRM) till automatisk.</span><span class="sxs-lookup"><span data-stu-id="2086c-147">It sets the WS-Management (WinRM) service startup type to automatic.</span></span>
  - <span data-ttu-id="2086c-148">Den skapar en lyssnare som accepterar begär Anden från alla IP-adresser.</span><span class="sxs-lookup"><span data-stu-id="2086c-148">It creates a listener that accepts requests from any IP address.</span></span> <span data-ttu-id="2086c-149">Standard transport protokollet är HTTP.</span><span class="sxs-lookup"><span data-stu-id="2086c-149">The default transport protocol is HTTP.</span></span>
  - <span data-ttu-id="2086c-150">Det aktiverar ett brand Väggs undantag för WS-Management trafik.</span><span class="sxs-lookup"><span data-stu-id="2086c-150">It enables a firewall exception for WS-Management traffic.</span></span>

  <span data-ttu-id="2086c-151">Obs! Om du vill köra den här cmdleten i Windows Vista, Windows Server 2008 och senare versioner av Windows, måste du starta Windows PowerShell med alternativet "kör som administratör".</span><span class="sxs-lookup"><span data-stu-id="2086c-151">Note: To run this cmdlet in Windows Vista, Windows Server 2008, and later versions of Windows, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

- <span data-ttu-id="2086c-152">Test-WSMan: verifierar att WS-Management har installerats och kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="2086c-152">Test-WSMan: Verifies that WS-Management is installed and configured.</span></span> <span data-ttu-id="2086c-153">Test-WSMan-cmdleten testar om tjänsten WS-Management (WinRM) körs och är konfigurerad på en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="2086c-153">The Test-WSMan cmdlet tests whether the WS-Management (WinRM) service is running and configured on a local or remote computer.</span></span>

- <span data-ttu-id="2086c-154">Disable-WSManCredSSP: inaktiverar CredSSP-autentisering på en klient dator.</span><span class="sxs-lookup"><span data-stu-id="2086c-154">Disable-WSManCredSSP: Disables CredSSP authentication on a client computer.</span></span>

- <span data-ttu-id="2086c-155">Enable-WSManCredSSP: aktiverar CredSSP-autentisering på en klient dator.</span><span class="sxs-lookup"><span data-stu-id="2086c-155">Enable-WSManCredSSP: Enables CredSSP authentication on a client computer.</span></span>

- <span data-ttu-id="2086c-156">Get-WSManCredSSP: hämtar den CredSSP-relaterade konfigurationen för en klient dator.</span><span class="sxs-lookup"><span data-stu-id="2086c-156">Get-WSManCredSSP: Gets the CredSSP-related configuration for a client computer.</span></span>

## <a name="ws-management-specific-cmdlets"></a><span data-ttu-id="2086c-157">WS-Management-Specific-cmdletar</span><span class="sxs-lookup"><span data-stu-id="2086c-157">WS-Management-Specific Cmdlets</span></span>

- <span data-ttu-id="2086c-158">New-WSManSessionOption: skapar ett WSManSessionOption-objekt som ska användas som inmatat för en eller flera parametrar för en WS-Management-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2086c-158">New-WSManSessionOption: Creates a WSManSessionOption object to use as input to one or more parameters of a WS-Management cmdlet.</span></span>

## <a name="additional-ws-management-information"></a><span data-ttu-id="2086c-159">Ytterligare WS-Management information</span><span class="sxs-lookup"><span data-stu-id="2086c-159">Additional WS-Management Information</span></span>

<span data-ttu-id="2086c-160">Mer information om WS-Management finns i följande avsnitt i Windows-dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="2086c-160">For more information about WS-Management, see the following topics in the Windows documentation.</span></span>

[<span data-ttu-id="2086c-161">Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="2086c-161">Windows Remote Management</span></span>](/windows/win32/winrm/portal)

[<span data-ttu-id="2086c-162">Om Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="2086c-162">About Windows Remote Management</span></span>](/windows/win32/winrm/about-windows-remote-management)

[<span data-ttu-id="2086c-163">Installation och konfigurering för Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="2086c-163">Installation and Configuration for Windows Remote Management</span></span>](/windows/win32/winrm/installation-and-configuration-for-windows-remote-management)

[<span data-ttu-id="2086c-164">Windows Remote Management-arkitektur</span><span class="sxs-lookup"><span data-stu-id="2086c-164">Windows Remote Management Architecture</span></span>](/windows/win32/winrm/windows-remote-management-architecture)

[<span data-ttu-id="2086c-165">WS-Managementprotokollet</span><span class="sxs-lookup"><span data-stu-id="2086c-165">WS-Management Protocol</span></span>](/windows/win32/winrm/ws-management-protocol)

[<span data-ttu-id="2086c-166">Windows Remote Management och WMI</span><span class="sxs-lookup"><span data-stu-id="2086c-166">Windows Remote Management and WMI</span></span>](/windows/win32/winrm/windows-remote-management-and-wmi)

[<span data-ttu-id="2086c-167">Resurs-URI: er</span><span class="sxs-lookup"><span data-stu-id="2086c-167">Resource URIs</span></span>](/windows/win32/winrm/resource-uris)

[<span data-ttu-id="2086c-168">Hantering av fjärrmaskinvara</span><span class="sxs-lookup"><span data-stu-id="2086c-168">Remote Hardware Management</span></span>](/windows/win32/winrm/remote-hardware-management)

[<span data-ttu-id="2086c-169">Händelser</span><span class="sxs-lookup"><span data-stu-id="2086c-169">Events</span></span>](/windows/win32/winrm/events)

## <a name="see-also"></a><span data-ttu-id="2086c-170">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="2086c-170">SEE ALSO</span></span>

[<span data-ttu-id="2086c-171">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="2086c-171">Connect-WSMan</span></span>](xref:Microsoft.WSMan.Management.Connect-WSMan)

[<span data-ttu-id="2086c-172">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="2086c-172">Disable-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Disable-WSManCredSSP)

[<span data-ttu-id="2086c-173">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="2086c-173">Disconnect-WSMan</span></span>](xref:Microsoft.WSMan.Management.Disconnect-WSMan)

[<span data-ttu-id="2086c-174">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="2086c-174">Enable-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Enable-WSManCredSSP)

[<span data-ttu-id="2086c-175">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="2086c-175">Get-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Get-WSManCredSSP)

[<span data-ttu-id="2086c-176">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2086c-176">Get-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Get-WSManInstance)

[<span data-ttu-id="2086c-177">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="2086c-177">Invoke-WSManAction</span></span>](xref:Microsoft.WSMan.Management.Invoke-WSManAction)

[<span data-ttu-id="2086c-178">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2086c-178">New-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.New-WSManInstance)

[<span data-ttu-id="2086c-179">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2086c-179">Remove-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Remove-WSManInstance)

[<span data-ttu-id="2086c-180">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="2086c-180">Set-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Set-WSManInstance)

[<span data-ttu-id="2086c-181">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="2086c-181">Set-WSManQuickConfig</span></span>](xref:Microsoft.WSMan.Management.Set-WSManQuickConfig)

[<span data-ttu-id="2086c-182">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="2086c-182">Test-WSMan</span></span>](xref:Microsoft.WSMan.Management.Test-WSMan)
