---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/install-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Script
ms.openlocfilehash: e2574121cc6b8500f0c5e9e0f76ac25d1c081a8c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889218"
---
# Install-Script

## SAMMANFATTNING
Installerar ett skript.

## SYNTAX

### NameParameterSet (standard)

```
Install-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Scope <String>] [-NoPathUpdate]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Install-Script [-InputObject] <PSObject[]> [-Scope <String>] [-NoPathUpdate] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Install-Script`Cmdlet: en hämtar en skript nytto Last från en lagrings plats, verifierar att nytto lasten är ett giltigt PowerShell-skript och kopierar skript filen till en angiven installations plats.

Standard databaserna `Install-Script` fungerar i kan konfigureras via `Register-PSRepository` `Set-PSRepository` `Unregister-PSRepository` cmdletarna,, och `Get-PSRepository` . När du arbetar med flera databaser `Install-Script` installerar det första skriptet som matchar de angivna Sök kriterierna (**namn**, **MinimumVersion** eller **MaximumVersion**) från den första lagrings platsen utan fel.

## EXEMPEL

### Exempel 1: hitta ett skript och installera det

```
PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2"
Version    Name                           Type       Repository           Description
-------    ----                           ----       ----------           -----------
2.5        Required-Script2               Script     local1               Description for the Required-Script2 script

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2" | Install-Script
PS C:\> Get-Command -Name "Required-Script2"
CommandType     Name                      Version    Source
-----------     ----                      -------    ------
ExternalScript  Required-Script2.ps1      2.0       C:\Users\pattif\Documents\WindowsPowerShell\Scripts\Required-Script2.ps1

PS C:\> Get-InstalledScript -Name "Required-Script2"
Version    Name                  Type     Repository           Description
-------    ----                  ----     ----------           -----------
2.5        Required-Script2      Script   local1               Description for the Required-Script2 script

PS C:\> Get-InstalledScript -Name "Required-Script2" | Format-List *
Name                       : Required-Script2
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:39 AM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Users\pattif\Documents\WindowsPowerShell\Scripts
```

Det första kommandot hittar skriptet som heter `Required-Script2` från Local1-lagringsplatsen och visar resultatet.

Det andra kommandot hittar `Required-Script2` skriptet och använder sedan pipeline-operatorn för att skicka det till `Install-Script` cmdlet: en för att installera det.

Det tredje kommandot använder `Get-Command` cmdleten för att hämta `Required-Script2` och visar resultatet.

Det fjärde kommandot använder `Get-InstalledScript` cmdleten för att hämta `Required-Script2` och visa resultaten.

Det femte kommandot hämtar `Required-Script2` och använder pipeline-operatorn för att skicka den till `Format-List` cmdlet: en för att formatera utdata.

### Exempel 2: installera ett skript med AllUsers-scope

```
PS C:\> Install-Script -Repository "Local1" -Name "Required-Script3" -Scope "AllUsers"
PS C:\> Get-InstalledScript -Name "Required-Script3"
Version    Name                  Type       Repository    Description
-------    ----                  ----       ----------    -----------
2.5        Required-Script3      Script     local1        Description for the Required-Script3 script

PS C:\> Get-InstalledScript -Name "Required-Script3" | Format-List *
Name                       : Required-Script3
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script3 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:45 AM
LicenseUri                 : http://required-script3.com/license
ProjectUri                 : http://required-script3.com/
IconUri                    : http://required-script3.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script3-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script3 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts
```

Det första kommandot installerar skriptet med namnet `Required-Script3` och tilldelar det allusers-omfånget.

Det andra kommandot hämtar det installerade skriptet `Required-Script3` och visar information om det.

Det tredje kommandot hämtar `Required-Script3` och använder pipeline-operatorn för att skicka den till `Format-List` cmdlet: en för att formatera utdata.

### Exempel 3: installera ett skript och dess beroenden

```
PS C:\> Find-Script -Repository "Local1" -Name "Script-WithDependencies2" -IncludeDependencies
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Script-WithDependencies2"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script

PS C:\> Get-InstalledModule
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script*"
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Required-Script*"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
```

Det första kommandot hittar skriptet med namnet `Script-WithDependencies2` och dess beroenden i Local1-lagringsplatsen och visar resultatet.

Det andra kommandot installeras `Script-WithDependencies2` .

Det tredje kommandot använder `Get-InstalledScript` skript-cmdleten för att hämta installerade skript och visa resultaten.

Det fjärde kommandot använder `Get-InstalledModule` cmdleten för att hämta installerade moduler och visa resultatet.

Det femte kommandot använder `Find-Script` cmdleten för att hitta skript där namnet börjar med `Required-Script` och visar resultatet.

Det sjätte kommandot installerar skripten där namnet börjar med `Required-Script` i Local1-lagringsplatsen.

Det sista kommandot hämtar installerade skript och visar resultatet.

## PARAMETRAR

### -AcceptLicense

Godkänn licens avtalet automatiskt under installationen om modulen kräver det.

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

### -AllowPrerelease

Gör att du kan installera ett skript som är markerat som en för hands version.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

### -Credential

Anger ett användar konto som har behörighet att installera ett skript för en angiven paket leverantör eller källa.

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

### – InputObject

Används för pipeline-ininformation.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### – MaximumVersion

Anger den högsta versionen av ett enstaka skript som ska installeras. Du kan inte lägga till den här parametern om du försöker installera flera skript. Parametrarna **MaximumVersion** och **RequiredVersion** kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – MinimumVersion

Anger den lägsta version av ett enskilt skript som ska installeras. Du kan inte lägga till den här parametern om du försöker installera flera skript. Parametrarna **MinimumVersion** och **RequiredVersion** kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger en matris med namn på skript som ska installeras.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoPathUpdate

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

### – PassThru

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

Anger det egna namnet på en lagrings plats som har registrerats med `Register-PSRepository` cmdleten. Standardvärdet är alla registrerade databaser.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – RequiredVersion

Anger det exakta versions numret för det skript som ska installeras.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Omfattning

Anger skriptets installations omfång.
Giltiga värden är: AllUsers och CurrentUser.

Med AllUsers omfattning kan moduler installeras på en plats som är tillgänglig för alla användare av datorn, det vill säga `$env:ProgramFiles\WindowsPowerShell\Scripts` .

I CurrentUser-scopet kan moduler endast installeras till `$home\Documents\WindowsPowerShell\Scripts` , så att modulen endast är tillgänglig för den aktuella användaren.

När inget **omfång** har definierats anges standardvärdet baserat på den aktuella sessionen:

- För en upphöjd **PowerShell-session** är standardvärdet allusers;
- För icke-förhöjda PowerShell-sessioner i [PowerShellGet-versioner 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) och senare, är **omfånget** CurrentUser;
- För icke-förhöjda PowerShell-sessioner i PowerShellGet-versioner 1.6.7 och tidigare, är **omfånget** odefinierat och `Install-Module` fungerar inte.

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

### -WhatIf

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

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

### System.String[]

### System. Management. Automation. PSObject []

### System. String

### System. URI

### System. Management. Automation. PSCredential

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

[Sök – skript](Find-Script.md)

[Publicera – skript](Publish-Script.md)

[Spara – skript](Save-Script.md)

[Avinstallera – skript](Uninstall-Script.md)

[Uppdatera skript](Update-Script.md)
