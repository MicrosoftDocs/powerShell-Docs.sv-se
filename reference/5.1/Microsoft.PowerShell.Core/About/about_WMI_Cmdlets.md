---
description: Innehåller bakgrunds information om Windows Management Instrumentation (WMI) och Windows PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI_Cmdlets
ms.openlocfilehash: c2099c005cedf64e9621d66d6757419320c9b43e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271917"
---
# <a name="about-wmi-cmdlets"></a><span data-ttu-id="d69c8-104">Om WMI-cmdletar</span><span class="sxs-lookup"><span data-stu-id="d69c8-104">About WMI Cmdlets</span></span>

## <a name="short-description"></a><span data-ttu-id="d69c8-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d69c8-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="d69c8-106">Innehåller bakgrunds information om Windows Management Instrumentation (WMI) och Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d69c8-106">Provides background information about Windows Management Instrumentation (WMI) and Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="d69c8-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d69c8-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="d69c8-108">Det här avsnittet innehåller information om WMI-teknik, WMI-cmdletar för Windows PowerShell, WMI-baserad fjärr kommunikation, WMI-acceleratorer och WMI-felsökning.</span><span class="sxs-lookup"><span data-stu-id="d69c8-108">This topic provides information about WMI technology, the WMI cmdlets for Windows PowerShell, WMI-based remoting, WMI accelerators, and WMI troubleshooting.</span></span> <span data-ttu-id="d69c8-109">Det här avsnittet innehåller också länkar till mer information om WMI.</span><span class="sxs-lookup"><span data-stu-id="d69c8-109">This topic also provides links to more information about WMI.</span></span>

### <a name="about-wmi"></a><span data-ttu-id="d69c8-110">OM WMI</span><span class="sxs-lookup"><span data-stu-id="d69c8-110">ABOUT WMI</span></span>

<span data-ttu-id="d69c8-111">Windows Management Instrumentation (WMI) är Microsofts implementering av webbaserad företagshantering (WBEM), som är ett branschinitiativ för utveckling av en standardteknik för åtkomst av hanteringsinformation i en företagsmiljö.</span><span class="sxs-lookup"><span data-stu-id="d69c8-111">Windows Management Instrumentation (WMI) is the Microsoft implementation of Web-Based Enterprise Management (WBEM), which is an industry initiative to develop a standard technology for accessing management information in an enterprise environment.</span></span> <span data-ttu-id="d69c8-112">WMI använder branschstandarden CIM (Common Information Model) för att representera system, program, nätverk, enheter och andra hanterade komponenter.</span><span class="sxs-lookup"><span data-stu-id="d69c8-112">WMI uses the Common Information Model (CIM) industry standard to represent systems, applications, networks, devices, and other managed components.</span></span> <span data-ttu-id="d69c8-113">CIM har utvecklats och underhålls av DMTF (Distributed Management Task Force).</span><span class="sxs-lookup"><span data-stu-id="d69c8-113">CIM is developed and maintained by the Distributed Management Task Force (DMTF).</span></span> <span data-ttu-id="d69c8-114">Du kan använda WMI för att hantera både lokala och fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="d69c8-114">You can use WMI to manage both local and remote computers.</span></span> <span data-ttu-id="d69c8-115">Du kan till exempel använda WMI för att göra följande:</span><span class="sxs-lookup"><span data-stu-id="d69c8-115">For example, you can use WMI to do the following:</span></span>

- <span data-ttu-id="d69c8-116">Starta en process på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="d69c8-116">Start a process on a remote computer.</span></span>
- <span data-ttu-id="d69c8-117">Starta om en dator via en fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="d69c8-117">Restart a computer remotely.</span></span>
- <span data-ttu-id="d69c8-118">Hämta en lista över de program som är installerade på en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="d69c8-118">Get a list of the applications that are installed on a local or remote computer.</span></span>
- <span data-ttu-id="d69c8-119">Fråga Windows-händelseloggen på en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="d69c8-119">Query the Windows event logs on a local or remote computer.</span></span>

### <a name="the-wmi-cmdlets-for-windows-powershell"></a><span data-ttu-id="d69c8-120">WMI-CMDLETAR FÖR WINDOWS POWERSHELL</span><span class="sxs-lookup"><span data-stu-id="d69c8-120">THE WMI CMDLETS FOR WINDOWS POWERSHELL</span></span>

