---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/register-psrepository?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSRepository
ms.openlocfilehash: 07f70f4fad6057ad689befaafd1d41f819a4538c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892771"
---
# Register-PSRepository

## SAMMANFATTNING
Registrerar en PowerShell-lagringsplats.

## SYNTAX

### NameParameterSet (standard)

```
Register-PSRepository [-Name] <String> [-SourceLocation] <Uri> [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

### PSGalleryParameterSet

```
Register-PSRepository [-Default] [-InstallationPolicy <String>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [<CommonParameters>]
```

## BESKRIVNING

`Register-PSRepository`Cmdleten registrerar standard lagrings platsen för PowerShell-moduler. När en lagrings plats har registrerats kan du referera till den från `Find-Module` `Install-Module` cmdletarna,, och `Publish-Module` . Den registrerade lagrings platsen blir standard lagrings platsen i `Find-Module` och `Install-Module` .

Registrerade databaser är användarspecifika. De är inte registrerade i en systemövergripande kontext.

Varje registrerad databas är associerad med en OneGet-paket leverantör som anges med parametern **PackageManagementProvider** . Varje OneGet-Provider är utformad för att samverka med en speciell typ av lagrings plats. NuGet-providern är till exempel utformad för att samverka med NuGet-baserade databaser. Om en OneGet-Provider inte anges under registreringen försöker PowerShellGet hitta en OneGet-provider som kan hantera den angivna käll platsen.

## EXEMPEL

### Exempel 1: registrera en lagrings plats

```powershell
$parameters = @{
  Name = "myNuGetSource"
  SourceLocation = "https://www.myget.org/F/powershellgetdemo/api/v2"
  PublishLocation = "https://www.myget.org/F/powershellgetdemo/api/v2/Packages"
  InstallationPolicy = 'Trusted'
}
Register-PSRepository @parameters
Get-PSRepository
```

```Output
Name                SourceLocation          OneGetProvider       InstallationPolicy
----                --------------          --------------       ------------------
PSGallery           http://go.micro...      NuGet                Untrusted
myNuGetSource       https://myget.c...      NuGet                Trusted
```

Det första kommandot registreras `https://www.myget.org/F/powershellgetdemo/` som en lagrings plats för den aktuella användaren. När myNuGetSource har registrerats kan du uttryckligen referera till den när du söker efter, installerar och publicerar moduler. Eftersom parametern **PackageManagementProvider** inte anges är lagrings platsen inte uttryckligen kopplad till en OneGet-paket leverantör, så PowerShellGet avsöker tillgängliga paket leverantörer och kopplar den till NuGet-providern.

Det andra kommandot hämtar registrerade databaser och visar resultatet.

## PARAMETRAR

### -Credential

Anger autentiseringsuppgifter för ett konto som har behörighet att registrera en lagrings plats.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Default

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PSGalleryParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstallationPolicy

Anger installations principen. Giltiga värden är: betrodda, ej betrodda. Standardvärdet är inte betrott.

En plats installations princip anger PowerShell-beteende när du installerar från den lagrings platsen. När du installerar moduler från ett ej betrott lager, uppmanas användaren att bekräfta.

Du kan ställa in **InstallationPolicy** med `Set-PSRepository` cmdleten.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Trusted, Untrusted

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger namnet på den lagrings plats som ska registreras. Du kan använda det här namnet för att ange lagrings platsen i-cmdlet: ar, till exempel `Find-Module` och `Install-Module` .

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

Anger en OneGet-paket leverantör. Om du inte anger något värde för den här parametern avsöker PowerShellGet de tillgängliga paket leverantörer och kopplar den här lagrings platsen till den första paket leverantören som anger att den kan hantera lagrings platsen.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

### -PublishLocation

Anger URI för publicerings platsen. För NuGet-baserade databaser liknar publicerings platsen till exempel `https://someNuGetUrl.com/api/v2/Packages` .

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptPublishLocation

Anger skriptets publicerings plats.

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptSourceLocation

Anger sökvägen till skript källan.

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – SourceLocation

Anger URI för identifiering och installation av moduler från den här lagrings platsen. En URI kan vara en NuGet Server-feed (den vanligaste situationen), HTTP, HTTPS, FTP eller File location.

För NuGet-baserade databaser liknar till exempel käll platsen `https://someNuGetUrl.com/api/v2` .

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSCredential

### System. URI

## UTDATA

### System. Object

## ANTECKNINGAR

> [!IMPORTANT]
> Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1. Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet. Använd följande kommando för att se till att du använder TLS 1,2:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.

## RELATERADE LÄNKAR

[Get-PSRepository](Get-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Avregistrera-PSRepository](Unregister-PSRepository.md)
