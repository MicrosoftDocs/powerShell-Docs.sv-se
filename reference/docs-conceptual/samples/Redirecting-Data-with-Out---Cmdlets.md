---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Omdirigera data med Out-cmdletar
ms.openlocfilehash: d4cc14e26bdef0f973f948177d0c1e68929605fa
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030073"
---
# <a name="redirecting-data-with-out--cmdlets"></a>Omdirigera data med out-*-cmdletar

Windows PowerShell innehåller flera cmdlets som låter dig styra data utdata direkt. Dessa cmdletar delar två viktiga egenskaper.

Först omvandlar de ofta data till någon form av text. De gör detta eftersom de skickar data till system komponenter som kräver text inmatning. Det innebär att de måste representera objekten som text. Därför formateras texten som du ser i fönstret Windows PowerShell-konsol.

För det andra använder dessa cmdlets för Windows PowerShell **-verbet** eftersom de skickar ut information från Windows PowerShell till någon annan stans. Cmdleten **out-Host** är inget undantag: värd fönstrets visning är utanför Windows PowerShell. Detta är viktigt eftersom när data skickas ut från Windows PowerShell tas de faktiskt bort. Du kan se detta om du försöker skapa en pipeline som Page-data till värd fönstret och sedan försöka formatera den som en lista, som du ser här:

```powershell
Get-Process | Out-Host -Paging | Format-List
```

Du kan vänta på att kommandot visar sidor i process information i list format. I stället visas standard tabell listan:

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

Cmdleten **out-Host** skickar data direkt till-konsolen så att kommandot **format-lista** aldrig får något att formatera.

Det korrekta sättet att strukturera det här kommandot är att placera cmdleten **out-Host** i slutet av pipelinen som visas nedan. Detta gör att process data formateras i en lista innan de växlas och visas.

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

Detta gäller för alla **out** -cmdletar. En **out** -cmdlet ska alltid visas i slutet av pipelinen.

> [!NOTE]
> Alla **utgångs** kommandon återger utdata som text med hjälp av formatering som gäller för konsol fönstret, inklusive gränser för linje längd.

## <a name="paging-console-output-out-host"></a>Utdata för växlings konsolen (out-Host)

Som standard skickar Windows PowerShell data till värd fönstret, vilket är exakt vad out-Host-cmdleten gör. Den primära användningen för out-Host-cmdleten är växlings data som vi beskrivit tidigare. Följande kommando använder till exempel out-Host för att visa utdata från cmdleten Get-Command:

```powershell
Get-Command | Out-Host -Paging
```

Du kan också använda funktionen **more** för att ange data på sidan. I Windows **PowerShell är en** funktion som anropar **out-Host-sid indelning**. Följande kommando visar hur du använder funktionen **more** för att visa utdata från Get-Command:

```powershell
Get-Command | more
```

Om du inkluderar ett eller flera fil namn som argument för funktionen More, kommer funktionen att läsa de angivna filerna och sidans innehåll till värden:

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

## <a name="discarding-output-out-null"></a>Tar bort utdata (out-null)

Cmdleten out-null är utformad för att omedelbart ta bort de **inloggade inaktuella inaktuella** . Detta är användbart för att ta bort onödiga data som du får som en sido effekt av att köra ett kommando. När du skriver följande kommando får du inte tillbaka något från kommandot:

```powershell
Get-Command | Out-Null
```

Cmdleten **out-null** ignorerar inte fel utdata. Om du till exempel anger följande kommando visas ett meddelande som talar om att Windows PowerShell inte känner igen "NotACommand":

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

## <a name="printing-data-out-printer"></a>Skriva ut data (ut-skrivare)

Du kan skriva ut data med hjälp av cmdleten **out-Printer** . Cmdleten **out-Printer** använder standard skrivaren om du inte anger något skrivar namn. Du kan använda valfri Windows-baserad skrivare genom att ange dess visnings namn. Det finns inget behov av någon typ av skrivar port mappning eller till och med en riktig fysisk skrivare. Om du till exempel har installerat Microsoft Office Document Imaging Tools kan du skicka data till en bildfil genom att skriva:

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

## <a name="saving-data-out-file"></a>Spara data (Out-File)

Du kan skicka utdata till en fil i stället för konsol fönstret genom att använda cmdleten **Out-File** . Följande kommando rad skickar en lista över processer till filen **C:\\Temp\\processlist. txt**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

Resultatet av att använda cmdleten **Out-File** är kanske inte det du förväntar dig om du använder traditionell omdirigering av utdata. För att förstå dess beteende måste du vara medveten om kontexten där cmdleten **Out-File** fungerar.

Som standard skapar cmdleten **Out-File** en Unicode-fil. Detta är det bästa standardvärdet för lång körning, men det innebär att verktyg som förväntar sig att ASCII-filer inte fungerar korrekt med standardformatet för utdata. Du kan ändra standardformatet för utdata till ASCII med hjälp av parametern **encoding** :

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

Fil innehåll i **fil** format är fil innehåll som ser ut som konsol utdata. Detta gör att utdata trunkeras precis som i ett konsol fönster i de flesta fall. Om du till exempel kör följande kommando:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

Utdata kommer att se ut så här:

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

Om du vill hämta utdata som inte tvingar rad brytningar att matcha skärm bredden kan du använda parametern **width** för att ange linje bredd. Eftersom **width** är en 32-bitars heltals parameter kan det högsta värdet vara 2147483647. Skriv följande för att ställa in linje bredden på det maximala värdet:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

Cmdleten **Out-File** är mest användbar när du vill spara utdata som den skulle ha visat i-konsolen. Du behöver mer avancerade verktyg för bättre kontroll över utdataformatet. Vi ska titta på dem i nästa kapitel, tillsammans med information om objekt manipulation.
