---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowexecutionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowExecutionOption
ms.openlocfilehash: db5d19396f555a41ad14552823c57f3b11c79321
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268251"
---
# <span data-ttu-id="6bc12-103">New-PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="6bc12-103">New-PSWorkflowExecutionOption</span></span>

## <span data-ttu-id="6bc12-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6bc12-104">SYNOPSIS</span></span>

<span data-ttu-id="6bc12-105">Skapar ett objekt som innehåller konfigurations alternativ för sessioner för arbets flödes sessioner.</span><span class="sxs-lookup"><span data-stu-id="6bc12-105">Creates an object that contains session configuration options for workflow sessions.</span></span>

## <span data-ttu-id="6bc12-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6bc12-106">SYNTAX</span></span>

```
New-PSWorkflowExecutionOption [-PersistencePath <String>] [-MaxPersistenceStoreSizeGB <Int64>]
 [-PersistWithEncryption] [-MaxRunningWorkflows <Int32>] [-AllowedActivity <String[]>]
 [-OutOfProcessActivity <String[]>] [-EnableValidation] [-MaxDisconnectedSessions <Int32>]
 [-MaxConnectedSessions <Int32>] [-MaxSessionsPerWorkflow <Int32>] [-MaxSessionsPerRemoteNode <Int32>]
 [-MaxActivityProcesses <Int32>] [-ActivityProcessIdleTimeoutSec <Int32>]
 [-RemoteNodeSessionIdleTimeoutSec <Int32>] [-SessionThrottleLimit <Int32>]
 [-WorkflowShutdownTimeoutMSec <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="6bc12-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6bc12-107">DESCRIPTION</span></span>

<span data-ttu-id="6bc12-108">`New-PSWorkflowExecutionOption`Cmdlet: en skapar ett objekt som innehåller avancerade alternativ för konfigurationer av arbetsflödeskonfigurationer, som är utformade för att köra arbets flöden för Windows PowerShell-arbetsflöden.</span><span class="sxs-lookup"><span data-stu-id="6bc12-108">The `New-PSWorkflowExecutionOption` cmdlet creates an object that contains advanced options for workflow session configurations, that is session configurations designed to run Windows PowerShell Workflow workflows.</span></span>

<span data-ttu-id="6bc12-109">Du kan använda **PSWorkflowExecutionOption** -objektet som `New-PSWorkflowExecutionOption` genererar som värdet för parametern **SessionTypeOption** för cmdletar som skapar eller ändrar en sessionsinformation, till exempel `Register-PSSessionConfiguration` `Set-PSSessionConfiguration` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="6bc12-109">You can use the **PSWorkflowExecutionOption** object that `New-PSWorkflowExecutionOption` generates as the value of the **SessionTypeOption** parameter of cmdlets that create or change a session configuration, such as the `Register-PSSessionConfiguration` and `Set-PSSessionConfiguration` cmdlets.</span></span>

<span data-ttu-id="6bc12-110">Varje parameter i `New-PSWorkflowExecutionOption` cmdleten representerar en egenskap i objektet konfigurations alternativ för arbets flödes session som cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="6bc12-110">Each parameter of the `New-PSWorkflowExecutionOption` cmdlet represents a property of the workflow session configuration option object that the cmdlet returns.</span></span> <span data-ttu-id="6bc12-111">Om du utelämnar en parameter skapar cmdleten objektet med ett standardvärde för egenskapen.</span><span class="sxs-lookup"><span data-stu-id="6bc12-111">If you omit a parameter, the cmdlet creates the object with a default value for the property.</span></span>

<span data-ttu-id="6bc12-112">`New-PSWorkflowExecutionOption`Cmdleten är en del av arbets flödes funktionen i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bc12-112">The `New-PSWorkflowExecutionOption` cmdlet is part of the Windows PowerShell Workflow feature.</span></span>

<span data-ttu-id="6bc12-113">Du kan också lägga till gemensamma parametrar för arbets flöden i det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="6bc12-113">You can also add workflow common parameters to this command.</span></span> <span data-ttu-id="6bc12-114">Mer information om gemensamma parametrar för arbets flöden finns i [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="6bc12-114">For more information about workflow common parameters, see [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md).</span></span>

<span data-ttu-id="6bc12-115">Denna cmdlet introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6bc12-115">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="6bc12-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6bc12-116">EXAMPLES</span></span>

### <span data-ttu-id="6bc12-117">Exempel 1: skapa ett objekt för arbets flödes alternativ</span><span class="sxs-lookup"><span data-stu-id="6bc12-117">Example 1: Create a Workflow Options Object</span></span>

```powershell
New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
```

```Output
SessionThrottleLimit                       : 100
PersistencePath                            : C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell\WF\PS
MaxPersistenceStoreSizeGB                  : 10
PersistWithEncryption                      : False
MaxRunningWorkflows                        : 30
AllowedActivity                            : {PSDefaultActivities}
OutOfProcessActivity                       : {InlineScript}
EnableValidation                           : True
MaxDisconnectedSessions                    : 200
MaxConnectedSessions                       : 100
MaxSessionsPerWorkflow                     : 10
MaxSessionsPerRemoteNode                   : 5
MaxActivityProcesses                       : 5
ActivityProcessIdleTimeoutSec              : 60
RemoteNodeSessionIdleTimeoutSec            : 60
WorkflowShutdownTimeoutMSec                : 500
```

<span data-ttu-id="6bc12-118">Det här kommandot använder `New-PSWorkflowExecutionOption` cmdleten för att öka **MaxSessionsPerWorkflow** -värdet till 10 och minska **MaxDisconnectedSessions** -värdet till 200.</span><span class="sxs-lookup"><span data-stu-id="6bc12-118">This command uses the `New-PSWorkflowExecutionOption` cmdlet to increase the **MaxSessionsPerWorkflow** value to 10 and decrease the **MaxDisconnectedSessions** value to 200.</span></span>

<span data-ttu-id="6bc12-119">Utdata visar objektet som cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="6bc12-119">The output shows the object that the cmdlet returns.</span></span>

### <span data-ttu-id="6bc12-120">Exempel 2: använda ett objekt för arbets flödes alternativ</span><span class="sxs-lookup"><span data-stu-id="6bc12-120">Example 2: Using a Workflow Options Object</span></span>

```powershell
# Create a Workflow Options object and save it in a variable
$wo = New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
# Create the ITWorkflow session configuration
Register-PSSessionConfiguration -Name ITWorkflows -SessionTypeOption $wo -Force
```

```Output
    WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=ITWorkflows}                  ITWorkflows
