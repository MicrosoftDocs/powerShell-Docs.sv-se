---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-wmiinstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WmiInstance
ms.openlocfilehash: 03288a2ffbef416937b2c92a7d08a5aed49ffb43
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265376"
---
# <span data-ttu-id="543b3-103">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="543b3-103">Set-WmiInstance</span></span>

## <span data-ttu-id="543b3-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="543b3-104">SYNOPSIS</span></span>
<span data-ttu-id="543b3-105">Skapar eller uppdaterar en instans av en befintlig Windows Management Instrumentation (WMI)-klass.</span><span class="sxs-lookup"><span data-stu-id="543b3-105">Creates or updates an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>

## <span data-ttu-id="543b3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="543b3-106">SYNTAX</span></span>

### <span data-ttu-id="543b3-107">klass (standard)</span><span class="sxs-lookup"><span data-stu-id="543b3-107">class (Default)</span></span>

```
Set-WmiInstance [-Class] <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="543b3-108">objekt</span><span class="sxs-lookup"><span data-stu-id="543b3-108">object</span></span>

```
Set-WmiInstance -InputObject <ManagementObject> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="543b3-109">path</span><span class="sxs-lookup"><span data-stu-id="543b3-109">path</span></span>

```
Set-WmiInstance -Path <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="543b3-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="543b3-110">WQLQuery</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="543b3-111">DocumentDB</span><span class="sxs-lookup"><span data-stu-id="543b3-111">query</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="543b3-112">lista</span><span class="sxs-lookup"><span data-stu-id="543b3-112">list</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="543b3-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="543b3-113">DESCRIPTION</span></span>
<span data-ttu-id="543b3-114">`Set-WmiInstance`Cmdleten skapar eller uppdaterar en instans av en befintlig Windows Management Instrumentation (WMI)-klass.</span><span class="sxs-lookup"><span data-stu-id="543b3-114">The `Set-WmiInstance` cmdlet creates or updates an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>
<span data-ttu-id="543b3-115">Den skapade eller uppdaterade instansen skrivs till WMI-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="543b3-115">The created or updated instance is written to the WMI repository.</span></span>

<span data-ttu-id="543b3-116">Nya CIM-cmdletar, introducerade Windows PowerShell 3,0, utför samma uppgifter som WMI-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="543b3-116">New CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span>
<span data-ttu-id="543b3-117">CIM-cmdletar följer WS-Management (WSMan)-standarder och med Common Information Model (CIM)-standarden.</span><span class="sxs-lookup"><span data-stu-id="543b3-117">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard.</span></span>
<span data-ttu-id="543b3-118">Detta gör att cmdlets kan använda samma metoder för att hantera Windows-baserade datorer och de som kör andra operativ system.</span><span class="sxs-lookup"><span data-stu-id="543b3-118">this enables cmdlets to use the same techniques to manage Windows-based computers and those running other operating systems.</span></span>
<span data-ttu-id="543b3-119">I stället för att använda bör `Set-WmiInstance` du överväga att använda cmdletarna [set-CimInstance](/powershell/module/cimcmdlets/set-ciminstance) eller [New-CimInstance](/powershell/module/cimcmdlets/new-ciminstance) .</span><span class="sxs-lookup"><span data-stu-id="543b3-119">Instead of using `Set-WmiInstance`, consider using the [Set-CimInstance](/powershell/module/cimcmdlets/set-ciminstance) or [New-CimInstance](/powershell/module/cimcmdlets/new-ciminstance) cmdlets.</span></span>

## <span data-ttu-id="543b3-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="543b3-120">EXAMPLES</span></span>

### <span data-ttu-id="543b3-121">Exempel 1: ange nivån för WMI-loggning</span><span class="sxs-lookup"><span data-stu-id="543b3-121">Example 1: Set WMI logging level</span></span>

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2}
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
```

<span data-ttu-id="543b3-122">Det här kommandot anger WMI-loggnings nivån till 2.</span><span class="sxs-lookup"><span data-stu-id="543b3-122">This command sets the WMI logging level to 2.</span></span>
<span data-ttu-id="543b3-123">Kommandot skickar egenskapen som ska ställas in och värdet, som tillsammans betraktas som ett värde par, i argument parametern.</span><span class="sxs-lookup"><span data-stu-id="543b3-123">The command passes the property to be set and the value, together considered a value pair, in the argument parameter.</span></span>
<span data-ttu-id="543b3-124">Parametern använder en hash-tabell som definieras av konstruktionen @ {Property = Value}.</span><span class="sxs-lookup"><span data-stu-id="543b3-124">The parameter takes a hash table that is defined by the @{property = value} construction.</span></span>
<span data-ttu-id="543b3-125">Den klass information som returneras visar det nya värdet.</span><span class="sxs-lookup"><span data-stu-id="543b3-125">The class information that is returned reflects the new value.</span></span>

