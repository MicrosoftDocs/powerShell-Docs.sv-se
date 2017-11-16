---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Direkt manipulering av objekt
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: d9aa95dcb0da2e8203cbe32d64b95bf33d914166
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="manipulating-items-directly"></a>Direkt manipulering av objekt
Element som du ser i Windows PowerShell-enheter, till exempel filer och mappar i systemenheter filer och registernycklar i Windows PowerShell registret enheter, kallas *objekt* i Windows PowerShell. Cmdlets för att arbeta med dessa objekt har substantivet **objektet** i sina namn.

Utdata från den **Get-Command - objektet substantiv** kommando visar att det finns nio Windows PowerShell-cmdletar för objektet.

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

### <a name="creating-new-items-new-item"></a>Skapa nya objekt (nytt objekt)
Använd för att skapa ett nytt objekt i filsystemet i **nytt objekt** cmdlet. Inkludera den **sökväg** parameter med sökvägen till objektet och **ItemType** parametern med värdet ”fil” eller ”directory”.

Till exempel vill skapa en ny katalog med namnet ”New.Directory"in enhet C:\\Temp-katalog, typ:

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

Om du vill skapa en fil, ändrar du värdet för den **ItemType** parameter för ”fil”. Till exempel för att skapa en fil med namnet ”file1.txt” i katalogen New.Directory, skriver du:

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

Du kan använda samma metod för att skapa en ny registernyckel. Faktum är är en registernyckel enklare att skapa eftersom endast objekttypen i Windows-registret är en nyckel. (Registerposterna är objektet *egenskaper*.) Till exempel för att skapa en nyckel med namnet ”_Test” i undernyckeln CurrentVersion, skriver du:

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

När du skriver en registersökväg Glöm kolon (**:**) i Windows PowerShell enhet namn, HKLM: och HKCU:. Utan kolon, kan Windows PowerShell inte identifiera enhetsnamnet i sökvägen.

### <a name="why-registry-values-are-not-items"></a>Varför registervärden inte är element
När du använder den **Get-ChildItem** för att hitta objekt i en registernyckel visas aldrig faktiska registerposter eller deras värden.

Till exempel registernyckeln **HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion\\kör** innehåller vanligtvis flera registerposter som representerar program som körs när systemet startar.

Men om du använder **Get-ChildItem** för att leta efter underordnade objekt i nyckeln visas bara de **OptionalComponents** undernycklar för nyckeln:

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

Även om det skulle vara praktiskt att behandla registerposter som objekt, kan du inte ange en sökväg till en registerpost på ett sätt som garanterar att den är unik. Sökvägen notation skiljer inte mellan registerundernyckeln med namnet **kör** och **(standard)** registerpost i den **kör** undernyckel. Dessutom eftersom registret postnamnen kan innehålla ett omvänt snedstreck (**\\**), om regsitry poster objekt som du kan inte använda sökväg notation för att särskilja en registerpost med namnet  **Windows\\CurrentVersion\\kör** från undernyckeln som finns i sökvägen.

### <a name="renaming-existing-items-rename-item"></a>Byta namn på befintliga objekt (Byt namn på objekt)
Du kan ändra namnet på en fil eller mapp med det **byta namnet på objektet** cmdlet. Följande kommando ändrar namnet på den **file1.txt** filen till **fileOne.txt**.

```
PS> Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

Den **byta namnet på objektet** cmdlet kan ändra namnet på en fil eller mapp, men det går inte att flytta ett objekt. Kommandot misslyckas eftersom den försöker flytta filen från katalogen New.Directory till Temp-katalogen.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

### <a name="moving-items-move-item"></a>Flytta objekt (flytta objekt)
Flytta en fil eller mapp med det **flytta objekt** cmdlet.

Till exempel följande kommando flyttas katalogen New.Directory från enhet C:\\temp-katalogen i roten på enhet C:. Om du vill kontrollera att objektet har flyttats, innehåller den **PassThru** parameter för den **flytta objekt** cmdlet. Utan **Passthru**, **flytta objekt** cmdleten visas inte några resultat.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

### <a name="copying-items-copy-item"></a>Kopiera objekt (kopiera objekt)
Om du är bekant med copy-åtgärder i andra, kanske beteendet för den **Copy-Item** cmdlet i Windows PowerShell för att vara annorlunda. När du kopierar ett objekt från en plats till en annan, kopierar inte innehållet som standard i Kopiera objekt.

Till exempel om du kopierar den **New.Directory** katalog från enheten C: till C:\\temp-katalog, kommandot lyckas men kopieras inte filerna i katalogen New.Directory.

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp
```

Om du visar innehållet i **C:\\temp\\New.Directory**, hittar du att den inte innehåller några filer:

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

Varför inte den **Copy-Item** cmdlet kopiera innehållet till den nya platsen?

Den **Copy-Item** cmdlet har utformats för att vara generisk och är inte bara för att kopiera filer och mappar. Trots att kopiera filer och mappar, kanske du vill kopiera endast för behållaren och inte objekt i den.

Kopiera hela innehållet i en mapp genom att inkludera den **Recurse** parameter för den **Copy-Item** cmdlet i kommandot. Om du redan har kopierat katalogen utan innehållet kan lägga till den **kraft** parameter, där du kan skriva över den tomma mappen.

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

### <a name="deleting-items-remove-item"></a>Ta bort objekt (ta bort objekt)
Ta bort filer och mappar genom att använda den **ta bort objektet** cmdlet. Windows PowerShell-cmdlets som **ta bort objektet**, som kan göra betydande, ångra ändringar ofta ombeds du att bekräfta när du anger dess kommandon. Till exempel om du försöker ta bort den **New.Directory** mappen, du uppmanas att bekräfta kommandot, eftersom den innehåller filer:

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Eftersom **Ja** är svaret som standard, ta bort mappen och dess filer, tryck på den **RETUR** nyckel. Ta bort mappen utan att bekräfta den **-Recurse** parameter.

```
PS> Remove-Item C:\temp\New.Directory -Recurse
```

### <a name="executing-items-invoke-item"></a>Köra objekt (anropa-objekt)
Windows PowerShell använder den **Invoke-objektet** för att utföra en standardåtgärd för en fil eller mapp. Den här standardåtgärd bestäms av standardprogram för programmet i registret. effekten är densamma som om du dubbelklickar på objektet i Utforskaren.

Anta att du kör följande kommando:

```
PS> Invoke-Item C:\WINDOWS
```

Ett Explorer-fönster som finns i C:\\Windows visas precis som om du hade dubbelklickar på enhet C:\\Windows-mappen.

Om du anropar den **Boot.ini** filen i ett system tidigare än Windows Vista:

```
PS> Invoke-Item C:\boot.ini
```

Om typen ini-filen är associerad med anteckningar öppnas boot.ini-filen i anteckningar.

