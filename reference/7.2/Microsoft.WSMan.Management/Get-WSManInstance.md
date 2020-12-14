---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManInstance
ms.openlocfilehash: 00680a466c9cc9dd719fbce3d66f4eb10ec47860
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708326"
---
# <span data-ttu-id="22f0d-102">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="22f0d-102">Get-WSManInstance</span></span>

## <span data-ttu-id="22f0d-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="22f0d-103">SYNOPSIS</span></span>
<span data-ttu-id="22f0d-104">Visar hanterings information för en resurs instans som anges av en resurs-URI.</span><span class="sxs-lookup"><span data-stu-id="22f0d-104">Displays management information for a resource instance specified by a Resource URI.</span></span>

## <span data-ttu-id="22f0d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="22f0d-105">SYNTAX</span></span>

### <span data-ttu-id="22f0d-106">GetInstance (standard)</span><span class="sxs-lookup"><span data-stu-id="22f0d-106">GetInstance (Default)</span></span>

```
Get-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-ConnectionURI <Uri>] [-Dialect <Uri>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet <Hashtable>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="22f0d-107">Räkna upp</span><span class="sxs-lookup"><span data-stu-id="22f0d-107">Enumerate</span></span>

```
Get-WSManInstance [-ApplicationName <String>] [-BasePropertiesOnly] [-ComputerName <String>]
 [-ConnectionURI <Uri>] [-Dialect <Uri>] [-Enumerate] [-Filter <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-Associations] [-ResourceURI] <Uri> [-ReturnType <String>] [-SessionOption <SessionOption>]
 [-Shallow] [-UseSSL] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="22f0d-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="22f0d-108">DESCRIPTION</span></span>
<span data-ttu-id="22f0d-109">Cmdlet: en **Get-WSManInstance** hämtar en instans av en hanterings resurs som anges av en resurs Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="22f0d-109">The **Get-WSManInstance** cmdlet retrieves an instance of a management resource that is specified by a resource Uniform Resource Identifier (URI).</span></span>
<span data-ttu-id="22f0d-110">Den information som hämtas kan vara en komplex XML-information, som är ett objekt eller ett enkelt värde.</span><span class="sxs-lookup"><span data-stu-id="22f0d-110">The information that is retrieved can be a complex XML information set, which is an object, or a simple value.</span></span>
<span data-ttu-id="22f0d-111">Denna cmdlet motsvarar kommandot **Get** (WS-Management) för hantering av webb tjänster.</span><span class="sxs-lookup"><span data-stu-id="22f0d-111">This cmdlet is the equivalent to the standard Web Services for Management (WS-Management) **Get** command.</span></span>

<span data-ttu-id="22f0d-112">Denna cmdlet använder WS-Management Connection/transport-lagret för att hämta information.</span><span class="sxs-lookup"><span data-stu-id="22f0d-112">This cmdlet uses the WS-Management connection/transport layer to retrieve information.</span></span>

## <span data-ttu-id="22f0d-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="22f0d-113">EXAMPLES</span></span>

### <span data-ttu-id="22f0d-114">Exempel 1: Hämta all information från WMI</span><span class="sxs-lookup"><span data-stu-id="22f0d-114">Example 1: Get all information from WMI</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI wmicimv2/win32_service -SelectorSet @{name="winrm"} -ComputerName "Server01"
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : true
Caption                 : Windows Remote Management (WS-Management)
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Windows Remote Management (WinRM) service implements the WS-Management protocol for remote
management. WS-Management is a standard web services protocol used for remote software and
hardware management. The WinRM service listens on the network for WS-Management requests
and processes them. The WinRM Service needs to be configured with a listener using the
winrm.cmd command line tool or through Group Policy in order for it to listen over the
network. The WinRM service provides access to WMI data and enables event collection. Event
collection and subscription to events require that the service is running. WinRM messages
use HTTP and HTTPS as transports. The WinRM service does not depend on IIS but is
preconfigured to share a port with IIS on the same computer.  The WinRM service reserves the
/wsman URL prefix. To prevent conflicts with IIS, administrators should ensure that any
websites hosted on IIS do not use the /wsman URL prefix.
DesktopInteract         : false
DisplayName             : Windows Remote Management (WS-Management)
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : winrm
PathName                : C:\Windows\System32\svchost.exe -k NetworkService
ProcessId               : 948
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : true
StartMode               : Auto
StartName               : NT AUTHORITY\NetworkService
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
WaitHint                : 0
```

<span data-ttu-id="22f0d-115">Det här kommandot returnerar all information som Windows Management Instrumentation (WMI) visar om **WinRM** -tjänsten på den fjärranslutna Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="22f0d-115">This command returns all of the information that Windows Management Instrumentation (WMI) exposes about the **WinRM** service on the remote server01 computer.</span></span>

### <span data-ttu-id="22f0d-116">Exempel 2: Hämta status för Spooler-tjänsten</span><span class="sxs-lookup"><span data-stu-id="22f0d-116">Example 2: Get the status of the Spooler service</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI wmicimv2/win32_service -SelectorSet @{name="spooler"} -Fragment Status -ComputerName "Server01"
XmlFragment=OK
```

