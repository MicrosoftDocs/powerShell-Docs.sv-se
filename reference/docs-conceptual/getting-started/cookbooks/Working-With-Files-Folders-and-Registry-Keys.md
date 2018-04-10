---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Arbeta med filer, mappar och registernycklar
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: a09b127d4ba37d33cb4c0f0ce0819e645fd4b137
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-files-folders-and-registry-keys"></a>Arbeta med filer, mappar och registernycklar

Windows PowerShell använder substantivet **objektet** att referera till objekt som finns på en Windows PowerShell-enhet. När du hanterar filsystem för Windows PowerShell-providern en **objektet** kan vara en fil, en mapp eller Windows PowerShell-enheten. Lista och arbeta med dessa objekt är en kritisk standardaktivitet i de flesta administrativa inställningar, så vi vill diskutera dessa uppgifter i detalj.

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>Uppräkning av filer, mappar och registernycklar (Get-ChildItem)

Eftersom hämtningen av en samling objekt från en viss plats är sådan vanliga uppgift i **Get-ChildItem** cmdlet är utformad särskilt för att returnera alla poster som hittades i en behållare, till exempel en mapp.

Om du vill återställa alla filer och mappar som finns i mappen C: direkt\\Windows, typ:

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

Listan liknar vad som visas när du anger den **dir** i **Cmd.exe**, eller **ls** i UNIX-kommandogränssnittet.

Du kan utföra mycket komplex listor med hjälp av parametrarna för den **Get-ChildItem** cmdlet. Vi ska titta på några scenarier nästa. Du kan se syntaxen i **Get-ChildItem** cmdlet genom att skriva:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

De här parametrarna kan blandas och matchas för att hämta anpassade utdata.

#### <a name="listing-all-contained-items--recurse"></a>Visar en lista över alla artiklar som ingår (-Recurse)

Både objekt i en Windows-mappen och alla objekt som ingår i undermapparna, Använd den **Recurse** -parametern för **Get-ChildItem**. Listan visar allt i Windows-mappen och objekten i dess undermappar. Till exempel:

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a>Filtrera objekt efter namn (-namn)

Använd för att visa endast namnen på objekten i **namn** -parametern för **Get-Childitem**:

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a>Framtvingar lista dolda objekt (-Force)

Objekt som är normalt osynliga i Utforskaren eller Cmd.exe visas inte i utdata från en **Get-ChildItem** kommando. Använd för att visa dolda objekt i **kraft** -parametern för **Get-ChildItem**. Till exempel:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Den här parametern heter kraft eftersom du kan framtvinga åsidosätta normalt av den **Get-ChildItem** kommando. Force är en mycket vanlig parameter som tvingar en åtgärd som en cmdlet inte normalt utförs, även om det inte kommer att utföra en åtgärd som äventyrar säkerheten för systemet.

#### <a name="matching-item-names-with-wildcards"></a>Matcha namn med jokertecken

**Get-ChildItem** kommandot accepterar jokertecken i sökvägen för objekt i listan.

Eftersom matchning med jokertecken hanteras av Windows PowerShell-motorn kan alla cmdletar som accepterar jokertecken använder samma notation och har samma matchande beteende. Windows PowerShell med jokertecken notation innehåller:

- Asterisk (\*) matchar noll eller flera förekomster av ett tecken.

- Frågetecken (?) matchar exakt ett tecken.

- Vänster hakparentes (\[) tecken och höger hakparentes (]) tecken omges av en uppsättning tecken som ska matchas.

Här följer några exempel på hur det fungerar med jokertecken-specifikationen.

Hitta alla filer i Windows-katalogen med suffixet **.log** och fem tecknen i det grundläggande namnet, anger du följande kommando:

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

Hitta alla filer som börjar med bokstaven **x** i Windows-katalogen, skriver du:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Hitta alla filer vars namn börjar med **x** eller **z**, typ:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a>Exkludera objekt (-exkludera)

Du kan exkludera specifika objekt med hjälp av den **undanta** parametern för Get-ChildItem. På så sätt kan du utföra komplicerade filtrering i en enskild instruktion.

Anta att du vill hitta Windows tid tjänsten DLL-filen i mappen System32 och alla du kommer ihåg om DLL-namn är att den börjar med ”W” och ”32” det finns i.

Ett uttryck som **w\&#42; 32\&#42;. DLL-filen** hittar alla DLL: er som uppfyller villkoren, men den kan också returnera Windows 95 och 16-bitars Windows-kompatibilitet DLL-filer som innehåller ”95” eller ”16” i sina namn. Du kan hoppa över filer med någon av dessa siffror i sina namn med hjälp av den **undanta** parameter med mönstret  **\&#42;\[ 9516]\&#42;**:

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

#### <a name="mixing-get-childitem-parameters"></a>Blanda Get-ChildItem parametrar

Du kan använda flera av parametrarna i den **Get-ChildItem** cmdlet i samma kommando. Innan du blanda parametrar måste du kontrollera att du förstår matchning med jokertecken. Till exempel returnerar följande kommando inga resultat:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Det finns inga resultat, även om det finns två DLL: er som börjar med bokstaven ”z” i Windows-mappen.

Inga resultat returnerades eftersom vi har angetts till jokertecken som en del av sökvägen. Även om kommandot var rekursiv den **Get-ChildItem** cmdlet begränsad objekten till dem som finns i Windows-mappen med namn som slutar med ”dll”.

Om du vill ange en rekursiv sökning efter filer vars namn matchar ett särskilt mönster i **-inkludera** parameter.

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