---
description: Förklarar hur du använder kommando rads verktyget PowerShell_Ise.exe.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_ise_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Ise_exe
ms.openlocfilehash: c7500eb6d8586b9dca568edc4e805c577e94bec4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272030"
---
# <a name="about-powershell-iseexe"></a>Om PowerShell-Ise.exe

## <a name="short-description"></a>KORT BESKRIVNING

Förklarar hur du använder kommando rads verktyget PowerShell_Ise.exe.

## <a name="long-description"></a>LÅNG BESKRIVNING

PowerShell_Ise.exe startar en Windows PowerShell ISE-session (Integrated Scripting Environment). Du kan köra den i Cmd.exe och i Windows PowerShell.

Om du vill köra PowerShell_ISE.exe skriver du PowerShell_ISE.exe, PowerShell_ISE eller ISE.

## <a name="syntax"></a>SYNTAX

```
PowerShell_Ise[.exe]
PowerShell_ISE[.exe]
ISE[.exe]
[-File]<FilePath[]> [-NoProfile] [-MTA]
-Help | ? | -? | /? Displays the syntax and describes the command-line switches.
```

## <a name="parameters"></a>PARAMETRAR

### <a name="-file"></a>– Fil

Öppnar de angivna filerna i Windows PowerShell ISE. Parameter namnet ("-File") är valfritt. Om du vill visa fler än en fil anger du en text sträng inom citat tecken. Använd kommatecken för att avgränsa fil namnen i strängen.

Ett exempel:

PowerShell_ISE-File "File1.ps1, File2.ps1 File3.xml".

Blank steg mellan fil namnen tillåts i Windows PowerShell, men kanske inte tolkas korrekt av andra program, t. ex. Cmd.exe.

Du kan använda den här parametern för att öppna en textfil, inklusive Windows PowerShell-skriptfiler och XML-filer.

### <a name="-mta"></a>-Mta

Startar Windows PowerShell ISE med hjälp av en flertrådad inne slutning. Den här parametern introduceras i Windows PowerShell 3,0. Enkel tråds Apartment (STA) är standard.

### <a name="-noprofile"></a>-Noprofil

Kör inte Windows PowerShell-profiler. Som standard körs Windows PowerShell-profiler i varje session.

Den här parametern rekommenderas när du skriver delat innehåll, till exempel funktioner och skript som ska köras på system med olika profiler.
Mer information finns i [about_Profiles](about_Profiles.md).

### <a name="-help---"></a>– Hjälp-?,/?

Visar hjälp för PowerShell_ISE.exe.

## <a name="examples"></a>EXEMPEL

Kommandona startar Windows PowerShell ISE. Kommandona är likvärdiga och kan användas utbytbara.

```
PS C:> PowerShell_ISE.exe
PS C:> PowerShell_ISE
PS C:> ISE
```

Kommandona öppnar Get-Profile.ps1-skriptet i Windows PowerShell ISE.
Kommandona är likvärdiga och kan användas utbytbara.

```
PS C:> PowerShell_ISE.exe -File .\Get-Profile.ps1
PS C:> ISE -File .\Get-Profile.ps1
PS C:> ISE .\Get-Profile.ps1
```

Det här kommandot öppnar Get-Backups.ps1 och Get-BackupInstance.ps1 skript i Windows PowerShell ISE. Om du vill öppna fler än en fil, använder du ett kommatecken för att avgränsa fil namnen och omger hela fil namnets värde inom citat tecken.

```
PS C:> ISE -File ".\Get-Backups.ps1,Get-BackupInstance.ps1"
```

Det här kommandot startar Windows PowerShell ISE utan profiler.

```
PS C:> ISE -NoProfile
```

Det här kommandot hämtar hjälp för PowerShell_ISE.exe.

```
PS C:> ISE -help
```

## <a name="see-also"></a>SE ÄVEN

[about_PowerShell.exe](about_PowerShell_exe.md)

[about_Windows_PowerShell_ISE](about_Windows_PowerShell_ISE.md)

[Windows PowerShell Integrated Scripting Environment (ISE)](/powershell/scripting/windows-powershell/ise/introducing-the-windows-powershell-ise)