<span data-ttu-id="22f0d-117">Det här kommandot returnerar bara statusen för **Spooler** -tjänsten på den fjärranslutna Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="22f0d-117">This command returns only the status of the **Spooler** service on the remote server01 computer.</span></span>

### <span data-ttu-id="22f0d-118">Exempel 3: Hämta slut punkts referenser för alla tjänster</span><span class="sxs-lookup"><span data-stu-id="22f0d-118">Example 3: Get endpoint references for all services</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -ResourceURI wmicimv2/win32_service -ReturnType EPR
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Visual Studio 2008 Remote Debugger
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Allows members of the Administrators group to remotely debug server applications using Visual
Studio 2008. Use the Visual Studio 2008 Remote Debugging Configuration Wizard to enable this
service.
DesktopInteract         : false
DisplayName             : Visual Studio 2008 Remote Debugger
ErrorControl            : Ignore
ExitCode                : 1077
InstallDate             : InstallDate
Name                    : msvsmon90
PathName                : "C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe" /service msvsmon90
ProcessId               : 0
ServiceSpecificExitCode : 0
ServiceType             : Own Process
Started                 : false
StartMode               : Disabled
StartName               : LocalSystem
State                   : Stopped
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : COMPUTER01
TagId                   : 0
WaitHint                : 0
...
```

<span data-ttu-id="22f0d-119">Det här kommandot returnerar slut punkts referenser som motsvarar alla tjänster på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="22f0d-119">This command returns endpoint references that correspond to all the services on the local computer.</span></span>

### <span data-ttu-id="22f0d-120">Exempel 4: Hämta tjänster som uppfyller angivna villkor</span><span class="sxs-lookup"><span data-stu-id="22f0d-120">Example 4: Get services that meet specified criteria</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -ResourceURI wmicimv2/* -Filter "select * from win32_service where StartMode = 'Auto' and State = 'Stopped'" -ComputerName "Server01"
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Windows Media Center Service Launcher
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Starts Windows Media Center Scheduler and Windows Media Center Receiver services
at startup if TV is enabled within Windows Media Center.
DesktopInteract         : false
DisplayName             : Windows Media Center Service Launcher
ErrorControl            : Ignore
ExitCode                : 0
InstallDate             : InstallDate
Name                    : ehstart
PathName                : C:\Windows\system32\svchost.exe -k LocalServiceNoNetwork
ProcessId               : 0
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : false
StartMode               : Auto
StartName               : NT AUTHORITY\LocalService
State                   : Stopped
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : Server01
TagId                   : 0
WaitHint                : 0
...
```

<span data-ttu-id="22f0d-121">Detta kommando visar alla tjänster som uppfyller följande kriterier på den fjärranslutna Server01-datorn:</span><span class="sxs-lookup"><span data-stu-id="22f0d-121">This command lists all of the services that meet the following criteria on the remote Server01 computer:</span></span>

- <span data-ttu-id="22f0d-122">Start typen för tjänsten är automatisk.</span><span class="sxs-lookup"><span data-stu-id="22f0d-122">The startup type of the service is Automatic.</span></span>
- <span data-ttu-id="22f0d-123">Tjänsten har stoppats.</span><span class="sxs-lookup"><span data-stu-id="22f0d-123">The service is stopped.</span></span>

### <span data-ttu-id="22f0d-124">Exempel 5: Hämta Listener-konfiguration som matchar villkor på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="22f0d-124">Example 5: Get listener configuration that matches criteria on the local computer</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{Address="*";Transport="http"}
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 80
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {100.0.0.1, 123.123.123.123, ::1, 2001:4898:0:fff:0:5efe:123.123.123.123...}
```

<span data-ttu-id="22f0d-125">Det här kommandot visar WS-Management lyssnar konfigurationen på den lokala datorn för den lyssnare som matchar kriterierna i Selector-uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="22f0d-125">This command lists the WS-Management listener configuration on the local computer for the listener that matches the criteria in the selector set.</span></span>

### <span data-ttu-id="22f0d-126">Exempel 6: Hämta Listener-konfiguration som matchar villkor på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="22f0d-126">Example 6: Get listener configuration that matches criteria on a remote computer</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{Address="*";Transport="http"} -ComputerName "Server01"
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 80
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {100.0.0.1, 123.123.123.124, ::1, 2001:4898:0:fff:0:5efe:123.123.123.124...}
```

