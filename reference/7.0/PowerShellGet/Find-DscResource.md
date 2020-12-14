---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/04/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-dscresource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-DscResource
ms.openlocfilehash: 4312ac522bf0b04a9a95414774bad9624737ce45
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892679"
---
# Find-DscResource

## SAMMANFATTNING
Söker efter Desired State Configuration (DSC)-resurser.

## SYNTAX

### Alla

```
Find-DscResource [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Find-DscResource`Cmdleten söker igenom registrerade databaser för att hitta DSC-resurser som ingår i moduler. Som standard `Find-DscResource` genomsöks alla registrerade databaser.

`Find-DscResource`Ett **PSGetDscResourceInfo** -objekt returneras för varje modul som hittas av.
**PSGetDscResourceInfo** -objekt kan skickas ned pipelinen till `Install-Module` cmdleten.
`Install-Module` installerar modulen.

## EXEMPEL

### Exempel 1: hitta alla DSC-resurser

`Find-DscResource` Returnerar DSC-resurser från registrerade databaser. Använd parametern **lagrings plats** om du vill söka i en speciell lagrings plats.

```powershell
Find-DscResource
```

```Output
Name                           Version    ModuleName                     Repository
----                           -------    ----------                     ----------
Carbon_Privilege               2.8.1      Carbon                         PSGallery
Carbon_ScheduledTask           2.8.1      Carbon                         PSGallery
Carbon_Service                 2.8.1      Carbon                         PSGallery
PackageManagement              1.4        PackageManagement              PSGallery
PackageManagementSource        1.4        PackageManagement              PSGallery
PSModule                       2.1.4      PowerShellGet                  PSGallery
PSRepository                   2.1.4      PowerShellGet                  PSGallery
xArchive                       8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xDSCWebService                 8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xEnvironment                   8.7.0.0    xPSDesiredStateConfiguration   PSGallery
```

### Exempel 2: hitta en DSC-resurs efter namn

`Find-DscResource` söker efter DSC-resurser efter namn. Använd kommatecken för att avgränsa en matris med resurs namn.

```powershell
Find-DscResource -Name xWebsite, xWebApplication, xWebSiteDefaults
```

```Output
Name               Version    ModuleName            Repository
----               -------    ----------            ----------
xWebApplication    2.6.0.0    xWebAdministration    PSGallery
xWebsite           2.6.0.0    xWebAdministration    PSGallery
xWebSiteDefaults   2.6.0.0    xWebAdministration    PSGallery
```

`Find-DscResource` använder parametern **Name** för att hitta den angivna matrisen med DSC-resurser.

### Exempel 3: hitta en DSC-resurs och installera den

`Find-DscResource` hittar en DSC-resurs och skickar objektet nedåt till den pipelines som ska installeras.
Använd `Get-InstalledModule` för att visa resultaten efter installationen.

Flera resurser från samma modul kan skickas ned pipelinen till `Install-Module` .
`Install-Module` försöker bara installera modulen en gång.

```powershell
Find-DscResource -Name xWebsite | Install-Module
```

`Find-DscResource` använder parametern **Name** för att hitta resursen med namnet **xWebsite**. Objektet skickas ned pipelinen till `Install-Module` cmdleten. `Install-Module` installerar **xWebAdministration** -modulen för resursen.

### Exempel 4: hitta alla DSC-resurser i en modul

`Find-DscResource` hittar alla DSC-resurser som ingår i en angiven modul. Som standard visas den aktuella versionen. Om du vill visa andra versioner använder du parametrarna **AllVersions** eller **RequiredVersions** .

```powershell
Find-DscResource -ModuleName xWebAdministration
```

```Output
Name                                Version    ModuleName              Repository
----                                -------    ----------              ----------
WebApplicationHandler               2.6.0.0    xWebAdministration      PSGallery
xIisFeatureDelegation               2.6.0.0    xWebAdministration      PSGallery
xIisHandler                         2.6.0.0    xWebAdministration      PSGallery
xIisLogging                         2.6.0.0    xWebAdministration      PSGallery
```

