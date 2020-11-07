---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disconnect-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-PSSession
ms.openlocfilehash: 2588d0d0a8d7ce9cddf65c94dcc79700df9deeb7
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345570"
---
# <span data-ttu-id="93a66-103">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="93a66-103">Disconnect-PSSession</span></span>

## <span data-ttu-id="93a66-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="93a66-104">SYNOPSIS</span></span>
<span data-ttu-id="93a66-105">Kopplar från en session.</span><span class="sxs-lookup"><span data-stu-id="93a66-105">Disconnects from a session.</span></span>

## <span data-ttu-id="93a66-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="93a66-106">SYNTAX</span></span>

### <span data-ttu-id="93a66-107">Session (standard)</span><span class="sxs-lookup"><span data-stu-id="93a66-107">Session (Default)</span></span>

```
Disconnect-PSSession [-Session] <PSSession[]> [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="93a66-108">Name</span><span class="sxs-lookup"><span data-stu-id="93a66-108">Name</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="93a66-109">InstanceId</span><span class="sxs-lookup"><span data-stu-id="93a66-109">InstanceId</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="93a66-110">Id</span><span class="sxs-lookup"><span data-stu-id="93a66-110">Id</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="93a66-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="93a66-111">DESCRIPTION</span></span>

<span data-ttu-id="93a66-112">`Disconnect-PSSession`Cmdleten kopplar från en PowerShell-session ("PSSession"), till exempel en som har startats med hjälp av `New-PSSession` cmdleten, från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-112">The `Disconnect-PSSession` cmdlet disconnects a PowerShell session ("PSSession"), such as one started by using the `New-PSSession` cmdlet, from the current session.</span></span> <span data-ttu-id="93a66-113">Därför är PSSession i frånkopplat läge.</span><span class="sxs-lookup"><span data-stu-id="93a66-113">As a result, the PSSession is in a disconnected state.</span></span> <span data-ttu-id="93a66-114">Du kan ansluta till den frånkopplade PSSession från den aktuella sessionen eller från en annan session på den lokala datorn eller en annan dator.</span><span class="sxs-lookup"><span data-stu-id="93a66-114">You can connect to the disconnected PSSession from the current session or from another session on the local computer or a different computer.</span></span>

<span data-ttu-id="93a66-115">`Disconnect-PSSession`Cmdleten kopplar bara från öppna PSSessions som är anslutna till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-115">The `Disconnect-PSSession` cmdlet disconnects only open PSSessions that are connected to the current session.</span></span> <span data-ttu-id="93a66-116">`Disconnect-PSSession` Det går inte att koppla från brutna eller stängda PSSessions eller interaktiva PSSessions som har startats med hjälp av `Enter-PSSession` cmdleten och kan inte koppla bort PSSessions som är anslutna till andra sessioner.</span><span class="sxs-lookup"><span data-stu-id="93a66-116">`Disconnect-PSSession` cannot disconnect broken or closed PSSessions, or interactive PSSessions started by using the `Enter-PSSession` cmdlet, and it cannot disconnect PSSessions that are connected to other sessions.</span></span>

<span data-ttu-id="93a66-117">Om du vill återansluta till en frånkopplad PSSession använder du `Connect-PSSession` `Receive-PSSession` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="93a66-117">To reconnect to a disconnected PSSession, use the `Connect-PSSession` or `Receive-PSSession` cmdlets.</span></span>

<span data-ttu-id="93a66-118">När en PSSession kopplas från fortsätter kommandona i PSSession att köras tills de har slutförts, om inte PSSession timeout-värde eller kommandon i PSSession blockeras av en fullständig utdatabuffert.</span><span class="sxs-lookup"><span data-stu-id="93a66-118">When a PSSession is disconnected, the commands in the PSSession continue to run until they complete, unless the PSSession times out or the commands in the PSSession are blocked by a full output buffer.</span></span> <span data-ttu-id="93a66-119">Om du vill ändra tids gränsen för inaktivitet använder du parametern **IdleTimeoutSec** .</span><span class="sxs-lookup"><span data-stu-id="93a66-119">To change the idle timeout, use the **IdleTimeoutSec** parameter.</span></span> <span data-ttu-id="93a66-120">Om du vill ändra utdata buffer-läget använder du parametern **OutputBufferingMode** . du kan också använda parametern **InDisconnectedSession** för `Invoke-Command` cmdleten för att köra ett kommando i en frånkopplad session.</span><span class="sxs-lookup"><span data-stu-id="93a66-120">To change the output buffering mode, use the **OutputBufferingMode** parameter You can also use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet to run a command in a disconnected session.</span></span>

<span data-ttu-id="93a66-121">Mer information om funktionen frånkopplade sessioner finns [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span><span class="sxs-lookup"><span data-stu-id="93a66-121">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="93a66-122">Denna cmdlet introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="93a66-122">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="93a66-123">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="93a66-123">EXAMPLES</span></span>

### <span data-ttu-id="93a66-124">Exempel 1 – Koppla från en session efter namn</span><span class="sxs-lookup"><span data-stu-id="93a66-124">Example 1 - Disconnect a session by name</span></span>

<span data-ttu-id="93a66-125">Det här kommandot kopplar från UpdateSession-PSSession på Server01-datorn från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-125">This command disconnects the UpdateSession PSSession on the Server01 computer from the current session.</span></span> <span data-ttu-id="93a66-126">Kommandot använder parametern **Name** för att identifiera PSSession.</span><span class="sxs-lookup"><span data-stu-id="93a66-126">The command uses the **Name** parameter to identify the PSSession.</span></span>

```
PS> Disconnect-PSSession -Name UpdateSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  UpdateSession   Server01        Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="93a66-127">Utdata visar att försöket att koppla från lyckades.</span><span class="sxs-lookup"><span data-stu-id="93a66-127">The output shows that the attempt to disconnect was successful.</span></span> <span data-ttu-id="93a66-128">Sessionstillståndet är frånkopplat och tillgängligheten är ingen, vilket indikerar att sessionen inte är upptagen och kan återanslutas.</span><span class="sxs-lookup"><span data-stu-id="93a66-128">The session state is Disconnected and the Availability is None, which indicates that the session is not busy and can be reconnected.</span></span>