<span data-ttu-id="22f0d-127">Det här kommandot visar WS-Management lyssnar konfigurationen på den fjärranslutna Server01 datorn för den lyssnare som matchar kriterierna i Selector-uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="22f0d-127">This command lists the WS-Management listener configuration on the remote server01 computer for the listener that matches the criteria in the selector set.</span></span>

### <span data-ttu-id="22f0d-128">Exempel 7: Hämta associerade instanser relaterade till en angiven instans</span><span class="sxs-lookup"><span data-stu-id="22f0d-128">Example 7: Get associated instances related to a specified instance</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -Dialect Association -Filter "{Object=win32_service?name=winrm}" -ResourceURI wmicimv2/*
xsi                       : http://www.w3.org/2001/XMLSchema-instance
p                         : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_ComputerSystem
cim                       : http://schemas.dmtf.org/wbem/wscim/1/common
type                      : p:Win32_ComputerSystem_Type
lang                      : en-US
AdminPasswordStatus       : 1
AutomaticManagedPagefile  : true
AutomaticResetBootOption  : true
AutomaticResetCapability  : true
BootOptionOnLimit         : BootOptionOnLimit
BootOptionOnWatchDog      : BootOptionOnWatchDog
BootROMSupported          : true
BootupState               : Normal boot
Caption                   : SERVER01
ChassisBootupState        : 3
CreationClassName         : Win32_ComputerSystem
CurrentTimeZone           : -480
DaylightInEffect          : false
Description               : AT/AT COMPATIBLE
DNSHostName               : server01
Domain                    : site01.corp.fabrikam.com
DomainRole                : 1
EnableDaylightSavingsTime : true
FrontPanelResetStatus     : 2
InfraredSupported         : false
InstallDate               : InstallDate
KeyboardPasswordStatus    : 2
LastLoadInfo              : LastLoadInfo
Manufacturer              : Dell Inc.
Model                     : OptiPlex 745
Name                      : SERVER01
NameFormat                : NameFormat
NetworkServerModeEnabled  : true
NumberOfLogicalProcessors : 2
NumberOfProcessors        : 1
OEMStringArray            : www.dell.com
PartOfDomain              : true
PauseAfterReset           : -1
PCSystemType              : 5
PowerManagementSupported  : PowerManagementSupported
PowerOnPasswordStatus     : 1
PowerState                : 0
PowerSupplyState          : 3
PrimaryOwnerContact       : PrimaryOwnerContact
PrimaryOwnerName          : testuser01
ResetCapability           : 1
ResetCount                : -1
ResetLimit                : -1
Roles                     : {LM_Workstation, LM_Server, SQLServer, NT}
Status                    : OK
SystemStartupDelay        : SystemStartupDelay
SystemStartupSetting      : SystemStartupSetting
SystemType                : X86-based PC
ThermalState              : 3
TotalPhysicalMemory       : 3217760256
UserName                  : FABRIKAM\testuser01
WakeUpType                : 6
Workgroup                 : Workgroup
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Remote Procedure Call (RPC)
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Serves as the endpoint mapper and COM Service Control Manager. If this service is stopped
or disabled, programs using COM or Remote Procedure Call (RPC) services will not function
properly.
DesktopInteract         : false
DisplayName             : Remote Procedure Call (RPC)
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : RpcSs
PathName                : C:\Windows\system32\svchost.exe -k rpcss
ProcessId               : 1100
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : true
StartMode               : Auto
StartName               : NT AUTHORITY\NetworkService
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
WaitHint                : 0

xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_SystemDriver
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_SystemDriver_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : true
Caption                 : HTTP
CreationClassName       : Win32_SystemDriver
Description             : HTTP
DesktopInteract         : false
DisplayName             : HTTP
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : HTTP
PathName                : C:\Windows\system32\drivers\HTTP.sys
ServiceSpecificExitCode : 0
ServiceType             : Kernel Driver
Started                 : true
StartMode               : Manual
StartName               :
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
```

<span data-ttu-id="22f0d-129">Det här kommandot hämtar de associerade instanserna som är relaterade till den angivna instansen (WinRM).</span><span class="sxs-lookup"><span data-stu-id="22f0d-129">This command gets the associated instances that are related to the specified instance (winrm).</span></span>

<span data-ttu-id="22f0d-130">Du måste omgärda filtret inom citat tecken, som du ser i exemplet.</span><span class="sxs-lookup"><span data-stu-id="22f0d-130">You must enclose the filter in quotation marks, as shown in the example.</span></span>

### <span data-ttu-id="22f0d-131">Exempel 8: Hämta associerings instanser relaterade till en angiven instans</span><span class="sxs-lookup"><span data-stu-id="22f0d-131">Example 8: Get association instances related to a specified instance</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -Dialect Association -Associations -Filter "{Object=win32_service?name=winrm}" -ResourceURI wmicimv2/*
```

