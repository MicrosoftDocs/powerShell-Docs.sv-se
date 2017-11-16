---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Arbeta med filer och mappar
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 73773df9f018c396c9c4237a40f2e9d2c841464e
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-files-and-folders"></a>Arbeta med filer och mappar
Navigera i Windows PowerShell-enheter och manipulera objekten på dem liknar manipulera filer och mappar på Windows fysiska hårddiskar. Vi upp hur du arbetar med specifika fil- och manipulation uppgifter i det här avsnittet.

### <a name="listing-all-the-files-and-folders-within-a-folder"></a>Visar en lista över alla filer och mappar i en mapp
Du kan hämta alla objekt direkt i en mapp med hjälp av **Get-ChildItem**. Lägga till valfria **kraft** parametern för att visa dolda eller system-objekt. Detta kommando visar till exempel direkt innehållet i Windows PowerShell-enhet C (vilket är samma som den fysiska Windows-enheten C):

```
Get-ChildItem -Force C:\
```

Kommandot visas endast de direkt objekten, ungefär som använder Cmd.exe's **DIR** kommando eller **ls** i ett UNIX-gränssnitt. För att kunna visa objekten, måste du ange den **-Recurse** samt parametern. (Detta kan ta en mycket lång tid att slutföra.) Att visa allt på enhet C:

```
Get-ChildItem -Force C:\ -Recurse
```

**Get-ChildItem** kan filtrera objekt med dess **sökväg**, **Filter**, **inkludera**, och **undanta** parametrar, men de Vanligtvis baseras endast på namn. Du kan utföra komplexa filtrering baserat på andra egenskaper för objekt med hjälp av **Where-Object**.

Följande kommando söker efter alla körbara filer i mappen Program som senast ändrades efter den 1 oktober 2005 och som varken är mindre än 1 megabyte eller större än 10 MB:

```
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt "2005-10-01") -and ($_.Length -ge 1m) -and ($_.Length -le 10m)}
```

### <a name="copying-files-and-folders"></a>Kopiera filer och mappar
Kopieringen är klar med **Copy-Item**. Följande kommando säkerhetskopierar C:\\boot.ini till C:\\boot.bak:

```
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak
```

Kopiera försöket misslyckas om filen redan finns. Använd Force-parametern om du vill ersätta en befintlig plats:

```
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak -Force
```

Det här kommandot fungerar även när målet är skrivskyddat.

Kopiera mappen fungerar på samma sätt. Det här kommandot kopieras mappen C:\\temp\\test1 till den nya mappen c:\\temp\\DeleteMe rekursivt:

```
Copy-Item C:\temp\test1 -Recurse c:\temp\DeleteMe
```

Du kan också kopiera ett urval av objekt. I följande kopieras alla txt-filer som finns någonstans i c:\\data till c:\\temp\\text:

```
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination c:\temp\text
```

Du kan fortfarande använda andra verktyg för att kopiera system. XCOPY ROBOCOPY och COM-objekt, som den **Scripting.FileSystemObject,** alla fungerar i Windows PowerShell. Du kan till exempel använda Windows Script Host **Scripting.FileSystem COM** klassen för att säkerhetskopiera C:\\boot.ini till C:\\boot.bak:

```
(New-Object -ComObject Scripting.FileSystemObject).CopyFile("c:\boot.ini", "c:\boot.bak")
```

### <a name="creating-files-and-folders"></a>Skapa filer och mappar
Skapa nya objekt fungerar på samma på alla Windows PowerShell-leverantörer. Om en Windows PowerShell-provider har mer än en typ av objekt, till exempel filsystem Windows PowerShell-providern skiljer mellan kataloger och filer, måste du ange vilken typ av objekt.

Det här kommandot skapar en ny mapp C:\\temp\\ny mapp:

```
New-Item -Path 'C:\temp\New Folder' -ItemType "directory"
```

Det här kommandot skapar en ny tom fil C:\\temp\\ny mapp\\fil.txt

```
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType "file"
```

### <a name="removing-all-files-and-folders-within-a-folder"></a>Ta bort alla filer och mappar i en mapp
Du kan ta bort ingående objekt med hjälp av **ta bort objektet**, men du uppmanas att bekräfta borttagningen om artikeln innehåller någonting annat. Till exempel om du försöker ta bort mappen C:\\temp\\DeleteMe som innehåller andra objekt, Windows PowerShell uppmanar dig att bekräfta innan du tar bort mappen:

```
Remove-Item C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Ange om du inte vill uppmanas att varje objekt som innesluts i **Recurse** parameter:

```
Remove-Item C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>Mappning av en lokal mapp som en tillgänglig enhet för Windows
Du kan också mappa en lokal mapp med hjälp av den **subst** kommando. Följande kommando skapar en lokal enhet P: rotad i den lokala katalogen Program:

```
subst p: $env:programfiles
```

Precis som med nätverksenheter, mappade enheter i Windows PowerShell med **subst** visas direkt för Windows PowerShell-gränssnittet.

### <a name="reading-a-text-file-into-an-array"></a>Läser en textfil i en Array
En av de vanligaste storage format för textdata är i en fil med separata rader behandlas som distinkta dataelement. Den **Get-innehåll** cmdlet kan användas för att läsa en hel fil i ett steg som visas här:

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional 
with Data Execution Prevention" /noexecute=optin /fastdetect
```

**Get-innehåll** redan behandlar data läses från filen som en matris med ett element per rad på filinnehåll. Du kan kontrollera detta genom att kontrollera den **längd** returnerade innehåll:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Det här kommandot är mest användbart för att hämta en lista över information i Windows PowerShell direkt. Du kan till exempel lagra en lista över datornamn eller IP-adresser i en fil C:\\temp\\domainMembers.txt med ett namn på varje rad i filen. Du kan använda **Get-innehåll** att hämta filens innehåll och placera dem i variabeln **$Computers**:

```
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** är nu en matris som innehåller ett datornamn i varje element.

