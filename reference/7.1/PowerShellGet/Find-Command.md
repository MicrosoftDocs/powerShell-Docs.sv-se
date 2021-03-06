---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Command
ms.openlocfilehash: 7bcf9073b31da8470fe2b542f90ae35c20dba36d
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892478"
---
# Find-Command

## SAMMANFATTNING
Söker efter PowerShell-kommandon i moduler.

## SYNTAX

### Alla

```
Find-Command [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en `Find-Command` hittar PowerShell-kommandon som cmdlets, alias, Functions och arbets flöden. `Find-Command` söker i moduler i registrerade databaser.

`Find-Command`Ett **PSGetCommandInfo** -objekt returneras för varje kommando som hittas av. **PSGetCommandInfo** -objektet kan skickas ned pipelinen till `Install-Module` cmdleten.
`Install-Module` installerar den modul som innehåller kommandot.

## EXEMPEL

### Exempel 1: Sök efter alla kommandon i en angiven lagrings plats

`Find-Command`Cmdleten söker efter moduler i en registrerad lagrings plats.

```powershell
Find-Command -Repository PSGallery | Select-Object -First 10
```

```output
Name                                Version    ModuleName          Repository
----                                -------    ----------          ----------
Disable-AzureRmDataCollection       5.8.3      AzureRM.profile     PSGallery
Disable-AzureRmContextAutosave      5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmDataCollection        5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmContextAutosave       5.8.3      AzureRM.profile     PSGallery
Remove-AzureRmEnvironment           5.8.3      AzureRM.profile     PSGallery
Get-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Set-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Add-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Get-AzureRmSubscription             5.8.3      AzureRM.profile     PSGallery
Connect-AzureRmAccount              5.8.3      AzureRM.profile     PSGallery
```

`Find-Command` använder parametern **lagrings plats** för att ange namnet på en registrerad databas. Objekten skickas ned pipelinen. `Select-Object` tar emot objekten och använder den **första** parametern för att visa de första 10 resultaten.

### Exempel 2: hitta ett kommando efter namn

`Find-Command` kan använda namnet på ett kommando för att hitta modulen i en lagrings plats. Det är möjligt att ett kommando namn finns i flera **ModuleNames**.

```powershell
Find-Command -Repository PSGallery -Name Get-TargetResource
```

```Output
Name                  Version    ModuleName                      Repository
----                  -------    ----------                      ----------
Get-TargetResource    3.1.0.0    xPowerShellExecutionPolicy      PSGallery
Get-TargetResource    1.0.0      xInternetExplorerHomePage       PSGallery
Get-TargetResource    1.2.0.0    SystemLocaleDsc                 PSGallery
```

`Find-Command` använder parametern **lagrings plats** för att söka i **PSGallery**. Parametern **Name** anger kommandot **Get-TargetResource**.

### Exempel 3: hitta kommandon efter namn och installera modulen

`Find-Command` kan hitta kommandot och modulen och sedan skicka objektet till `Install-Module` . Om ett kommando ingår i flera moduler, använder du `Find-Command` parametern cmdlets **-modul-Name** .
Annars kan moduler installeras som du inte vill installera.

```powershell
PS> Find-Command -Name Get-TargetResource -Repository PSGallery -ModuleName SystemLocaleDsc |
    Install-Module

PS> Get-InstalledModule

Version   Name               Repository   Description
-------   ----               ----------   -----------
1.2.0.0   SystemLocaleDsc    PSGallery    This DSC Resource allows configuration of the Windows...
```

`Find-Command` använder parametern **Name** för att ange kommandot **Get-TargetResource**. Parametern **lagring** söker i **PSGallery**. Parametern **Modulnamn** anger den modul som du vill installera, **SystemLocaleDsc**. Objektet skickas ned pipelinen till `Install-Module` och modulen är installerad. När installationen är klar kan du använda `Get-InstalledModule` för att visa resultatet.

### Exempel 4: hitta ett kommando och spara dess modul

```
PS> Find-Command -Name Invoke-ScriptAnalyzer -Repository PSGallery | Save-Module -Path C:\Test\Modules -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'PSScriptAnalyzer'.
VERBOSE: Module 'PSScriptAnalyzer' was saved successfully to path 'C:\Test\Modules\PSScriptAnalyzer\1.18.0'.
```

`Find-Command` använder parametrarna **namn** och **lagrings plats** för att söka efter kommandot **Invoke-ScriptAnalyzer** i **PSGallery** -lagringsplatsen. Objektet skickas ned pipelinen till `Save-Module` . Parametern **Path** bestämmer var du vill spara modulen. **Verbose** är en valfri parameter, men visar status utdata i PowerShell-konsolen. Utförliga utdata är bra för fel sökning.

## PARAMETRAR

### -AllowPrerelease

Innehåller moduler som är markerade som en för hands version i resultaten.

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

### -AllVersions

Anger att denna cmdlet hämtar alla versioner av en modul.

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

### -Filter

Söker efter moduler baserat på **PackageManagement** -providerns söksyntax. Ange till exempel ord att söka efter i egenskaperna **Modulnamn** och **Description** .

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

### – MaximumVersion

Anger den maximala version av modulen som ska tas med i resultaten. Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.

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

### – MinimumVersion

Anger den lägsta version av modulen som ska tas med i resultaten. Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.

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

### -Modulnamn

Anger namnet på en modul för att söka efter kommandon. Standardvärdet är alla moduler.

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

### -Name

Anger kommando namnet som ska sökas efter i en lagrings plats. Använd kommatecken för att avgränsa en matris med kommando namn.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Proxy

Anger en proxyserver för begäran, i stället för en direkt anslutning till Internet resursen.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Databas

Anger den lagrings plats som ska sökas efter kommandon. Använd kommatecken för att avgränsa en matris med lagrings namn. Standardvärdet är alla databaser.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – RequiredVersion

Anger den version av modulen som ska tas med i resultaten.

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

### -Tagga

Anger taggar som kategoriserar moduler i en lagrings plats. Använd kommatecken för att avgränsa en matris med taggar.

```yaml
Type: System.String[]
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

### PSGetCommandInfo

`Find-Command` matar ut ett **PSGetCommandInfo** -objekt.

## ANTECKNINGAR

> [!IMPORTANT]
> Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1. Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet. Använd följande kommando för att se till att du använder TLS 1,2:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.

## RELATERADE LÄNKAR

[Get-InstalledModule](Get-InstalledModule.md)

[Installera-modul](Install-Module.md)

[Spara-modul](Save-Module.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Avinstallera-modul](Uninstall-Module.md)

