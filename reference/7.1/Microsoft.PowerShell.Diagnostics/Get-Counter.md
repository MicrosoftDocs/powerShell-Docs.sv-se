---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-counter?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Counter
ms.openlocfilehash: b8b78c0a2dec0c3e51c91df522cc5b026952a222
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267752"
---
# Get-Counter

## SAMMANFATTNING
Hämtar prestanda räknar data från lokala datorer och fjärrdatorer.

## SYNTAX

### GetCounterSet (standard)

```
Get-Counter [[-Counter] <String[]>] [-SampleInterval <Int32>] [-MaxSamples <Int64>] [-Continuous]
 [-ComputerName <String[]>] [<CommonParameters>]
```

### ListSetSet

```
Get-Counter [-ListSet] <String[]> [-ComputerName <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Get-Counter`Cmdlet: en hämtar prestanda räknar data direkt från övervakningen av prestanda i Windows-serien med operativ system. `Get-Counter` hämtar prestanda data från en lokal dator eller fjärrdatorer.

Du kan använda `Get-Counter` parametrarna för att ange en eller flera datorer, lista över prestanda räknar uppsättningar och de instanser som de innehåller, ange exempel intervall och ange maximalt antal exempel. Utan parametrar `Get-Counter` hämtar prestanda räknar data för en uppsättning system räknare.

Många räknar uppsättningar skyddas av åtkomst kontrol listor (ACL). Om du vill se alla räknar uppsättningar öppnar du PowerShell med alternativet **Kör som administratör** .

Den här cmdleten introducerades om i PowerShell 7.

## EXEMPEL

### Exempel 1: hämta listan med räknar uppsättningar

Det här exemplet hämtar listan över räknar uppsättningar på den lokala datorn.

```powershell
Get-Counter -ListSet *
```

```Output
CounterSetName     : Processor
MachineName        : .
CounterSetType     : MultiInstance
Description        : The Processor performance object consists of counters that measure aspects ...
                     computer that performs arithmetic and logical computations, initiates ...
                     computer can have multiple processors.  The processor object represents ...
Paths              : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
PathsWithInstances : {\Processor(0)\% Processor Time, \Processor(1)\% Processor Time, ...
Counter            : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
```

`Get-Counter` använder parametern **ListSet** med en asterisk ( `*` ) för att hämta listan över räknar uppsättningar.
Punkten ( `.` ) i kolumnen **MachineName** representerar den lokala datorn.

### Exempel 2: Ange SampleInterval och MaxSamples

I det här exemplet hämtas räknar data för alla processorer på den lokala datorn. Data samlas in med två sekunders mellanrum tills det finns tre exempel.

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -SampleInterval 2 -MaxSamples 3
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/18/2019 14:39:56        \\Computer01\processor(_total)\% processor time :
                          20.7144271584086

6/18/2019 14:39:58        \\Computer01\processor(_total)\% processor time :
                          10.4391790575511

6/18/2019 14:40:01        \\Computer01\processor(_total)\% processor time :
                          37.5968799396998
```

`Get-Counter` använder **Counter** -parametern för att ange räknar Sök vägen `\Processor(_Total)\% Processor Time` . Parametern **SampleInterval** anger ett intervall på två sekunder för att kontrol lera räknaren. **MaxSamples** anger att tre är det maximala antalet gånger för att kontrol lera räknaren.

### Exempel 3: Hämta kontinuerliga exempel på en räknare

I det här exemplet hämtas kontinuerliga exempel för en räknare varje sekund. Tryck på <kbd>CTRL</kbd>C om du vill stoppa kommandot + <kbd>C</kbd>. Om du vill ange ett längre intervall mellan exempel använder du parametern **SampleInterval** .

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -Continuous
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 15:35:03        \\Computer01\processor(_total)\% processor time :
                          43.8522842937022

6/19/2019 15:35:04        \\Computer01\processor(_total)\% processor time :
                          29.7896844697383

6/19/2019 15:35:05        \\Computer01\processor(_total)\% processor time :
                          29.4962645638135

6/19/2019 15:35:06        \\Computer01\processor(_total)\% processor time :
                          25.5901500127408
```