```

```powershell
Get-PSSessionConfiguration ITWorkflows | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITWorkflows
MaxConcurrentCommandsPerShell : 1000
allowedactivity               : PSDefaultActivities
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
maxsessionsperworkflow        : 10
lang                          : en-US
sessionconfigurationdata      : <SessionConfigurationData>
                                    <Param Name='PrivateData'>
                                        <PrivateData>
                                            <ParamName='enablevalidation' Value='True'/>
                                            <Param Name='allowedactivity'Value='PSDefaultActivities' />
                                            <Param Name='outofprocessactivity' Value='InlineScript'/>
                                            <Param Name='maxdisconnectedsessions' Value='200' />
                                            <ParamName='maxsessionsperworkflow' Value='10'/>
                                        </PrivateData>
                                    </Param>
                                </SessionConfigurationData>
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 25
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
outofprocessactivity          : InlineScript
SDKVersion                    : 2
Name                          : ITWorkflows
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
enablevalidation              : True
Enabled                       : True
maxdisconnectedsessions       : 200
MaxShellsPerUser              : 25
Permission                    :
```

<span data-ttu-id="6bc12-121">De två första kommandona skapar ett nytt konfigurations objekt för sessionen och registrerar det.</span><span class="sxs-lookup"><span data-stu-id="6bc12-121">The first two commands create a new session configuration object and registers it.</span></span>

<span data-ttu-id="6bc12-122">Det tredje kommandot använder `Get-PSSessionConfiguration` cmdleten för att hämta ITWorkflows och `Format-List` för att visa alla egenskaper för sessionen i en lista. Utdata visar att arbets flödes alternativen i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6bc12-122">The third command uses the `Get-PSSessionConfiguration` cmdlet to the get the ITWorkflows session configuration and the `Format-List` to display all properties of the session configuration in a list.The output shows that the workflow options in the session configuration.</span></span> <span data-ttu-id="6bc12-123">Mer specifikt har sessionens konfiguration en **MaxSessionsPerWorkflow** -egenskap med värdet 10 och en **MaxDisconnectedSessions** -egenskap med värdet 200.</span><span class="sxs-lookup"><span data-stu-id="6bc12-123">Specifically, the session configuration has a **MaxSessionsPerWorkflow** property with a value of 10 and a **MaxDisconnectedSessions** property with a value of 200.</span></span>

## <span data-ttu-id="6bc12-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6bc12-124">PARAMETERS</span></span>

### <span data-ttu-id="6bc12-125">-ActivityProcessIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="6bc12-125">-ActivityProcessIdleTimeoutSec</span></span>

<span data-ttu-id="6bc12-126">Anger hur lång tid varje aktivitets värd process underhålls när processen blir inaktiv.</span><span class="sxs-lookup"><span data-stu-id="6bc12-126">Determines how long each activity host process is maintained after the process becomes idle.</span></span> <span data-ttu-id="6bc12-127">När intervallet går ut stängs processen.</span><span class="sxs-lookup"><span data-stu-id="6bc12-127">When the interval expires, the process closes.</span></span>

<span data-ttu-id="6bc12-128">Ange ett värde i sekunder.</span><span class="sxs-lookup"><span data-stu-id="6bc12-128">Enter a value in seconds.</span></span> <span data-ttu-id="6bc12-129">Standardvärdet är 60.</span><span class="sxs-lookup"><span data-stu-id="6bc12-129">The default value is 60.</span></span>

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

### <span data-ttu-id="6bc12-130">-AllowedActivity</span><span class="sxs-lookup"><span data-stu-id="6bc12-130">-AllowedActivity</span></span>

<span data-ttu-id="6bc12-131">Anger de aktiviteter som tillåts att köras i sessionen.</span><span class="sxs-lookup"><span data-stu-id="6bc12-131">Specifies the activities that are permitted to run in the session.</span></span>

<span data-ttu-id="6bc12-132">Ange namn på namn område – kvalificerade aktiviteter, till exempel `Microsoft.Powershell.HyperV.Activities.*` .</span><span class="sxs-lookup"><span data-stu-id="6bc12-132">Enter namespace-qualified activity names, such as `Microsoft.Powershell.HyperV.Activities.*`.</span></span>
<span data-ttu-id="6bc12-133">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="6bc12-133">Wildcard characters are supported.</span></span> <span data-ttu-id="6bc12-134">Standardvärdet, **PSDefaultActivities** , innehåller inbyggda Windows Workflow Foundation aktiviteter och de aktiviteter som representerar Windows PowerShell Core-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="6bc12-134">The default value, **PSDefaultActivities** , includes the built-in Windows Workflow Foundation activities and the activities that represent the Windows PowerShell Core cmdlets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: PSDefaultActivities
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc12-135">-EnableValidation</span><span class="sxs-lookup"><span data-stu-id="6bc12-135">-EnableValidation</span></span>

<span data-ttu-id="6bc12-136">Verifierar att alla arbets flödes aktiviteter i sessionen ingår i listan över tillåtna aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="6bc12-136">Verifies that all workflow activities in the session are included in the allowed activities list.</span></span>

<span data-ttu-id="6bc12-137">Standardvärdet är true.</span><span class="sxs-lookup"><span data-stu-id="6bc12-137">The default value is True.</span></span> <span data-ttu-id="6bc12-138">Om du vill inaktivera verifiering använder du följande kommando format: `-EnableValidation:$false` .</span><span class="sxs-lookup"><span data-stu-id="6bc12-138">To disable validation, use the following command format: `-EnableValidation:$false`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc12-139">-MaxActivityProcesses</span><span class="sxs-lookup"><span data-stu-id="6bc12-139">-MaxActivityProcesses</span></span>

<span data-ttu-id="6bc12-140">Anger det maximala antalet processer som kan skapas i sessionen för att stödja arbets flödes aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="6bc12-140">Specifies the maximum number of processes that can be created in the session to support workflow activities.</span></span> <span data-ttu-id="6bc12-141">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="6bc12-141">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc12-142">-MaxConnectedSessions</span><span class="sxs-lookup"><span data-stu-id="6bc12-142">-MaxConnectedSessions</span></span>

<span data-ttu-id="6bc12-143">Anger det maximala antalet fjärrsessioner som är i drifts läge.</span><span class="sxs-lookup"><span data-stu-id="6bc12-143">Specifies the maximum number of remote sessions that are in an operational state.</span></span> <span data-ttu-id="6bc12-144">Den här kvoten tillämpas på sessioner som är anslutna till alla fjärrnoder (mål datorer).</span><span class="sxs-lookup"><span data-stu-id="6bc12-144">This quota is applied to sessions connected to all remote nodes (target computers).</span></span> <span data-ttu-id="6bc12-145">Standardvärdet är 100.</span><span class="sxs-lookup"><span data-stu-id="6bc12-145">The default value is 100.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc12-146">-MaxDisconnectedSessions</span><span class="sxs-lookup"><span data-stu-id="6bc12-146">-MaxDisconnectedSessions</span></span>

<span data-ttu-id="6bc12-147">Anger det maximala antalet fjärrsessioner som är i frånkopplat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="6bc12-147">Specifies the maximum number of remote sessions that are in a disconnected state.</span></span> <span data-ttu-id="6bc12-148">Den här kvoten tillämpas på sessioner som är anslutna till alla fjärrnoder (mål datorer).</span><span class="sxs-lookup"><span data-stu-id="6bc12-148">This quota is applied to sessions connected to all remote nodes (target computers).</span></span> <span data-ttu-id="6bc12-149">Standardvärdet är 1000.</span><span class="sxs-lookup"><span data-stu-id="6bc12-149">The default value is 1000.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1000
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc12-150">-MaxPersistenceStoreSizeGB</span><span class="sxs-lookup"><span data-stu-id="6bc12-150">-MaxPersistenceStoreSizeGB</span></span>

<span data-ttu-id="6bc12-151">Anger maximal storlek i GB för det beständiga arkiv som allokerats till arbets flöden som körs i sessionen.</span><span class="sxs-lookup"><span data-stu-id="6bc12-151">Specifies the maximum size, in gigabytes, of the persistence store allocated to workflows that run in the session.</span></span> <span data-ttu-id="6bc12-152">När storleken har överskridits expanderas det beständiga arkivet för att spara alla sparade data, men en varning visas och ett meddelande skrivs till händelse loggen för arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="6bc12-152">When the size is exceeded, the persistence store is expanded to save all persisted data, but a warning is displayed and a message is written to the workflow event log.</span></span> <span data-ttu-id="6bc12-153">Standardvärdet är 10.</span><span class="sxs-lookup"><span data-stu-id="6bc12-153">The default value is 10.</span></span>

<span data-ttu-id="6bc12-154">Det beständiga arkivet innehåller data för alla arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="6bc12-154">The persistence store contains data for all workflow jobs.</span></span> <span data-ttu-id="6bc12-155">Möjligheten att lagra data tillåter att jobb återupptas utan att förlora tillstånd.</span><span class="sxs-lookup"><span data-stu-id="6bc12-155">The ability to store data allows the jobs to resume without losing state.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc12-156">-MaxRunningWorkflows</span><span class="sxs-lookup"><span data-stu-id="6bc12-156">-MaxRunningWorkflows</span></span>

<span data-ttu-id="6bc12-157">Anger att maximalt antal arbets flöden som kan köras i sessionen samtidigt.</span><span class="sxs-lookup"><span data-stu-id="6bc12-157">Specifies that maximum number of workflows that can run in the session concurrently.</span></span>
<span data-ttu-id="6bc12-158">Standardvärdet är 30.</span><span class="sxs-lookup"><span data-stu-id="6bc12-158">The default value is 30.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 30
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc12-159">-MaxSessionsPerRemoteNode</span><span class="sxs-lookup"><span data-stu-id="6bc12-159">-MaxSessionsPerRemoteNode</span></span>

<span data-ttu-id="6bc12-160">Anger det maximala antalet sessioner som kan anslutas till varje fjärrnod (måldator).</span><span class="sxs-lookup"><span data-stu-id="6bc12-160">Specifies the maximum number of sessions that can be connected to each remote node (target computer).</span></span> <span data-ttu-id="6bc12-161">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="6bc12-161">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc12-162">-MaxSessionsPerWorkflow</span><span class="sxs-lookup"><span data-stu-id="6bc12-162">-MaxSessionsPerWorkflow</span></span>

<span data-ttu-id="6bc12-163">Anger det maximala antalet sessioner som kan skapas för att stödja varje arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="6bc12-163">Specifies the maximum number of session that can be created to support each workflow.</span></span> <span data-ttu-id="6bc12-164">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="6bc12-164">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc12-165">– OutOfProcessActivity</span><span class="sxs-lookup"><span data-stu-id="6bc12-165">-OutOfProcessActivity</span></span>

<span data-ttu-id="6bc12-166">Bestämmer vilka tillåtna aktiviteter (som anges av parametern **AllowedActivities** ) som körs utanför processen.</span><span class="sxs-lookup"><span data-stu-id="6bc12-166">Determines which allowed activities (specified by the **AllowedActivities** parameter) run out-of-process.</span></span> <span data-ttu-id="6bc12-167">Standardvärdet är **InlineScript**.</span><span class="sxs-lookup"><span data-stu-id="6bc12-167">The default value is **InlineScript**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: InlineScript
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc12-168">-PersistencePath</span><span class="sxs-lookup"><span data-stu-id="6bc12-168">-PersistencePath</span></span>

<span data-ttu-id="6bc12-169">Anger platsen för den disk där arbets flödets tillstånd och data lagras.</span><span class="sxs-lookup"><span data-stu-id="6bc12-169">Specifies the location on disk where workflow state and data are stored.</span></span> <span data-ttu-id="6bc12-170">Lagring av arbets flödets tillstånd och data gör att arbets flöden kan pausas och återupptas och återställas efter avbrott och nätverks fel.</span><span class="sxs-lookup"><span data-stu-id="6bc12-170">Storing the workflow state and data allows workflows to be suspended and resumed, and to recover from interruptions and network failures.</span></span>

<span data-ttu-id="6bc12-171">Standardvärdet är `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`.</span><span class="sxs-lookup"><span data-stu-id="6bc12-171">The default value is `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc12-172">-PersistWithEncryption</span><span class="sxs-lookup"><span data-stu-id="6bc12-172">-PersistWithEncryption</span></span>

