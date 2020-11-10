---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSession
ms.openlocfilehash: dfb5d6f46dec89495d19680cec8b73ad12340797
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388696"
---
# <span data-ttu-id="6829c-103">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="6829c-103">Get-PSSession</span></span>

## <span data-ttu-id="6829c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6829c-104">SYNOPSIS</span></span>
<span data-ttu-id="6829c-105">Hämtar PowerShell-sessioner på lokala och fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="6829c-105">Gets the PowerShell sessions on local and remote computers.</span></span>

## <span data-ttu-id="6829c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6829c-106">SYNTAX</span></span>

### <span data-ttu-id="6829c-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="6829c-107">Name (Default)</span></span>

```
Get-PSSession [-Name <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="6829c-108">ComputerName</span><span class="sxs-lookup"><span data-stu-id="6829c-108">ComputerName</span></span>

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="6829c-109">ComputerInstanceId</span><span class="sxs-lookup"><span data-stu-id="6829c-109">ComputerInstanceId</span></span>

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="6829c-110">ConnectionUriInstanceId</span><span class="sxs-lookup"><span data-stu-id="6829c-110">ConnectionUriInstanceId</span></span>

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] -InstanceId <Guid[]>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="6829c-111">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="6829c-111">ConnectionUri</span></span>

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="6829c-112">Hålla</span><span class="sxs-lookup"><span data-stu-id="6829c-112">ContainerId</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="6829c-113">ContainerIdInstanceId</span><span class="sxs-lookup"><span data-stu-id="6829c-113">ContainerIdInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="6829c-114">VMId</span><span class="sxs-lookup"><span data-stu-id="6829c-114">VMId</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### <span data-ttu-id="6829c-115">VMIdInstanceId</span><span class="sxs-lookup"><span data-stu-id="6829c-115">VMIdInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### <span data-ttu-id="6829c-116">VMName</span><span class="sxs-lookup"><span data-stu-id="6829c-116">VMName</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMName <String[]>
 [<CommonParameters>]
```

### <span data-ttu-id="6829c-117">VMNameInstanceId</span><span class="sxs-lookup"><span data-stu-id="6829c-117">VMNameInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="6829c-118">InstanceId</span><span class="sxs-lookup"><span data-stu-id="6829c-118">InstanceId</span></span>

```
Get-PSSession [-InstanceId <Guid[]>] [<CommonParameters>]
```

### <span data-ttu-id="6829c-119">Id</span><span class="sxs-lookup"><span data-stu-id="6829c-119">Id</span></span>

```
Get-PSSession [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="6829c-120">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6829c-120">DESCRIPTION</span></span>

<span data-ttu-id="6829c-121">`Get-PSSession`Cmdleten hämtar de användare-hanterade PowerShell-sessionerna ( **PSSessions** ) på lokala datorer och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="6829c-121">The `Get-PSSession` cmdlet gets the user-managed PowerShell sessions ( **PSSessions** ) on local and remote computers.</span></span>

<span data-ttu-id="6829c-122">Från och med Windows PowerShell 3,0 lagras sessioner på datorerna i fjärrparten för varje anslutning.</span><span class="sxs-lookup"><span data-stu-id="6829c-122">Starting in Windows PowerShell 3.0, sessions are stored on the computers at the remote end of each connection.</span></span> <span data-ttu-id="6829c-123">Du kan använda parametrarna **computername** eller **ConnectionUri** för `Get-PSSession` för att hämta de sessioner som ansluter till den lokala datorn eller fjärrdatorer, även om de inte har skapats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-123">You can use the **ComputerName** or **ConnectionUri** parameters of `Get-PSSession` to get the sessions that connect to the local computer or remote computers, even if they were not created in the current session.</span></span>

<span data-ttu-id="6829c-124">Utan parametrar `Get-PSSession` hämtar alla sessioner som har skapats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-124">Without parameters, `Get-PSSession` gets all sessions that were created in the current session.</span></span>

<span data-ttu-id="6829c-125">Använd filtrerings parametrarna, inklusive **namn** , **ID** , **InstanceID** , **State** , **ApplicationName** och **ConfigurationName** för att välja bland de sessioner som `Get-PSSession` returneras.</span><span class="sxs-lookup"><span data-stu-id="6829c-125">Use the filtering parameters, including **Name** , **ID** , **InstanceID** , **State** , **ApplicationName** , and **ConfigurationName** to select from among the sessions that `Get-PSSession` returns.</span></span>

<span data-ttu-id="6829c-126">Använd de återstående parametrarna för att konfigurera den tillfälliga anslutning där `Get-PSSession` kommandot körs när du använder parametrarna **computername** eller **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="6829c-126">Use the remaining parameters to configure the temporary connection in which the `Get-PSSession` command runs when you use the **ComputerName** or **ConnectionUri** parameters.</span></span>

<span data-ttu-id="6829c-127">Obs: i Windows PowerShell 2,0, utan parametrar, `Get-PSSession` hämtas alla sessioner som har skapats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-127">NOTE: In Windows PowerShell 2.0, without parameters, `Get-PSSession` gets all sessions that were created in the current session.</span></span> <span data-ttu-id="6829c-128">Parametern **computername** hämtar sessioner som har skapats i den aktuella sessionen och anslutit till den angivna datorn.</span><span class="sxs-lookup"><span data-stu-id="6829c-128">The **ComputerName** parameter gets sessions that were created in the current session and connect to the specified computer.</span></span>

<span data-ttu-id="6829c-129">Mer information om PowerShell-sessioner finns [about_PSSessions](about/about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="6829c-129">For more information about PowerShell sessions, see [about_PSSessions](about/about_PSSessions.md).</span></span>

## <span data-ttu-id="6829c-130">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6829c-130">EXAMPLES</span></span>

### <span data-ttu-id="6829c-131">Exempel 1: Hämta sessioner som skapats i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="6829c-131">Example 1: Get sessions created in the current session</span></span>

```powershell
Get-PSSession
```

<span data-ttu-id="6829c-132">Det här kommandot hämtar alla **PSSessions** som skapades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-132">This command gets all of the **PSSessions** that were created in the current session.</span></span> <span data-ttu-id="6829c-133">Den hämtar inte **PSSessions** som har skapats i andra sessioner eller på andra datorer, även om de ansluter till den här datorn.</span><span class="sxs-lookup"><span data-stu-id="6829c-133">It does not get **PSSessions** that were created in other sessions or on other computers, even if they connect to this computer.</span></span>

### <span data-ttu-id="6829c-134">Exempel 2: Hämta sessioner som är anslutna till den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="6829c-134">Example 2: Get sessions connected to the local computer</span></span>

```powershell
Get-PSSession -ComputerName "localhost"
```

<span data-ttu-id="6829c-135">Det här kommandot hämtar **PSSessions** som är anslutna till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6829c-135">This command gets the **PSSessions** that are connected to the local computer.</span></span> <span data-ttu-id="6829c-136">Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.)</span><span class="sxs-lookup"><span data-stu-id="6829c-136">To indicate the local computer, type the computer name, localhost, or a dot (.)</span></span>

<span data-ttu-id="6829c-137">Kommandot returnerar alla sessioner på den lokala datorn, även om de har skapats i olika sessioner eller på olika datorer.</span><span class="sxs-lookup"><span data-stu-id="6829c-137">The command returns all of the sessions on the local computer, even if they were created in different sessions or on different computers.</span></span>

### <span data-ttu-id="6829c-138">Exempel 3: Hämta sessioner som är anslutna till en dator</span><span class="sxs-lookup"><span data-stu-id="6829c-138">Example 3: Get sessions connected to a computer</span></span>

```powershell
Get-PSSession -ComputerName "Server02"
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  2 Session3        Server02       Disconnected  ITTasks                       Busy
  1 ScheduledJobs   Server02       Opened        Microsoft.PowerShell     Available
  3 Test            Server02       Disconnected  Microsoft.PowerShell          Busy
