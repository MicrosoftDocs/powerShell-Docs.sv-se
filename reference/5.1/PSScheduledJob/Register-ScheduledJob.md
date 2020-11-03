---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/register-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ScheduledJob
ms.openlocfilehash: 89887474142490a71d372577576fb0059b4ff12e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264639"
---
# Register-ScheduledJob

## SAMMANFATTNING
Skapar ett schemalagt jobb.

## SYNTAX

### Script block (standard)

```
Register-ScheduledJob [-ScriptBlock] <ScriptBlock> [-Name] <String>
 [-Trigger <ScheduledJobTrigger[]>] [-InitializationScript <ScriptBlock>] [-RunAs32]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-ScheduledJobOption <ScheduledJobOptions>] [-ArgumentList <Object[]>] [-MaxResultCount <Int32>]
 [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilePath

```
Register-ScheduledJob [-FilePath] <String> [-Name] <String> [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-ArgumentList <Object[]>] [-MaxResultCount <Int32>] [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Register-ScheduledJob`Cmdlet: en skapar schemalagda jobb på den lokala datorn.

Ett schemalagt jobb är ett Windows PowerShell-bakgrunds jobb som kan startas automatiskt vid ett engångs-eller återkommande schema. Schemalagda jobb lagras på disk och registreras i Schemaläggaren.
Jobben kan hanteras i Schemaläggaren eller med hjälp av de schemalagda jobb-cmdletarna i Windows PowerShell.

När ett schemalagt jobb startar skapas en instans av det schemalagda jobbet. Schemalagda jobb instanser är identiska med bakgrunds jobb i Windows PowerShell, förutom att resultaten sparas på disken. Använd jobb-cmdletarna, till exempel,, `Start-Job` `Get-Job` och `Receive-Job` för att starta, Visa och hämta resultatet av jobb instanserna.

Använd `Register-ScheduledJob` för att skapa ett nytt schemalagt jobb. Om du vill ange vilka kommandon som det schemalagda jobbet ska köra använder du parametern **script block** . Om du vill ange ett skript som jobbet kör använder du parametern **sökväg** .

Windows PowerShell – schemalagda jobb använder samma jobb utlösare och jobb alternativ som Schemaläggaren använder för schemalagda aktiviteter.

**Utlösar** -parametern för `Register-ScheduledJob` lägger till en eller flera jobb utlösare som startar jobbet. **Utlösar** -parametern är valfri, så du kan lägga till utlösare när du skapar det schemalagda jobbet, lägga till jobb utlösare senare, lägga till parametern **RunNow** för att starta jobbet omedelbart, använda `Start-Job` cmdleten för att starta jobbet omedelbart när som helst, eller spara det ej utlösta schemalagda jobbet som en mall för andra jobb.

Med **alternativ** -parametern kan du anpassa alternativ inställningarna för det schemalagda jobbet. Parametern **alternativ** är valfri, så du kan ange jobb alternativ när du skapar det schemalagda jobbet eller ändra dem när som helst. Eftersom inställningarna för jobb alternativ kan förhindra att det schemalagda jobbet körs granskar du jobb alternativen och anger dem noggrant.

`Register-ScheduledJob` är en samling jobb schemaläggnings-cmdletar i **PSScheduledJob** -modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i artikeln om artiklar i **PSScheduledJob** -modulen.
Importera modulen **PSScheduledJob** och skriv sedan: `Get-Help about_Scheduled*` eller se [about_Scheduled_Jobs](./about/about_scheduled_jobs.md).

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: skapa ett schemalagt jobb

I det här exemplet skapas ett schemalagt jobb på den lokala datorn.

```powershell
Register-ScheduledJob -Name "Archive-Scripts" -ScriptBlock {
  Get-ChildItem $home\*.ps1 -Recurse |
    Copy-Item -Destination "\\Server\Share\PSScriptArchive"
}
```

`Register-ScheduledJob` använder parametern **Name** för att skapa ett schemalagt jobb för **Arkiv skript** .
Parametern **script block** körs `Get-ChildItem` som söker igenom `$home` katalogen rekursivt efter `.ps1` filer. `Copy-Item`Cmdleten kopierar filerna till en katalog som anges av **mål** parametern.

Eftersom det schemalagda jobbet inte innehåller någon utlösare startas det inte automatiskt. Du kan lägga till jobb utlösare med `Add-JobTrigger` , använda `Start-Job` cmdleten för att starta jobbet på begäran eller använda det schemalagda jobbet som en mall för andra schemalagda jobb.

### Exempel 2: skapa ett schemalagt jobb med utlösare och anpassade alternativ

Det här exemplet visar hur du skapar ett schemalagt jobb som har en jobb utlösare och anpassade jobb alternativ.

```powershell
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
$path = "\\Srv01\Scripts\UpdateVersion.ps1"
Register-ScheduledJob -Name "UpdateVersion" -FilePath $path -ScheduledJobOption $O -Trigger $T
```

`$O`Variabeln lagrar det jobb alternativ objekt som `New-ScheduledJobOption` cmdleten skapade. Alternativen startar det schemalagda jobbet även om datorn inte är inaktiv, aktiverar datorn för att köra jobbet, om det behövs, och tillåter att flera instanser av jobbet körs i en serie.

`$T`Variabeln lagrar resultatet från `New-JobTrigger` cmdleten för att skapa jobb utlösare som startar ett jobb varannan måndag vid 9:00 PM.

`$path`Variabeln lagrar sökvägen till `UpdateVersion.ps1` skript filen.

`Register-ScheduledJob` använder **namn** parametern för att skapa det schemalagda **UpdateVersion** -jobbet.
Parametern **sökväg** används `$path` för att ange det skript som jobbet kör. **ScheduledJobOption** -parametern använder de jobb alternativ som lagras i `$O` . **Utlösar** -parametern använder de jobb utlösare som lagras i `$T` .

### Exempel 3: Använd hash-tabeller för att ange alternativ för utlösare och schemalagt jobb

Det här exemplet har samma resultat som kommandot i exempel 2. Det skapar ett schemalagt jobb och använder hash-tabeller för att ange värdena för **Utlösar** -och **ScheduledJobOption** -parametrarna. `$O` `$T` Variablerna och som definieras i exempel 2 ersätts med hash-tabeller.

```powershell
$T = @{
  Frequency="Weekly"
  At="9:00PM"
  DaysOfWeek="Monday"
  Interval=2
}
$O = @{
  WakeToRun=$true
  StartIfNotIdle=$false
  MultipleInstancePolicy="Queue"
}
Register-ScheduledJob -Trigger $T -ScheduledJobOption $O -Name UpdateVersion -FilePath "\\Srv01\Scripts\Update-Version.ps1"
```

### Exempel 4: skapa schemalagda jobb på fjärrdatorer

I det här exemplet skapas det schemalagda **EnergyData** -jobbet på flera fjärranslutna datorer. Det schemalagda jobbet kör ett skript som samlar in rå data och sparar det i en löpande logg på fjärrdatorn.

```powershell
$Cred = Get-Credential
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Invoke-Command -ComputerName (Get-Content Servers.txt) -Credential $Cred -ScriptBlock {
  $params = @{
      Name = "Get-EnergyData"
      FilePath = "\\Srv01\Scripts\Get-EnergyData.ps1"
      ScheduledJobOption = $using:O
      Trigger = $using:T
  }
  Register-ScheduledJob @params
}
```

`$Cred`Variabeln lagrar autentiseringsuppgifter i ett **PSCredential** -objekt för en användare med behörighet att skapa schemalagda jobb. `$O`Variabeln lagrar de jobb alternativ som skapats med `New-ScheduledJobOption` . `$T`Variabeln lagrar jobb utlösare som skapats med `New-JobTrigger` .

`Invoke-Command`Cmdlet: en använder parametern **computername** för att hämta en lista över Server namn från `Servers.txt` filen. Parametern **Credential** hämtar objektet Credential som lagras i `$Cred` .
Parametern **script block** kör ett `Register-ScheduledJob` kommando på datorerna i `Servers.txt` filen.

Parametrarna för `Register-ScheduledJob` definieras av `$params` . **Namn** parametrarna anger att jobbet heter **Get-EnergyData** på varje fjärrdator. **Sökväg** är platsen för `EnergyData.ps1` skriptet. Skriptet finns på en fil server som är tillgänglig för alla deltagande datorer. Jobbet körs enligt det schema som anges av jobb utlösarna i `$T` och jobb alternativen i `$O` .

`Register-ScheduledJob @params`Kommandot skapar det schemalagda jobbet med parametrarna från skript blocket.

### Exempel 5: skapa ett schemalagt jobb som kör ett skript på fjärrdatorer

I det här exemplet skapas det schemalagda **CollectEnergyData** -jobbet på den lokala datorn. Jobbet körs på flera fjärrdatorer.

```powershell
$Admin = Get-Credential
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Register-ScheduledJob -Name "CollectEnergyData" -Trigger $T -MaxResultCount 99 -ScriptBlock {
  $params = @{
    AsJob = $true
    ComputerName = (Get-Content Servers.txt)
    FilePath = '\\Srv01\Scripts\Get-EnergyData.ps1'
    Credential = $using:Admin
    Authentication = 'CredSSP'
  }
  Invoke-Command @params
}
```

`$Admin`Variabeln lagrar autentiseringsuppgifter för en användare med behörighet att köra kommandona i ett **PSCredential** -objekt. `$T`Variabeln lagrar jobb utlösare som skapats med `New-JobTrigger` .

`Register-ScheduledJob`Cmdleten använder parametern **Name** för att skapa det schemalagda **CollectEnergyData** -jobbet på den lokala datorn. Parametern **trigger** anger jobb utlösare i `$T` och parametern **MaxResultCount** ökar antalet sparade resultat till 99.

Parametern **script block** definierar `Invoke-Command` parametrarna med `$params` . Parametern **AsJob** skapar objektet bakgrunds jobb på den lokala datorn, även om `Energydata.ps1` skriptet körs på fjärrdatorerna. Parametern **computername** hämtar en lista över Server namn från `Servers.txt` filen. Parametern **Credential** anger ett användar konto som har behörighet att köra skript på fjärrdatorerna. Dessutom anger parametern **Authentication** värdet **CredSSP** för att tillåta delegerade autentiseringsuppgifter.

`Invoke-Command @params`Kör kommandot med parametrarna från skript blocket.

## PARAMETRAR

### – Argument List

Anger värden för parametrarna i skriptet som anges av parametern **sökväg** eller för kommandot som anges av parametern **script block** .

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Autentisering

Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter. Standardvärdet är default.

De acceptabla värdena för den här parametern är:

- Default
- Basic
- CredSSP
- Sammandrag
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

Mer information om värdena för den här parametern finns i [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!CAUTION]
> Autentisering av Credential Security Service Provider (CredSSP), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs. Den här mekanismen ökar säkerhets risken för Fjärråtgärden. Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

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

Anger ett användar konto som har behörighet att köra det schemalagda jobbet. Standard är den aktuella användaren.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt, till exempel ett från `Get-Credential` cmdleten. Om du bara anger ett användar namn uppmanas du att ange ett lösen ord.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

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

### -Sökväg

Anger ett skript som det schemalagda jobbet körs på. Ange sökvägen till en `.ps1` fil på den lokala datorn. Om du vill ange standardvärden för skript parametrarna använder du parametern **argument List** .
Varje `Register-ScheduledJob` kommando måste använda antingen parametrarna **script block** eller **sökväg** .

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript

Anger den fullständigt kvalificerade sökvägen till ett Windows PowerShell-skript ( `.ps1` ). Initierings skriptet körs i sessionen som skapas för bakgrunds jobbet före de kommandon som anges av parametern **script block** eller det skript som anges av parametern **sökväg** . Du kan använda initierings skriptet för att konfigurera sessionen, till exempel lägga till filer, funktioner eller alias, skapa kataloger eller kontrol lera krav.

Om du vill ange ett skript som kör de primära jobb kommandona använder du parametern **sökväg** .

Om initierings skriptet genererar ett fel, även ett icke-avslutande fel, körs inte den aktuella instansen av det schemalagda jobbet och dess status **misslyckades**.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – MaxResultCount

Anger hur många jobb resultat poster som ska behållas för det schemalagda jobbet. Standardvärdet är 32.

Windows PowerShell sparar körnings historiken och resultaten av varje utlöst instans av det schemalagda jobbet på disken. Värdet för den här parametern avgör antalet jobb instans resultat som sparas för det här schemalagda jobbet. När antalet jobb instans resultat överskrider det här värdet, tar Windows PowerShell bort resultatet från den äldsta jobb instansen för att göra plats för resultatet av den senaste jobb instansen.

Jobb körnings historiken och jobb resultaten sparas i `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`
kataloger på den dator där jobbet skapas. Om du vill se körnings historiken använder du `Get-Job` cmdleten. Använd cmdleten för att hämta jobb resultatet `Receive-Job` .

Parametern **MaxResultCount** anger värdet för egenskapen ExecutionHistoryLength för det schemalagda jobbet.

Om du vill ta bort den aktuella körnings historiken och jobb resultaten använder du **ClearExecutionHistory** -parametern för `Set-ScheduledJob` cmdleten.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger ett namn för det schemalagda jobbet. Namnet används också för alla startade instanser av det schemalagda jobbet. Namnet måste vara unikt på datorn. Den här parametern är obligatorisk.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAs32

Kör det schemalagda jobbet i en 32-bitars process.

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

### -RunEvery

Används för att ange hur ofta jobbet ska köras. Använd exempelvis det här alternativet för att köra ett jobb var 15: e minut.

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunNow

Startar ett jobb omedelbart så fort `Register-ScheduledJob` cmdleten körs. Den här parametern eliminerar behovet av att utlösa Schemaläggaren för att köra ett Windows PowerShell-skript direkt efter registreringen och kräver inte att användare skapar en utlösare som anger start datum och start tid.

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

### -ScheduledJobOption

Anger alternativ för det schemalagda jobbet. Ange ett **ScheduledJobOptions** -objekt, till exempel ett som du skapar med hjälp av `New-ScheduledJobOption` cmdleten eller ett värde för hash-tabellen.

Du kan ange alternativ för ett schemalagt jobb när du registrerar schema jobbet eller använda `Set-ScheduledJobOption` `Set-ScheduledJob` cmdletarna eller för att ändra alternativen.

Många av alternativen och deras standardvärden avgör om och när ett schemalagt jobb körs. Se till att granska de här alternativen innan du schemalägger ett jobb. En beskrivning av de schemalagda jobb alternativen, inklusive standardvärdena, finns i `New-ScheduledJobOption` .

Om du vill skicka en hash-tabell använder du följande nycklar. I följande hash-tabell visas nycklarna med standardvärdena.

`@{StartIfOnBattery=$False; StopIfGoingOnBattery=$True; WakeToRun=$False; StartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False; ShowInTaskScheduler=$True; RunElevated=$False; RunWithoutNetwork=$False; DoNotAllowDemandStart=$False; MultipleInstancePolicy="IgnoreNew"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Script block

Anger de kommandon som det schemalagda jobbet körs på. Omge kommandoen med klammerparenteser ( `{}` ) för att skapa ett skript block. Om du vill ange standardvärden för kommando parametrar använder du parametern **argument List** .

Varje `Register-ScheduledJob` kommando måste använda antingen parametrarna **script block** eller **sökväg** .

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Utlös

Anger utlösare för det schemalagda jobbet. Ange ett eller flera **ScheduledJobTrigger** -objekt, till exempel de objekt som `New-JobTrigger` cmdleten returnerar eller en hash-tabell för jobb utlöser nycklar och värden.

En jobb utlösare startar schema jobbet. Utlösaren kan ange en enstaka eller återkommande schemalagd eller en händelse, till exempel när en användare loggar in eller Windows startas.

**Utlösar** parametern är valfri. Du kan lägga till en utlösare när du skapar det schemalagda jobbet, använda `Add-JobTrigger` `Set-JobTrigger` `Set-ScheduledJob` cmdletarna, eller för att lägga till eller ändra jobb utlösare senare, eller använda `Start-Job` cmdleten för att starta det schemalagda jobbet omedelbart. Du kan också skapa och underhålla ett schemalagt jobb utan en utlösare som används som mall.

Om du vill skicka en hash-tabell använder du följande nycklar:

- **Frekvens** : varje dag, varje vecka, AtStartup, AtLogon
- **Vid** : en giltig tids sträng
- **DaysOfWeek** – valfri kombination av dag namn
- **Intervall** – valfritt giltigt frekvens intervall
- **RandomDelay** : en giltig TimeSpan-sträng
- **Användare** : en giltig användare. Används endast med AtLogon-frekvens svärdet

Ett exempel:

`@{Frequency="Once"; At="3am"; DaysOfWeek="Monday", "Wednesday"; Interval=2; RandomDelay="30minutes"; User="Domain1\User01"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

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

### Inget

Du kan inte skicka inmatade pipelines till denna cmdlet.

## UTDATA

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition

## ANTECKNINGAR

Varje schemalagt jobb sparas i en under katalog till `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` katalogen på den lokala datorn.
Under katalogen är namngiven för det schemalagda jobbet och innehåller en XML-fil för det schemalagda jobbet och poster i körnings historiken. Mer information om schemalagda jobb på disk finns [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md).

Schemalagda jobb som du skapar i Windows PowerShell visas i Schemaläggaren i mappen Schemaläggaren `Library\Microsoft\Windows\PowerShell\ScheduledJobs` . Du kan använda Schemaläggaren för att visa och redigera det schemalagda jobbet.

Du kan använda Schemaläggaren, **schtasks.exe** kommando rads verktyget och Schemaläggaren-cmdletar för att hantera schemalagda jobb som du skapar med de schemalagda jobb-cmdletarna. Du kan dock inte använda de schemalagda jobb-cmdletarna för att hantera aktiviteter som du skapar i Schemaläggaren.

Om ett schemalagt jobb-kommando Miss lyckas, returnerar Windows PowerShell ett fel meddelande. Men om jobbet Miss lyckas när Schemaläggaren försöker köra det, är felet inte tillgängligt för Windows PowerShell.

Om ett schemalagt jobb inte körs kan du använda följande metoder för att hitta orsaken:

- Kontrol lera att jobb utlösaren är korrekt inställd.
  - Kontrol lera att villkoren som anges i jobb alternativen är uppfyllda.
- Kontrol lera att användar kontot som jobbet körs under har behörighet att köra kommandona eller skripten i jobbet.
- Kontrol lera om det finns fel i Schemaläggarens historik.
- Kontrol lera om det finns fel i händelse loggen för Schemaläggaren.

Mer information finns i [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md).

## RELATERADE LÄNKAR

[Add-JobTrigger](Add-JobTrigger.md)

[Disable-JobTrigger](Disable-JobTrigger.md)

[Disable-ScheduledJob](Disable-ScheduledJob.md)

[Aktivera – JobTrigger](Enable-JobTrigger.md)

[Aktivera – ScheduledJob](Enable-ScheduledJob.md)

[Get-JobTrigger](Get-JobTrigger.md)

[Get-ScheduledJob](Get-ScheduledJob.md)

[Get-ScheduledJobOption](Get-ScheduledJobOption.md)

[New-JobTrigger](New-JobTrigger.md)

[New-ScheduledJobOption](New-ScheduledJobOption.md)

[Registrera – ScheduledJob](Register-ScheduledJob.md)

[Remove-JobTrigger](Remove-JobTrigger.md)

[Set-JobTrigger](Set-JobTrigger.md)

[Set-ScheduledJob](Set-ScheduledJob.md)

[Set-ScheduledJobOption](Set-ScheduledJobOption.md)

[Avregistrera-ScheduledJob](Unregister-ScheduledJob.md)