<span data-ttu-id="22f0d-132">Detta kommando hämtar associerings instanser som är relaterade till den angivna instansen (WinRM).</span><span class="sxs-lookup"><span data-stu-id="22f0d-132">This command gets association instances that are related to the specified instance (winrm).</span></span>
<span data-ttu-id="22f0d-133">Eftersom *dialekt* -värdet är Association och parametern *Associations* används returnerar det här kommandot associerings instanser, inte associerade instanser.</span><span class="sxs-lookup"><span data-stu-id="22f0d-133">Because the *Dialect* value is association and the *Associations* parameter is used, this command returns association instances, not associated instances.</span></span>

<span data-ttu-id="22f0d-134">Du måste omgärda filtret inom citat tecken, som du ser i exemplet.</span><span class="sxs-lookup"><span data-stu-id="22f0d-134">You must enclose the filter in quotation marks, as shown in the example.</span></span>

## <span data-ttu-id="22f0d-135">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="22f0d-135">PARAMETERS</span></span>

### <span data-ttu-id="22f0d-136">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="22f0d-136">-ApplicationName</span></span>
<span data-ttu-id="22f0d-137">Anger program namnet i anslutningen.</span><span class="sxs-lookup"><span data-stu-id="22f0d-137">Specifies the application name in the connection.</span></span>
<span data-ttu-id="22f0d-138">Standardvärdet för parametern *ApplicationName* är WSMan.</span><span class="sxs-lookup"><span data-stu-id="22f0d-138">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="22f0d-139">Den fullständiga identifieraren för Fjärrslutpunkten har följande format:</span><span class="sxs-lookup"><span data-stu-id="22f0d-139">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="22f0d-140">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="22f0d-140">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="22f0d-141">Exempel: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="22f0d-141">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="22f0d-142">Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="22f0d-142">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="22f0d-143">Den här standardinställningen för WSMAN är lämplig för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="22f0d-143">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="22f0d-144">Den här parametern är avsedd att användas om många datorer upprättar fjärr anslutningar till en dator som kör PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22f0d-144">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="22f0d-145">I det här fallet är IIS värd för WS-Management effektivitet.</span><span class="sxs-lookup"><span data-stu-id="22f0d-145">In this case, IIS hosts WS-Management for efficiency.</span></span>

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