```

<span data-ttu-id="6829c-139">Det här kommandot hämtar **PSSessions** som är anslutna till Server02-datorn.</span><span class="sxs-lookup"><span data-stu-id="6829c-139">This command gets the **PSSessions** that are connected to the Server02 computer.</span></span>

<span data-ttu-id="6829c-140">Kommandot returnerar alla sessioner på Server02, även om de har skapats i olika sessioner eller på olika datorer.</span><span class="sxs-lookup"><span data-stu-id="6829c-140">The command returns all of the sessions on Server02, even if they were created in different sessions or on different computers.</span></span>

<span data-ttu-id="6829c-141">Utdata visar att två av sessionerna har ett frånkopplat tillstånd och en upptagen tillgänglighet.</span><span class="sxs-lookup"><span data-stu-id="6829c-141">The output shows that two of the sessions have a Disconnected state and a Busy availability.</span></span> <span data-ttu-id="6829c-142">De skapades i olika sessioner och används för närvarande.</span><span class="sxs-lookup"><span data-stu-id="6829c-142">They were created in different sessions and are currently in use.</span></span> <span data-ttu-id="6829c-143">ScheduledJobs-sessionen, som öppnas och är tillgänglig, har skapats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-143">The ScheduledJobs session, which is Opened and Available, was created in the current session.</span></span>

### <span data-ttu-id="6829c-144">Exempel 4: Spara resultatet av det här kommandot</span><span class="sxs-lookup"><span data-stu-id="6829c-144">Example 4: Save results of this command</span></span>

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
$s1, $s2, $s3 = Get-PSSession
```

<span data-ttu-id="6829c-145">Det här exemplet visar hur du sparar resultatet av ett `Get-PSSession` kommando i flera variabler.</span><span class="sxs-lookup"><span data-stu-id="6829c-145">This example shows how to save the results of a `Get-PSSession` command in multiple variables.</span></span>

<span data-ttu-id="6829c-146">Det första kommandot använder `New-PSSession` cmdleten för att skapa **PSSessions** på tre fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="6829c-146">The first command uses the `New-PSSession` cmdlet to create **PSSessions** on three remote computers.</span></span>

<span data-ttu-id="6829c-147">Det andra kommandot använder en `Get-PSSession` cmdlet för att hämta de tre **PSSessions**.</span><span class="sxs-lookup"><span data-stu-id="6829c-147">The second command uses a `Get-PSSession` cmdlet to get the three **PSSessions**.</span></span> <span data-ttu-id="6829c-148">Sedan sparas varje **PSSessions** i en separat variabel.</span><span class="sxs-lookup"><span data-stu-id="6829c-148">It then saves each of the **PSSessions** in a separate variable.</span></span>

<span data-ttu-id="6829c-149">När PowerShell tilldelar en matris med objekt till en matris med variabler tilldelas det första objektet till den första variabeln, det andra objektet till den andra variabeln, och så vidare.</span><span class="sxs-lookup"><span data-stu-id="6829c-149">When PowerShell assigns an array of objects to an array of variables, it assigns the first object to the first variable, the second object to the second variable, and so on.</span></span> <span data-ttu-id="6829c-150">Om det finns fler objekt än variabler tilldelas alla återstående objekt till den sista variabeln i matrisen.</span><span class="sxs-lookup"><span data-stu-id="6829c-150">If there are more objects than variables, it assigns all remaining objects to the last variable in the array.</span></span> <span data-ttu-id="6829c-151">Om det finns fler variabler än objekt används inte de extra variablerna.</span><span class="sxs-lookup"><span data-stu-id="6829c-151">If there are more variables than objects, the extra variables are not used.</span></span>

### <span data-ttu-id="6829c-152">Exempel 5: ta bort en session med ett instans-ID</span><span class="sxs-lookup"><span data-stu-id="6829c-152">Example 5: Delete a session by using an instance ID</span></span>

```powershell
Get-PSSession | Format-Table -Property ComputerName, InstanceID
$s = Get-PSSession -InstanceID a786be29-a6bb-40da-80fb-782c67f7db0f
Remove-PSSession -Session $s
```

