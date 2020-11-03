---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: 88eeb312c0c31a7e9a9f5c52622c58fe7831e98d
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268358"
---
# New-PSTransportOption

## SAMMANFATTNING
Skapar ett objekt som innehåller avancerade alternativ för en konfiguration av sessionen.

## SYNTAX

```
New-PSTransportOption [-MaxIdleTimeoutSec <Int32>] [-ProcessIdleTimeoutSec <Int32>] [-MaxSessions <Int32>]
 [-MaxConcurrentCommandsPerSession <Int32>] [-MaxSessionsPerUser <Int32>] [-MaxMemoryPerSessionMB <Int32>]
 [-MaxProcessesPerSession <Int32>] [-MaxConcurrentUsers <Int32>] [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en **New-PSTransportOption** skapar ett objekt som innehåller transport alternativ för sessionsinställningar.
Du kan använda objektet som värdet för *TransportOption* -parametern för cmdlet: ar som skapar eller ändrar en sessionsinformation, till exempel Register-PSSessionConfiguration-och Set-PSSessionConfiguration-cmdletar.

Du kan också ändra transport alternativ inställningarna genom att redigera värdena för konfigurations egenskaperna för sessionen på WSMan: Drive.
Mer information finns i WSMan-providern.

Konfigurations alternativen för sessionen representerar de Sessionsgränser som anges på Server sidan eller tar emot en fjärr anslutning.
Klient sidan eller sändnings änden av anslutningen kan ange alternativ värden för sessionen när sessionen skapas, eller när klienten kopplar från eller återansluter till sessionen.
Om inget annat anges, när inställnings värden är i konflikt med varandra, prioriteras värden på klient sidan.
Värdena på klient sidan kan dock inte bryta mot maximalt antal värden och kvoter som angetts i konfigurationen av sessionen.

Utan parametrar genererar **New-PSTransportOption** ett transport alternativ objekt som har null-värden för alla alternativ.
Om du utelämnar en parameter har objektet ett null-värde för egenskapen som parametern representerar.
Ett null-värde påverkar inte konfigurationen av sessionen.

Mer information om sessions alternativ finns i New-PSSessionOption.
För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: generera ett standard transport alternativ

```powershell
New-PSTransportOption
```

```Output
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

Det här kommandot kör kommandot **New-PSTransportOption** utan parametrar.
Utdata visar att cmdleten genererar ett transport alternativ objekt som har null-värden för alla egenskaper.

### Exempel 2: hämta konfigurations alternativ för sessioner

Det här exemplet visar hur du använder ett transport alternativ objekt för att ange konfigurations alternativ för sessioner.

```powershell
$t = New-PSTransportOption -MaxSessions 40
Register-PSSessionConfiguration -Name ITTasks -TransportOption $t
Get-PSSessionConfiguration -Name ITTasks | Format-List -Property *
```

```Output
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

Det första kommandot använder cmdleten **New-PSTransportOption** för att skapa ett transport alternativ objekt, som det sparas i variabeln $t. Kommandot använder parametern *MaxSessions* för att öka det maximala antalet sessioner till 40.

Det andra kommandot använder cmdleten **register-PSSessionConfiguration** för att skapa konfigurationen av ITTasks-sessionen. Kommandot använder parametern *TransportOption* för att ange objektet transport alternativ i variabeln $t.

Det tredje kommandot använder cmdleten Get-PSSessionConfiguration för att hämta ITTasks och Format-List-cmdleten för att visa alla egenskaper för sessionens konfigurations objekt i en lista. Utdata visar att värdet för **MaxShells** -egenskapen i sessionens konfiguration är 40.

### Exempel 3: Ange ett transport alternativ

Det här kommandot visar resultatet av att ställa in ett transport alternativ i en sessionsinformation på de sessioner som använder-sessionen.

```powershell
$t = New-PSTransportOption -IdleTimeoutSec 3600
Set-PSSessionConfiguration -Name ITTasks -TransportOption $t
$s = New-PSSession -Name MyITTasks -ConfigurationName ITTasks
$s | Format-List -Property *
```

```Output
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

Det första kommandot använder cmdleten **New-PSTransportOption** för att skapa ett transport alternativ objekt. Kommandot använder parametern *IdleTimeoutSec* för att ange objektets **egenskaps** värde till en timme (3600 sekunder). Kommandot sparar objektet transport objekt i variabeln $t.

Det andra kommandot använder cmdleten Set-PSSessionConfiguration för att ändra transport alternativ för konfigurationen av ITTasks-sessionen. Kommandot använder parametern *TransportOption* för att ange objektet transport alternativ i variabeln $t.

Det tredje kommandot använder cmdleten New-PSSession för att skapa MyITTasks-sessionen på den lokala datorn. Kommandot använder egenskapen **ConfigurationName** för att ange konfigurationen av ITTasks-sessionen. Kommandot sparar sessionen i variabeln $s. Observera att kommandot inte använder *SessionOption* -parametern för **New-PSSession** för att ange en anpassad tids gräns för inaktivitet för sessionen. Om den gjorde det inaktivt timeout-värde som angetts i alternativet session, prioriteras tids gränsen för inaktivitet i konfigurationen av sessionen.