`Get-Counter` använder **Counter** -parametern för att ange `\Processor\% Processor Time` räknaren.
Den **kontinuerliga** parametern anger för att hämta exempel varje sekund tills kommandot har stoppats med <kbd>CTRL</kbd> + <kbd>+ C</kbd>.

### Exempel 4: alfabetisk lista över räknar uppsättningar

I det här exemplet används pipelinen för att hämta räknar listan och sortera listan i alfabetisk ordning.

```powershell
Get-Counter -ListSet * |
  Sort-Object -Property CounterSetName |
    Format-Table CounterSetName, CounterSetType -AutoSize
```

```Output
CounterSetName                        CounterSetType
--------------                        --------------
.NET CLR Data                         SingleInstance
.NET Data Provider for SqlServer      SingleInstance
AppV Client Streamed Data Percentage  SingleInstance
Authorization Manager Applications    SingleInstance
BitLocker                             MultiInstance
Bluetooth Device                      SingleInstance
Cache                                 SingleInstance
Client Side Caching                   SingleInstance
```

`Get-Counter` använder parametern **ListSet** med en asterisk ( `*` ) för att få en fullständig lista över räknar uppsättningar. **CounterSet** -objekten skickas nedåt i pipelinen. `Sort-Object` använder **egenskaps** parametern för att ange att objekten sorteras efter **CounterSetName**. Objekten skickas ned pipelinen till `Format-Table` . Parametern **AutoSize** justerar kolumn bredderna för att minimera trunkering.

Punkten ( `.` ) i kolumnen **MachineName** representerar den lokala datorn.

### Exempel 5: kör ett bakgrunds jobb för att hämta räknar data

I det här exemplet `Start-Job` kör ett `Get-Counter` kommando som bakgrunds jobb på den lokala datorn.
Om du vill visa prestanda räknarens utdata från jobbet använder du `Receive-Job` cmdleten.

```powershell
Start-Job -ScriptBlock {Get-Counter -Counter "\LogicalDisk(_Total)\% Free Space" -MaxSamples 1000}
```

```Output
Id     Name  PSJobTypeName   State    HasMoreData  Location   Command
--     ----  -------------   -----    -----------  --------   -------
1      Job1  BackgroundJob   Running  True         localhost  Get-Counter -Counter
```

`Start-Job` använder parametern **script block** för att köra ett `Get-Counter` kommando. `Get-Counter` använder **Counter** -parametern för att ange räknar Sök vägen `\LogicalDisk(_Total)\% Free Space` . Parametern **MaxSamples** anger för att hämta 1000-exempel av räknaren.

### Exempel 6: Hämta räknar data från flera datorer

I det här exemplet används en variabel för att hämta prestanda räknar data från två datorer.

```powershell
$DiskReads = "\LogicalDisk(C:)\Disk Reads/sec"
$DiskReads | Get-Counter -ComputerName Server01, Server02 -MaxSamples 10
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/21/2019 10:51:04        \\Server01\logicaldisk(c:)\disk reads/sec :
                          0

                          \\Server02\logicaldisk(c:)\disk reads/sec :
                          0.983050344269146
```

`$DiskReads`Variabeln lagrar `\LogicalDisk(C:)\Disk Reads/sec` räknar Sök vägen. `$DiskReads`Variabeln skickas ned pipelinen till `Get-Counter` . **Counter** är den första positions parametern och accepterar sökvägen som lagras i `$DiskReads` . **Computername** anger de två datorerna och **MaxSamples** anger för att hämta 10 exempel från varje dator.

### Exempel 7: Hämta en räknares instans värden från flera slumpmässiga datorer