<span data-ttu-id="6829c-153">Det här exemplet visar hur du hämtar en **PSSession** genom att använda dess instans-ID och sedan ta bort **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="6829c-153">This example shows how to get a **PSSession** by using its instance ID, and then to delete the **PSSession**.</span></span>

<span data-ttu-id="6829c-154">Det första kommandot hämtar alla **PSSessions** som skapades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-154">The first command gets all of the **PSSessions** that were created in the current session.</span></span> <span data-ttu-id="6829c-155">Den skickar **PSSessions** till Format-Table-cmdlet, som visar **computername** -och **InstanceID** -egenskaperna för varje **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="6829c-155">It sends the **PSSessions** to the Format-Table cmdlet, which displays the **ComputerName** and **InstanceID** properties of each **PSSession**.</span></span>

<span data-ttu-id="6829c-156">Det andra kommandot använder `Get-PSSession` cmdleten för att hämta en viss **PSSession** och för att spara den i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6829c-156">The second command uses the `Get-PSSession` cmdlet to get a particular **PSSession** and to save it in the `$s` variable.</span></span> <span data-ttu-id="6829c-157">Kommandot använder **InstanceID** -parametern för att identifiera **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="6829c-157">The command uses the **InstanceID** parameter to identify the **PSSession**.</span></span>

<span data-ttu-id="6829c-158">Det tredje kommandot använder cmdleten Remove-PSSession för att ta bort **PSSession** i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6829c-158">The third command uses the Remove-PSSession cmdlet to delete the **PSSession** in the `$s` variable.</span></span>

### <span data-ttu-id="6829c-159">Exempel 6: Hämta en session med ett visst namn</span><span class="sxs-lookup"><span data-stu-id="6829c-159">Example 6: Get a session that has a particular name</span></span>

<span data-ttu-id="6829c-160">Kommandona i det här exemplet söker efter en session med ett visst namn format och använder en viss sessionsinformation och ansluter sedan till sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-160">The commands in this example find a session that has a particular name format and uses a particular session configuration and then connect to the session.</span></span> <span data-ttu-id="6829c-161">Du kan använda ett kommando som det här för att hitta en session där en kollega startade en uppgift och ansluta för att slutföra uppgiften.</span><span class="sxs-lookup"><span data-stu-id="6829c-161">You can use a command like this one to find a session in which a colleague started a task and connect to finish the task.</span></span>

```powershell
Get-PSSession -ComputerName Server02, Server12 -Name BackupJob* -ConfigurationName ITTasks -SessionOption @{OperationTimeout=240000}
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  3 BackupJob04     Server02        Disconnected        ITTasks                  None
```

```powershell
$s = Get-PSSession -ComputerName Server02 -Name BackupJob04 -ConfigurationName ITTasks | Connect-PSSession
$s
```

```Output
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 5 BackupJob04     Server02        Opened        ITTasks                  Available
```

<span data-ttu-id="6829c-162">Det första kommandot hämtar sessioner på Server02-och Server12-fjärrdatorer som har namn som börjar med BackupJob och använder ITTasks-sessionen. Kommandot använder **Name** -parametern för att ange namn mönstret och parametern **ConfigurationName** för att ange konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-162">The first command gets sessions on the Server02 and Server12 remote computers that have names that begin with BackupJob and use the ITTasks session configuration.The command uses the **Name** parameter to specify the name pattern and the **ConfigurationName** parameter to specify the session configuration.</span></span> <span data-ttu-id="6829c-163">Värdet för parametern **SessionOption** är en hash-tabell som anger värdet för **OperationTimeout** till 240000 millisekunder (4 minuter).</span><span class="sxs-lookup"><span data-stu-id="6829c-163">The value of the **SessionOption** parameter is a hash table that sets the value of the **OperationTimeout** to 240000 milliseconds (4 minutes).</span></span> <span data-ttu-id="6829c-164">Den här inställningen ger kommandot mer tid att slutföra. Parametrarna **ConfigurationName** och **SessionOption** används för att konfigurera de tillfälliga sessioner där `Get-PSSession` cmdleten körs på varje dator. Utdata visar att kommandot returnerar BackupJob04-sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-164">This setting gives the command more time to complete.The **ConfigurationName** and **SessionOption** parameters are used to configure the temporary sessions in which the `Get-PSSession` cmdlet runs on each computer.The output shows that the command returns the BackupJob04 session.</span></span> <span data-ttu-id="6829c-165">Sessionen är frånkopplad och **tillgängligheten** är ingen, vilket anger att den inte används.</span><span class="sxs-lookup"><span data-stu-id="6829c-165">The session is disconnected and the **Availability** is None, which indicates that it is not in use.</span></span>

<span data-ttu-id="6829c-166">Det andra kommandot använder `Get-PSSession` cmdleten för att komma till BackupJob04-sessionen och Connect-PSSession cmdlet för att ansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-166">The second command uses the `Get-PSSession` cmdlet to get to the BackupJob04 session and the Connect-PSSession cmdlet to connect to the session.</span></span> <span data-ttu-id="6829c-167">Kommandot sparar sessionen i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="6829c-167">The command saves the session in the $s variable.</span></span>

<span data-ttu-id="6829c-168">Det tredje kommandot hämtar sessionen i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="6829c-168">The third command gets the session in the $s variable.</span></span> <span data-ttu-id="6829c-169">Resultatet visar att `Connect-PSSession` kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6829c-169">The output shows that the `Connect-PSSession` command was successful.</span></span> <span data-ttu-id="6829c-170">Sessionen är i ett **öppet** tillstånd och kan användas.</span><span class="sxs-lookup"><span data-stu-id="6829c-170">The session is in the **Opened** state and is available for use.</span></span>

### <span data-ttu-id="6829c-171">Exempel 7: Hämta en session med hjälp av dess ID</span><span class="sxs-lookup"><span data-stu-id="6829c-171">Example 7: Get a session by using its ID</span></span>

```powershell
Get-PSSession -Id 2
```