<span data-ttu-id="d69c8-121">Windows PowerShell implementerar WMI-funktioner via en uppsättning cmdletar som är tillgängliga i Windows PowerShell som standard.</span><span class="sxs-lookup"><span data-stu-id="d69c8-121">Windows PowerShell implements WMI functionality through a set of cmdlets that are available in Windows PowerShell by default.</span></span> <span data-ttu-id="d69c8-122">Du kan använda dessa cmdletar för att slutföra de slut punkt till slut punkts uppgifter som krävs för att hantera lokala och fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="d69c8-122">You can use these cmdlets to complete the end-to-end tasks necessary to manage local and remote computers.</span></span>

<span data-ttu-id="d69c8-123">Följande WMI-cmdletar ingår.</span><span class="sxs-lookup"><span data-stu-id="d69c8-123">The following WMI cmdlets are included.</span></span>

|<span data-ttu-id="d69c8-124">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d69c8-124">Cmdlet</span></span>           |<span data-ttu-id="d69c8-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d69c8-125">Description</span></span>                                   |
|-----------------|----------------------------------------------|
|<span data-ttu-id="d69c8-126">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="d69c8-126">Get-WmiObject</span></span>    |<span data-ttu-id="d69c8-127">Hämtar instanser av WMI-klasser eller information</span><span class="sxs-lookup"><span data-stu-id="d69c8-127">Gets instances of WMI classes or information</span></span>  |
|                 |<span data-ttu-id="d69c8-128">om tillgängliga klasser.</span><span class="sxs-lookup"><span data-stu-id="d69c8-128">about the available classes.</span></span>                  |
|<span data-ttu-id="d69c8-129">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="d69c8-129">Invoke-WmiMethod</span></span> |<span data-ttu-id="d69c8-130">Anropar WMI-metoder.</span><span class="sxs-lookup"><span data-stu-id="d69c8-130">Calls WMI methods.</span></span>                            |
|<span data-ttu-id="d69c8-131">Register-WmiEvent</span><span class="sxs-lookup"><span data-stu-id="d69c8-131">Register-WmiEvent</span></span>|<span data-ttu-id="d69c8-132">Prenumererar på en WMI-händelse.</span><span class="sxs-lookup"><span data-stu-id="d69c8-132">Subscribes to a WMI event.</span></span>                    |
|<span data-ttu-id="d69c8-133">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="d69c8-133">Remove-WmiObject</span></span> |<span data-ttu-id="d69c8-134">Tar bort WMI-klasser och-instanser.</span><span class="sxs-lookup"><span data-stu-id="d69c8-134">Deletes WMI classes and instances.</span></span>            |
|<span data-ttu-id="d69c8-135">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="d69c8-135">Set-WmiInstance</span></span>  |<span data-ttu-id="d69c8-136">Skapar eller ändrar instanser av WMI-klasser.</span><span class="sxs-lookup"><span data-stu-id="d69c8-136">Creates or modifies instances of WMI classes.</span></span> |

### <a name="sample-commands"></a><span data-ttu-id="d69c8-137">EXEMPEL KOMMANDON</span><span class="sxs-lookup"><span data-stu-id="d69c8-137">SAMPLE COMMANDS</span></span>
<span data-ttu-id="d69c8-138">Följande kommando visar BIOS-information för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="d69c8-138">The following command displays the BIOS information for the local computer.</span></span>

```powershell
C:\PS> get-wmiobject win32_bios | format-list *
```

<span data-ttu-id="d69c8-139">Följande kommando visar information om WinRM-tjänsten för tre fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="d69c8-139">The following command displays information about the WinRM service for three remote computers.</span></span>

```powershell
$wql = "select * from win32_service where name='WinRM'"
get-wmiobject -query $wql -computername server01, server01, server03
```

<span data-ttu-id="d69c8-140">Följande mer komplexa kommando avslutar alla instanser av ett program.</span><span class="sxs-lookup"><span data-stu-id="d69c8-140">The following more complex command exits all instances of a program.</span></span>

```powershell
C:\PS> notepad.exe
C:\PS> $wql = "select * from win32_process where name='notepad.exe'"
C:\PS> $np = get-wmiobject -query $wql
C:\PS> $np | remove-wmiobject
```

### <a name="wmi-based-remoting"></a><span data-ttu-id="d69c8-141">WMI-BASERAD FJÄRR KOMMUNIKATION</span><span class="sxs-lookup"><span data-stu-id="d69c8-141">WMI-BASED REMOTING</span></span>

