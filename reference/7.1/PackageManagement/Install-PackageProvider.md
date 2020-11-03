---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: ed69b50019b3393eeeda42a250d65d4dfb809a51
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266397"
---
# Install-PackageProvider

## SAMMANFATTNING
Installerar en eller flera leverantörer av paket hanterings paket.

## SYNTAX

### PackageBySearch (standard)

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### PackageByInputObject

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **install-PackageProvider** installerar matchande paket hanterings leverantörer som är tillgängliga i paket källor som registrerats med **PowerShellGet**.
Som standard inkluderar detta moduler som är tillgängliga i PowerShell-galleriet med taggen **PackageManagement** .
**PowerShellGet** paket hanterings leverantör används för att hitta leverantörer i dessa databaser.

Denna cmdlet installerar även matchande paket hanterings leverantörer som är tillgängliga med Start programmet för paket hantering.

Den här cmdleten installerar även matchande paket hanterings leverantörer som är tillgängliga i paket hantering Azure Blob Store.
Använd start program-providern för att hitta och installera dem.

För att kunna köra första gången kräver PackageManagement en Internet anslutning för att ladda ned NuGet-paket leverantören.
Men om datorn inte har någon Internet anslutning och du behöver använda NuGet-eller PowerShellGet-providern kan du hämta dem på en annan dator och kopiera dem till mål datorn.
Använd följande steg för att göra detta:

1.
Kör `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` för att installera providern från en dator med en Internet anslutning.

2.
Efter installationen kan du hitta providern som är installerad i `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` eller `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` .

3.
Placera \<ProviderName\> mappen, som i det här fallet är mappen NuGet, på motsvarande plats på mål datorn.
Om mål datorn är Nano Server måste du köra **install-PackageProvider** från Nano Server för att ladda ned rätt NuGet-binärfiler.

4.
Starta om PowerShell för att automatiskt läsa in paket leverantören.
Du kan också köra `Get-PackageProvider -ListAvailable` för att visa en lista över alla paket leverantörer som är tillgängliga på datorn.
Använd sedan `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` för att importera providern till den aktuella PowerShell-sessionen.

## EXEMPEL

### Exempel 1: installera en Package provider från PowerShell-galleriet

```
PS C:\> Install-PackageProvider -Name "Gistprovider" -Verbose
```

Det här kommandot installerar Gistprovider från PowerShell-galleriet.

### Exempel 2: installera en angiven version av en paket leverantör

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
PS C:\> Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.216" -Force
```

I det här exemplet installeras en angiven version av NuGet-paket leverantören.

Det första kommandot hittar alla versioner av paket leverantören som heter NuGet.
Det andra kommandot installerar en angiven version av NuGet-paket leverantören.

### Exempel 3: hitta en provider och installera den

```
PS C:\> Find-PackageProvider -Name "Gistprovider" | Install-PackageProvider -Verbose
```

Det här kommandot använder **find-PackageProvider** och pipelinen för att söka efter registrerings enheten och installera den.

### Exempel 4: installera en provider till den aktuella användarens modul-mapp

```
PS C:\> Install-PackageProvider -Name Gistprovider -Verbose -Scope CurrentUser
```

Det här kommandot installerar en paket leverantör som $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies så att endast den aktuella användaren kan använda den.

## PARAMETRAR

### -AllVersions

Anger att denna cmdlet installerar alla tillgängliga versioner av paket leverantören.
Som standard returnerar **install-PackageProvider** endast den senaste tillgängliga versionen.

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

### -Credential

Anger ett användar konto som har behörighet att installera paket leverantörer.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Anger att denna cmdlet tvingar alla åtgärder med denna cmdlet som kan tvingas.
För närvarande innebär detta att *Force* -parametern fungerar på samma sätt som parametern *ForceBootstrap* .

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

Anger att paket leverantören installeras automatiskt av den här cmdleten.

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

### – InputObject

Anger ett **SoftwareIdentity** -objekt.
Använd **find-PackageProvider** -cmdlet: en för att hämta ett **SoftwareIdentity** -objekt till pipe i **install-PackageProvider**.

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – MaximumVersion

Anger den högsta tillåtna versionen av paket leverantören som du vill installera.
Om du inte lägger till den här parametern installerar **install-PackageProvider** den högsta tillgängliga versionen av providern.

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – MinimumVersion

Anger den lägsta tillåtna versionen av paket leverantören som du vill installera.
Om du inte lägger till den här parametern installerar **install-PackageProvider** den högsta tillgängliga versionen av paketet som också uppfyller eventuella krav som anges av parametern *MaximumVersion* .

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger ett eller flera namn på moduler för paket leverantör.
Separera flera paket namn med kommatecken.
Jokertecken stöds inte.

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Proxy

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – RequiredVersion

Anger den exakta versionen av paket leverantören som du vill installera.
Om du inte lägger till den här parametern installerar **install-PackageProvider** den högsta tillgängliga versionen av providern som också uppfyller den högsta version som anges av parametern *MaximumVersion* .

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Omfattning

Anger providerns installations omfång.
De acceptabla värdena för den här parametern är: **allusers** och **CurrentUser**.

**Allusers** -scopet installerar providrar på en plats som är tillgänglig för alla användare av datorn.
Som standard är detta **$env:P rogramfiles\packagemanagement\providerassemblies.**

**CurrentUser** -scopet installerar providrar på en plats där de endast är tillgängliga för den aktuella användaren.
Som standard är detta **$env: LOCALAPPDATA\PackageManagement\ProviderAssemblies.**

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

### -Source

Anger en eller flera paket källor.
Använd Get-PackageSource-cmdlet för att hämta en lista över tillgängliga paket källor.

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### Microsoft. PackageManagement. packning. SoftwareIdentity

Du kan skicka ett **SoftwareIdentity** -objekt till denna cmdlet.
Använd Find-PackageProvider för att hämta ett **SoftwareIdentity** -objekt som kan skickass till **install-PackageProvider**.

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Find-PackageProvider](Find-PackageProvider.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Importera – PackageProvider](Import-PackageProvider.md)