`Find-DscResource` använder **Modulnamn** -parametern för att ange **XWEBADMINISTRATION** och hitta DSC-resurserna som finns i modulen. Den aktuella versionen av varje resurs visas.

### Exempel 5: hitta en DSC-resurs efter tagg och nödvändig version

DSC-resurser kan hittas med parametrarna **tag** och **RequiredVersion**. **Tagg** visar den aktuella versionen av varje resurs som innehåller den angivna taggen i lagrings platsen.
**RequiredVersion** kräver att parametern **Modulnamn** och parametern **Name** är valfri. **Namn** -och **Modulnamn** -parametrarna begränsar utdata. Använd parametern **AllVersions** för att visa tillgängliga versioner av en DSC-resurs.

```powershell
Find-DscResource -ModuleName xWebAdministration -Tag DSC -RequiredVersion 1.20
```

```output
Name                    Version    ModuleName             Repository
----                    -------    ----------             ----------
xIisFeatureDelegation   1.20.0.0   xWebAdministration     PSGallery
xIisHandler             1.20.0.0   xWebAdministration     PSGallery
xIisLogging             1.20.0.0   xWebAdministration     PSGallery
xIisMimeTypeMapping     1.20.0.0   xWebAdministration     PSGallery
```

### Exempel 6: hitta en resurs med hjälp av ett filter

`Find-DscResource` söker efter alla resurser och använder **filter** parametern för att ange resultaten efter **domän**. **Filter** parametern hittar filtervärdet i objektets beskrivning eller modulens namn. Använd `Select-Object` cmdleten för att visa egenskaperna för ett objekt.

```powershell
Find-DscResource -Filter Domain
```

```output
Name                    Version    ModuleName                 Repository
----                    -------    ----------                 ---------
xComputer               4.1.0.0    xComputerManagement        PSGallery
Computer                6.4.0.0    ComputerManagementDsc      PSGallery
xDSCDomainjoin          1.1        xDSCDomainjoin             PSGallery
xDisk                   1.0        xDisk                      PSGallery
xDSCFirewall            1.6.21     xDSCFirewall               PSGallery
dmAwsTagInstance        1.0.1      domainAwsDSCResources      PSGallery
```

## PARAMETRAR

### -AllowPrerelease

Innehåller resurser som marker ATS som en för hands version i resultaten.

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

Parametern **AllVersions** visar var och en av en DSC-resurs tillgängliga versioner. Du kan inte använda parametern **AllVersions** med parametrarna **MinimumVersion**, **MaximumVersion** eller **RequiredVersion** .

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

Söker efter resurser baserat på **PackageManagement** -providerns söksyntax. Ange till exempel ord att söka efter i egenskaperna **Modulnamn** och **Description** .

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

Anger den maximala resurs version som ska tas med i resultaten. Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.

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

Anger den lägsta resurs version som ska tas med i resultaten. Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.

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

Anger en modul som innehåller DSC-resursen.

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

Anger namnet på en resurs. Standardvärdet är alla resurser. Använd kommatecken för att avgränsa en matris med resurs namn.

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

Anger ett användar konto med behörighet att använda den proxyserver som anges i parametern **proxy** .

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

Anger en lagrings plats för att söka efter resurser. Använd kommatecken för att avgränsa en matris med lagrings namn.

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

Anger modulens exakta versions nummer som ska ingå i resultaten. Parametrarna **RequiredVersion** och **MinimumVersion** kan inte användas i samma kommando.

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

### PSGetDscResourceInfo

`Find-DscResource` Returnerar ett **PSGetDscResourceInfo** -objekt.

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

[Registrera – PSRepository](Register-PSRepository.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Avinstallera-modul](Uninstall-Module.md)
