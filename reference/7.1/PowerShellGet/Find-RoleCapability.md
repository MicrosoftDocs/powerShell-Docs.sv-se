---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: ca6a3845920793e7825727bef455c1001c13f0f0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266343"
---
# Find-RoleCapability

## SAMMANFATTNING
Hittar roll funktioner i moduler.

## SYNTAX

### Alla

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>] 
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease] 
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] 
[-Repository <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Find-RoleCapability`Cmdleten söker igenom registrerade databaser för att hitta funktioner och moduler för PowerShell-roller.

`Find-RoleCapability`Ett **PSGetRoleCapabilityInfo** -objekt returneras för varje roll kapacitet som hittas av. **PSGetRoleCapabilityInfo** -objekt kan skickas ned pipelinen till `Install-Module` `Save-Module` cmdletarna eller.

Funktioner i PowerShell-rollen definierar vilka kommandon och program som är tillgängliga för en användare på en just tillräckligt JEA-slutpunkt (administration). Roll funktioner definieras av filer med ett `.psrc` tillägg.

## EXEMPEL

### Exempel 1: hitta roll funktioner

`Find-RoleCapability` hittar roll funktioner i varje registrerad lagrings plats. Använd parametern **lagrings plats** om du vill söka i en speciell lagrings plats.

```powershell
Find-RoleCapability
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
General-Lev2     1.0        JeaExamples    PSGallery
IIS-Lev1         1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### Exempel 2: hitta roll funktioner efter namn

`Find-RoleCapability` hittar roll funktioner efter namn. Använd kommatecken för att avgränsa en mat ris namn.

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### Exempel 3: hitta och spara en roll kapacitets modul

`Find-RoleCapability`Cmdleten hittar en roll kapacitet och skickar objektet nedåt i pipelinen.
`Save-Module` sparar roll funktionens modul i ett fil system. `Get-ChildItem` visar innehållet i modulens katalog.

```
PS> Find-RoleCapability -Name General-Lev1 | Save-Module -Path C:\Test\Modules

PS> Get-ChildItem -Path C:\Test\Modules\JeaExamples\1.0\

    Directory: C:\Test\Modules\JeaExamples\1.0

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----          6/4/2019    16:37                RoleCapabilities
-a----          2/5/2019    18:46           1702 CreateRegisterPSSC.ps1
-a----          2/5/2019    18:46           7656 JeaExamples.psd1
-a----         10/1/2018    08:16            595 JeaExamples.psm1
```

`Find-RoleCapability` använder **Name** -parametern för att ange den **allmänna-Lev1** roll funktionen.
Objektet skickas ned pipelinen. `Save-Module` använder parametern **Path** för fil systemets plats för att spara modulen. När modulen har sparats `Get-ChildItem` anger modulens **sökväg** och visar innehållet i **JeaExamples** -modulens katalog.

### Exempel 4: Sök efter och installera en roll kapacitets modul

`Find-RoleCapability` söker efter modulen och skickar objektet nedåt i pipelinen. `Install-Module` installerar modulen. Efter installationen använder `Get-InstalledModule` du för att se resultatet.

```
PS> Find-RoleCapability -Name General-Lev1 | Install-Module -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'JeaExamples'.
VERBOSE: InstallPackageLocal' - name='JeaExamples', version='1.0',
VERBOSE: Validating the 'JeaExamples' module contents
VERBOSE: Test-ModuleManifest successfully validated the module manifest file
VERBOSE: Module 'JeaExamples' was installed successfully to path

PS> Get-InstalledModule

Version    Name            Repository     Description
-------    ----            ----------     -----------
1.0        JeaExamples     PSGallery      Some example Jea roles for general server maintenance...
```

`Find-RoleCapability` använder **Name** -parametern för att ange den **allmänna-Lev1** roll funktionen.
Objektet skickas ned pipelinen. `Install-Module` använder **verbose** -parametern för att visa status meddelanden under installationen. När installationen är färdig `Get-InstalledModule` bekräftar utdata att **JeaExamples** -modulen har installerats.

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

Anger att denna cmdlet hämtar alla versioner av en modul. Parametern **AllVersions** visar var och en av modulernas tillgängliga versioner.

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

Anger namnet på den modul som du vill söka efter roll funktioner i. Standardvärdet är alla moduler.

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

Anger namnet på en roll funktion. Standardvärdet är alla roll funktioner. Använd kommatecken för att avgränsa en matris med resurs namn.

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

Anger en lagrings plats för att söka efter roll funktioner. Använd kommatecken för att avgränsa en matris med lagrings namn.

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

### System. URI

### System. Management. Automation. PSCredential

## UTDATA

### PSGetRoleCapabilityInfo

`Find-RoleCapability`Cmdleten returnerar ett **PSGetRoleCapabilityInfo** -objekt.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Installera-modul](Install-Module.md)

[New-PSRoleCapabilityFile](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[Spara-modul](Save-Module.md)

