---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: 9257c0a1829cc9cc85029f7c6fdc8e61b0ed7e56
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268161"
---
# <span data-ttu-id="b193b-103">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="b193b-103">New-PSTransportOption</span></span>

## <span data-ttu-id="b193b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b193b-104">SYNOPSIS</span></span>

<span data-ttu-id="b193b-105">Skapar ett objekt som innehåller avancerade alternativ för en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="b193b-105">Creates an object that contains advanced options for a session configuration.</span></span>

## <span data-ttu-id="b193b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b193b-106">SYNTAX</span></span>

```
New-PSTransportOption [-MaxIdleTimeoutSec <Int32>] [-ProcessIdleTimeoutSec <Int32>] [-MaxSessions <Int32>]
 [-MaxConcurrentCommandsPerSession <Int32>] [-MaxSessionsPerUser <Int32>] [-MaxMemoryPerSessionMB <Int32>]
 [-MaxProcessesPerSession <Int32>] [-MaxConcurrentUsers <Int32>] [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [<CommonParameters>]
```

## <span data-ttu-id="b193b-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b193b-107">DESCRIPTION</span></span>

<span data-ttu-id="b193b-108">Cmdlet: en **New-PSTransportOption** skapar ett objekt som innehåller transport alternativ för sessionsinställningar.</span><span class="sxs-lookup"><span data-stu-id="b193b-108">The **New-PSTransportOption** cmdlet creates an object that contains transport options for session configurations.</span></span>
<span data-ttu-id="b193b-109">Du kan använda objektet som värdet för *TransportOption* -parametern för cmdlet: ar som skapar eller ändrar en sessionsinformation, till exempel Register-PSSessionConfiguration-och Set-PSSessionConfiguration-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="b193b-109">You can use the object as the value of the *TransportOption* parameter of cmdlets that create or change a session configuration, such as the Register-PSSessionConfiguration and Set-PSSessionConfiguration cmdlets.</span></span>

<span data-ttu-id="b193b-110">Du kan också ändra transport alternativ inställningarna genom att redigera värdena för konfigurations egenskaperna för sessionen på WSMan: Drive.</span><span class="sxs-lookup"><span data-stu-id="b193b-110">You can also change the transport option settings by editing the values of the session configuration properties in the WSMan: drive.</span></span>
<span data-ttu-id="b193b-111">Mer information finns i WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="b193b-111">For more information, see WSMan Provider.</span></span>

<span data-ttu-id="b193b-112">Konfigurations alternativen för sessionen representerar de Sessionsgränser som anges på Server sidan eller tar emot en fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="b193b-112">The session configuration options represent the session values set on the server-side, or receiving end of a remote connection.</span></span>
<span data-ttu-id="b193b-113">Klient sidan eller sändnings änden av anslutningen kan ange alternativ värden för sessionen när sessionen skapas, eller när klienten kopplar från eller återansluter till sessionen.</span><span class="sxs-lookup"><span data-stu-id="b193b-113">The client-side, or sending end of the connection, can set session option values when the session is created, or when the client disconnects from or reconnects to the session.</span></span>
<span data-ttu-id="b193b-114">Om inget annat anges, när inställnings värden är i konflikt med varandra, prioriteras värden på klient sidan.</span><span class="sxs-lookup"><span data-stu-id="b193b-114">Unless stated otherwise, when the setting values conflict, the client-side values take precedence.</span></span>
<span data-ttu-id="b193b-115">Värdena på klient sidan kan dock inte bryta mot maximalt antal värden och kvoter som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="b193b-115">However, the client-side values cannot violate maximum values and quotas set in the session configuration.</span></span>