### <span data-ttu-id="22f0d-146">-Associationer</span><span class="sxs-lookup"><span data-stu-id="22f0d-146">-Associations</span></span>
<span data-ttu-id="22f0d-147">Anger att denna cmdlet hämtar Associations instanser, inte associerade instanser.</span><span class="sxs-lookup"><span data-stu-id="22f0d-147">Indicates that this cmdlet gets association instances, not associated instances.</span></span>
<span data-ttu-id="22f0d-148">Du kan bara använda den här parametern när *Dialect* -parametern har ett värde för Association.</span><span class="sxs-lookup"><span data-stu-id="22f0d-148">You can use this parameter only when the *Dialect* parameter has a value of Association.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-149">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="22f0d-149">-Authentication</span></span>
<span data-ttu-id="22f0d-150">Anger vilken autentiseringsmekanism som ska användas på servern.</span><span class="sxs-lookup"><span data-stu-id="22f0d-150">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="22f0d-151">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="22f0d-151">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="22f0d-152">Frö.</span><span class="sxs-lookup"><span data-stu-id="22f0d-152">Basic.</span></span>
<span data-ttu-id="22f0d-153">Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.</span><span class="sxs-lookup"><span data-stu-id="22f0d-153">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="22f0d-154">Standard.</span><span class="sxs-lookup"><span data-stu-id="22f0d-154">Default.</span></span>
<span data-ttu-id="22f0d-155">Använd autentiseringsmetoden som implementeras av WS-Management-protokollet.</span><span class="sxs-lookup"><span data-stu-id="22f0d-155">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="22f0d-156">Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="22f0d-156">This is the default.</span></span>
- <span data-ttu-id="22f0d-157">Nedbrytning.</span><span class="sxs-lookup"><span data-stu-id="22f0d-157">Digest.</span></span>
<span data-ttu-id="22f0d-158">Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="22f0d-158">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="22f0d-159">Paket.</span><span class="sxs-lookup"><span data-stu-id="22f0d-159">Kerberos.</span></span>
<span data-ttu-id="22f0d-160">Klient datorn och servern autentiseras ömsesidigt med hjälp av Kerberos-certifikat.</span><span class="sxs-lookup"><span data-stu-id="22f0d-160">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="22f0d-161">Fram.</span><span class="sxs-lookup"><span data-stu-id="22f0d-161">Negotiate.</span></span>
<span data-ttu-id="22f0d-162">Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="22f0d-162">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="22f0d-163">Detta parameter värde kan till exempel användas för förhandling för att avgöra om Kerberos-protokollet eller NTLM används.</span><span class="sxs-lookup"><span data-stu-id="22f0d-163">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="22f0d-164">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="22f0d-164">CredSSP.</span></span>
<span data-ttu-id="22f0d-165">Använd CredSSP-autentisering (Credential Security Support Provider), vilket gör att användaren kan delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="22f0d-165">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="22f0d-166">Det här alternativet är utformat för kommandon som körs på en fjärrdator men samlar in data från eller kör ytterligare kommandon på andra fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="22f0d-166">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="22f0d-167">Varning! CredSSP delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="22f0d-167">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="22f0d-168">Den här metoden ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="22f0d-168">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="22f0d-169">Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="22f0d-169">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-170">-BasePropertiesOnly</span><span class="sxs-lookup"><span data-stu-id="22f0d-170">-BasePropertiesOnly</span></span>
<span data-ttu-id="22f0d-171">Anger att denna cmdlet endast räknar upp de egenskaper som ingår i Bask Lassen som anges av parametern *ResourceURI* .</span><span class="sxs-lookup"><span data-stu-id="22f0d-171">Indicates that this cmdlet enumerates only the properties that are part of the base class that is specified by the *ResourceURI* parameter.</span></span>
<span data-ttu-id="22f0d-172">Den här parametern har ingen inverkan om en *ytlig* -parameter har angetts.</span><span class="sxs-lookup"><span data-stu-id="22f0d-172">This parameter has no effect if the *Shallow* parameter is specified.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases: UBPO, Base

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-173">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="22f0d-173">-CertificateThumbprint</span></span>
<span data-ttu-id="22f0d-174">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="22f0d-174">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="22f0d-175">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="22f0d-175">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="22f0d-176">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="22f0d-176">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="22f0d-177">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="22f0d-177">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="22f0d-178">Om du vill hämta ett tumavtryck för certifikatet använder du kommandot Get-Item eller Get-ChildItem i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="22f0d-178">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="22f0d-179">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="22f0d-179">-ComputerName</span></span>
<span data-ttu-id="22f0d-180">Anger den dator som hanterings åtgärden ska köras mot.</span><span class="sxs-lookup"><span data-stu-id="22f0d-180">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="22f0d-181">Värdet kan vara ett fullständigt kvalificerat domän namn, ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="22f0d-181">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="22f0d-182">Använd namnet på den lokala datorn, Använd localhost eller Använd en punkt (.) för att ange den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="22f0d-182">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="22f0d-183">Den lokala datorn är standard.</span><span class="sxs-lookup"><span data-stu-id="22f0d-183">The local computer is the default.</span></span>
<span data-ttu-id="22f0d-184">Om fjärrdatorn finns i en annan domän än användaren måste du använda ett fullständigt kvalificerat domän namn.</span><span class="sxs-lookup"><span data-stu-id="22f0d-184">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="22f0d-185">Du kan skicka ett värde för den här parametern till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="22f0d-185">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-186">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="22f0d-186">-ConnectionURI</span></span>
<span data-ttu-id="22f0d-187">Anger anslutnings slut punkten.</span><span class="sxs-lookup"><span data-stu-id="22f0d-187">Specifies the connection endpoint.</span></span>
<span data-ttu-id="22f0d-188">Formatet för den här strängen är följande:</span><span class="sxs-lookup"><span data-stu-id="22f0d-188">The format of this string is as follows:</span></span>

