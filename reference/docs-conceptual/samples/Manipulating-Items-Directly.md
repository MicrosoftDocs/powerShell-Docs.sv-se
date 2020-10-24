---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Manipulera objekt direkt
description: PowerShell innehåller flera cmdlets som hjälper dig att hantera objekt på lokala och fjärranslutna datorer. Objekt är objekt som exponeras av PowerShell-leverantörer som fil system, register, certifikat och andra.
ms.openlocfilehash: 20132b63a8ff4ef24b1d8346066315dbb053e59c
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500325"
---
# <a name="manipulating-items-directly"></a>Manipulera objekt direkt

De element som visas i Windows PowerShell-enheter, till exempel filerna och mapparna i fil system enheterna och register nycklarna i Windows PowerShell-registernycklarna, kallas *objekt* i Windows PowerShell. Cmdletarna för att arbeta med dem har **elementet Substantiv i** sina namn.

Utdata från kommandot **Get-Command-Substantiv objekt** visar att det finns nio objekt-cmdletar för Windows PowerShell.

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

## <a name="creating-new-items-new-item"></a>Skapa nya objekt (nytt objekt)

Om du vill skapa ett nytt objekt i fil systemet använder du cmdleten **New-item** . Inkludera parametern **Path** med sökvägen till objektet och parametern **itemType** med värdet "File" eller "Directory".

Om du till exempel vill skapa en ny katalog med namnet "New. Directory" i katalogen C: \\ temp, skriver du:

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

Om du vill skapa en fil ändrar du värdet för parametern **itemType** till "File". Om du till exempel vill skapa en fil med namnet "file1.txt" i katalogen New. Directory skriver du:

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

Du kan använda samma metod för att skapa en ny register nyckel. I själva verket är det enklare att skapa en register nyckel eftersom den enda objekt typen i Windows-registret är en nyckel. (Register poster är objekt *Egenskaper*.) Om du till exempel vill skapa en nyckel med namnet "_Test" i CurrentVersion-undernyckeln, skriver du:

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

När du skriver en register Sök väg ska du se till att inkludera kolon (**:**) i Windows PowerShell-enhetens namn, HKLM: och HKCU:. Utan kolonet känner Windows PowerShell inte igen enhets namnet i sökvägen.

## <a name="why-registry-values-are-not-items"></a>Varför register värden inte är objekt

När du använder cmdleten **Get-ChildItem** för att hitta objekten i en register nyckel, ser du aldrig faktiska register poster eller deras värden.

Till exempel innehåller register nyckeln **HKEY_LOCAL_MACHINE \\ Software \\ Microsoft \\ Windows CurrentVersion- \\ \\ körningen** vanligt vis flera register poster som representerar program som körs när systemet startar.

Men när du använder **Get-ChildItem** för att leta efter underordnade objekt i nyckeln ser du att det finns en **OptionalComponents** -under nyckel i nyckeln:

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

Även om det skulle vara praktiskt att behandla register poster som objekt kan du inte ange en sökväg till en register post på ett sätt som garanterar att det är unikt. Sök vägs notationen skiljer sig inte mellan register under nyckeln med namnet **Run** och register posten **(default)** i **körnings** under nyckeln. Dessutom, eftersom register post namn kan innehålla omvänt snedstreck ( **\\** ), om register poster var objekt, kunde du inte använda Sök vägs notation för att skilja en register post med namnet **Windows \\ CurrentVersion att \\ köras** från under nyckeln som finns i den sökvägen.

## <a name="renaming-existing-items-rename-item"></a>Byta namn på befintliga objekt (Byt namn på objekt)

Om du vill ändra namnet på en fil eller mapp använder du cmdleten **rename-item** . Följande kommando ändrar namnet på den **file1.txt** -fil som ska **fileOne.txt**.

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

Cmdleten **rename-item** kan ändra namnet på en fil eller mapp, men det går inte att flytta ett objekt. Följande kommando Miss lyckas eftersom det försöker flytta filen från den nya katalog katalogen till Temp-katalogen.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a>Flytta objekt (flytta objekt)

Om du vill flytta en fil eller mapp använder du cmdleten **Move-item** .

Följande kommando flyttar till exempel den nya katalog katalogen från katalogen C: \\ Temp till roten på enheten c:. För att verifiera att objektet har flyttats inkluderar du parametern **Passthru** i cmdleten **Move-item** . Utan **Passthru**visar cmdleten **Move-item** inga resultat.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a>Kopiera objekt (kopiera objekt)

Om du är bekant med kopierings åtgärderna i andra gränssnitt kan du vara ovanlig om du märker att cmdleten **copy-item** i Windows PowerShell fungerar som den ska. När du kopierar ett objekt från en plats till en annan kopierar Copy-Item inte innehållet som standard.

Om du till exempel kopierar den **nya katalog** katalogen från c:-enheten till katalogen c: \\ temp, lyckas kommandot, men filerna i katalogen New. Directory kopieras inte.

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

Om du visar innehållet i **C: \\ Temp \\ New. Directory**, kommer du att se att den inte innehåller några filer:

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

Varför kopierar inte cmdleten **copy-item** innehållet till den nya platsen?

Cmdleten **copy-item** har utformats för att vara generisk; Det är inte bara att kopiera filer och mappar. Även när du kopierar filer och mappar kanske du vill kopiera endast behållaren och inte objekten i den.

Om du vill kopiera hela innehållet i en mapp inkluderar du parametern **rekursivt** i cmdleten **copy-item** i kommandot. Om du redan har kopierat katalogen utan innehållet lägger du till parametern **Force** , så att du kan skriva över den tomma mappen.

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

## <a name="deleting-items-remove-item"></a>Ta bort objekt (Remove-item)

Använd cmdleten **Remove-item** om du vill ta bort filer och mappar. Windows PowerShell-cmdletar, t. ex. **Remove-item**, som kan göra betydande, bestående ändringar kommer ofta att uppmanas att bekräfta när du anger dess kommandon. Om du till exempel försöker ta bort den **nya.** mappen, uppmanas du att bekräfta kommandot, eftersom mappen innehåller filer:

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Eftersom **Ja** är standard svaret tar du bort mappen och dess filer genom att trycka på **RETUR** . Om du vill ta bort mappen utan att bekräfta, använder du parametern **-rekursivt** .

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a>Köra objekt (Invoke-item)

Windows PowerShell använder cmdleten **Invoke-item** för att utföra en standard åtgärd för en fil eller mapp. Den här standard åtgärden bestäms av standard program hanteraren i registret. Resultatet är detsamma som om du dubbelklickar på objektet i Utforskaren.

Anta till exempel att du kör följande kommando:

```powershell
Invoke-Item C:\WINDOWS
```

Ett Explorer-fönster som finns i C: \\ Windows visas, precis som om du hade dubbelklickat på mappen C: \\ Windows.

Om du anropar **Boot.ini** -filen på ett system före Windows Vista:

```powershell
Invoke-Item C:\boot.ini
```

Om fil typen. ini är associerad med anteckningar öppnas boot.ini-filen i anteckningar.