<span data-ttu-id="b193b-116">Utan parametrar genererar **New-PSTransportOption** ett transport alternativ objekt som har null-värden för alla alternativ.</span><span class="sxs-lookup"><span data-stu-id="b193b-116">Without parameters, **New-PSTransportOption** generates a transport option object that has null values for all of the options.</span></span>
<span data-ttu-id="b193b-117">Om du utelämnar en parameter har objektet ett null-värde för egenskapen som parametern representerar.</span><span class="sxs-lookup"><span data-stu-id="b193b-117">If you omit a parameter, the object has a null value for the property that the parameter represents.</span></span>
<span data-ttu-id="b193b-118">Ett null-värde påverkar inte konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="b193b-118">A null value does not affect the session configuration.</span></span>

<span data-ttu-id="b193b-119">Mer information om sessions alternativ finns i New-PSSessionOption.</span><span class="sxs-lookup"><span data-stu-id="b193b-119">For more information about session options, see New-PSSessionOption.</span></span>
<span data-ttu-id="b193b-120">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="b193b-120">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="b193b-121">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b193b-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="b193b-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b193b-122">EXAMPLES</span></span>

### <span data-ttu-id="b193b-123">Exempel 1: generera ett standard transport alternativ</span><span class="sxs-lookup"><span data-stu-id="b193b-123">Example 1: Generate a default transport option</span></span>

```
PS C:\> New-PSTransportOption
ProcessIdleTimeoutSec           :
MaxIdleTimeoutSec               :
MaxSessions                     :
MaxConcurrentCommandsPerSession :
MaxSessionsPerUser              :
MaxMemoryPerSessionMB           :
MaxProcessesPerSession          :
MaxConcurrentUsers              :
IdleTimeoutSec                  :
OutputBufferingMode             :
```

<span data-ttu-id="b193b-124">Det här kommandot kör kommandot **New-PSTransportOption** utan parametrar.</span><span class="sxs-lookup"><span data-stu-id="b193b-124">This command runs the **New-PSTransportOption** without parameters.</span></span>
<span data-ttu-id="b193b-125">Utdata visar att cmdleten genererar ett transport alternativ objekt som har null-värden för alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="b193b-125">The output shows that the cmdlet generates a transport option object that has null values for all properties.</span></span>

### <span data-ttu-id="b193b-126">Exempel 2: hämta konfigurations alternativ för sessioner</span><span class="sxs-lookup"><span data-stu-id="b193b-126">Example 2: Get session configuration options</span></span>

```
The first command uses the **New-PSTransportOption** cmdlet to create a transport options object, which it saves in the $t variable. The command uses the *MaxSessions* parameter to increase the maximum number of sessions to 40.
PS C:\> $t = New-PSTransportOption -MaxSessions 40

The second command uses the **Register-PSSessionConfiguration** cmdlet create the ITTasks session configuration. The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.
PS C:\> Register-PSSessionConfiguration -Name ITTasks -TransportOption $t

The third command uses the Get-PSSessionConfiguration cmdlet to get the ITTasks session configurations and the Format-List cmdlet to display all of the properties of the session configuration object in a list. The output shows that the value of the **MaxShells** property of the session configuration is 40.
PS C:\> Get-PSSessionConfiguration -Name ITTasks | Format-List -Property *
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITTasks
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
MaxShells                     : 40
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 2
Name                          : ITTasks
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
Enabled                       : True
MaxShellsPerUser              : 25
Permission                    :
```

<span data-ttu-id="b193b-127">Det här exemplet visar hur du använder ett transport alternativ objekt för att ange konfigurations alternativ för sessioner.</span><span class="sxs-lookup"><span data-stu-id="b193b-127">This example shows how to use a transport options object to set session configuration options.</span></span>

### <span data-ttu-id="b193b-128">Exempel 3: Ange ett transport alternativ</span><span class="sxs-lookup"><span data-stu-id="b193b-128">Example 3: Setting a transport option</span></span>

