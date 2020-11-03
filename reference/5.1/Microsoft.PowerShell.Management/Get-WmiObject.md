---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WmiObject
ms.openlocfilehash: ed759ff3d0dd35cd55f9dac5a2d76e36eac4dc6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266103"
---
# <span data-ttu-id="252aa-103">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="252aa-103">Get-WmiObject</span></span>

## <span data-ttu-id="252aa-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="252aa-104">SYNOPSIS</span></span>
<span data-ttu-id="252aa-105">Hämtar instanser av Windows Management Instrumentation (WMI)-klasser eller information om tillgängliga klasser.</span><span class="sxs-lookup"><span data-stu-id="252aa-105">Gets instances of Windows Management Instrumentation (WMI) classes or information about the available classes.</span></span>

## <span data-ttu-id="252aa-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="252aa-106">SYNTAX</span></span>

### <span data-ttu-id="252aa-107">fråga (standard)</span><span class="sxs-lookup"><span data-stu-id="252aa-107">query (Default)</span></span>

```
Get-WmiObject [-Class] <String> [[-Property] <String[]>] [-Filter <String>] [-Amended] [-DirectRead]
 [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="252aa-108">lista</span><span class="sxs-lookup"><span data-stu-id="252aa-108">list</span></span>

```
Get-WmiObject [[-Class] <String>] [-Recurse] [-Amended] [-List] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="252aa-109">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="252aa-109">WQLQuery</span></span>

```
Get-WmiObject [-Amended] [-DirectRead] -Query <String> [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="252aa-110">klass</span><span class="sxs-lookup"><span data-stu-id="252aa-110">class</span></span>

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="252aa-111">path</span><span class="sxs-lookup"><span data-stu-id="252aa-111">path</span></span>

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

## <span data-ttu-id="252aa-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="252aa-112">DESCRIPTION</span></span>

<span data-ttu-id="252aa-113">Från och med PowerShell 3,0 har denna cmdlet ersatts av `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="252aa-113">Starting in PowerShell 3.0, this cmdlet has been superseded by `Get-CimInstance`.</span></span>

<span data-ttu-id="252aa-114">`Get-WmiObject`Cmdlet: en hämtar instanser av WMI-klasser eller information om tillgängliga WMI-klasser.</span><span class="sxs-lookup"><span data-stu-id="252aa-114">The `Get-WmiObject` cmdlet gets instances of WMI classes or information about the available WMI classes.</span></span> <span data-ttu-id="252aa-115">Om du vill ange en fjärrdator använder du parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="252aa-115">To specify a remote computer, use the **ComputerName** parameter.</span></span> <span data-ttu-id="252aa-116">Om **list** parametern anges, hämtar cmdleten information om de WMI-klasser som är tillgängliga i en angiven namnrymd.</span><span class="sxs-lookup"><span data-stu-id="252aa-116">If the **List** parameter is specified, the cmdlet gets information about the WMI classes that are available in a specified namespace.</span></span> <span data-ttu-id="252aa-117">Om **Frågeparametern** anges kör cmdleten en WQL-instruktion (WMI Query Language).</span><span class="sxs-lookup"><span data-stu-id="252aa-117">If the **Query** parameter is specified, the cmdlet runs a WMI query language (WQL) statement.</span></span>

<span data-ttu-id="252aa-118">`Get-WmiObject`Cmdlet: en använder inte Windows PowerShell-fjärrkommunikation för att utföra fjärråtgärder.</span><span class="sxs-lookup"><span data-stu-id="252aa-118">The `Get-WmiObject` cmdlet does not use Windows PowerShell remoting to perform remote operations.</span></span>
<span data-ttu-id="252aa-119">Du kan använda parametern **computername** för `Get-WmiObject` cmdleten även om datorn inte uppfyller kraven för Windows PowerShell-fjärrkommunikation eller inte har kon figurer ATS för fjärr kommunikation i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="252aa-119">You can use the **ComputerName** parameter of the `Get-WmiObject` cmdlet even if your computer does not meet the requirements for Windows PowerShell remoting or is not configured for remoting in Windows PowerShell.</span></span>

<span data-ttu-id="252aa-120">Från och med Windows PowerShell 3,0 har egenskapen **__Server** för det objekt som `Get-WmiObject` returnerar ett **PSComputerName** -alias.</span><span class="sxs-lookup"><span data-stu-id="252aa-120">Beginning in Windows PowerShell 3.0, the **__Server** property of the object that `Get-WmiObject` returns has a **PSComputerName** alias.</span></span> <span data-ttu-id="252aa-121">Detta gör det enklare att inkludera käll datorns namn i utdata och rapporter.</span><span class="sxs-lookup"><span data-stu-id="252aa-121">This makes it easier to include the source computer name in output and reports.</span></span>