I det här exemplet hämtas värdet för en prestanda räknare på 50 slumpmässiga, fjärrdatorer i företaget. Parametern **computername** använder slumpmässiga dator namn som lagras i en variabel. Skapa om variabeln om du vill uppdatera dator namnen i variabeln.

Ett alternativ för Server namnen i parametern **computername** är att använda en textfil. Ett exempel:

`-ComputerName (Get-Random (Get-Content -Path C:\Servers.txt) -Count 50)`

Räknar Sök vägen innehåller en asterisk ( `*` ) i instans namnet för att hämta data för var och en av datorns processorer.

```powershell
$Servers = Get-Random (Get-Content -Path C:\Servers.txt) -Count 50
$Counter = "\Processor(*)\% Processor Time"
Get-Counter -Counter $Counter -ComputerName $Servers
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/20/2019 12:20:35        \\Server01\processor(0)\% processor time :
                          6.52610319637854

                          \\Server01\processor(1)\% processor time :
                          3.41030663625782

                          \\Server01\processor(2)\% processor time :
                          9.64189975649925

                          \\Server01\processor(3)\% processor time :
                          1.85240835619747

                          \\Server01\processor(_total)\% processor time :
                          5.35768447160776
```

`Get-Random`Cmdleten använder `Get-Content` för att välja 50 slumpmässiga dator namn från `Servers.txt` filen. Fjärrdatorns namn lagras i `$Servers` variabeln. `\Processor(*)\% Processor Time`Räknar Sök vägen lagras i `$Counter` variabeln. `Get-Counter` använder **Counter** -parametern för att ange räknare i `$Counter` variabeln. Parametern **computername** anger dator namnen i `$Servers` variabeln.

### Exempel 8: Använd egenskapen Path för att hämta formaterade Sök vägs namn

I det här exemplet används **Sök vägs** egenskapen för en räknare för att hitta de formaterade Sök vägs namnen för prestanda räknarna.

Pipelinen används med `Where-Object` cmdleten för att hitta en delmängd av Sök vägs namnen. Om du vill söka efter en lista över räknar Sök vägar tar du bort pipelinen ( `|` ) och `Where-Object` kommandot.

`$_`Är en automatisk variabel för det aktuella objektet i pipelinen.
Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

```powershell
(Get-Counter -ListSet Memory).Paths | Where-Object { $_ -like "*Cache*" }
```

```Output
\Memory\Cache Faults/sec
\Memory\Cache Bytes
\Memory\Cache Bytes Peak
\Memory\System Cache Resident Bytes
\Memory\Standby Cache Reserve Bytes
\Memory\Standby Cache Normal Priority Bytes
\Memory\Standby Cache Core Bytes
\Memory\Long-Term Average Standby Cache Lifetime (s)
```

`Get-Counter` använder parametern **ListSet** för att ange **minnes** räknar uppsättningen. Kommandot omges av parenteser så att egenskapen **Paths** returnerar varje sökväg som en sträng. Objekten skickas ned pipelinen till `Where-Object` . `Where-Object` använder variabeln `$_` för att bearbeta varje objekt och använder `-like` operatorn för att hitta matchningar för strängen `*Cache*` . Asteriskerna ( `*` ) är jokertecken för alla tecken.

### Exempel 9: Använd egenskapen PathsWithInstances för att hämta formaterade Sök vägs namn

I det här exemplet hämtas de formaterade Sök vägs namnen som innehåller instanserna för prestanda räknaren **fysisk disk** .

```powershell
(Get-Counter -ListSet PhysicalDisk).PathsWithInstances
```

```Output
\PhysicalDisk(0 C:)\Current Disk Queue Length
\PhysicalDisk(_Total)\Current Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Time
\PhysicalDisk(_Total)\% Disk Time
\PhysicalDisk(0 C:)\Avg. Disk Queue Length
\PhysicalDisk(_Total)\Avg. Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Read Time
\PhysicalDisk(_Total)\% Disk Read Time
```

