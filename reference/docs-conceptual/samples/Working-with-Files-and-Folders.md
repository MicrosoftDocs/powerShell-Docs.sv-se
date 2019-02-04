---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Arbeta med filer och mappar
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: a8d57a1c269d95e692db6c3f1ae10df49e305e4e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685055"
---
# <a name="working-with-files-and-folders"></a>Arbeta med filer och mappar

Navigera i Windows PowerShell-enheter och manipulera objekt på dem liknar manipulera filer och mappar på Windows fysiska hårddiskar. Det här avsnittet beskrivs hur du arbetar med specifika fil- och manipulering av uppgifter-med hjälp av PowerShell.

### <a name="listing-all-the-files-and-folders-within-a-folder"></a>Visa en lista över alla filer och mappar i en mapp

Du kan hämta alla objekt direkt i en mapp med hjälp av **Get-ChildItem**. Lägg till det valfria **kraft** parameter för att visa dolda eller poster. Det här kommandot visar till exempel direkt innehållet i Windows PowerShell-enhet C (som är samma som den fysiska Windows-enheten C):

```powershell
Get-ChildItem -Path C:\ -Force
```

Kommandot visas endast direkt inneslutna objekten, ungefär som med Cmd.exe's **DIR** kommando eller **ls** i ett UNIX-gränssnitt. Du vill visa objekten, måste du ange den **-Recurse** parametern samt. (Det kan ta en mycket lång tid att slutföra.) Visa en lista över allt på enhet C:

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

**Get-ChildItem** kan filtrera objekt med dess **sökväg**, **Filter**, **inkludera**, och **undanta** parametrar, men de är Vanligtvis baseras endast på namnet. Du kan utföra komplex filtrering baserat på andra egenskaper för objekt med hjälp av **Where-Object**.

Kommandot söker efter alla körbara filer i mappen program som senast ändrades efter den 1 oktober 2005 och som varken är mindre än 1 MB eller större än 10 MB:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

### <a name="copying-files-and-folders"></a>Kopiera filer och mappar

Kopieringen är klar med **Copy-Item**. Följande kommando säkerhetskopierar C:\\boot.ini till C:\\boot.bak:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Kopiera försöket misslyckas om filen redan finns. Om du vill skriva över en befintlig mål, använda den **kraft** parameter:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

Det här kommandot fungerar även när målet är skrivskyddad.

Kopiera mappen fungerar på samma sätt. Det här kommandot kopierar mappen C:\\temp\\test1 till den nya mappen C:\\temp\\DeleteMe rekursivt:

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

Du kan också kopiera ett urval av objekt. I följande kopieras alla txt-filer som finns var som helst i c:\\data till c:\\temp\\text:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

Du kan fortfarande använda andra verktyg för att kopiera system. XCOPY ROBOCOPY och COM-objekt, till exempel den **Scripting.FileSystemObject,** användas i Windows PowerShell. Du kan till exempel använda Windows Script Host **Scripting.FileSystem COM** klassen för att säkerhetskopiera C:\\boot.ini till C:\\boot.bak:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

### <a name="creating-files-and-folders"></a>Skapa filer och mappar

Skapa nya objekt fungerar på samma på alla Windows PowerShell-leverantörer. Om en Windows PowerShell-providern har mer än en typ av objekt, till exempel filsystem Windows PowerShell-providern skiljer mellan kataloger och filer, måste du ange vilken typ av objekt.

Det här kommandot skapar en ny mapp C:\\temp\\ny mapp:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

Det här kommandot skapar en ny tom fil C:\\temp\\ny mapp\\fil.txt

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

### <a name="removing-all-files-and-folders-within-a-folder"></a>Ta bort alla filer och mappar i en mapp

Du kan ta bort ingående objekt med hjälp av **Remove-Item**, men du kommer att uppmanas att bekräfta borttagningen om objektet innehåller något annat. Exempel: Om du försöker ta bort mappen C:\\temp\\DeleteMe som innehåller andra objekt, Windows PowerShell uppmanas du att bekräfta innan du tar bort mappen:

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Om du inte vill uppmanas att varje ingående objekt anger du den **Recurse** parameter:

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>Mappa en lokal mapp som en tillgänglig Windows-enhet

Du kan också mappa en lokal mapp med hjälp av den **subst** kommando. Följande kommando skapar en lokal enhet P: rotad i den lokala katalogen för programfiler:

```powershell
subst p: $env:programfiles
```

Precis som med nätverksenheter, mappade enheter i Windows PowerShell med hjälp av **subst** visas direkt för Windows PowerShell-gränssnittet.

### <a name="reading-a-text-file-into-an-array"></a>Läser en textfil i en matris

En av de vanliga storage format för textdata är i en fil med separata rader behandlas som distinkta dataelement. Den **Get-innehåll** cmdlet kan användas för att läsa en hel fil i ett steg som visas här:

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

**Get-innehåll** redan behandlar data läses från filen som en matris med ett element per rad i filinnehållet. Du kan kontrollera detta genom att markera den **längd** av returnerat innehåll:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Det här kommandot är mest användbara för att hämta en lista över information i Windows PowerShell direkt. Du kan till exempel lagra en lista med datornamn eller IP-adresser i en fil C:\\temp\\domainMembers.txt med ett namn på varje rad i filen. Du kan använda **Get-innehåll** hämtar filinnehållet och placerar dem i variabeln **$Computers**:

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** är nu en matris som innehåller namnet på en dator i varje element.
