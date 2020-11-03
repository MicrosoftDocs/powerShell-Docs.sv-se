---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 04/29/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/set-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-DscLocalConfigurationManager
ms.openlocfilehash: 0d35aa56a52f0e6c17abd0e7b2707869e780324c
ms.sourcegitcommit: 0d4d3e47f6979876550591f62061096e7a568f7e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/11/2020
ms.locfileid: "93268047"
---
# Set-DscLocalConfigurationManager

## SAMMANFATTNING

Tillämpar lokala Configuration Manager-inställningar (LCM) på noder.

## SYNTAX

### ComputerNameSet (standard)

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionSet

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Set-DscLocalConfigurationManager`Cmdleten tillämpar LCM-inställningar eller meta-konfiguration på noder. Ange datorer genom att ange dator namn eller använda Common Information Model CIM-sessioner. Om du inte anger en måldator, tillämpar cmdleten inställningar på den lokala datorn.

## EXEMPEL

### Exempel 1: tillämpa inställningar för LCM

```
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\"
```

Detta kommando tillämpar LCM-inställningarna från `C:\DSC\Configurations\` på de riktade noderna. När du har tagit emot inställningarna bearbetar LCM dem.

> [!WARNING]
> Om det finns flera meta-MOF: ar för samma dator som lagras i den angivna mappen tillämpas bara den första meta MOF.

### Exempel 2: tillämpa inställningar för LCM med hjälp av en CIM-session

```
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\" -CimSession $Session
```

Det här exemplet tillämpar LCM-inställningar på en dator och tillämpar inställningarna. I exemplet skapas en CIM-session för en dator med namnet Server01 för användning med cmdleten. Du kan också skapa en matris med CIM-sessioner för att tillämpa cmdleten på flera angivna datorer.

Det första kommandot skapar en CIM-session med hjälp av `New-CimSession` cmdleten och lagrar sedan **CimSession** -objektet i `$Session` variabeln. I kommandot uppmanas du att ange ett lösen ord. För mer information ange `Get-Help New-CimSession`.

Det andra kommandot tillämpar LCM-inställningar för den riktade noden från `C:\DSC\Configurations\` till datorn som identifieras av **CimSession** -objekten som lagras i `$Session` variabeln. I det här exemplet `$Session` innehåller variabeln endast en CIM-session för datorn med namnet Server01. Kommandot tillämpar inställningarna. När du har tagit emot inställningarna bearbetar LCM dem.

## PARAMETRAR

### – CimSession

Kör cmdleten i en fjärran sluten session eller på en fjärrdator. Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en [New-CimSession-](/powershell/module/CimCmdlets/New-CimSession) eller [Get-CimSession-](/powershell/module/CimCmdlets/Get-CimSession) cmdlet.
Standardvärdet är den aktuella sessionen på den lokala datorn.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName

Anger en matris med dator namn. Den här parametern begränsar de datorer som har meta-konfigurations dokument i parametern **Path** till de som anges i matrisen.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential

Anger ett användar namn och lösen ord, som ett **PSCredential** -objekt, för mål datorn. Om du vill hämta ett **PSCredential** -objekt använder du cmdleten Get-Credential. För mer information ange `Get-Help Get-Credential`.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse.

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

### -Path

Anger en fil Sök väg till en mapp som innehåller filer för konfigurations inställningar. Cmdleten publicerar och tillämpar dessa LCM-inställningar på datorer som har installationsfiler på den angivna sökvägen. Varje målnod måste ha en inställnings fil med följande format: `NetBIOS Name.meta.mof` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten. Om den här parametern utelämnas eller värdet `0` anges, beräknar Windows PowerShell en optimal begränsnings gräns för cmdleten baserat på antalet CIM-cmdletar som körs på datorn. Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.

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

[Get-DscLocalConfigurationManager](Get-DscLocalConfigurationManager.md)
