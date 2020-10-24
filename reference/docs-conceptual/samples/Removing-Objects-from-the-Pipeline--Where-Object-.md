---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Ta bort objekt från pipelinen där objektet
description: Med Where-Object cmdlet kan du filtrera objekt som skickas i pipelinen.
ms.openlocfilehash: e744dc671303711f1cbe8cc724a97c3327c1da85
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500121"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Ta bort objekt från pipelinen (Where-Object)

I PowerShell genererar och passerar du ofta fler objekt till en pipeline än du vill. Du kan ange egenskaperna för specifika objekt som ska visas med hjälp av `Format-*` cmdletarna, men det hjälper inte att ta bort hela objekt från skärmen. Du kanske vill filtrera objekt före slutet av en pipeline, så att du kan utföra åtgärder på endast en delmängd av de ursprungligen genererade objekten.

PowerShell innehåller en `Where-Object` cmdlet som gör att du kan testa varje objekt i pipelinen och bara skicka det längs pipelinen om det uppfyller ett visst test villkor. Objekt som inte klarar testet tas bort från pipelinen. Du anger test villkoret som värdet för parametern **FilterScript** .

## <a name="performing-simple-tests-with-where-object"></a>Utföra enkla tester med Where-Object

Värdet för **FilterScript** är ett *skript block* – ett eller flera PowerShell-kommandon som omges av klammerparenteser ( `{}` ) – som utvärderas till true eller false. Dessa skript block kan vara väldigt enkla, men att skapa dem kräver att du känner till ett annat PowerShell-begrepp, jämförelse operatorer. En jämförelse operator jämför objekten som visas på varje sida av den. Jämförelse operatorer börjar med ett bindestreck ( `-` ) och följs av ett namn. Grundläggande jämförelse operatorer fungerar på nästan alla typer av objekt. De mer avancerade jämförelse operatörerna kanske bara arbetar med text eller matriser.

> [!NOTE]
> När du arbetar med text är PowerShell-jämförelsen som standard Skift läges okänslig.

På grund av tolknings överväganden används symboler som `<` , `>` och `=` inte som jämförelse operatorer. Jämförelse operatorer består i stället av bokstäver. De grundläggande jämförelse operatorerna visas i följande tabell.

| Jämförelseoperator |                  Innebörd                   |    Exempel (returnerar true)    |
| ------------------- | ------------------------------------------ | ---------------------------- |
| -EQ                 | är lika med                                | 1 – EQ 1                      |
| -Ne                 | Är inte lika med                            | 1 – Ne 2                      |
| -lt                 | Är mindre än                               | 1 – lt 2                      |
| -Le                 | Är mindre än eller lika med                   | 1 – Le 2                      |
| -gt                 | Är större än                            | 2 – gt 1                      |
| -ge                 | Är större än eller lika med                | 2-ge 1                      |
| – som               | Liknar (jämförelse av jokertecken för text)     | "file.doc" – som "f *. gör?"    |
| -notlike            | Liknar inte (jämförelse av jokertecken för text) | "file.doc"-notlike "p*. doc" |
| – innehåller           | Innehåller                                   | 1, 2, 3 – innehåller 1            |
| -notcontains        | Innehåller inte                           | 1, 2, 3-notcontains 4         |

`Where-Object` skript block använder den särskilda variabeln `$_` för att referera till det aktuella objektet i pipelinen. Här är ett exempel på hur det fungerar. Om du har en lista med tal och bara vill returnera de som är mindre än 3 kan du använda `Where-Object` för att filtrera talen genom att skriva:

```
1,2,3,4 | Where-Object {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a>Filtrering baserat på objekt egenskaper

Eftersom `$_` refererar till det aktuella pipeline-objektet kan vi komma åt dess egenskaper för våra tester.

Vi kan till exempel titta på **Win32_SystemDriver** -klassen i WMI. Det kan finnas hundratals system driv rutiner i ett visst system, men du kanske bara är intresse rad av en viss uppsättning system driv rutiner, till exempel de som för närvarande körs. För den **Win32_SystemDriver** klassen är relevant egenskap är **State**. Du kan filtrera system driv rutinerna, välja enbart de som körs genom att skriva:

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq 'Running'}
```

Detta skapar fortfarande en lång lista. Du kanske vill filtrera för att endast välja de driv rutiner som ska starta automatiskt genom att testa **Start mode** -värdet också:

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Auto"}
```

```Output
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
...
```

Detta ger oss mycket information som vi inte längre behöver eftersom vi vet att driv rutinerna körs.
Den enda information som vi förmodligen behöver i det här läget är i själva verket namnet och visnings namnet. Följande kommando innehåller bara de två egenskaperna, vilket resulterar i mycket enklare utdata:

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Manual"} |
      Format-Table -Property Name,DisplayName
```

```Output
Name              DisplayName
----              -----------
AsyncMac               RAS Asynchronous Media Driver
bindflt                Windows Bind Filter Driver
bowser                 Browser
CompositeBus           Composite Bus Enumerator Driver
condrv                 Console Driver
HdAudAddService        Microsoft 1.1 UAA Function Driver for High Definition Audio Service
HDAudBus               Microsoft UAA Bus Driver for High Definition Audio
HidUsb                 Microsoft HID Class Driver
HTTP                   HTTP Service
igfx                   igfx
IntcDAud               Intel(R) Display Audio
intelppm               Intel Processor Driver
...
```

Det finns två `Where-Object` element i ovanstående kommando, men de kan uttryckas i ett enda `Where-Object` element med hjälp av den `-and` logiska operatorn, så här:

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual')} |
    Format-Table -Property Name,DisplayName
```

De logiska standard operatörerna visas i följande tabell.

| Logisk operator |                 Innebörd                  |  Exempel (returnerar true)  |
| ---------------- | ---------------------------------------- | ------------------------ |
| -och             | Logisk och; sant om båda sidorna är sanna | (1 – EQ 1)-och (2-EQ 2) |
| -eller              | Logiskt eller; sant om endera sidan är sann  | (1 – EQ 1)-eller (1-EQ 2)  |
| – inte             | Logiskt not; ångrar sant och falskt     | – inte (1 – EQ 2)           |
| \!               | Logiskt not; ångrar sant och falskt     | \!(1 – EQ 2)              |
