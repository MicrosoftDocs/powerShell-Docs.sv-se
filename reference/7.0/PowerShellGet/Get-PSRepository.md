---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: cc92188384497b5e7534e3dc7daa4fc73c314a36
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262293"
---
# Get-PSRepository

## SAMMANFATTNING
Hämtar PowerShell-databaser.

## SYNTAX

```
Get-PSRepository [[-Name] <String[]>] [<CommonParameters>]
```

## BESKRIVNING

Cmdlet **: en get-PSRepository** hämtar PowerShell-modulens databaser som är registrerade för den aktuella användaren.

## EXEMPEL

### Exempel 1: Hämta alla modul databaser

```
PS C:\> Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

Det här kommandot hämtar alla modul-dataarkiv som registrerats för den aktuella användaren.

### Exempel 2: Hämta modul Arkiv efter namn

```
PS C:\> Get-PSRepository -Name "*NuGet*"
```

Det här kommandot hämtar alla modulblad som innehåller NuGet i sina namn.

### Exempel 3: Hämta en modul-lagringsplats och formatera utdata

```
PS C:\> Get-PSRepository -Name "Local01" | Format-List * -Force
Name                      : local01
SourceLocation            : http://manikb-dev:8765/api/v2/
Trusted                   : True
Registered                : True
InstallationPolicy        : Trusted
PackageManagementProvider : NuGet
PublishLocation           : http://pattif-dev:8765/api/v2/package/
ScriptSourceLocation      : http://pattif-dev:8765/api/v2/artifacts/psscript
ScriptPublishLocation     : http://pattif-dev:8765/api/v2/package/
ProviderOptions           : {}
```

Det här kommandot hämtar lagrings platsen med namnet Local01 och använder pipelinen-operatorn för att skicka objektet till Format-List-cmdleten.

## PARAMETRAR

### -Name

Anger namnen på de databaser som ska hämtas.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System.String[]

## UTDATA

### System. Object

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Registrera – PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Avregistrera-PSRepository](Unregister-PSRepository.md)