<span data-ttu-id="22f0d-189">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="22f0d-189">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="22f0d-190">Följande sträng är ett korrekt formaterat värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="22f0d-190">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="22f0d-191">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="22f0d-191">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-192">-Credential</span><span class="sxs-lookup"><span data-stu-id="22f0d-192">-Credential</span></span>
<span data-ttu-id="22f0d-193">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="22f0d-193">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="22f0d-194">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="22f0d-194">The default is the current user.</span></span>
<span data-ttu-id="22f0d-195">Ange ett användar namn, till exempel user01, Domain01\User01 eller User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="22f0d-195">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="22f0d-196">Eller ange ett **PSCredential** -objekt, till exempel ett som returneras av Get-Credential-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="22f0d-196">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="22f0d-197">När du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="22f0d-197">When you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-198">– Dialekt</span><span class="sxs-lookup"><span data-stu-id="22f0d-198">-Dialect</span></span>
<span data-ttu-id="22f0d-199">Anger dialekten som ska användas i filtrets predikat.</span><span class="sxs-lookup"><span data-stu-id="22f0d-199">Specifies the dialect to use in the filter predicate.</span></span>
<span data-ttu-id="22f0d-200">Detta kan vara vilken dialekt som helst som stöds av fjärrtjänsten.</span><span class="sxs-lookup"><span data-stu-id="22f0d-200">This can be any dialect that is supported by the remote service.</span></span>
<span data-ttu-id="22f0d-201">Följande alias kan användas för dialekt-URI: n:</span><span class="sxs-lookup"><span data-stu-id="22f0d-201">The following aliases can be used for the dialect URI:</span></span>

- <span data-ttu-id="22f0d-202">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span><span class="sxs-lookup"><span data-stu-id="22f0d-202">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span></span>
- <span data-ttu-id="22f0d-203">Select `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span><span class="sxs-lookup"><span data-stu-id="22f0d-203">Selector `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span></span>
- <span data-ttu-id="22f0d-204">Föreningar `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span><span class="sxs-lookup"><span data-stu-id="22f0d-204">Association `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-205">-Räkna upp</span><span class="sxs-lookup"><span data-stu-id="22f0d-205">-Enumerate</span></span>
<span data-ttu-id="22f0d-206">Anger att denna cmdlet returnerar alla instanser av en hanterings resurs.</span><span class="sxs-lookup"><span data-stu-id="22f0d-206">Indicates that this cmdlet returns all of the instances of a management resource.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-207">-Filter</span><span class="sxs-lookup"><span data-stu-id="22f0d-207">-Filter</span></span>
<span data-ttu-id="22f0d-208">Anger filter uttrycket för uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="22f0d-208">Specifies the filter expression for the enumeration.</span></span>
<span data-ttu-id="22f0d-209">Om du anger den här parametern måste du även ange *dialekt*.</span><span class="sxs-lookup"><span data-stu-id="22f0d-209">If you specify this parameter, you must also specify *Dialect*.</span></span>

<span data-ttu-id="22f0d-210">Giltiga värden för den här parametern är beroende av dialekten som anges i *dialekten*.</span><span class="sxs-lookup"><span data-stu-id="22f0d-210">The valid values of this parameter depend on the dialect that is specified in *Dialect*.</span></span>
<span data-ttu-id="22f0d-211">Om *dialekt* till exempel är WQL måste *filter* parametern innehålla en sträng och strängen måste innehålla en giltig WQL-fråga som följande fråga:</span><span class="sxs-lookup"><span data-stu-id="22f0d-211">For example, if *Dialect* is WQL, the *Filter* parameter must contain a string, and the string must contain a valid WQL query such as the following query:</span></span>

`"Select * from Win32_Service where State != Running"`

<span data-ttu-id="22f0d-212">Om *dialekten* är Association måste *filtret* innehålla en sträng och strängen måste innehålla ett giltigt filter, till exempel följande filter:</span><span class="sxs-lookup"><span data-stu-id="22f0d-212">If *Dialect* is Association, *Filter* must contain a string, and the string must contain a valid filter, such as the following filter:</span></span>

`-filter:Object=EPR\[;AssociationClassName=AssocClassName\]\[;ResultClassName=ClassName\]\[;Role=RefPropertyName\]\[;ResultRole=RefPropertyName\]}`

```yaml
Type: System.String
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-213">– Fragment</span><span class="sxs-lookup"><span data-stu-id="22f0d-213">-Fragment</span></span>
<span data-ttu-id="22f0d-214">Anger ett avsnitt inuti instansen som ska uppdateras eller hämtas för den angivna åtgärden.</span><span class="sxs-lookup"><span data-stu-id="22f0d-214">Specifies a section inside the instance that is to be updated or retrieved for the specified operation.</span></span>
<span data-ttu-id="22f0d-215">Om du till exempel vill hämta statusen för en Spooler-tjänst anger du följande:</span><span class="sxs-lookup"><span data-stu-id="22f0d-215">For example, to get the status of a spooler service, specify the following:</span></span>

`-Fragment Status`

```yaml
Type: System.String
Parameter Sets: GetInstance
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-216">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="22f0d-216">-OptionSet</span></span>
<span data-ttu-id="22f0d-217">Anger en uppsättning växlar till en tjänst för att ändra eller förfina begärans typ.</span><span class="sxs-lookup"><span data-stu-id="22f0d-217">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="22f0d-218">Dessa liknar växlar som används i kommando rads gränssnitt eftersom de är specifika för specifika tjänster.</span><span class="sxs-lookup"><span data-stu-id="22f0d-218">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="22f0d-219">Valfritt antal alternativ kan anges.</span><span class="sxs-lookup"><span data-stu-id="22f0d-219">Any number of options can be specified.</span></span>

