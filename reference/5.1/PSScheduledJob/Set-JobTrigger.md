---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-JobTrigger
ms.openlocfilehash: 8d1b12b67ccf695e1c4b948e6eeecf292c588af4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264627"
---
# Set-JobTrigger

## SAMMANFATTNING
Ändrar jobb utlösaren för ett schemalagt jobb.

## SYNTAX

```
Set-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-DaysInterval <Int32>] [-WeeksInterval <Int32>]
 [-RandomDelay <TimeSpan>] [-At <DateTime>] [-User <String>] [-DaysOfWeek <DayOfWeek[]>] [-AtStartup]
 [-AtLogOn] [-Once] [-RepetitionInterval <TimeSpan>] [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely]
 [-Daily] [-Weekly] [-PassThru] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet **: en Set-JobTrigger** ändrar egenskaperna för jobb utlösare för schemalagda jobb.
Du kan använda den för att ändra tid eller frekvens då jobben startar eller ändras från tidsbaserade scheman till scheman som utlöses av en inloggning eller start.

En jobb utlösare definierar ett återkommande schema eller villkor för att starta ett schemalagt jobb.
Även om jobb utlösare inte sparas på disk, kan du ändra jobb utlösare för schemalagda jobb som sparas till disk.

Om du vill ändra en jobb utlösare för ett schemalagt jobb börjar du med att använda Get-JobTrigger-cmdlet för att hämta jobb utlösaren för ett schemalagt jobb.
Skicka sedan utlösaren till **set-JobTrigger** eller spara utlösaren i en variabel och Använd *InputObject* -parametern för cmdleten **set-JobTrigger** för att identifiera utlösaren.
Använd de återstående parametrarna för **set-JobTrigger** för att ändra jobb utlösaren.

När du ändrar typen för en jobb utlösare, t. ex. ändrar en jobb utlösare från en daglig eller veckovis utlösare till en *AtLogon* -utlösare, tas de ursprungliga utlösarens egenskaper bort.
Men om du ändrar värdena för utlösaren, men inte dess typ, t. ex. om du ändrar dagar i en veckovis utlösare, ändras bara de egenskaper som du anger.
Alla andra egenskaper för den ursprungliga jobb utlösaren behålls.

**Set-JobTrigger** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*`  eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: ändra antalet dagar i en jobb utlösare

```
PS C:\> Get-JobTrigger -Name "DeployPackage"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Saturday}   True

The second command uses the Get-JobTrigger cmdlet to get the job trigger of the DeployPackage scheduled job. A pipeline operator (|) sends the trigger to the **Set-JobTrigger** cmdlet, which changes the job trigger so that it starts the DeployPackage job on Wednesdays and Sundays. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "DeployPackage" | Set-JobTrigger -DaysOfWeek "Wednesday", "Sunday" -Passthru
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Sunday}     True
```

Det här exemplet visar hur du ändrar antalet dagar i en veckovis jobb utlösare.

Det första kommandot använder Get-JobTrigger-cmdlet för att hämta jobb utlösaren för det schemalagda DeployPackage-jobbet.
Resultatet visar att utlösaren startar jobbet vid midnatt på onsdagar och lördagar.

Det här kommandot krävs inte. den ingår endast för att Visa effekterna av utlösnings ändringen.

### Exempel 2: Ändra jobb utlösnings typen

```
PS C:\> Get-JobTrigger -Name "Inventory"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          AtStartup                                                      True

The second command uses the **Get-JobTrigger** cmdlet to get the *AtStartup* job trigger of the Inventory job. The command uses the *TriggerID* parameter to identify the job trigger. A pipeline operator (|) sends the job trigger to the **Set-JobTrigger** cmdlet, which changes it to a weekly job trigger that runs every four weeks on Monday at midnight. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "Inventory" -TriggerID 2 | Set-JobTrigger -Weekly -WeeksInterval 4 -DaysOfWeek Monday -At "12:00 AM"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          Weekly          10/31/2011 12:00:00 AM {Monday}                True
```

Det här exemplet visar hur du ändrar vilken typ av jobb utlösare som startar ett jobb.
Kommandona i det här exemplet ersätter en utlösare för AtStartup-jobb med en veckovis utlösare.

Det första kommandot använder Get-JobTrigger-cmdlet för att hämta jobb utlösaren för det schemalagda jobbet för lager.
Utdata visar att jobbet har två utlösare en daglig utlösare och en *AtStartup* -utlösare.

Det här kommandot krävs inte. den ingår endast för att Visa effekterna av utlösnings ändringen.

### Exempel 3: ändra användaren på en utlösare för Fjärrjobb

```
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.User} | Set-JobTrigger -User "Domain01/Admin02"}
```

Det här kommandot ändrar användaren i alla *AtLogon* jobb-utlösare för schemalagda jobb på Server01-datorn.

Kommandot använder cmdleten Invoke-Command för att köra ett kommando på Server01-datorn.