### <span data-ttu-id="93a66-129">Exempel 2 – Koppla från en session från en angiven dator</span><span class="sxs-lookup"><span data-stu-id="93a66-129">Example 2 - Disconnect a session from a specific computer</span></span>

<span data-ttu-id="93a66-130">Det här kommandot kopplar från ITTask-PSSession på Server12-datorn från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-130">This command disconnects the ITTask PSSession on the Server12 computer from the current session.</span></span>
<span data-ttu-id="93a66-131">ITTask-sessionen skapades i den aktuella sessionen och ansluts till Server12-datorn.</span><span class="sxs-lookup"><span data-stu-id="93a66-131">The ITTask session was created in the current session and connects to the Server12 computer.</span></span> <span data-ttu-id="93a66-132">Kommandot använder `Get-PSSession` cmdleten för att hämta sessionen och `Disconnect-PSSession` cmdleten för att koppla bort den.</span><span class="sxs-lookup"><span data-stu-id="93a66-132">The command uses the `Get-PSSession` cmdlet to get the session and the `Disconnect-PSSession` cmdlet to disconnect it.</span></span>

```
PS> Get-PSSession -ComputerName Server12 -Name ITTask |
  Disconnect-PSSession -OutputBufferingMode Drop -IdleTimeoutSec 86400
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  ITTask          Server12        Disconnected  ITTasks               None
```

<span data-ttu-id="93a66-133">`Disconnect-PSSession`Kommandot använder parametern **OutputBufferingMode** för att ange vilket utmatnings läge som ska **släppas**.</span><span class="sxs-lookup"><span data-stu-id="93a66-133">The `Disconnect-PSSession` command uses the **OutputBufferingMode** parameter to set the output mode to **Drop**.</span></span> <span data-ttu-id="93a66-134">Den här inställningen säkerställer att skriptet som körs i sessionen kan fortsätta att köras även om buffertens utdatabuffert är full.</span><span class="sxs-lookup"><span data-stu-id="93a66-134">This setting ensures that the script that is running in the session can continue to run even if the session output buffer is full.</span></span> <span data-ttu-id="93a66-135">Eftersom skriptet skriver utdata till en rapport på en fil resurs kan andra utdata gå förlorade utan konsekvens.</span><span class="sxs-lookup"><span data-stu-id="93a66-135">Because the script writes its output to a report on a file share, other output can be lost without consequence.</span></span>

<span data-ttu-id="93a66-136">Kommandot använder också parametern **IdleTimeoutSec** för att utöka tids gränsen för inaktivitet i sessionen till 24 timmar.</span><span class="sxs-lookup"><span data-stu-id="93a66-136">The command also uses the **IdleTimeoutSec** parameter to extend the idle timeout of the session to 24 hours.</span></span> <span data-ttu-id="93a66-137">Med den här inställningen kan administratören eller andra administratörer återansluta till sessionen för att kontrol lera att skriptet kördes och felsöka vid behov.</span><span class="sxs-lookup"><span data-stu-id="93a66-137">This setting allows time for this administrator or other administrators to reconnect to the session to verify that the script ran and troubleshoot if needed.</span></span>

### <span data-ttu-id="93a66-138">Exempel 3 – använda flera PSSessions på flera datorer</span><span class="sxs-lookup"><span data-stu-id="93a66-138">Example 3 - Using multiple PSSessions on multiple computers</span></span>

<span data-ttu-id="93a66-139">Den här serien med kommandon visar hur `Disconnect-PSSession` cmdleten kan användas i ett företags scenario.</span><span class="sxs-lookup"><span data-stu-id="93a66-139">This series of commands shows how the `Disconnect-PSSession` cmdlet might be used in an enterprise scenario.</span></span> <span data-ttu-id="93a66-140">I det här fallet startar en ny tekniker ett skript i en session på en fjärrdator och kan köras i ett problem.</span><span class="sxs-lookup"><span data-stu-id="93a66-140">In this case, a new technician starts a script in a session on a remote computer and runs into a problem.</span></span> <span data-ttu-id="93a66-141">Teknikern kopplar från sessionen så att en mer erfaren hanterare kan ansluta till sessionen och lösa problemet.</span><span class="sxs-lookup"><span data-stu-id="93a66-141">The technician disconnects from the session so that a more experienced manager can connect to the session and resolve the problem.</span></span>

```
PS> $s = New-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
PS> Invoke-Command $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Get-PSSession -Name ITTask -ComputerName Srv1 | Disconnect-PSSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1 ITTask           Srv1            Disconnected  Microsoft.PowerShell          None

PS> Get-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None
 2 ITTask          Srv2            Opened        Microsoft.PowerShell     Available
 3 ITTask          Srv30           Opened        Microsoft.PowerShell     Available

PS> Get-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None

PS> $s = Connect-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
PS> Invoke-Command -Session $s {dir $home\Scripts\PatchStatusOutput.ps1}
PS> Invoke-Command -Session $s {mkdir $home\Scripts\PatchStatusOutput}
PS> Invoke-Command -Session $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Disconnect-PSSession -Session $s
```

