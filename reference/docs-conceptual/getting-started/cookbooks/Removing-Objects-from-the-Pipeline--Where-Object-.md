---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Ta bort objekt från Pipeline där objekt
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 2d89defdb1b234a9d0021fc06e1f05a95bb1bce9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Ta bort objekt från Pipeline (Where-Object)

I Windows PowerShell kan du ofta generera och skicka vidare flera objekt för en pipeline än du vill. Du kan ange egenskaper för specifika objekt som ska visas med hjälp av den **Format** cmdlets, men detta hjälper inte problemet med att ta bort hela objekt från skärmen. Du kanske vill filtrera objekt före utgången av en pipeline, så att du kan utföra åtgärder på endast en delmängd av objekt som ursprungligen genererades.

Windows PowerShell innehåller en **Where-Object** cmdlet som du kan testa varje objekt i pipeline och bara skicka den längsmed pipelinen om den uppfyller ett visst Testvillkor. Objekt som inte klarar testet tas bort från pipeline. Du kan ange testvillkoret som värde för den **var ObjectFilterScript** parameter.

### <a name="performing-simple-tests-with-where-object"></a>Utför enkla tester med Where-Object

Värdet för **FilterScript** är en *skriptblock* - en eller flera Windows PowerShell-kommandon omges av klammerparenteser {} - som utvärderas till true eller false. Dessa skriptblock kan vara mycket enkla, men skapa dem kräver att veta om en annan Windows PowerShell-konceptet jämförelseoperatorer. Jämförelseoperator jämför de objekt som visas på varje sida. Jämförelseoperatorer börja med en '-' tecken och följas av ett namn. Grundläggande jämförelseoperatorer fungerar på nästan vilken typ av objekt. Mer avancerade jämförelseoperatorer kanske bara fungerar på text eller matriser.

> [!NOTE]
> Som standard när du arbetar med text, är Windows PowerShell-jämförelseoperatorer inte skiftlägeskänsliga.

Symboler till exempel <>, på grund av parsning överväganden och = inte används som jämförelseoperatorer. I stället består jämförelseoperatorer av bokstäver. Grundläggande jämförelseoperatorer visas i följande tabell.

|Jämförelseoperatorn|Innebörd|Exempel (returnerar true)|
|-----------------------|-----------|--------------------------|
|-eq|är lika med|1 - eq 1|
|-ne|Är inte lika med|1 - ne 2|
|-lt|Är mindre än|1 - lt 2|
|-le|Är mindre än eller lika med|1 - le 2|
|-gt|Är större än|2 - gt 1|
|-ge|Är större än eller lika med|2 -ge 1|
|-exempel|Liknar (jämförelse med jokertecken för text)|”file.doc”-som ”f\*.skicka”?|
|-notlike|Är inte som (jämförelse med jokertecken för text)|”file.doc”-notlike ”p\*.doc”|
|-innehåller|Innehåller|1,2,3 - innehåller 1|
|-notcontains|Innehåller inte|1,2,3 - notcontains 4|

WHERE-Object-skriptblock använder variabeln särskilda $_ att referera till det aktuella objektet i pipelinen. Här är ett exempel på hur det fungerar. Om du har en lista med tal och bara vill returnera de som är mindre än 3, kan du använda Where-Object för att filtrera numren genom att skriva:

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a>Filtrering baserat på objektets egenskaper

Eftersom $_ refererar till det aktuella pipeline-objektet, kan vi komma åt egenskaperna för våra tester.

Ett exempel kan vi titta på klassen Win32_SystemDriver i WMI. Det kan finnas hundratals drivrutiner för filsystemet på ett visst system, men kanske du bara är intresserad av en viss uppsättning drivrutiner för filsystemet, till exempel de som för närvarande körs. Om du använder Get-medlem för att visa Win32_SystemDriver medlemmarna (**Get-WmiObject-klassen Win32_SystemDriver | Get-Member - MemberType egenskapen**) att egenskapen relevanta är tillstånd och att den har värdet ”körs” när drivrutinen körs visas. Du kan filtrera drivrutiner för filsystemet väljer du kör dem genom att skriva:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

Detta ger fortfarande en lång lista. Du kanske vill filtrera för att bara markera de drivrutiner som startar automatiskt genom att testa värdet StartMode:

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

Det ger oss en stor mängd information som vi inte längre behöver eftersom vi vet att drivrutinerna som körs. I praktiken är den enda information som vi måste förmodligen nu namn och visningsnamn. Följande kommando innehåller endast de två egenskaper, vilket resulterar i mycket enklare utdata:

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

Standard logiska operatorer visas i följande tabell.

|Logisk Operator|Innebörd|Exempel (returnerar true)|
|--------------------|-----------|--------------------------|
|- och|Logiska och; TRUE om båda sidorna utvärderas som true|(1 - eq 1) - och (2 - eq 2).|
|- eller|Logisk eller; TRUE om endera sida är true|(1 - eq 1) - eller (1 - eq 2).|
|-inte|Logiska inte; ångrar SANT och FALSKT|-inte (1 - eq 2)|
|\!|Logiska inte; ångrar SANT och FALSKT|\!(1 - eq 2)|