Fjärrkommandot börjar med ett Get-ScheduledJob-kommando som hämtar alla schemalagda jobb på datorn.
De schemalagda jobben är skickas till Get-JobTrigger-cmdleten, som hämtar jobb utlösarna för de schemalagda jobben.
Varje jobb utlösare innehåller en jobb definitionen-egenskap som innehåller det schemalagda jobbet, så utlösaren förblir kopplad till det schemalagda jobbet även om den ändras.

Jobb utlösarna är skickas till Where-Object-cmdleten, som hämtar jobb utlösare som har egenskapen User.
De valda jobb utlösarna är skickas till cmdleten **set-JobTrigger** , som ändrar användaren till Domain01\Admin02.

### Exempel 4: ändra en av många jobb utlösare

```
PS C:\> Get-JobTrigger -Name "SecurityCheck"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           4/24/2013 3:00:00 AM                           True
2          Weekly          4/24/2013 4:00:00 PM   {Sunday}                True
3          Once            4/24/2013 4:00:00 PM                           True

The second command uses the **TriggerID** parameter of the **Get-JobTrigger** cmdlet to get the *Once* trigger of the SecurityCheck scheduled job. The command pipes the trigger to the Format-List cmdlet, which displays all of the properties of the *Once* job trigger.The output shows that the trigger starts the job once every hour (RepetitionInterval = 1 hour) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:00:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The third command changes the repetition interval of the job trigger from one hour to 90 minutes. The command does not return any output.
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerId 3 | Set-JobTrigger -RepetitionInterval (New-TimeSpan -Minutes 90)

The fourth command displays the effect of the change.The output shows that the trigger starts the job once every 90 minutes (RepetitionInterval = 1 hour, 30 minutes) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:30:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

Kommandona i det här exemplet ändrar upprepnings intervallet för *en gång* jobb utlösare för SecurityCheck schemalagda jobb från var 60: e minut till var 90 minut.
Det schemalagda SecurityCheck-jobbet har tre jobb utlösare, så kommandona använder parametern *TriggerId* i Get-JobTrigger-cmdlet för att identifiera den jobb utlösare som ändras.

Det första kommandot använder cmdleten **Get-JobTrigger** för att hämta alla jobb utlösare för det schemalagda SecurityCheck-jobbet.
Utdata, som visar ID: n för jobb utlösare, visar att den *när* jobb utlösaren har ett ID på 3.

## PARAMETRAR

### – På
Startar jobbet vid angivet datum och tid.
Ange ett **datetime** -objekt, till exempel ett som Get-Date cmdlet returnerar, eller en sträng som kan konverteras till en tid, till exempel "April 19, 2012 15:00", "12/31/2013 9:00 PM" eller "3am".

Om du inte anger ett element i **datetime** -objektet, till exempel sekunder, ändras inte det element som ingår i jobb utlösaren.
Om den ursprungliga jobb utlösaren inte innehåller ett **datetime** -objekt och du utelämnar ett element, skapas jobb utlösaren med motsvarande element från aktuellt datum och aktuell tid.

När du använder parametern *Once* ställer du in värdet för parametern *at* på ett visst datum och en viss tid.
Eftersom standard datumet i ett **datetime** -objekt är det aktuella datumet, ställer du in en tid före den aktuella tiden utan ett explicit datum resulterar i en jobb utlösare för en tid i det förflutna.

**Datetime** -objekt och strängar som konverteras till **datetime** -objekt justeras automatiskt så att de är kompatibla med de datum-och tids format som valts för den lokala datorn i region och språk på kontroll panelen.

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AtLogOn
Startar det schemalagda jobbet när de angivna användarna loggar in på datorn.
Använd *användar* parametern för att ange en användare.

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

### -AtStartup
Startar det schemalagda jobbet när Windows startas.

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

### – Varje dag
Anger ett återkommande schema för dagligt jobb.
Använd de andra parametrarna i den *dagliga* parameter uppsättningen för att ange schema information.

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

### -DaysInterval
Anger antalet dagar mellan förekomster enligt ett dagligt schema.
Värdet 3 startar till exempel det schemalagda jobbet på dagar 1, 4, 7 och så vidare.
Standardvärdet är 1.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DaysOfWeek
Anger vecko dagarna som ett schemalagt vecko jobb körs på.
Ange dag namn, till exempel måndag, torsdag, heltal 0-6, där 0 representerar söndag eller en asterisk ( \* ) som representerar varje dag.
Den här parametern krävs i den veckobaserade parameter uppsättningen.

Dag namn konverteras till deras heltals värden i jobb utlösaren.
När du omger dag namn inom citat tecken i ett kommando, omger du varje dag med separata citat tecken, till exempel "måndag", "tisdag".
Om du omger flera dag namn i ett enkelt citat tecken, summeras motsvarande heltals värden.
Till exempel "måndag, tisdag" (1, 2) resulterar i värdet "onsdag" (3).

```yaml
Type: System.DayOfWeek[]
Parameter Sets: (All)
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject
Anger jobb utlösare.
Ange en variabel som innehåller **ScheduledJobTrigger** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobTrigger** -objekt, till exempel ett Get-JobTrigger-kommando.
Du kan också skicka ett **ScheduledJobTrigger** -objekt till **set-JobTrigger**.