<span data-ttu-id="93a66-142">Teknikern börjar genom att skapa sessioner på flera fjärranslutna datorer och köra ett skript i varje session.</span><span class="sxs-lookup"><span data-stu-id="93a66-142">The technician begins by creating sessions on several remote computers and running a script in each session.</span></span> <span data-ttu-id="93a66-143">Det första kommandot använder `New-PSSession` cmdleten för att skapa ITTask-sessionen på tre fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="93a66-143">The first command uses the `New-PSSession` cmdlet to create the ITTask session on three remote computers.</span></span> <span data-ttu-id="93a66-144">Kommandot sparar sessionerna i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="93a66-144">The command saves the sessions in the $s variable.</span></span> <span data-ttu-id="93a66-145">Det andra kommandot använder parametern **sökväg** för `Invoke-Command` cmdleten för att köra ett skript i sessionerna i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="93a66-145">The second command uses the **FilePath** parameter of the `Invoke-Command` cmdlet to run a script in the sessions in the $s variable.</span></span>

<span data-ttu-id="93a66-146">Det skript som körs på Srv1-datorn genererar oväntade fel.</span><span class="sxs-lookup"><span data-stu-id="93a66-146">The script running on the Srv1 computer generates unexpected errors.</span></span> <span data-ttu-id="93a66-147">Teknikern kontaktar sin chef och ber om hjälp.</span><span class="sxs-lookup"><span data-stu-id="93a66-147">The technician contacts his manager and asks for assistance.</span></span> <span data-ttu-id="93a66-148">Chefen instruerar teknikern att koppla från sessionen så att han kan undersöka den. Det andra kommandot använder `Get-PSSession` cmdleten för att hämta ITTask-sessionen på Srv1-datorn och `Disconnect-PSSession` cmdlet: en för att koppla bort den.</span><span class="sxs-lookup"><span data-stu-id="93a66-148">The manager directs the technician to disconnect from the session so he can investigate.The second command uses the `Get-PSSession` cmdlet to get the ITTask session on the Srv1 computer and the `Disconnect-PSSession` cmdlet to disconnect it.</span></span> <span data-ttu-id="93a66-149">Det här kommandot påverkar inte ITTask-sessionerna på de andra datorerna.</span><span class="sxs-lookup"><span data-stu-id="93a66-149">This command does not affect the ITTask sessions on the other computers.</span></span>

<span data-ttu-id="93a66-150">Det tredje kommandot använder `Get-PSSession` cmdleten för att hämta ITTask-sessionerna.</span><span class="sxs-lookup"><span data-stu-id="93a66-150">The third command uses the `Get-PSSession` cmdlet to get the ITTask sessions.</span></span> <span data-ttu-id="93a66-151">Utdata visar att ITTask-sessionerna på Srv2-och Srv30-datorerna inte påverkades av kommandot för från koppling.</span><span class="sxs-lookup"><span data-stu-id="93a66-151">The output shows that the ITTask sessions on the Srv2 and Srv30 computers were not affected by the command to disconnect.</span></span>

<span data-ttu-id="93a66-152">Chefen loggar in på sin hem dator, ansluter till företagets nätverk, startar PowerShell och använder `Get-PSSession` cmdleten för att hämta ITTask-sessionen på den Srv1 datorn.</span><span class="sxs-lookup"><span data-stu-id="93a66-152">The manager logs on to his home computer, connects to his corporate network, starts PowerShell, and uses the `Get-PSSession` cmdlet to get the ITTask session on the Srv1 computer.</span></span> <span data-ttu-id="93a66-153">Han använder autentiseringsuppgifterna för teknikern för att få åtkomst till sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-153">He uses the credentials of the technician to access the session.</span></span>

<span data-ttu-id="93a66-154">Därefter använder chefen `Connect-PSSession` cmdleten för att ansluta till ITTask-sessionen på datorn med Srv1.</span><span class="sxs-lookup"><span data-stu-id="93a66-154">Next, the manager uses the `Connect-PSSession` cmdlet to connect to the ITTask session on the Srv1 computer.</span></span> <span data-ttu-id="93a66-155">Kommandot sparar sessionen i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="93a66-155">The command saves the session in the $s variable.</span></span>

<span data-ttu-id="93a66-156">Chefen använder `Invoke-Command` cmdleten för att köra vissa diagnostiska kommandon i sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="93a66-156">The manager uses the `Invoke-Command` cmdlet to run some diagnostic commands in the session in the `$s` variable.</span></span> <span data-ttu-id="93a66-157">Han känner av att skriptet misslyckades eftersom det inte gick att hitta en obligatorisk katalog.</span><span class="sxs-lookup"><span data-stu-id="93a66-157">He recognizes that the script failed because it did not find a required directory.</span></span>
<span data-ttu-id="93a66-158">Chefen använder `MkDir` funktionen för att skapa katalogen och startar sedan om `Get-PatchStatus.ps1` skriptet och kopplar från sessionen. Chefen rapporterar sina resultat till teknikern, vilket tyder på att han återansluter till sessionen för att slutföra uppgifterna och ber honom att lägga till ett kommando i `Get-PatchStatus.ps1` skriptet som skapar den nödvändiga katalogen om den inte finns.</span><span class="sxs-lookup"><span data-stu-id="93a66-158">The manager uses the `MkDir` function to create the directory, and then he restarts the `Get-PatchStatus.ps1` script and disconnects from the session.The manager reports his findings to the technician, suggests that he reconnect to the session to complete the tasks, and asks him to add a command to the `Get-PatchStatus.ps1` script that creates the required directory if it does not exist.</span></span>

