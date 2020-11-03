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
# New-PSWorkflowExecutionOption

## SAMMANFATTNING

Skapar ett objekt som innehåller konfigurations alternativ för sessioner för arbets flödes sessioner.

## SYNTAX

```
New-PSWorkflowExecutionOption [-PersistencePath <String>] [-MaxPersistenceStoreSizeGB <Int64>]
 [-PersistWithEncryption] [-MaxRunningWorkflows <Int32>] [-AllowedActivity <String[]>]
 [-OutOfProcessActivity <String[]>] [-EnableValidation] [-MaxDisconnectedSessions <Int32>]
 [-MaxConnectedSessions <Int32>] [-MaxSessionsPerWorkflow <Int32>] [-MaxSessionsPerRemoteNode <Int32>]
 [-MaxActivityProcesses <Int32>] [-ActivityProcessIdleTimeoutSec <Int32>]
 [-RemoteNodeSessionIdleTimeoutSec <Int32>] [-SessionThrottleLimit <Int32>]
 [-WorkflowShutdownTimeoutMSec <Int32>] [<CommonParameters>]
```

## BESKRIVNING

`New-PSWorkflowExecutionOption`Cmdlet: en skapar ett objekt som innehåller avancerade alternativ för konfigurationer av arbetsflödeskonfigurationer, som är utformade för att köra arbets flöden för Windows PowerShell-arbetsflöden.

Du kan använda **PSWorkflowExecutionOption** -objektet som `New-PSWorkflowExecutionOption` genererar som värdet för parametern **SessionTypeOption** för cmdletar som skapar eller ändrar en sessionsinformation, till exempel `Register-PSSessionConfiguration` `Set-PSSessionConfiguration` cmdletarna och.

Varje parameter i `New-PSWorkflowExecutionOption` cmdleten representerar en egenskap i objektet konfigurations alternativ för arbets flödes session som cmdleten returnerar. Om du utelämnar en parameter skapar cmdleten objektet med ett standardvärde för egenskapen.

`New-PSWorkflowExecutionOption`Cmdleten är en del av arbets flödes funktionen i Windows PowerShell.

Du kan också lägga till gemensamma parametrar för arbets flöden i det här kommandot. Mer information om gemensamma parametrar för arbets flöden finns i [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md).

Denna cmdlet introduceras i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: skapa ett objekt för arbets flödes alternativ

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

Det här kommandot använder `New-PSWorkflowExecutionOption` cmdleten för att öka **MaxSessionsPerWorkflow** -värdet till 10 och minska **MaxDisconnectedSessions** -värdet till 200.

Utdata visar objektet som cmdleten returnerar.

### Exempel 2: använda ett objekt för arbets flödes alternativ

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

De två första kommandona skapar ett nytt konfigurations objekt för sessionen och registrerar det.

Det tredje kommandot använder `Get-PSSessionConfiguration` cmdleten för att hämta ITWorkflows och `Format-List` för att visa alla egenskaper för sessionen i en lista. Utdata visar att arbets flödes alternativen i konfigurationen för sessionen. Mer specifikt har sessionens konfiguration en **MaxSessionsPerWorkflow** -egenskap med värdet 10 och en **MaxDisconnectedSessions** -egenskap med värdet 200.

## PARAMETRAR

### -ActivityProcessIdleTimeoutSec

Anger hur lång tid varje aktivitets värd process underhålls när processen blir inaktiv. När intervallet går ut stängs processen.

Ange ett värde i sekunder. Standardvärdet är 60.

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

### -AllowedActivity

Anger de aktiviteter som tillåts att köras i sessionen.

Ange namn på namn område – kvalificerade aktiviteter, till exempel `Microsoft.Powershell.HyperV.Activities.*` .
Jokertecken stöds. Standardvärdet, **PSDefaultActivities** , innehåller inbyggda Windows Workflow Foundation aktiviteter och de aktiviteter som representerar Windows PowerShell Core-cmdletar.

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

### -EnableValidation

Verifierar att alla arbets flödes aktiviteter i sessionen ingår i listan över tillåtna aktiviteter.

Standardvärdet är true. Om du vill inaktivera verifiering använder du följande kommando format: `-EnableValidation:$false` .

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

