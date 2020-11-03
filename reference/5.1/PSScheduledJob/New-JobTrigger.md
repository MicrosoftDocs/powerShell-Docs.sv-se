---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-JobTrigger
ms.openlocfilehash: de49ab937c6f3a8187f5aecd6aafc81425b8cd00
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264645"
---
# New-JobTrigger

## SAMMANFATTNING
Skapar en jobb utlösare för ett schemalagt jobb.

## SYNTAX

### En gång (standard)

```
New-JobTrigger [-RandomDelay <TimeSpan>] -At <DateTime> [-Once] [-RepetitionInterval <TimeSpan>]
 [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely] [<CommonParameters>]
```

### Varje dag

```
New-JobTrigger [-DaysInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> [-Daily] [<CommonParameters>]
```

### Varje vecka

```
New-JobTrigger [-WeeksInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> -DaysOfWeek <DayOfWeek[]>
 [-Weekly] [<CommonParameters>]
```

### AtStartup

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-AtStartup] [<CommonParameters>]
```

### AtLogon

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-User <String>] [-AtLogOn] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet **: en New-JobTrigger** skapar en jobb utlösare som startar ett schemalagt jobb vid ett engångs-eller återkommande schema, eller när en händelse inträffar.

Du kan använda **ScheduledJobTrigger** -objektet som **New-JobTrigger** returnerar för att ange en jobb utlösare för ett nytt eller befintligt schemalagt jobb.
Du kan också skapa en jobb utlösare med hjälp av Get-JobTrigger cmdlet för att hämta jobb utlösaren för ett befintligt schemalagt jobb, eller genom att använda ett värde för hash-tabellen för att representera en jobb utlösare.

När du skapar en jobb utlösare granskar du standardvärdena för de alternativ som anges i New-ScheduledJobOption-cmdleten.
Dessa alternativ, som har samma giltiga värden och standardvärden som motsvarande alternativ i **Schemaläggaren** , påverkar schemaläggningen och tids inställningen för schemalagda jobb.

**New-JobTrigger** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: schema

```
PS C:\> New-JobTrigger -Once -At "1/20/2012 3:00 AM"
```

Det här kommandot använder cmdleten **New-JobTrigger** för att skapa en jobb utlösare som bara startar ett schemalagt jobb en gången.
Värdet för *at* -parametern är en sträng som Windows PowerShell konverterar till ett **datetime** -objekt.
Värdet *vid* parameter innehåller ett explicit datum, inte bara en tid.
Om datumet utelämnas skulle utlösaren att skapas med aktuellt datum och 3:00 AM tid, vilket förmodligen motsvarar en tid i det förflutna.

### Exempel 2: dagligt schema

```
PS C:\> New-JobTrigger -Daily -At "4:15 AM" -DaysInterval 3
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/21/2012 4:15:00 AM                           True
```

Det här kommandot skapar en jobb utlösare som startar ett schemalagt jobb var tredje dag kl. 4:15

Eftersom värdet för *at* -parametern inte innehåller ett datum används det aktuella datumet som datumvärdet i **datetime** -objektet.
Om datumet och tiden är i det förflutna, startas det schemalagda jobbet vid nästa tillfälle, vilket är 3 dagar senare från värdet *vid* parameter.

### Exempel 3: vecko schema

```
PS C:\> New-JobTrigger -Weekly -DaysOfWeek Monday, Wednesday, Friday -At "23:00" -WeeksInterval 4
Id Frequency Time                  DaysOfWeek                  Enabled
-- --------- ----                  ----------                  -------
0  Weekly    9/21/2012 11:00:00 PM {Monday, Wednesday, Friday} True
```

Det här kommandot skapar en jobb utlösare som startar ett schemalagt jobb var fjärde vecka på måndag, onsdag och fredag med 2300 timmar (11:00 PM).

Du kan också ange värdet för parametern *DaysOfWeek* i heltal, till exempel `-DaysOfWeek 1, 5` .

### Exempel 4: inloggnings schema

```
PS C:\> New-JobTrigger -AtLogOn -User Domain01\Admin01
```

Det här kommandot skapar en jobb utlösare som startar ett schemalagt jobb varje gång som domän administratören loggar in på datorn.

### Exempel 5: använda en slumpmässig fördröjning

```
PS C:\> New-JobTrigger -Daily -At 1:00 -RandomDelay 00:20:00
```

Det här kommandot skapar en jobb utlösare som startar ett schemalagt jobb varje dag på 1:00 i morgon.
Kommandot använder parametern *RandomDelay* för att ange maximal fördröjning till 20 minuter.
Det innebär att jobbet körs varje dag mellan 1:00 och 1:20, med intervallet varierande pseudo-slumpvis.

Du kan använda en slumpmässig fördröjning för sampling, belastnings utjämning och andra administrativa uppgifter.
När du anger fördröjning svärdet granskar du effektiva och standardvärden för New-ScheduledJobOption-cmdleten och koordinerar fördröjningen med alternativ inställningarna.

### Exempel 6: skapa en jobb utlösare för ett nytt schemalagt jobb

```
The first command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The command saves the job trigger in the $T variable.
PS C:\> $T = New-JobTrigger -Weekly -DaysOfWeek 1,3,5 -At 12:01AM


