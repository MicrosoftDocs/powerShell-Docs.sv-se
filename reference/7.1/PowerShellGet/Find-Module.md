---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Module
ms.openlocfilehash: 22ac0b5651ffa9f055a5c436f56711dc33f95f6e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266348"
---
# Find-Module

## SAMMANFATTNING
Söker efter moduler i en lagrings plats som matchar de angivna kriterierna.

## SYNTAX

### Alla

```
Find-Module [[-Name] <string[]>] [-MinimumVersion <string>] [-MaximumVersion <string>]
 [-RequiredVersion <string>] [-AllVersions] [-IncludeDependencies] [-Filter <string>]
 [-Tag <string[]>] [-Includes <string[]>] [-DscResource <string[]>] [-RoleCapability <string[]>]
 [-Command <string[]>] [-Proxy <uri>] [-ProxyCredential <pscredential>] [-Repository <string[]>]
 [-Credential <pscredential>] [-AllowPrerelease] [<CommonParameters>]
```

## BESKRIVNING

`Find-Module`Cmdleten söker efter moduler i en lagrings plats som matchar de angivna kriterierna.
`Find-Module` Returnerar ett **PSRepositoryItemInfo** -objekt för varje modul som hittas. Objekten kan skickas ned pipelinen till-cmdlet: ar, till exempel `Install-Module` .

Första gången du `Find-Module` försöker använda en lagrings plats kan du uppmanas att installera uppdateringar.
Om lagrings platsen inte har registrerats med `Register-PSRepository` cmdleten returneras ett fel.

`Find-Module` Returnerar den nyaste versionen av en modul om inga parametrar används som begränsar versionen. Om du vill hämta en lista över en moduls versioner använder du parametern **AllVersions**.

Om parametern **MinimumVersion** anges `Find-Module` returnerar modulens version som är lika med eller större än minimivärdet. Om det finns en nyare version som är tillgänglig i lagrings platsen returneras den nya versionen.

Om parametern **MaximumVersion** anges `Find-Module` returnerar den nyaste versionen av modulen som inte överskrider den angivna versionen.

Om parametern **RequiredVersion** anges `Find-Module` returnerar endast den version som är en exakt matchning till den angivna versionen. `Find-Module` söker igenom alla tillgängliga moduler eftersom namn konflikter mellan källor kan uppstå.