Det fjärde kommandot använder Format-List-cmdleten för att visa alla sessionens egenskaper i $s-variabeln i en lista. Utdata visar att sessionen har en inaktiv timeout på en timme (360 000 millisekunder).

## PARAMETRAR

### -IdleTimeoutSec

Anger hur lång tid varje session förblir öppen om fjärrdatorn inte får någon kommunikation från den lokala datorn.
Detta inkluderar pulsslags signalen.
När intervallet går ut stängs sessionen.

Timeout-värdet för inaktivitet är av stor betydelse när användaren avser att koppla från och återansluta till en session.
Användaren kan bara återansluta om sessionen inte har nått sin tids gräns.

Parametern *IdleTimeoutSec* motsvarar **IdleTimeoutMs** -egenskapen för en sessions konfiguration.

Ange ett värde i sekunder.
Standardvärdet är 7200 (2 timmar).
Det minsta värdet är 60 (1 minut).
Det maximala värdet är värdet för egenskapen **idleTimeout** för gränssnitts objekt i WSMan-konfigurationen ( `WSMan:\\\<ComputerName\>\Shell\IdleTimeout` ).
Standardvärdet är 7200000 millisekunder (2 timmar).

Om ett tids gräns värde för inaktivitet anges i sessions-alternativen och i konfigurationen av sessionen, har värdet som anges i session alternativen företräde, men det får inte överskrida värdet för **MaxIdleTimeoutMs** -egenskapen i konfigurationen för sessionen.
Ange värdet för egenskapen **MaxIdleTimeoutMs** med parametern *MaxIdleTimeoutSec* .

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

### -MaxConcurrentCommandsPerSession

Begränsar antalet kommandon som kan köras samtidigt i varje session till det angivna värdet.
Standardvärdet är 1000.

Parametern *MaxConcurrentCommandsPerSession* motsvarar **MaxConcurrentCommandsPerShell** -egenskapen för en sessions konfiguration.

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

### -MaxConcurrentUsers

Begränsar antalet användare som kan köra kommandon på samma tid i varje session till det angivna värdet.
Standardvärdet är 5.

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

### -MaxIdleTimeoutSec

Begränsar tids gränsen för inaktivitet för varje session till det angivna värdet.
Standardvärdet är \[ int \] :: MaxValue (~ 25 dagar).

Timeout-värdet för inaktivitet är av stor betydelse när användaren avser att koppla från och återansluta till en session.
Användaren kan bara återansluta om sessionen inte har nått sin tids gräns.

Parametern *MaxIdleTimeoutSec* motsvarar **MaxIdleTimeoutMs** -egenskapen för en sessions konfiguration.

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

### -MaxMemoryPerSessionMB

Begränsar det minne som används av varje session till det angivna värdet.
Ange ett värde i megabyte.
Standardvärdet är 1024 megabyte (1 GB).

Parametern *MaxMemoryPerSessionMB* motsvarar **MaxMemoryPerShellMB** -egenskapen för en sessions konfiguration.

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

### -MaxProcessesPerSession

Begränsar antalet processer som körs i varje session till det angivna värdet.
Standardvärdet är 15.

Parametern *MaxProcessesPerSession* motsvarar **MaxProcessesPerShell** -egenskapen för en sessions konfiguration.

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

### -MaxSessions

Begränsar antalet sessioner som använder-konfigurationen av sessionen.
Standardvärdet är 25.

Parametern *MaxSessions* motsvarar **MaxShells** -egenskapen för en sessions konfiguration.

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

### -MaxSessionsPerUser

Begränsar antalet sessioner som använder-konfigurationen av sessionen och körs med autentiseringsuppgifterna för en viss användare till det angivna värdet.
Standardvärdet är 25.

När du anger det här värdet bör du tänka på att många användare kan använda autentiseringsuppgifterna för en kör som-användare.

Parametern *MaxSessionsPerUser* motsvarar **MaxShellsPerUser** -egenskapen för en sessions konfiguration.

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

### -OutputBufferingMode

Anger hur kommandoutdata hanteras i frånkopplade sessioner när utdatabufferten blir full.
De acceptabla värdena för den här parametern är:

- Undantaget.
När utdatabufferten är full pausas körningen tills bufferten är klar.
- Skugg.
När utdatabufferten är full fortsätter körningen.
När nya utdata sparas, ignoreras det äldsta resultatet.
- Inga.
Inget utdata buffer-läge har angetts.

Standardvärdet för egenskapen **OutputBufferingMode** för sessioner är blockera.

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

### -ProcessIdleTimeoutSec

Begränsar tids gränsen för varje värd process till det angivna värdet.
Standardvärdet är 0, vilket innebär att det inte finns något timeout-värde för processen.

Andra sessionsdata har timeout-värden per process.
Konfigurationen för **Microsoft. PowerShell. Workflow** -sessionen har till exempel ett tids gräns värde för per process på 28800 sekunder (8 timmar).

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Microsoft. PowerShell. commands. WSManConfigurationOption

## ANTECKNINGAR

- Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ. Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.

## RELATERADE LÄNKAR

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Registrera – PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)
