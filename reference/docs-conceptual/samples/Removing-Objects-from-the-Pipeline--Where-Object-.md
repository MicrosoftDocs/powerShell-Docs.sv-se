---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Ta bort objekt från pipelinen där objektet
ms.openlocfilehash: c47efd38e2ff40ce3b7bf50b161cc38de922c5da
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030879"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Ta bort objekt från pipelinen (Where-Object)

I Windows PowerShell genererar och passerar du ofta fler objekt till en pipeline än du vill. Du kan ange egenskaperna för specifika objekt som ska visas med hjälp av **format** -cmdletar, men det hjälper inte till med problemet med att ta bort hela objekt från skärmen. Du kanske vill filtrera objekt före slutet av en pipeline, så att du kan utföra åtgärder på endast en delmängd av de ursprungligen genererade objekten.

Windows PowerShell innehåller en `Where-Object`-cmdlet som gör att du kan testa varje objekt i pipelinen och bara skicka det längs pipelinen om det uppfyller ett visst test villkor. Objekt som inte klarar testet tas bort från pipelinen. Du anger test villkoret som värdet för parametern `Where-Object` **FilterScript** .

## <a name="performing-simple-tests-with-where-object"></a>Utföra enkla tester med Where-Object

Värdet för **FilterScript** är ett *skript block* – ett eller flera Windows PowerShell-kommandon som omges av klammerparenteser {} – som utvärderas till true eller false. Dessa skript block kan vara väldigt enkla, men att skapa dem kräver att du känner till ett annat Windows PowerShell-begrepp, jämförelse operatorer. En jämförelse operator jämför objekten som visas på varje sida av den. Jämförelse operatorer börjar med ett-och följt av ett namn. Grundläggande jämförelse operatorer fungerar på nästan alla typer av objekt. De mer avancerade jämförelse operatörerna kanske bara arbetar med text eller matriser.

> [!NOTE]
> När du arbetar med text är Windows PowerShell-jämförelsen som standard Skift läges okänslig.

På grund av tolknings överväganden används symboler som <, > och = inte som jämförelse operatorer. Jämförelse operatorer består i stället av bokstäver. De grundläggande jämförelse operatorerna visas i följande tabell.

|Jämförelseoperator|Innebörd|Exempel (returnerar true)|
|-----------------------|-----------|--------------------------|
|-EQ|är lika med|1 – EQ 1|
|-Ne|Är inte lika med|1 – Ne 2|
|-lt|Är mindre än|1 – lt 2|
|-Le|är mindre än eller lika med|1 – Le 2|
|-gt|Är större än|2 – gt 1|
|-ge|är större än eller lika med|2-ge 1|
|– som|Liknar (jämförelse av jokertecken för text)|"File. doc" – som "f\*. gör?"|
|-notlike|Liknar inte (jämförelse av jokertecken för text)|"File. doc"-notlike "p\*. doc"|
|– innehåller|innehåller|1, 2, 3 – innehåller 1|
|-notcontains|Innehåller inte|1, 2, 3-notcontains 4|

Where-Object skript block använder den särskilda variabeln `$_` för att referera till det aktuella objektet i pipelinen. Här är ett exempel på hur det fungerar. Om du har en lista med tal, och bara vill returnera de som är mindre än 3, kan du använda Where-Object för att filtrera talen genom att skriva:

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a>Filtrering baserat på objekt egenskaper

Eftersom `$_` refererar till det aktuella pipeline-objektet kan vi komma åt dess egenskaper för våra tester.

Vi kan till exempel titta på Win32_SystemDriver-klassen i WMI. Det kan finnas hundratals system driv rutiner i ett visst system, men du kanske bara är intresse rad av en viss uppsättning system driv rutiner, till exempel de som för närvarande körs. Om du använder Get-Member för att Visa Win32_SystemDriver medlemmar (**Get-WmiObject-Class Win32_SystemDriver | Get-Member-MemberType-egenskap**) ser du att relevant egenskap är State och att den har värdet "körs" när driv rutinen körs. Du kan filtrera system driv rutinerna, välja enbart de som körs genom att skriva:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

Detta skapar fortfarande en lång lista. Du kanske vill filtrera för att endast välja de driv rutiner som ska starta automatiskt genom att testa start mode-värdet också:

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

Detta ger oss mycket information som vi inte längre behöver eftersom vi vet att driv rutinerna körs. Den enda information som vi förmodligen behöver i det här läget är i själva verket namnet och visnings namnet. Följande kommando innehåller bara de två egenskaperna, vilket resulterar i mycket enklare utdata:

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

Det finns två element i WHERE-objekt i ovanstående kommando, men de kan uttryckas i ett enda WHERE-objekt-element med hjälp av operatorn-och logiska operatorn, så här:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

De logiska standard operatörerna visas i följande tabell.

|Logisk operator|Innebörd|Exempel (returnerar true)|
|--------------------|-----------|--------------------------|
|-och|Logisk och; sant om båda sidorna är sanna|(1 – EQ 1)-och (2-EQ 2)|
|-eller|Logiskt eller; sant om endera sidan är sann|(1 – EQ 1)-eller (1-EQ 2)|
|– inte|Logiskt not; ångrar sant och falskt|– inte (1 – EQ 2)|
|\!|Logiskt not; ångrar sant och falskt|\!(1 – EQ 2)|
