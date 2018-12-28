---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Arbeta med filer, mappar och registernycklar
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: a09b127d4ba37d33cb4c0f0ce0819e645fd4b137
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405495"
---
# <a name="working-with-files-folders-and-registry-keys"></a>Arbeta med filer, mappar och registernycklar

Windows PowerShell använder substantivet **objekt** att referera till objekt som finns på en Windows PowerShell-enhet. När du hanterar filsystem för Windows PowerShell-providern, en **objekt** kan vara en fil, en mapp eller Windows PowerShell-enhet. Lista och arbeta med de här objekten är en kritisk standardaktivitet i de flesta administrativa inställningar, så vi vill diskutera dessa uppgifter i detalj.

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>Räkna upp filer, mappar och registernycklar (Get-ChildItem)

Eftersom hämtar en samling objekt från en viss plats är sådan vanliga uppgift, den **Get-ChildItem** cmdlet har utformats speciellt för att returnera alla objekt som hittas i en behållare, till exempel en mapp.

Om du vill returnera alla filer och mappar som finns direkt i mappen C:\\Windows, typ:

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

Listan liknar vad som skulle visas när du anger den **dir** i **Cmd.exe**, eller **ls** i en UNIX-kommandogränssnittet.

Du kan utföra mycket komplex listor med hjälp av parametrarna för den **Get-ChildItem** cmdlet. Vi ska titta på några scenarier bredvid. Du kan se syntaxen i **Get-ChildItem** cmdlet genom att skriva:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Dessa parametrar kan kombineras och matchas i syfte för att få stora anpassningar utdata.

#### <a name="listing-all-contained-items--recurse"></a>Lista alla innehöll objekt (-Recurse)

Om du vill se både objekt i en Windows-mapp och alla objekt som ingår i undermapparna, använda den **Recurse** -parametern för **Get-ChildItem**. Listan visar allt inom den Windows-mappen och dess undermappar objekt. Till exempel:

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

Använd för att visa bara namnen på objekten i **namn** -parametern för **Get-Childitem**:

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a>Forcerar lista dolda objekt (-Force)

Objekt som är normalt osynliga i Utforskaren eller Cmd.exe inte visas i utdata från en **Get-ChildItem** kommando. Använd för att visa dolda objekt, den **kraft** -parametern för **Get-ChildItem**. Till exempel:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Den här parametern heter Force eftersom du kan framtvinga åsidosätta det normala beteendet för den **Get-ChildItem** kommando. Force är en term som används parameter som tvingar en åtgärd som inte normalt utför en cmdlet, även om det inte att utföra några åtgärder som äventyrar säkerheten i systemet.

#### <a name="matching-item-names-with-wildcards"></a>Matchande namn med jokertecken

**Get-ChildItem** kommando accepterar jokertecken i sökvägen till de objekt som ska visas.

Eftersom matchning med jokertecken hanteras av Windows PowerShell-motorn, alla cmdletar som accepterar jokertecken använder samma notation och har samma matchande beteende. Windows PowerShell med jokertecken notation innehåller:

- Asterisk (\*) matchar noll eller flera förekomster av valfritt tecken.

- Frågetecken (?) matchar exakt 1 tecken.

- Vänster hakparentes (\[) tecken och tecken som höger hakparentes (]) omger du en uppsättning tecken som ska matchas.

Här följer några exempel på hur det fungerar med jokertecken-specifikationen.

Att hitta alla filer i katalogen Windows med suffixet **.log** och fem tecken i det grundläggande namnet, anger du följande kommando:

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

Att hitta alla filer som börjar med bokstaven **x** i Windows-katalogen, skriver du:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Att hitta alla filer vars namn börjar med **x** eller **z**, typ:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a>Undanta objekt (-exkludera)

Du kan utesluta specifika objekt med hjälp av den **undanta** -parametern för Get-ChildItem. På så sätt kan du utföra komplex filtrering i en enskild instruktion.

Anta exempelvis att du försöker att hitta Windows Time Service DLL-filen i mappen System32 och allt du kan komma ihåg om DLL-namn är att den börjar med ”W” och innehåller ”32”.

Ett uttryck som **w\&#42; 32\&#42;. DLL-filen** hittar alla DLL: er som uppfyller villkoren, men det kan också returnera Windows 95 och 16-bitars Windows kompatibilitet DLL-filer som innehåller ”95” eller ”16” i sina namn. Du kan hoppa över filer som har någon av dessa siffror i sina namn med hjälp av den **undanta** parametern med mönstret  **\&#42;\[ 9516]\&#42;**:

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

#### <a name="mixing-get-childitem-parameters"></a>Blandade Get-ChildItem parametrar

Du kan använda flera av parametrarna i den **Get-ChildItem** cmdlet i samma kommando. Innan du blanda parametrar måste du kontrollera att du förstår matchning med jokertecken. Till exempel returnerar följande kommando inga resultat:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Det finns inga resultat, även om det finns två DLL: er som börjar med bokstaven ”z” i Windows-mappen.

Inga resultat returnerades eftersom vi angav jokertecknet som en del av sökvägen. Även om kommandot har rekursiv, den **Get-ChildItem** cmdlet begränsade objekten till dem som ingår i Windows-mappen med namn som slutar med ”dll”.

Om du vill ange en rekursiv sökning efter filer vars namn matchar ett särskilt mönster, använda den **-inkludera** parametern.

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