### <span data-ttu-id="543b3-126">Exempel 2: skapa en miljö variabel och dess värde</span><span class="sxs-lookup"><span data-stu-id="543b3-126">Example 2: Create an environment variable and its value</span></span>

```
PS C:\> Set-WmiInstance -Class win32_environment -Argument @{Name="testvar";VariableValue="testvalue";UserName="<SYSTEM>"}
__GENUS          : 2
__CLASS          : Win32_Environment
__SUPERCLASS     : CIM_SystemResource
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Environment.Name="testvar",UserName="<SYSTEM>"
__PROPERTY_COUNT : 8
__DERIVATION     : {CIM_SystemResource, CIM_LogicalElement, CIM_ManagedSystemElement}
__SERVER         : SYSTEM01
__NAMESPACE      : root\cimv2
__PATH           : \\SYSTEM01\root\cimv2:Win32_Environment.Name="testvar",UserName="<SYSTEM>"
Caption          : <SYSTEM>\testvar
Description      : <SYSTEM>\testvar
InstallDate      :
Name             : testvar
Status           : OK
SystemVariable   : True
UserName         : <SYSTEM>
VariableValue    : testvalue
```

<span data-ttu-id="543b3-127">Det här kommandot skapar testvar-miljövariabeln som har värdet TestValue.</span><span class="sxs-lookup"><span data-stu-id="543b3-127">This command creates the testvar environment variable that has the value testvalue.</span></span>
<span data-ttu-id="543b3-128">Det gör du genom att skapa en ny instans av klassen **Win32_Environment** WMI.</span><span class="sxs-lookup"><span data-stu-id="543b3-128">It does this by creating a new instance of the **Win32_Environment** WMI class.</span></span>
<span data-ttu-id="543b3-129">Den här åtgärden kräver lämpliga autentiseringsuppgifter och du kan behöva starta om Windows PowerShell för att se den nya miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="543b3-129">This operation requires appropriate credentials and that you may have to restart Windows PowerShell to see the new environment variable.</span></span>