### <span data-ttu-id="93a66-159">Exempel 4 – ändra timeout-värdet för en PSSession</span><span class="sxs-lookup"><span data-stu-id="93a66-159">Example 4 - Change the timeout value for a PSSession</span></span>

<span data-ttu-id="93a66-160">Det här exemplet visar hur du korrigerar värdet för egenskapen **idleTimeout** för en session så att den kan kopplas från.</span><span class="sxs-lookup"><span data-stu-id="93a66-160">This example shows how to correct the value of the **IdleTimeout** property of a session so that it can be disconnected.</span></span>

<span data-ttu-id="93a66-161">Egenskapen timeout för inaktivitet i en session är kritisk för frånkopplade sessioner, eftersom den fastställer hur länge en frånkopplad session upprätthålls innan den tas bort.</span><span class="sxs-lookup"><span data-stu-id="93a66-161">The idle timeout property of a session is critical to disconnected sessions, because it determines how long a disconnected session is maintained before it is deleted.</span></span> <span data-ttu-id="93a66-162">Du kan ställa in timeout-alternativet för inaktivitet när du skapar en session och när du kopplar från den.</span><span class="sxs-lookup"><span data-stu-id="93a66-162">You can set the idle timeout option when you create a session and when you disconnect it.</span></span> <span data-ttu-id="93a66-163">Standardvärdena för tids gränsen för inaktivitet i en session ställs in i `$PSSessionOption` Preference-variabeln på den lokala datorn och i konfigurationen på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="93a66-163">The default values for the idle timeout of a session are set in the `$PSSessionOption` preference variable on the local computer and in the session configuration on the remote computer.</span></span> <span data-ttu-id="93a66-164">Värden som har ställts in för sessionen har företräde framför värden som anges i konfigurationen av sessionen, men sessionsgränser får inte överskrida kvoter som angetts i konfigurationen för sessionen, till exempel **MaxIdleTimeoutMs** -värdet.</span><span class="sxs-lookup"><span data-stu-id="93a66-164">Values set for the session take precedence over values set in the session configuration, but session values cannot exceed quotas set in the session configuration, such as the **MaxIdleTimeoutMs** value.</span></span>

```
PS> $Timeout = New-PSSessionOption -IdleTimeout 172800000
PS> $s = New-PSSession -Computer Server01 -Name ITTask -SessionOption $Timeout
PS> Disconnect-PSSession -Session $s
Disconnect-PSSession : The session ITTask cannot be disconnected because the specified
idle timeout value 172800(seconds) is either greater than the server maximum allowed
43200 (seconds) or less that the minimum allowed60(seconds).  Choose an idle time out
value that is within the allowed range and try again.

PS> Invoke-Command -ComputerName Server01 {Get-PSSessionConfiguration Microsoft.PowerShell} |
 Format-List -Property *

Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/microsoft.powershell
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
SecurityDescriptorSddl        : O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GXGW;;;WD)
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 2147483647
Uri                           : http://schemas.microsoft.com/powershell/microsoft.powershell
SDKVersion                    : 2
Name                          : microsoft.powershell
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
ParentResourceUri             : http://schemas.microsoft.com/powershell/microsoft.powershell
Enabled                       : true
MaxShells                     : 25
MaxShellsPerUser              : 25
Permission                    : BUILTIN\Administrators AccessAllowed
PSComputerName                : localhost
RunspaceId                    : aea84310-6dbf-4c21-90ac-13980039925a
PSShowComputerName            : True


PS> $s.Runspace.ConnectionInfo
ConnectionUri                     : http://Server01/wsman
ComputerName                      : Server01
Scheme                            : http
Port                              : 80
AppName                           : /wsman
Credential                        :
ShellUri                          : http://schemas.microsoft.com/powershell/Microsoft.PowerShell
AuthenticationMechanism           : Default
CertificateThumbprint             :
MaximumConnectionRedirectionCount : 5
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
UseCompression                    : True
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
NoEncryption                      : False
UseUTF16                          : False
OutputBufferingMode               : Drop
IncludePortInSPN                  : False
Culture                           : en-US
UICulture                         : en-US
OpenTimeout                       : 180000
CancelTimeout                     : 60000
OperationTimeout                  : 180000
IdleTimeout                       : 172800000

PS> Disconnect-PSSession $s -IdleTimeoutSec 43200
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Disconnected  Microsoft.PowerShell          None

PS> $s.Runspace.ConnectionInfo.IdleTimeout
43200000
```

<span data-ttu-id="93a66-165">Det första kommandot använder `New-PSSessionOption` cmdleten för att skapa ett session alternativ-objekt.</span><span class="sxs-lookup"><span data-stu-id="93a66-165">The first command uses the `New-PSSessionOption` cmdlet to create a session option object.</span></span> <span data-ttu-id="93a66-166">Den använder **idleTimeout** -parametern för att ange en tids gräns för inaktivitet på 48 timmar (172800000 millisekunder).</span><span class="sxs-lookup"><span data-stu-id="93a66-166">It uses the **IdleTimeout** parameter to set an idle timeout of 48 hours (172800000 milliseconds).</span></span> <span data-ttu-id="93a66-167">Kommandot sparar objektet Session-alternativ i variabeln $Timeout.</span><span class="sxs-lookup"><span data-stu-id="93a66-167">The command saves the session option object in the $Timeout variable.</span></span>