<span data-ttu-id="22f0d-220">I följande exempel visas syntaxen som skickar värdena 1, 2 och 3 för parametrarna a, b och c:</span><span class="sxs-lookup"><span data-stu-id="22f0d-220">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: OS

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-221">-Port</span><span class="sxs-lookup"><span data-stu-id="22f0d-221">-Port</span></span>
<span data-ttu-id="22f0d-222">Anger vilken port som ska användas när klienten ansluter till WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="22f0d-222">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="22f0d-223">När transporten är HTTP är standard porten 80.</span><span class="sxs-lookup"><span data-stu-id="22f0d-223">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="22f0d-224">När transporten är HTTPS är standard porten 443.</span><span class="sxs-lookup"><span data-stu-id="22f0d-224">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="22f0d-225">När du använder HTTPS som transport måste värdet för parametern *computername* matcha serverns certifikats eget namn (CN).</span><span class="sxs-lookup"><span data-stu-id="22f0d-225">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="22f0d-226">Men om parametern *SkipCNCheck* anges som en del av parametern *SessionOption* , behöver inte Certifikatets gemensamma namn matcha serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="22f0d-226">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="22f0d-227">Parametern *SkipCNCheck* ska endast användas för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="22f0d-227">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="22f0d-228">– ResourceURI</span><span class="sxs-lookup"><span data-stu-id="22f0d-228">-ResourceURI</span></span>
<span data-ttu-id="22f0d-229">Anger URI för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="22f0d-229">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="22f0d-230">URI: n identifierar en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="22f0d-230">The URI identifies a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="22f0d-231">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="22f0d-231">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="22f0d-232">Exempel:</span><span class="sxs-lookup"><span data-stu-id="22f0d-232">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: RURI

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-233">-ReturnType</span><span class="sxs-lookup"><span data-stu-id="22f0d-233">-ReturnType</span></span>
<span data-ttu-id="22f0d-234">Anger vilken typ av data som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="22f0d-234">Specifies the type of data to be returned.</span></span>
<span data-ttu-id="22f0d-235">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="22f0d-235">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="22f0d-236">Objekt</span><span class="sxs-lookup"><span data-stu-id="22f0d-236">Object</span></span>
- <span data-ttu-id="22f0d-237">EPR</span><span class="sxs-lookup"><span data-stu-id="22f0d-237">EPR</span></span>
- <span data-ttu-id="22f0d-238">ObjectAndEPR</span><span class="sxs-lookup"><span data-stu-id="22f0d-238">ObjectAndEPR</span></span>

<span data-ttu-id="22f0d-239">Standardvärdet är Object.</span><span class="sxs-lookup"><span data-stu-id="22f0d-239">The default value is Object.</span></span>

<span data-ttu-id="22f0d-240">Om du anger objekt eller inte anger den här parametern, returnerar denna cmdlet endast objekt.</span><span class="sxs-lookup"><span data-stu-id="22f0d-240">If you specify Object or do not specify this parameter, this cmdlet returns only objects.</span></span>
<span data-ttu-id="22f0d-241">Om du anger slut punkts referens (EPR) returnerar denna cmdlet endast slut punkts referenserna för objekten.</span><span class="sxs-lookup"><span data-stu-id="22f0d-241">If you specify endpoint reference (EPR) this cmdlet returns only the endpoint references of the objects.</span></span>
<span data-ttu-id="22f0d-242">Slut punkts referenser innehåller information om resurs-URI och väljare för instansen.</span><span class="sxs-lookup"><span data-stu-id="22f0d-242">Endpoint references contain information about the resource URI and the selectors for the instance.</span></span>
<span data-ttu-id="22f0d-243">Om du anger ObjectAndEPR returnerar denna cmdlet både objektet och dess associerade slut punkts referenser.</span><span class="sxs-lookup"><span data-stu-id="22f0d-243">If you specify ObjectAndEPR, this cmdlet returns both the object and its associated endpoint references.</span></span>