```
The first command uses the **New-PSTransportOption** cmdlet to create a transport option object. The command uses the *IdleTimeoutSec* parameter to set the **IdleTimeoutSec** property value of the object to one hour (3600 seconds). The command saves the transport objects object in the $t variable.
PS C:\> $t = New-PSTransportOption -IdleTimeoutSec 3600

The second command uses the Set-PSSessionConfiguration cmdlet to change the transport options of the ITTasks session configuration. The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.
PS C:\> Set-PSSessionConfiguration -Name ITTasks -TransportOption $t

The third command uses the New-PSSession cmdlet to create the MyITTasks session on the local computer. The command uses the **ConfigurationName** property to specify the ITTasks session configuration. The command saves the session in the $s variable.Notice that the command does not use the *SessionOption* parameter of **New-PSSession** to set a custom idle time-out for the session. If it did, the idle time-out value set in the session option would take precedence over the idle time-out set in the session configuration.
PS C:\> $s = New-PSSession -Name MyITTasks -ConfigurationName ITTasks

The fourth command uses the Format-List cmdlet to display all properties of the session in the $s variable in a list. The output shows that the session has an idle time-out of one hour (360,000 milliseconds).
PS C:\> $s | Format-List -Property *
State                  : Opened
IdleTimeout            : 3600000
OutputBufferingMode    : Block
ComputerName           : localhost
ConfigurationName      : ITTasks
InstanceId             : 4110c3f5-68ea-40fa-9bbf-04a433dbb02d
Id                     : 1
Name                   : MyITTasks
Availability           : Available
ApplicationPrivateData : {PSVersionTable}
Runspace               : System.Management.Automation.RemoteRunspace
```

<span data-ttu-id="b193b-129">Det här kommandot visar resultatet av att ställa in ett transport alternativ i en sessionsinformation på de sessioner som använder-sessionen.</span><span class="sxs-lookup"><span data-stu-id="b193b-129">This command shows the effect of setting a transport option in a session configuration on the sessions that use the session configuration.</span></span>

## <span data-ttu-id="b193b-130">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b193b-130">PARAMETERS</span></span>

### <span data-ttu-id="b193b-131">-IdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="b193b-131">-IdleTimeoutSec</span></span>

<span data-ttu-id="b193b-132">Anger hur lång tid varje session förblir öppen om fjärrdatorn inte får någon kommunikation från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="b193b-132">Determines how long each session stays open if the remote computer does not receive any communication from the local computer.</span></span>
<span data-ttu-id="b193b-133">Detta inkluderar pulsslags signalen.</span><span class="sxs-lookup"><span data-stu-id="b193b-133">This includes the heartbeat signal.</span></span>
<span data-ttu-id="b193b-134">När intervallet går ut stängs sessionen.</span><span class="sxs-lookup"><span data-stu-id="b193b-134">When the interval expires, the session closes.</span></span>

<span data-ttu-id="b193b-135">Timeout-värdet för inaktivitet är av stor betydelse när användaren avser att koppla från och återansluta till en session.</span><span class="sxs-lookup"><span data-stu-id="b193b-135">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="b193b-136">Användaren kan bara återansluta om sessionen inte har nått sin tids gräns.</span><span class="sxs-lookup"><span data-stu-id="b193b-136">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="b193b-137">Parametern *IdleTimeoutSec* motsvarar **IdleTimeoutMs** -egenskapen för en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b193b-137">The *IdleTimeoutSec* parameter corresponds to the **IdleTimeoutMs** property of a session configuration.</span></span>

