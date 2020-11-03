---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: 42a2b37144d9af188a7204500227fddf4827bdf9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266931"
---
# Update-Module

## SAMMANFATTNING
Hämtar och installerar den senaste versionen av angivna moduler från ett onlinegalleri till den lokala datorn.

## SYNTAX

### Alla

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Update-Module`Cmdleten installerar en moduls nyaste version från ett onlinegalleri. Du uppmanas att bekräfta uppdateringen innan den installeras. Uppdateringar installeras bara för moduler som har installerats på den lokala datorn med `Install-Module` . `Update-Module` söker efter `$env:PSModulePath` installerade moduler.

`Update-Module` Om inga parametrar har angetts uppdaterar alla installerade moduler. Om du vill ange en modul som ska uppdateras använder du parametern **Name** . Du kan uppdatera till en moduls aktuella version med hjälp av parametern **RequiredVersion** .

Om en installerad modul redan är den senaste versionen, uppdateras inte modulen. Om modulen inte finns i `$env:PSModulePath` visas ett fel.

Använd om du vill visa de installerade modulerna `Get-InstalledModule` .

## EXEMPEL

### Exempel 1: uppdatera alla moduler

I det här exemplet uppdateras alla installerade moduler till den senaste versionen i ett onlinegalleri.

```powershell
Update-Module
```

### Exempel 2: uppdatera en modul efter namn

Det här exemplet uppdaterar en speciell modul till den senaste versionen i ett onlinegalleri.

```powershell
Update-Module -Name SpeculationControl
```

`Update-Module` använder **namn** parametern för att uppdatera en speciell modul, **SpeculationControl**.

### Exempel 3: Visa vad-om-Update-Module körs

Det här exemplet gör ett konsekvens scenario för att visa vad som händer om körs `Update-Module` . Kommandot körs inte.

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

`Update-Module` använder parametern **whatIf** som visar vad som skulle hända om kördes `Update-Module` .

### Exempel 4: uppdatera en modul till en angiven version

I det här exemplet uppdateras en modul till en angiven version. Versionen måste finnas i online-galleriet eller så visas ett fel.

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

`Update-Module` använder parametern **Name** för att ange modulen **SpeculationControl**. Parametern **RequiredVersion** anger versionen, **1.0.14**.

### Exempel 5: uppdatera en modul utan bekräftelse

Det här exemplet begär inte bekräftelse för att uppdatera modulen till den senaste versionen från ett onlinegalleri. Om modulen redan är installerad installerar **Force** -parametern om modulen.

```powershell
Update-Module -Name SpeculationControl -Force
```

`Update-Module` använder parametern **Name** för att ange modulen **SpeculationControl**. Parametern **Force** uppdaterar modulen utan att begära bekräftelse från användaren.

## PARAMETRAR

### -AcceptLicense

Godkänn licens avtalet automatiskt under installationen om paketet kräver det.

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

Gör att du kan uppdatera en modul med den nyare modulen markerad som en för hands version.

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

### -Confirm

Du uppmanas att bekräfta innan du kör `Update-Module` .

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

Anger ett användar konto som har behörighet att uppdatera en modul.

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

Tvingar fram en uppdatering av varje angiven modul utan att uppmana att begära bekräftelse. Om modulen redan är installerad **installerar du om** modulen.

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

Anger den maximala version av en enskild modul som ska uppdateras. Du kan inte lägga till den här parametern om du försöker uppdatera flera moduler. Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.

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

Anger namnen på en eller flera moduler som ska uppdateras. `Update-Module` söker efter `$env:PSModulePath` moduler att uppdatera. Om det inte finns några matchningar i `$env:PSModulePath` för angivet Modulnamn uppstår ett fel.

Jokertecken accepteras i modulnamn. Om du lägger till jokertecken till det angivna namnet och inga matchningar hittas inträffar inget fel.

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

### – PassThru

Returnerar ett objekt som representerar det objekt som du arbetar med. Som standard genererar denna cmdlet inga utdata.

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

Anger en proxyserver för begäran, i stället för att ansluta direkt till en Internet resurs.

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

### – RequiredVersion

Anger den exakta version som den befintliga installerade modulen ska uppdateras till. Versionen som anges av **RequiredVersion** måste finnas i online-galleriet eller så visas ett fel. Om mer än en modul uppdateras i ett enda kommando kan du inte använda **RequiredVersion**.

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

### – Omfattning

Anger modulens installations omfång. De acceptabla värdena för den här parametern är **allusers** och **CurrentUser**. Om **omfång** inte anges installeras uppdateringen i **CurrentUser** -omfånget.

**Allusers** -omfånget kräver förhöjd behörighet och installerar moduler på en plats som är tillgänglig för alla användare av datorn:

`$env:ProgramFiles\PowerShell\Modules`

**CurrentUser** kräver inte utökade behörigheter och installerar moduler på en plats som endast är tillgänglig för den aktuella användaren av datorn:

`$home\Documents\PowerShell\Modules`

När inget **omfång** har definierats anges standardvärdet baserat på PowerShellGet-versionen.

- I PowerShellGet-versioner 2.0.0 och senare är standardvärdet **CurrentUser** , vilket inte kräver höjning för installation.
- I PowerShellGet 1. x-versioner är standardvärdet **allusers** , vilket kräver höjning för installation.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som händer om `Update-Module` körs. Cmdleten körs inte.

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

### System. String

### System. Management. Automation. PSCredential

### System. URI

## UTDATA

### System. Object

## ANTECKNINGAR

För PowerShell version 6,0 och senare är standard installations omfånget alltid **CurrentUser**.
Module-uppdateringar för **CurrentUser** , `$home\Documents\PowerShell\Modules` , behöver inte utökade behörigheter. Uppdatering av modulen för **allusers** , `$env:ProgramFiles\PowerShell\Modules` kräver förhöjd behörighet.

`Update-Module` körs på PowerShell 3,0 eller senare versioner av PowerShell på Windows 7 eller Windows 2008 R2 och senare versioner av Windows.

Om den modul som du anger med **namn** parametern inte har installerats med hjälp av `Install-Module` , uppstår ett fel.

Du kan bara köra `Update-Module` i moduler som du har installerat från Onlinegalleri online genom att köra `Install-Module` .

Om `Update-Module` försök att uppdatera binärfiler som används, `Update-Module` returnerar ett fel som identifierar problem processerna. Användaren meddelas om att försöka igen `Update-Module` efter att processerna har stoppats.

## RELATERADE LÄNKAR

[Sök-modul](Find-Module.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Installera-modul](Install-Module.md)

[Publicera-modul](Publish-Module.md)

[Avinstallera-modul](Uninstall-Module.md)