<span data-ttu-id="d69c8-142">Även om möjligheten att hantera ett lokalt system via WMI är användbar, är det fjärr kommunikations funktioner som gör WMI till ett kraftfullt administrativt verktyg.</span><span class="sxs-lookup"><span data-stu-id="d69c8-142">While the ability to manage a local system through WMI is useful, it is the remoting capabilities that make WMI a powerful administrative tool.</span></span> <span data-ttu-id="d69c8-143">WMI använder Microsofts DCOM (Distributed Component Object Model) för att ansluta till och hantera system.</span><span class="sxs-lookup"><span data-stu-id="d69c8-143">WMI uses Microsoft's Distributed Component Object Model (DCOM) to connect to and manage systems.</span></span> <span data-ttu-id="d69c8-144">Du kan behöva konfigurera vissa system för att tillåta DCOM-anslutningar.</span><span class="sxs-lookup"><span data-stu-id="d69c8-144">You might have to configure some systems to allow DCOM connections.</span></span>
<span data-ttu-id="d69c8-145">Brand Väggs inställningar och nedlåsta DCOM-behörigheter kan blockera WMI: s möjlighet att fjärrhantera system.</span><span class="sxs-lookup"><span data-stu-id="d69c8-145">Firewall settings and locked-down DCOM permissions can block WMI's ability to remotely manage systems.</span></span>

### <a name="wmi-type-accelerators"></a><span data-ttu-id="d69c8-146">ACCELERATORER FÖR WMI-TYP</span><span class="sxs-lookup"><span data-stu-id="d69c8-146">WMI TYPE ACCELERATORS</span></span>

<span data-ttu-id="d69c8-147">Windows PowerShell innehåller acceleratorer för WMI-typ.</span><span class="sxs-lookup"><span data-stu-id="d69c8-147">Windows PowerShell includes WMI type accelerators.</span></span> <span data-ttu-id="d69c8-148">Dessa WMI-typer acceleratorer (genvägar) tillåter mer direkt åtkomst till ett WMI-objekt än en typ som inte är av typen Accelerator som tillåter.</span><span class="sxs-lookup"><span data-stu-id="d69c8-148">These WMI type accelerators (shortcuts) allow more direct access to a WMI objects than a non-type accelerator approach would allow.</span></span>

<span data-ttu-id="d69c8-149">Följande typ acceleratorer stöds med WMI:</span><span class="sxs-lookup"><span data-stu-id="d69c8-149">The following type accelerators are supported with WMI:</span></span>

<span data-ttu-id="d69c8-150">[WMISEARCHER] – en genväg för att söka efter WMI-objekt.</span><span class="sxs-lookup"><span data-stu-id="d69c8-150">[WMISEARCHER] - A shortcut for searching for WMI objects.</span></span>

<span data-ttu-id="d69c8-151">[WMICLASS] – en genväg för att få åtkomst till statiska egenskaper och metoder för en klass.</span><span class="sxs-lookup"><span data-stu-id="d69c8-151">[WMICLASS] - A shortcut for accessing the static properties and methods of a class.</span></span>

<span data-ttu-id="d69c8-152">[WMI] – en genväg för att hämta en enda instans av en klass.</span><span class="sxs-lookup"><span data-stu-id="d69c8-152">[WMI] - A shortcut for getting a single instance of a class.</span></span>

<span data-ttu-id="d69c8-153">[WMISEARCHER] är en typ Accelerator för en ManagementObjectSearcher.</span><span class="sxs-lookup"><span data-stu-id="d69c8-153">[WMISEARCHER] is a type accelerator for a ManagementObjectSearcher.</span></span> <span data-ttu-id="d69c8-154">Det kan ta en sträng konstruktor för att skapa en sökre som du sedan kan göra en GET () på.</span><span class="sxs-lookup"><span data-stu-id="d69c8-154">It can take a string constructor to create a searcher that you can then do a GET() on.</span></span>

<span data-ttu-id="d69c8-155">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="d69c8-155">For example:</span></span>

```powershell
PS> $s = [WmiSearcher]'Select * from Win32_Process where Handlecount > 1000'
PS> $s.Get() |sort handlecount |ft handlecount,__path,name -auto

count  __PATH                                              name
-----  ------                                              ----
1105   \\SERVER01\root\cimv2:Win32_Process.Handle="3724"   PowerShell...
1132   \\SERVER01\root\cimv2:Win32_Process.Handle="1388"   winlogon.exe
1495   \\SERVER01\root\cimv2:Win32_Process.Handle="2852"   iexplore.exe
1699   \\SERVER01\root\cimv2:Win32_Process.Handle="1204"   OUTLOOK.EXE
1719   \\SERVER01\root\cimv2:Win32_Process.Handle="1912"   iexplore.exe
2579   \\SERVER01\root\cimv2:Win32_Process.Handle="1768"   svchost.exe
```