<span data-ttu-id="6bc12-173">Anger att arbets flödet krypterar data i det beständiga arkivet.</span><span class="sxs-lookup"><span data-stu-id="6bc12-173">Indicates that the workflow encrypts the data in the persistence store.</span></span> <span data-ttu-id="6bc12-174">Överväg att använda den här funktionen när du lagrar beständiga data i en nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="6bc12-174">Consider using this feature when storing persistence data in a network share.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc12-175">-RemoteNodeSessionIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="6bc12-175">-RemoteNodeSessionIdleTimeoutSec</span></span>

<span data-ttu-id="6bc12-176">Anger hur länge en session som är ansluten till en fjärrnod (måldator) upprätthålls om den är inaktiv.</span><span class="sxs-lookup"><span data-stu-id="6bc12-176">Specifies how long a session that is connected to a remote node (target computer) is maintained if it is idle.</span></span>

<span data-ttu-id="6bc12-177">Ange ett värde i sekunder.</span><span class="sxs-lookup"><span data-stu-id="6bc12-177">Enter a value in seconds.</span></span> <span data-ttu-id="6bc12-178">Standardvärdet är 60.</span><span class="sxs-lookup"><span data-stu-id="6bc12-178">The default value is 60.</span></span>

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

### <span data-ttu-id="6bc12-179">-SessionThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6bc12-179">-SessionThrottleLimit</span></span>