<span data-ttu-id="b193b-138">Ange ett värde i sekunder.</span><span class="sxs-lookup"><span data-stu-id="b193b-138">Enter a value in seconds.</span></span>
<span data-ttu-id="b193b-139">Standardvärdet är 7200 (2 timmar).</span><span class="sxs-lookup"><span data-stu-id="b193b-139">The default value is 7200 (2 hours).</span></span>
<span data-ttu-id="b193b-140">Det minsta värdet är 60 (1 minut).</span><span class="sxs-lookup"><span data-stu-id="b193b-140">The minimum value is 60 (1 minute).</span></span>
<span data-ttu-id="b193b-141">Det maximala värdet är värdet för egenskapen **idleTimeout** för gränssnitts objekt i WSMan-konfigurationen ( `WSMan:\\\<ComputerName\>\Shell\IdleTimeout` ).</span><span class="sxs-lookup"><span data-stu-id="b193b-141">The maximum is the value of the **IdleTimeout** property of Shell objects in the WSMan configuration (`WSMan:\\\<ComputerName\>\Shell\IdleTimeout`).</span></span>
<span data-ttu-id="b193b-142">Standardvärdet är 7200000 millisekunder (2 timmar).</span><span class="sxs-lookup"><span data-stu-id="b193b-142">The default value is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="b193b-143">Om ett tids gräns värde för inaktivitet anges i sessions-alternativen och i konfigurationen av sessionen, har värdet som anges i session alternativen företräde, men det får inte överskrida värdet för **MaxIdleTimeoutMs** -egenskapen i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="b193b-143">If an idle time-out value is set in the session options and in the session configuration, value set in the session options takes precedence, but it cannot exceed the value of the **MaxIdleTimeoutMs** property of the session configuration.</span></span>
<span data-ttu-id="b193b-144">Ange värdet för egenskapen **MaxIdleTimeoutMs** med parametern *MaxIdleTimeoutSec* .</span><span class="sxs-lookup"><span data-stu-id="b193b-144">To set the value of the **MaxIdleTimeoutMs** property, use the *MaxIdleTimeoutSec* parameter.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b193b-145">-MaxConcurrentCommandsPerSession</span><span class="sxs-lookup"><span data-stu-id="b193b-145">-MaxConcurrentCommandsPerSession</span></span>

<span data-ttu-id="b193b-146">Begränsar antalet kommandon som kan köras samtidigt i varje session till det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="b193b-146">Limits the number of commands that can run at the same time in each session to the specified value.</span></span>
<span data-ttu-id="b193b-147">Standardvärdet är 1000.</span><span class="sxs-lookup"><span data-stu-id="b193b-147">The default value is 1000.</span></span>

<span data-ttu-id="b193b-148">Parametern *MaxConcurrentCommandsPerSession* motsvarar **MaxConcurrentCommandsPerShell** -egenskapen för en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b193b-148">The *MaxConcurrentCommandsPerSession* parameter corresponds to the **MaxConcurrentCommandsPerShell** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b193b-149">-MaxConcurrentUsers</span><span class="sxs-lookup"><span data-stu-id="b193b-149">-MaxConcurrentUsers</span></span>

<span data-ttu-id="b193b-150">Begränsar antalet användare som kan köra kommandon på samma tid i varje session till det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="b193b-150">Limits the number of users who can run commands at the same time in each session to the specified value.</span></span>
<span data-ttu-id="b193b-151">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="b193b-151">The default value is 5.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b193b-152">-MaxIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="b193b-152">-MaxIdleTimeoutSec</span></span>

<span data-ttu-id="b193b-153">Begränsar tids gränsen för inaktivitet för varje session till det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="b193b-153">Limits the idle time-out set for each session to the specified value.</span></span>
<span data-ttu-id="b193b-154">Standardvärdet är \[ int \] :: MaxValue (~ 25 dagar).</span><span class="sxs-lookup"><span data-stu-id="b193b-154">The default value is \[Int\]::MaxValue (~25 days).</span></span>

<span data-ttu-id="b193b-155">Timeout-värdet för inaktivitet är av stor betydelse när användaren avser att koppla från och återansluta till en session.</span><span class="sxs-lookup"><span data-stu-id="b193b-155">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="b193b-156">Användaren kan bara återansluta om sessionen inte har nått sin tids gräns.</span><span class="sxs-lookup"><span data-stu-id="b193b-156">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="b193b-157">Parametern *MaxIdleTimeoutSec* motsvarar **MaxIdleTimeoutMs** -egenskapen för en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b193b-157">The *MaxIdleTimeoutSec* parameter corresponds to the **MaxIdleTimeoutMs** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b193b-158">-MaxMemoryPerSessionMB</span><span class="sxs-lookup"><span data-stu-id="b193b-158">-MaxMemoryPerSessionMB</span></span>

