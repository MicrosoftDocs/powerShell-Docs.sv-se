---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-process?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Process
ms.openlocfilehash: 75f0b0bed808efbe31254fcd04662ddef2f3a22c
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524747"
---
# <span data-ttu-id="97199-103">Start-Process</span><span class="sxs-lookup"><span data-stu-id="97199-103">Start-Process</span></span>

## <span data-ttu-id="97199-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="97199-104">SYNOPSIS</span></span>
<span data-ttu-id="97199-105">Startar en eller flera processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="97199-105">Starts one or more processes on the local computer.</span></span>

## <span data-ttu-id="97199-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="97199-106">SYNTAX</span></span>

### <span data-ttu-id="97199-107">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="97199-107">Default (Default)</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-Credential <PSCredential>]
 [-WorkingDirectory <String>] [-LoadUserProfile] [-NoNewWindow] [-PassThru]
 [-RedirectStandardError <String>] [-RedirectStandardInput <String>]
 [-RedirectStandardOutput <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-UseNewEnvironment]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="97199-108">UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="97199-108">UseShellExecute</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-WorkingDirectory <String>]
 [-PassThru] [-Verb <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="97199-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="97199-109">DESCRIPTION</span></span>

<span data-ttu-id="97199-110">`Start-Process`Cmdleten startar en eller flera processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="97199-110">The `Start-Process` cmdlet starts one or more processes on the local computer.</span></span> <span data-ttu-id="97199-111">Som standard `Start-Process` skapar en ny process som ärver alla miljövariabler som definieras i den aktuella processen.</span><span class="sxs-lookup"><span data-stu-id="97199-111">By default, `Start-Process` creates a new process that inherits all the environment variables that are defined in the current process.</span></span>

<span data-ttu-id="97199-112">Ange det program som körs i processen genom att ange en körbar fil eller skript fil, eller en fil som kan öppnas med hjälp av ett program på datorn.</span><span class="sxs-lookup"><span data-stu-id="97199-112">To specify the program that runs in the process, enter an executable file or script file, or a file that can be opened by using a program on the computer.</span></span> <span data-ttu-id="97199-113">Om du anger en fil som inte är körbar `Start-Process` startar programmet som är associerat med filen, ungefär som- `Invoke-Item` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="97199-113">If you specify a non-executable file, `Start-Process` starts the program that is associated with the file, similar to the `Invoke-Item` cmdlet.</span></span>

<span data-ttu-id="97199-114">Du kan använda parametrarna för `Start-Process` för att ange alternativ, till exempel att läsa in en användar profil, starta processen i ett nytt fönster eller använda alternativa autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="97199-114">You can use the parameters of `Start-Process` to specify options, such as loading a user profile, starting the process in a new window, or using alternate credentials.</span></span>

## <span data-ttu-id="97199-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="97199-115">EXAMPLES</span></span>

### <span data-ttu-id="97199-116">Exempel 1: starta en process som använder standardvärden</span><span class="sxs-lookup"><span data-stu-id="97199-116">Example 1: Start a process that uses default values</span></span>

<span data-ttu-id="97199-117">I det här exemplet startas en process som använder `Sort.exe` filen i den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="97199-117">This example starts a process that uses the `Sort.exe` file in the current folder.</span></span> <span data-ttu-id="97199-118">Kommandot använder alla standardvärden, inklusive standard fönster format, arbetsmapp och autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="97199-118">The command uses all of the default values, including the default window style, working folder, and credentials.</span></span>

```powershell
Start-Process -FilePath "sort.exe"
```

### <span data-ttu-id="97199-119">Exempel 2: skriva ut en textfil</span><span class="sxs-lookup"><span data-stu-id="97199-119">Example 2: Print a text file</span></span>

<span data-ttu-id="97199-120">I det här exemplet startas en process som skriver ut `C:\PS-Test\MyFile.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="97199-120">This example starts a process that prints the `C:\PS-Test\MyFile.txt` file.</span></span>

```powershell
Start-Process -FilePath "myfile.txt" -WorkingDirectory "C:\PS-Test" -Verb Print
```

### <span data-ttu-id="97199-121">Exempel 3: starta en process för att sortera objekt till en ny fil</span><span class="sxs-lookup"><span data-stu-id="97199-121">Example 3: Start a process to sort items to a new file</span></span>

<span data-ttu-id="97199-122">I det här exemplet startas en process som sorterar objekten i `Testsort.txt` filen och returnerar de sorterade objekten i `Sorted.txt` filerna.</span><span class="sxs-lookup"><span data-stu-id="97199-122">This example starts a process that sorts items in the `Testsort.txt` file and returns the sorted items in the `Sorted.txt` files.</span></span> <span data-ttu-id="97199-123">Eventuella fel skrivs till `SortError.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="97199-123">Any errors are written to the `SortError.txt` file.</span></span>

```powershell
Start-Process -FilePath "Sort.exe" -RedirectStandardInput "Testsort.txt" -RedirectStandardOutput "Sorted.txt" -RedirectStandardError "SortError.txt" -UseNewEnvironment
```

<span data-ttu-id="97199-124">Parametern **UseNewEnvironment** anger att processen körs med egna miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="97199-124">The **UseNewEnvironment** parameter specifies that the process runs with its own environment variables.</span></span>

### <span data-ttu-id="97199-125">Exempel 4: starta en process i ett maximerat fönster</span><span class="sxs-lookup"><span data-stu-id="97199-125">Example 4: Start a process in a maximized window</span></span>

<span data-ttu-id="97199-126">Det här exemplet startar `Notepad.exe` processen.</span><span class="sxs-lookup"><span data-stu-id="97199-126">This example starts the `Notepad.exe` process.</span></span> <span data-ttu-id="97199-127">Det maximerar fönstret och bevarar fönstret tills processen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="97199-127">It maximizes the window and retains the window until the process completes.</span></span>

```powershell
Start-Process -FilePath "notepad" -Wait -WindowStyle Maximized
```

### <span data-ttu-id="97199-128">Exempel 5: starta PowerShell som administratör</span><span class="sxs-lookup"><span data-stu-id="97199-128">Example 5: Start PowerShell as an administrator</span></span>

<span data-ttu-id="97199-129">Det här exemplet startar PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="97199-129">This example starts PowerShell by using the **Run as administrator** option.</span></span>

```powershell
Start-Process -FilePath "powershell" -Verb RunAs
```

### <span data-ttu-id="97199-130">Exempel 6: använda olika verb för att starta en process</span><span class="sxs-lookup"><span data-stu-id="97199-130">Example 6: Using different verbs to start a process</span></span>

<span data-ttu-id="97199-131">Det här exemplet visar hur du hittar de verb som kan användas när du startar en process.</span><span class="sxs-lookup"><span data-stu-id="97199-131">This example shows how to find the verbs that can be used when starting a process.</span></span> <span data-ttu-id="97199-132">Tillgängliga verb bestäms av fil namns tillägget för filen som körs i processen.</span><span class="sxs-lookup"><span data-stu-id="97199-132">The available verbs are determined by the filename extension of the file that runs in the process.</span></span>

```powershell
$startExe = New-Object System.Diagnostics.ProcessStartInfo -Args PowerShell.exe
$startExe.verbs
```

```Output
open
runas
runasuser
```

<span data-ttu-id="97199-133">Exemplet använder `New-Object` för att skapa ett **system. Diagnostics. ProcessStartInfo** -objekt för **PowerShell.exe** , den fil som körs i PowerShell-processen.</span><span class="sxs-lookup"><span data-stu-id="97199-133">The example uses `New-Object` to create a **System.Diagnostics.ProcessStartInfo** object for **PowerShell.exe** , the file that runs in the PowerShell process.</span></span> <span data-ttu-id="97199-134">Egenskapen **verb** för **ProcessStartInfo** -objektet visar att du kan använda **Open** -och **runas** -verben med `PowerShell.exe` eller med en process som kör en `.exe` fil.</span><span class="sxs-lookup"><span data-stu-id="97199-134">The **Verbs** property of the **ProcessStartInfo** object shows that you can use the **Open** and **RunAs** verbs with `PowerShell.exe`, or with any process that runs a `.exe` file.</span></span>

### <span data-ttu-id="97199-135">Exempel 7: ange argument för processen</span><span class="sxs-lookup"><span data-stu-id="97199-135">Example 7: Specifying arguments to the process</span></span>

<span data-ttu-id="97199-136">Båda kommandona startar Windows kommando tolken och utfärdar ett `dir` kommando i `Program Files` mappen.</span><span class="sxs-lookup"><span data-stu-id="97199-136">Both commands start the Windows command interpreter, issuing a `dir` command on the `Program Files` folder.</span></span> <span data-ttu-id="97199-137">Eftersom den här mappnamn innehåller ett blank steg måste värdet omges av Escaped citat tecken.</span><span class="sxs-lookup"><span data-stu-id="97199-137">Because this foldername contains a space, the value needs surrounded with escaped quotes.</span></span>
<span data-ttu-id="97199-138">Observera att det första kommandot anger en sträng som **argument List**.</span><span class="sxs-lookup"><span data-stu-id="97199-138">Note that the first command specifies a string as **ArgumentList**.</span></span> <span data-ttu-id="97199-139">Det andra kommandot är en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="97199-139">The second command is a string array.</span></span>

```powershell
Start-Process -FilePath "$env:comspec" -ArgumentList "/c dir `"%systemdrive%\program files`""
Start-Process -FilePath "$env:comspec" -ArgumentList "/c","dir","`"%systemdrive%\program files`""
```

### <span data-ttu-id="97199-140">Exempel 8: skapa en frånkopplad process på Linux</span><span class="sxs-lookup"><span data-stu-id="97199-140">Example 8: Create a detached process on Linux</span></span>

<span data-ttu-id="97199-141">I Windows `Start-Process` skapar en oberoende process som förblir igång oberoende av start gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="97199-141">On Windows, `Start-Process` creates an independent process that remains running independently of the launching shell.</span></span> <span data-ttu-id="97199-142">På andra plattformar än Windows-plattformar är den nyligen startade processen kopplad till gränssnittet som startades.</span><span class="sxs-lookup"><span data-stu-id="97199-142">On non-Windows platforms, the newly started process is attached to the shell that launched.</span></span> <span data-ttu-id="97199-143">Om start gränssnittet stängs avbryts den underordnade processen.</span><span class="sxs-lookup"><span data-stu-id="97199-143">If the launching shell is closed, the child process is terminated.</span></span>

<span data-ttu-id="97199-144">För att undvika att avsluta den underordnade processen på UNIX-liknande plattformar kan du kombinera `Start-Process` med `nohup` .</span><span class="sxs-lookup"><span data-stu-id="97199-144">To avoid terminating the child process on Unix-like platforms, you can combine `Start-Process` with `nohup`.</span></span> <span data-ttu-id="97199-145">I följande exempel startas en bakgrunds instans av PowerShell på Linux som är aktiv även när du har stängt start sessionen.</span><span class="sxs-lookup"><span data-stu-id="97199-145">The following example launches a background instance of PowerShell on Linux that stays alive even after you close the launching session.</span></span> <span data-ttu-id="97199-146">`nohup`Kommandot samlar in utdata i filen `nohup.out` i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="97199-146">The `nohup` command collects output in file `nohup.out` in the current directory.</span></span>

```powershell
# Runs for 2 minutes and appends output to ./nohup.out
Start-Process nohup 'pwsh -noprofile -c "1..120 | % { Write-Host . -NoNewline; sleep 1 }"'
```

<span data-ttu-id="97199-147">I det här exemplet `Start-Process` kör Linux `nohup` -kommandot som startar `pwsh` som en frånkopplad process.</span><span class="sxs-lookup"><span data-stu-id="97199-147">In this example, `Start-Process` is running the Linux `nohup` command, which launches `pwsh` as a detached process.</span></span> <span data-ttu-id="97199-148">Mer information finns på sidan man för [nohup](https://linux.die.net/man/1/nohup).</span><span class="sxs-lookup"><span data-stu-id="97199-148">For more information, see the man page for [nohup](https://linux.die.net/man/1/nohup).</span></span>

## <span data-ttu-id="97199-149">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="97199-149">PARAMETERS</span></span>

### <span data-ttu-id="97199-150">– Argument List</span><span class="sxs-lookup"><span data-stu-id="97199-150">-ArgumentList</span></span>

<span data-ttu-id="97199-151">Anger parametrar eller parameter värden som ska användas när denna cmdlet startar processen.</span><span class="sxs-lookup"><span data-stu-id="97199-151">Specifies parameters or parameter values to use when this cmdlet starts the process.</span></span> <span data-ttu-id="97199-152">Argument kan godkännas som en enskild sträng med argumenten avgränsade med blank steg eller som en matris med strängar avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="97199-152">Arguments can be accepted as a single string with the arguments separated by spaces, or as an array of strings separated by commas.</span></span>

<span data-ttu-id="97199-153">Om parametrar eller parameter värden innehåller ett blank steg måste de omges av Escaped dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="97199-153">If parameters or parameter values contain a space, they need to be surrounded with escaped double quotes.</span></span> <span data-ttu-id="97199-154">Mer information finns i [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="97199-154">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-155">-Credential</span><span class="sxs-lookup"><span data-stu-id="97199-155">-Credential</span></span>

<span data-ttu-id="97199-156">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="97199-156">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="97199-157">Som standard använder cmdleten autentiseringsuppgifterna för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="97199-157">By default, the cmdlet uses the credentials of the current user.</span></span>

<span data-ttu-id="97199-158">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="97199-158">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="97199-159">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="97199-159">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="97199-160">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="97199-160">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="97199-161">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="97199-161">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Default
Aliases: RunAs

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-162">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="97199-162">-FilePath</span></span>

<span data-ttu-id="97199-163">Anger den valfria sökvägen och fil namnet för det program som körs i processen.</span><span class="sxs-lookup"><span data-stu-id="97199-163">Specifies the optional path and filename of the program that runs in the process.</span></span> <span data-ttu-id="97199-164">Ange namnet på en körbar fil eller ett dokument, till exempel en `.txt` eller `.doc` -fil, som är associerad med ett program på datorn.</span><span class="sxs-lookup"><span data-stu-id="97199-164">Enter the name of an executable file or of a document, such as a `.txt` or `.doc` file, that is associated with a program on the computer.</span></span> <span data-ttu-id="97199-165">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="97199-165">This parameter is required.</span></span>

<span data-ttu-id="97199-166">Om du bara anger ett fil namn använder du parametern **WorkingDirectory** för att ange sökvägen.</span><span class="sxs-lookup"><span data-stu-id="97199-166">If you specify only a filename, use the **WorkingDirectory** parameter to specify the path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-167">– LoadUserProfile</span><span class="sxs-lookup"><span data-stu-id="97199-167">-LoadUserProfile</span></span>

<span data-ttu-id="97199-168">Anger att denna cmdlet läser in Windows-användarprofilen som lagras i `HKEY_USERS` register nyckeln för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="97199-168">Indicates that this cmdlet loads the Windows user profile stored in the `HKEY_USERS` registry key for the current user.</span></span> <span data-ttu-id="97199-169">Parametern gäller inte för system som inte är Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="97199-169">The parameter does not apply for non-Windows systems.</span></span>

<span data-ttu-id="97199-170">Den här parametern påverkar inte PowerShell-profilerna.</span><span class="sxs-lookup"><span data-stu-id="97199-170">This parameter does not affect the PowerShell profiles.</span></span> <span data-ttu-id="97199-171">Mer information finns i [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="97199-171">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: Lup

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-172">-NoNewWindow</span><span class="sxs-lookup"><span data-stu-id="97199-172">-NoNewWindow</span></span>

<span data-ttu-id="97199-173">Starta den nya processen i det aktuella konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="97199-173">Start the new process in the current console window.</span></span> <span data-ttu-id="97199-174">Som standard öppnas ett nytt fönster i PowerShell i Windows.</span><span class="sxs-lookup"><span data-stu-id="97199-174">By default on Windows, PowerShell opens a new window.</span></span> <span data-ttu-id="97199-175">På andra datorer än Windows-system får du aldrig ett nytt terminalfönster.</span><span class="sxs-lookup"><span data-stu-id="97199-175">On non-Windows systems, you never get a new terminal window.</span></span>

<span data-ttu-id="97199-176">Du kan inte använda parametrarna **NoNewWindow** och **windowstyle** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="97199-176">You cannot use the **NoNewWindow** and **WindowStyle** parameters in the same command.</span></span>

<span data-ttu-id="97199-177">Parametern gäller inte för system som inte är Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="97199-177">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: nnw

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-178">– PassThru</span><span class="sxs-lookup"><span data-stu-id="97199-178">-PassThru</span></span>

<span data-ttu-id="97199-179">Returnerar ett process objekt för varje process som cmdleten startade.</span><span class="sxs-lookup"><span data-stu-id="97199-179">Returns a process object for each process that the cmdlet started.</span></span> <span data-ttu-id="97199-180">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="97199-180">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-181">-RedirectStandardError</span><span class="sxs-lookup"><span data-stu-id="97199-181">-RedirectStandardError</span></span>

<span data-ttu-id="97199-182">Anger en fil.</span><span class="sxs-lookup"><span data-stu-id="97199-182">Specifies a file.</span></span> <span data-ttu-id="97199-183">Den här cmdleten skickar eventuella fel som genereras av processen till en fil som du anger.</span><span class="sxs-lookup"><span data-stu-id="97199-183">This cmdlet sends any errors generated by the process to a file that you specify.</span></span>
<span data-ttu-id="97199-184">Ange sökväg och fil namn.</span><span class="sxs-lookup"><span data-stu-id="97199-184">Enter the path and filename.</span></span> <span data-ttu-id="97199-185">Som standard visas felen i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="97199-185">By default, the errors are displayed in the console.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-186">-RedirectStandardInput</span><span class="sxs-lookup"><span data-stu-id="97199-186">-RedirectStandardInput</span></span>

<span data-ttu-id="97199-187">Anger en fil.</span><span class="sxs-lookup"><span data-stu-id="97199-187">Specifies a file.</span></span> <span data-ttu-id="97199-188">Denna cmdlet läser indata från den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="97199-188">This cmdlet reads input from the specified file.</span></span> <span data-ttu-id="97199-189">Ange sökväg och fil namn för indatafilen.</span><span class="sxs-lookup"><span data-stu-id="97199-189">Enter the path and filename of the input file.</span></span> <span data-ttu-id="97199-190">Som standard hämtas den inmatade processen från tangent bordet.</span><span class="sxs-lookup"><span data-stu-id="97199-190">By default, the process gets its input from the keyboard.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-191">-RedirectStandardOutput</span><span class="sxs-lookup"><span data-stu-id="97199-191">-RedirectStandardOutput</span></span>

<span data-ttu-id="97199-192">Anger en fil.</span><span class="sxs-lookup"><span data-stu-id="97199-192">Specifies a file.</span></span> <span data-ttu-id="97199-193">Denna cmdlet skickar de utdata som genereras av processen till en fil som du anger.</span><span class="sxs-lookup"><span data-stu-id="97199-193">This cmdlet sends the output generated by the process to a file that you specify.</span></span>
<span data-ttu-id="97199-194">Ange sökväg och fil namn.</span><span class="sxs-lookup"><span data-stu-id="97199-194">Enter the path and filename.</span></span> <span data-ttu-id="97199-195">Som standard visas utdata i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="97199-195">By default, the output is displayed in the console.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-196">-UseNewEnvironment</span><span class="sxs-lookup"><span data-stu-id="97199-196">-UseNewEnvironment</span></span>

<span data-ttu-id="97199-197">Anger att denna cmdlet använder nya miljövariabler som har angetts för processen.</span><span class="sxs-lookup"><span data-stu-id="97199-197">Indicates that this cmdlet uses new environment variables specified for the process.</span></span> <span data-ttu-id="97199-198">Som standard körs den startade processen med miljövariablerna som ärvts från den överordnade processen.</span><span class="sxs-lookup"><span data-stu-id="97199-198">By default, the started process runs with the environment variables inherited from the parent process.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-199">-Verb</span><span class="sxs-lookup"><span data-stu-id="97199-199">-Verb</span></span>

<span data-ttu-id="97199-200">Anger ett verb som ska användas när denna cmdlet startar processen.</span><span class="sxs-lookup"><span data-stu-id="97199-200">Specifies a verb to use when this cmdlet starts the process.</span></span> <span data-ttu-id="97199-201">Vilka verb som är tillgängliga beror på fil namns tillägget för filen som körs i processen.</span><span class="sxs-lookup"><span data-stu-id="97199-201">The verbs that are available are determined by the filename extension of the file that runs in the process.</span></span>

<span data-ttu-id="97199-202">I följande tabell visas verben för vissa vanliga process fil typer.</span><span class="sxs-lookup"><span data-stu-id="97199-202">The following table shows the verbs for some common process file types.</span></span>

| <span data-ttu-id="97199-203">Filtyp</span><span class="sxs-lookup"><span data-stu-id="97199-203">File type</span></span> |                <span data-ttu-id="97199-204">Verb</span><span class="sxs-lookup"><span data-stu-id="97199-204">Verbs</span></span>                |
| --------- | ----------------------------------- |
| <span data-ttu-id="97199-205">.cmd</span><span class="sxs-lookup"><span data-stu-id="97199-205">.cmd</span></span>      | <span data-ttu-id="97199-206">Redigera, öppna, skriva ut, RunAs, RunAsUser</span><span class="sxs-lookup"><span data-stu-id="97199-206">Edit, Open, Print, RunAs, RunAsUser</span></span> |
| <span data-ttu-id="97199-207">.exe</span><span class="sxs-lookup"><span data-stu-id="97199-207">.exe</span></span>      | <span data-ttu-id="97199-208">Öppna, RunAs, RunAsUser</span><span class="sxs-lookup"><span data-stu-id="97199-208">Open, RunAs, RunAsUser</span></span>              |
| <span data-ttu-id="97199-209">.txt</span><span class="sxs-lookup"><span data-stu-id="97199-209">.txt</span></span>      | <span data-ttu-id="97199-210">Öppna, skriva ut, PrintTo</span><span class="sxs-lookup"><span data-stu-id="97199-210">Open, Print, PrintTo</span></span>                |
| <span data-ttu-id="97199-211">.wav</span><span class="sxs-lookup"><span data-stu-id="97199-211">.wav</span></span>      | <span data-ttu-id="97199-212">Öppna, spela upp</span><span class="sxs-lookup"><span data-stu-id="97199-212">Open, Play</span></span>                          |

<span data-ttu-id="97199-213">Om du vill hitta de verb som kan användas med den fil som körs i en process använder du `New-Object` cmdleten för att skapa ett **system. Diagnostics. ProcessStartInfo** -objekt för filen.</span><span class="sxs-lookup"><span data-stu-id="97199-213">To find the verbs that can be used with the file that runs in a process, use the `New-Object` cmdlet to create a **System.Diagnostics.ProcessStartInfo** object for the file.</span></span> <span data-ttu-id="97199-214">Tillgängliga verb finns i egenskapen **verbs** i **ProcessStartInfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="97199-214">The available verbs are in the **Verbs** property of the **ProcessStartInfo** object.</span></span> <span data-ttu-id="97199-215">Mer information finns i exemplen.</span><span class="sxs-lookup"><span data-stu-id="97199-215">For details, see the examples.</span></span>

<span data-ttu-id="97199-216">Parametern gäller inte för system som inte är Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="97199-216">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.String
Parameter Sets: UseShellExecute
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-217">– Vänta</span><span class="sxs-lookup"><span data-stu-id="97199-217">-Wait</span></span>

<span data-ttu-id="97199-218">Anger att denna cmdlet väntar på att den angivna processen och dess underordnade ska slutföras innan fler indatatyper accepteras.</span><span class="sxs-lookup"><span data-stu-id="97199-218">Indicates that this cmdlet waits for the specified process and its descendants to complete before accepting more input.</span></span> <span data-ttu-id="97199-219">Den här parametern förhindrar kommando tolken eller behåller fönstret tills processerna har slutförts.</span><span class="sxs-lookup"><span data-stu-id="97199-219">This parameter suppresses the command prompt or retains the window until the processes finish.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-220">– WindowStyle</span><span class="sxs-lookup"><span data-stu-id="97199-220">-WindowStyle</span></span>

<span data-ttu-id="97199-221">Anger status för det fönster som används för den nya processen.</span><span class="sxs-lookup"><span data-stu-id="97199-221">Specifies the state of the window that is used for the new process.</span></span> <span data-ttu-id="97199-222">De acceptabla värdena för den här parametern är: **Normal** , **dold** , **minimerad** och **maximerad**.</span><span class="sxs-lookup"><span data-stu-id="97199-222">The acceptable values for this parameter are: **Normal** , **Hidden** , **Minimized** , and **Maximized**.</span></span> <span data-ttu-id="97199-223">Standardvärdet är **Normal**.</span><span class="sxs-lookup"><span data-stu-id="97199-223">The default value is **Normal**.</span></span>

<span data-ttu-id="97199-224">Du kan inte använda parametrarna **windowstyle** och **NoNewWindow** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="97199-224">You cannot use the **WindowStyle** and **NoNewWindow** parameters in the same command.</span></span>

<span data-ttu-id="97199-225">Parametern gäller inte för system som inte är Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="97199-225">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.Diagnostics.ProcessWindowStyle
Parameter Sets: (All)
Aliases:
Accepted values: Normal, Hidden, Minimized, Maximized

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-226">– WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="97199-226">-WorkingDirectory</span></span>

<span data-ttu-id="97199-227">Anger den plats som den nya processen ska starta i.</span><span class="sxs-lookup"><span data-stu-id="97199-227">Specifies the location that the new process should start in.</span></span> <span data-ttu-id="97199-228">Standardvärdet är platsen för den körbara filen eller det dokument som startas.</span><span class="sxs-lookup"><span data-stu-id="97199-228">The default is the location of the executable file or document being started.</span></span> <span data-ttu-id="97199-229">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="97199-229">Wildcards are not supported.</span></span> <span data-ttu-id="97199-230">Sök vägs namnet får inte innehålla tecken som tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="97199-230">The path name must not contain characters that would be interpreted as wildcards.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-231">-Confirm</span><span class="sxs-lookup"><span data-stu-id="97199-231">-Confirm</span></span>

<span data-ttu-id="97199-232">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="97199-232">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-233">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="97199-233">-WhatIf</span></span>

<span data-ttu-id="97199-234">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="97199-234">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="97199-235">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="97199-235">The cmdlet is not run.</span></span>

<span data-ttu-id="97199-236">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="97199-236">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97199-237">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="97199-237">CommonParameters</span></span>

<span data-ttu-id="97199-238">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="97199-238">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="97199-239">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="97199-239">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="97199-240">INDATA</span><span class="sxs-lookup"><span data-stu-id="97199-240">INPUTS</span></span>

### <span data-ttu-id="97199-241">Inget</span><span class="sxs-lookup"><span data-stu-id="97199-241">None</span></span>

<span data-ttu-id="97199-242">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="97199-242">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="97199-243">UTDATA</span><span class="sxs-lookup"><span data-stu-id="97199-243">OUTPUTS</span></span>

### <span data-ttu-id="97199-244">Ingen, system. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="97199-244">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="97199-245">Denna cmdlet genererar ett **system. Diagnostics. process** -objekt, om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="97199-245">This cmdlet generates a **System.Diagnostics.Process** object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="97199-246">Annars returnerar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="97199-246">Otherwise, this cmdlet does not return any output.</span></span>

## <span data-ttu-id="97199-247">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="97199-247">NOTES</span></span>

- <span data-ttu-id="97199-248">Denna cmdlet implementeras med hjälp av metoden **Start** i klassen **system. Diagnostics. process** .</span><span class="sxs-lookup"><span data-stu-id="97199-248">This cmdlet is implemented by using the **Start** method of the **System.Diagnostics.Process** class.</span></span> <span data-ttu-id="97199-249">Mer information om den här metoden finns i [metoden process. start](/dotnet/api/system.diagnostics.process.start#overloads).</span><span class="sxs-lookup"><span data-stu-id="97199-249">For more information about this method, see [Process.Start Method](/dotnet/api/system.diagnostics.process.start#overloads).</span></span>

- <span data-ttu-id="97199-250">När du använder **UseNewEnvironment** i Windows, börjar den nya processen bara att innehålla de standard miljö variabler som definierats för **dator** omfånget.</span><span class="sxs-lookup"><span data-stu-id="97199-250">On Windows, when you use **UseNewEnvironment** , the new process starts only containing the default environment variables defined for the **Machine** scope.</span></span> <span data-ttu-id="97199-251">Detta har samma effekt som `$env:USERNAME` är inställd på **system**.</span><span class="sxs-lookup"><span data-stu-id="97199-251">This has the side affect that the `$env:USERNAME` is set to **SYSTEM**.</span></span> <span data-ttu-id="97199-252">Ingen av variablerna från **användar** omfånget ingår.</span><span class="sxs-lookup"><span data-stu-id="97199-252">None of the variables from the **User** scope are included.</span></span>

- <span data-ttu-id="97199-253">I Windows är det vanligaste användnings fallet för `Start-Process` att använda parametern **wait** för att blockera förloppet tills den nya processen avslutas.</span><span class="sxs-lookup"><span data-stu-id="97199-253">On Windows, the most common use case for `Start-Process` is to use the **Wait** parameter to block progress until the new process exits.</span></span> <span data-ttu-id="97199-254">På andra datorer än Windows-system behövs detta sällan eftersom standard beteendet för kommando rads program är lika med `Start-Process -Wait` .</span><span class="sxs-lookup"><span data-stu-id="97199-254">On non-Windows system, this is rarely needed since the default behavior for command-line applications is equivalent to `Start-Process -Wait`.</span></span>

- <span data-ttu-id="97199-255">När `Start-Process` du använder på andra datorer än Windows-system får du aldrig ett nytt terminalfönster.</span><span class="sxs-lookup"><span data-stu-id="97199-255">When using `Start-Process` on non-Windows systems, you never get a new terminal window.</span></span>

## <span data-ttu-id="97199-256">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="97199-256">RELATED LINKS</span></span>

[<span data-ttu-id="97199-257">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="97199-257">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="97199-258">Fel sökning – process</span><span class="sxs-lookup"><span data-stu-id="97199-258">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="97199-259">Hämta process</span><span class="sxs-lookup"><span data-stu-id="97199-259">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="97199-260">Start-Service</span><span class="sxs-lookup"><span data-stu-id="97199-260">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="97199-261">Stoppa – process</span><span class="sxs-lookup"><span data-stu-id="97199-261">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="97199-262">Vänta-process</span><span class="sxs-lookup"><span data-stu-id="97199-262">Wait-Process</span></span>](Wait-Process.md)
