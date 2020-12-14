---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: d62144be2b3d498e794dbde425313ee0f619efca
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890550"
---
# Get-PackageProvider

## SAMMANFATTNING
Returnerar en lista med paket leverantörer som är anslutna till paket hantering.

## SYNTAX

```
Get-PackageProvider [[-Name] <String[]>] [-ListAvailable] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## BESKRIVNING

Cmdlet **: en get-PackageProvider** returnerar en lista med paket leverantörer som är anslutna till paket hantering.
Exempel på dessa leverantörer är PSModule, NuGet och choklad.
Du kan filtrera resultaten baserat på hela eller delar av ett eller flera providernamn.

## EXEMPEL

### Exempel 1: Hämta alla paket leverantörer som har lästs in

```
PS C:\> Get-PackageProvider
```

Det här kommandot hämtar en lista över alla paket leverantörer som för närvarande har lästs in på den lokala datorn.

### Exempel 2: Hämta alla tillgängliga paket leverantörer

```
PS C:\> Get-PackageProvider -ListAvailable
```

Det här kommandot hämtar en lista över alla paket leverantörer som är tillgängliga på den lokala datorn.

### Exempel 3: Hämta en paket leverantör dynamiskt

```
PS C:\> Get-PackageProvider -Name "Chocolatey" -ForceBootstrap
```

Med det här kommandot installeras choklad leverantören automatiskt om datorn inte har någon choklad-Provider installerad.

## PARAMETRAR

### -Force

Anger att denna cmdlet tvingar alla andra åtgärder med denna cmdlet som kan tvingas.
I **Get-PackageProvider** innebär detta att *Force* -parametern fungerar på samma sätt som parametern *ForceBootstrap* .

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

### – ListAvailable

Hämtar alla installerade providrar.
**Get-PackageProvider** hämtar providern i sökvägar som anges i miljövariabeln **PSModulePath** och paket providerns Assembly-mappar:

**$env:P rogramfiles\packagemanagement\providerassemblies** **$env: LOCALAPPDATA\PackageManagement\ProviderAssemblies**

Utan den här parametern hämtar **Get-PackageProvider** bara de providrar som lästs in i den aktuella sessionen.

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

### -Name

Anger ett eller flera providernamn eller delar av leverantörs namn.
Separera flera providernamn med kommatecken.
Giltiga värden för den här parametern är namn på leverantörer som du har installerat med paket. PackageManagement levereras med en uppsättning standard leverantörer, inklusive **PSModule** -och **MSI** -providers.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

### PackageProvider[]

## ANTECKNINGAR

> [!IMPORTANT]
> Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1. Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet. Använd följande kommando för att se till att du använder TLS 1,2:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.

## RELATERADE LÄNKAR

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Get-PackageSource](Get-PackageSource.md)

[Registrera – PackageSource](Register-PackageSource.md)

[Unregister-PackageSource](Unregister-PackageSource.md)