<span data-ttu-id="6829c-172">Det här kommandot hämtar **PSSession** med ID 2.</span><span class="sxs-lookup"><span data-stu-id="6829c-172">This command gets the **PSSession** with ID 2.</span></span> <span data-ttu-id="6829c-173">Eftersom värdet för egenskapen **ID** endast är unikt i den aktuella sessionen, är **ID-** parametern endast giltig för lokala kommandon.</span><span class="sxs-lookup"><span data-stu-id="6829c-173">Because the value of the **ID** property is unique only in the current session, the **Id** parameter is valid only for local commands.</span></span>

## <span data-ttu-id="6829c-174">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6829c-174">PARAMETERS</span></span>

### <span data-ttu-id="6829c-175">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="6829c-175">-AllowRedirection</span></span>

<span data-ttu-id="6829c-176">Anger att denna cmdlet tillåter omdirigering av anslutningen till en alternativ Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="6829c-176">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="6829c-177">Som standard omdirigerar PowerShell inte anslutningar.</span><span class="sxs-lookup"><span data-stu-id="6829c-177">By default, PowerShell does not redirect connections.</span></span>

<span data-ttu-id="6829c-178">Den här parametern konfigurerar den tillfälliga anslutning som skapas för att köra ett `Get-PSSession` kommando med parametern **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="6829c-178">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ConnectionUri** parameter.</span></span>

<span data-ttu-id="6829c-179">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6829c-179">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-180">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="6829c-180">-ApplicationName</span></span>

<span data-ttu-id="6829c-181">Anger namnet på ett program.</span><span class="sxs-lookup"><span data-stu-id="6829c-181">Specifies the name of an application.</span></span> <span data-ttu-id="6829c-182">Denna cmdlet ansluter bara till sessioner som använder det angivna programmet.</span><span class="sxs-lookup"><span data-stu-id="6829c-182">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="6829c-183">Ange program namns segmentet för anslutnings-URI: n.</span><span class="sxs-lookup"><span data-stu-id="6829c-183">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="6829c-184">I följande anslutnings-URI är till exempel program namnet WSMan: `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="6829c-184">For example, in the following connection URI, the application name is WSMan: `http://localhost:5985/WSMAN`.</span></span> <span data-ttu-id="6829c-185">Program namnet för en session lagras i egenskapen **körnings utrymme. ConnectionInfo. APPNAME** för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-185">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="6829c-186">Värdet för den här parametern används för att välja och filtrera sessioner.</span><span class="sxs-lookup"><span data-stu-id="6829c-186">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="6829c-187">Den ändrar inte det program som används av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-187">It does not change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-188">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="6829c-188">-Authentication</span></span>

<span data-ttu-id="6829c-189">Anger den mekanism som används för att autentisera autentiseringsuppgifter för den session där `Get-PSSession` kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="6829c-189">Specifies the mechanism that is used to authenticate credentials for the session in which the `Get-PSSession` command runs.</span></span>

<span data-ttu-id="6829c-190">Den här parametern konfigurerar den tillfälliga anslutning som skapas för att köra ett `Get-PSSession` kommando med parametern **computername** eller **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="6829c-190">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="6829c-191">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="6829c-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6829c-192">Standard</span><span class="sxs-lookup"><span data-stu-id="6829c-192">Default</span></span>
- <span data-ttu-id="6829c-193">Grundläggande</span><span class="sxs-lookup"><span data-stu-id="6829c-193">Basic</span></span>
- <span data-ttu-id="6829c-194">CredSSP</span><span class="sxs-lookup"><span data-stu-id="6829c-194">Credssp</span></span>
- <span data-ttu-id="6829c-195">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="6829c-195">Digest</span></span>
- <span data-ttu-id="6829c-196">Kerberos</span><span class="sxs-lookup"><span data-stu-id="6829c-196">Kerberos</span></span>
- <span data-ttu-id="6829c-197">Negotiate</span><span class="sxs-lookup"><span data-stu-id="6829c-197">Negotiate</span></span>
- <span data-ttu-id="6829c-198">NegotiateWithImplicitCredential.</span><span class="sxs-lookup"><span data-stu-id="6829c-198">NegotiateWithImplicitCredential.</span></span>

<span data-ttu-id="6829c-199">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="6829c-199">The default value is Default.</span></span>

<span data-ttu-id="6829c-200">Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="6829c-200">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="6829c-201">Varning! CredSSP-autentisering (Credential Security Support Provider), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="6829c-201">CAUTION: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="6829c-202">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="6829c-202">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="6829c-203">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-203">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="6829c-204">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6829c-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-205">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="6829c-205">-CertificateThumbprint</span></span>

<span data-ttu-id="6829c-206">Anger det digitala certifikat för offentlig nyckel (X509) för ett användar konto som har behörighet att skapa sessionen där `Get-PSSession` kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="6829c-206">Specifies the digital public key certificate (X509) of a user account that has permission to create the session in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="6829c-207">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="6829c-207">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="6829c-208">Den här parametern konfigurerar den tillfälliga anslutning som skapas för att köra ett `Get-PSSession` kommando med parametern **computername** eller **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="6829c-208">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="6829c-209">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="6829c-209">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="6829c-210">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="6829c-210">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="6829c-211">Använd ett Get-Item-eller Get-ChildItem kommando i PowerShell-certifikatet för att hämta ett tumavtryck för certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="6829c-211">To get a certificate thumbprint, use a Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

<span data-ttu-id="6829c-212">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6829c-212">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-213">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="6829c-213">-ComputerName</span></span>

<span data-ttu-id="6829c-214">Anger en matris med namn på datorer.</span><span class="sxs-lookup"><span data-stu-id="6829c-214">Specifies an array of names of computers.</span></span> <span data-ttu-id="6829c-215">Hämtar de sessioner som ansluter till de angivna datorerna.</span><span class="sxs-lookup"><span data-stu-id="6829c-215">Gets the sessions that connect to the specified computers.</span></span>
<span data-ttu-id="6829c-216">Jokertecken tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="6829c-216">Wildcard characters are not permitted.</span></span> <span data-ttu-id="6829c-217">Det finns inget standardvärde.</span><span class="sxs-lookup"><span data-stu-id="6829c-217">There is no default value.</span></span>