<span data-ttu-id="93a66-168">Det andra kommandot använder `New-PSSession` cmdleten för att skapa ITTask-sessionen på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="93a66-168">The second command uses the `New-PSSession` cmdlet to create the ITTask session on the Server01 computer.</span></span> <span data-ttu-id="93a66-169">Kommandot sparar sessionen i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="93a66-169">The command save the session in the $s variable.</span></span> <span data-ttu-id="93a66-170">Värdet för parametern **SessionOption** är tids gränsen på 48 timmar för inaktivitet i $timeout variabeln.</span><span class="sxs-lookup"><span data-stu-id="93a66-170">The value of the **SessionOption** parameter is the 48-hour idle timeout in the $Timeout variable.</span></span>

<span data-ttu-id="93a66-171">Det tredje kommandot kopplar från ITTask-sessionen i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="93a66-171">The third command disconnects the ITTask session in the $s variable.</span></span> <span data-ttu-id="93a66-172">Kommandot Miss lyckas eftersom tids gränsen för inaktivitet i sessionen överskrider **MaxIdleTimeoutMs** kvoten i sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-172">The command fails because the idle timeout value of the session exceeds the **MaxIdleTimeoutMs** quota in the session configuration.</span></span> <span data-ttu-id="93a66-173">Eftersom tids gränsen för inaktivitet inte används förrän sessionen kopplas från, kan denna överträdelse gå ur bruk medan sessionen används.</span><span class="sxs-lookup"><span data-stu-id="93a66-173">Because the idle timeout is not used until the session is disconnected, this violation can go undetected while the session is in use.</span></span>

<span data-ttu-id="93a66-174">Det fjärde kommandot använder `Invoke-Command` cmdleten för att köra ett `Get-PSSessionConfiguration` kommando för konfigurationen av Microsoft. PowerShell-sessionen på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="93a66-174">The fourth command uses the `Invoke-Command` cmdlet to run a `Get-PSSessionConfiguration` command for the Microsoft.PowerShell session configuration on the Server01 computer.</span></span> <span data-ttu-id="93a66-175">Kommandot använder `Format-List` cmdleten för att visa alla egenskaper för sessionens konfiguration i en lista. Utdata visar att egenskapen **MaxIdleTimeoutMS** , som upprättar det högsta tillåtna **idleTimeout** -värdet för sessioner som använder sessionen, är 43200000 millisekunder (12 timmar).</span><span class="sxs-lookup"><span data-stu-id="93a66-175">The command uses the `Format-List` cmdlet to display all properties of the session configuration in a list.The output shows that the **MaxIdleTimeoutMS** property, which establishes the maximum permitted **IdleTimeout** value for sessions that use the session configuration, is 43200000 milliseconds (12 hours).</span></span>

<span data-ttu-id="93a66-176">Det femte kommandot hämtar sessionens alternativ värden i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="93a66-176">The fifth command gets the session option values of the session in the $s variable.</span></span> <span data-ttu-id="93a66-177">Värdena för många session-alternativ är egenskaper för egenskapen **ConnectionInfo** för sessionens **körnings utrymme** -egenskap. Utdata visar att värdet för egenskapen **idleTimeout** i sessionen är 172800000 millisekunder (48 timmar), vilket bryter mot **MaxIdleTimeoutMs** -kvoten på 12 timmar i konfigurationen av sessionen. Du kan lösa den här konflikten genom att använda parametern **ConfigurationName** för att välja en annan sessions konfiguration eller använda **idleTimeout** -parametern för att minska tids gränsen för inaktivitet för sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-177">The values of many session options are properties of the **ConnectionInfo** property of the **Runspace** property of the session.The output shows that the value of the **IdleTimeout** property of the session is 172800000 milliseconds (48 hours), which violates the **MaxIdleTimeoutMs** quota of 12 hours in the session configuration.To resolve this conflict, you can use the **ConfigurationName** parameter to select a different session configuration or use the **IdleTimeout** parameter to reduce the idle timeout of the session.</span></span>

<span data-ttu-id="93a66-178">Det sjätte kommandot kopplar från sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-178">The sixth command disconnects the session.</span></span> <span data-ttu-id="93a66-179">Parametern **IdleTimeoutSec** används för att ange tids gränsen för inaktivitet till maximalt 12 timmar.</span><span class="sxs-lookup"><span data-stu-id="93a66-179">It uses the **IdleTimeoutSec** parameter to set the idle timeout to the 12-hour maximum.</span></span>

<span data-ttu-id="93a66-180">Det sjunde kommandot hämtar värdet för egenskapen **idleTimeout** för den frånkopplade sessionen, som mäts i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="93a66-180">The seventh command gets the value of the **IdleTimeout** property of the disconnected session, which is measured in milliseconds.</span></span> <span data-ttu-id="93a66-181">Resultatet bekräftar att kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="93a66-181">The output confirms that the command was successful.</span></span>

## <span data-ttu-id="93a66-182">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="93a66-182">PARAMETERS</span></span>

### <span data-ttu-id="93a66-183">-ID</span><span class="sxs-lookup"><span data-stu-id="93a66-183">-Id</span></span>