<span data-ttu-id="6bc12-180">Anger hur många åtgärder som har skapats för att stödja alla arbets flöden som startats i sessionen.</span><span class="sxs-lookup"><span data-stu-id="6bc12-180">Specifies how many operations are created to support all workflows started in the session.</span></span> <span data-ttu-id="6bc12-181">Standardvärdet är 100.</span><span class="sxs-lookup"><span data-stu-id="6bc12-181">The default value is 100.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc12-182">-WorkflowShutdownTimeoutMSec</span><span class="sxs-lookup"><span data-stu-id="6bc12-182">-WorkflowShutdownTimeoutMSec</span></span>

<span data-ttu-id="6bc12-183">Anger hur länge sessionen upprätthålls efter att alla arbets flöden i sessionen har upphört att gälla.</span><span class="sxs-lookup"><span data-stu-id="6bc12-183">Specifies how long the session is maintained after all workflows in the session are forcibly suspended.</span></span> <span data-ttu-id="6bc12-184">När tids gränsen går ut stängs sessionen i Windows PowerShell, även om alla arbets flöden ännu inte har pausats.</span><span class="sxs-lookup"><span data-stu-id="6bc12-184">When the timeout expires, Windows PowerShell closes the session, even if all workflows are not yet suspended.</span></span>

