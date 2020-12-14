---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Process
ms.openlocfilehash: 28f343ddc6021e129d3eae007114b93ed17d5e95
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710381"
---
# <span data-ttu-id="ea0b3-102">Start-Process</span><span class="sxs-lookup"><span data-stu-id="ea0b3-102">Start-Process</span></span>

## <span data-ttu-id="ea0b3-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ea0b3-103">SYNOPSIS</span></span>
<span data-ttu-id="ea0b3-104">Startar en eller flera processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-104">Starts one or more processes on the local computer.</span></span>

## <span data-ttu-id="ea0b3-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ea0b3-105">SYNTAX</span></span>

### <span data-ttu-id="ea0b3-106">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="ea0b3-106">Default (Default)</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-Credential <PSCredential>]
 [-WorkingDirectory <String>] [-LoadUserProfile] [-NoNewWindow] [-PassThru]
 [-RedirectStandardError <String>] [-RedirectStandardInput <String>]
 [-RedirectStandardOutput <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-UseNewEnvironment]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ea0b3-107">UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="ea0b3-107">UseShellExecute</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-WorkingDirectory <String>]
 [-PassThru] [-Verb <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="ea0b3-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ea0b3-108">DESCRIPTION</span></span>

<span data-ttu-id="ea0b3-109">`Start-Process`Cmdleten startar en eller flera processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-109">The `Start-Process` cmdlet starts one or more processes on the local computer.</span></span> <span data-ttu-id="ea0b3-110">Som standard `Start-Process` skapar en ny process som ärver alla miljövariabler som definieras i den aktuella processen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-110">By default, `Start-Process` creates a new process that inherits all the environment variables that are defined in the current process.</span></span>

<span data-ttu-id="ea0b3-111">Ange det program som körs i processen genom att ange en körbar fil eller skript fil, eller en fil som kan öppnas med hjälp av ett program på datorn.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-111">To specify the program that runs in the process, enter an executable file or script file, or a file that can be opened by using a program on the computer.</span></span> <span data-ttu-id="ea0b3-112">Om du anger en fil som inte är körbar `Start-Process` startar programmet som är associerat med filen, ungefär som- `Invoke-Item` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-112">If you specify a non-executable file, `Start-Process` starts the program that is associated with the file, similar to the `Invoke-Item` cmdlet.</span></span>

<span data-ttu-id="ea0b3-113">Du kan använda parametrarna för `Start-Process` för att ange alternativ, till exempel att läsa in en användar profil, starta processen i ett nytt fönster eller använda alternativa autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-113">You can use the parameters of `Start-Process` to specify options, such as loading a user profile, starting the process in a new window, or using alternate credentials.</span></span>

## <span data-ttu-id="ea0b3-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ea0b3-114">EXAMPLES</span></span>

### <span data-ttu-id="ea0b3-115">Exempel 1: starta en process som använder standardvärden</span><span class="sxs-lookup"><span data-stu-id="ea0b3-115">Example 1: Start a process that uses default values</span></span>

<span data-ttu-id="ea0b3-116">I det här exemplet startas en process som använder `Sort.exe` filen i den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-116">This example starts a process that uses the `Sort.exe` file in the current folder.</span></span> <span data-ttu-id="ea0b3-117">Kommandot använder alla standardvärden, inklusive standard fönster format, arbetsmapp och autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-117">The command uses all of the default values, including the default window style, working folder, and credentials.</span></span>

```powershell
Start-Process -FilePath "sort.exe"
```

### <span data-ttu-id="ea0b3-118">Exempel 2: skriva ut en textfil</span><span class="sxs-lookup"><span data-stu-id="ea0b3-118">Example 2: Print a text file</span></span>

<span data-ttu-id="ea0b3-119">I det här exemplet startas en process som skriver ut `C:\PS-Test\MyFile.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-119">This example starts a process that prints the `C:\PS-Test\MyFile.txt` file.</span></span>

```powershell
Start-Process -FilePath "myfile.txt" -WorkingDirectory "C:\PS-Test" -Verb Print
```

### <span data-ttu-id="ea0b3-120">Exempel 3: starta en process för att sortera objekt till en ny fil</span><span class="sxs-lookup"><span data-stu-id="ea0b3-120">Example 3: Start a process to sort items to a new file</span></span>

<span data-ttu-id="ea0b3-121">I det här exemplet startas en process som sorterar objekten i `Testsort.txt` filen och returnerar de sorterade objekten i `Sorted.txt` filerna.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-121">This example starts a process that sorts items in the `Testsort.txt` file and returns the sorted items in the `Sorted.txt` files.</span></span> <span data-ttu-id="ea0b3-122">Eventuella fel skrivs till `SortError.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-122">Any errors are written to the `SortError.txt` file.</span></span>

```powershell
Start-Process -FilePath "Sort.exe" -RedirectStandardInput "Testsort.txt" -RedirectStandardOutput "Sorted.txt" -RedirectStandardError "SortError.txt" -UseNewEnvironment
```

<span data-ttu-id="ea0b3-123">Parametern **UseNewEnvironment** anger att processen körs med egna miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-123">The **UseNewEnvironment** parameter specifies that the process runs with its own environment variables.</span></span>

### <span data-ttu-id="ea0b3-124">Exempel 4: starta en process i ett maximerat fönster</span><span class="sxs-lookup"><span data-stu-id="ea0b3-124">Example 4: Start a process in a maximized window</span></span>

<span data-ttu-id="ea0b3-125">Det här exemplet startar `Notepad.exe` processen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-125">This example starts the `Notepad.exe` process.</span></span> <span data-ttu-id="ea0b3-126">Det maximerar fönstret och bevarar fönstret tills processen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-126">It maximizes the window and retains the window until the process completes.</span></span>

```powershell
Start-Process -FilePath "notepad" -Wait -WindowStyle Maximized
```

### <span data-ttu-id="ea0b3-127">Exempel 5: starta PowerShell som administratör</span><span class="sxs-lookup"><span data-stu-id="ea0b3-127">Example 5: Start PowerShell as an administrator</span></span>

<span data-ttu-id="ea0b3-128">Det här exemplet startar PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="ea0b3-128">This example starts PowerShell by using the **Run as administrator** option.</span></span>

```powershell
Start-Process -FilePath "powershell" -Verb RunAs
```

### <span data-ttu-id="ea0b3-129">Exempel 6: använda olika verb för att starta en process</span><span class="sxs-lookup"><span data-stu-id="ea0b3-129">Example 6: Using different verbs to start a process</span></span>

<span data-ttu-id="ea0b3-130">Det här exemplet visar hur du hittar de verb som kan användas när du startar en process.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-130">This example shows how to find the verbs that can be used when starting a process.</span></span> <span data-ttu-id="ea0b3-131">Tillgängliga verb bestäms av fil namns tillägget för filen som körs i processen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-131">The available verbs are determined by the filename extension of the file that runs in the process.</span></span>

```powershell
$startExe = New-Object System.Diagnostics.ProcessStartInfo -Args PowerShell.exe
$startExe.verbs
```

```Output
open
runas
runasuser
```

<span data-ttu-id="ea0b3-132">Exemplet använder `New-Object` för att skapa ett **system. Diagnostics. ProcessStartInfo** -objekt för **PowerShell.exe**, den fil som körs i PowerShell-processen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-132">The example uses `New-Object` to create a **System.Diagnostics.ProcessStartInfo** object for **PowerShell.exe**, the file that runs in the PowerShell process.</span></span> <span data-ttu-id="ea0b3-133">Egenskapen **verb** för **ProcessStartInfo** -objektet visar att du kan använda **Open** -och **runas** -verben med `PowerShell.exe` eller med en process som kör en `.exe` fil.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-133">The **Verbs** property of the **ProcessStartInfo** object shows that you can use the **Open** and **RunAs** verbs with `PowerShell.exe`, or with any process that runs a `.exe` file.</span></span>

### <span data-ttu-id="ea0b3-134">Exempel 7: ange argument för processen</span><span class="sxs-lookup"><span data-stu-id="ea0b3-134">Example 7: Specifying arguments to the process</span></span>

<span data-ttu-id="ea0b3-135">Båda kommandona startar Windows kommando tolken och utfärdar ett `dir` kommando i `Program Files` mappen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-135">Both commands start the Windows command interpreter, issuing a `dir` command on the `Program Files` folder.</span></span> <span data-ttu-id="ea0b3-136">Eftersom den här mappnamn innehåller ett blank steg måste värdet omges av Escaped citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-136">Because this foldername contains a space, the value needs surrounded with escaped quotes.</span></span>
<span data-ttu-id="ea0b3-137">Observera att det första kommandot anger en sträng som **argument List**.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-137">Note that the first command specifies a string as **ArgumentList**.</span></span> <span data-ttu-id="ea0b3-138">Det andra kommandot är en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-138">The second command is a string array.</span></span>

```powershell
Start-Process -FilePath "$env:comspec" -ArgumentList "/c dir `"%systemdrive%\program files`""
Start-Process -FilePath "$env:comspec" -ArgumentList "/c","dir","`"%systemdrive%\program files`""
```

### <span data-ttu-id="ea0b3-139">Exempel 8: skapa en frånkopplad process på Linux</span><span class="sxs-lookup"><span data-stu-id="ea0b3-139">Example 8: Create a detached process on Linux</span></span>

<span data-ttu-id="ea0b3-140">I Windows `Start-Process` skapar en oberoende process som förblir igång oberoende av start gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-140">On Windows, `Start-Process` creates an independent process that remains running independently of the launching shell.</span></span> <span data-ttu-id="ea0b3-141">På andra plattformar än Windows-plattformar är den nyligen startade processen kopplad till gränssnittet som startades.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-141">On non-Windows platforms, the newly started process is attached to the shell that launched.</span></span> <span data-ttu-id="ea0b3-142">Om start gränssnittet stängs avbryts den underordnade processen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-142">If the launching shell is closed, the child process is terminated.</span></span>

<span data-ttu-id="ea0b3-143">För att undvika att avsluta den underordnade processen på UNIX-liknande plattformar kan du kombinera `Start-Process` med `nohup` .</span><span class="sxs-lookup"><span data-stu-id="ea0b3-143">To avoid terminating the child process on Unix-like platforms, you can combine `Start-Process` with `nohup`.</span></span> <span data-ttu-id="ea0b3-144">I följande exempel startas en bakgrunds instans av PowerShell på Linux som är aktiv även när du har stängt start sessionen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-144">The following example launches a background instance of PowerShell on Linux that stays alive even after you close the launching session.</span></span> <span data-ttu-id="ea0b3-145">`nohup`Kommandot samlar in utdata i filen `nohup.out` i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-145">The `nohup` command collects output in file `nohup.out` in the current directory.</span></span>

```powershell
# Runs for 2 minutes and appends output to ./nohup.out
Start-Process nohup 'pwsh -noprofile -c "1..120 | % { Write-Host . -NoNewline; sleep 1 }"'
```

<span data-ttu-id="ea0b3-146">I det här exemplet `Start-Process` kör Linux `nohup` -kommandot som startar `pwsh` som en frånkopplad process.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-146">In this example, `Start-Process` is running the Linux `nohup` command, which launches `pwsh` as a detached process.</span></span> <span data-ttu-id="ea0b3-147">Mer information finns på sidan man för [nohup](https://linux.die.net/man/1/nohup).</span><span class="sxs-lookup"><span data-stu-id="ea0b3-147">For more information, see the man page for [nohup](https://linux.die.net/man/1/nohup).</span></span>

## <span data-ttu-id="ea0b3-148">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ea0b3-148">PARAMETERS</span></span>

### <span data-ttu-id="ea0b3-149">– Argument List</span><span class="sxs-lookup"><span data-stu-id="ea0b3-149">-ArgumentList</span></span>

<span data-ttu-id="ea0b3-150">Anger parametrar eller parameter värden som ska användas när denna cmdlet startar processen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-150">Specifies parameters or parameter values to use when this cmdlet starts the process.</span></span> <span data-ttu-id="ea0b3-151">Argument kan godkännas som en enskild sträng med argumenten avgränsade med blank steg eller som en matris med strängar avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-151">Arguments can be accepted as a single string with the arguments separated by spaces, or as an array of strings separated by commas.</span></span>

<span data-ttu-id="ea0b3-152">Om parametrar eller parameter värden innehåller ett blank steg måste de omges av Escaped dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-152">If parameters or parameter values contain a space, they need to be surrounded with escaped double quotes.</span></span> <span data-ttu-id="ea0b3-153">Mer information finns i [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="ea0b3-153">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="ea0b3-154">-Credential</span><span class="sxs-lookup"><span data-stu-id="ea0b3-154">-Credential</span></span>

<span data-ttu-id="ea0b3-155">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-155">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="ea0b3-156">Som standard använder cmdleten autentiseringsuppgifterna för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-156">By default, the cmdlet uses the credentials of the current user.</span></span>

<span data-ttu-id="ea0b3-157">Ange ett användar namn, till exempel **user01** eller **Domain01\User01**, eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-157">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="ea0b3-158">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-158">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="ea0b3-159">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="ea0b3-159">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="ea0b3-160">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="ea0b3-160">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="ea0b3-161">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="ea0b3-161">-FilePath</span></span>

<span data-ttu-id="ea0b3-162">Anger den valfria sökvägen och fil namnet för det program som körs i processen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-162">Specifies the optional path and filename of the program that runs in the process.</span></span> <span data-ttu-id="ea0b3-163">Ange namnet på en körbar fil eller ett dokument, till exempel en `.txt` eller `.doc` -fil, som är associerad med ett program på datorn.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-163">Enter the name of an executable file or of a document, such as a `.txt` or `.doc` file, that is associated with a program on the computer.</span></span> <span data-ttu-id="ea0b3-164">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-164">This parameter is required.</span></span>

<span data-ttu-id="ea0b3-165">Om du bara anger ett fil namn använder du parametern **WorkingDirectory** för att ange sökvägen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-165">If you specify only a filename, use the **WorkingDirectory** parameter to specify the path.</span></span>

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

### <span data-ttu-id="ea0b3-166">– LoadUserProfile</span><span class="sxs-lookup"><span data-stu-id="ea0b3-166">-LoadUserProfile</span></span>

<span data-ttu-id="ea0b3-167">Anger att denna cmdlet läser in Windows-användarprofilen som lagras i `HKEY_USERS` register nyckeln för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-167">Indicates that this cmdlet loads the Windows user profile stored in the `HKEY_USERS` registry key for the current user.</span></span> <span data-ttu-id="ea0b3-168">Parametern gäller inte för system som inte är Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-168">The parameter does not apply for non-Windows systems.</span></span>

<span data-ttu-id="ea0b3-169">Den här parametern påverkar inte PowerShell-profilerna.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-169">This parameter does not affect the PowerShell profiles.</span></span> <span data-ttu-id="ea0b3-170">Mer information finns i [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ea0b3-170">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

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

### <span data-ttu-id="ea0b3-171">-NoNewWindow</span><span class="sxs-lookup"><span data-stu-id="ea0b3-171">-NoNewWindow</span></span>

<span data-ttu-id="ea0b3-172">Starta den nya processen i det aktuella konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-172">Start the new process in the current console window.</span></span> <span data-ttu-id="ea0b3-173">Som standard öppnas ett nytt fönster i PowerShell i Windows.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-173">By default on Windows, PowerShell opens a new window.</span></span> <span data-ttu-id="ea0b3-174">På andra datorer än Windows-system får du aldrig ett nytt terminalfönster.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-174">On non-Windows systems, you never get a new terminal window.</span></span>

<span data-ttu-id="ea0b3-175">Du kan inte använda parametrarna **NoNewWindow** och **windowstyle** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-175">You cannot use the **NoNewWindow** and **WindowStyle** parameters in the same command.</span></span>

<span data-ttu-id="ea0b3-176">Parametern gäller inte för system som inte är Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-176">The parameter does not apply for non-Windows systems.</span></span>

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

### <span data-ttu-id="ea0b3-177">– PassThru</span><span class="sxs-lookup"><span data-stu-id="ea0b3-177">-PassThru</span></span>

<span data-ttu-id="ea0b3-178">Returnerar ett process objekt för varje process som cmdleten startade.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-178">Returns a process object for each process that the cmdlet started.</span></span> <span data-ttu-id="ea0b3-179">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-179">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="ea0b3-180">-RedirectStandardError</span><span class="sxs-lookup"><span data-stu-id="ea0b3-180">-RedirectStandardError</span></span>

<span data-ttu-id="ea0b3-181">Anger en fil.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-181">Specifies a file.</span></span> <span data-ttu-id="ea0b3-182">Den här cmdleten skickar eventuella fel som genereras av processen till en fil som du anger.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-182">This cmdlet sends any errors generated by the process to a file that you specify.</span></span>
<span data-ttu-id="ea0b3-183">Ange sökväg och fil namn.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-183">Enter the path and filename.</span></span> <span data-ttu-id="ea0b3-184">Som standard visas felen i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-184">By default, the errors are displayed in the console.</span></span>

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

### <span data-ttu-id="ea0b3-185">-RedirectStandardInput</span><span class="sxs-lookup"><span data-stu-id="ea0b3-185">-RedirectStandardInput</span></span>

<span data-ttu-id="ea0b3-186">Anger en fil.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-186">Specifies a file.</span></span> <span data-ttu-id="ea0b3-187">Denna cmdlet läser indata från den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-187">This cmdlet reads input from the specified file.</span></span> <span data-ttu-id="ea0b3-188">Ange sökväg och fil namn för indatafilen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-188">Enter the path and filename of the input file.</span></span> <span data-ttu-id="ea0b3-189">Som standard hämtas den inmatade processen från tangent bordet.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-189">By default, the process gets its input from the keyboard.</span></span>

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

### <span data-ttu-id="ea0b3-190">-RedirectStandardOutput</span><span class="sxs-lookup"><span data-stu-id="ea0b3-190">-RedirectStandardOutput</span></span>

<span data-ttu-id="ea0b3-191">Anger en fil.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-191">Specifies a file.</span></span> <span data-ttu-id="ea0b3-192">Denna cmdlet skickar de utdata som genereras av processen till en fil som du anger.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-192">This cmdlet sends the output generated by the process to a file that you specify.</span></span>
<span data-ttu-id="ea0b3-193">Ange sökväg och fil namn.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-193">Enter the path and filename.</span></span> <span data-ttu-id="ea0b3-194">Som standard visas utdata i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-194">By default, the output is displayed in the console.</span></span>

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

### <span data-ttu-id="ea0b3-195">-UseNewEnvironment</span><span class="sxs-lookup"><span data-stu-id="ea0b3-195">-UseNewEnvironment</span></span>

<span data-ttu-id="ea0b3-196">Anger att denna cmdlet använder nya miljövariabler som har angetts för processen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-196">Indicates that this cmdlet uses new environment variables specified for the process.</span></span> <span data-ttu-id="ea0b3-197">Som standard körs den startade processen med miljövariablerna som ärvts från den överordnade processen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-197">By default, the started process runs with the environment variables inherited from the parent process.</span></span>

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

### <span data-ttu-id="ea0b3-198">-Verb</span><span class="sxs-lookup"><span data-stu-id="ea0b3-198">-Verb</span></span>

<span data-ttu-id="ea0b3-199">Anger ett verb som ska användas när denna cmdlet startar processen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-199">Specifies a verb to use when this cmdlet starts the process.</span></span> <span data-ttu-id="ea0b3-200">Vilka verb som är tillgängliga beror på fil namns tillägget för filen som körs i processen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-200">The verbs that are available are determined by the filename extension of the file that runs in the process.</span></span>

<span data-ttu-id="ea0b3-201">I följande tabell visas verben för vissa vanliga process fil typer.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-201">The following table shows the verbs for some common process file types.</span></span>

| <span data-ttu-id="ea0b3-202">Filtyp</span><span class="sxs-lookup"><span data-stu-id="ea0b3-202">File type</span></span> |                <span data-ttu-id="ea0b3-203">Verb</span><span class="sxs-lookup"><span data-stu-id="ea0b3-203">Verbs</span></span>                |
| --------- | ----------------------------------- |
| <span data-ttu-id="ea0b3-204">.cmd</span><span class="sxs-lookup"><span data-stu-id="ea0b3-204">.cmd</span></span>      | <span data-ttu-id="ea0b3-205">Redigera, öppna, skriva ut, RunAs, RunAsUser</span><span class="sxs-lookup"><span data-stu-id="ea0b3-205">Edit, Open, Print, RunAs, RunAsUser</span></span> |
| <span data-ttu-id="ea0b3-206">.exe</span><span class="sxs-lookup"><span data-stu-id="ea0b3-206">.exe</span></span>      | <span data-ttu-id="ea0b3-207">Öppna, RunAs, RunAsUser</span><span class="sxs-lookup"><span data-stu-id="ea0b3-207">Open, RunAs, RunAsUser</span></span>              |
| <span data-ttu-id="ea0b3-208">.txt</span><span class="sxs-lookup"><span data-stu-id="ea0b3-208">.txt</span></span>      | <span data-ttu-id="ea0b3-209">Öppna, skriva ut, PrintTo</span><span class="sxs-lookup"><span data-stu-id="ea0b3-209">Open, Print, PrintTo</span></span>                |
| <span data-ttu-id="ea0b3-210">.wav</span><span class="sxs-lookup"><span data-stu-id="ea0b3-210">.wav</span></span>      | <span data-ttu-id="ea0b3-211">Öppna, spela upp</span><span class="sxs-lookup"><span data-stu-id="ea0b3-211">Open, Play</span></span>                          |

<span data-ttu-id="ea0b3-212">Om du vill hitta de verb som kan användas med den fil som körs i en process använder du `New-Object` cmdleten för att skapa ett **system. Diagnostics. ProcessStartInfo** -objekt för filen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-212">To find the verbs that can be used with the file that runs in a process, use the `New-Object` cmdlet to create a **System.Diagnostics.ProcessStartInfo** object for the file.</span></span> <span data-ttu-id="ea0b3-213">Tillgängliga verb finns i egenskapen **verbs** i **ProcessStartInfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-213">The available verbs are in the **Verbs** property of the **ProcessStartInfo** object.</span></span> <span data-ttu-id="ea0b3-214">Mer information finns i exemplen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-214">For details, see the examples.</span></span>

<span data-ttu-id="ea0b3-215">Parametern gäller inte för system som inte är Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-215">The parameter does not apply for non-Windows systems.</span></span>

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

### <span data-ttu-id="ea0b3-216">– Vänta</span><span class="sxs-lookup"><span data-stu-id="ea0b3-216">-Wait</span></span>

<span data-ttu-id="ea0b3-217">Anger att denna cmdlet väntar på att den angivna processen och dess underordnade ska slutföras innan fler indatatyper accepteras.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-217">Indicates that this cmdlet waits for the specified process and its descendants to complete before accepting more input.</span></span> <span data-ttu-id="ea0b3-218">Den här parametern förhindrar kommando tolken eller behåller fönstret tills processerna har slutförts.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-218">This parameter suppresses the command prompt or retains the window until the processes finish.</span></span>

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

### <span data-ttu-id="ea0b3-219">– WindowStyle</span><span class="sxs-lookup"><span data-stu-id="ea0b3-219">-WindowStyle</span></span>

<span data-ttu-id="ea0b3-220">Anger status för det fönster som används för den nya processen.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-220">Specifies the state of the window that is used for the new process.</span></span> <span data-ttu-id="ea0b3-221">De acceptabla värdena för den här parametern är: **Normal**, **dold**, **minimerad** och **maximerad**.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-221">The acceptable values for this parameter are: **Normal**, **Hidden**, **Minimized**, and **Maximized**.</span></span> <span data-ttu-id="ea0b3-222">Standardvärdet är **Normal**.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-222">The default value is **Normal**.</span></span>

<span data-ttu-id="ea0b3-223">Du kan inte använda parametrarna **windowstyle** och **NoNewWindow** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-223">You cannot use the **WindowStyle** and **NoNewWindow** parameters in the same command.</span></span>

<span data-ttu-id="ea0b3-224">Parametern gäller inte för system som inte är Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-224">The parameter does not apply for non-Windows systems.</span></span>

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

### <span data-ttu-id="ea0b3-225">– WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="ea0b3-225">-WorkingDirectory</span></span>

<span data-ttu-id="ea0b3-226">Anger den plats som den nya processen ska starta i.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-226">Specifies the location that the new process should start in.</span></span> <span data-ttu-id="ea0b3-227">Standardvärdet är platsen för den körbara filen eller det dokument som startas.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-227">The default is the location of the executable file or document being started.</span></span> <span data-ttu-id="ea0b3-228">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-228">Wildcards are not supported.</span></span> <span data-ttu-id="ea0b3-229">Sök vägs namnet får inte innehålla tecken som tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-229">The path name must not contain characters that would be interpreted as wildcards.</span></span>

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

### <span data-ttu-id="ea0b3-230">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ea0b3-230">-Confirm</span></span>

<span data-ttu-id="ea0b3-231">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-231">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ea0b3-232">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ea0b3-232">-WhatIf</span></span>

<span data-ttu-id="ea0b3-233">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-233">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ea0b3-234">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-234">The cmdlet is not run.</span></span>

<span data-ttu-id="ea0b3-235">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-235">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="ea0b3-236">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ea0b3-236">CommonParameters</span></span>

<span data-ttu-id="ea0b3-237">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-237">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ea0b3-238">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ea0b3-238">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ea0b3-239">INDATA</span><span class="sxs-lookup"><span data-stu-id="ea0b3-239">INPUTS</span></span>

### <span data-ttu-id="ea0b3-240">Inga</span><span class="sxs-lookup"><span data-stu-id="ea0b3-240">None</span></span>

<span data-ttu-id="ea0b3-241">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-241">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="ea0b3-242">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ea0b3-242">OUTPUTS</span></span>

### <span data-ttu-id="ea0b3-243">Ingen, system. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="ea0b3-243">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="ea0b3-244">Denna cmdlet genererar ett **system. Diagnostics. process** -objekt, om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="ea0b3-244">This cmdlet generates a **System.Diagnostics.Process** object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="ea0b3-245">Annars returnerar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-245">Otherwise, this cmdlet does not return any output.</span></span>

## <span data-ttu-id="ea0b3-246">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ea0b3-246">NOTES</span></span>

- <span data-ttu-id="ea0b3-247">Denna cmdlet implementeras med hjälp av metoden **Start** i klassen **system. Diagnostics. process** .</span><span class="sxs-lookup"><span data-stu-id="ea0b3-247">This cmdlet is implemented by using the **Start** method of the **System.Diagnostics.Process** class.</span></span> <span data-ttu-id="ea0b3-248">Mer information om den här metoden finns i [metoden process. start](/dotnet/api/system.diagnostics.process.start#overloads).</span><span class="sxs-lookup"><span data-stu-id="ea0b3-248">For more information about this method, see [Process.Start Method](/dotnet/api/system.diagnostics.process.start#overloads).</span></span>

- <span data-ttu-id="ea0b3-249">När du använder **UseNewEnvironment** i Windows, börjar den nya processen bara att innehålla de standard miljö variabler som definierats för **dator** omfånget.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-249">On Windows, when you use **UseNewEnvironment**, the new process starts only containing the default environment variables defined for the **Machine** scope.</span></span> <span data-ttu-id="ea0b3-250">Detta har samma effekt som `$env:USERNAME` är inställd på **system**.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-250">This has the side affect that the `$env:USERNAME` is set to **SYSTEM**.</span></span> <span data-ttu-id="ea0b3-251">Ingen av variablerna från **användar** omfånget ingår.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-251">None of the variables from the **User** scope are included.</span></span>

- <span data-ttu-id="ea0b3-252">I Windows är det vanligaste användnings fallet för `Start-Process` att använda parametern **wait** för att blockera förloppet tills den nya processen avslutas.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-252">On Windows, the most common use case for `Start-Process` is to use the **Wait** parameter to block progress until the new process exits.</span></span> <span data-ttu-id="ea0b3-253">På andra datorer än Windows-system behövs detta sällan eftersom standard beteendet för kommando rads program är lika med `Start-Process -Wait` .</span><span class="sxs-lookup"><span data-stu-id="ea0b3-253">On non-Windows system, this is rarely needed since the default behavior for command-line applications is equivalent to `Start-Process -Wait`.</span></span>

- <span data-ttu-id="ea0b3-254">När `Start-Process` du använder på andra datorer än Windows-system får du aldrig ett nytt terminalfönster.</span><span class="sxs-lookup"><span data-stu-id="ea0b3-254">When using `Start-Process` on non-Windows systems, you never get a new terminal window.</span></span>

## <span data-ttu-id="ea0b3-255">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ea0b3-255">RELATED LINKS</span></span>

[<span data-ttu-id="ea0b3-256">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="ea0b3-256">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="ea0b3-257">Fel sökning – process</span><span class="sxs-lookup"><span data-stu-id="ea0b3-257">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="ea0b3-258">Hämta process</span><span class="sxs-lookup"><span data-stu-id="ea0b3-258">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="ea0b3-259">Start-Service</span><span class="sxs-lookup"><span data-stu-id="ea0b3-259">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="ea0b3-260">Stoppa – process</span><span class="sxs-lookup"><span data-stu-id="ea0b3-260">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="ea0b3-261">Vänta-process</span><span class="sxs-lookup"><span data-stu-id="ea0b3-261">Wait-Process</span></span>](Wait-Process.md)