<span data-ttu-id="93a66-184">Kopplar från sessioner med angivet sessions-ID.</span><span class="sxs-lookup"><span data-stu-id="93a66-184">Disconnects from sessions with the specified session ID.</span></span> <span data-ttu-id="93a66-185">Skriv ett eller flera ID: n (avgränsade med kommatecken) eller Använd intervall operatorn (..) för att ange ett intervall med ID: n.</span><span class="sxs-lookup"><span data-stu-id="93a66-185">Type one or more IDs (separated by commas), or use the range operator (..) to specify a range of IDs.</span></span>

<span data-ttu-id="93a66-186">Använd cmdleten för att hämta ID för en session `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="93a66-186">To get the ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="93a66-187">Instans-ID: t lagras i sessionens **ID-** egenskap.</span><span class="sxs-lookup"><span data-stu-id="93a66-187">The instance ID is stored in the **ID** property of the session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="93a66-188">-IdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="93a66-188">-IdleTimeoutSec</span></span>

<span data-ttu-id="93a66-189">Ändrar timeout-värdet för inaktivitet för den frånkopplade PSSession.</span><span class="sxs-lookup"><span data-stu-id="93a66-189">Changes the idle timeout value of the disconnected PSSession.</span></span> <span data-ttu-id="93a66-190">Ange ett värde i sekunder.</span><span class="sxs-lookup"><span data-stu-id="93a66-190">Enter a value in seconds.</span></span> <span data-ttu-id="93a66-191">Det minsta värdet är 60 (1 minut).</span><span class="sxs-lookup"><span data-stu-id="93a66-191">The minimum value is 60 (1 minute).</span></span>

<span data-ttu-id="93a66-192">Tids gränsen för inaktivitet avgör hur länge den frånkopplade PSSession upprätthålls på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="93a66-192">The idle timeout determines how long the disconnected PSSession is maintained on the remote computer.</span></span> <span data-ttu-id="93a66-193">När tids gränsen går ut tas PSSession bort.</span><span class="sxs-lookup"><span data-stu-id="93a66-193">When the timeout expires, the PSSession is deleted.</span></span>

<span data-ttu-id="93a66-194">Frånkopplade PSSessions anses vara inaktiva från det ögonblick då de kopplas från, även om kommandon körs i den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-194">Disconnected PSSessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

<span data-ttu-id="93a66-195">Standardvärdet för tids gränsen för inaktivitet i en session anges av värdet för **IdleTimeoutMs** -egenskapen i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-195">The default value for the idle timeout of a session is set by the value of the **IdleTimeoutMs** property of the session configuration.</span></span> <span data-ttu-id="93a66-196">Standardvärdet är 7200000 millisekunder (2 timmar).</span><span class="sxs-lookup"><span data-stu-id="93a66-196">The default value is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="93a66-197">Värdet för den här parametern prioriteras över värdet för egenskapen **idleTimeout** i variabeln $PSSessionOption och standardvärdet för tids gräns för inaktivitet i sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-197">The value of this parameter takes precedence over the value of the **IdleTimeout** property of the $PSSessionOption preference variable and the default idle timeout value in the session configuration.</span></span> <span data-ttu-id="93a66-198">Värdet får dock inte överstiga värdet för **MaxIdleTimeoutMs** -egenskapen i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-198">However, this value cannot exceed the value of the **MaxIdleTimeoutMs** property of the session configuration.</span></span> <span data-ttu-id="93a66-199">Standardvärdet för **MaxIdleTimeoutMs** är 12 timmar (43200000 millisekunder).</span><span class="sxs-lookup"><span data-stu-id="93a66-199">The default value of **MaxIdleTimeoutMs** is 12 hours (43200000 milliseconds).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93a66-200">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="93a66-200">-InstanceId</span></span>

<span data-ttu-id="93a66-201">Kopplar från sessioner med angivet instans-ID.</span><span class="sxs-lookup"><span data-stu-id="93a66-201">Disconnects from sessions with the specified instance IDs.</span></span>

<span data-ttu-id="93a66-202">Instans-ID är ett GUID som unikt identifierar en session på en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="93a66-202">The instance ID is a GUID that uniquely identifies a session on a local or remote computer.</span></span> <span data-ttu-id="93a66-203">Instans-ID: t är unikt, även över flera sessioner på flera datorer.</span><span class="sxs-lookup"><span data-stu-id="93a66-203">The instance ID is unique, even across multiple sessions on multiple computers.</span></span>

<span data-ttu-id="93a66-204">Använd cmdleten för att hämta instans-ID för en session `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="93a66-204">To get the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="93a66-205">Instans-ID: t lagras i sessionens **InstanceID** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="93a66-205">The instance ID is stored in the **InstanceID** property of the session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="93a66-206">-Name</span><span class="sxs-lookup"><span data-stu-id="93a66-206">-Name</span></span>

<span data-ttu-id="93a66-207">Kopplar från sessioner med angivna egna namn.</span><span class="sxs-lookup"><span data-stu-id="93a66-207">Disconnects from sessions with the specified friendly names.</span></span> <span data-ttu-id="93a66-208">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="93a66-208">Wildcards are permitted.</span></span>

<span data-ttu-id="93a66-209">Använd cmdleten för att hämta det egna namnet på en session `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="93a66-209">To get the friendly name of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="93a66-210">Det egna namnet lagras i sessionens **namn** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="93a66-210">The friendly name is stored in the **Name** property of the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="93a66-211">– Session</span><span class="sxs-lookup"><span data-stu-id="93a66-211">-Session</span></span>

<span data-ttu-id="93a66-212">Kopplar från den angivna PSSessions.</span><span class="sxs-lookup"><span data-stu-id="93a66-212">Disconnects from the specified PSSessions.</span></span> <span data-ttu-id="93a66-213">Ange PSSession-objekt, till exempel de som `New-PSSession` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="93a66-213">Enter PSSession objects, such as those that the `New-PSSession` cmdlet returns.</span></span> <span data-ttu-id="93a66-214">Du kan också skicka ett PSSession-objekt till `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="93a66-214">You can also pipe a PSSession object to `Disconnect-PSSession`.</span></span>

