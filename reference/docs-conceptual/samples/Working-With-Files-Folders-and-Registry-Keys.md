---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Arbeta med filer, mappar och registernycklar
ms.openlocfilehash: 0c8716c384827d0816e2847ff81232c14638681b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030754"
---
# <a name="working-with-files-folders-and-registry-keys"></a>Arbeta med filer, mappar och register nycklar

Windows PowerShell använder **objektet** Substantiv för att referera till objekt som finns på en Windows PowerShell-enhet. När du hanterar Windows PowerShell-filsystem-providern kan ett **objekt** vara en fil, en mapp eller Windows PowerShell-enheten. Att lista och arbeta med dessa objekt är en viktig grundläggande uppgift i de flesta administrativa inställningar, så vi vill diskutera dessa uppgifter i detalj.

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>Räkna upp filer, mappar och register nycklar (Get-ChildItem)

Eftersom hämtning av en samling av objekt från en viss plats är en sådan vanlig uppgift, är cmdleten **Get-ChildItem** utformad för att returnera alla objekt som finns i en behållare, till exempel en mapp.

Om du vill returnera alla filer och mappar som finns direkt i mappen C:\\Windows, skriver du:

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

Listan ser ut ungefär som du ser när du anger kommandot **dir** i **cmd. exe**eller kommandot **ls** i ett UNIX-kommando gränssnitt.

Du kan utföra mycket komplexa listor genom att använda parametrarna för **Get-ChildItem** -cmdlet: en. Vi kommer att titta på några scenarier härnäst. Du kan se syntaxen **Get-ChildItem** -cmdleten genom att skriva:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Dessa parametrar kan kombineras och matchas för att få mycket anpassade utdata.

### <a name="listing-all-contained-items--recurse"></a>Visar alla objekt som finns (-rekursivt)

Om du vill se både objekten i en Windows-mapp och alla objekt som ingår i undermapparna använder du parametern **rekursivt** för **Get-ChildItem**. I listan visas allting i Windows-mappen och objekten i dess undermappar. Till exempel:

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

Om du bara vill visa objekt namn använder du **Name** -parametern för **Get-Childitem**:

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a>Tvångs lista över dolda objekt (-Force)

Objekt som normalt är osynliga i Utforskaren eller cmd. exe visas inte i utdata från ett **Get-ChildItem** -kommando. Använd parametern **Force** för **Get-ChildItem**om du vill visa dolda objekt. Till exempel:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Den här parametern heter Force eftersom du kan framtvinga åsidosättning av det normala beteendet för kommandot **Get-ChildItem** . Force är en mycket Använd parameter som tvingar fram en åtgärd som en cmdlet normalt inte utför, även om den inte kommer att utföra någon åtgärd som äventyrar säkerheten i systemet.

### <a name="matching-item-names-with-wildcards"></a>Matchande objekt namn med jokertecken

Kommandot **Get-ChildItem** accepterar jokertecken i sökvägen för objekten som ska listas.

Eftersom matchning av jokertecken hanteras av Windows PowerShell-motorn, använder alla cmdlets som accepterar jokertecken samma notation och har samma matchnings beteende. Jokertecken i Windows PowerShell innehåller:

- Asterisk (\*) matchar noll eller flera förekomster av tecken.

- Frågetecken (?) matchar exakt ett tecken.

- Vänster hak paren tes tecken (\[) och höger hak paren tes (]) omger en uppsättning tecken som ska matchas.

Här följer några exempel på hur wildcard-specifikation fungerar.

Om du vill hitta alla filer i Windows-katalogen med suffixet **. log** och exakt fem tecken i bas namnet anger du följande kommando:

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

Om du vill hitta alla filer som börjar med bokstaven **x** i Windows-katalogen skriver du:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Om du vill hitta alla filer vars namn börjar med **x** eller **z**skriver du:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a>Uteslut objekt (-exkludera)

Du kan exkludera vissa objekt med hjälp av parametern **exclude** för Get-ChildItem. På så sätt kan du utföra komplex filtrering i ett enda uttryck.

Anta till exempel att du försöker hitta Windows Time Service-DLL i mappen System32, och allt du kan komma ihåg om DLL-namnet är att det börjar med "W" och innehåller "32".

Ett uttryck som **w\&#42; 32\&#42;. DLL** hittar alla DLL: er som uppfyller villkoren, men kan också returnera windows 95-och 16-bitars Windows-kompatibla dll: er som innehåller "95" eller "16" i namnen. Du kan utelämna filer som har något av dessa nummer i namnen med hjälp av parametern **exclude** med mönstret **\&#42;\[9516]\&#42;** :

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a>Blanda get-ChildItem-parametrar

Du kan använda flera av parametrarna för **Get-ChildItem** -cmdlet: en i samma kommando. Innan du blandar parametrar bör du vara säker på att du förstår matchning med jokertecken. Följande kommando returnerar till exempel inga resultat:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Det finns inga resultat, även om det finns två dll: er som börjar med bokstaven "z" i Windows-mappen.

Inga resultat returnerades eftersom vi har angett jokertecknet som en del av sökvägen. Även om kommandot var rekursivt, har cmdleten **Get-ChildItem** begränsat objekten till de som finns i Windows-mappen med namn som slutar med ". dll".

Om du vill ange en rekursiv sökning efter filer vars namn matchar ett särskilt mönster använder du parametern **-include** .

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