<span data-ttu-id="6829c-218">Från och med Windows PowerShell 3,0 lagras **PSSession** -objekt på datorerna i Fjärrslutpunkten för varje anslutning.</span><span class="sxs-lookup"><span data-stu-id="6829c-218">Beginning in Windows PowerShell 3.0, **PSSession** objects are stored on the computers at the remote end of each connection.</span></span> <span data-ttu-id="6829c-219">För att hämta sessionerna på de angivna datorerna skapar PowerShell en tillfällig anslutning till varje dator och kör ett `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="6829c-219">To get the sessions on the specified computers, PowerShell creates a temporary connection to each computer and runs a `Get-PSSession` command.</span></span>

<span data-ttu-id="6829c-220">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera datorer.</span><span class="sxs-lookup"><span data-stu-id="6829c-220">Type the NetBIOS name, an IP address, or a fully-qualified domain name of one or more computers.</span></span> <span data-ttu-id="6829c-221">Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.).</span><span class="sxs-lookup"><span data-stu-id="6829c-221">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

<span data-ttu-id="6829c-222">OBS! den här parametern hämtar endast sessioner från datorer som kör Windows PowerShell 3,0 eller senare versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6829c-222">Note: This parameter gets sessions only from computers that run Windows PowerShell 3.0 or later versions of PowerShell.</span></span> <span data-ttu-id="6829c-223">Tidigare versioner lagrar inte sessioner.</span><span class="sxs-lookup"><span data-stu-id="6829c-223">Earlier versions do not store sessions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerInstanceId, ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-224">– ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="6829c-224">-ConfigurationName</span></span>

<span data-ttu-id="6829c-225">Anger namnet på en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6829c-225">Specifies the name of a configuration.</span></span> <span data-ttu-id="6829c-226">Denna cmdlet får endast användas för sessioner som använder den angivna konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-226">This cmdlet gets only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="6829c-227">Ange ett konfigurations namn eller den fullständigt kvalificerade resurs-URI: n för en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-227">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="6829c-228">Om du bara anger konfigurations namnet är följande schema-URI anpassningsprefix: `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="6829c-228">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span> <span data-ttu-id="6829c-229">Konfigurations namnet för en session lagras i sessionens **ConfigurationName** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="6829c-229">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="6829c-230">Värdet för den här parametern används för att välja och filtrera sessioner.</span><span class="sxs-lookup"><span data-stu-id="6829c-230">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="6829c-231">Den ändrar inte den sessionsinformation som sessionen använder.</span><span class="sxs-lookup"><span data-stu-id="6829c-231">It does not change the session configuration that the session uses.</span></span>

<span data-ttu-id="6829c-232">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="6829c-232">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-233">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="6829c-233">-ConnectionUri</span></span>

<span data-ttu-id="6829c-234">Anger en URI som definierar anslutnings slut punkten för den tillfälliga sessionen där `Get-PSSession` kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="6829c-234">Specifies a URI that defines the connection endpoint for the temporary session in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="6829c-235">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="6829c-235">The URI must be fully qualified.</span></span>

<span data-ttu-id="6829c-236">Den här parametern konfigurerar den tillfälliga anslutning som skapas för att köra ett `Get-PSSession` kommando med parametern **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="6829c-236">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ConnectionUri** parameter.</span></span>

<span data-ttu-id="6829c-237">Formatet för den här strängen är:</span><span class="sxs-lookup"><span data-stu-id="6829c-237">The format of this string is:</span></span>

`<Transport>://<ComputerName>:<Port\>/<ApplicationName>`

<span data-ttu-id="6829c-238">Standardvärdet är: `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="6829c-238">The default value is: `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="6829c-239">Om du inte anger en **ConnectionUri** kan du använda parametrarna **UseSSL** , **computername** , **port** och **ApplicationName** för att ange **ConnectionUri** -värden.</span><span class="sxs-lookup"><span data-stu-id="6829c-239">If you do not specify a **ConnectionUri** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span> <span data-ttu-id="6829c-240">Giltiga värden för URI: n i transport segmentet är HTTP och HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6829c-240">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="6829c-241">Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med standard portar: 80 för HTTP och 443 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6829c-241">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="6829c-242">Om du vill använda standard portarna för PowerShell-fjärrkommunikation anger du Port 5985 för HTTP eller 5986 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6829c-242">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="6829c-243">Om mål datorn omdirigerar anslutningen till en annan URI, förhindrar PowerShell omdirigeringen om du inte använder parametern **AllowRedirection** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="6829c-243">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

<span data-ttu-id="6829c-244">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6829c-244">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="6829c-245">Den här parametern hämtar endast sessioner från datorer som kör Windows PowerShell 3,0 eller senare versioner av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6829c-245">This parameter gets sessions only from computers that run Windows PowerShell 3.0 or later versions of Windows PowerShell.</span></span> <span data-ttu-id="6829c-246">Tidigare versioner lagrar inte sessioner.</span><span class="sxs-lookup"><span data-stu-id="6829c-246">Earlier versions do not store sessions.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUri, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: Http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-247">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="6829c-247">-ContainerId</span></span>

