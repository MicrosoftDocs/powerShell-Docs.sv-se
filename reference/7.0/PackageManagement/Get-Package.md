---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: c6604b06f8ff971bc18d9811bd23b6932b9f414c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262466"
---
# Get-Package

## SAMMANFATTNING
Returnerar en lista med alla program varu paket som har installerats med **PackageManagement**.

## SYNTAX

### NuGet

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### PowerShellGet

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## BESKRIVNING

`Get-Package`Cmdleten returnerar en lista över alla program varu paket på den lokala datorn som installerades med **PackageManagement**. Du kan köra `Get-Package` på fjärrdatorer genom att köra den som en del av ett `Invoke-Command` `Enter-PSSession` kommando eller skript.

## EXEMPEL

### Exempel 1: Hämta alla installerade paket

`Get-Package`Cmdlet: en hämtar alla paket som är installerade på den lokala datorn.

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### Exempel 2: Hämta paket som är installerade på en fjärrdator

Det här kommandot hämtar en lista över paket som har installerats av **PackageManagement** på en fjärrdator. Med det här kommandot kan du ange användarens lösen ord.

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

`Invoke-Command` använder parametern **computername** för att ange en fjärrdator, **Server01**. Parametern **Credential** anger en domän och ett användar namn med behörigheter att köra kommandon på datorn. Parametern **script block** kör `Get-Package` cmdleten på fjärrdatorn.

### Exempel 3: Hämta paket för en angiven Provider

Detta kommando hämtar program varu paket som är installerade på den lokala datorn från en speciell Provider.

```powershell
Get-Package -ProviderName PowerShellGet -AllVersions
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.2.2        https://www.powershellgallery.com/api/v2   PowerShellGet
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
posh-git              0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
PowerShellGet         2.0.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

`Get-Package` använder parametern **ProviderName** för att ange en speciell Provider, **PowerShellGet**.
Parametern **alla-versioner** visar varje version som är installerad.

### Exempel 4: Hämta en exakt version av ett visst paket

Det här kommandot hämtar en angiven version av ett installerat paket. Mer än en version av ett paket kan installeras.

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

`Get-Package` använder parametern **Name** för att ange paket namnet, **PackageManagement**. Parametern **ProviderName** anger providern, **PowerShellGet**. Den **obligatoriska version-** parametern anger en installerad version.

### Exempel 5: Avinstallera ett paket

Det här exemplet hämtar paket information och avinstallerar sedan paketet.

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

`Get-Package` använder **Name** -parametern för att ange paket namnet, **posh-git**. Parametern **RequiredVersion** är en angiven version av paketet. Objektet skickas ned pipelinen till `Uninstall-Package` cmdleten. `Uninstall-Package` tar bort paketet.

## PARAMETRAR

### -AllowClobber

Åsidosätter varnings meddelanden om konflikter med befintliga kommandon. Skriver över befintliga kommandon som har samma namn som kommandon som installeras av en modul.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowPrereleaseVersions

Innehåller paket som marker ATS som en för hands version i resultaten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllVersions

Anger att `Get-Package` returnerar alla tillgängliga versioner av paketet. Som standard `Get-Package` returnerar endast den senaste tillgängliga versionen.

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

### -Mål

Anger sökvägen till en katalog som innehåller extraherade paketfiler.

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExcludeVersion

Byt för att utesluta versions numret i mappsökvägen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
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

### -ForceBootstrap

Anger att `Get-Package` paket leverantören ska installeras automatiskt av **PackageManagement** .

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

### -InstallUpdate

Anger att den här cmdleten installerar uppdateringar.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – MaximumVersion

Anger den maximala paket version som du vill söka efter.

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

Anger den minsta paket version som du vill söka efter. Om det finns en senare version returneras den versionen.

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

Anger ett eller flera paket namn, eller paket namn med jokertecken. Separera flera paket namn med kommatecken.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -NoPathUpdate

**NoPathUpdate** gäller endast för `Install-Script` cmdlet. **NoPathUpdate** är en dynamisk parameter som lagts till av providern och som inte stöds av `Get-Package` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

Anger namnet på en paket hanterings leverantör.

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

Anger ett eller flera paket leverantörs namn. Separera namn på flera paket leverantörer med kommatecken.
Använd `Get-PackageProvider` för att hämta en lista över tillgängliga paket leverantörer.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – RequiredVersion

Anger den exakta versionen av paketet som ska hittas.

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

### – Omfattning

Anger Sök omfånget för paketet.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipDependencies

Växel som anger att sökning efter eventuella paket beroenden ska hoppas över.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipPublisherCheck

Gör att du kan hämta en paket version som är nyare än den installerade versionen. Till exempel ett installerat paket som har signerats digitalt av en betrodd utgivare, men en ny version inte har signerats digitalt.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Typ

Anger om du vill söka efter paket med en modul, ett skript eller något av alternativen.

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Module, Script, All

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

### SoftwareIdentity []

## ANTECKNINGAR

Att inkludera en paket leverantör i ett kommando kan göra dynamiska parametrar tillgängliga för en cmdlet. Dynamiska parametrar är speciella för en paket leverantör. `Get-Help`Cmdleten listar en cmdlets parameter uppsättningar och inkluderar providerns parameter uppsättning. Till exempel `Get-Package` har **PowerShellGet** parameter uppsättning som innehåller `-NoPathUpdate` , `AllowClobber` , och `SkipPublisherCheck` .

## RELATERADE LÄNKAR

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Retur-PSSession](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[Sök-paket](Find-Package.md)

[Get – hjälp](../Microsoft.PowerShell.Core/Get-Help.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Get-PackageSource](Get-PackageSource.md)

[Installationspaket](Install-Package.md)

[Invoke-kommando](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Spara paket](Save-Package.md)

[Avinstallera paket](Uninstall-Package.md)
