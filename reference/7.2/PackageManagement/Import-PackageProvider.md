---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 6c19d1cbc7b7e4dc37e24c466f83efae688f3cec
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889477"
---
# Import-PackageProvider

## SAMMANFATTNING
Lägger till leverantörer av paket hanterings paket i den aktuella sessionen.

## SYNTAX

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## BESKRIVNING

`Import-PackageProvider`Cmdleten lägger till en eller flera paket leverantörer i den aktuella sessionen.
Leverantören som du importerar måste vara installerad på den lokala datorn.

Kör om du vill hämta en lista över tillgängliga providers `Get-PackageProvider -ListAvailable` .
Observera att ett paket leverantörs namn kan skilja sig från dess modulnamn.

På grund av säkerhets skäl kräver **PackageManagement** C#-baserade providers för att innehålla en `provider.manifest` . Mer information om hur du skapar en Provider med `provider.manifest` inmatad finns i `.csproj` projektfilerna på [https://github.com/oneget/oneget](https://github.com/oneget/oneget) .

## EXEMPEL

### Exempel 1: importera en paket leverantör från den lokala datorn

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

Det här kommandot importerar NuGet-providern när den har installerats på den lokala datorn.

### Exempel 2: importera en angiven version av en paket leverantör

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

Det här kommandot hittar, installerar och importerar en angiven version av NuGet-paket leverantören.

## PARAMETRAR

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse.
Importerar en paket leverantör igen.

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

### – MaximumVersion

Anger den högsta tillåtna versionen av paket leverantören som du vill importera. Om du inte lägger till den här parametern `Import-PackageProvider` importeras den högsta tillgängliga versionen av providern.

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

Anger den lägsta tillåtna versionen av paket leverantören som du vill importera. Om du inte lägger till den här parametern `Import-PackageProvider` importeras den högsta tillgängliga versionen av paketet som också uppfyller den högsta version som anges med parametern *MaximumVersion* .

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

Anger ett eller flera paket leverantörs namn. Jokertecken är inte tillåtna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – RequiredVersion

Anger den exakta versionen av paket leverantören som du vill importera. Om du inte lägger till den här parametern `Import-PackageProvider` importeras den högsta tillgängliga versionen av providern som också uppfyller den högsta version som anges med parametern **MaximumVersion** .

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Microsoft. PackageManagement. implementation. PackageProvider

Du kan skicka vidare ett **PackageProvider** -objekt som returnerades av `Get-PackageProvider` till `Import-PackageProvider` .

## UTDATA

## ANTECKNINGAR

> [!IMPORTANT]
> Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1. Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet. Använd följande kommando för att se till att du använder TLS 1,2:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.

## RELATERADE LÄNKAR

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Unregister-PackageSource](Unregister-PackageSource.md)

[Get-PackageSource](Get-PackageSource.md)

[Registrera – PackageSource](Register-PackageSource.md)

[Get-PackageProvider](Get-PackageProvider.md)
