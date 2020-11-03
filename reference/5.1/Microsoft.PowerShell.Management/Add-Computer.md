---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Computer
ms.openlocfilehash: c1527c04d795206b8de968daf62456837627a098
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266276"
---
# Add-Computer

## SAMMANFATTNING
Lägg till den lokala datorn i en domän eller arbets grupp.

## SYNTAX

### Domän (standard)

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>]
 [-UnjoinDomainCredential <PSCredential>] -Credential <PSCredential> [-DomainName] <String> [-OUPath <String>]
 [-Server <String>] [-Unsecure] [-Options <JoinOptions>] [-Restart] [-PassThru] [-NewName <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Arbetsgrupp

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>] [-Credential <PSCredential>]
 [-WorkgroupName] <String> [-Restart] [-PassThru] [-NewName <String>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`Add-Computer`Cmdleten lägger till den lokala datorn eller fjärrdatorerna i en domän eller arbets grupp, eller flyttar dem från en domän till en annan.
Det skapar också ett domän konto om datorn läggs till i domänen utan ett konto.

Du kan använda parametrarna för denna cmdlet för att ange en organisationsenhet (OU) och domänkontrollant eller för att utföra en oskyddad anslutning.

Om du vill hämta resultatet av kommandot använder du parametrarna **verbose** och **Passthru** .

## EXEMPEL

### Exempel 1: Lägg till en lokal dator i en domän och starta sedan om datorn

```powershell
Add-Computer -DomainName Domain01 -Restart
```

Detta kommando lägger till den lokala datorn i Domain01-domänen och startar sedan om datorn för att ändringen ska börja gälla.

### Exempel 2: lägga till en lokal dator i en arbets grupp

```powershell
Add-Computer -WorkgroupName WORKGROUP-A
```

Detta kommando lägger till den lokala datorn i arbets gruppen – en arbets grupp.

### Exempel 3: lägga till en lokal dator i en domän

```powershell
Add-Computer -DomainName Domain01 -Server Domain01\DC01 -PassThru -Verbose
```

Detta kommando lägger till den lokala datorn i Domain01-domänen med hjälp av Domain01\DC01-domänkontrollanten.

Kommandot använder parametrarna **Passthru** och **verbose** för att få detaljerad information om resultatet av kommandot.

### Exempel 4: Lägg till en lokal dator i en domän med parametern OUPath

```powershell
Add-Computer -DomainName Domain02 -OUPath "OU=testOU,DC=domain,DC=Domain,DC=com"
```

Detta kommando lägger till den lokala datorn i Domain02-domänen.
Den använder parametern OUPath för att ange organisationsenhet för de nya kontona.

### Exempel 5: lägga till en lokal dator i en domän med hjälp av autentiseringsuppgifter

```powershell
Add-Computer -ComputerName Server01 -LocalCredential Server01\Admin01 -DomainName Domain02 -Credential Domain02\Admin02 -Restart -Force
```

Detta kommando lägger till Server01-datorn till Domain02-domänen.
Parametern **LocalCredential** används för att ange ett användar konto som har behörighet att ansluta till Server01-datorn.
Den använder parametern **Credential** för att ange ett användar konto som har behörighet att ansluta datorer till domänen.
Den använder parametern **restart** för att starta om datorn när anslutnings åtgärden har slutförts och **Force** -parametern för att utelämna användar bekräftelse meddelanden.

### Exempel 6: flytta en grupp med datorer till en ny domän

```powershell
Add-Computer -ComputerName Server01, Server02, localhost -DomainName Domain02 -LocalCredential Domain01\User01 -UnjoinDomainCredential Domain01\Admin01 -Credential Domain02\Admin01 -Restart
```

Det här kommandot flyttar Server01-och Server02-datorer och den lokala datorn från Domain01 till Domain02.

Parametern **LocalCredential** används för att ange ett användar konto som har behörighet att ansluta till de tre berörda datorerna.
Parametern **UnjoinDomainCredential** används för att ange ett användar konto som har behörighet att koppla från datorerna från Domain01-domänen och parametern **Credential** för att ange ett användar konto som har behörighet att ansluta till datorerna till Domain02-domänen.
Den använder parametern **restart** för att starta om alla tre datorerna när flyttningen är klar.

### Exempel 7: flytta en dator till en ny domän och ändra namnet på datorn

```powershell
Add-Computer -ComputerName Server01 -DomainName Domain02 -NewName Server044 -Credential Domain02\Admin01 -Restart
```

Det här kommandot flyttar Server01-datorn till Domain02 och ändrar dator namnet till Server044.

Kommandot använder den aktuella användarens autentiseringsuppgifter för att ansluta till Server01-datorn och ta bort anslutningen från den aktuella domänen.
Den använder parametern **Credential** för att ange ett användar konto som har behörighet att ansluta datorn till Domain02-domänen.

### Exempel 8: lägga till datorer som listas i en fil till en ny domän

```powershell
Add-Computer -ComputerName (Get-Content Servers.txt) -DomainName Domain02 -Credential Domain02\Admin02 -Options Win9xUpgrade  -Restart
```

Detta kommando lägger till de datorer som listas i Servers.txt-filen till Domain02-domänen.
Parametern **Options** används för att ange alternativet **Win9xUpgrade** .
Parametern **restart** startar om alla nyligen tillagda datorer när kopplingen har slutförts.

### Exempel 9: lägga till en dator i en domän med fördefinierade autentiseringsuppgifter för datorn

Det här första kommandot ska köras av en administratör från en dator som redan är ansluten till en domän `Domain03` :

```powershell
New-ADComputer -Name "Server02" -AccountPassword (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)

# Then this command is run from `Server02` which is not yet domain-joined:

$joinCred = New-Object pscredential -ArgumentList ([pscustomobject]@{
    UserName = $null
    Password = (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)[0]
})
Add-Computer -Domain "Domain03" -Options UnsecuredJoin,PasswordPass -Credential $joinCred
```

Den här kombinationen av kommandon skapar ett nytt dator konto med ett fördefinierat namn och tillfälligt kopplings lösen ord i en domän med en befintlig domänansluten dator.
Sedan är en dator med det fördefinierade namnet ansluts domänen med endast dator namnet och det tillfälliga kopplings lösen ordet.
Det fördefinierade lösen ordet används bara för att stödja kopplings åtgärden och ersätts som en del av vanliga dator konto procedurer när datorn har slutfört anslutningen.

## PARAMETRAR

### -ComputerName

Anger de datorer som ska läggas till i en domän eller arbets grupp.
Standard är den lokala datorn.

Ange NetBIOS-namnet, en Internet Protocol IP-adress eller ett fullständigt kvalificerat domän namn för var och en av de fjärranslutna datorerna.
Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller "localhost".

Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.
Du kan använda parametern **computername** för `Add-Computer` även om datorn inte är konfigurerad för att köra fjärrkommandon.

Den här parametern introduceras i Windows PowerShell 3,0.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att ansluta datorer till en ny domän.
Standard är den aktuella användaren.

Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.
Om du anger ett användar namn uppmanas du att ange ett lösen ord.

Använd parametern **UnjoinDomainCredential** om du vill ange ett användar konto som har behörighet att ta bort datorn från den aktuella domänen.
Om du vill ange ett användar konto som har behörighet att ansluta till en fjärrdator använder du parametern **LocalCredential** .

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain, Workgroup
Aliases: DomainCredential

Required: True (Domain), False (Workgroup)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DomainName

Anger den domän som datorerna ska läggas till i.
Den här parametern krävs när du lägger till datorerna i en domän.

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DN, Domain

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Förhindrar att användaren bekräftar frågan.
Utan den här parametern måste `Add-Computer` du bekräfta att varje dator ska läggas till.

Den här parametern introduceras i Windows PowerShell 3,0.

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

### -LocalCredential

Anger ett användar konto som har behörighet att ansluta till de datorer som anges av parametern **computername** .
Standard är den aktuella användaren.

Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.
Om du anger ett användar namn uppmanas du att ange ett lösen ord.

Om du vill ange ett användar konto som har behörighet att lägga till datorer i en ny domän, använder du parametern **Credential** .
Om du vill ange ett användar konto som har behörighet att ta bort datorerna från den aktuella domänen använder du parametern **UnjoinDomainCredential** .

Den här parametern introduceras i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Nyttnamn

Anger ett nytt namn för datorn i den nya domänen.
Den här parametern är endast giltig när en dator läggs till eller flyttas.

Den här parametern introduceras i Windows PowerShell 3,0.

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

### – Alternativ

Anger avancerade alternativ för åtgärden **Lägg till dator** anslutning.
Ange ett eller flera värden i en kommaavgränsad sträng.

De acceptabla värdena för den här parametern är:

- **AccountCreate** : skapar ett domän konto. Cmdleten **Add-Computer** skapar automatiskt ett domän konto när den lägger till en dator i en domän. Det här alternativet ingår för fullständighet.

- **Win9XUpgrade** : anger att anslutnings åtgärden ingår i en uppgradering av Windows-operativsystemet.

- **UnsecuredJoin** : utför en oskyddad anslutning. Om du vill begära en oskyddad anslutning använder du den *oskyddade* parametern eller det här alternativet. Om du vill skicka ett dator lösen ord måste du använda det här alternativet i kombination med `PasswordPass` alternativ.

- **PasswordPass** : anger datorns lösen ord till värdet för *Credential* -parametern (DomainCredential) när en oskyddad anslutning har utförts. Det här alternativet anger också att värdet för parametern *Credential* (DomainCredential) är ett dator lösen ord, inte ett användar lösen ord. Det här alternativet är endast giltigt när `UnsecuredJoin` alternativet har angetts. När du använder det här alternativet måste autentiseringsuppgiften som anges `-Credential` för *must* parametern ha ett null-användarnamn.

- **JoinWithNewName** : byter namn på dator namnet i den nya domänen till det namn som anges av parametern *Nyttnamn* . När du använder parametern *Nyttnamn* anges det här alternativet automatiskt. Det här alternativet är avsett att användas med Rename-Computer-cmdleten. Om du använder cmdleten **rename-Computer** för att byta namn på datorn, men inte startar om datorn för att göra ändringen gällande, kan du använda den här parametern för att ansluta datorn till en domän med det nya namnet.

- **JoinReadOnly** : använder ett befintligt dator konto för att ansluta datorn till en skrivskyddad domänkontrollant. Dator kontot måste läggas till i listan över tillåtna för lösenordsreplikeringsprincipen och konto lösen ordet måste replikeras till den skrivskyddade domänkontrollanten före kopplings åtgärden.

- **InstallInvoke** : anger flaggorna Create (0x2) och Delete (0x4) för parametern **FJoinOptions** för **JoinDomainOrWorkgroup** -metoden. Mer information om **JoinDomainOrWorkgroup** -metoden finns i [JoinDomainOrWorkgroup-metoden i Win32_ComputerSystem-klassen](https://msdn.microsoft.com/library/aa392154) i MSDN-biblioteket. Mer information om de här alternativen finns i [NetJoinDomain-funktionen](https://msdn.microsoft.com/library/aa370433) i MSDN-biblioteket.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: Microsoft.PowerShell.Commands.JoinOptions
Parameter Sets: Domain
Aliases:
Accepted values: AccountCreate, Win9XUpgrade, UnsecuredJoin, PasswordPass, DeferSPNSet, JoinWithNewName, JoinReadOnly, InstallInvoke

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OUPath

Anger en organisationsenhet (OU) för domän kontot.
Ange det fullständiga unika namnet på ORGANISATIONSENHETen inom citat tecken.
Standardvärdet är standard ORGANISATIONSENHETen för dator objekt i domänen.

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: OU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar det objekt som du arbetar med.
Som standard genererar denna cmdlet inga utdata.

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

### -Restart

Startar om datorerna som har lagts till i domänen eller arbets gruppen.
En omstart krävs ofta för att ändringen ska börja gälla.

Den här parametern introduceras i Windows PowerShell 3,0.

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

### -Server

Anger namnet på en domänkontrollant som lägger till datorn i domänen.
Ange namnet i DomainName\ComputerName-format.
Ingen domänkontrollant har angetts som standard.

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UnjoinDomainCredential

Anger ett användar konto som har behörighet att ta bort datorerna från deras aktuella domäner.
Standard är den aktuella användaren.

Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.
Om du anger ett användar namn uppmanas du att ange ett lösen ord.

Använd den här parametern när du flyttar datorer till en annan domän.
Om du vill ange ett användar konto som har behörighet att ansluta till den nya domänen använder du parametern **Credential** .
Om du vill ange ett användar konto som har behörighet att ansluta till en fjärrdator använder du parametern **LocalCredential** .

Den här parametern introduceras i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Osäkra

Utför en oskyddad anslutning till den angivna domänen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkgroupName

Anger namnet på en arbets grupp som datorerna läggs till i.
Standardvärdet är "WORKGROUP".

```yaml
Type: System.String
Parameter Sets: Workgroup
Aliases: WGN

Required: True
Position: 0
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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. String

Du kan skicka vidare dator namn och nya namn till- `Add-Computer` cmdleten.

## UTDATA

### Microsoft. PowerShell. commands. ComputerChangeInfo

När du använder parametern **Passthru** `Add-Computer` returnerar ett **ComputerChangeInfo** -objekt.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

- I Windows PowerShell 2,0 Miss lyckas **Server** parametern för `Add-Computer` trots att servern finns. I Windows PowerShell 3,0 ändras implementeringen av **Server** parametern så att den fungerar på ett tillförlitligt sätt.

## RELATERADE LÄNKAR

[Checkpoint-Computer](Checkpoint-Computer.md)

[Ta bort dator](Remove-Computer.md)

[Starta om datorn](Restart-Computer.md)

[Byt namn – dator](Rename-Computer.md)

[Återställa-dator](Restore-Computer.md)

[Stoppa – dator](Stop-Computer.md)

[Test-Connection](Test-Connection.md)