<span data-ttu-id="b193b-159">Begränsar det minne som används av varje session till det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="b193b-159">Limits the memory used by each session to the specified value.</span></span>
<span data-ttu-id="b193b-160">Ange ett värde i megabyte.</span><span class="sxs-lookup"><span data-stu-id="b193b-160">Enter a value in megabytes.</span></span>
<span data-ttu-id="b193b-161">Standardvärdet är 1024 megabyte (1 GB).</span><span class="sxs-lookup"><span data-stu-id="b193b-161">The default value is 1024 megabytes (1 GB).</span></span>

<span data-ttu-id="b193b-162">Parametern *MaxMemoryPerSessionMB* motsvarar **MaxMemoryPerShellMB** -egenskapen för en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b193b-162">The *MaxMemoryPerSessionMB* parameter corresponds to the **MaxMemoryPerShellMB** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b193b-163">-MaxProcessesPerSession</span><span class="sxs-lookup"><span data-stu-id="b193b-163">-MaxProcessesPerSession</span></span>

<span data-ttu-id="b193b-164">Begränsar antalet processer som körs i varje session till det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="b193b-164">Limits the number of processes running in each session to the specified value.</span></span>
<span data-ttu-id="b193b-165">Standardvärdet är 15.</span><span class="sxs-lookup"><span data-stu-id="b193b-165">The default value is 15.</span></span>

<span data-ttu-id="b193b-166">Parametern *MaxProcessesPerSession* motsvarar **MaxProcessesPerShell** -egenskapen för en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b193b-166">The *MaxProcessesPerSession* parameter corresponds to the **MaxProcessesPerShell** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b193b-167">-MaxSessions</span><span class="sxs-lookup"><span data-stu-id="b193b-167">-MaxSessions</span></span>

<span data-ttu-id="b193b-168">Begränsar antalet sessioner som använder-konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="b193b-168">Limits the number of sessions that use the session configuration.</span></span>
<span data-ttu-id="b193b-169">Standardvärdet är 25.</span><span class="sxs-lookup"><span data-stu-id="b193b-169">The default value is 25.</span></span>

<span data-ttu-id="b193b-170">Parametern *MaxSessions* motsvarar **MaxShells** -egenskapen för en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b193b-170">The *MaxSessions* parameter corresponds to the **MaxShells** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b193b-171">-MaxSessionsPerUser</span><span class="sxs-lookup"><span data-stu-id="b193b-171">-MaxSessionsPerUser</span></span>

<span data-ttu-id="b193b-172">Begränsar antalet sessioner som använder-konfigurationen av sessionen och körs med autentiseringsuppgifterna för en viss användare till det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="b193b-172">Limits the number of sessions that use the session configuration and run with the credentials of a given user to the specified value.</span></span>
<span data-ttu-id="b193b-173">Standardvärdet är 25.</span><span class="sxs-lookup"><span data-stu-id="b193b-173">The default value is 25.</span></span>

<span data-ttu-id="b193b-174">När du anger det här värdet bör du tänka på att många användare kan använda autentiseringsuppgifterna för en kör som-användare.</span><span class="sxs-lookup"><span data-stu-id="b193b-174">When you specify this value, consider that many users might be using the credentials of a run as user.</span></span>

<span data-ttu-id="b193b-175">Parametern *MaxSessionsPerUser* motsvarar **MaxShellsPerUser** -egenskapen för en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b193b-175">The *MaxSessionsPerUser* parameter corresponds to the **MaxShellsPerUser** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b193b-176">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="b193b-176">-OutputBufferingMode</span></span>

