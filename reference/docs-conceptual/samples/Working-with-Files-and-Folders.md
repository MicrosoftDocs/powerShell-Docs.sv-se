---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Arbeta med filer och mappar
description: Den här artikeln beskriver hur du hanterar vissa åtgärder för att manipulera filer och mappar med hjälp av PowerShell.
ms.openlocfilehash: c0c3abb082b05296daa480ac06bcbfa3a784e0c9
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500036"
---
# <a name="working-with-files-and-folders"></a>Arbeta med filer och mappar

Att navigera genom Windows PowerShell-enheter och ändra objekten på dem liknar att manipulera filer och mappar på fysiska Windows-diskar. Den här artikeln beskriver hur du hanterar vissa åtgärder för att manipulera filer och mappar med hjälp av PowerShell.

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>Visar alla filer och mappar i en mapp

Du kan hämta alla objekt direkt i en mapp med hjälp av `Get-ChildItem` . Lägg till den valfria **Force** -parametern om du vill visa dolda eller system objekt. Detta kommando visar till exempel direkt innehållet i Windows PowerShell-enhet C (som är samma som den fysiska Windows-enheten C):

```powershell
Get-ChildItem -Path C:\ -Force
```

Kommandot visar bara de objekt som finns direkt, ungefär som att `Cmd.exe` använda `DIR` kommandot eller `ls` i ett UNIX-gränssnitt. För att kunna visa de objekt som finns måste du även ange `-Recurse` parametern. (Det kan ta mycket lång tid att slutföra.) Så här visar du allt på C-enheten:

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

`Get-ChildItem` kan filtrera objekt med dess **sökväg**, **filtrera**, **Inkludera**och **exkludera** parametrar, men de är vanligt vis endast baserade på namn. Du kan utföra komplex filtrering baserat på andra egenskaper för objekt med hjälp av `Where-Object` .

Följande kommando hittar alla körbara filer i mappen program som senast ändrades efter den 1 oktober 2005 och som inte är mindre än 1 MB eller större än 10 megabyte:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>Kopiera filer och mappar

Kopieringen görs med `Copy-Item` . Följande kommando säkerhetskopierar C: \\boot.ini till c: \\ Boot. bak:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Om målfilen redan finns, Miss lyckas kopierings försöket. Om du vill skriva över ett redan befintligt mål använder du parametern **Force** :

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

Kommandot fungerar även om målet är skrivskyddat.

Kopiering av mappar fungerar på samma sätt. Det här kommandot kopierar mappen `C:\temp\test1` till den nya mappen `C:\temp\DeleteMe` rekursivt:

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

Du kan också kopiera ett urval av objekt. Följande kommando kopierar alla. txt-filer som finns var som helst i `C:\data` till `C:\temp\text` :

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

Du kan fortfarande använda andra verktyg för att utföra fil system kopior. XCOPY-, ROBOCOPY-och COM-objekt, till exempel **Scripting. FileSystemObject,** allt arbete i Windows PowerShell. Du kan till exempel använda Windows Script Host **Scripting. filesystem COM-** klassen för att säkerhetskopiera `C:\boot.ini` till `C:\boot.bak` :

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>Skapa filer och mappar

Att skapa nya objekt fungerar likadant på alla Windows PowerShell-leverantörer. Om en Windows PowerShell-provider har fler än en typ av objekt, till exempel Windows PowerShell-providern för fil systemet skiljer sig mellan kataloger och filer, måste du ange objekt typen.

Det här kommandot skapar en ny mapp `C:\temp\New Folder` :

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

Det här kommandot skapar en ny tom fil `C:\temp\New Folder\file.txt`

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

> [!IMPORTANT]
> När du använder **Force** -växeln med `New-Item` kommandot för att skapa en mapp, och mappen redan finns, _kommer den inte_ att skriva över eller ersätta mappen. Det kommer bara att returnera det befintliga objektet Folder. Men om du använder `New-Item -Force` på en fil som redan finns _kommer_ filen att skrivas över helt.

## <a name="removing-all-files-and-folders-within-a-folder"></a>Ta bort alla filer och mappar i en mapp

Du kan ta bort de objekt som finns i `Remove-Item` , men du uppmanas att bekräfta borttagningen om objektet innehåller något annat. Om du till exempel försöker ta bort mappen `C:\temp\DeleteMe` som innehåller andra objekt, uppmanas du i Windows PowerShell att bekräfta innan du tar bort mappen:

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the Recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Om du inte vill bli tillfrågad om varje objekt som ingår, anger du parametern **rekursivt** :

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a>Mappa en lokal mapp som en enhet

Du kan också mappa en lokal mapp med hjälp av `New-PSDrive` kommandot. Följande kommando skapar en lokal enhet `P:` som är rotad i katalogen lokala program filer, som endast visas från PowerShell-sessionen:

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

Precis som med nätverks enheter är enheter som mappas i Windows PowerShell direkt synliga för Windows PowerShell-gränssnittet. För att kunna skapa en mappad enhet som visas i Utforskaren, `-Persist` krävs parametern. Dock kan endast fjärrsökvägar användas med persist.

## <a name="reading-a-text-file-into-an-array"></a>Läsa en textfil i en matris

Ett av de vanligaste lagrings formaten för text data finns i en fil med separata rader som behandlas som distinkta data element. `Get-Content`Cmdleten kan användas för att läsa en hel fil i ett enda steg, som du ser här:

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

`Get-Content` behandlar redan data som läses från filen som en matris, med ett element per rad med fil innehåll. Du kan bekräfta detta genom att kontrol lera **längden** på det returnerade innehållet:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Det här kommandot är mest användbart för att hämta listor med information till Windows PowerShell direkt. Du kan till exempel lagra en lista med dator namn eller IP-adresser i en fil `C:\temp\domainMembers.txt` med ett namn på varje rad i filen. Du kan använda `Get-Content` för att hämta fil innehållet och infoga dem i variabeln `$Computers` :

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

`$Computers` är nu en matris som innehåller ett dator namn i varje element.