`Get-Counter` använder parametern **ListSet** för att ange **fysisk disk** uppsättning. Kommandot omges av parenteser så att egenskapen **PathsWithInstances** returnerar varje Sök vägs instans som en sträng.

### Exempel 10: Hämta ett enda värde för varje räknare i en räknar uppsättning

I det här exemplet returneras ett enskilt värde för varje prestanda räknare i den lokala datorns **minnes** räknar uppsättning.

```powershell
$MemCounters = (Get-Counter -ListSet Memory).Paths
Get-Counter -Counter $MemCounters
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 12:05:00        \\Computer01\memory\page faults/sec :
                          868.772077545597

                          \\Computer01\memory\available bytes :
                          9031176192

                          \\Computer01\memory\committed bytes :
                          8242982912

                          \\Computer01\memory\commit limit :
                          19603333120
```

`Get-Counter` använder parametern **ListSet** för att ange **minnes** räknar uppsättningen. Kommandot omges av parenteser så att egenskapen **Paths** returnerar varje sökväg som en sträng. Sök vägarna lagras i `$MemCounters` variabeln. `Get-Counter` använder **Counter** -parametern för att ange räknar Sök vägar i `$MemCounters` variabeln.

### Exempel 11: Visa ett objekts egenskaps värden

Egenskaps värden i **PerformanceCounterSample** -objektet representerar varje data exempel. I det här exemplet använder vi egenskaperna för **CounterSamples** -objektet för att undersöka, välja, sortera och gruppera data.

```powershell
$Counter = "\\Server01\Process(Idle)\% Processor Time"
$Data = Get-Counter $Counter
$Data.CounterSamples | Format-List -Property *
```

```Output
Path             : \\Server01\process(idle)\% processor time
InstanceName     : idle
CookedValue      : 198.467899571389
RawValue         : 14329160321003
SecondValue      : 128606459528326201
MultipleCount    : 1
CounterType      : Timer100Ns
Timestamp        : 6/19/2019 12:20:49
Timestamp100NSec : 128606207528320000
Status           : 0
DefaultScale     : 0
TimeBase         : 10000000
```

Räknar Sök vägen lagras i `$Counter` variabeln. `Get-Counter` hämtar ett exempel på räknar värden och lagrar resultatet i `$Data` variabeln. `$Data`Variabeln använder egenskapen **CounterSamples** för att hämta objektets egenskaper. Objektet skickas ned pipelinen till `Format-List` . **Egenskaps** parametern använder en asterisk ( `*` ) som jokertecken för att markera alla egenskaper.

### Exempel 12: mat ris värden för prestanda räknare

I det här exemplet lagrar en variabel varje prestanda räknare. Egenskapen **CounterSamples** är en matris som kan visa vissa räknar värden.

Om du vill visa varje räknar exempel använder du `$Counter.CounterSamples` .

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples[0]
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              1.33997091699662
```

`Get-Counter` använder **Counter** -parametern för att ange räknaren `\Processor(*)\% Processor Time` . Värdena lagras i `$Counter` variabeln.
`$Counter.CounterSamples[0]` visar mat ris värdet för det första räknarvärdet.

### Exempel 13: jämför prestanda räknar värden

I det här exemplet hittar du mängden processor tid som används av varje processor på den lokala datorn. Egenskapen **CounterSamples** används för att jämföra räknar data med ett angivet värde.

Om du vill visa varje räknar exempel använder du `$Counter.CounterSamples` .

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples | Where-Object { $_.CookedValue -lt "20" }
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              12.6398025240208
\\Computer01\processor(1)\% processor time   1              15.7598095767344
```

