---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/set-logproperties?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LogProperties
ms.openlocfilehash: a852a3016d7e63d17b86cf2efb3c928d2f7b901c
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194530"
---
# Set-LogProperties

## SAMMANFATTNING
Ändrar egenskaperna för en händelse logg i Windows.

## SYNTAX

```
Set-LogProperties [-LogDetails] <LogDetails> [-Force] [<CommonParameters>]
```

## BESKRIVNING

Den här cmdleten ändrar konfigurations inställningarna för en händelse logg i Windows. Denna cmdlet används av `Enable-PSTrace` `Disable-PSTrace` cmdletarna och.

Du måste köra denna cmdlet från en upphöjd PowerShell-session.

## EXEMPEL

### Exempel 1: ändra inställningen kvarhållning för händelse loggen i Windows PowerShell

```powershell
$logDetails = Get-LogProperties 'Windows PowerShell'
$logDetails.Retention = $True
Set-LogProperties -LogDetails $logDetails
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : True
AutoBackup : False
MaxLogSize : 15728640
```

## PARAMETRAR

### -Force

Används för att framtvinga ändringen utan att du behöver göra något.

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

### -LogDetails

De uppdaterade konfigurations inställningarna som ska tilldelas händelse loggen.

```yaml
Type: Microsoft.PowerShell.Diagnostics.LogDetails
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Microsoft. PowerShell. Diagnostics. LogDetails

Du måste skicka ett fullständigt konfigurerat **LogDetails** -objekt till `Set-LogProperties` cmdleten.
Därför bör du använda `Get-LogProperties` för att hämta den aktuella konfigurationen om du vill ändra en inställning.

## UTDATA

### System. Object

## ANTECKNINGAR

Du måste köra denna cmdlet från en upphöjd PowerShell-session.

## RELATERADE LÄNKAR

[Get-LogProperties](Get-LogProperties.md)

[Aktivera – PSTrace](Enable-PSTrace.md)

[Disable-PSTrace](Disable-PSTrace.md)
