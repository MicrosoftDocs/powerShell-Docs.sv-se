---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Omdirigera data med Out-cmdletar
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: 3ca7984e831a995e80cbd8a4d83ae9225c2a4f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="redirecting-data-with-out--cmdlets"></a>Omdirigera Data med Out-* Cmdlets

Windows PowerShell innehåller flera cmdlets som låter dig styra data utdata direkt. Dessa cmdletar har två viktiga egenskaper.

Först transformera de vanligtvis data till någon form av text. Det gör de eftersom de utdata för systemkomponenter i som kräver indata från text. Det innebär att de behöver för att representera objekt som text. Texten är därför formaterad som det visas i fönstret Windows PowerShell-konsolen.

Sedan använder dessa cmdlets i Windows PowerShell-verb **ut** eftersom de skicka information från Windows PowerShell till någon annanstans. Den **ut värd** cmdlet är inget undantag: visningen värden som ligger utanför Windows PowerShell. Detta är viktigt eftersom när data skickas utanför Windows PowerShell, den tas bort. Du kan se dessa om du försöker skapa en pipeline sidor data till fönstret värden och försök sedan att formatera som en lista som visas här:

```powershell
Get-Process | Out-Host -Paging | Format-List
```

Du kan förvänta sig kommandot för att visa sidor i processinformation i listformat. I stället visas listan över tabeller som standard:

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

Den **ut värd** cmdlet skickar data direkt till konsolen så **Format-List** kommandot får aldrig något format.

Det korrekta sättet att struktur det här kommandot är att placera den **ut värd** cmdlet i slutet av pipeline enligt nedan. Detta medför processdata ska formateras i en lista före som växlingsbart och visas.

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

Detta gäller för alla de **ut** cmdlets. En **ut** cmdlet alltid ska visas i slutet av pipeline.

> [!NOTE]
> Alla de **ut** cmdlets återge resultatet som text med den formatering som tillämpas för konsolfönstret, inklusive rad längd gränser.

#### <a name="paging-console-output-out-host"></a>Växling konsolens utdata (routningsserver värd)

Som standard, Windows PowerShell skickar data till fönstret värden som är exakt vad den ut värd för cmdlet har. Primär användning för den inkommande värd cmdlet är sidindelning data som har beskrivits tidigare. Till exempel värdar följande kommando använder ut till sidan utdata från cmdleten Get-Command:

```powershell
Get-Command | Out-Host -Paging
```

Du kan också använda den **mer** siddata av funktionen. I Windows PowerShell **mer** är en funktion som anropar **ut värd-växling**. Följande kommando visas hur du använder den **mer** funktion på sidan Get-kommandot:

```powershell
Get-Command | more
```

Om du inkluderar ett eller flera filnamn som argument till funktionen mer funktionen läsa de angivna filerna och sidan innehållet till värden:

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a>Ignorera utdata (routningsserver Null)

Den **ut Null** cmdlet är utformat för att direkt ta bort alla indata som tas emot. Detta är användbart för att ta bort onödiga data som är tillgängliga som en sidoeffekt av ett kommando körs. När skriver du följande kommando, du får inte något tillbaka från kommandot:

```powreshell
Get-Command | Out-Null
```

Den **ut Null** cmdlet tar inte bort Felutdata. Till exempel om du anger följande kommando, visas ett meddelande informerar dig om att Windows PowerShell inte känner igen 'Är NotACommand':

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a>Data för utskrift (Out-skrivare)

Du kan skriva ut data med hjälp av den **Out-skrivare** cmdlet. Den **Out-skrivare** cmdlet använder standardskrivaren om du inte anger namnet på en skrivare. Du kan använda alla Windows-baserade skrivare genom att ange dess namn. Det behövs ingen för alla typer av skrivare portmappning eller även verkliga fysiska skrivare. Om du har Microsoft Office-dokument avbildning verktygen som installeras kan kan du till exempel skicka data till en bildfil genom att skriva:

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a>Spara Data (out-File)

Du kan skicka utdata till en fil i stället för konsolfönstret med hjälp av den **out-File** cmdlet. Följande kommandorad skickar en lista över processer till filen **C:\\temp\\processlist.txt**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

Resultatet av att använda den **out-File** cmdlet kanske inte som du förväntar dig om du för omdirigering av traditionella utdata. För att förstå sitt beteende, måste du vara medveten om kontexten där den **out-File** cmdlet fungerar.

Som standard den **out-File** cmdlet skapar en Unicode-fil. Detta är den bästa standardvärdet på lång sikt, men innebär det att verktyg som ASCII-filer ska fungera korrekt med standardformatet för utdata. Du kan ändra standardformatet för utdata till ASCII med hjälp av den **kodning** parameter:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-File** format filinnehåll ska se ut som konsolens utdata. Detta leder till utdata till trunkeras precis som i ett konsolfönster i de flesta fall. Till exempel om du kör följande kommando:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

Resultatet ser ut så här:

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

Du kan använda för att hämta utdata som inte tvingar rad radbryter att matcha skärmbredden på **bredd** parametern för att ange linjebredd. Eftersom **bredd** är en 32-bitars heltal-parameter kan ha maxvärdet är 2147483647. Skriv följande för att ange bredden för den här högsta värdet:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

Den **out-File** cmdlet är användbar när du vill spara utdata som den skulle ha visas på konsolen. Du behöver mer avancerade verktyg får bättre kontroll över utdataformat. Vi ska titta på de i nästa kapitel, tillsammans med information om objektet manipulation.