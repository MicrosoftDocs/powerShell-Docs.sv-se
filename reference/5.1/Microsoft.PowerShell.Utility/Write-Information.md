---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-information?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Information
ms.openlocfilehash: e0f28393c95e2c0703c489d4691edcf883b4cb05
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272750"
---
# Write-Information

## SAMMANFATTNING

Anger hur PowerShell hanterar informations Ströms data för ett kommando.

## SYNTAX

```
Write-Information [-MessageData] <Object> [[-Tags] <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Write-Information`Cmdleten anger hur PowerShell hanterar informations data Ströms data för ett kommando.

Windows PowerShell 5,0 introducerar en ny, strukturerad informations ström. Du kan använda den här data strömmen för att skicka strukturerade data mellan ett skript och dess anropare eller värd programmet.
`Write-Information` låter dig lägga till ett informations meddelande i data strömmen och ange hur PowerShell hanterar informations data Ströms data för ett kommando. Informations strömmar fungerar också för `PowerShell.Streams` jobb och schemalagda aktiviteter.

> [!NOTE]
> Informations data strömmen följer inte standard konventionen för att förlösa sina meddelanden med "[Stream Name]:". Detta var avsett för det kortfattat och visuell renlighet.

`$InformationPreference`Variabeln Preference avgör om det meddelande som du anger ska `Write-Information` visas vid den förväntade punkten i skriptets åtgärd. Eftersom standardvärdet för den här variabeln är `SilentlyContinue` , visas inte informations meddelanden som standard. Om du inte vill ändra värdet för `$InformationPreference` kan du åsidosätta dess värde genom att lägga till den `InformationAction` gemensamma parametern i kommandot. Mer information finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) och [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

> [!NOTE]
> Från och med Windows PowerShell 5,0 `Write-Host` är en omslutning som `Write-Information` gör att du kan använda `Write-Host` för att generera utdata till informations strömmen. Detta gör det möjligt att **samla in** eller **undertrycka** data som skrivits med samtidigt som du `Write-Host` behåller bakåtkompatibilitet. Mer information finns i [Write-Host](Write-Host.md)

`Write-Information` är också en arbets flödes aktivitet som stöds i PowerShell 5. x.

## EXEMPEL

### Exempel 1: Skriv information för Get-Results

I det här exemplet visar du ett informations meddelande, "skaffa dina funktioner!", efter att du kört `Get-WindowsFeature` kommandot för att hitta alla funktioner som har ett namn värde som börjar med "p".
Eftersom `$InformationPreference` variabeln fortfarande är inställd på standardvärdet, `SilentlyContinue` lägger du till `InformationAction` parametern för att åsidosätta `$InformationPreference` värdet och visa meddelandet. `InformationAction`Värdet är Continue, vilket innebär att meddelandet visas, men skriptet eller kommandot fortsätter om det inte har slutförts ännu.

```powershell
Get-WindowsFeature -Name p*
Write-Information -MessageData "Got your features!" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
Got your features!
```

### Exempel 2: Skriv information och tagga den

I det här exemplet använder du `Write-Information` för att meddela användarna att de behöver köra ett annat kommando när de är klar med det aktuella kommandot. I exemplet läggs etikett instruktionerna till i informations meddelandet. När du har kört det här kommandot, och om du söker i informations data strömmen efter taggade instruktioner, kommer det meddelande som anges här vara bland resultatet.

```powershell
$message = "To filter your results for PowerShell, pipe your results to the Where-Object cmdlet."
Get-WindowsFeature -Name p*
Write-Information -MessageData $message -Tags "Instructions" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
To filter your results for PowerShell, pipe your results to the Where-Object cmdlet.
```

### Exempel 3: skriva information till en fil

```powershell
function Test-Info
{
    Get-Process P*
    Write-Information "Here you go"
}
Test-Info 6> Info.txt
```

## PARAMETRAR

### -MessageData

Anger ett informations meddelande som ska visas för användarna när de kör ett skript eller kommando. För bästa resultat omger du informations meddelandet inom citat tecken.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Taggar

Anger en enkel sträng som du kan använda för att sortera och filtrera meddelanden som du har lagt till i informations strömmen med `Write-Information` . Den här parametern fungerar på samma sätt som parametern **taggar** i `New-ModuleManifest` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

`Write-Information` accepterar inte skickas-inmatade.

## UTDATA

### System. Management. Automation. InformationRecord

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)

[about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Skriv-debug](Write-Debug.md)

[Skriv värd](Write-Host.md)

[Skriv information](Write-Information.md)

[Skriv förlopp](Write-Progress.md)

[Skriv-verbose](Write-Verbose.md)

[Skriv varning](Write-Warning.md)

[Skriva-utdata](Write-Output.md)
