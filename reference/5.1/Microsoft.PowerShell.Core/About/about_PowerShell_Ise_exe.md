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
# <a name="about-powershell-iseexe"></a><span data-ttu-id="e43ca-104">Om PowerShell-Ise.exe</span><span class="sxs-lookup"><span data-stu-id="e43ca-104">About PowerShell Ise.exe</span></span>

## <a name="short-description"></a><span data-ttu-id="e43ca-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e43ca-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="e43ca-106">Förklarar hur du använder kommando rads verktyget PowerShell_Ise.exe.</span><span class="sxs-lookup"><span data-stu-id="e43ca-106">Explains how to use the PowerShell_Ise.exe command-line tool.</span></span>

## <a name="long-description"></a><span data-ttu-id="e43ca-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e43ca-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e43ca-108">PowerShell_Ise.exe startar en Windows PowerShell ISE-session (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="e43ca-108">PowerShell_Ise.exe starts a Windows PowerShell Integrated Scripting Environment (ISE) session.</span></span> <span data-ttu-id="e43ca-109">Du kan köra den i Cmd.exe och i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e43ca-109">You can run it in Cmd.exe and in Windows PowerShell.</span></span>

<span data-ttu-id="e43ca-110">Om du vill köra PowerShell_ISE.exe skriver du PowerShell_ISE.exe, PowerShell_ISE eller ISE.</span><span class="sxs-lookup"><span data-stu-id="e43ca-110">To run PowerShell_ISE.exe, type PowerShell_ISE.exe, PowerShell_ISE, or ISE.</span></span>

## <a name="syntax"></a><span data-ttu-id="e43ca-111">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e43ca-111">SYNTAX</span></span>

```
PowerShell_Ise[.exe]
PowerShell_ISE[.exe]
ISE[.exe]
[-File]<FilePath[]> [-NoProfile] [-MTA]
-Help | ? | -? | /? Displays the syntax and describes the command-line switches.
```

## <a name="parameters"></a><span data-ttu-id="e43ca-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e43ca-112">PARAMETERS</span></span>

### <a name="-file"></a><span data-ttu-id="e43ca-113">– Fil</span><span class="sxs-lookup"><span data-stu-id="e43ca-113">-File</span></span>

<span data-ttu-id="e43ca-114">Öppnar de angivna filerna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="e43ca-114">Opens the specified files in Windows PowerShell ISE.</span></span> <span data-ttu-id="e43ca-115">Parameter namnet ("-File") är valfritt.</span><span class="sxs-lookup"><span data-stu-id="e43ca-115">The parameter name ("-File") is optional.</span></span> <span data-ttu-id="e43ca-116">Om du vill visa fler än en fil anger du en text sträng inom citat tecken.</span><span class="sxs-lookup"><span data-stu-id="e43ca-116">To list more than one file, enter one text string enclosed in quotation marks.</span></span> <span data-ttu-id="e43ca-117">Använd kommatecken för att avgränsa fil namnen i strängen.</span><span class="sxs-lookup"><span data-stu-id="e43ca-117">Use commas to separate the file names within the string.</span></span>

<span data-ttu-id="e43ca-118">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="e43ca-118">For example:</span></span>

<span data-ttu-id="e43ca-119">PowerShell_ISE-File "File1.ps1, File2.ps1 File3.xml".</span><span class="sxs-lookup"><span data-stu-id="e43ca-119">PowerShell_ISE -File "File1.ps1,File2.ps1,File3.xml".</span></span>

<span data-ttu-id="e43ca-120">Blank steg mellan fil namnen tillåts i Windows PowerShell, men kanske inte tolkas korrekt av andra program, t. ex. Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="e43ca-120">Spaces between the file names are permitted in Windows PowerShell, but might not be interpreted correctly by other programs, such as Cmd.exe.</span></span>

<span data-ttu-id="e43ca-121">Du kan använda den här parametern för att öppna en textfil, inklusive Windows PowerShell-skriptfiler och XML-filer.</span><span class="sxs-lookup"><span data-stu-id="e43ca-121">You can use this parameter to open any text file, including Windows PowerShell script files and XML files.</span></span>

### <a name="-mta"></a><span data-ttu-id="e43ca-122">-Mta</span><span class="sxs-lookup"><span data-stu-id="e43ca-122">-Mta</span></span>

<span data-ttu-id="e43ca-123">Startar Windows PowerShell ISE med hjälp av en flertrådad inne slutning.</span><span class="sxs-lookup"><span data-stu-id="e43ca-123">Starts Windows PowerShell ISE using a multi-threaded apartment.</span></span> <span data-ttu-id="e43ca-124">Den här parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e43ca-124">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="e43ca-125">Enkel tråds Apartment (STA) är standard.</span><span class="sxs-lookup"><span data-stu-id="e43ca-125">Single-threaded apartment (STA) is the default.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="e43ca-126">-Noprofil</span><span class="sxs-lookup"><span data-stu-id="e43ca-126">-NoProfile</span></span>