<span data-ttu-id="b193b-177">Anger hur kommandoutdata hanteras i frånkopplade sessioner när utdatabufferten blir full.</span><span class="sxs-lookup"><span data-stu-id="b193b-177">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>
<span data-ttu-id="b193b-178">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="b193b-178">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b193b-179">Undantaget.</span><span class="sxs-lookup"><span data-stu-id="b193b-179">Block.</span></span>
<span data-ttu-id="b193b-180">När utdatabufferten är full pausas körningen tills bufferten är klar.</span><span class="sxs-lookup"><span data-stu-id="b193b-180">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="b193b-181">Skugg.</span><span class="sxs-lookup"><span data-stu-id="b193b-181">Drop.</span></span>
<span data-ttu-id="b193b-182">När utdatabufferten är full fortsätter körningen.</span><span class="sxs-lookup"><span data-stu-id="b193b-182">When the output buffer is full, execution continues.</span></span>
<span data-ttu-id="b193b-183">När nya utdata sparas, ignoreras det äldsta resultatet.</span><span class="sxs-lookup"><span data-stu-id="b193b-183">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="b193b-184">Inga.</span><span class="sxs-lookup"><span data-stu-id="b193b-184">None.</span></span>
<span data-ttu-id="b193b-185">Inget utdata buffer-läge har angetts.</span><span class="sxs-lookup"><span data-stu-id="b193b-185">No output buffering mode is specified.</span></span>

<span data-ttu-id="b193b-186">Standardvärdet för egenskapen **OutputBufferingMode** för sessioner är blockera.</span><span class="sxs-lookup"><span data-stu-id="b193b-186">The default value of the **OutputBufferingMode** property of sessions is Block.</span></span>

```yaml
Type: System.Nullable`1[System.Management.Automation.Runspaces.OutputBufferingMode]
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b193b-187">-ProcessIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="b193b-187">-ProcessIdleTimeoutSec</span></span>

<span data-ttu-id="b193b-188">Begränsar tids gränsen för varje värd process till det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="b193b-188">Limits the time-out for each host process to the specified value.</span></span>
<span data-ttu-id="b193b-189">Standardvärdet är 0, vilket innebär att det inte finns något timeout-värde för processen.</span><span class="sxs-lookup"><span data-stu-id="b193b-189">The default value, 0, means that there is no time-out value for the process.</span></span>

<span data-ttu-id="b193b-190">Andra sessionsdata har timeout-värden per process.</span><span class="sxs-lookup"><span data-stu-id="b193b-190">Other session configurations have per-process time-out values.</span></span>
<span data-ttu-id="b193b-191">Konfigurationen för **Microsoft. PowerShell. Workflow** -sessionen har till exempel ett tids gräns värde för per process på 28800 sekunder (8 timmar).</span><span class="sxs-lookup"><span data-stu-id="b193b-191">For example, the **Microsoft.PowerShell.Workflow** session configuration has a per-process time-out value of 28800 seconds (8 hours).</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b193b-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b193b-192">CommonParameters</span></span>
<span data-ttu-id="b193b-193">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b193b-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b193b-194">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b193b-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b193b-195">INDATA</span><span class="sxs-lookup"><span data-stu-id="b193b-195">INPUTS</span></span>

### <span data-ttu-id="b193b-196">Inget</span><span class="sxs-lookup"><span data-stu-id="b193b-196">None</span></span>

<span data-ttu-id="b193b-197">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b193b-197">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b193b-198">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b193b-198">OUTPUTS</span></span>

### <span data-ttu-id="b193b-199">Microsoft. PowerShell. commands. WSManConfigurationOption</span><span class="sxs-lookup"><span data-stu-id="b193b-199">Microsoft.PowerShell.Commands.WSManConfigurationOption</span></span>

## <span data-ttu-id="b193b-200">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b193b-200">NOTES</span></span>

- <span data-ttu-id="b193b-201">Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ.</span><span class="sxs-lookup"><span data-stu-id="b193b-201">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="b193b-202">Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.</span><span class="sxs-lookup"><span data-stu-id="b193b-202">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="b193b-203">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b193b-203">RELATED LINKS</span></span>

[<span data-ttu-id="b193b-204">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="b193b-204">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="b193b-205">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="b193b-205">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="b193b-206">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b193b-206">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="b193b-207">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b193b-207">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)
