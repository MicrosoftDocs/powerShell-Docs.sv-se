---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Omdirigera data med Out-cmdletar
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: 7c601b09cc53524eb55014b8ea19a5d79cb98b0e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086161"
---
# <a name="redirecting-data-with-out--cmdlets"></a>Omdirigera Data med Out-* cmdlet: ar

Windows PowerShell innehåller flera cmdletar som låter dig styra data utdata direkt. Dessa cmdletar har två viktiga egenskaper.

Först måste omvandla de vanligtvis data till någon form av text. De göra det eftersom de mata ut data till systemkomponenter som behöver mata in text. Det innebär att de behöver för att representera objekt som text. Därför formateras texten som syns i Windows PowerShell-konsolfönster.

Sedan dessa cmdletar använder Windows PowerShell-verb **ut** eftersom de skicka information från Windows PowerShell till en annan plats. Den **ut värd** cmdlet är inget undantag: visningen värden som ligger utanför Windows PowerShell. Detta är viktigt eftersom när data skickas ut från Windows PowerShell, den tas bort. Du kan se om du försöker skapa en pipeline som sidor-data till fönstret värden och försök sedan att formatera den som en lista som visas här:

```powershell
Get-Process | Out-Host -Paging | Format-List
```

Du kan förvänta dig kommandot för att visa sidor i processinformation i listformat. I stället visas listan över tabular:

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

Den **ut värd** cmdleten skickar data direkt till konsolen så **Format-List** kommando får aldrig något ska formateras.

Det korrekta sättet att strukturera det här kommandot är att placera den **ut värd** cmdlet i slutet av pipelinen enligt nedan. Detta leder till processdata ska vara formaterad i en lista innan du kan växlat minne och visas.

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

Detta gäller för alla de **ut** cmdletar. En **ut** cmdlet alltid ska visas i slutet av pipelinen.

> [!NOTE]
> Alla de **ut** cmdletar återges resultatet som text med formateringen gäller för konsolfönstret, inklusive rad längd gränser.

## <a name="paging-console-output-out-host"></a>Växling konsolens utdata (ut värd)

Som standard, Windows PowerShell skickar data till fönstret värd, vilket är exakt vad de ut värd cmdlet gör. Primär användning för den värd ut cmdlet är sidindelning data som har beskrivits tidigare. Till exempel följande kommando använder ut att ha till sidan utdata från Get-Command-cmdlet:

```powershell
Get-Command | Out-Host -Paging
```

Du kan också använda den **mer** att siddata. I Windows PowerShell **mer** är en funktion som anropar **ut värd-växling**. Följande kommando visar hur du använder den **mer** att sidan utdata från Get-kommandot:

```powershell
Get-Command | more
```

Om du anger ett eller flera filnamn som argument till funktionen mer funktionen läser de angivna filerna och sidan innehållet till värden:

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

## <a name="discarding-output-out-null"></a>Tar bort utdata (ut Null)

Den **ut Null** cmdlet har utformats för att omedelbart ta bort några indata som tas emot. Detta är användbart för att ta bort onödiga data som är tillgängliga som en sidoeffekt av som kör ett kommando. När skriver du följande kommando, du får inte något tillbaka från kommandot:

```powershell
Get-Command | Out-Null
```

Den **ut Null** cmdlet tar inte bort utdata om felet. Till exempel om du anger du följande kommando, meddelande ett informerar dig om att Windows PowerShell inte känner igen ”är NotACommand':

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

## <a name="printing-data-out-printer"></a>Data för utskrift (Out-skrivare)

Du kan skriva ut data med hjälp av den **Out-skrivare** cmdlet. Den **Out-skrivare** cmdlet använder standardskrivaren om du inte anger namnet på en skrivare. Du kan använda valfri Windows-baserade skrivare genom att ange dess namn. Det finns inget behov av alla slags skrivare portmappning och även en riktig fysisk skrivare. Om du har Microsoft Office-dokument avbildning verktygen som installeras kan kan du till exempel skicka data till en bildfil genom att skriva:

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

## <a name="saving-data-out-file"></a>Sparar Data (out-File)

Du kan skicka utdata till en fil i stället för konsolfönstret genom att använda den **out-File** cmdlet. Följande kommandorad skickar en lista över processer till filen **C:\\temp\\processlist.txt**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

Resultatet av att använda den **out-File** cmdlet kanske inte vad du förväntar dig om du är van att omdirigering av traditionella utdata. För att förstå dess beteende, måste du vara medveten om kontexten där den **out-File** cmdlet fungerar.

Som standard den **out-File** cmdlet skapar en Unicode-fil. Det här är den bästa standarden på lång sikt, men det innebär att verktyg som räknar ASCII-filer inte fungerar korrekt med format för standardutdata. Du kan ändra format för standardutdata till ASCII med hjälp av den **Encoding** parameter:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-File** format filinnehåll ska se ut som konsolens utdata. Detta leder till utdata till trunkeras precis som i ett konsolfönster i de flesta fall. Exempel: Om du kör följande kommando:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

Utdata ser ut så här:

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

Du kan använda för att få utdata som inte tvingar rad radbryter så att den matchar skärmbredden kan den **bredd** parametern för att ange bredden. Eftersom **bredd** är en 32-bitars heltal-parameter, det högsta värdet som den kan ha är 2147483647. Skriv följande för att ange bredden för den här högsta värdet:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

Den **out-File** cmdlet är mest användbara när du vill spara utdata som det skulle ha visas på konsolen. För mer detaljerad kontroll över utdataformat behöver du mer avancerade verktyg. Vi ska titta på dem i nästa kapitel, tillsammans med viss information om manipulering av objekt.