<span data-ttu-id="d69c8-156">[WMICLASS] är en typ Accelerator för ManagementClass.</span><span class="sxs-lookup"><span data-stu-id="d69c8-156">[WMICLASS] is a type accelerator for ManagementClass.</span></span> <span data-ttu-id="d69c8-157">Detta har en sträng konstruktor som tar en lokal eller absolut WMI-sökväg till en WMI-klass och returnerar ett objekt som är kopplat till den klassen.</span><span class="sxs-lookup"><span data-stu-id="d69c8-157">This has a string constructor that takes a local or absolute WMI path to a WMI class and returns an object that is bound to that class.</span></span>

<span data-ttu-id="d69c8-158">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="d69c8-158">For example:</span></span>

```powershell
PS> $c = [WMICLASS]"root\cimv2:WIn32_Process"
PS> $c |fl *
Name             : Win32_Process
__GENUS          : 1
__CLASS          : Win32_Process
__SUPERCLASS     : CIM_Process
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Process
__PROPERTY_COUNT : 45
__DERIVATION     : {CIM_Process, CIM_LogicalElement,
                   CIM_ManagedSystemElement}
__SERVER         : SERVER01
__NAMESPACE      : ROOT\cimv2
__PATH           : \\SERVER01\ROOT\cimv2:Win32_Process
```

<span data-ttu-id="d69c8-159">[WMI] är en typ Accelerator för ManagementObject.</span><span class="sxs-lookup"><span data-stu-id="d69c8-159">[WMI] is a type accelerator for ManagementObject.</span></span> <span data-ttu-id="d69c8-160">Detta har en sträng konstruktor som tar en lokal eller absolut WMI-sökväg till en WMI-instans och returnerar ett objekt som är kopplat till den instansen.</span><span class="sxs-lookup"><span data-stu-id="d69c8-160">This has a string constructor that takes a local or absolute WMI path to a WMI instance and returns an object that is bound to that instance.</span></span>

<span data-ttu-id="d69c8-161">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="d69c8-161">For example:</span></span>

```powershell
PS> $p = [WMI]'\\SERVER01\root\cimv2:Win32_Process.Handle="1204"'
PS> $p.Name
OUTLOOK.EXE
```

### <a name="wmi-troubleshooting"></a><span data-ttu-id="d69c8-162">WMI-FELSÖKNING</span><span class="sxs-lookup"><span data-stu-id="d69c8-162">WMI TROUBLESHOOTING</span></span>

<span data-ttu-id="d69c8-163">Följande problem är de vanligaste problemen som kan uppstå när du försöker ansluta till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="d69c8-163">The following problems are the most common problems that might occur when you try to connect to a remote computer.</span></span>

<span data-ttu-id="d69c8-164">Problem 1: fjärrdatorn är inte online.</span><span class="sxs-lookup"><span data-stu-id="d69c8-164">Problem 1: The remote computer is not online.</span></span>

<span data-ttu-id="d69c8-165">Om en dator är offline går det inte att ansluta till den med hjälp av WMI.</span><span class="sxs-lookup"><span data-stu-id="d69c8-165">If a computer is offline, you will not be able to connect to it by using WMI.</span></span>
<span data-ttu-id="d69c8-166">Du kan få följande felmeddelande:</span><span class="sxs-lookup"><span data-stu-id="d69c8-166">You may receive the following error message:</span></span>

```
Remote server machine does not exist or is unavailable
```

<span data-ttu-id="d69c8-167">Om du får det här fel meddelandet kontrollerar du att datorn är online.</span><span class="sxs-lookup"><span data-stu-id="d69c8-167">If you receive this error message, verify that the computer is online.</span></span> <span data-ttu-id="d69c8-168">Försök att pinga fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="d69c8-168">Try to ping the remote computer.</span></span>

<span data-ttu-id="d69c8-169">Problem 2: du har inte lokal administratörs behörighet på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="d69c8-169">Problem 2: You do not have local administrator rights on the remote computer.</span></span>

<span data-ttu-id="d69c8-170">Du måste ha lokal administratörs behörighet på fjärrdatorn för att kunna använda WMI via fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="d69c8-170">To use WMI remotely, you must have local administrator rights on the remote computer.</span></span> <span data-ttu-id="d69c8-171">Om du inte gör det kommer åtkomst till datorn att nekas.</span><span class="sxs-lookup"><span data-stu-id="d69c8-171">If you do not, access to that computer will be denied.</span></span>