<span data-ttu-id="e43ca-127">Kör inte Windows PowerShell-profiler.</span><span class="sxs-lookup"><span data-stu-id="e43ca-127">Does not run Windows PowerShell profiles.</span></span> <span data-ttu-id="e43ca-128">Som standard körs Windows PowerShell-profiler i varje session.</span><span class="sxs-lookup"><span data-stu-id="e43ca-128">By default, Windows PowerShell profiles are run in every session.</span></span>

<span data-ttu-id="e43ca-129">Den här parametern rekommenderas när du skriver delat innehåll, till exempel funktioner och skript som ska köras på system med olika profiler.</span><span class="sxs-lookup"><span data-stu-id="e43ca-129">This parameter is recommended when you are writing shared content, such as functions and scripts that will be run on systems with different profiles.</span></span>
<span data-ttu-id="e43ca-130">Mer information finns i [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e43ca-130">For more information, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="-help---"></a><span data-ttu-id="e43ca-131">– Hjälp-?,/?</span><span class="sxs-lookup"><span data-stu-id="e43ca-131">-Help -?, /?</span></span>

<span data-ttu-id="e43ca-132">Visar hjälp för PowerShell_ISE.exe.</span><span class="sxs-lookup"><span data-stu-id="e43ca-132">Displays help for PowerShell_ISE.exe.</span></span>

## <a name="examples"></a><span data-ttu-id="e43ca-133">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e43ca-133">EXAMPLES</span></span>

<span data-ttu-id="e43ca-134">Kommandona startar Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="e43ca-134">These commands start Windows PowerShell ISE.</span></span> <span data-ttu-id="e43ca-135">Kommandona är likvärdiga och kan användas utbytbara.</span><span class="sxs-lookup"><span data-stu-id="e43ca-135">The commands are equivalent and can be used interchangeably.</span></span>

```
PS C:> PowerShell_ISE.exe
PS C:> PowerShell_ISE
PS C:> ISE
```

<span data-ttu-id="e43ca-136">Kommandona öppnar Get-Profile.ps1-skriptet i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="e43ca-136">These commands open the Get-Profile.ps1 script in Windows PowerShell ISE.</span></span>
<span data-ttu-id="e43ca-137">Kommandona är likvärdiga och kan användas utbytbara.</span><span class="sxs-lookup"><span data-stu-id="e43ca-137">The commands are equivalent and can be used interchangeably.</span></span>

```
PS C:> PowerShell_ISE.exe -File .\Get-Profile.ps1
PS C:> ISE -File .\Get-Profile.ps1
PS C:> ISE .\Get-Profile.ps1
```

<span data-ttu-id="e43ca-138">Det här kommandot öppnar Get-Backups.ps1 och Get-BackupInstance.ps1 skript i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="e43ca-138">This command opens the Get-Backups.ps1 and Get-BackupInstance.ps1 scripts in Windows PowerShell ISE.</span></span> <span data-ttu-id="e43ca-139">Om du vill öppna fler än en fil, använder du ett kommatecken för att avgränsa fil namnen och omger hela fil namnets värde inom citat tecken.</span><span class="sxs-lookup"><span data-stu-id="e43ca-139">To open more than one file, use a comma to separate the file names and enclose the entire file name value in quotation marks.</span></span>

```
PS C:> ISE -File ".\Get-Backups.ps1,Get-BackupInstance.ps1"
```

<span data-ttu-id="e43ca-140">Det här kommandot startar Windows PowerShell ISE utan profiler.</span><span class="sxs-lookup"><span data-stu-id="e43ca-140">This command starts Windows PowerShell ISE with no profiles.</span></span>

```
PS C:> ISE -NoProfile
```

<span data-ttu-id="e43ca-141">Det här kommandot hämtar hjälp för PowerShell_ISE.exe.</span><span class="sxs-lookup"><span data-stu-id="e43ca-141">This command gets help for PowerShell_ISE.exe.</span></span>

```
PS C:> ISE -help
```

## <a name="see-also"></a><span data-ttu-id="e43ca-142">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="e43ca-142">SEE ALSO</span></span>

[<span data-ttu-id="e43ca-143">about_PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="e43ca-143">about_PowerShell.exe</span></span>](about_PowerShell_exe.md)

[<span data-ttu-id="e43ca-144">about_Windows_PowerShell_ISE</span><span class="sxs-lookup"><span data-stu-id="e43ca-144">about_Windows_PowerShell_ISE</span></span>](about_Windows_PowerShell_ISE.md)

[<span data-ttu-id="e43ca-145">Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="e43ca-145">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>](/powershell/scripting/windows-powershell/ise/introducing-the-windows-powershell-ise)