I följande exempel används [PowerShell-galleriet](https://www.powershellgallery.com/) som den enda registrerade lagrings platsen. `Get-PSRepository` visar de registrerade databaserna. Om du har flera registrerade databaser använder du `-Repository` parametern för att ange namnet på lagrings platsen.

## EXEMPEL

### Exempel 1: hitta en modul efter namn

I det här exemplet hittas en modul i standard lagrings platsen.

```powershell
Find-Module -Name PowerShellGet
```

```Output
Version   Name              Repository           Description
-------   ----              ----------           -----------
2.1.0     PowerShellGet     PSGallery            PowerShell module with commands for discovering...
```

`Find-Module`Cmdleten använder **Name** -parametern för att ange **PowerShellGet** -modulen.

### Exempel 2: hitta moduler med liknande namn

I det här exemplet används jokertecknet asterisk ( `*` ) för att hitta moduler med liknande namn.

```powershell
Find-Module -Name PowerShell*
```

```Output
Version   Name                            Repository    Description
-------   ----                            ----------    -----------
0.4.0     powershell-yaml                 PSGallery     Powershell module for serializing and...
2.1.0     PowerShellGet                   PSGallery     PowerShell module with commands for...
1.9       Powershell.Helper.Extension     PSGallery     # Powershell.Helper.Extension...
3.1       PowerShellHumanizer             PSGallery     PowerShell Humanizer wraps Humanizer...
4.0       PowerShellISEModule             PSGallery     a module that adds capability to the ISE
```

`Find-Module`Cmdleten använder **Name** -parametern med jokertecknet asterisk ( `*` ) för att hitta alla moduler som innehåller **PowerShell**.

### Exempel 3: hitta en modul efter lägsta version

Det här exemplet söker efter en moduls lägsta version. Om lagrings platsen innehåller en nyare version av modulen returneras den nya versionen.

```powershell
Find-Module -Name PowerShellGet -MinimumVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

`Find-Module`Cmdleten använder **Name** -parametern för att ange **PowerShellGet** -modulen. **MinimumVersion** anger version **1.6.5**. `Find-Module` Returnerar PowerShellGet version **2.1.0** eftersom den överskrider den lägsta versionen och den mest aktuella versionen.

### Exempel 4: hitta en modul efter en version

Det här exemplet returnerar ett objekt som representerar en moduls aktuella version. Om den angivna versionen inte hittas returneras ett fel.

```powershell
Find-Module -Name PowerShellGet -RequiredVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
1.6.5     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

`Find-Module`Cmdleten använder **Name** -parametern för att ange **PowerShellGet** -modulen. Parametern **RequiredVersion** anger version **1.6.5**.

### Exempel 5: hitta en modul i ett särskilt lager

I det här exemplet används parametern **lagrings plats** för att hitta en modul i en angiven lagrings plats.

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

`Find-Module`Cmdleten använder **Name** -parametern för att ange **PowerShellGet** -modulen. Parametern för **lagrings platsen** anger att söka i **PSGallery** -lagringsplatsen.

### Exempel 6: hitta en modul i flera databaser

I det här exemplet används `Register-PSRepository` för att ange en lagrings plats. `Find-Module` använder lagrings platsen för att söka efter en modul.

```powershell
Register-PSRepository -Name MySource -SourceLocation https://www.myget.org/F/powershellgetdemo/
Find-Module -Name Contoso* -Repository PSGallery, MySource
```

```Output
Repository    Version   Name             Description
----------    -------   ----             -----------
PSGallery     2.0.0.0   ContosoServer    Cmdlets and DSC resources for managing Contoso Server...
MySource      1.2.0.0   ContosoClient    Cmdlets and DSC resources for managing Contoso Client...
```

`Register-PSRepository`Cmdleten registrerar en ny lagrings plats. Parametern **Name** tilldelar namnet **källa**. Parametern **SourceLocation** anger lagrings platsens adress.

`Find-Module`Cmdleten använder **Name** -parametern med jokertecknet asterisk ( `*` ) för att ange **contoso** -modulen. Parametern **lagrings plats** anger för att söka i två databaser, **PSGallery** och **källa**.

### Exempel 7: hitta en modul som innehåller en DSC-resurs

Det här kommandot returnerar moduler som innehåller DSC-resurser. Parametern **includes** har fyra fördefinierade funktioner som används för att söka i lagrings platsen. Använd Tabb-Complete för att visa de fyra funktionerna som stöds av parametern **includes** .

```powershell
Find-Module -Repository PSGallery -Includes DscResource
```

```Output
Version     Name                            Repository    Description
-------     ----                            ----------    -----------
2.7.0       Carbon                          PSGallery     Carbon is a PowerShell module...
8.5.0.0     xPSDesiredStateConfiguration    PSGallery     The xPSDesiredStateConfiguration module...
1.3.1       PackageManagement               PSGallery     PackageManagement (a.k.a. OneGet) is...
2.7.0.0     xWindowsUpdate                  PSGallery     Module with DSC Resources...
3.2.0.0     xCertificate                    PSGallery     This module includes DSC resources...
3.1.0.0     xPowerShellExecutionPolicy      PSGallery     This DSC resource can change the user...
```

`Find-Module`Cmdlet: en använder parametern **lagrings plats** för att söka i lagrings platsen, **PSGallery**.
Parametern **includes** anger **dscresource Keyword Supports** , som är en funktion som parametern kan söka efter i lagrings platsen.

### Exempel 8: hitta en modul med ett filter

I det här exemplet används ett filter för att söka efter moduler.

För en NuGet-baserad lagring söker **filter** parametern igenom igenom namnet, beskrivningen och taggarna för argumentet.

```powershell
Find-Module -Filter AppDomain
```

```Output
Version    Name              Repository           Description
-------    ----              ----------           -----------
1.0.0.0  AppDomainConfig     PSGallery            Manipulate AppDomain configuration...
1.1.0    ClassExplorer       PSGallery            Quickly search the AppDomain for classes...
```

`Find-Module`Cmdleten använder **filter** parametern för att söka i lagrings platsen för **AppDomain**.

## PARAMETRAR

### -AllowPrerelease

Innehåller i de resultat moduler som marker ATS som en för hands version.

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

Anger om du vill inkludera alla versioner av en modul i resultaten. Du kan inte använda parametern **AllVersions** med parametrarna **MinimumVersion** , **MaximumVersion** eller **RequiredVersion** .

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

### -Kommando

Anger en matris med kommandon som ska hittas i moduler. Ett kommando kan vara en funktion eller ett arbets flöde.

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

### -Credential

Anger ett användar konto som har behörighet att installera en modul för en angiven paket leverantör eller källa.

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

### – Dscresource Keyword Supports

Anger namnet eller en del av namnet på moduler som innehåller DSC-resurser. Per PowerShell-konventioner utför en **eller** -sökning när du anger flera argument.

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

### -Filter

Anger ett filter baserat på **PackageManagement** -providerspecifika söksyntax. För NuGet-moduler är den här parametern motsvarigheten till sökning med hjälp av Sök fältet på [PowerShell-galleriet](https://www.powershellgallery.com/) webbplats.

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

### -IncludeDependencies

Anger att den här åtgärden inkluderar alla moduler som är beroende av den modul som anges i parametern **Name** .

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

### – Innehåller

Returnerar bara de moduler som innehåller vissa typer av PowerShell-funktioner. Till exempel kanske du bara vill hitta moduler som innehåller **dscresource Keyword Supports**. De acceptabla värdena för den här parametern är följande:

- Cmdlet
- Dscresource Keyword Supports
- Funktion
- RoleCapability

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: DscResource, Cmdlet, Function, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – MaximumVersion

Anger den maximala eller senaste versionen av modulen som ska ingå i Sök resultaten.
Det går inte att använda **MaximumVersion** och **RequiredVersion** i samma kommando.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – MinimumVersion

Anger den lägsta version av modulen som ska tas med i resultaten. Det går inte att använda **MinimumVersion** och **RequiredVersion** i samma kommando.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger namnen på de moduler som ska sökas efter i lagrings platsen. En kommaavgränsad lista med Modulnamn accepteras. Jokertecken accepteras.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Proxy

Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.

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

Använd parametern **lagrings plats** för att ange vilken lagrings plats som ska sökas efter en modul. Används när flera databaser har registrerats. Accepterar en kommaavgränsad lista över databaser. Använd om du vill registrera en lagrings plats `Register-PSRepository` . Använd om du vill visa registrerade databaser `Get-PSRepository` .

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

Anger det exakta versions numret för den modul som ska tas med i resultaten. **RequiredVersion** kan inte användas i samma kommando som **MinimumVersion** eller **MaximumVersion**.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RoleCapability

Anger en matris med roll funktioner.

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

### -Tagga

Anger en matris med taggar. Exempel taggar är **DesiredStateConfiguration** , **DSC** , **DSCResourceKit** eller **PSModule**.

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

### System.String[]

### System. String

### System. URI

### System. Management. Automation. PSCredential

## UTDATA

### PSRepositoryItemInfo

`Find-Module` skapar **PSRepositoryItemInfo** -objekt som kan skickas ned pipelinen till-cmdlet: ar, till exempel `Install-Module` .

## ANTECKNINGAR

Denna cmdlet körs på PowerShell 5,0 eller senare versioner av PowerShell, på Windows 7 eller Windows 2008 R2 och senare versioner av Windows.

## RELATERADE LÄNKAR

[Get-PSRepository](Get-PSRepository.md)

[Installera-modul](Install-Module.md)

[Publicera-modul](Publish-Module.md)

[Spara-modul](Save-Module.md)

[Avinstallera-modul](Uninstall-Module.md)

[Update-modul](Update-Module.md)

[Registrera – PSRepository](Register-PSRepository.md)