<span data-ttu-id="d69c8-172">För att verifiera namn områdes säkerhet:</span><span class="sxs-lookup"><span data-stu-id="d69c8-172">To verify namespace security:</span></span>

1. <span data-ttu-id="d69c8-173">Klicka på Start, högerklicka på den här datorn och klicka sedan på hantera.</span><span class="sxs-lookup"><span data-stu-id="d69c8-173">Click Start, right-click My Computer, and then click Manage.</span></span>
2. <span data-ttu-id="d69c8-174">Expandera tjänster och program i dator hantering, högerklicka på WMI-kontroll och klicka sedan på egenskaper.</span><span class="sxs-lookup"><span data-stu-id="d69c8-174">In Computer Management, expand Services and Applications, right-click WMI Control, and then click Properties.</span></span>
3. <span data-ttu-id="d69c8-175">I dialog rutan Egenskaper för WMI-kontroll klickar du på fliken säkerhet.</span><span class="sxs-lookup"><span data-stu-id="d69c8-175">In the WMI Control Properties dialog box, click  the Security tab.</span></span>

<span data-ttu-id="d69c8-176">Problem 3: en brand vägg blockerar åtkomsten till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="d69c8-176">Problem 3: A firewall is blocking access to the remote computer.</span></span>

<span data-ttu-id="d69c8-177">WMI använder protokollen DCOM (Distributed COM) och RPC (Remote Procedure Call) för att passera nätverket.</span><span class="sxs-lookup"><span data-stu-id="d69c8-177">WMI uses the DCOM (Distributed COM) and RPC (Remote Procedure Call) protocols to traverse the network.</span></span> <span data-ttu-id="d69c8-178">Som standard blockerar många brand väggar DCOM-och RPC-trafik.</span><span class="sxs-lookup"><span data-stu-id="d69c8-178">By default, many firewalls block DCOM and RPC traffic.</span></span> <span data-ttu-id="d69c8-179">Om brand väggen blockerar dessa protokoll kommer anslutningen att Miss förväntas.</span><span class="sxs-lookup"><span data-stu-id="d69c8-179">If your firewall is blocking these protocols, your connection will fail.</span></span> <span data-ttu-id="d69c8-180">Windows-brandväggen i Microsoft Windows XP Service Pack 2 är till exempel konfigurerad för att automatiskt blockera all oönskad nätverks trafik, inklusive DCOM och WMI.</span><span class="sxs-lookup"><span data-stu-id="d69c8-180">For example, Windows Firewall in Microsoft Windows XP Service Pack 2 is configured to automatically block all unsolicited network traffic, including DCOM and WMI.</span></span> <span data-ttu-id="d69c8-181">I standard konfigurationen avvisar Windows-brandväggen en inkommande WMI-begäran och följande fel meddelande visas:</span><span class="sxs-lookup"><span data-stu-id="d69c8-181">In its default configuration, Windows Firewall rejects an incoming WMI request, and you receive the following error message:</span></span>

```
Remote server machine does not exist or is unavailable
```

## <a name="see-also"></a><span data-ttu-id="d69c8-182">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="d69c8-182">SEE ALSO</span></span>

[<span data-ttu-id="d69c8-183">Om WMI</span><span class="sxs-lookup"><span data-stu-id="d69c8-183">About WMI</span></span>](/windows/win32/wmisdk/about-wmi)

[<span data-ttu-id="d69c8-184">WMI-felsökning</span><span class="sxs-lookup"><span data-stu-id="d69c8-184">WMI Troubleshooting</span></span>](/windows/win32/wmisdk/wmi-troubleshooting)

[<span data-ttu-id="d69c8-185">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="d69c8-185">Get-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[<span data-ttu-id="d69c8-186">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="d69c8-186">Invoke-WmiMethod</span></span>](xref:Microsoft.PowerShell.Management.Invoke-WmiMethod)

[<span data-ttu-id="d69c8-187">Registrera – WmiEvent</span><span class="sxs-lookup"><span data-stu-id="d69c8-187">Register-WmiEvent</span></span>](xref:Microsoft.PowerShell.Management.Register-WmiEvent)

[<span data-ttu-id="d69c8-188">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="d69c8-188">Remove-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Remove-WmiObject)

[<span data-ttu-id="d69c8-189">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="d69c8-189">Set-WmiInstance</span></span>](xref:Microsoft.PowerShell.Management.Set-WmiInstance)
