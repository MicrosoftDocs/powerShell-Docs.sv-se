---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Module
ms.openlocfilehash: ec9862e9003bd73e952422a8d15d373193a80c12
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889784"
---
# Install-Module

## SAMMANFATTNING
Laddar ned en eller flera moduler från en lagrings plats och installerar dem på den lokala datorn.

## SYNTAX

### NameParameterSet (standard)

```
Install-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Install-Module [-InputObject] <PSObject[]> [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Install-Module`Cmdlet: en hämtar en eller flera moduler som uppfyller de angivna kriterierna från en online-lagringsplats. Cmdleten verifierar att Sök resultaten är giltiga moduler och kopierar modulens mappar till installations platsen. Installerade moduler importeras inte automatiskt efter installationen.
Du kan filtrera vilken modul som installeras baserat på de lägsta, högsta och exakta versionerna av de angivna modulerna.

Om modulen som installeras har samma namn eller version, eller innehåller kommandon i en befintlig modul, visas varnings meddelanden. När du har bekräftat att du vill installera modulen och åsidosätta varningarna använder du `-Force` parametrarna och `-AllowClobber` . Beroende på dina lagrings plats inställningar kan du behöva besvara en prompt för att modulen ska kunna fortsätta.

I de här exemplen används [PowerShell-galleriet](https://www.powershellgallery.com/) som den enda registrerade lagrings platsen. `Get-PSRepository` visar de registrerade databaserna. Om du har flera registrerade databaser använder du `-Repository` parametern för att ange namnet på lagrings platsen.

## EXEMPEL

### Exempel 1: söka efter och installera en modul

I det här exemplet hittar du en modul i lagrings platsen och installerar modulen.

```powershell
Find-Module -Name PowerShellGet | Install-Module
```

`Find-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen. Den nyaste versionen av modulen laddas som standard ned från lagrings platsen. Objektet skickas ned pipelinen till `Install-Module` cmdleten. `Install-Module` installerar modulen för alla användare i `$env:ProgramFiles\WindowsPowerShell\Modules` .

### Exempel 2: installera en modul efter namn

I det här exemplet installeras den nyaste versionen av **PowerShellGet** -modulen.

```powershell
Install-Module -Name PowerShellGet
```

`Install-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen. Den nyaste versionen av modulen laddas som standard ned från lagrings platsen och installeras.

### Exempel 3: installera en modul med dess lägsta version

I det här exemplet installeras den lägsta versionen av **PowerShellGet** -modulen. Parametern **MinimumVersion** anger den lägsta versionen av modulen som ska installeras. Om en nyare version av modulen är tillgänglig laddas den versionen ned och installeras för alla användare.

```powershell
Install-Module -Name PowerShellGet -MinimumVersion 2.0.1
```

`Install-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen. Parametern **MinimumVersion** anger att version **2.0.1** hämtas från lagrings platsen och installeras. Eftersom version **2.0.4** är tillgänglig laddas den versionen ned och installeras för alla användare.

### Exempel 4: installera en angiven version av en modul

I det här exemplet installeras en angiven version av **PowerShellGet** -modulen.

```powershell
Install-Module -Name PowerShellGet -RequiredVersion 2.0.0
```

`Install-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen. Parametern **RequiredVersion** anger att version **2.0.0** har laddats ned och installerats för alla användare.

### Exempel 5: installera bara en modul för den aktuella användaren

I det här exemplet hämtas och installeras den senaste versionen av en modul, bara för den aktuella användaren.

```powershell
Install-Module -Name PowerShellGet -Scope CurrentUser
```

`Install-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen.
`Install-Module` laddar ned och installerar den senaste versionen av **PowerShellGet** i den aktuella användarens katalog `$home\Documents\WindowsPowerShell\Modules` .

## PARAMETRAR

### -AcceptLicense

För moduler som kräver en licens accepterar **AcceptLicense** automatiskt licens avtalet under installationen. Mer information finns i [moduler som kräver licens godkännande](/powershell/scripting/gallery/concepts/module-license-acceptance).

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

### -AllowClobber

Åsidosätter varnings meddelanden om installations konflikter för befintliga kommandon på en dator.
Skriver över befintliga kommandon som har samma namn som kommandon som installeras av en modul.
**AllowClobber** och **Force** kan användas tillsammans i ett `Install-Module` kommando.

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

Gör att du kan installera en modul som är markerad som en för hands version.

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

Du uppmanas att bekräfta innan du kör `Install-Module` cmdleten.

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

Anger ett användar konto som har behörighet att installera en modul för en angiven paket leverantör eller källa.

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

Installerar en modul och åsidosätter varnings meddelanden om installations konflikter i modulen. Om det redan finns en modul med samma namn på datorn, tillåter **Force** att flera versioner är installerade. Om det finns en befintlig modul med samma namn och version, kommer **Framtvinga** att skriva över den versionen. **Force** och **AllowClobber** kan användas tillsammans i ett `Install-Module` kommando.

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

Anger den maximala version av en enskild modul som ska installeras. Den installerade versionen måste vara mindre än eller lika med **MaximumVersion**. Om du vill installera flera moduler kan du inte använda **MaximumVersion**. Det går inte att använda **MaximumVersion** och **RequiredVersion** i samma `Install-Module` kommando.

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

Anger den lägsta version av en enskild modul som ska installeras. Den installerade versionen måste vara större än eller lika med **MinimumVersion**. Om det finns en nyare version av modulen som är tillgänglig installeras den nyare versionen. Om du vill installera flera moduler kan du inte använda **MinimumVersion**.
Det går inte att använda **MinimumVersion** och **RequiredVersion** i samma `Install-Module` kommando.

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

Anger de exakta namnen på de moduler som ska installeras från onlinegalleri. En kommaavgränsad lista med Modulnamn accepteras. Modulnamnet måste matcha modulens namn i lagrings platsen. Används `Find-Module` för att hämta en lista över modulnamn.

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

### – PassThru

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

Använd parametern **lagrings plats** för att ange vilken databas som används för att ladda ned och installera en modul. Används när flera databaser har registrerats. Anger namnet på en registrerad databas i `Install-Module` kommandot. Använd om du vill registrera en lagrings plats `Register-PSRepository` .
Använd om du vill visa registrerade databaser `Get-PSRepository` .

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

Anger den exakta versionen av en enda modul som ska installeras. Om det inte finns någon matchning i lagrings platsen för den angivna versionen visas ett fel. Om du vill installera flera moduler kan du inte använda **RequiredVersion**. **RequiredVersion** kan inte användas i samma `Install-Module` kommando som **MinimumVersion** eller **MaximumVersion**.

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

Anger modulens installations omfång. De acceptabla värdena för den här parametern är **allusers** och **CurrentUser**.

**Allusers** scope installerar moduler på en plats som är tillgänglig för alla användare av datorn:

`$env:ProgramFiles\WindowsPowerShell\Modules`

**CurrentUser** installerar moduler på en plats som endast är tillgänglig för den aktuella användaren av datorn. Exempel:

`$home\Documents\WindowsPowerShell\Modules`

När inget **omfång** har definierats anges standardvärdet baserat på PowerShellGet-versionen.

- I PowerShellGet-versioner 2.0.0 och senare är standardvärdet **CurrentUser**, vilket inte kräver höjning för installation.
- I PowerShellGet 1. x-versioner är standardvärdet **allusers**, vilket kräver höjning för installation.

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

### -SkipPublisherCheck

Gör att du kan installera en nyare version av en modul som redan finns på datorn. Till exempel när en befintlig modul signeras digitalt av en betrodd utgivare men den nya versionen inte signeras digitalt av en betrodd utgivare.

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

### -WhatIf

Visar vad som händer om ett `Install-Module` kommando kördes. Cmdleten körs inte.

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

### PSRepositoryItemInfo

`Find-Module` skapar **PSRepositoryItemInfo** -objekt som kan skickas till pipelinen till `Install-Module` .

### System.String[]

### System. Management. Automation. PSObject []

### System. String

### System. Management. Automation. PSCredential

### System. URI

## UTDATA

### Microsoft. PowerShell. commands. PSRepositoryItemInfo

När du använder parametern **Passthru** `Install-Module` matar ut ett **PSRepositoryItemInfo** -objekt för modulen. Detta är samma information som du hämtar från `Find-Module` cmdleten.

## ANTECKNINGAR

`Install-Module` körs på PowerShell 5,0 eller senare versioner, på Windows 7 eller Windows 2008 R2 och senare versioner av Windows.

> [!IMPORTANT]
> Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1. Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet. Använd följande kommando för att se till att du använder TLS 1,2:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.

Som en säkerhets åtgärd bör du utvärdera modulens kod innan du kör några cmdlets eller Functions för första gången. För att förhindra att moduler som innehåller skadlig kod körs, importeras inte installerade moduler automatiskt efter installationen.

Om det Modulnamn som anges av **namn** parametern inte finns i databasen `Install-Module` returneras ett fel.

Om du vill installera flera moduler använder du parametern **Name** och anger en kommaavgränsad matris med modulnamn. Om du anger flera modulnamn kan du inte använda **MinimumVersion**, **MaximumVersion** eller **RequiredVersion**. `Find-Module` skapar **PSRepositoryItemInfo** -objekt som kan skickas till pipelinen till `Install-Module` . Pipelinen är ett annat sätt att ange flera moduler som ska installeras i ett enda kommando.

Som standard installeras moduler för omfånget för **allusers** i `$env:ProgramFiles\WindowsPowerShell\Modules` . Standard förhindrar förvirring när du installerar PowerShell-resurser för Desired State Configuration (DSC).

En modul installeras inte och kan inte importeras om den inte har något `.psm1` , `.psd1` eller `.dll` av samma namn i mappen. Använd parametern **Force** för att installera modulen.

Om en befintlig moduls version matchar namnet som anges av parametern **Name** , och parametern **MinimumVersion** eller **RequiredVersion** inte används, `Install-Module` fortsätter tyst men installerar inte modulen.

Om en befintlig moduls version är större än värdet för parametern **MinimumVersion** , eller är lika med värdet för parametern **RequiredVersion** , `Install-Module` fortsätter obevakat, men modulen installeras inte.

Om den befintliga modulen inte matchar värdena som anges i parametrarna **MinimumVersion** eller **RequiredVersion** inträffar ett fel i `Install-Module` kommandot. Till exempel, om versionen för den befintliga installerade modulen är lägre än **MinimumVersion** -värdet eller inte lika med **RequiredVersion** -värdet.

Vid en installation av en modul installeras även eventuella beroende moduler som anges i modulen utgivare.
Utgivaren anger de moduler och versioner som krävs i manifestet för modulen.

## RELATERADE LÄNKAR

[Sök-modul](Find-Module.md)

[Get-PSRepository](Get-PSRepository.md)

[Importera-modul](../Microsoft.PowerShell.Core/Import-Module.md)

[Publicera-modul](Publish-Module.md)

[Registrera – PSRepository](Register-PSRepository.md)

[Avinstallera-modul](Uninstall-Module.md)

[Update-modul](Update-Module.md)

[about_Module](../Microsoft.PowerShell.Core/About/about_Modules.md)
