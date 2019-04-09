---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Ta bort objekt från pipelinen Where-Object
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 1f7d064c7bf2dd551ea96b29762fbccad8174084
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293154"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Ta bort objekt från pipelinen (Where-Object)

I Windows PowerShell kan du ofta generera och skicka längs flera objekt till en pipeline än vad du vill. Du kan ange egenskaperna för specifika objekt som ska visas med hjälp av den **Format** cmdlet: ar, men detta inte hjälper med problemet med att ta bort hela objekt från visningen. Du kanske vill filtrera objekten innan slutet av en pipeline, så att du kan utföra åtgärder på endast en delmängd av objekt som ursprungligen genererades.

Windows PowerShell innehåller en `Where-Object` cmdlet som gör att du kan testa varje objekt i pipelinen och endast skicka dem längsmed pipelinen om den uppfyller ett visst test-villkor. Objekt som inte klarar testet tas bort från pipelinen. Du kan ange testvillkoret som värde för den `Where-Object` **FilterScript** parametern.

## <a name="performing-simple-tests-with-where-object"></a>Utför enkla tester med Where-Object

Värdet för **FilterScript** är en *skriptblock* -en eller flera Windows PowerShell-kommandon som omges av klammerparenteser {} -som utvärderas SANT eller FALSKT. Dessa skriptblocken kan vara väldigt enkelt skapa dem kräver dock att känna till om en annan Windows PowerShell-koncept jämförelseoperatorer. Jämförelseoperator jämför de objekt som visas på varje sida. Jämförelseoperatorer börjar med en '-' tecken och följas av ett namn. Grundläggande jämförelseoperatorer fungerar på nästan vilken typ av objekt. Mer avancerade jämförelseoperatorer kanske bara fungerar på text eller matriser.

> [!NOTE]
> Som standard när du arbetar med text, är Windows PowerShell-jämförelseoperatorer skiftlägeskänsliga.

På grund av parsning överväganden symboler till exempel <>, och = inte används som jämförelseoperatorer. I stället består jämförelseoperatorer av bokstäver. Grundläggande jämförelseoperatorer visas i följande tabell.

|Jämförelseoperator|Innebörd|Exempel (returnerar true)|
|-----------------------|-----------|--------------------------|
|-eq|är lika med|1 -eq 1|
|-ne|Är inte lika med|1 - ne 2|
|-lt|Är mindre än|1 -lt 2|
|-le|är mindre än eller lika med|1 - le 2|
|-gt|Är större än|2 - gt 1|
|-ge|är större än eller lika med|2 -ge 1|
|– t.ex.|Liknar (jokertecken jämförelse för text)|”file.doc”-som ”f\*.skicka”?|
|-notlike|Liknar inte (jokertecken jämförelse för text)|”file.doc”-notlike ”p\*.doc”|
|-innehåller|innehåller|1,2,3 - innehåller 1|
|-notcontains|Innehåller inte|1,2,3 - notcontains 4|

WHERE-Object-skriptblock använder variabeln särskilda `$_` att referera till det aktuella objektet i pipelinen. Här är ett exempel på hur det fungerar. Om du har en lista med tal och bara vill returnera de som är mindre än 3, kan du använda Where-Object för att filtrera talen genom att skriva:

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a>Filtrering baserat på objektegenskaper

Eftersom `$_` refererar till det aktuella pipeline-objektet kan vi komma åt egenskaperna för våra tester.

Exempelvis kan vi titta på klassen Win32_SystemDriver i WMI. Det kan finnas hundratals systemdrivrutiner på ett visst system, men kanske du bara är intresserad av en viss uppsättning systemdrivrutiner, till exempel de som för närvarande körs. Om du använder Get-Member för att visa Win32_SystemDriver medlemmar (**Get-WmiObject-klassen Win32_SystemDriver | Get-Member - MemberType egenskapen**) visas att egenskapen relevanta är tillstånd och att den har ett värde ”körs” när drivrutinen körs. Du kan filtrera systemdrivrutiner, att välja endast de som körs som genom att skriva:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

Detta ger ändå en lång lista. Du kanske vill filtrera för att välja endast de drivrutiner som är konfigurerad att starta automatiskt genom att testa värdet StartMode:

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

Det ger oss en mängd information som vi behöver inte längre eftersom vi vet att drivrutinerna som körs. I själva verket är den enda information som vi behöver förmodligen nu namn och visningsnamn. Följande kommando innehåller endast de två egenskaper, vilket resulterar i mycket enklare utdata:

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

Det finns två Where-Object-element i kommandot ovan, men de kan uttryckas i ett enda Where-Object-element med hjälp av- och den logiska operatorn så här:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

De logiska operatorerna som standard visas i följande tabell.

|Logisk Operator|Innebörd|Exempel (returnerar true)|
|--------------------|-----------|--------------------------|
|- och|Logiska och; TRUE om båda sidorna utvärderas som true|(1 -eq 1) -and (2 -eq 2)|
|- eller|Logiska eller; SANT om endera sida är true|(1 - eq 1) - eller (1 - eq 2).|
|-inte|Logiskt not; omvänd true och false|-not (1 -eq 2)|
|\!|Logiskt not; omvänd true och false|\!(1 -eq 2)|
