---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/start-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-DscConfiguration
ms.openlocfilehash: c34754aeb7fce99030cf4ddb235e3e7e8161f3eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266025"
---
# Start-DscConfiguration

## SAMMANFATTNING
Tillämpar konfiguration på noder.

## SYNTAX

### ComputerNameAndPathSet (standard)

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimSessionAndPathSet

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] -CimSession <CimSession[]> [-ThrottleLimit <Int32>]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameAndUseExistingSet

```
Start-DscConfiguration [-Wait] [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-UseExisting] [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionAndUseExistingSet

```
Start-DscConfiguration [-Wait] [-Force] -CimSession <CimSession[]> [-ThrottleLimit <Int32>] [-UseExisting]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **Start-DscConfiguration** tillämpar konfigurationen på noderna.
När den används med parametern *UseExisting* tillämpas den befintliga konfigurationen på mål datorn.
Ange vilka datorer som du vill tillämpa konfigurationen på genom att ange dator namn eller använda Common Information Model CIM-sessioner.

Som standard skapar denna cmdlet ett jobb och returnerar ett **jobb** objekt.
Om du vill ha mer information om bakgrunds jobb skriver du `Get-Help about_Jobs` .
Om du vill använda den här cmdleten interaktivt anger du parametern *wait* .

Ange *utförlig* parameter om du vill se information om vad cmdleten gör när konfigurations inställningarna tillämpas.

## EXEMPEL

### Exempel 1: Använd konfigurations inställningar

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\"
```

Detta kommando tillämpar konfigurations inställningarna från C:\DSC\Configurations\ till alla datorer som har inställningar i den mappen.
Kommandot returnerar **jobb** objekt för varje målnod som distribueras till.

### Exempel 2: tillämpa konfigurations inställningar och vänta tills konfigurationen är klar

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -Wait -Verbose
```

Detta kommando tillämpar konfigurationen från C:\DSC\Configurations\ till den lokala datorn.
Kommandot returnerar **jobb** objekt för varje målnod som distribueras till, i det här fallet bara den lokala datorn.
I det här exemplet anges *utförlig* parameter.
Därför skickar kommandot meddelanden till-konsolen när de fortsätter.
Kommandot innehåller parametern *wait* .
Därför kan du inte använda-konsolen förrän kommandot har slutfört alla konfigurations åtgärder.

### Exempel 3: tillämpa konfigurations inställningar med en CIM-session

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -CimSession $Session
```

I det här exemplet används konfigurations inställningar på en angiven dator.
I exemplet skapas en CIM-session för en dator med namnet Server01 för användning med cmdleten.
Du kan också skapa en matris med CIM-sessioner för att tillämpa cmdleten på flera angivna datorer.

Det första kommandot skapar en CIM-session med hjälp av cmdleten **New-CimSession** och lagrar sedan **CimSession** -objektet i variabeln $session.
I kommandot uppmanas du att ange ett lösen ord.
För mer information ange `Get-Help NewCimSession`.

Det andra kommandot tillämpar konfigurations inställningarna från C:\DSC\Configurations\ på de datorer som identifieras av de **CimSession** -objekt som lagras i variabeln $session.
I det här exemplet innehåller variabeln $Session endast en CIM-session för datorn med namnet Server01.
Kommandot tillämpar konfigurationen.
Kommandot skapar **jobb** objekt för varje konfigurerad dator.

## PARAMETRAR

### – CimSession
Kör cmdleten i en fjärran sluten session eller på en fjärrdator.
Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en [New-CimSession-](/powershell/module/cimcmdlets/new-cimsession) eller [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) cmdlet.
Standardvärdet är den aktuella sessionen på den lokala datorn.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
Anger en matris med dator namn.
Den här parametern begränsar de datorer som har konfigurations dokument i parametern *Path* till de som anges i matrisen.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential
Anger ett användar namn och lösen ord, som ett **PSCredential** -objekt, för mål datorn.
Om du vill hämta ett **PSCredential** -objekt använder du cmdleten Get-Credential.
För mer information ange `Get-Help Get-Credential`.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
Stoppar den konfigurations åtgärd som körs på mål datorn och påbörjar den nya Start-Configuration åtgärden.
Om egenskapen **RefreshMode** för den lokala Configuration Manager är inställd på **Hämta** , ändrar den här parametern den till **push**.

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

### – JobName
Anger ett eget namn för ett jobb.
Om du anger den här parametern körs cmdleten som ett jobb och den returnerar ett **jobb** objekt.

Som standard tilldelar Windows PowerShell namnet JobN där N är ett heltal.

Ange inte den här parametern om du anger parametern *wait* .

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

### -Path
Anger en fil Sök väg till en mapp som innehåller filer för konfigurations inställningar.
Denna cmdlet publicerar och tillämpar dessa konfigurations inställningar på datorer som har installationsfiler på den angivna sökvägen.
Varje målnod måste ha en inställnings fil med följande format: NetBIOS-namn. mof.

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.
Om den här parametern utelämnas eller värdet `0` anges, beräknar Windows PowerShell en optimal begränsnings gräns för cmdleten baserat på antalet CIM-cmdletar som körs på datorn.
Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.

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

### -UseExisting
Anger att den här cmdleten tillämpar den befintliga konfigurationen.
Konfigurationen kan finnas på mål datorn av HITECH med hjälp av **Start-DscConfiguration** eller genom att publicera med hjälp av cmdleten Publish-DscConfiguration.

Innan du anger den här parametern för denna cmdlet bör du läsa informationen i [Nyheter i Windows PowerShell 5,0](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50)

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameAndUseExistingSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Vänta
Anger att cmdleten blockerar konsolen tills den Slutför alla konfigurations åtgärder.

Om du anger den här parametern ska du inte ange parametern *JobName* .

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

### -Confirm
Uppmanar dig att bekräfta innan du kör cmdleten.

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

### -WhatIf
Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

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

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Översikt över önskad tillstånds konfiguration i Windows PowerShell](/powershell/scripting/dsc/overview/overview)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Stop-DscConfiguration](Stop-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)

[Uppdatera – DscConfiguration](Update-DscConfiguration.md)