<span data-ttu-id="6bc12-185">Ange ett värde i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="6bc12-185">Enter a value in milliseconds.</span></span>
<span data-ttu-id="6bc12-186">Standardvärdet är 500.</span><span class="sxs-lookup"><span data-stu-id="6bc12-186">The default value is 500.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 500
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc12-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6bc12-187">CommonParameters</span></span>

<span data-ttu-id="6bc12-188">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6bc12-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6bc12-189">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="6bc12-189">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6bc12-190">INDATA</span><span class="sxs-lookup"><span data-stu-id="6bc12-190">INPUTS</span></span>

### <span data-ttu-id="6bc12-191">Inget</span><span class="sxs-lookup"><span data-stu-id="6bc12-191">None</span></span>

<span data-ttu-id="6bc12-192">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6bc12-192">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="6bc12-193">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6bc12-193">OUTPUTS</span></span>

### <span data-ttu-id="6bc12-194">Microsoft. PowerShell. commands. PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="6bc12-194">Microsoft.PowerShell.Commands.PSWorkflowExecutionOption</span></span>

## <span data-ttu-id="6bc12-195">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6bc12-195">NOTES</span></span>

<span data-ttu-id="6bc12-196">När det maximala värdet som anges av ett alternativ överskrids, Miss lyckas kommandot för att skapa en annan instans i sessionen, om inget annat anges i parameter beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="6bc12-196">When the maximum value set by an option is exceeded, the command to create another instance in the session fails, unless noted in the parameter description.</span></span> <span data-ttu-id="6bc12-197">Om värdet för **MaxConnectedSessions** till exempel är 100.</span><span class="sxs-lookup"><span data-stu-id="6bc12-197">For example, if the value of **MaxConnectedSessions** is 100.</span></span> <span data-ttu-id="6bc12-198">Kommandot för att skapa 101st-sessionen till en fjärrnod (måldator) Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="6bc12-198">The command to create the 101st session to a remote node (target computer) fails.</span></span>