## <span data-ttu-id="252aa-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="252aa-122">EXAMPLES</span></span>

### <span data-ttu-id="252aa-123">Exempel 1: Hämta processer på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="252aa-123">Example 1: Get processes on the local computer</span></span>

<span data-ttu-id="252aa-124">Det här exemplet hämtar processerna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="252aa-124">This example get the processes on the local computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Process
```

### <span data-ttu-id="252aa-125">Exempel 2: hämtar tjänster på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="252aa-125">Example 2: Gets services on a remote computer</span></span>

<span data-ttu-id="252aa-126">Det här exemplet hämtar tjänsterna på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="252aa-126">This example gets the services on a remote computer.</span></span> <span data-ttu-id="252aa-127">Parametern **computername** anger IP-adressen för en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="252aa-127">The **ComputerName** parameter specifies the IP address of a remote computer.</span></span> <span data-ttu-id="252aa-128">Som standard måste det aktuella användar kontot vara medlem i gruppen **Administratörer** på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="252aa-128">By default, the current user account must be a member of the **Administrators** group on the remote computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName 10.1.4.62
```

### <span data-ttu-id="252aa-129">Exempel 3: hämta WMI-klasser i roten eller standard namn området för den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="252aa-129">Example 3: Get WMI classes in the root or default namespace of the local computer</span></span>

<span data-ttu-id="252aa-130">Det här exemplet hämtar WMI-klasserna i roten eller standard namn området för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="252aa-130">This example gets the WMI classes in the root or default namespace of the local computer.</span></span>

```powershell
Get-WmiObject -Namespace "root/default" -List
```

### <span data-ttu-id="252aa-131">Exempel 4: Hämta en namngiven tjänst på flera datorer</span><span class="sxs-lookup"><span data-stu-id="252aa-131">Example 4: Get a named service on multiple computers</span></span>

<span data-ttu-id="252aa-132">Det här exemplet hämtar WinRM-tjänsten på de datorer som anges av värdet för parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="252aa-132">This example gets the WinRM service on the computers specified by the value of the **ComputerName** parameter.</span></span>

```powershell
Get-WmiObject -Query "select * from win32_service where name='WinRM'" -ComputerName Server01, Server02 |
  Format-List -Property PSComputerName, Name, ExitCode, Name, ProcessID, StartMode, State, Status
```

```Output
PSComputerName : SERVER01
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 844
StartMode      : Auto
State          : Running
Status         : OK

PSComputerName : SERVER02
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 932
StartMode      : Auto
State          : Running
Status         : OK
```

<span data-ttu-id="252aa-133">En pipeline-operator (|) skickar utdata till `Format-List` cmdleten, som lägger till egenskapen **PSComputerName** i standardutdata.</span><span class="sxs-lookup"><span data-stu-id="252aa-133">A pipeline operator (|) sends the output to the `Format-List` cmdlet, which adds the **PSComputerName** property to the default output.</span></span> <span data-ttu-id="252aa-134">**PSComputerName** är ett alias för egenskapen **__Server** för de objekt som `Get-WmiObject` returneras.</span><span class="sxs-lookup"><span data-stu-id="252aa-134">**PSComputerName** is an alias of the **__Server** property of the objects that `Get-WmiObject` returns.</span></span> <span data-ttu-id="252aa-135">Det här aliaset introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="252aa-135">This alias was introduced in PowerShell 3.0.</span></span>

### <span data-ttu-id="252aa-136">Exempel 5: stoppa en tjänst på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="252aa-136">Example 5: Stop a service on a remote computer</span></span>

<span data-ttu-id="252aa-137">I det här exemplet stoppas WinRM-tjänsten på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="252aa-137">This example stops the WinRM service on a remote computer.</span></span> <span data-ttu-id="252aa-138">`Get-WmiObject` hämtar instansen av WinRM-tjänsteobjektet på Server01.</span><span class="sxs-lookup"><span data-stu-id="252aa-138">`Get-WmiObject` gets the instance of the WinRM service object on Server01.</span></span> <span data-ttu-id="252aa-139">Sedan anropar den **Stop** -metoden i **Win32_Service** WMI-klassen för objektet.</span><span class="sxs-lookup"><span data-stu-id="252aa-139">Then, it invokes the **StopService** method of the **Win32_Service** WMI class on that object.</span></span>