`Get-Counter` använder **Counter** -parametern för att ange räknaren `\Processor(*)\% Processor Time` . Värdena lagras i `$Counter` variabeln. De objekt som lagras i `$Counter.CounterSamples` skickas till pipelinen. `Where-Object` använder ett-skript block för att jämföra varje objekt värde mot ett angivet värde på 20. `$_.CookedValue`Är en variabel för det aktuella objektet i pipelinen. Räknare med en **CookedValue** som är mindre än 20 visas.

### Exempel 14: sortera prestanda räknar data

Det här exemplet visar hur du sorterar prestanda räknar data. Exemplet hittar processerna på datorn som använder den mest processor tiden under exemplet.

```powershell
$Procs = Get-Counter -Counter "\Process(*)\% Processor Time"
$Procs.CounterSamples | Sort-Object -Property CookedValue -Descending |
   Format-Table -Property Path, InstanceName, CookedValue -AutoSize
```

```Output
Path                                                         InstanceName             CookedValue
----                                                         ------------             -----------
\\Computer01\process(_total)\% processor time                _total              395.464129650573
\\Computer01\process(idle)\% processor time                  idle                389.356575524695
\\Computer01\process(mssense)\% processor time               mssense             3.05377706293879
\\Computer01\process(csrss#1)\% processor time               csrss               1.52688853146939
\\Computer01\process(microsoftedgecp#10)\% processor time    microsoftedgecp     1.52688853146939
\\Computer01\process(runtimebroker#5)\% processor time       runtimebroker                      0
\\Computer01\process(settingsynchost)\% processor time       settingsynchost                    0
\\Computer01\process(microsoftedgecp#16)\% processor time    microsoftedgecp                    0
```

`Get-Counter` använder **Counter** -parametern för att ange `\Process(*)\% Processor Time` räknaren för alla processer på den lokala datorn. Resultatet lagras i `$Procs` variabeln. `$Procs`Variabeln med egenskapen **CounterSamples** skickar **PerformanceCounterSample** -objekten nedåt i pipelinen. `Sort-Object` använder **egenskaps** parametern för att sortera objekten efter **CookedValue** i **fallande** ordning. `Format-Table` använder **egenskaps** parametern för att välja kolumner för utdata. Parametern **AutoSize** justerar kolumn bredderna för att minimera trunkering.

## PARAMETRAR

### -ComputerName

Anger ett dator namn eller en kommaavgränsad **matris med fjärrdatornamn.** Använd NetBIOS-namnet, en IP-adress eller datorns fullständigt kvalificerade domän namn.

Om du vill hämta prestanda räknar data från den **lokala** datorn utesluter du parametern **computername** .
För utdata, till exempel en **ListSet** som innehåller kolumnen **MachineName** , visar en punkt ( `.` ) den lokala datorn.

`Get-Counter` förlitar sig inte på PowerShell-fjärrkommunikation. Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Kontinuerlig

När den **kontinuerliga** har angetts `Get-Counter` hämtar vi exempel tills du trycker på <kbd>CTRL</kbd> + <kbd>C</kbd>. Exempel hämtas varje sekund för varje angiven prestanda räknare. Använd parametern **SampleInterval** för att öka intervallet mellan kontinuerliga exempel.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Counter

Anger sökvägen till en eller flera räknar Sök vägar. Sökvägar är indata som en kommaavgränsad matris, en variabel eller värden från en textfil. Du kan skicka räknar Sök vägs strängar nedåt i pipeline till `Get-Counter` .

Räknar Sök vägar använder följande syntax:

`\\ComputerName\CounterSet(Instance)\CounterName`

`\CounterSet(Instance)\CounterName`

Ett exempel:

`\\Server01\Processor(*)\% User Time`

`\Processor(*)\% User Time`

`\\ComputerName`Är valfritt i en prestanda räknar Sök väg. Om räknar Sök vägen inte innehåller dator namnet, `Get-Counter` använder den lokala datorn.

En asterisk ( `*` ) i instansen är ett jokertecken för att hämta alla instanser av räknaren.

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -ListSet

