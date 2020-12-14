---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Module
ms.openlocfilehash: f167990361a332f3b6f696d934e5d2835de849ed
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892628"
---
# Publish-Module

## SAMMANFATTNING
Publicerar en angiven modul från den lokala datorn till ett onlinegalleri.

## SYNTAX

### ModuleNameParameterSet (standard)

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ModulePathParameterSet

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Publish-Module`Cmdleten publicerar en modul till ett NuGet-baserat galleri med hjälp av en API-nyckel som lagras som en del av en användar profil i galleriet. Du kan ange vilken modul som ska publiceras antingen av modulens namn eller efter sökvägen till mappen som innehåller modulen.

När du anger en modul efter namn, `Publish-Module` publicerar den första modulen som skulle hittas genom att köra `Get-Module -ListAvailable <Name>` . Om du anger en lägsta version av en modul som ska publiceras, `Publish-Module` publicerar den första modulen med en version som är större än eller lika med den lägsta version som du har angett.

Att publicera en modul kräver metadata som visas på Galleri sidan för modulen. Obligatoriska metadata innehåller modulens namn, version, beskrivning och författare. Även om de flesta metadata tas från modulens manifest, måste vissa metadata anges i `Publish-Module` parametrar, till exempel **tag**, **ReleaseNote**, **IconUri**, **ProjectUri** och **LicenseUri**, eftersom dessa parametrar matchar fält i ett NuGet-baserat Galleri.

## EXEMPEL

### Exempel 1: publicera en modul

I det här exemplet publiceras MyDscModule i online-galleriet med hjälp av API-nyckeln för att ange module-kontots onlinegalleri. Om MyDscModule inte är en giltig manifest-modul som anger namn, version, beskrivning och författare inträffar ett fel.

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### Exempel 2: publicera en modul med metadata för galleriet

I det här exemplet publiceras MyDscModule i online-galleriet med hjälp av API-nyckeln för att ange modulens ägares Galleri konto. De ytterligare metadata som anges visas på webb sidan för modulen i galleriet. Ägaren lägger till två söktaggar för modulen, relaterad den till Active Directory. en kort versions anteckning har lagts till. Om MyDscModule inte är en giltig manifest-modul som anger namn, version, beskrivning och författare inträffar ett fel.

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## PARAMETRAR

### -AllowPrerelease

Gör det möjligt att publicera moduler som är markerade som för hands versioner.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Du uppmanas att bekräfta innan du kör `Publish-Module` .

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

Anger ett användar konto som har behörighet att publicera en modul för en angiven paket leverantör eller källa.

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

### -Undanta

Definierar filer som ska undantas från den publicerade modulen.

```yaml
Type: System.String[]
Parameter Sets: ModuleNameParameterSet
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
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatVersion

Accepterar endast giltiga värden som anges av attributet **ValidateSet** .

Mer information finns i [ValidateSet-attributets deklaration](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) och [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:
Accepted values: 2.0

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – IconUri

Anger URL-adressen till en ikon för modulen. Den angivna ikonen visas på Galleri webb sidan för modulen.

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

### -LicenseUri

Anger webb adressen till licens villkoren för den modul som du vill publicera.

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

### -Name

Anger namnet på den modul som du vill publicera. `Publish-Module` söker efter det angivna modulnamnet i `$Env:PSModulePath` .

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NuGetApiKey

Anger den API-nyckel som du vill använda för att publicera en modul i onlinegalleri. API-nyckeln är en del av din profil i Onlinegalleri, och du hittar den på sidan användar konto i galleriet. API-nyckeln är NuGet funktioner.

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

### -Path

Anger sökvägen till den modul som du vill publicera. Den här parametern godkänner sökvägen till mappen som innehåller modulen.

```yaml
Type: System.String
Parameter Sets: ModulePathParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProjectUri

Anger webb adressen till en webb sida om projektet.

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

### -ReleaseNotes

Anger en sträng som innehåller viktig information eller kommentarer som du vill ska vara tillgängliga för användare av den här versionen av modulen.

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

### – Databas

Anger det egna namnet på en lagrings plats som har registrerats genom att köra `Register-PSRepository` . Lagrings platsen måste ha en **PublishLocation**, vilket är en giltig NUGET-URI.
**PublishLocation** kan anges genom att köra `Set-PSRepository` .

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

### – RequiredVersion

Anger den exakta versionen av en enda modul som ska publiceras.

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipAutomaticTags

Tar bort kommandon och resurser från att inkluderas som taggar. Hoppar över automatiskt tillägg av taggar i en modul.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Taggar

Lägger till en eller flera taggar till den modul som du publicerar. Exempel taggar är DesiredStateConfiguration, DSC, DSCResourceKit eller PSModule. Avgränsa flera taggar med kommatecken.

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

### -WhatIf

Visar vad som händer om `Publish-Module` körningarna körs. Cmdleten körs inte.

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

### System. String

### System. Management. Automation. PSCredential

## UTDATA

### System. Object

## ANTECKNINGAR

`Publish-Module` körs på PowerShell 3,0 eller senare versioner av PowerShell på Windows 7 eller Windows 2008 R2 och senare versioner av Windows.

> [!IMPORTANT]
> Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1. Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet. Använd följande kommando för att se till att du använder TLS 1,2:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.

Att publicera en modul kräver metadata som visas på Galleri sidan för modulen. Obligatoriska metadata innehåller modulens namn, version, beskrivning och författare. De flesta metadata tas från modulens manifest, men vissa metadata kan anges i `Publish-Module` parametrar, t. ex. **tagg**, **ReleaseNote**, **IconUri**, **ProjectUri** och **LicenseUri**. Mer information finns i [paket manifest värden som påverkar PowerShell-galleriet användar gränssnittet](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).

## RELATERADE LÄNKAR

[Sök-modul](Find-Module.md)

[Installera-modul](Install-Module.md)

[Registrera – PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Avinstallera-modul](Uninstall-Module.md)

[Update-modul](Update-Module.md)