```powershell
(Get-WmiObject -Class Win32_Service -Filter "name='WinRM'" -ComputerName Server01).StopService()
```

<span data-ttu-id="252aa-140">Detta motsvarar att använda `Stop-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="252aa-140">This is equivalent to using the `Stop-Service` cmdlet.</span></span>

### <span data-ttu-id="252aa-141">Exempel 6: Hämta BIOS på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="252aa-141">Example 6: Get the BIOS on the local computer</span></span>

<span data-ttu-id="252aa-142">Det här exemplet hämtar BIOS-information från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="252aa-142">This example gets the BIOS information from the local computer.</span></span> <span data-ttu-id="252aa-143">**Egenskaps** parametern för `Format-List` cmdleten används för att visa alla egenskaper för det returnerade objektet i en lista.</span><span class="sxs-lookup"><span data-stu-id="252aa-143">The **Property** parameter of the `Format-List` cmdlet is used to display all properties of the returned object in a list.</span></span> <span data-ttu-id="252aa-144">Som standard visas endast en delmängd av de egenskaper som definierats i `Types.ps1xml` konfigurations filen.</span><span class="sxs-lookup"><span data-stu-id="252aa-144">By default, only the subset of properties defined in the `Types.ps1xml` configuration file are displayed.</span></span>

```powershell
Get-WmiObject -Class Win32_Bios | Format-List -Property *
```

```Output
Status                : OK
Name                  : Phoenix ROM BIOS PLUS Version 1.10 A05
Caption               : Phoenix ROM BIOS PLUS Version 1.10 A05
SMBIOSPresent         : True
__GENUS               : 2
__CLASS               : Win32_BIOS
__SUPERCLASS          : CIM_BIOSElement
__DYNASTY             : CIM_ManagedSystemElement
__RELPATH             : Win32_BIOS.Name="Phoenix ROM BIOS PLUS Version 1.10
__PROPERTY_COUNT      : 27
__DERIVATION          : {CIM_BIOSElement, CIM_SoftwareElement, CIM_LogicalElement,
__SERVER              : Server01
__NAMESPACE           : root\cimv2
__PATH                : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
BiosCharacteristics   : {7, 9, 10, 11...}
BIOSVersion           : {DELL   - 15, Phoenix ROM BIOS PLUS Version 1.10 A05}
BuildNumber           :
CodeSet               :
CurrentLanguage       : en|US|iso8859-1
Description           : Phoenix ROM BIOS PLUS Version 1.10 A05
IdentificationCode    :
InstallableLanguages  : 1
InstallDate           :
LanguageEdition       :
ListOfLanguages       : {en|US|iso8859-1}
Manufacturer          : Dell Inc.
OtherTargetOS         :
PrimaryBIOS           : True
ReleaseDate           : 20101103000000.000000+000
SerialNumber          : 8VDM9P1
SMBIOSBIOSVersion     : A05
SMBIOSMajorVersion    : 2
SMBIOSMinorVersion    : 6
SoftwareElementID     : Phoenix ROM BIOS PLUS Version 1.10 A05
SoftwareElementState  : 3
TargetOperatingSystem : 0
Version               : DELL   - 15
Scope                 : System.Management.ManagementScope
Path                  : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
Options               : System.Management.ObjectGetOptions
ClassPath             : \\JUNE-PC\root\cimv2:Win32_BIOS
Properties            : {BiosCharacteristics, BIOSVersion, BuildNumber, Caption...}
SystemProperties      : {__GENUS, __CLASS, __SUPERCLASS, __DYNASTY...}
Qualifiers            : {dynamic, Locale, provider, UUID}
Site                  :
Container             :
```

### <span data-ttu-id="252aa-145">Exempel 7: Hämta tjänsterna på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="252aa-145">Example 7: Get the services on a remote computer</span></span>

<span data-ttu-id="252aa-146">I det här exemplet används parametern **Credential** för `Get-WmiObject` cmdleten för att hämta tjänsterna på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="252aa-146">This example uses the **Credential** parameter of the `Get-WmiObject` cmdlet to get the services on a remote computer.</span></span> <span data-ttu-id="252aa-147">Värdet för parametern **Credential** är ett användar konto namn.</span><span class="sxs-lookup"><span data-stu-id="252aa-147">The value of the **Credential** parameter is a user account name.</span></span> <span data-ttu-id="252aa-148">Användaren uppmanas att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="252aa-148">The user is prompted for a password.</span></span>

```powershell
Get-WmiObject Win32_Service -Credential FABRIKAM\administrator -ComputerName Fabrikam
```

> [!NOTE]
> <span data-ttu-id="252aa-149">Det går inte att använda autentiseringsuppgifter när den lokala datorn riktas mot.</span><span class="sxs-lookup"><span data-stu-id="252aa-149">Credentials cannot be used when targeting the local computer.</span></span>

## <span data-ttu-id="252aa-150">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="252aa-150">PARAMETERS</span></span>

### <span data-ttu-id="252aa-151">-Ändrad</span><span class="sxs-lookup"><span data-stu-id="252aa-151">-Amended</span></span>

<span data-ttu-id="252aa-152">Hämtar eller anger ett värde som anger om de objekt som returneras från WMI ska innehålla ändrad information.</span><span class="sxs-lookup"><span data-stu-id="252aa-152">Gets or sets a value that indicates whether the objects that are returned from WMI should contain amended information.</span></span> <span data-ttu-id="252aa-153">Normalt är den ändrade informationen lokaliserad information, till exempel beskrivningar av objekt och egenskaper, som är kopplade till WMI-objektet.</span><span class="sxs-lookup"><span data-stu-id="252aa-153">Typically, amended information is localizable information, such as object and property descriptions, that is attached to the WMI object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-154">– AsJob</span><span class="sxs-lookup"><span data-stu-id="252aa-154">-AsJob</span></span>

<span data-ttu-id="252aa-155">Kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="252aa-155">Runs the command as a background job.</span></span> <span data-ttu-id="252aa-156">Använd den här parametern för att köra kommandon som tar lång tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="252aa-156">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="252aa-157">När du använder parametern **AsJob** returnerar kommandot ett objekt som representerar bakgrunds jobbet och visar sedan kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="252aa-157">When you use the **AsJob** parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span> <span data-ttu-id="252aa-158">Du kan fortsätta att arbeta i sessionen medan jobbet är klart.</span><span class="sxs-lookup"><span data-stu-id="252aa-158">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="252aa-159">Om `Get-WmiObject` används på en fjärrdator skapas jobbet på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="252aa-159">If `Get-WmiObject` is used on a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="252aa-160">Använd cmdlet: arna som innehåller jobb-cmdletar för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="252aa-160">To manage the job, use the cmdlets that contain the Job cmdlets.</span></span> <span data-ttu-id="252aa-161">Använd cmdleten för att hämta jobb resultatet `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="252aa-161">To get the job results, use the `Receive-Job` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="252aa-162">Om du vill använda den här parametern med fjärrdatorer måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="252aa-162">To use this parameter with remote computers, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="252aa-163">Dessutom måste du starta Windows PowerShell med alternativet "kör som administratör" i Windows Vista och senare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="252aa-163">Additionally, you must start Windows PowerShell by using the "Run as administrator" option in Windows Vista and later versions of Windows.</span></span> <span data-ttu-id="252aa-164">Mer information finns i [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="252aa-164">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="252aa-165">Mer information om bakgrunds jobb i Windows PowerShell finns i [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) och [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="252aa-165">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-166">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="252aa-166">-Authentication</span></span>

<span data-ttu-id="252aa-167">Anger den autentiseringsnivå som ska användas med WMI-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="252aa-167">Specifies the authentication level to be used with the WMI connection.</span></span>
<span data-ttu-id="252aa-168">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="252aa-168">Valid values are:</span></span>

- <span data-ttu-id="252aa-169">-1: oförändrad</span><span class="sxs-lookup"><span data-stu-id="252aa-169">-1: Unchanged</span></span>
- <span data-ttu-id="252aa-170">0: standard</span><span class="sxs-lookup"><span data-stu-id="252aa-170">0: Default</span></span>
- <span data-ttu-id="252aa-171">1: ingen (ingen autentisering utförs)</span><span class="sxs-lookup"><span data-stu-id="252aa-171">1: None (No authentication in performed.)</span></span>
- <span data-ttu-id="252aa-172">2: Anslut (autentisering utförs endast när klienten upprättar en relation med programmet.)</span><span class="sxs-lookup"><span data-stu-id="252aa-172">2: Connect (Authentication is performed only when the client establishes a relationship with the application.)</span></span>
- <span data-ttu-id="252aa-173">3: anrop (autentisering utförs endast i början av varje anrop när programmet tar emot begäran.)</span><span class="sxs-lookup"><span data-stu-id="252aa-173">3: Call (Authentication is performed only at the beginning of each call when the application receives the request.)</span></span>
- <span data-ttu-id="252aa-174">4: paket (autentisering utförs på alla data som tas emot från klienten).</span><span class="sxs-lookup"><span data-stu-id="252aa-174">4: Packet (Authentication is performed on all the data that is received from the client.)</span></span>
- <span data-ttu-id="252aa-175">5: PacketIntegrity (alla data som överförs mellan klienten och programmet autentiseras och verifieras.)</span><span class="sxs-lookup"><span data-stu-id="252aa-175">5: PacketIntegrity (All the data that is transferred between the client and the application is authenticated and verified.)</span></span>
- <span data-ttu-id="252aa-176">6: PacketPrivacy (egenskaperna för de andra autentiseringsnivåer används och alla data krypteras.)</span><span class="sxs-lookup"><span data-stu-id="252aa-176">6: PacketPrivacy (The properties of the other authentication levels are used, and all the data is encrypted.)</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-177">-Authority</span><span class="sxs-lookup"><span data-stu-id="252aa-177">-Authority</span></span>

<span data-ttu-id="252aa-178">Anger den auktoritet som ska användas för att autentisera WMI-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="252aa-178">Specifies the authority to use to authenticate the WMI connection.</span></span> <span data-ttu-id="252aa-179">Du kan ange standard-NTLM eller Kerberos-autentisering.</span><span class="sxs-lookup"><span data-stu-id="252aa-179">You can specify standard NTLM or Kerberos authentication.</span></span> <span data-ttu-id="252aa-180">Om du vill använda NTLM anger du auktoritets inställningen till `ntlmdomain:<DomainName>` , där `<DomainName>` identifierar ett giltigt NTLM-domännamn.</span><span class="sxs-lookup"><span data-stu-id="252aa-180">To use NTLM, set the authority setting to `ntlmdomain:<DomainName>`, where `<DomainName>` identifies a valid NTLM domain name.</span></span> <span data-ttu-id="252aa-181">Om du vill använda Kerberos anger du `kerberos:<DomainName>\<ServerName>` .</span><span class="sxs-lookup"><span data-stu-id="252aa-181">To use Kerberos, specify `kerberos:<DomainName>\<ServerName>`.</span></span> <span data-ttu-id="252aa-182">Du kan inte inkludera auktoritets inställningen när du ansluter till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="252aa-182">You cannot include the authority setting when you connect to the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-183">– Klass</span><span class="sxs-lookup"><span data-stu-id="252aa-183">-Class</span></span>

<span data-ttu-id="252aa-184">Anger namnet på en WMI-klass.</span><span class="sxs-lookup"><span data-stu-id="252aa-184">Specifies the name of a WMI class.</span></span> <span data-ttu-id="252aa-185">När den här parametern används hämtar cmdleten instanser av WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="252aa-185">When this parameter is used, the cmdlet retrieves instances of the WMI class.</span></span>

```yaml
Type: System.String
Parameter Sets: query, list
Aliases: ClassName

Required: True (query), False (list)
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-186">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="252aa-186">-ComputerName</span></span>

<span data-ttu-id="252aa-187">Anger mål datorn för hanterings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="252aa-187">Specifies the target computer for the management operation.</span></span> <span data-ttu-id="252aa-188">Ange ett fullständigt kvalificerat domän namn (FQDN), ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="252aa-188">Enter a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="252aa-189">När fjärrdatorn finns i en annan domän än den lokala datorn krävs det fullständigt kvalificerade domän namnet.</span><span class="sxs-lookup"><span data-stu-id="252aa-189">When the remote computer is in a different domain than the local computer, the fully qualified domain name is required.</span></span>

<span data-ttu-id="252aa-190">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="252aa-190">The default is the local computer.</span></span> <span data-ttu-id="252aa-191">Om du vill ange den lokala datorn, till exempel i en lista över dator namn, använder du "localhost", namnet på den lokala datorn eller en punkt (.).</span><span class="sxs-lookup"><span data-stu-id="252aa-191">To specify the local computer, such as in a list of computer names, use "localhost", the local computer name, or a dot (.).</span></span>

<span data-ttu-id="252aa-192">Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation, som använder WS-Management.</span><span class="sxs-lookup"><span data-stu-id="252aa-192">This parameter does not rely on Windows PowerShell remoting, which uses WS-Management.</span></span> <span data-ttu-id="252aa-193">Du kan använda parametern **computername** för `Get-WmiObject` även om datorn inte är konfigurerad för att köra WS-Management fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="252aa-193">You can use the **ComputerName** parameter of `Get-WmiObject` even if your computer is not configured to run WS-Management remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-194">-Credential</span><span class="sxs-lookup"><span data-stu-id="252aa-194">-Credential</span></span>

<span data-ttu-id="252aa-195">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="252aa-195">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="252aa-196">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="252aa-196">The default is the current user.</span></span> <span data-ttu-id="252aa-197">Ange ett användar namn, till exempel "user01", "Domain01\User01" eller User@Contoso.com .</span><span class="sxs-lookup"><span data-stu-id="252aa-197">Type a user name, such as "User01", "Domain01\User01", or User@Contoso.com.</span></span> <span data-ttu-id="252aa-198">Eller ange ett **PSCredential** -objekt, till exempel ett objekt som returneras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="252aa-198">Or, enter a **PSCredential** object, such as an object that is returned by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="252aa-199">När du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="252aa-199">When you type a user name, you are prompted for a password.</span></span> <span data-ttu-id="252aa-200">Det går inte att använda autentiseringsuppgifter när den lokala datorn riktas mot.</span><span class="sxs-lookup"><span data-stu-id="252aa-200">Credentials cannot be used when targeting the local computer.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-201">-DirectRead</span><span class="sxs-lookup"><span data-stu-id="252aa-201">-DirectRead</span></span>

<span data-ttu-id="252aa-202">Anger om direkt åtkomst till WMI-providern begärs för den angivna klassen utan hänsyn till dess basklass eller dess härledda klasser.</span><span class="sxs-lookup"><span data-stu-id="252aa-202">Specifies whether direct access to the WMI provider is requested for the specified class without any regard to its base class or to its derived classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: query, WQLQuery
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-203">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="252aa-203">-EnableAllPrivileges</span></span>

<span data-ttu-id="252aa-204">Aktiverar alla behörigheter för den aktuella användaren innan kommandot gör WMI-anropet.</span><span class="sxs-lookup"><span data-stu-id="252aa-204">Enables all the privileges of the current user before the command makes the WMI call.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-205">-Filter</span><span class="sxs-lookup"><span data-stu-id="252aa-205">-Filter</span></span>

<span data-ttu-id="252aa-206">Anger en **WHERE** -sats som ska användas som ett filter.</span><span class="sxs-lookup"><span data-stu-id="252aa-206">Specifies a **Where** clause to use as a filter.</span></span> <span data-ttu-id="252aa-207">Använder syntaxen för WMI Query Language (WQL).</span><span class="sxs-lookup"><span data-stu-id="252aa-207">Uses the syntax of the WMI Query Language (WQL).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="252aa-208">Ta inte med nyckelordet **WHERE** i värdet för parametern.</span><span class="sxs-lookup"><span data-stu-id="252aa-208">Do not include the **Where** keyword in the value of the parameter.</span></span> <span data-ttu-id="252aa-209">Följande kommandon returnerar till exempel bara de logiska diskar som har en **DeviceID** av "c:" och tjänster som har namnet "WinRM" utan att använda nyckelordet **WHERE** .</span><span class="sxs-lookup"><span data-stu-id="252aa-209">For example, the following commands return only the logical disks that have a **DeviceID** of 'c:' and services that have the name 'WinRM' without using the **Where** keyword.</span></span>

`Get-WmiObject Win32_LogicalDisk -filter "DeviceID = 'c:' "`

`Get-WmiObject win32_service -filter "name='WinRM'"`

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-210">-Personifiering</span><span class="sxs-lookup"><span data-stu-id="252aa-210">-Impersonation</span></span>

<span data-ttu-id="252aa-211">Anger personifieringsnivån som ska användas.</span><span class="sxs-lookup"><span data-stu-id="252aa-211">Specifies the impersonation level to use.</span></span>

<span data-ttu-id="252aa-212">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="252aa-212">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="252aa-213">0: standard.</span><span class="sxs-lookup"><span data-stu-id="252aa-213">0: Default.</span></span> <span data-ttu-id="252aa-214">Läser det lokala registret för standard personifieringsnivån.</span><span class="sxs-lookup"><span data-stu-id="252aa-214">Reads the local registry for the default impersonation level.</span></span> <span data-ttu-id="252aa-215">Standardvärdet är inställt på att **Personifiera**.</span><span class="sxs-lookup"><span data-stu-id="252aa-215">The default is usually set to **Impersonate**.</span></span>
- <span data-ttu-id="252aa-216">1: Anonym.</span><span class="sxs-lookup"><span data-stu-id="252aa-216">1: Anonymous.</span></span> <span data-ttu-id="252aa-217">Döljer anroparens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="252aa-217">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="252aa-218">2: identifiera.</span><span class="sxs-lookup"><span data-stu-id="252aa-218">2: Identify.</span></span> <span data-ttu-id="252aa-219">Tillåter att objekt frågar efter anroparens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="252aa-219">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="252aa-220">3: personifiera.</span><span class="sxs-lookup"><span data-stu-id="252aa-220">3: Impersonate.</span></span> <span data-ttu-id="252aa-221">Tillåter att objekt använder autentiseringsuppgifterna för anroparen.</span><span class="sxs-lookup"><span data-stu-id="252aa-221">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="252aa-222">4: delegera.</span><span class="sxs-lookup"><span data-stu-id="252aa-222">4: Delegate.</span></span> <span data-ttu-id="252aa-223">Tillåter objekt att tillåta att andra objekt använder autentiseringsuppgifterna för anroparen.</span><span class="sxs-lookup"><span data-stu-id="252aa-223">Allows objects to permit other objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-224">– Lista</span><span class="sxs-lookup"><span data-stu-id="252aa-224">-List</span></span>

<span data-ttu-id="252aa-225">Hämtar namnen på WMI-klasserna i namn området för WMI-lagringsplatsen som anges av **namn områdes** parametern.</span><span class="sxs-lookup"><span data-stu-id="252aa-225">Gets the names of the WMI classes in the WMI repository namespace that is specified by the **Namespace** parameter.</span></span>

<span data-ttu-id="252aa-226">Om du anger **list** parametern, men inte **namn områdes** parametern, `Get-WmiObject` använder **Root\Cimv2** -namnområdet som standard.</span><span class="sxs-lookup"><span data-stu-id="252aa-226">If you specify the **List** parameter, but not the **Namespace** parameter, `Get-WmiObject` uses the **Root\Cimv2** namespace by default.</span></span> <span data-ttu-id="252aa-227">Denna cmdlet använder inte **standard namn områdets** register post i `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` register nyckeln för att fastställa standard namn området.</span><span class="sxs-lookup"><span data-stu-id="252aa-227">This cmdlet does not use the **Default Namespace** registry entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` registry key to determine the default namespace.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-228">-Locale</span><span class="sxs-lookup"><span data-stu-id="252aa-228">-Locale</span></span>

<span data-ttu-id="252aa-229">Anger det önskade språket för WMI-objekt.</span><span class="sxs-lookup"><span data-stu-id="252aa-229">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="252aa-230">Ange ett värde i MS_ \<LCID\> format.</span><span class="sxs-lookup"><span data-stu-id="252aa-230">Enter a value in MS_\<LCID\> format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-231">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="252aa-231">-Namespace</span></span>

<span data-ttu-id="252aa-232">När den används med **klassen Class** , anger **namespace** -parametern namn området för WMI-lagringsplatsen där den angivna WMI-klassen finns.</span><span class="sxs-lookup"><span data-stu-id="252aa-232">When used with the **Class** parameter, the **Namespace** parameter specifies the WMI repository namespace where the specified WMI class is located.</span></span> <span data-ttu-id="252aa-233">När det används med parametern **list** anger den det namn område som information om WMI-klass ska samlas in från.</span><span class="sxs-lookup"><span data-stu-id="252aa-233">When used with the **List** parameter, it specifies the namespace from which to gather WMI class information.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-234">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="252aa-234">-Property</span></span>

<span data-ttu-id="252aa-235">Anger egenskaper för WMI-klass som denna cmdlet hämtar information från.</span><span class="sxs-lookup"><span data-stu-id="252aa-235">Specifies the WMI class properties that this cmdlet gets information from.</span></span> <span data-ttu-id="252aa-236">Ange egenskaps namnen.</span><span class="sxs-lookup"><span data-stu-id="252aa-236">Enter the property names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: query
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-237">– Fråga</span><span class="sxs-lookup"><span data-stu-id="252aa-237">-Query</span></span>

<span data-ttu-id="252aa-238">Kör den angivna WQL-instruktionen (WMI Query Language).</span><span class="sxs-lookup"><span data-stu-id="252aa-238">Runs the specified WMI Query Language (WQL) statement.</span></span> <span data-ttu-id="252aa-239">Den här parametern stöder inte händelse frågor.</span><span class="sxs-lookup"><span data-stu-id="252aa-239">This parameter does not support event queries.</span></span>

```yaml
Type: System.String
Parameter Sets: WQLQuery
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-240">– Rekursivt</span><span class="sxs-lookup"><span data-stu-id="252aa-240">-Recurse</span></span>

<span data-ttu-id="252aa-241">Söker efter det aktuella namn området och alla andra namn områden för klass namnet som anges av **klass** parametern.</span><span class="sxs-lookup"><span data-stu-id="252aa-241">Searches the current namespace and all other namespaces for the class name that is specified by the **Class** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-242">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="252aa-242">-ThrottleLimit</span></span>

<span data-ttu-id="252aa-243">Anger det maximala antalet WMI-åtgärder som kan köras samtidigt.</span><span class="sxs-lookup"><span data-stu-id="252aa-243">Specifies the maximum number of WMI operations that can be executed simultaneously.</span></span> <span data-ttu-id="252aa-244">Den här parametern är endast giltig när parametern **AsJob** används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="252aa-244">This parameter is valid only when the **AsJob** parameter is used in the command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="252aa-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="252aa-245">CommonParameters</span></span>

<span data-ttu-id="252aa-246">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="252aa-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="252aa-247">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="252aa-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="252aa-248">INDATA</span><span class="sxs-lookup"><span data-stu-id="252aa-248">INPUTS</span></span>

### <span data-ttu-id="252aa-249">Inget</span><span class="sxs-lookup"><span data-stu-id="252aa-249">None</span></span>

<span data-ttu-id="252aa-250">Du kan inte skicka pipe-ininformation till `Get-WmiObject` .</span><span class="sxs-lookup"><span data-stu-id="252aa-250">You cannot pipe input to `Get-WmiObject`.</span></span>

## <span data-ttu-id="252aa-251">UTDATA</span><span class="sxs-lookup"><span data-stu-id="252aa-251">OUTPUTS</span></span>

### <span data-ttu-id="252aa-252">PSObject eller system. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="252aa-252">PSObject or System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="252aa-253">När du använder parametern **AsJob** , returnerar cmdleten ett Job-objekt.</span><span class="sxs-lookup"><span data-stu-id="252aa-253">When you use the **AsJob** parameter, the cmdlet returns a job object.</span></span> <span data-ttu-id="252aa-254">Annars är det objekt som `Get-WmiObject` returnerar beroende av värdet för **klass** parametern.</span><span class="sxs-lookup"><span data-stu-id="252aa-254">Otherwise, the object that `Get-WmiObject` returns depends on the value of the **Class** parameter.</span></span>

## <span data-ttu-id="252aa-255">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="252aa-255">NOTES</span></span>

<span data-ttu-id="252aa-256">För att få åtkomst till WMI-information på en fjärrdator måste cmdleten köras under ett konto som är medlem i den lokala gruppen Administratörer på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="252aa-256">To access WMI information on a remote computer, the cmdlet must run under an account that is a member of the local administrators group on the remote computer.</span></span> <span data-ttu-id="252aa-257">Eller så kan standard åtkomst kontrollen i WMI-namnrymden för fjärrlagringsplatsen ändras för att ge åtkomst behörighet till andra konton.</span><span class="sxs-lookup"><span data-stu-id="252aa-257">Or, the default access control on the WMI namespace of the remote repository can be changed to give access rights to other accounts.</span></span>

<span data-ttu-id="252aa-258">Endast några av egenskaperna för varje WMI-klass visas som standard.</span><span class="sxs-lookup"><span data-stu-id="252aa-258">Only some of the properties of each WMI class are displayed by default.</span></span> <span data-ttu-id="252aa-259">Uppsättningen egenskaper som visas för varje WMI-klass anges i Types.ps1XML-konfigurationsfilen.</span><span class="sxs-lookup"><span data-stu-id="252aa-259">The set of properties that is displayed for each WMI class is specified in the Types.ps1xml configuration file.</span></span> <span data-ttu-id="252aa-260">Använd cmdletarna eller för att hämta alla egenskaper för ett WMI-objekt `Get-Member` `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="252aa-260">To get all properties of a WMI object, use the `Get-Member` or `Format-List` cmdlets.</span></span>

## <span data-ttu-id="252aa-261">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="252aa-261">RELATED LINKS</span></span>

[<span data-ttu-id="252aa-262">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="252aa-262">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="252aa-263">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="252aa-263">Remove-WmiObject</span></span>](Remove-WmiObject.md)

[<span data-ttu-id="252aa-264">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="252aa-264">Set-WmiInstance</span></span>](Set-WmiInstance.md)

[<span data-ttu-id="252aa-265">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="252aa-265">Get-WSManInstance</span></span>](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[<span data-ttu-id="252aa-266">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="252aa-266">Invoke-WSManAction</span></span>](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[<span data-ttu-id="252aa-267">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="252aa-267">New-WSManInstance</span></span>](../Microsoft.WsMan.Management/New-WSManInstance.md)

[<span data-ttu-id="252aa-268">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="252aa-268">Remove-WSManInstance</span></span>](../Microsoft.WsMan.Management/Remove-WSManInstance.md)