### -MaxActivityProcesses

Anger det maximala antalet processer som kan skapas i sessionen för att stödja arbets flödes aktiviteter. Standardvärdet är 5.

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

### -MaxConnectedSessions

Anger det maximala antalet fjärrsessioner som är i drifts läge. Den här kvoten tillämpas på sessioner som är anslutna till alla fjärrnoder (mål datorer). Standardvärdet är 100.

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

### -MaxDisconnectedSessions

Anger det maximala antalet fjärrsessioner som är i frånkopplat tillstånd. Den här kvoten tillämpas på sessioner som är anslutna till alla fjärrnoder (mål datorer). Standardvärdet är 1000.

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

### -MaxPersistenceStoreSizeGB

Anger maximal storlek i GB för det beständiga arkiv som allokerats till arbets flöden som körs i sessionen. När storleken har överskridits expanderas det beständiga arkivet för att spara alla sparade data, men en varning visas och ett meddelande skrivs till händelse loggen för arbets flödet. Standardvärdet är 10.

Det beständiga arkivet innehåller data för alla arbets flödes jobb. Möjligheten att lagra data tillåter att jobb återupptas utan att förlora tillstånd.

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

### -MaxRunningWorkflows

Anger att maximalt antal arbets flöden som kan köras i sessionen samtidigt.
Standardvärdet är 30.

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

### -MaxSessionsPerRemoteNode

Anger det maximala antalet sessioner som kan anslutas till varje fjärrnod (måldator). Standardvärdet är 5.

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

### -MaxSessionsPerWorkflow

Anger det maximala antalet sessioner som kan skapas för att stödja varje arbets flöde. Standardvärdet är 5.

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

### – OutOfProcessActivity

Bestämmer vilka tillåtna aktiviteter (som anges av parametern **AllowedActivities** ) som körs utanför processen. Standardvärdet är **InlineScript**.

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

### -PersistencePath

Anger platsen för den disk där arbets flödets tillstånd och data lagras. Lagring av arbets flödets tillstånd och data gör att arbets flöden kan pausas och återupptas och återställas efter avbrott och nätverks fel.

Standardvärdet är `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`.

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

### -PersistWithEncryption

Anger att arbets flödet krypterar data i det beständiga arkivet. Överväg att använda den här funktionen när du lagrar beständiga data i en nätverks resurs.

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

### -RemoteNodeSessionIdleTimeoutSec

Anger hur länge en session som är ansluten till en fjärrnod (måldator) upprätthålls om den är inaktiv.

Ange ett värde i sekunder. Standardvärdet är 60.

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

### -SessionThrottleLimit

Anger hur många åtgärder som har skapats för att stödja alla arbets flöden som startats i sessionen. Standardvärdet är 100.

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

### -WorkflowShutdownTimeoutMSec

Anger hur länge sessionen upprätthålls efter att alla arbets flöden i sessionen har upphört att gälla. När tids gränsen går ut stängs sessionen i Windows PowerShell, även om alla arbets flöden ännu inte har pausats.

Ange ett värde i millisekunder.
Standardvärdet är 500.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Microsoft. PowerShell. commands. PSWorkflowExecutionOption

## ANTECKNINGAR

När det maximala värdet som anges av ett alternativ överskrids, Miss lyckas kommandot för att skapa en annan instans i sessionen, om inget annat anges i parameter beskrivningen. Om värdet för **MaxConnectedSessions** till exempel är 100. Kommandot för att skapa 101st-sessionen till en fjärrnod (måldator) Miss lyckas.

Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ. Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.

Dessutom varierar egenskaperna för de sessionsinställningar som innehåller ett **PSWorkflowExecutionOptions** -objekt baserat på alternativ värden för arbets flödet. Om konfigurationen till exempel innehåller ett **PSWorkflowExecutionOptions** -objekt som anger ett värde som inte är standardvärdet för egenskapen **SessionThrottleLimit** , har sessionens konfiguration en **SessionThrottleLimit** -egenskap. Annars är det inte.

## RELATERADE LÄNKAR

[New-PSWorkflowSession](New-PSWorkflowSession.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)