Visar en lista över prestanda räknar uppsättningar på datorerna. Använd en asterisk ( `*` ) för att ange alla räknar uppsättningar. Ange ett namn eller en kommaavgränsad sträng för räknar uppsättnings namn. Du kan skicka räknar uppsättnings namn nedåt i pipelinen.

Om du vill hämta en räknare som anger formaterade räknar Sök vägar använder du parametern **ListSet** . Egenskaperna för **Sök vägarna** och **PathsWithInstances** för varje räknare innehåller de enskilda räknar Sök vägarna formaterade som en sträng.

Du kan spara räknar Sök vägs strängarna i en variabel eller använda pipelinen för att skicka strängen till ett annat `Get-Counter` kommando.

Till exempel för att skicka varje **processors** räknar Sök väg till `Get-Counter` :

`Get-Counter -ListSet Processor | Get-Counter`

> [!NOTE]
> Det `Get-Counter` går inte att hämta egenskapen **Description** för räknar uppsättningen i PowerShell 7. **Beskrivningen** anges till `$null` .

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -MaxSamples

Anger antalet prover som ska hämtas från varje angiven prestanda räknare. Om du vill hämta en konstant data ström med exempel använder du den **kontinuerliga** parametern.

Om parametern **MaxSamples** inte anges `Get-Counter` hämtas bara ett sampel för varje angiven räknare.

Om du vill samla in en stor data uppsättning kör du `Get-Counter` som ett PowerShell-bakgrunds jobb. Mer information finns i artikeln [om jobb](../Microsoft.PowerShell.Core/About/about_Jobs.md).

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SampleInterval

Anger antalet sekunder mellan exempel för varje angiven prestanda räknare. Om parametern **SampleInterval** inte anges `Get-Counter` används ett intervall på en sekund.

```yaml
Type: System.Int32
Parameter Sets: GetCounterSet
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

### System.String[]

`Get-Counter` accepterar pipeline-inflöden för räknar Sök vägar och räknar uppsättnings namn.

## UTDATA

### Microsoft. PowerShell. commands. GetCounter. CounterSet, Microsoft. PowerShell. commands. GetCounter. PerformanceCounterSampleSet, Microsoft. PowerShell. commands. GetCounter. PerformanceCounterSample

Om du vill visa ett objekts egenskaper skickar du ut pipelinen till `Get-Member` . De objekt typer som ska matas ut är följande:

**ListSet** -parameter: **Microsoft. PowerShell. commands. GetCounter. CounterSet**

**Räknar** parameter: **Microsoft. PowerShell. commands. GetCounter. PerformanceCounterSampleSet**

**CounterSamples** -egenskap: **Microsoft. PowerShell. commands. GetCounter. PerformanceCounterSample**

## ANTECKNINGAR

Om inga parametrar har angetts `Get-Counter` hämtas ett exempel för varje angiven prestanda räknare. Använd parametrarna **MaxSamples** och **kontinuerlig** för att få fler exempel.

`Get-Counter` använder ett intervall på en sekund mellan exempel. Använd parametern **SampleInterval** för att öka intervallet.

Värdena för **MaxSamples** och **SampleInterval** gäller för alla räknare på varje dator i kommandot. Ange olika värden för olika räknare genom att ange separata `Get-Counter` kommandon.

När du använder parametern **ListSet** i PowerShell 7 `Get-Counter` kan inte hämta egenskapen **Description** för räknar uppsättningen. **Beskrivningen** anges till `$null` .

## RELATERADE LÄNKAR

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md)

[Format-List](../Microsoft.PowerShell.Utility/Format-List.md)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Hämta medlem](../Microsoft.PowerShell.Utility/Get-Member.md)

[Mottagning – jobb](../Microsoft.PowerShell.Core/Receive-Job.md)

[Start – jobb](../Microsoft.PowerShell.Core/Start-Job.md)

[Where-objekt](..//Microsoft.PowerShell.Core/Where-Object.md)

