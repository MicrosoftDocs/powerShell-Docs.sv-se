---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJob
ms.openlocfilehash: 6144d9f19b86727bc09d07e94f4bcf158e3b7071
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387914"
---
# Set-ScheduledJob

## SAMMANFATTNING
Ändrar schemalagda jobb.

## SYNTAX

### Script block (standard)

```
Set-ScheduledJob [-Name <String>] [-ScriptBlock <ScriptBlock>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### FilePath

```
Set-ScheduledJob [-Name <String>] [-FilePath <String>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### Körnings-

```
Set-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-ClearExecutionHistory] [-PassThru]
 [<CommonParameters>]
```

## BESKRIVNING
Cmdlet: en **set-ScheduledJob** ändrar egenskaperna för schemalagda jobb, till exempel de kommandon som jobben kör eller de autentiseringsuppgifter som krävs för att köra jobbet.
Du kan också använda den för att rensa körnings historiken för det schemalagda jobbet.

Om du vill använda denna cmdlet börjar du med att använda Get-ScheduledJob cmdlet för att hämta det schemalagda jobbet.
Skicka sedan det schemalagda jobbet till **set-ScheduledJob** eller spara jobbet i en variabel och Använd parametern *InputObject* för att identifiera jobbet.
Använd de återstående parametrarna för **set-ScheduledJob** för att ändra jobb egenskaperna eller rensa körnings historiken.

Även om du kan använda **set-ScheduledJob** för att ändra utlösare och alternativ för ett schemalagt jobb, ger cmdletarna Add-JobTrigger, set-JobTrigger och Set-ScheduledJobOption ett mycket enklare sätt att utföra dessa uppgifter.
Använd Register-ScheduledJob-cmdleten om du vill skapa ett nytt schemalagt jobb.

*Utlösar* -parametern för **set-ScheduledJob** lägger till en eller flera jobb utlösare som startar jobbet.
*Utlösar* -parametern är valfri, så du kan lägga till utlösare när du skapar det schemalagda jobbet, lägga till jobb utlösare senare, lägga till parametern *RunNow* för att starta jobbet omedelbart, använda Start-Job cmdlet för att starta jobbet omedelbart när som helst, eller spara det ej utlösta schemalagda jobbet som en mall för andra jobb.

**Set-ScheduledJob** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: ändra det skript som ett jobb kör

```
PS C:\> Get-ScheduledJob -Name "Inventory"
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-Inventory.ps1             True

The second command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job. A pipeline operator (|) sends the scheduled job to the **Set-ScheduledJob** cmdlet. The **Set-ScheduledJob** cmdlet uses the *Script* parameter to specify a new script, Get-FullInventory.ps1. The command uses the *Passthru* parameter to return the scheduled job after the change.
PS C:\> Get-ScheduledJob -Name "Inventory" | Set-ScheduledJob -FilePath "C:\Scripts\Get-FullInventory.ps1" -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-FullInventory.ps1         True
```

Det här exemplet visar hur du ändrar det skript som körs i ett schemalagt jobb.

Det första kommandot använder Get-ScheduledJob-cmdlet för att hämta det schemalagda jobbet för lager.
Utdata visar att jobbet kör Get-Inventory.ps1-skriptet.

Det här kommandot krävs inte. den ingår bara för att Visa effekterna av skript ändringen.

### Exempel 2: ta bort körnings historiken för ett schemalagt jobb

```
PS C:\> Get-ScheduledJob BackupArchive | Set-ScheduledJob -ClearExecutionHistory
```

Det här kommandot tar bort den aktuella körnings historiken och de sparade jobb resultaten för det schemalagda BackupArchive-jobbet.

Kommandot använder Get-ScheduledJob-cmdlet för att hämta det schemalagda BackupArchive-jobbet.
En pipeline-operator (|) skickar jobbet till **set-ScheduledJob** -cmdlet: en för att ändra det.
Cmdlet **: en Set-ScheduledJob** använder parametern *ClearExecutionHistory* för att ta bort körnings historiken och de sparade resultaten.

Mer information om körnings historik och sparade jobb resultat för schemalagda jobb finns about_Scheduled_Jobs.

### Exempel 3: ändra schemalagda jobb på en fjärrdator

```
PS C:\> Invoke-Command -Computer "Server01, Server02" -ScriptBlock {Get-ScheduledJob | Set-ScheduledJob -InitializationScript \\SrvA\Scripts\SetForRun.ps1}
```

Det här kommandot ändrar initierings skriptet i alla schemalagda jobb på Server01-och Server02-datorerna.

Kommandot använder cmdleten Invoke-Command för att köra ett kommando på Server01-och Server02-datorerna.

Fjärrkommandot börjar med ett Get-ScheduledJob-kommando som hämtar alla schemalagda jobb på datorn.
De schemalagda jobben är skickas till cmdleten **set-ScheduledJob** , som ändrar initierings skriptet till SetForRun.ps1.

## PARAMETRAR

### – Argument List
Anger värden för parametrarna i skriptet som anges av parametern *sökväg* eller för kommandot som anges av parametern *script block* .

```yaml
Type: System.Object[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Autentisering
Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter.
De acceptabla värdena för den här parametern är:

- Standard
- Grundläggande
- CredSSP
- Sammandrag
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

Standardvärdet är default. Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism) i PowerShell SDK.

Varning! CredSSP-autentisering (Credential Security Support Provider), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.
Den här mekanismen ökar säkerhets risken för Fjärråtgärden.
Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ScriptBlock, FilePath
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClearExecutionHistory
Tar bort den aktuella körnings historiken och de sparade resultaten för det schemalagda jobbet.

Jobb körnings historiken och jobb resultaten sparas med det schemalagda jobbet i katalogen $home \AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs på den dator där jobbet skapas.
Använd Get-Job-cmdleten om du vill se körnings historiken.
Använd Receive-Job-cmdleten för att hämta jobb resultatet.

Den här parametern påverkar inte de händelser som Schemaläggaren skriver till händelse loggarna i Windows, och den stoppar inte Windows PowerShell från att spara jobb resultat.
Om du vill hantera antalet jobb resultat som sparas använder du parametern *MaxResultCount* .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Execution
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Anger ett användar konto som har behörighet att köra det schemalagda jobbet.
Standard är den aktuella användaren.

Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, till exempel ett från Get-Credential-cmdleten.
Om du bara anger ett användar namn uppmanas du att ange ett lösen ord.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sökväg
Anger ett skript som det schemalagda jobbet körs på.
Ange sökvägen till en. ps1-fil på den lokala datorn.
Om du vill ange standardvärden för skript parametrarna använder du parametern *argument List* .
Varje schemalagt jobb måste ha antingen ett *script block* eller ett värde för *fil Sök väg* .

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript
Anger den fullständigt kvalificerade sökvägen till ett Windows PowerShell-skript (. ps1).
Initierings skriptet körs i sessionen som skapas för bakgrunds jobbet före de kommandon som anges av parametern *script block* eller det skript som anges av parametern *sökväg* .
Du kan använda initierings skriptet för att konfigurera sessionen, till exempel lägga till filer, funktioner eller alias, skapa kataloger eller kontrol lera krav.

Om du vill ange ett skript som kör de primära jobb kommandona använder du parametern *sökväg* .

Om initierings skriptet genererar ett fel, inklusive ett icke-avslutande fel, körs inte den aktuella instansen av det schemalagda jobbet och dess status misslyckades.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject
Anger det schemalagda jobbet som ska ändras.
Ange en variabel som innehåller **ScheduledJobDefinition** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobDefinition** -objekt, till exempel ett Get-ScheduledJob-kommando.
Du kan också skicka ett **ScheduledJobDefinition** -objekt till **set-ScheduledJob**.

Om du anger flera schemalagda jobb gör **set-ScheduledJob** samma ändringar i alla jobb.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – MaxResultCount
Anger hur många jobb resultat poster som ska behållas för det schemalagda jobbet.
Standardvärdet är 32.

Windows PowerShell sparar körnings historiken och resultaten av varje utlöst instans av det schemalagda jobbet på disken.
Värdet för den här parametern avgör antalet jobb instans resultat som sparas för det här schemalagda jobbet.
När antalet jobb instans resultat överskrider det här värdet, tar Windows PowerShell bort resultatet från den äldsta jobb instansen för att göra plats för resultatet av den senaste jobb instansen.

Jobb körnings historiken och jobb resultaten sparas i katalogen $home \AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs- \\ \<JobName\> \Output \\ \<Timestamp\> på den dator där jobbet skapas.
Använd Get-Job-cmdleten om du vill se körnings historiken.
Använd Receive-Job-cmdleten för att hämta jobb resultatet.

Parametern *MaxResultCount* anger värdet för egenskapen ExecutionHistoryLength för det schemalagda jobbet.

Om du vill ta bort den aktuella körnings historiken och jobb resultaten använder du parametern *ClearExecutionHistory* .

```yaml
Type: System.Int32
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Anger ett nytt namn för det schemalagda jobbet och instanser av det schemalagda jobbet.
Namnet måste vara unikt på den lokala datorn.

Om du vill identifiera det schemalagda jobbet som ska ändras använder du parametern *InputObject* eller lägger till ett schemalagt jobb från Get-ScheduledJob till **set-ScheduledJob**.

Den här parametern ändrar inte namnen på jobb instanser på disken.
Den påverkar bara jobb instanser som startas när det här kommandot har slutförts.

```yaml
Type: System.String
Parameter Sets: ScriptBlock, FilePath
Aliases:

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

### -RunAs32
Kör det schemalagda jobbet i en 32-bitars process.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
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
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunNow
Startar ett jobb omedelbart så snart cmdleten **set-ScheduledJob** körs.
Den här parametern eliminerar behovet av att utlösa Schemaläggaren för att köra ett Windows PowerShell-skript direkt efter registreringen och kräver inte att användare skapar en utlösare som anger start datum och start tid.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScheduledJobOption
Anger alternativ för det schemalagda jobbet.
Ange ett **ScheduledJobOptions** -objekt, till exempel ett som du skapar med hjälp av New-ScheduledJobOption-cmdlet eller ett värde för hash-tabellen.

Du kan ange alternativ för ett schemalagt jobb när du registrerar det schemalagda jobbet eller använda Set-ScheduledJobOption eller **set-ScheduledJob-** cmdletar för att ange eller ändra alternativ.

Många av alternativen och deras standardvärden avgör om och när ett schemalagt jobb körs.
Se till att granska de här alternativen innan du schemalägger ett jobb.
En beskrivning av de schemalagda jobb alternativen, inklusive standardvärdena, finns i New-ScheduledJobOption.

Om du vill skicka en hash-tabell använder du följande nycklar.
I följande hash-tabell visas nycklarna med standardvärdena.

`@{# Power SettingsStartIfOnBattery=$False;StopIfGoingOnBattery=$True; WakeToRun=$False; # Idle SettingsStartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False;# Security settingsShowInTaskScheduler=$TrueRunElevated=$False;# MiscRunWithoutNetwork=$False;DoNotAllowDemandStart=$False;MultipleInstancePolicy=IgnoreNew# Can be IgnoreNew, Parallel, Queue, StopExisting}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Script block
Anger de kommandon som det schemalagda jobbet körs på.
Omge kommandoen med klammerparenteser ({}) för att skapa ett skript block.
Om du vill ange standardvärden för kommando parametrar använder du parametern *argument List* .

Alla Register-ScheduledJob-kommandon måste använda antingen parametrarna *script block* eller *sökväg* .

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Utlös
Anger utlösare för det schemalagda jobbet.
Ange ett eller flera **ScheduledJobTrigger** -objekt, till exempel de objekt som New-JobTrigger cmdlet returnerar eller en hash-tabell med jobb utlöser nycklar och värden.

En jobb utlösare startar ett schemalagt jobb automatiskt vid en enstaka tidpunkt eller ett återkommande schema eller när en händelse inträffar.

Jobb utlösare är valfria.
Du kan lägga till en utlösare när du skapar det schemalagda jobbet, använda cmdletarna Add-JobTrigger eller **set-ScheduledJob** för att lägga till utlösare senare, eller använda cmdleten Start-Job för att starta det schemalagda jobbet omedelbart.
Du kan också skapa och underhålla ett schemalagt jobb som inte har några jobb utlösare.

Om du vill skicka en hash-tabell använder du följande nycklar.

`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (eller en giltig tids sträng); `DaysOfWeek="Monday", "Wednesday"` (eller valfri kombination av dag namn); `Interval=2` (eller ett giltigt frekvens intervall); `RandomDelay="30minutes"` (eller en giltig TimeSpan-sträng); `User="Domain1\User01"` (eller en giltig användare, används endast med AtLogon frekvens värde)

}

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: ScriptBlock, FilePath
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

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Du kan skicka vidare schemalagda jobb till **set-ScheduledJob**.

## UTDATA

### Ingen eller Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Om du använder parametern *Passthru* , **set-ScheduledJob** returnerar det schemalagda jobbet som ändrades.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

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
