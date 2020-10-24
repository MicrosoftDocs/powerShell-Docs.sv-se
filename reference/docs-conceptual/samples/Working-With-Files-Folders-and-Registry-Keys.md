---
ms.date: 07/28/2020
keywords: powershell,cmdlet
title: Arbeta med filer, mappar och registernycklar
description: Den här artikeln beskriver hur du hanterar aktiviteter för register nyckel hantering med hjälp av PowerShell.
ms.openlocfilehash: 6f653c1fb409a238aa05658e89261a12e96f6fe1
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499985"
---
# <a name="working-with-files-folders-and-registry-keys"></a>Arbeta med filer, mappar och register nycklar

Windows PowerShell använder **objektet** Substantiv för att referera till objekt som finns på en Windows PowerShell-enhet.
När du hanterar Windows PowerShell-filsystem-providern kan ett **objekt** vara en fil, en mapp eller Windows PowerShell-enheten. Att lista och arbeta med dessa objekt är en viktig grundläggande uppgift i de flesta administrativa inställningar, så vi vill diskutera dessa uppgifter i detalj.

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>Räkna upp filer, mappar och register nycklar (Get-ChildItem)

Eftersom hämtning av en samling av objekt från en viss plats är en sådan vanlig uppgift, `Get-ChildItem` är cmdleten utformad för att returnera alla objekt som finns i en behållare, till exempel en mapp.

Om du vill returnera alla filer och mappar som finns direkt i mappen C: \\ Windows skriver du:

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

Listan ser ut ungefär som du ser när du anger `dir` kommandot i **Cmd.exe**eller `ls` kommandot i ett UNIX-kommando gränssnitt.

Du kan utföra mycket komplexa listor genom att använda parametrarna i `Get-ChildItem` cmdleten. Vi kommer att titta på några scenarier härnäst. Du kan se syntaxen för `Get-ChildItem` cmdleten genom att skriva:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Dessa parametrar kan kombineras och matchas för att få mycket anpassade utdata.

### <a name="listing-all-contained-items--recurse"></a>Visar alla objekt som finns (-rekursivt)

Om du vill se både objekten i en Windows-mapp och alla objekt som ingår i undermapparna använder du parametern **rekursivt** i `Get-ChildItem` . I listan visas allting i Windows-mappen och objekten i dess undermappar. Exempel:

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a>Filtrera objekt efter namn (-namn)

Om du bara vill visa objekt namn använder du parametern **Name** för `Get-Childitem` :

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a>Tvångs lista över dolda objekt (-Force)

Objekt som normalt är osynliga i Utforskaren eller Cmd.exe visas inte i utdata från ett `Get-ChildItem` kommando. Om du vill visa dolda objekt använder du **Force** -parametern i `Get-ChildItem` .
Exempel:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Den här parametern heter Force eftersom du kan framtvinga åsidosättning av `Get-ChildItem` kommandots normala beteende. Force är en mycket Använd parameter som tvingar fram en åtgärd som en cmdlet normalt inte utför, även om den inte kommer att utföra någon åtgärd som äventyrar säkerheten i systemet.

### <a name="matching-item-names-with-wildcards"></a>Matchande objekt namn med jokertecken

`Get-ChildItem`Kommandot accepterar jokertecken i sökvägen för objekten som ska listas.

Eftersom matchning av jokertecken hanteras av Windows PowerShell-motorn, använder alla cmdlets som accepterar jokertecken samma notation och har samma matchnings beteende. Jokertecken i Windows PowerShell innehåller:

- Asterisk ( `*` ) matchar noll eller flera förekomster av tecken.

- Frågetecken ( `?` ) matchar exakt ett tecken.

- Vänster hak paren tes tecken `[` och höger hak paren tes tecken ( `]` ) omger en uppsättning tecken som ska matchas.

Här följer några exempel på hur wildcard-specifikation fungerar.

Om du vill hitta alla filer i Windows-katalogen med suffixet `.log` och exakt fem tecken i bas namnet, anger du följande kommando:

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

Om du vill hitta alla filer som börjar med bokstaven `x` i Windows-katalogen skriver du:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Om du vill hitta alla filer vars namn börjar med "x" eller "z", skriver du:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

Mer information om jokertecken finns [about_Wildcards](/powershell/module/microsoft.powershell.core/about/about_wildcards).

### <a name="excluding-items--exclude"></a>Uteslut objekt (-exkludera)

Du kan undanta vissa objekt med hjälp av parametern **exclude** i `Get-ChildItem` . På så sätt kan du utföra komplex filtrering i ett enda uttryck.

Anta till exempel att du försöker hitta Windows Time Service-DLL i mappen **system32** , och allt du kan komma ihåg om dll-namnet är att det börjar med "W" och innehåller "32".

Ett uttryck som visar `w*32*.dll` alla DLL: er som uppfyller villkoren, men du kanske vill filtrera bort filerna ytterligare och utelämna eventuella Win32-filer. Du kan utelämna dessa filer med hjälp av parametern **exclude** med mönstret `win*` :

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude win*

    Directory: C:\WINDOWS\System32

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           3/18/2019  9:43 PM         495616 w32time.dll
-a---           3/18/2019  9:44 PM          35328 w32topl.dll
-a---           1/24/2020  5:44 PM         401920 Wldap32.dll
-a---          10/10/2019  5:40 PM         442704 ws2_32.dll
-a---           3/18/2019  9:44 PM          66048 wsnmp32.dll
-a---           3/18/2019  9:44 PM          18944 wsock32.dll
-a---           3/18/2019  9:44 PM          64792 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a>Blanda Get-ChildItem parametrar

Du kan använda flera av parametrarna i `Get-ChildItem` cmdleten i samma kommando. Innan du blandar parametrar bör du vara säker på att du förstår matchning med jokertecken. Följande kommando returnerar till exempel inga resultat:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Det finns inga resultat, även om det finns två dll: er som börjar med bokstaven "z" i Windows-mappen.

Inga resultat returnerades eftersom vi har angett jokertecknet som en del av sökvägen. Även om kommandot var rekursivt, var cmdlet: en begränsad till de `Get-ChildItem` objekt som finns i Windows-mappen med namn som slutar med `.dll` .

Om du vill ange en rekursiv sökning efter filer vars namn matchar ett särskilt mönster använder du parametern **include** .

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```