### <span data-ttu-id="543b3-130">Exempel 3: ange nivån för WMI-loggning för flera fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="543b3-130">Example 3: Set WMI logging level for several remote computers</span></span>

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2} -Computername "system01", "system02", "system03"
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
...
```

<span data-ttu-id="543b3-131">Det här kommandot anger WMI-loggnings nivån till 2.</span><span class="sxs-lookup"><span data-stu-id="543b3-131">This command sets the WMI logging level to 2.</span></span>
<span data-ttu-id="543b3-132">Kommandot skickar egenskapen som ska ställas in och värdet, som tillsammans betraktas som ett värde par, i argument parametern.</span><span class="sxs-lookup"><span data-stu-id="543b3-132">The command passes the property to be set and the value, together considered a value pair, in the argument parameter.</span></span>
<span data-ttu-id="543b3-133">Parametern använder en hash-tabell som definieras av konstruktionen @ {Property = Value}.</span><span class="sxs-lookup"><span data-stu-id="543b3-133">The parameter takes a hash table that is defined by the @{property = value} construction.</span></span>
<span data-ttu-id="543b3-134">Den returnerade klass informationen visar det nya värdet.</span><span class="sxs-lookup"><span data-stu-id="543b3-134">The returned class information reflects the new value.</span></span>

## <span data-ttu-id="543b3-135">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="543b3-135">PARAMETERS</span></span>

### <span data-ttu-id="543b3-136">-Argument</span><span class="sxs-lookup"><span data-stu-id="543b3-136">-Arguments</span></span>
<span data-ttu-id="543b3-137">Anger namnet på den egenskap som ska ändras och det nya värdet för den egenskapen.</span><span class="sxs-lookup"><span data-stu-id="543b3-137">Specifies the name of the property to be changed and the new value for that property.</span></span>
<span data-ttu-id="543b3-138">Namnet och värdet måste vara ett namn-värde-par.</span><span class="sxs-lookup"><span data-stu-id="543b3-138">The name and value must be a name-value pair.</span></span>
<span data-ttu-id="543b3-139">Namn-värde-paret skickas till kommando raden som en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="543b3-139">The name-value pair is passed on the command line as a hash table.</span></span>
<span data-ttu-id="543b3-140">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="543b3-140">For example:</span></span>

`@{Setting1=1; Setting2=5; Setting3="test"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: class, object, path
Aliases: Args, Property

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-141">– AsJob</span><span class="sxs-lookup"><span data-stu-id="543b3-141">-AsJob</span></span>
<span data-ttu-id="543b3-142">Anger att den här cmdket körs som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="543b3-142">Indicates that this cmdket runs as a background job.</span></span>
<span data-ttu-id="543b3-143">Använd den här parametern för att köra kommandon som tar lång tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="543b3-143">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="543b3-144">När du anger parametern *AsJob* , returnerar kommandot ett objekt som representerar bakgrunds jobbet och visar sedan kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="543b3-144">When you specify the *AsJob* parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span>
<span data-ttu-id="543b3-145">Du kan fortsätta att arbeta i sessionen medan jobbet är klart.</span><span class="sxs-lookup"><span data-stu-id="543b3-145">You can continue to work in the session while the job finishes.</span></span>
<span data-ttu-id="543b3-146">Om **set-WmiInstance** används för en fjärrdator, skapas jobbet på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="543b3-146">If **Set-WmiInstance** is used for a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="543b3-147">Om du vill hantera jobbet använder du de cmdlet: ar som innehåller **jobbet** Substantiv ( **jobb** -cmdletarna).</span><span class="sxs-lookup"><span data-stu-id="543b3-147">To manage the job, use the cmdlets that contain the **Job** noun (the **Job** cmdlets).</span></span>
<span data-ttu-id="543b3-148">Använd Receive-Job-cmdleten för att hämta jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="543b3-148">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="543b3-149">Om du vill använda den här parametern tillsammans med fjärrdatorer måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="543b3-149">To use this parameter together with remote computers, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="543b3-150">Dessutom måste du starta Windows PowerShell med alternativet Kör som administratör i Windows Vista och senare versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="543b3-150">Additionally, you must start Windows PowerShell by using the Run as administrator option in Windows Vista and later versions of the Windows operating system.</span></span>
<span data-ttu-id="543b3-151">Mer information finns i about_Remote_Requirements.</span><span class="sxs-lookup"><span data-stu-id="543b3-151">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="543b3-152">Mer information om bakgrunds jobb i Windows PowerShell finns i about_Jobs och about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="543b3-152">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

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

### <span data-ttu-id="543b3-153">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="543b3-153">-Authentication</span></span>
<span data-ttu-id="543b3-154">Anger den autentiseringsnivå som måste användas med WMI-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="543b3-154">Specifies the authentication level that must be used with the WMI connection.</span></span>
<span data-ttu-id="543b3-155">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="543b3-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="543b3-156">-1: oförändrad.</span><span class="sxs-lookup"><span data-stu-id="543b3-156">-1: Unchanged.</span></span>
- <span data-ttu-id="543b3-157">0: standard.</span><span class="sxs-lookup"><span data-stu-id="543b3-157">0: Default.</span></span>
- <span data-ttu-id="543b3-158">1: ingen.</span><span class="sxs-lookup"><span data-stu-id="543b3-158">1: None.</span></span>
<span data-ttu-id="543b3-159">Ingen autentisering utförs.</span><span class="sxs-lookup"><span data-stu-id="543b3-159">No authentication in performed.</span></span>
- <span data-ttu-id="543b3-160">2: Anslut.</span><span class="sxs-lookup"><span data-stu-id="543b3-160">2: Connect.</span></span>
<span data-ttu-id="543b3-161">Autentisering utförs endast när klienten upprättar en relation med programmet.</span><span class="sxs-lookup"><span data-stu-id="543b3-161">Authentication is performed only when the client establishes a relationship with the application.</span></span>
- <span data-ttu-id="543b3-162">3: anropa.</span><span class="sxs-lookup"><span data-stu-id="543b3-162">3: Call.</span></span>
<span data-ttu-id="543b3-163">Autentisering utförs endast i början av varje anrop när programmet tar emot begäran.</span><span class="sxs-lookup"><span data-stu-id="543b3-163">Authentication is performed only at the start of each call when the application receives the request.</span></span>
- <span data-ttu-id="543b3-164">4: paket.</span><span class="sxs-lookup"><span data-stu-id="543b3-164">4: Packet.</span></span>
<span data-ttu-id="543b3-165">Autentisering utförs på alla data som tas emot från klienten.</span><span class="sxs-lookup"><span data-stu-id="543b3-165">Authentication is performed on all the data that is received from the client.</span></span>
- <span data-ttu-id="543b3-166">5: PacketIntegrity.</span><span class="sxs-lookup"><span data-stu-id="543b3-166">5: PacketIntegrity.</span></span>
<span data-ttu-id="543b3-167">Alla data som överförs mellan klienten och programmet autentiseras och verifieras.</span><span class="sxs-lookup"><span data-stu-id="543b3-167">All the data that is transferred between the client and the application is authenticated and verified.</span></span>
- <span data-ttu-id="543b3-168">6: PacketPrivacy.</span><span class="sxs-lookup"><span data-stu-id="543b3-168">6: PacketPrivacy.</span></span>
<span data-ttu-id="543b3-169">Egenskaperna för de andra autentiseringsnivåer används och alla data krypteras.</span><span class="sxs-lookup"><span data-stu-id="543b3-169">The properties of the other authentication levels are used, and all the data is encrypted.</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-170">-Authority</span><span class="sxs-lookup"><span data-stu-id="543b3-170">-Authority</span></span>
<span data-ttu-id="543b3-171">Anger den auktoritet som ska användas för att autentisera WMI-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="543b3-171">Specifies the authority to use to authenticate the WMI connection.</span></span>
<span data-ttu-id="543b3-172">Du kan ange standard-NTLM eller Kerberos-autentisering.</span><span class="sxs-lookup"><span data-stu-id="543b3-172">You can specify standard NTLM or Kerberos authentication.</span></span>
<span data-ttu-id="543b3-173">Om du vill använda NTLM ställer du in inställningen auktoritet på ntlmdomain: \<DomainName\> , där \<DomainName\> identifierar ett giltigt NTLM-domännamn.</span><span class="sxs-lookup"><span data-stu-id="543b3-173">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span>
<span data-ttu-id="543b3-174">Ange Kerberos om du vill använda Kerberos: \<DomainName\> \\ \<ServerName\> .</span><span class="sxs-lookup"><span data-stu-id="543b3-174">To use Kerberos, specify kerberos:\<DomainName\>\\\<ServerName\>.</span></span>
<span data-ttu-id="543b3-175">Du kan inte inkludera auktoritets inställningen när du ansluter till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="543b3-175">You cannot include the authority setting when you connect to the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-176">– Klass</span><span class="sxs-lookup"><span data-stu-id="543b3-176">-Class</span></span>
<span data-ttu-id="543b3-177">Anger namnet på en WMI-klass.</span><span class="sxs-lookup"><span data-stu-id="543b3-177">Specifies the name of a WMI class.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-178">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="543b3-178">-ComputerName</span></span>
<span data-ttu-id="543b3-179">Anger namnet på den dator där cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="543b3-179">Specifies the name of the computer on which this cmdlet runs.</span></span>
<span data-ttu-id="543b3-180">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="543b3-180">The default is the local computer.</span></span>

<span data-ttu-id="543b3-181">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera datorer.</span><span class="sxs-lookup"><span data-stu-id="543b3-181">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span>
<span data-ttu-id="543b3-182">Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.</span><span class="sxs-lookup"><span data-stu-id="543b3-182">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="543b3-183">Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="543b3-183">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="543b3-184">Du kan använda parametern *computername* även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="543b3-184">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-185">-Credential</span><span class="sxs-lookup"><span data-stu-id="543b3-185">-Credential</span></span>
<span data-ttu-id="543b3-186">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="543b3-186">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="543b3-187">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="543b3-187">The default is the current user.</span></span>

<span data-ttu-id="543b3-188">Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, till exempel ett som genereras av Get-Credential cmdlet.</span><span class="sxs-lookup"><span data-stu-id="543b3-188">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="543b3-189">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="543b3-189">If you type a user name, this cmdlet prompts for a password.</span></span>

<span data-ttu-id="543b3-190">Den här parametern stöds inte av någon provider som har installerats med en parameter som inte stöds av några leverantörer som installeras med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="543b3-190">This parameter is not supported by any providers installed with parameter is not supported by any providers installed with Windows PowerShell.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-191">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="543b3-191">-EnableAllPrivileges</span></span>
<span data-ttu-id="543b3-192">Anger att denna cmdlet aktiverar alla behörigheter för den aktuella användaren innan det kommando som gör WMI-anropet.</span><span class="sxs-lookup"><span data-stu-id="543b3-192">Indicates that this cmdlet enables all the permissions of the current user before the command it makes the WMI call.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-193">-Personifiering</span><span class="sxs-lookup"><span data-stu-id="543b3-193">-Impersonation</span></span>
<span data-ttu-id="543b3-194">Anger personifieringsnivån som ska användas.</span><span class="sxs-lookup"><span data-stu-id="543b3-194">Specifies the impersonation level to use.</span></span>
<span data-ttu-id="543b3-195">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="543b3-195">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="543b3-196">0: standard.</span><span class="sxs-lookup"><span data-stu-id="543b3-196">0: Default.</span></span>
<span data-ttu-id="543b3-197">Läser det lokala registret för standard personifieringsnivån, som vanligt vis anges till 3: personifiera.</span><span class="sxs-lookup"><span data-stu-id="543b3-197">Reads the local registry for the default impersonation level, which is usually set to 3: Impersonate.</span></span>
- <span data-ttu-id="543b3-198">1: Anonym.</span><span class="sxs-lookup"><span data-stu-id="543b3-198">1: Anonymous.</span></span>
<span data-ttu-id="543b3-199">Döljer anroparens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="543b3-199">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="543b3-200">2: identifiera.</span><span class="sxs-lookup"><span data-stu-id="543b3-200">2: Identify.</span></span>
<span data-ttu-id="543b3-201">Tillåter att objekt frågar efter anroparens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="543b3-201">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="543b3-202">3: personifiera.</span><span class="sxs-lookup"><span data-stu-id="543b3-202">3: Impersonate.</span></span>
<span data-ttu-id="543b3-203">Tillåter att objekt använder autentiseringsuppgifterna för anroparen.</span><span class="sxs-lookup"><span data-stu-id="543b3-203">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="543b3-204">4: delegera.</span><span class="sxs-lookup"><span data-stu-id="543b3-204">4: Delegate.</span></span>
<span data-ttu-id="543b3-205">Tillåter objekt att tillåta att andra objekt använder autentiseringsuppgifterna för anroparen.</span><span class="sxs-lookup"><span data-stu-id="543b3-205">Allows objects to permit other objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-206">– InputObject</span><span class="sxs-lookup"><span data-stu-id="543b3-206">-InputObject</span></span>
<span data-ttu-id="543b3-207">Anger ett **ManagementObject** -objekt som ska användas som indatamängd.</span><span class="sxs-lookup"><span data-stu-id="543b3-207">Specifies a **ManagementObject** object to use as input.</span></span>
<span data-ttu-id="543b3-208">När den här parametern används ignoreras alla andra parametrar, förutom *argument* parametern,.</span><span class="sxs-lookup"><span data-stu-id="543b3-208">When this parameter is used, all other parameters ,except the *Arguments* parameter, are ignored.</span></span>

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-209">-Locale</span><span class="sxs-lookup"><span data-stu-id="543b3-209">-Locale</span></span>
<span data-ttu-id="543b3-210">Anger det önskade språket för WMI-objekt.</span><span class="sxs-lookup"><span data-stu-id="543b3-210">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="543b3-211">Parametern *locale* anges i en matris i MS_ \<LCID\> formatet i den ordning som du föredrar.</span><span class="sxs-lookup"><span data-stu-id="543b3-211">The *Locale* parameter is specified in an array in the MS_\<LCID\> format in the preferred order.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-212">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="543b3-212">-Namespace</span></span>
<span data-ttu-id="543b3-213">Anger namn området för WMI-lagringsplatsen där den refererade WMI-klassen finns när den används med *klass* parametern.</span><span class="sxs-lookup"><span data-stu-id="543b3-213">Specifies the WMI repository namespace where the referenced WMI class is located when it is used with the *Class* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-214">-Path</span><span class="sxs-lookup"><span data-stu-id="543b3-214">-Path</span></span>
<span data-ttu-id="543b3-215">Anger en sökväg till WMI-objektet för den instans som du vill skapa eller uppdatera.</span><span class="sxs-lookup"><span data-stu-id="543b3-215">Specifies a WMI object path of the instance that you want to create or update.</span></span>

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-216">-PutType</span><span class="sxs-lookup"><span data-stu-id="543b3-216">-PutType</span></span>
<span data-ttu-id="543b3-217">Anger om WMI-instansen ska skapas eller uppdateras.</span><span class="sxs-lookup"><span data-stu-id="543b3-217">Indicates whether to create or update the WMI instance.</span></span>
<span data-ttu-id="543b3-218">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="543b3-218">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="543b3-219">UpdateOnly.</span><span class="sxs-lookup"><span data-stu-id="543b3-219">UpdateOnly.</span></span>
<span data-ttu-id="543b3-220">Uppdaterar en befintlig WMI-instans.</span><span class="sxs-lookup"><span data-stu-id="543b3-220">Updates an existing WMI instance.</span></span>
- <span data-ttu-id="543b3-221">CreateOnly.</span><span class="sxs-lookup"><span data-stu-id="543b3-221">CreateOnly.</span></span>
<span data-ttu-id="543b3-222">Skapar en ny WMI-instans.</span><span class="sxs-lookup"><span data-stu-id="543b3-222">Creates a new WMI instance.</span></span>
- <span data-ttu-id="543b3-223">UpdateOrCreate.</span><span class="sxs-lookup"><span data-stu-id="543b3-223">UpdateOrCreate.</span></span>
<span data-ttu-id="543b3-224">Uppdaterar WMI-instansen om den finns eller skapar en ny instans om en instans inte finns.</span><span class="sxs-lookup"><span data-stu-id="543b3-224">Updates the WMI instance if it exists or creates a new instance if an instance does not exist.</span></span>

```yaml
Type: System.Management.PutType
Parameter Sets: (All)
Aliases:
Accepted values: None, UpdateOnly, CreateOnly, UpdateOrCreate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-225">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="543b3-225">-ThrottleLimit</span></span>
<span data-ttu-id="543b3-226">Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="543b3-226">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="543b3-227">Den här parametern används tillsammans med parametern *AsJob* .</span><span class="sxs-lookup"><span data-stu-id="543b3-227">This parameter is used together with the *AsJob* parameter.</span></span>
<span data-ttu-id="543b3-228">Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.</span><span class="sxs-lookup"><span data-stu-id="543b3-228">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="543b3-229">-Confirm</span><span class="sxs-lookup"><span data-stu-id="543b3-229">-Confirm</span></span>
<span data-ttu-id="543b3-230">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="543b3-230">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-231">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="543b3-231">-WhatIf</span></span>
<span data-ttu-id="543b3-232">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="543b3-232">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="543b3-233">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="543b3-233">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="543b3-234">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="543b3-234">CommonParameters</span></span>
<span data-ttu-id="543b3-235">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="543b3-235">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="543b3-236">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="543b3-236">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="543b3-237">INDATA</span><span class="sxs-lookup"><span data-stu-id="543b3-237">INPUTS</span></span>

### <span data-ttu-id="543b3-238">Inget</span><span class="sxs-lookup"><span data-stu-id="543b3-238">None</span></span>
<span data-ttu-id="543b3-239">Denna cmdlet accepterar inte indatatyper.</span><span class="sxs-lookup"><span data-stu-id="543b3-239">This cmdlet does not accept input.</span></span>

## <span data-ttu-id="543b3-240">UTDATA</span><span class="sxs-lookup"><span data-stu-id="543b3-240">OUTPUTS</span></span>

### <span data-ttu-id="543b3-241">Inget</span><span class="sxs-lookup"><span data-stu-id="543b3-241">None</span></span>
<span data-ttu-id="543b3-242">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="543b3-242">This cmdlet does not generate output.</span></span>

## <span data-ttu-id="543b3-243">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="543b3-243">NOTES</span></span>

## <span data-ttu-id="543b3-244">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="543b3-244">RELATED LINKS</span></span>

[<span data-ttu-id="543b3-245">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="543b3-245">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="543b3-246">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="543b3-246">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="543b3-247">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="543b3-247">Remove-WmiObject</span></span>](Remove-WmiObject.md)