The second command uses the Register-ScheduledJob cmdlet to create a scheduled job that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The value of the *Trigger* parameter is the trigger that is stored in the $T variable.
PS C:\> Register-ScheduledJob -Name Test-HelpFiles -FilePath C:\Scripts\Test-HelpFiles.ps1 -Trigger $T
```

Dessa kommandon använder en jobb utlösare för att skapa ett nytt schemalagt jobb.

### Exempel 7: Lägg till en jobb utlösare i ett schemalagt jobb

```
PS C:\> Add-JobTrigger -Name SynchronizeApps -Trigger (New-JobTrigger -Daily -At 3:10AM)
```

Det här exemplet visar hur du lägger till en jobb utlösare i ett befintligt schemalagt jobb.
Du kan lägga till flera jobb utlösare till ett schemalagt jobb.

Kommandot använder cmdleten Add-JobTrigger för att lägga till jobb utlösaren i det schemalagda jobbet SynchronizeApps.
Värdet för *Utlösar* -parametern är ett **New-JobTrigger-** kommando som kör jobbet varje dag kl. 3:10.

När kommandot har slutförts är SynchronizeApps ett schemalagt jobb som körs vid de tidpunkter som anges av jobb utlösaren.

### Exempel 8: skapa en utlösare för återkommande jobb

```
PS C:\> New-JobTrigger -Once -At "09/12/2013 1:00:00" -RepetitionInterval (New-TimeSpan -Hours 1) -RepetitionDuration (New-Timespan -Hours 48)
```

Det här kommandot skapar en jobb utlösare som kör ett jobb var 60: e minut i 48 timmar från den 12 september 2013 vid 1:00.

### Exempel 9: stoppa en utlösare för upprepad utskrift

```
PS C:\> Get-JobTrigger -Name SecurityCheck | Set-JobTrigger -RepetitionInterval 0:00 -RepetitionDuration 0:00
```

Med det här kommandot stoppas SecurityCheck-jobbet, som aktive ras för körning var 60: e minut tills jobb utlösaren upphör att gälla.

För att förhindra att jobbet upprepas använder kommandot Get-JobTrigger för att hämta jobb utlösaren för SecurityCheck-jobbet och cmdleten Set-JobTrigger för att ändra upprepnings intervallet och upprepnings tiden för jobb utlösaren till noll (0).

### Exempel 10: skapa en jobb utlösare per timme

```
PS C:\> New-JobTrigger -Once -At "9/21/2012 0am" -RepetitionInterval (New-TimeSpan -Hour 12) -RepetitionDuration ([TimeSpan]::MaxValue)
```

Följande kommando skapar en jobb utlösare som kör ett schemalagt jobb en gång var 12: e timme under en obestämd tids period.
Schemat börjar i morgon (9/21/2012) vid midnatt (0:00 AM).

## PARAMETRAR

### – På
Startar jobbet vid angivet datum och tid.
Ange ett **datetime** -objekt, till exempel ett som Get-Date cmdlet returnerar, eller en sträng som kan konverteras till ett datum och en tid, till exempel "April 19, 2012 15:00", "12/31" eller "3am".
Om du inte anger ett element i datumet, till exempel året, har datumet i utlösaren motsvarande element från det aktuella datumet.

När du använder parametern *Once* ställer du in värdet för parametern *at* till ett framtida datum och en framtida tidpunkt.
Eftersom standard datumet i ett **datetime** -objekt är det aktuella datumet, om du anger en tid före den aktuella tiden utan ett explicit datum, skapas jobb utlösaren för en tid i det förflutna.

**Datetime** -objekt och strängar som konverteras till **datetime** -objekt justeras automatiskt så att de är kompatibla med de datum-och tids format som valts för den lokala datorn i region och språk på kontroll panelen.

```yaml
Type: System.DateTime
Parameter Sets: Once, Daily, Weekly
Aliases:

Required: True
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
Parameter Sets: AtLogon
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AtStartup
Startar det schemalagda jobbet när Windows startas.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtStartup
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Varje dag
Anger ett återkommande schema för dagligt jobb.
Använd de andra parametrarna i den *dagliga* parameter uppsättningen för att ange schema information.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Daily
Aliases:

Required: True
Position: 0
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
Parameter Sets: Daily
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DaysOfWeek
Anger vecko dagarna som ett schemalagt vecko jobb körs på.
Ange dag namn, till exempel "måndag" eller heltal 0-6, där 0 representerar söndag.
Den här parametern krävs i den veckobaserade parameter uppsättningen.

Dag namn konverteras till deras heltals värden i jobb utlösaren.
När du omger dag namn inom citat tecken i ett kommando, omger du varje dag med separata citat tecken, till exempel "måndag", "tisdag".
Om du omger flera dag namn i ett enkelt citat tecken, summeras motsvarande heltals värden.
Till exempel "måndag, tisdag" (1, 2) resulterar i värdet "onsdag" (3).

```yaml
Type: System.DayOfWeek[]
Parameter Sets: Weekly
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – En gång
Anger en icke-återkommande (en tid) eller ett anpassat upprepat schema.
Om du vill skapa ett upprepat schema använder du parametern *Once* med parametrarna *RepetitionDuration* och *RepetitionInterval* .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RandomDelay
Aktiverar en slumpmässig fördröjning som börjar vid den schemalagda start tiden och anger högsta fördröjnings värde.
Längden på fördröjningen är att ställa in pseudo – slumpvis för varje start och varierar från ingen fördröjning till den tid som anges av värdet för den här parametern.
Standardvärdet noll (00:00:00), inaktiverar slumpmässig fördröjning.

Ange ett TimeSpan-objekt, till exempel ett som returneras av New-TimeSpan-cmdleten, eller ange ett värde i \<hours\> : \<minutes\> : \<seconds\> format, som automatiskt konverteras till ett **TimeSpan** -objekt.

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
Parameter Sets: Once
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
Om värdet för **RepetitionInterval** till exempel är 5 minuter och värdet för **RepetitionDuration** är 2 timmar utlöses jobbet var femte minut i två timmar.

Ange ett TimeSpan-objekt, till exempel ett som New-TimeSpan cmdlet returnerar eller en sträng som kan konverteras till ett TimeSpan-objekt, till exempel "1:05:30".

Om du vill köra ett jobb oändligt lägger du till parametern *RepeatIndefinitely* i stället.

Om du vill stoppa ett jobb innan jobbets repetitions varaktighet upphör att gälla, använder du Set-JobTrigger cmdlet för att ange värdet noll (0) för *RepetitionDuration* -värdet.

Den här parametern är endast giltig när parametrarna *Once* , *at* och *RepetitionInterval* används i kommandot.

```yaml
Type: System.TimeSpan
Parameter Sets: Once
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

Den här parametern är endast giltig när parametrarna *Once* , *at* och *RepetitionDuration* används i kommandot.

```yaml
Type: System.TimeSpan
Parameter Sets: Once
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
Parameter Sets: AtLogon
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Varje vecka
Anger ett återkommande veckovis jobb schema.
Använd de andra parametrarna i vecko parametern set för att ange schema information.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Weekly
Aliases:

Required: True
Position: 0
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
Parameter Sets: Weekly
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

### Inget
Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger

## ANTECKNINGAR

* Jobb utlösare sparas inte på disk. Schemalagda jobb sparas dock på disk och du kan använda Get-JobTrigger för att hämta jobb utlösaren för schemalagda jobb.
* **New-JobTrigger** förhindrar inte att du skapar en jobb utlösare som inte kommer att köra ett schemalagt jobb, till exempel engångs utlösare för ett datum som redan har infallit.
* Register-ScheduledJob cmdleten accepterar ett ScheduledJobTrigger-objekt, till exempel en som returneras av cmdletarna **New-JobTrigger** eller Get-JobTrigger eller en hash-tabell med utlösarens värden.

  Om du vill skicka en hash-tabell använder du följande nycklar.

  `@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (eller en giltig tids sträng); `DaysOfWeek="Monday", "Wednesday"` (eller valfri kombination av dag namn); `Interval=2` (eller ett giltigt frekvens intervall); `RandomDelay="30minutes"` (eller en giltig TimeSpan-sträng); `User="Domain1\User01` (eller en giltig användare, används endast med värdet för *AtLogon* )}

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
