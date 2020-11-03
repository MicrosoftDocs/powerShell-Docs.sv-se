---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-packageprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-PackageProvider
ms.openlocfilehash: 664e6064580f9212c25632a1146d1ac67f2308bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264279"
---
# Find-PackageProvider

## SAMMANFATTNING
Returnerar en lista med paket hanterings paket leverantörer som är tillgängliga för installation.

## SYNTAX

```
Find-PackageProvider [[-Name] <String[]>] [-AllVersions] [-Source <String[]>] [-IncludeDependencies]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **find-PackageProvider** hittar matchande PackageManagement-providers som är tillgängliga i paket källor som registrerats med PowerShellGet.
Detta är paket leverantörer som är tillgängliga för installation med cmdleten Install-PackageProvider.
Som standard inkluderar detta moduler som är tillgängliga i PowerShell-galleriet med taggarna **PackageManagement** och **Provider** .

**Find-PackageProvider** hittar också matchande paket hanterings leverantörer som är tillgängliga i paket hantering Azure Blob Store.
Använd start program-providern för att hitta och installera dem.

## EXEMPEL

### Exempel 1: Sök efter alla tillgängliga paket leverantörer

```
PS C:\> Find-PackageProvider
```

Det här kommandot hämtar en lista över alla paket leverantörer som är tillgängliga i de databaser som stöds av paket hantering.
Som standard är dessa paket leverantörer tillgängliga på PowerShell-galleriet och med hjälp av Start programmet för paket hantering.

### Exempel 2: hitta alla versioner av en provider

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
```

Det här kommandot hittar alla versioner av paket leverantören som heter NuGet.

### Exempel 3: hitta en provider från en angiven källa

```
PS C:\> Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

Det här kommandot hittar en paket leverantör som är tillgänglig med hjälp av en angiven paket källa.

## PARAMETRAR

### -AllVersions

Anger att denna cmdlet returnerar alla tillgängliga versioner av paket leverantören.
Som standard returnerar **find-PackageProvider** endast den senaste tillgängliga versionen.

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

Anger ett användar konto som har behörighet att söka efter paket leverantörer.

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

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse.
Detta motsvarar för närvarande parametern *ForceBootstrap* .

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

Anger att den här cmdleten tvingar paket hantering att automatiskt installera paket leverantören.

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

### -IncludeDependencies

Anger att denna cmdlet innehåller beroenden.

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

### – MaximumVersion

Anger den högsta tillåtna versionen av paket leverantören som du vill hitta.
Om du inte lägger till den här parametern söker **find-PackageProvider** efter den högsta tillgängliga versionen av providern.

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

Anger den lägsta tillåtna versionen av paket leverantören som du vill hitta.
Om du inte lägger till den här parametern hittar **find-PackageProvider** den högsta tillgängliga versionen av paketet som också uppfyller den högsta version som anges av parametern *MaximumVersion* .

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

Anger ett eller flera namn på en paket leverantör, eller namn på providrar med jokertecken.
Separera flera paket namn med kommatecken.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
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
Accept pipeline input: False
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
Accept pipeline input: False
Accept wildcard characters: False
```

### – RequiredVersion

Anger den exakta versionen av paket leverantören som du vill hitta.
Om du inte lägger till den här parametern söker **find-PackageProvider** efter den högsta tillgängliga versionen av providern som också uppfyller den högsta version som anges av parametern *MaximumVersion* .

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

### -Source

Anger en eller flera paket källor.
Du kan hämta en lista över tillgängliga paket källor med hjälp av Get-PackageSource-cmdleten.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

### Microsoft. PackageManagement. packning. SoftwareIdentity

Denna cmdlet returnerar ett **SoftwareIdentity** -objekt.
Ett **SoftwareIdentity** -objekt kan skickas till **install-PackageProvider** för att installera resultaten av **find-PackageProvider**.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Unregister-PackageSource](Unregister-PackageSource.md)

[Get-PackageSource](Get-PackageSource.md)

[Registrera – PackageSource](Register-PackageSource.md)

[Installera-PackageProvider](Install-PackageProvider.md)