```yaml
Type: System.String
Parameter Sets: Enumerate
Aliases: RT
Accepted values: object, epr, objectandepr

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-244">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="22f0d-244">-SelectorSet</span></span>
<span data-ttu-id="22f0d-245">Anger en uppsättning värdepar som används för att välja specifika hanterings resurs instanser.</span><span class="sxs-lookup"><span data-stu-id="22f0d-245">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="22f0d-246">Parametern *SelectorSet* används när det finns mer än en instans av resursen.</span><span class="sxs-lookup"><span data-stu-id="22f0d-246">The *SelectorSet* parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="22f0d-247">Värdet för parametern *SelectorSet* måste vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="22f0d-247">The value of the *SelectorSet* parameter must be a hash table.</span></span>

<span data-ttu-id="22f0d-248">I följande exempel visas hur du anger ett värde för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="22f0d-248">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: GetInstance
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-249">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="22f0d-249">-SessionOption</span></span>
<span data-ttu-id="22f0d-250">Anger utökade alternativ för WS-Management-sessionen.</span><span class="sxs-lookup"><span data-stu-id="22f0d-250">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="22f0d-251">Ange ett **SessionOption** -objekt som du skapar med hjälp av New-WSManSessionOption-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="22f0d-251">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="22f0d-252">Om du vill ha mer information om vilka alternativ som är tillgängliga skriver du `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="22f0d-252">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: SO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-253">– Lite</span><span class="sxs-lookup"><span data-stu-id="22f0d-253">-Shallow</span></span>
<span data-ttu-id="22f0d-254">Anger att denna cmdlet bara returnerar instanser av Bask Lassen som anges i resurs-URI: n.</span><span class="sxs-lookup"><span data-stu-id="22f0d-254">Indicates that this cmdlet returns only instances of the base class that is specified in the resource URI.</span></span>
<span data-ttu-id="22f0d-255">Om du inte anger den här parametern returnerar denna cmdlet instanser av Bask Lassen som anges i URI: n och i alla dess härledda klasser.</span><span class="sxs-lookup"><span data-stu-id="22f0d-255">If you do not specify this parameter,, this cmdlet returns instances of the base class that is specified in the URI and in all its derived classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-256">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="22f0d-256">-UseSSL</span></span>
<span data-ttu-id="22f0d-257">Anger att Secure Sockets Layer-protokollet (SSL) används för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="22f0d-257">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="22f0d-258">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="22f0d-258">By default, SSL is not used.</span></span>

<span data-ttu-id="22f0d-259">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="22f0d-259">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="22f0d-260">Med parametern *UseSSL* kan du ange ytterligare skydd av https i stället för http.</span><span class="sxs-lookup"><span data-stu-id="22f0d-260">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="22f0d-261">Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="22f0d-261">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SSL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22f0d-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="22f0d-262">CommonParameters</span></span>
<span data-ttu-id="22f0d-263">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="22f0d-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="22f0d-264">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="22f0d-264">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="22f0d-265">INDATA</span><span class="sxs-lookup"><span data-stu-id="22f0d-265">INPUTS</span></span>

### <span data-ttu-id="22f0d-266">Inga</span><span class="sxs-lookup"><span data-stu-id="22f0d-266">None</span></span>
<span data-ttu-id="22f0d-267">Det här kommandot accepterar inte några indatatyper.</span><span class="sxs-lookup"><span data-stu-id="22f0d-267">This command does not accept any input.</span></span>

## <span data-ttu-id="22f0d-268">UTDATA</span><span class="sxs-lookup"><span data-stu-id="22f0d-268">OUTPUTS</span></span>

### <span data-ttu-id="22f0d-269">System.Xml.Xml-element</span><span class="sxs-lookup"><span data-stu-id="22f0d-269">System.Xml.XmlElement</span></span>
<span data-ttu-id="22f0d-270">Denna cmdlet genererar ett **XMLElement** -objekt.</span><span class="sxs-lookup"><span data-stu-id="22f0d-270">This cmdlet generates an **XMLElement** object.</span></span>

## <span data-ttu-id="22f0d-271">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="22f0d-271">NOTES</span></span>

## <span data-ttu-id="22f0d-272">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="22f0d-272">RELATED LINKS</span></span>

[<span data-ttu-id="22f0d-273">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="22f0d-273">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="22f0d-274">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="22f0d-274">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="22f0d-275">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="22f0d-275">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="22f0d-276">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="22f0d-276">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="22f0d-277">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="22f0d-277">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="22f0d-278">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="22f0d-278">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="22f0d-279">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="22f0d-279">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="22f0d-280">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="22f0d-280">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="22f0d-281">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="22f0d-281">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="22f0d-282">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="22f0d-282">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="22f0d-283">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="22f0d-283">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="22f0d-284">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="22f0d-284">Test-WSMan</span></span>](Test-WSMan.md)