<span data-ttu-id="6bc12-199">Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ.</span><span class="sxs-lookup"><span data-stu-id="6bc12-199">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="6bc12-200">Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.</span><span class="sxs-lookup"><span data-stu-id="6bc12-200">Also, session configurations that use a session configuration file have additional properties.</span></span>

<span data-ttu-id="6bc12-201">Dessutom varierar egenskaperna för de sessionsinställningar som innehåller ett **PSWorkflowExecutionOptions** -objekt baserat på alternativ värden för arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="6bc12-201">In particular, the properties of session configurations that include a **PSWorkflowExecutionOptions** object vary based on the workflow option values.</span></span> <span data-ttu-id="6bc12-202">Om konfigurationen till exempel innehåller ett **PSWorkflowExecutionOptions** -objekt som anger ett värde som inte är standardvärdet för egenskapen **SessionThrottleLimit** , har sessionens konfiguration en **SessionThrottleLimit** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="6bc12-202">For example, if the session configuration includes a **PSWorkflowExecutionOptions** object that sets a non-default value for the **SessionThrottleLimit** property, the session configuration has a **SessionThrottleLimit** property.</span></span> <span data-ttu-id="6bc12-203">Annars är det inte.</span><span class="sxs-lookup"><span data-stu-id="6bc12-203">Otherwise, it does not.</span></span>

## <span data-ttu-id="6bc12-204">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6bc12-204">RELATED LINKS</span></span>

[<span data-ttu-id="6bc12-205">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="6bc12-205">New-PSWorkflowSession</span></span>](New-PSWorkflowSession.md)

[<span data-ttu-id="6bc12-206">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="6bc12-206">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="6bc12-207">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="6bc12-207">about_WorkflowCommonParameters</span></span>](About/about_WorkflowCommonParameters.md)
