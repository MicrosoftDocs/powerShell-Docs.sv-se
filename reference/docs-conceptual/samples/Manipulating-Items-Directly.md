---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Manipulera objekt direkt
ms.openlocfilehash: 50aed569cf6b876297abe3cf1544eba70f6279ce
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030123"
---
# <a name="manipulating-items-directly"></a>Manipulera objekt direkt

De element som du ser i Windows PowerShell-enheter, till exempel filer och mappar i filen systemenheter och registernycklar i Windows PowerShell registret enheter, kallas *objekt* i Windows PowerShell. Cmdletar för att arbeta med dem objekt har substantivet **objekt** i sina namn.

Utdata från den **Get-Command - substantiv objekt** kommandot visar att det finns nio artikel-cmdletar för Windows PowerShell.

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

## <a name="creating-new-items-new-item"></a>Skapa nya objekt (nya objekt)

Om du vill skapa ett nytt objekt i filsystemet, Använd den **New-Item** cmdlet. Inkludera den **sökväg** parameter med sökvägen till objektet och **ItemType** parametern med värdet ”fil” eller ”directory”.

Till exempel vill skapa en ny katalog med namnet ”New.Directory"in enhet C:\\Temp-katalog, skriver du in:

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

Skapa en fil genom att ändra värdet för den **ItemType** parameter ”fil”. Till exempel för att skapa en fil med namnet ”file1.txt” i katalogen New.Directory, skriver du:

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

Du kan använda samma metod för att skapa en ny registernyckel. I själva verket är det enklare att skapa eftersom endast objekttypen i Windows-registret är en nyckel med en registernyckel. (Registerposter är objektet *egenskaper*.) Till exempel för att skapa en nyckel med namnet ”_testa” i undernyckeln CurrentVersion, skriver du:

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

När du skriver en registersökväg, måste du använda kolumnen ( **:** ) i Windows PowerShell enhet namn, HKLM: och HKCU:. Utan kolumnen identifieras Windows PowerShell inte enhetsbeteckning i sökvägen.

## <a name="why-registry-values-are-not-items"></a>Varför registervärden finns inga objekt

När du använder den **Get-ChildItem** cmdlet för att hitta objekt i en registernyckel visas aldrig faktiska registerposterna eller deras värden.

Till exempel registernyckeln **HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion\\kör** innehåller vanligtvis flera registerposter som representerar program som körs när datorn startas.

Men när du använder **Get-ChildItem** för att leta efter underordnade objekt i nyckeln, visas bara den **OptionalComponents** undernycklar för nyckeln:

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

Även om det skulle vara praktiskt att behandla registerposter som objekt, kan du inte ange en sökväg till en registerpost på ett sätt som säkerställer att det blir unikt. Sökvägen notation skiljer inte mellan registerundernyckeln med namnet **kör** och **(standard)** registerposten i den **kör** undernyckel. Dessutom eftersom registernamn posten kan innehålla ett omvänt snedstreck ( **\\** ), om registerposter objekt, så du inte kan använda beteckningen sökväg att skilja mellan en registerpost med namnet  **Windows\\CurrentVersion\\kör** från undernyckeln som finns i sökvägen.

## <a name="renaming-existing-items-rename-item"></a>Byta namn på befintliga objekt (Byt namn på objekt)

Du kan ändra namnet på en fil eller mapp med det **Rename-Item** cmdlet. Följande kommando byter namn på den **file1.txt** filen till **fileOne.txt**.

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

Den **Rename-Item** cmdlet kan ändra namnet på en fil eller mapp, men det går inte att flytta ett objekt. Följande kommando misslyckas eftersom den försöker flytta filen från katalogen New.Directory till Temp-katalog.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a>Flytta objekt (flytta objekt)

Om du vill flytta en fil eller mapp, använda den **flytta objekt** cmdlet.

Till exempel följande kommando flyttas katalogen New.Directory från enhet C:\\temp-katalogen i roten på enhet C:. Om du vill kontrollera att objektet har flyttats, innehåller den **PassThru** -parametern för den **flytta objekt** cmdlet. Utan **Passthru**, **flytta objekt** cmdlet visar inte några resultat.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a>Kopiera objekt (Copy-Item)

Om du är bekant med kopieringsåtgärder i andra gränssnitt, kanske du upptäcker beteendet för den **Copy-Item** cmdlet i Windows PowerShell är ovanliga. När du kopierar ett objekt från en plats till en annan, kopierar inte Copy-Item innehållet som standard.

Exempel: Om du kopierar den **New.Directory** katalogen från C:-enheten till enhet C:\\temp-katalog, kommandot lyckas men kopieras inte filerna i katalogen New.Directory.

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

Om du visar innehållet i **C:\\temp\\New.Directory**, hittar du att den innehåller inga filer:

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

Varför inte den **Copy-Item** cmdlet kopiera innehållet till den nya platsen?

Den **Copy-Item** cmdlet har utformats för att vara Allmänt, och inte bara för att kopiera filer och mappar. Även om kopiering av filer och mappar, kanske du vill kopiera endast för behållaren och inte objekt i den.

Kopiera hela innehållet i en mapp genom att inkludera den **Recurse** -parametern för den **Copy-Item** cmdlet i kommandot. Om du redan har kopierat katalogen utan dess innehåll kan du lägga till den **kraft** parametern, som du kan skriva över den tomma mappen.

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

## <a name="deleting-items-remove-item"></a>Ta bort objekt (ta bort objekt)

Ta bort filer och mappar genom att använda den **Remove-Item** cmdlet. Windows PowerShell-cmdletar, till exempel **Remove-Item**, som kan göra betydande, går inte att ångra ändringar ofta efterfrågar bekräftelse när du anger kommandona. Exempel: Om du försöker ta bort den **New.Directory** mappen du uppmanas att bekräfta kommandot, eftersom mappen innehåller filer:

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Eftersom **Ja** är Standardsvar att ta bort mappen och dess filer, tryck på den **RETUR** nyckel. Ta bort mappen utan att bekräfta att använda den **-Recurse** parametern.

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a>Körning av objekt (anropa-objekt)

Windows PowerShell använder den **Invoke-Item** cmdlet för att utföra en standardåtgärd för en fil eller mapp. Den här standardåtgärd bestäms av Programhanteraren standard i registret. effekten är samma som om du dubbelklickar på objektet i Utforskaren.

Anta exempelvis att du kör följande kommando:

```powershell
Invoke-Item C:\WINDOWS
```

Ett Explorer-fönster som finns i C:\\Windows visas, precis som om du hade dubbelklickade på enhet C:\\Windows-mappen.

Om du anropar den **Boot.ini** filen i ett system innan Windows Vista:

```powershell
Invoke-Item C:\boot.ini
```

Om typen ini-filen är associerad med anteckningar, öppnas boot.ini-filen i anteckningar.