Om du anger flera jobb utlösare gör **set-JobTrigger** samma ändringar i alla jobb utlösare.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – En gång
Anger ett schema som inte är återkommande (en tid).

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
Returnerar de jobb utlösare som har ändrats.
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

### -RandomDelay
Aktiverar en slumpmässig fördröjning som börjar vid den schemalagda start tiden och anger högsta fördröjnings värde.
Längden på fördröjningen är att ställa in pseudo – slumpvis för varje start och varierar från ingen fördröjning till den tid som anges av värdet för den här parametern.
Standardvärdet noll (00:00:00), inaktiverar slumpmässig fördröjning.

Ange ett TimeSpan-objekt, till exempel ett som returneras av New-TimeSpan-cmdleten, eller ange ett värde i \<hours\> : \<minutes\> : \<seconds\> format, som automatiskt konverteras till ett TimeSpan-objekt.

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

### -RepeatIndefinitely
Den här parametern, som är tillgänglig från och med Windows PowerShell 4,0, eliminerar behovet av att ange ett **TimeSpan. MaxValue** -värde för parametern *RepetitionDuration* för att köra ett schemalagt jobb upprepade gånger, under obestämd tid.

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

### -RepetitionDuration
Upprepar jobbet tills den angivna tiden upphör att gälla.
Upprepnings frekvensen bestäms av värdet för parametern *RepetitionInterval* .
Om värdet för **RepetitionInterval** till exempel är 5 minuter och värdet för *RepetitionDuration* är 2 timmar utlöses jobbet var femte minut i två timmar.

Ange ett TimeSpan-objekt, till exempel ett som New-TimeSpan cmdlet returnerar eller en sträng som kan konverteras till ett TimeSpan-objekt, till exempel "1:05:30".

Om du vill köra ett jobb oändligt lägger du till parametern *RepeatIndefinitely* i stället.

Om du vill stoppa ett jobb innan jobbets repetitions varaktighet upphör att gälla, ställer du in värdet för **RepetitionDuration** på noll (0).

Om du vill ändra varaktigheten eller upprepnings intervallet för en *gång* jobb utlösare måste kommandot innehålla parametrarna **RepetitionInterval** och **RepetitionDuration** .
Om du vill ändra varaktighet eller upprepnings intervall för andra typer av jobb utlösare måste kommandot inkludera parametrarna *Once* , *at* , *RepetitionInterval* och *RepetitionDuration* .

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

### -RepetitionInterval
Upprepar jobbet vid det angivna tidsintervallet.
Om värdet för den här parametern till exempel är 2 timmar utlöses jobbet varannan timme.
Standardvärdet, 0, upprepar inte jobbet.

Ange ett TimeSpan-objekt, till exempel ett som New-TimeSpan cmdlet returnerar eller en sträng som kan konverteras till ett TimeSpan-objekt, till exempel "1:05:30".

Om du vill ändra varaktigheten eller upprepnings intervallet för en **gång** jobb utlösare måste kommandot innehålla parametrarna **RepetitionInterval** och **RepetitionDuration** .
Om du vill ändra varaktighet eller upprepnings intervall för andra typer av jobb utlösare måste kommandot inkludera parametrarna **Once** , **at** , **RepetitionInterval** och **RepetitionDuration** .

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

### -User
Anger de användare som utlöser en *AtLogon* början av ett schemalagt jobb.
Ange namnet på en användare i \<UserName\> eller \<Domain\Username\> formatera eller ange en asterisk ( \* ) för att representera alla användare.
Standardvärdet är alla användare.

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

### – Varje vecka
Anger ett återkommande veckovis jobb schema.
Använd de andra parametrarna i *vecko* parametern set för att ange schema information.

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

### -WeeksInterval
Anger antalet veckor mellan förekomster för ett vecko jobb schema.
Värdet 3 startar till exempel det schemalagda jobbet på veckor 1, 4, 7 och så vidare.
Standardvärdet är 1.

```yaml
Type: System.Int32
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

### Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger
Du kan skicka flera jobb utlösare till **set-JobTrigger**.

## UTDATA

### Ingen eller Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger
När du använder *Passthru* -parametern returnerar **set-JobTrigger** de jobb utlösare som har ändrats.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

* Jobb utlösare har en JobDefintion-egenskap som kopplar dem till det schemalagda jobbet. När du ändrar jobb utlösaren för ett schemalagt jobb ändras jobbet. Du behöver inte använda ett Set-ScheduledJob-kommando för att tillämpa den ändrade utlösaren på det schemalagda jobbet.

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