<span data-ttu-id="93a66-215">`Get-PSSession`Cmdleten kan hämta alla PSSessions som avslutas på en fjärrdator, inklusive PSSessions som är frånkopplade och PSSessions som är anslutna till andra sessioner på andra datorer.</span><span class="sxs-lookup"><span data-stu-id="93a66-215">The `Get-PSSession` cmdlet can get all PSSessions that terminate at a remote computer, including PSSessions that are disconnected and PSSessions that are connected to other sessions on other computers.</span></span> <span data-ttu-id="93a66-216">`Disconnect-PSSession` kopplar bara från PSSession som är anslutna till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-216">`Disconnect-PSSession` disconnects only PSSession that are connected to the current session.</span></span> <span data-ttu-id="93a66-217">Om du rör andra PSSessions till `Disconnect-PSSession` `Disconnect-PSSession` Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="93a66-217">If you pipe other PSSessions to `Disconnect-PSSession`, the `Disconnect-PSSession` command fails.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="93a66-218">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="93a66-218">-ThrottleLimit</span></span>

<span data-ttu-id="93a66-219">Anger begränsnings begränsningen för `Disconnect-PSSession` kommandot.</span><span class="sxs-lookup"><span data-stu-id="93a66-219">Sets the throttle limit for the `Disconnect-PSSession` command.</span></span>

<span data-ttu-id="93a66-220">Begränsnings gränsen är det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="93a66-220">The throttle limit is the maximum number of concurrent connections that can be established to run this command.</span></span> <span data-ttu-id="93a66-221">Om du utelämnar den här parametern eller anger värdet 0, används standardvärdet 32.</span><span class="sxs-lookup"><span data-stu-id="93a66-221">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="93a66-222">Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.</span><span class="sxs-lookup"><span data-stu-id="93a66-222">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93a66-223">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="93a66-223">-OutputBufferingMode</span></span>

<span data-ttu-id="93a66-224">Anger hur kommandoutdata hanteras i den frånkopplade sessionen när utdatabufferten är full.</span><span class="sxs-lookup"><span data-stu-id="93a66-224">Determines how command output is managed in the disconnected session when the output buffer is full.</span></span> <span data-ttu-id="93a66-225">Standardvärdet är **block**.</span><span class="sxs-lookup"><span data-stu-id="93a66-225">The default value is **Block**.</span></span>

<span data-ttu-id="93a66-226">Om kommandot i den frånkopplade sessionen returnerar utdata och utdata buffrar, avgör värdet för parametern effektivt om kommandot fortsätter att köras medan sessionen kopplas från.</span><span class="sxs-lookup"><span data-stu-id="93a66-226">If the command in the disconnected session is returning output and the output buffer fills, the value of this parameter effectively determines whether the command continues to run while the session is disconnected.</span></span> <span data-ttu-id="93a66-227">Värdet **block** pausar kommandot tills sessionen återansluts.</span><span class="sxs-lookup"><span data-stu-id="93a66-227">A value of **Block** suspends the command until the session is reconnected.</span></span> <span data-ttu-id="93a66-228">Ett **Drop** -värde gör att kommandot kan slutföras, men data kan gå förlorade.</span><span class="sxs-lookup"><span data-stu-id="93a66-228">A value of **Drop** allows the command to complete, although data might be lost.</span></span> <span data-ttu-id="93a66-229">När du använder **Drop** -värdet dirigerar du om kommandots utdata till en fil på disk.</span><span class="sxs-lookup"><span data-stu-id="93a66-229">When using the **Drop** value, redirect the command output to a file on disk.</span></span>

<span data-ttu-id="93a66-230">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="93a66-230">Valid values are:</span></span>

- <span data-ttu-id="93a66-231">**Blockera** : när utdatabufferten är full pausas körningen tills bufferten är klar.</span><span class="sxs-lookup"><span data-stu-id="93a66-231">**Block** : When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="93a66-232">**Drop** : när utdatabufferten är full fortsätter körningen.</span><span class="sxs-lookup"><span data-stu-id="93a66-232">**Drop** : When the output buffer is full, execution continues.</span></span> <span data-ttu-id="93a66-233">När nya utdata sparas, ignoreras det äldsta resultatet.</span><span class="sxs-lookup"><span data-stu-id="93a66-233">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="93a66-234">**Ingen** : inget utdata buffer-läge har angetts.</span><span class="sxs-lookup"><span data-stu-id="93a66-234">**None** : No output buffering mode is specified.</span></span> <span data-ttu-id="93a66-235">Värdet för **OutputBufferingMode** -egenskapen i konfigurationen används för den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-235">The value of the **OutputBufferingMode** property of the session configuration is used for the disconnected session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Block
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93a66-236">-Confirm</span><span class="sxs-lookup"><span data-stu-id="93a66-236">-Confirm</span></span>

<span data-ttu-id="93a66-237">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="93a66-237">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="93a66-238">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="93a66-238">-WhatIf</span></span>

