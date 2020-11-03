---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-DscConfiguration
ms.openlocfilehash: 25c8bc61976ce3940e0b9bd949fa3ee60728450d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264759"
---
# Test-DscConfiguration

## SAMMANFATTNING
Testar om den faktiska konfigurationen på noderna matchar önskad konfiguration.

## SYNTAX

### ComputerNameSet (standard)

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Detailed] [<CommonParameters>]
```

### ComputerNameAndPathSet

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Path] <String> [<CommonParameters>]
```

### ComputerNameAndReferenceConfigurationSet

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] -ReferenceConfiguration <String> [<CommonParameters>]
```

### CimSessionAndPathSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Path] <String>
 [<CommonParameters>]
```

### CimSessionAndReferenceConfigurationSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob]
 -ReferenceConfiguration <String> [<CommonParameters>]
```

### CimSessionSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Detailed]
 [<CommonParameters>]
```

## BESKRIVNING
**Test-DscConfiguration** -cmdleten testar om den faktiska konfigurationen på noderna matchar önskad konfiguration.
Ange vilka datorer som du vill testa konfigurationerna med hjälp av dator namn eller Common Information Model CIM-sessioner.
Om du inte anger en måldator testar cmdleten konfigurationen av den lokala datorn.

Om de önskade och de faktiska konfigurationerna matchar, returnerar cmdleten ett sträng värde för "true".
Annars returnerar den ett sträng värde på ' false '.

## EXEMPEL

### Exempel 1: testa konfigurationen för den lokala datorn

```
PS C:\> Test-DscConfiguration
```

Det här kommandot testar konfigurationen för den lokala datorn.

### Exempel 2: testa konfigurationen för en angiven dator

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Test-DscConfiguration -CimSession $Session
```

Det här exemplet testar konfigurationen från en dator som anges av en CIM-session.
I exemplet skapas en CIM-session för en dator med namnet Server01 för användning med cmdleten.
Du kan också skapa en matris med CIM-sessioner för att tillämpa cmdleten på flera angivna datorer.

Det första kommandot skapar en CIM-session med hjälp av cmdleten **New-CimSession** och lagrar sedan **CimSession** -objektet i variabeln $session.
I kommandot uppmanas du att ange ett lösen ord.
För mer information ange `Get-Help New-CimSession`.

Det andra kommandot testar konfigurationen för de datorer som identifieras av de **CimSession** -objekt som lagras i variabeln $session, i det här fallet datorn med namnet Server01.

### Exempel 3: testa konfigurationer med detaljerade resultat

```
PS C:\> Test-DscConfiguration -ComputerName "Server01", "Server02", "Server03" -Detailed
```

Det här kommandot testar konfigurationer för en uppsättning datorer som anges av parametern *computername* och returnerar detaljerad information som innehåller det övergripande läget, resurser som är i önskat tillstånd, resurser som inte är i önskat tillstånd och dator namn.

### Exempel 4: testa konfigurationer som anges i en mapp

```
PS C:\> Test-DscConfiguration -Path "C:\Dsc\Configurations"
```

Det här kommandot testar konfigurationer som definieras i en mapp som anges av parametern *Path* .
Konfigurationerna testas mot en uppsättning datorer, som identifieras av konfigurations filens fil namn.

### Exempel 5: testa konfigurationer som anges i en fil

```
PS C:\> Test-DscConfiguration -ReferenceConfiguration "C:\Dsc\Configurations\WebServer.mof" -ComputerName "Server01", "Server02", "Server03"
```

Det här kommandot testar en konfiguration som definierats i en fil mot en uppsättning datorer som anges av parametern *computername* .

## PARAMETRAR

### – AsJob
Anger att denna cmdlet kör kommandot som ett bakgrunds jobb.

Om du anger parametern *AsJob* , returnerar kommandot ett objekt som representerar jobbet och visar sedan kommando tolken.
Du kan fortsätta att arbeta i sessionen tills jobbet har slutförts.
Jobbet skapas på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn.
Använd jobb-cmdletar för att hantera jobbet.
Använd Receive-Job-cmdleten för att hämta jobb resultatet.

Om du vill använda den här parametern måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation och i Windows Vista och senare versioner av Windows operativ system måste du öppna Windows PowerShell med alternativet Kör som administratör.
Mer information finns i [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).

Mer information om bakgrunds jobb i Windows PowerShell finns i [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) och [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).

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

### – CimSession
Kör cmdleten i en fjärran sluten session eller på en fjärrdator.
Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en [New-CimSession-](/powershell/module/cimcmdlets/new-cimsession) eller [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) cmdlet.
Standardvärdet är den aktuella sessionen på den lokala datorn.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndReferenceConfigurationSet, CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
Anger en matris med dator namn som denna cmdlet testar konfigurationen på.
Cmdleten testar konfigurations dokumentet på den plats som anges av *Sök vägs* parametern till de här datorerna.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
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
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Detaljerad
Anger att denna cmdlet returnerar ett detaljerat resultat vid jämförelse av konfigurations dokumentet med det önskade läget för noderna.
Resultatet innehåller information, till exempel övergripande tillstånd, resurser som är i önskat tillstånd, resurser som inte är i önskat tillstånd och dator namn.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameSet, CimSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Anger sökvägen till en mapp som innehåller konfigurationsfiler för filer.
Cmdleten testar konfigurationen mot önskat tillstånd för datorer som anges av parametern *computername* eller *CimSession* .

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferenceConfiguration
Anger sökvägen till konfigurations dokument filen.
Den här cmdleten testar konfigurationen mot det aktuella läget för datorer som anges av parametern *computername* eller *CimSession* .

```yaml
Type: System.String
Parameter Sets: ComputerNameAndReferenceConfigurationSet, CimSessionAndReferenceConfigurationSet
Aliases:

Required: True
Position: Named
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

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Översikt över önskad tillstånds konfiguration i Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)