<span data-ttu-id="6829c-248">Anger en matris med ID: n för behållare.</span><span class="sxs-lookup"><span data-stu-id="6829c-248">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="6829c-249">Den här cmdleten startar en interaktiv session med var och en av de angivna behållarna.</span><span class="sxs-lookup"><span data-stu-id="6829c-249">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="6829c-250">Använd `docker ps` kommandot för att hämta en lista över behållar-ID: n.</span><span class="sxs-lookup"><span data-stu-id="6829c-250">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="6829c-251">Mer information finns i hjälpen för kommandot [Docker PS](https://docs.docker.com/engine/reference/commandline/ps/) .</span><span class="sxs-lookup"><span data-stu-id="6829c-251">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId, ContainerIdInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-252">-Credential</span><span class="sxs-lookup"><span data-stu-id="6829c-252">-Credential</span></span>

<span data-ttu-id="6829c-253">Anger autentiseringsuppgifter för användare.</span><span class="sxs-lookup"><span data-stu-id="6829c-253">Specifies a user credential.</span></span> <span data-ttu-id="6829c-254">Denna cmdlet kör kommandot med behörigheterna för den angivna användaren.</span><span class="sxs-lookup"><span data-stu-id="6829c-254">This cmdlet runs the command with the permissions of the specified user.</span></span> <span data-ttu-id="6829c-255">Ange ett användar konto som har behörighet att ansluta till fjärrdatorn och kör ett `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="6829c-255">Specify a user account that has permission to connect to the remote computer and run a `Get-PSSession` command.</span></span> <span data-ttu-id="6829c-256">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="6829c-256">The default is the current user.</span></span>

<span data-ttu-id="6829c-257">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6829c-257">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="6829c-258">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="6829c-258">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="6829c-259">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="6829c-259">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="6829c-260">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="6829c-260">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="6829c-261">Den här parametern konfigurerar till den tillfälliga anslutning som skapas för att köra ett `Get-PSSession` kommando med parametern **computername** eller **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="6829c-261">This parameter configures to the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="6829c-262">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6829c-262">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-263">-ID</span><span class="sxs-lookup"><span data-stu-id="6829c-263">-Id</span></span>

<span data-ttu-id="6829c-264">Anger en matris med sessions-ID: n.</span><span class="sxs-lookup"><span data-stu-id="6829c-264">Specifies an array of session IDs.</span></span> <span data-ttu-id="6829c-265">Denna cmdlet hämtar bara sessionerna med de angivna ID: na.</span><span class="sxs-lookup"><span data-stu-id="6829c-265">This cmdlet gets only the sessions with the specified IDs.</span></span> <span data-ttu-id="6829c-266">Skriv ett eller flera ID: n, avgränsade med kommatecken eller Använd intervall operatorn (..) för att ange ett intervall med ID: n.</span><span class="sxs-lookup"><span data-stu-id="6829c-266">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span> <span data-ttu-id="6829c-267">Du kan inte använda ID-parametern tillsammans med parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="6829c-267">You cannot use the ID parameter together with the **ComputerName** parameter.</span></span>

<span data-ttu-id="6829c-268">Ett ID är ett heltal som unikt identifierar de användar hanterade sessionerna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-268">An ID is an integer that uniquely identifies the user-managed sessions in the current session.</span></span> <span data-ttu-id="6829c-269">Det är enklare att komma ihåg och skriva än **InstanceID** , men det är endast unikt inom den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-269">It is easier to remember and type than the **InstanceId** , but it is unique only within the current session.</span></span> <span data-ttu-id="6829c-270">ID: t för en session lagras i sessionens ID-egenskap.</span><span class="sxs-lookup"><span data-stu-id="6829c-270">The ID of a session is stored in the ID property of the session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-271">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="6829c-271">-InstanceId</span></span>

<span data-ttu-id="6829c-272">Anger en matris med instans-ID: n för sessioner.</span><span class="sxs-lookup"><span data-stu-id="6829c-272">Specifies an array of instance IDs of sessions.</span></span> <span data-ttu-id="6829c-273">Denna cmdlet hämtar bara sessionerna med de angivna instans-ID: na.</span><span class="sxs-lookup"><span data-stu-id="6829c-273">This cmdlet gets only the sessions with the specified instance IDs.</span></span>

<span data-ttu-id="6829c-274">Instans-ID är ett GUID som unikt identifierar en session på en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="6829c-274">The instance ID is a GUID that uniquely identifies a session on a local or remote computer.</span></span> <span data-ttu-id="6829c-275">**InstanceID** är unikt, även om du har flera sessioner som körs i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6829c-275">The **InstanceID** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="6829c-276">Instans-ID: t för en session lagras i sessionens **InstanceID** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="6829c-276">The instance ID of a session is stored in the **InstanceID** property of the session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId, InstanceId
Aliases:

Required: True (ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId), False (InstanceId)
Position: Named
Default value: All sessions
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-277">-Name</span><span class="sxs-lookup"><span data-stu-id="6829c-277">-Name</span></span>

<span data-ttu-id="6829c-278">Anger en matris med sessionsnamn.</span><span class="sxs-lookup"><span data-stu-id="6829c-278">Specifies an array of session names.</span></span> <span data-ttu-id="6829c-279">Denna cmdlet hämtar bara de sessioner som har angivna egna namn.</span><span class="sxs-lookup"><span data-stu-id="6829c-279">This cmdlet gets only the sessions that have the specified friendly names.</span></span> <span data-ttu-id="6829c-280">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="6829c-280">Wildcard characters are permitted.</span></span>

<span data-ttu-id="6829c-281">Det egna namnet på en session lagras i sessionens **namn** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="6829c-281">The friendly name of a session is stored in the **Name** property of the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri, ContainerId, VMId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="6829c-282">-Port</span><span class="sxs-lookup"><span data-stu-id="6829c-282">-Port</span></span>

<span data-ttu-id="6829c-283">Anger den angivna nätverks porten som används för den tillfälliga anslutning där `Get-PSSession` kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="6829c-283">Specifies the specified network port that is used for the temporary connection in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="6829c-284">Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder.</span><span class="sxs-lookup"><span data-stu-id="6829c-284">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="6829c-285">Standard portarna är 5985, som är WinRM-porten för HTTP och 5986, som är WinRM-porten för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6829c-285">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="6829c-286">Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.</span><span class="sxs-lookup"><span data-stu-id="6829c-286">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="6829c-287">Konfigurera lyssnaren genom att skriva följande två kommandon i PowerShell-prompten:</span><span class="sxs-lookup"><span data-stu-id="6829c-287">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="6829c-288">Den här parametern konfigurerar till den tillfälliga anslutning som skapas för att köra ett `Get-PSSession` kommando med parametern **computername** eller **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="6829c-288">This parameter configures to the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="6829c-289">Använd inte **port** parametern om du inte behöver.</span><span class="sxs-lookup"><span data-stu-id="6829c-289">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="6829c-290">**Porten** som anges i kommandot gäller för alla datorer eller sessioner där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="6829c-290">The **Port** set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="6829c-291">En alternativ port inställning kan hindra kommandot från att köras på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="6829c-291">An alternate port setting might prevent the command from running on all computers.</span></span>

<span data-ttu-id="6829c-292">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6829c-292">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: 5985, 5986
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-293">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="6829c-293">-SessionOption</span></span>

<span data-ttu-id="6829c-294">Anger avancerade alternativ för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-294">Specifies advanced options for the session.</span></span> <span data-ttu-id="6829c-295">Ange ett **SessionOption** -objekt, t. ex. ett som du skapar med hjälp av New-PSSessionOption-cmdleten, eller en hash-tabell där nycklarna är namn på sessionstillstånd och värdena är alternativ värden för session.</span><span class="sxs-lookup"><span data-stu-id="6829c-295">Enter a **SessionOption** object, such as one that you create by using the New-PSSessionOption cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="6829c-296">Standardvärdena för alternativen bestäms av värdet för variabeln $PSSessionOption, om det har angetts.</span><span class="sxs-lookup"><span data-stu-id="6829c-296">The default values for the options are determined by the value of the $PSSessionOption preference variable, if it is set.</span></span> <span data-ttu-id="6829c-297">Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-297">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="6829c-298">Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i variabeln $PSSessionOption och i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-298">The session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span> <span data-ttu-id="6829c-299">De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-299">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="6829c-300">En beskrivning av sessions alternativen, inklusive standardvärdena, finns i `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="6829c-300">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="6829c-301">Information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="6829c-301">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="6829c-302">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="6829c-302">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-303">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="6829c-303">-State</span></span>

<span data-ttu-id="6829c-304">Anger ett sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="6829c-304">Specifies a session state.</span></span> <span data-ttu-id="6829c-305">Denna cmdlet hämtar endast sessioner i det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="6829c-305">This cmdlet gets only sessions in the specified state.</span></span> <span data-ttu-id="6829c-306">De acceptabla värdena för den här parametern är: alla, öppna, frånkopplade, stängda och brutna.</span><span class="sxs-lookup"><span data-stu-id="6829c-306">The acceptable values for this parameter are: All, Opened, Disconnected, Closed, and Broken.</span></span> <span data-ttu-id="6829c-307">Standardvärdet är Alla.</span><span class="sxs-lookup"><span data-stu-id="6829c-307">The default value is All.</span></span>

<span data-ttu-id="6829c-308">Värdet för sessionstillstånd är i förhållande till de aktuella sessionerna.</span><span class="sxs-lookup"><span data-stu-id="6829c-308">The session state value is relative to the current sessions.</span></span> <span data-ttu-id="6829c-309">Sessioner som inte har skapats i de aktuella sessionerna och som inte är anslutna till den aktuella sessionen har statusen Frånkopplad även om de är anslutna till en annan session.</span><span class="sxs-lookup"><span data-stu-id="6829c-309">Sessions that were not created in the current sessions and are not connected to the current session have a state of Disconnected even when they are connected to a different session.</span></span>

<span data-ttu-id="6829c-310">Status för en session lagras i sessionens **tillstånds** egenskap.</span><span class="sxs-lookup"><span data-stu-id="6829c-310">The state of a session is stored in the **State** property of the session.</span></span>

<span data-ttu-id="6829c-311">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6829c-311">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.SessionFilterState
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:
Accepted values: All, Opened, Disconnected, Closed, Broken

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-312">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6829c-312">-ThrottleLimit</span></span>

<span data-ttu-id="6829c-313">Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra `Get-PSSession` kommandot.</span><span class="sxs-lookup"><span data-stu-id="6829c-313">Specifies the maximum number of concurrent connections that can be established to run the `Get-PSSession` command.</span></span> <span data-ttu-id="6829c-314">Om du utelämnar den här parametern eller anger värdet 0 (noll) används standardvärdet 32.</span><span class="sxs-lookup"><span data-stu-id="6829c-314">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span> <span data-ttu-id="6829c-315">Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.</span><span class="sxs-lookup"><span data-stu-id="6829c-315">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

<span data-ttu-id="6829c-316">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6829c-316">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-317">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="6829c-317">-UseSSL</span></span>

<span data-ttu-id="6829c-318">Anger att denna cmdlet använder Secure Sockets Layer (SSL)-protokollet för att upprätta anslutningen där `Get-PSSession` kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="6829c-318">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish the connection in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="6829c-319">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="6829c-319">By default, SSL is not used.</span></span> <span data-ttu-id="6829c-320">Om du använder den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="6829c-320">If you use this parameter, but SSL is not available on the port used for the command, the command fails.</span></span>

<span data-ttu-id="6829c-321">Den här parametern konfigurerar den tillfälliga anslutning som skapas för att köra ett `Get-PSSession` kommando med parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="6829c-321">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** parameter.</span></span>

<span data-ttu-id="6829c-322">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6829c-322">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-323">-VMId</span><span class="sxs-lookup"><span data-stu-id="6829c-323">-VMId</span></span>

<span data-ttu-id="6829c-324">Anger en matris med ID för virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="6829c-324">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="6829c-325">Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna.</span><span class="sxs-lookup"><span data-stu-id="6829c-325">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="6829c-326">Använd följande kommando för att se de virtuella datorer som är tillgängliga för dig:</span><span class="sxs-lookup"><span data-stu-id="6829c-326">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId, VMIdInstanceId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-327">– VMName</span><span class="sxs-lookup"><span data-stu-id="6829c-327">-VMName</span></span>

<span data-ttu-id="6829c-328">Anger en matris med namn på virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="6829c-328">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="6829c-329">Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna.</span><span class="sxs-lookup"><span data-stu-id="6829c-329">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="6829c-330">Använd cmdleten för att se de virtuella datorer som är tillgängliga för dig `Get-VM` .</span><span class="sxs-lookup"><span data-stu-id="6829c-330">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName, VMNameInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6829c-331">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6829c-331">CommonParameters</span></span>

<span data-ttu-id="6829c-332">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6829c-332">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6829c-333">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6829c-333">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6829c-334">INDATA</span><span class="sxs-lookup"><span data-stu-id="6829c-334">INPUTS</span></span>

### <span data-ttu-id="6829c-335">Inget</span><span class="sxs-lookup"><span data-stu-id="6829c-335">None</span></span>

<span data-ttu-id="6829c-336">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6829c-336">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="6829c-337">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6829c-337">OUTPUTS</span></span>

### <span data-ttu-id="6829c-338">System. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="6829c-338">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="6829c-339">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6829c-339">NOTES</span></span>

- <span data-ttu-id="6829c-340">Med den här cmdleten får du **PSSession** objekt som skapats med hjälp av cmdletarna New-PSSession, `Enter-PSSession` och Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="6829c-340">This cmdlet gets user-managed sessions **PSSession** objects" such as those that are created by using the New-PSSession, `Enter-PSSession`, and Invoke-Command cmdlets.</span></span> <span data-ttu-id="6829c-341">Den får inte den systemhanterade sessionen som skapas när du startar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6829c-341">It does not get the system-managed session that is created when you start PowerShell.</span></span>
- <span data-ttu-id="6829c-342">Från och med Windows PowerShell 3,0 lagras **PSSession** -objekt på den dator som finns på Server sidan eller tar emot en anslutning.</span><span class="sxs-lookup"><span data-stu-id="6829c-342">Starting in Windows PowerShell 3.0, **PSSession** objects are stored on the computer that is at the server-side or receiving end of a connection.</span></span> <span data-ttu-id="6829c-343">För att hämta de sessioner som lagras på den lokala datorn eller en fjärrdator, upprättar PowerShell en tillfällig session till den angivna datorn och kör fråga-kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-343">To get the sessions that are stored on the local computer or a remote computer, PowerShell establishes a temporary session to the specified computer and runs query commands in the session.</span></span>
- <span data-ttu-id="6829c-344">Om du vill hämta sessioner som ansluter till en fjärrdator använder du parametrarna **computername** eller **ConnectionUri** för att ange fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="6829c-344">To get sessions that connect to a remote computer, use the **ComputerName** or **ConnectionUri** parameters to specify the remote computer.</span></span> <span data-ttu-id="6829c-345">Om du vill filtrera de sessioner som `Get-PSSession` hämtar använder du parametrarna **namn** , **ID** , **InstanceID** och **tillstånd** .</span><span class="sxs-lookup"><span data-stu-id="6829c-345">To filter the sessions that `Get-PSSession` gets, use the **Name** , **ID** , **InstanceID** , and **State** parameters.</span></span> <span data-ttu-id="6829c-346">Använd de återstående parametrarna för att konfigurera den tillfälliga sessionen som `Get-PSSession` använder.</span><span class="sxs-lookup"><span data-stu-id="6829c-346">Use the remaining parameters to configure the temporary session that `Get-PSSession` uses.</span></span>
- <span data-ttu-id="6829c-347">När du använder parametrarna **computername** eller **ConnectionUri** `Get-PSSession` hämtar endast sessioner från datorer som kör Windows PowerShell 3,0 och senare versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6829c-347">When you use the **ComputerName** or **ConnectionUri** parameters, `Get-PSSession` gets only sessions from computers running Windows PowerShell 3.0 and later versions of PowerShell.</span></span>
- <span data-ttu-id="6829c-348">Värdet för egenskapen **State** för en **PSSession** är i förhållande till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-348">The value of the **State** property of a **PSSession** is relative to the current session.</span></span>
  <span data-ttu-id="6829c-349">Därför innebär värdet **frånkopplat** att **PSSession** inte är ansluten till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-349">Therefore, a value of **Disconnected** means that the **PSSession** is not connected to the current session.</span></span> <span data-ttu-id="6829c-350">Det innebär dock inte att **PSSession** är frånkopplad från alla sessioner.</span><span class="sxs-lookup"><span data-stu-id="6829c-350">However, it does not mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="6829c-351">Den kan vara ansluten till en annan session.</span><span class="sxs-lookup"><span data-stu-id="6829c-351">It might be connected to a different session.</span></span> <span data-ttu-id="6829c-352">Använd egenskapen **Availability** för att avgöra om du kan ansluta eller återansluta till **PSSession** från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-352">To determine whether you can connect or reconnect to the **PSSession** from the current session, use the **Availability** property.</span></span>

<span data-ttu-id="6829c-353">**Tillgänglighet** svärdet **none** anger att du kan ansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="6829c-353">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="6829c-354">Värdet **upptagen** anger att du inte kan ansluta till **PSSession** eftersom det är anslutet till en annan session.</span><span class="sxs-lookup"><span data-stu-id="6829c-354">A value of **Busy** indicates that you cannot connect to the **PSSession** because it is connected to another session.</span></span>

<span data-ttu-id="6829c-355">Mer information om värdena för egenskapen **State** för sessioner finns i [RunspaceState-uppräkning](/dotnet/api/system.management.automation.runspaces.runspacestate).</span><span class="sxs-lookup"><span data-stu-id="6829c-355">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>

<span data-ttu-id="6829c-356">Mer information om värdena för egenskapen **Availability** för sessioner finns i [RunspaceAvailability-uppräkning](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span><span class="sxs-lookup"><span data-stu-id="6829c-356">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="6829c-357">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6829c-357">RELATED LINKS</span></span>

[<span data-ttu-id="6829c-358">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="6829c-358">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="6829c-359">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="6829c-359">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="6829c-360">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="6829c-360">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="6829c-361">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="6829c-361">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="6829c-362">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="6829c-362">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="6829c-363">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="6829c-363">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="6829c-364">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="6829c-364">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="6829c-365">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="6829c-365">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="6829c-366">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="6829c-366">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="6829c-367">about_Remote</span><span class="sxs-lookup"><span data-stu-id="6829c-367">about_Remote</span></span>](About/about_Remote.md)