<span data-ttu-id="93a66-239">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="93a66-239">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="93a66-240">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="93a66-240">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="93a66-241">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="93a66-241">CommonParameters</span></span>

<span data-ttu-id="93a66-242">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="93a66-242">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="93a66-243">Mer information finns i [about_CommonParameters](./About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="93a66-243">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="93a66-244">INDATA</span><span class="sxs-lookup"><span data-stu-id="93a66-244">INPUTS</span></span>

### <span data-ttu-id="93a66-245">System. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="93a66-245">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="93a66-246">Du kan skicka vidare en session till `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="93a66-246">You can pipe a session to `Disconnect-PSSession`.</span></span>

## <span data-ttu-id="93a66-247">UTDATA</span><span class="sxs-lookup"><span data-stu-id="93a66-247">OUTPUTS</span></span>

### <span data-ttu-id="93a66-248">System. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="93a66-248">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="93a66-249">`Disconnect-PSSession` Returnerar ett objekt som representerar sessionen som den kopplades från.</span><span class="sxs-lookup"><span data-stu-id="93a66-249">`Disconnect-PSSession` returns an object that represents the session that it disconnected.</span></span>

## <span data-ttu-id="93a66-250">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="93a66-250">NOTES</span></span>

<span data-ttu-id="93a66-251">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="93a66-251">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="93a66-252">`Disconnect-PSSession`Cmdleten fungerar bara när lokala och fjärranslutna datorer kör PowerShell 3,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="93a66-252">The `Disconnect-PSSession` cmdlet works only when the local and remote computers are running PowerShell 3.0 or later.</span></span>
- <span data-ttu-id="93a66-253">Om du använder `Disconnect-PSSession` cmdleten i en frånkopplad session har kommandot ingen påverkan på sessionen och det genererar inga fel.</span><span class="sxs-lookup"><span data-stu-id="93a66-253">If you use the `Disconnect-PSSession` cmdlet on a disconnected session, the command has no effect on the session and it does not generate errors.</span></span>
- <span data-ttu-id="93a66-254">Frånkopplade loopback-sessioner med interaktiva säkerhetstoken (de som skapats med parametern **EnableNetworkAccess** ) kan bara återanslutas från den dator där sessionen skapades.</span><span class="sxs-lookup"><span data-stu-id="93a66-254">Disconnected loopback sessions with interactive security tokens (those created with the **EnableNetworkAccess** parameter) can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="93a66-255">Den här begränsningen skyddar datorn från skadlig åtkomst.</span><span class="sxs-lookup"><span data-stu-id="93a66-255">This restriction protects the computer from malicious access.</span></span>
- <span data-ttu-id="93a66-256">När du kopplar från en PSSession **kopplas sessionstillståndet ned** och tillgängligheten är **ingen**.</span><span class="sxs-lookup"><span data-stu-id="93a66-256">When you disconnect a PSSession, the session state is **Disconnected** and the availability is **None**.</span></span>

  <span data-ttu-id="93a66-257">Värdet för egenskapen **State** är i förhållande till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-257">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="93a66-258">Därför innebär värdet **frånkopplat** att PSSession inte är ansluten till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-258">Therefore, a value of **Disconnected** means that the PSSession is not connected to the current session.</span></span> <span data-ttu-id="93a66-259">Det innebär dock inte att PSSession är frånkopplad från alla sessioner.</span><span class="sxs-lookup"><span data-stu-id="93a66-259">However, it does not mean that the PSSession is disconnected from all sessions.</span></span> <span data-ttu-id="93a66-260">Den kan vara ansluten till en annan session.</span><span class="sxs-lookup"><span data-stu-id="93a66-260">It might be connected to a different session.</span></span> <span data-ttu-id="93a66-261">Använd egenskapen **tillgänglighet** för att avgöra om du kan ansluta eller återansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-261">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

  <span data-ttu-id="93a66-262">**Tillgänglighet** svärdet **none** anger att du kan ansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="93a66-262">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="93a66-263">Värdet **upptagen** anger att du inte kan ansluta till PSSession eftersom det är anslutet till en annan session.</span><span class="sxs-lookup"><span data-stu-id="93a66-263">A value of **Busy** indicates that you cannot connect to the PSSession because it is connected to another session.</span></span>

  <span data-ttu-id="93a66-264">Mer information om värdena för egenskapen **State** för sessioner finns i [RunspaceState-uppräkning](/dotnet/api/system.management.automation.runspaces.runspacestate).</span><span class="sxs-lookup"><span data-stu-id="93a66-264">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>

  <span data-ttu-id="93a66-265">Mer information om värdena för egenskapen **Availability** för sessioner finns i [RunspaceAvailability-uppräkning](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span><span class="sxs-lookup"><span data-stu-id="93a66-265">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="93a66-266">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="93a66-266">RELATED LINKS</span></span>

[<span data-ttu-id="93a66-267">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="93a66-267">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="93a66-268">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="93a66-268">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="93a66-269">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="93a66-269">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="93a66-270">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="93a66-270">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="93a66-271">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="93a66-271">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="93a66-272">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="93a66-272">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="93a66-273">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="93a66-273">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="93a66-274">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="93a66-274">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="93a66-275">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="93a66-275">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="93a66-276">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="93a66-276">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="93a66-277">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="93a66-277">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="93a66-278">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="93a66-278">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="93a66-279">about_Remote</span><span class="sxs-lookup"><span data-stu-id="93a66-279">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="93a66-280">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="93a66-280">about_Remote_Disconnected_Sessions</span></span>](About/about_Remote_Disconnected_Sessions.md)
