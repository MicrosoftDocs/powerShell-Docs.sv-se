---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Process
ms.openlocfilehash: b6147b35a8818cf448b1e23f5458550d1c6e5c50
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2020
ms.locfileid: "93268827"
---
# <span data-ttu-id="faa99-103">Start-Process</span><span class="sxs-lookup"><span data-stu-id="faa99-103">Start-Process</span></span>

## <span data-ttu-id="faa99-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="faa99-104">SYNOPSIS</span></span>
<span data-ttu-id="faa99-105">Startar en eller flera processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="faa99-105">Starts one or more processes on the local computer.</span></span>

## <span data-ttu-id="faa99-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="faa99-106">SYNTAX</span></span>

### <span data-ttu-id="faa99-107">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="faa99-107">Default (Default)</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-Credential <PSCredential>]
 [-WorkingDirectory <String>] [-LoadUserProfile] [-NoNewWindow] [-PassThru]
 [-RedirectStandardError <String>] [-RedirectStandardInput <String>]
 [-RedirectStandardOutput <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-UseNewEnvironment]
 [<CommonParameters>]
```

### <span data-ttu-id="faa99-108">UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="faa99-108">UseShellExecute</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-WorkingDirectory <String>]
 [-PassThru] [-Verb <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [<CommonParameters>]
```

## <span data-ttu-id="faa99-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="faa99-109">DESCRIPTION</span></span>

<span data-ttu-id="faa99-110">`Start-Process`Cmdleten startar en eller flera processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="faa99-110">The `Start-Process` cmdlet starts one or more processes on the local computer.</span></span> <span data-ttu-id="faa99-111">Som standard `Start-Process` skapar en ny process som ärver alla miljövariabler som definieras i den aktuella processen.</span><span class="sxs-lookup"><span data-stu-id="faa99-111">By default, `Start-Process` creates a new process that inherits all the environment variables that are defined in the current process.</span></span>

<span data-ttu-id="faa99-112">Ange det program som körs i processen genom att ange en körbar fil eller skript fil, eller en fil som kan öppnas med hjälp av ett program på datorn.</span><span class="sxs-lookup"><span data-stu-id="faa99-112">To specify the program that runs in the process, enter an executable file or script file, or a file that can be opened by using a program on the computer.</span></span> <span data-ttu-id="faa99-113">Om du anger en fil som inte är körbar `Start-Process` startar programmet som är associerat med filen, ungefär som- `Invoke-Item` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="faa99-113">If you specify a non-executable file, `Start-Process` starts the program that is associated with the file, similar to the `Invoke-Item` cmdlet.</span></span>

<span data-ttu-id="faa99-114">Du kan använda parametrarna för `Start-Process` för att ange alternativ, till exempel att läsa in en användar profil, starta processen i ett nytt fönster eller använda alternativa autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="faa99-114">You can use the parameters of `Start-Process` to specify options, such as loading a user profile, starting the process in a new window, or using alternate credentials.</span></span>

## <span data-ttu-id="faa99-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="faa99-115">EXAMPLES</span></span>

### <span data-ttu-id="faa99-116">Exempel 1: starta en process som använder standardvärden</span><span class="sxs-lookup"><span data-stu-id="faa99-116">Example 1: Start a process that uses default values</span></span>

<span data-ttu-id="faa99-117">I det här exemplet startas en process som använder `Sort.exe` filen i den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="faa99-117">This example starts a process that uses the `Sort.exe` file in the current folder.</span></span> <span data-ttu-id="faa99-118">Kommandot använder alla standardvärden, inklusive standard fönster format, arbetsmapp och autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="faa99-118">The command uses all of the default values, including the default window style, working folder, and credentials.</span></span>

```powershell
Start-Process -FilePath "sort.exe"
```

### <span data-ttu-id="faa99-119">Exempel 2: skriva ut en textfil</span><span class="sxs-lookup"><span data-stu-id="faa99-119">Example 2: Print a text file</span></span>

<span data-ttu-id="faa99-120">I det här exemplet startas en process som skriver ut `C:\PS-Test\MyFile.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="faa99-120">This example starts a process that prints the `C:\PS-Test\MyFile.txt` file.</span></span>

```powershell
Start-Process -FilePath "myfile.txt" -WorkingDirectory "C:\PS-Test" -Verb Print
```

### <span data-ttu-id="faa99-121">Exempel 3: starta en process för att sortera objekt till en ny fil</span><span class="sxs-lookup"><span data-stu-id="faa99-121">Example 3: Start a process to sort items to a new file</span></span>

<span data-ttu-id="faa99-122">I det här exemplet startas en process som sorterar objekten i `Testsort.txt` filen och returnerar de sorterade objekten i `Sorted.txt` filerna.</span><span class="sxs-lookup"><span data-stu-id="faa99-122">This example starts a process that sorts items in the `Testsort.txt` file and returns the sorted items in the `Sorted.txt` files.</span></span> <span data-ttu-id="faa99-123">Eventuella fel skrivs till `SortError.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="faa99-123">Any errors are written to the `SortError.txt` file.</span></span>

```powershell
Start-Process -FilePath "Sort.exe" -RedirectStandardInput "Testsort.txt" -RedirectStandardOutput "Sorted.txt" -RedirectStandardError "SortError.txt" -UseNewEnvironment
```

<span data-ttu-id="faa99-124">Parametern **UseNewEnvironment** anger att processen körs med egna miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="faa99-124">The **UseNewEnvironment** parameter specifies that the process runs with its own environment variables.</span></span>

### <span data-ttu-id="faa99-125">Exempel 4: starta en process i ett maximerat fönster</span><span class="sxs-lookup"><span data-stu-id="faa99-125">Example 4: Start a process in a maximized window</span></span>

<span data-ttu-id="faa99-126">Det här exemplet startar `Notepad.exe` processen.</span><span class="sxs-lookup"><span data-stu-id="faa99-126">This example starts the `Notepad.exe` process.</span></span> <span data-ttu-id="faa99-127">Det maximerar fönstret och bevarar fönstret tills processen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="faa99-127">It maximizes the window and retains the window until the process completes.</span></span>

```powershell
Start-Process -FilePath "notepad" -Wait -WindowStyle Maximized
```

### <span data-ttu-id="faa99-128">Exempel 5: starta PowerShell som administratör</span><span class="sxs-lookup"><span data-stu-id="faa99-128">Example 5: Start PowerShell as an administrator</span></span>

<span data-ttu-id="faa99-129">Det här exemplet startar PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="faa99-129">This example starts PowerShell by using the **Run as administrator** option.</span></span>

```powershell
Start-Process -FilePath "powershell" -Verb RunAs
```

### <span data-ttu-id="faa99-130">Exempel 6: använda olika verb för att starta en process</span><span class="sxs-lookup"><span data-stu-id="faa99-130">Example 6: Using different verbs to start a process</span></span>

<span data-ttu-id="faa99-131">Det här exemplet visar hur du hittar de verb som kan användas när du startar en process.</span><span class="sxs-lookup"><span data-stu-id="faa99-131">This example shows how to find the verbs that can be used when starting a process.</span></span> <span data-ttu-id="faa99-132">Tillgängliga verb bestäms av fil namns tillägget för filen som körs i processen.</span><span class="sxs-lookup"><span data-stu-id="faa99-132">The available verbs are determined by the filename extension of the file that runs in the process.</span></span>

```powershell
$startExe = New-Object System.Diagnostics.ProcessStartInfo -Args PowerShell.exe
$startExe.verbs
```

```Output
open
runas
runasuser
```

<span data-ttu-id="faa99-133">Exemplet använder `New-Object` för att skapa ett **system. Diagnostics. ProcessStartInfo** -objekt för **PowerShell.exe** , den fil som körs i PowerShell-processen.</span><span class="sxs-lookup"><span data-stu-id="faa99-133">The example uses `New-Object` to create a **System.Diagnostics.ProcessStartInfo** object for **PowerShell.exe** , the file that runs in the PowerShell process.</span></span> <span data-ttu-id="faa99-134">Egenskapen **verb** för **ProcessStartInfo** -objektet visar att du kan använda **Open** -och **runas** -verben med `PowerShell.exe` eller med en process som kör en `.exe` fil.</span><span class="sxs-lookup"><span data-stu-id="faa99-134">The **Verbs** property of the **ProcessStartInfo** object shows that you can use the **Open** and **RunAs** verbs with `PowerShell.exe`, or with any process that runs a `.exe` file.</span></span>

### <span data-ttu-id="faa99-135">Exempel 7: ange argument för processen</span><span class="sxs-lookup"><span data-stu-id="faa99-135">Example 7: Specifying arguments to the process</span></span>

<span data-ttu-id="faa99-136">Båda kommandona startar Windows kommando tolken och utfärdar ett `dir` kommando i `Program Files` mappen.</span><span class="sxs-lookup"><span data-stu-id="faa99-136">Both commands start the Windows command interpreter, issuing a `dir` command on the `Program Files` folder.</span></span> <span data-ttu-id="faa99-137">Eftersom den här mappnamn innehåller ett blank steg måste värdet omges av Escaped citat tecken.</span><span class="sxs-lookup"><span data-stu-id="faa99-137">Because this foldername contains a space, the value needs surrounded with escaped quotes.</span></span>
<span data-ttu-id="faa99-138">Observera att det första kommandot anger en sträng som **argument List**.</span><span class="sxs-lookup"><span data-stu-id="faa99-138">Note that the first command specifies a string as **ArgumentList**.</span></span> <span data-ttu-id="faa99-139">Det andra kommandot är en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="faa99-139">The second command is a string array.</span></span>

```powershell
Start-Process -FilePath "$env:comspec" -ArgumentList "/c dir `"%systemdrive%\program files`""
Start-Process -FilePath "$env:comspec" -ArgumentList "/c","dir","`"%systemdrive%\program files`""
```

## <span data-ttu-id="faa99-140">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="faa99-140">PARAMETERS</span></span>

### <span data-ttu-id="faa99-141">– Argument List</span><span class="sxs-lookup"><span data-stu-id="faa99-141">-ArgumentList</span></span>

<span data-ttu-id="faa99-142">Anger parametrar eller parameter värden som ska användas när denna cmdlet startar processen.</span><span class="sxs-lookup"><span data-stu-id="faa99-142">Specifies parameters or parameter values to use when this cmdlet starts the process.</span></span> <span data-ttu-id="faa99-143">Argument kan godkännas som en enskild sträng med argumenten avgränsade med blank steg eller som en matris med strängar avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="faa99-143">Arguments can be accepted as a single string with the arguments separated by spaces, or as an array of strings separated by commas.</span></span>

<span data-ttu-id="faa99-144">Om parametrar eller parameter värden innehåller ett blank steg måste de omges av Escaped dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="faa99-144">If parameters or parameter values contain a space, they need to be surrounded with escaped double quotes.</span></span> <span data-ttu-id="faa99-145">Mer information finns i [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="faa99-145">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="faa99-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="faa99-146">-Credential</span></span>

<span data-ttu-id="faa99-147">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="faa99-147">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="faa99-148">Som standard använder cmdleten autentiseringsuppgifterna för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="faa99-148">By default, the cmdlet uses the credentials of the current user.</span></span>

<span data-ttu-id="faa99-149">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="faa99-149">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="faa99-150">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="faa99-150">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="faa99-151">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="faa99-151">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="faa99-152">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="faa99-152">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="faa99-153">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="faa99-153">-FilePath</span></span>

<span data-ttu-id="faa99-154">Anger den valfria sökvägen och fil namnet för det program som körs i processen.</span><span class="sxs-lookup"><span data-stu-id="faa99-154">Specifies the optional path and filename of the program that runs in the process.</span></span> <span data-ttu-id="faa99-155">Ange namnet på en körbar fil eller ett dokument, till exempel en `.txt` eller `.doc` -fil, som är associerad med ett program på datorn.</span><span class="sxs-lookup"><span data-stu-id="faa99-155">Enter the name of an executable file or of a document, such as a `.txt` or `.doc` file, that is associated with a program on the computer.</span></span> <span data-ttu-id="faa99-156">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="faa99-156">This parameter is required.</span></span>

<span data-ttu-id="faa99-157">Om du bara anger ett fil namn använder du parametern **WorkingDirectory** för att ange sökvägen.</span><span class="sxs-lookup"><span data-stu-id="faa99-157">If you specify only a filename, use the **WorkingDirectory** parameter to specify the path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="faa99-158">– LoadUserProfile</span><span class="sxs-lookup"><span data-stu-id="faa99-158">-LoadUserProfile</span></span>

<span data-ttu-id="faa99-159">Anger att denna cmdlet läser in Windows-användarprofilen som lagras i `HKEY_USERS` register nyckeln för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="faa99-159">Indicates that this cmdlet loads the Windows user profile stored in the `HKEY_USERS` registry key for the current user.</span></span>

<span data-ttu-id="faa99-160">Den här parametern påverkar inte PowerShell-profilerna.</span><span class="sxs-lookup"><span data-stu-id="faa99-160">This parameter does not affect the PowerShell profiles.</span></span> <span data-ttu-id="faa99-161">Mer information finns i [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="faa99-161">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

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

### <span data-ttu-id="faa99-162">-NoNewWindow</span><span class="sxs-lookup"><span data-stu-id="faa99-162">-NoNewWindow</span></span>

<span data-ttu-id="faa99-163">Starta den nya processen i det aktuella konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="faa99-163">Start the new process in the current console window.</span></span> <span data-ttu-id="faa99-164">Som standard öppnas ett nytt fönster i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="faa99-164">By default PowerShell opens a new window.</span></span>

<span data-ttu-id="faa99-165">Du kan inte använda parametrarna **NoNewWindow** och **windowstyle** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="faa99-165">You cannot use the **NoNewWindow** and **WindowStyle** parameters in the same command.</span></span>

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

### <span data-ttu-id="faa99-166">– PassThru</span><span class="sxs-lookup"><span data-stu-id="faa99-166">-PassThru</span></span>

<span data-ttu-id="faa99-167">Returnerar ett process objekt för varje process som cmdleten startade.</span><span class="sxs-lookup"><span data-stu-id="faa99-167">Returns a process object for each process that the cmdlet started.</span></span> <span data-ttu-id="faa99-168">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="faa99-168">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="faa99-169">-RedirectStandardError</span><span class="sxs-lookup"><span data-stu-id="faa99-169">-RedirectStandardError</span></span>

<span data-ttu-id="faa99-170">Anger en fil.</span><span class="sxs-lookup"><span data-stu-id="faa99-170">Specifies a file.</span></span> <span data-ttu-id="faa99-171">Den här cmdleten skickar eventuella fel som genereras av processen till en fil som du anger.</span><span class="sxs-lookup"><span data-stu-id="faa99-171">This cmdlet sends any errors generated by the process to a file that you specify.</span></span>
<span data-ttu-id="faa99-172">Ange sökväg och fil namn.</span><span class="sxs-lookup"><span data-stu-id="faa99-172">Enter the path and filename.</span></span> <span data-ttu-id="faa99-173">Som standard visas felen i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="faa99-173">By default, the errors are displayed in the console.</span></span>

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

### <span data-ttu-id="faa99-174">-RedirectStandardInput</span><span class="sxs-lookup"><span data-stu-id="faa99-174">-RedirectStandardInput</span></span>

<span data-ttu-id="faa99-175">Anger en fil.</span><span class="sxs-lookup"><span data-stu-id="faa99-175">Specifies a file.</span></span> <span data-ttu-id="faa99-176">Denna cmdlet läser indata från den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="faa99-176">This cmdlet reads input from the specified file.</span></span> <span data-ttu-id="faa99-177">Ange sökväg och fil namn för indatafilen.</span><span class="sxs-lookup"><span data-stu-id="faa99-177">Enter the path and filename of the input file.</span></span> <span data-ttu-id="faa99-178">Som standard hämtas den inmatade processen från tangent bordet.</span><span class="sxs-lookup"><span data-stu-id="faa99-178">By default, the process gets its input from the keyboard.</span></span>

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

### <span data-ttu-id="faa99-179">-RedirectStandardOutput</span><span class="sxs-lookup"><span data-stu-id="faa99-179">-RedirectStandardOutput</span></span>

<span data-ttu-id="faa99-180">Anger en fil.</span><span class="sxs-lookup"><span data-stu-id="faa99-180">Specifies a file.</span></span> <span data-ttu-id="faa99-181">Denna cmdlet skickar de utdata som genereras av processen till en fil som du anger.</span><span class="sxs-lookup"><span data-stu-id="faa99-181">This cmdlet sends the output generated by the process to a file that you specify.</span></span>
<span data-ttu-id="faa99-182">Ange sökväg och fil namn.</span><span class="sxs-lookup"><span data-stu-id="faa99-182">Enter the path and filename.</span></span> <span data-ttu-id="faa99-183">Som standard visas utdata i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="faa99-183">By default, the output is displayed in the console.</span></span>

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

### <span data-ttu-id="faa99-184">-UseNewEnvironment</span><span class="sxs-lookup"><span data-stu-id="faa99-184">-UseNewEnvironment</span></span>

<span data-ttu-id="faa99-185">Anger att denna cmdlet använder nya miljövariabler som har angetts för processen.</span><span class="sxs-lookup"><span data-stu-id="faa99-185">Indicates that this cmdlet uses new environment variables specified for the process.</span></span> <span data-ttu-id="faa99-186">Som standard körs den startade processen med miljövariablerna som ärvts från den överordnade processen.</span><span class="sxs-lookup"><span data-stu-id="faa99-186">By default, the started process runs with the environment variables inherited from the parent process.</span></span>

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

### <span data-ttu-id="faa99-187">-Verb</span><span class="sxs-lookup"><span data-stu-id="faa99-187">-Verb</span></span>

<span data-ttu-id="faa99-188">Anger ett verb som ska användas när denna cmdlet startar processen.</span><span class="sxs-lookup"><span data-stu-id="faa99-188">Specifies a verb to use when this cmdlet starts the process.</span></span> <span data-ttu-id="faa99-189">Vilka verb som är tillgängliga beror på fil namns tillägget för filen som körs i processen.</span><span class="sxs-lookup"><span data-stu-id="faa99-189">The verbs that are available are determined by the filename extension of the file that runs in the process.</span></span>

<span data-ttu-id="faa99-190">I följande tabell visas verben för vissa vanliga process fil typer.</span><span class="sxs-lookup"><span data-stu-id="faa99-190">The following table shows the verbs for some common process file types.</span></span>

| <span data-ttu-id="faa99-191">Filtyp</span><span class="sxs-lookup"><span data-stu-id="faa99-191">File type</span></span> |                <span data-ttu-id="faa99-192">Verb</span><span class="sxs-lookup"><span data-stu-id="faa99-192">Verbs</span></span>                |
| --------- | ----------------------------------- |
| <span data-ttu-id="faa99-193">.cmd</span><span class="sxs-lookup"><span data-stu-id="faa99-193">.cmd</span></span>      | <span data-ttu-id="faa99-194">Redigera, öppna, skriva ut, RunAs, RunAsUser</span><span class="sxs-lookup"><span data-stu-id="faa99-194">Edit, Open, Print, RunAs, RunAsUser</span></span> |
| <span data-ttu-id="faa99-195">.exe</span><span class="sxs-lookup"><span data-stu-id="faa99-195">.exe</span></span>      | <span data-ttu-id="faa99-196">Öppna, RunAs, RunAsUser</span><span class="sxs-lookup"><span data-stu-id="faa99-196">Open, RunAs, RunAsUser</span></span>              |
| <span data-ttu-id="faa99-197">.txt</span><span class="sxs-lookup"><span data-stu-id="faa99-197">.txt</span></span>      | <span data-ttu-id="faa99-198">Öppna, skriva ut, PrintTo</span><span class="sxs-lookup"><span data-stu-id="faa99-198">Open, Print, PrintTo</span></span>                |
| <span data-ttu-id="faa99-199">.wav</span><span class="sxs-lookup"><span data-stu-id="faa99-199">.wav</span></span>      | <span data-ttu-id="faa99-200">Öppna, spela upp</span><span class="sxs-lookup"><span data-stu-id="faa99-200">Open, Play</span></span>                          |

<span data-ttu-id="faa99-201">Om du vill hitta de verb som kan användas med den fil som körs i en process använder du `New-Object` cmdleten för att skapa ett **system. Diagnostics. ProcessStartInfo** -objekt för filen.</span><span class="sxs-lookup"><span data-stu-id="faa99-201">To find the verbs that can be used with the file that runs in a process, use the `New-Object` cmdlet to create a **System.Diagnostics.ProcessStartInfo** object for the file.</span></span> <span data-ttu-id="faa99-202">Tillgängliga verb finns i egenskapen **verbs** i **ProcessStartInfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="faa99-202">The available verbs are in the **Verbs** property of the **ProcessStartInfo** object.</span></span> <span data-ttu-id="faa99-203">Mer information finns i exemplen.</span><span class="sxs-lookup"><span data-stu-id="faa99-203">For details, see the examples.</span></span>

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

### <span data-ttu-id="faa99-204">– Vänta</span><span class="sxs-lookup"><span data-stu-id="faa99-204">-Wait</span></span>

<span data-ttu-id="faa99-205">Anger att denna cmdlet väntar på att den angivna processen och dess underordnade ska slutföras innan fler indatatyper accepteras.</span><span class="sxs-lookup"><span data-stu-id="faa99-205">Indicates that this cmdlet waits for the specified process and its descendants to complete before accepting more input.</span></span> <span data-ttu-id="faa99-206">Den här parametern förhindrar kommando tolken eller behåller fönstret tills processerna har slutförts.</span><span class="sxs-lookup"><span data-stu-id="faa99-206">This parameter suppresses the command prompt or retains the window until the processes finish.</span></span>

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

### <span data-ttu-id="faa99-207">– WindowStyle</span><span class="sxs-lookup"><span data-stu-id="faa99-207">-WindowStyle</span></span>

<span data-ttu-id="faa99-208">Anger status för det fönster som används för den nya processen.</span><span class="sxs-lookup"><span data-stu-id="faa99-208">Specifies the state of the window that is used for the new process.</span></span> <span data-ttu-id="faa99-209">De acceptabla värdena för den här parametern är: **Normal** , **dold** , **minimerad** och **maximerad**.</span><span class="sxs-lookup"><span data-stu-id="faa99-209">The acceptable values for this parameter are: **Normal** , **Hidden** , **Minimized** , and **Maximized**.</span></span> <span data-ttu-id="faa99-210">Standardvärdet är **Normal**.</span><span class="sxs-lookup"><span data-stu-id="faa99-210">The default value is **Normal**.</span></span>

<span data-ttu-id="faa99-211">Du kan inte använda parametrarna **windowstyle** och **NoNewWindow** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="faa99-211">You cannot use the **WindowStyle** and **NoNewWindow** parameters in the same command.</span></span>

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

### <span data-ttu-id="faa99-212">– WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="faa99-212">-WorkingDirectory</span></span>

<span data-ttu-id="faa99-213">Anger den plats som den nya processen ska starta i.</span><span class="sxs-lookup"><span data-stu-id="faa99-213">Specifies the location that the new process should start in.</span></span> <span data-ttu-id="faa99-214">Standardvärdet är platsen för den körbara filen eller det dokument som startas.</span><span class="sxs-lookup"><span data-stu-id="faa99-214">The default is the location of the executable file or document being started.</span></span> <span data-ttu-id="faa99-215">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="faa99-215">Wildcards are not supported.</span></span> <span data-ttu-id="faa99-216">Sök vägs namnet får inte innehålla tecken som tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="faa99-216">The path name must not contain characters that would be interpreted as wildcards.</span></span>

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

### <span data-ttu-id="faa99-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="faa99-217">CommonParameters</span></span>

<span data-ttu-id="faa99-218">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="faa99-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="faa99-219">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="faa99-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="faa99-220">INDATA</span><span class="sxs-lookup"><span data-stu-id="faa99-220">INPUTS</span></span>

### <span data-ttu-id="faa99-221">Inget</span><span class="sxs-lookup"><span data-stu-id="faa99-221">None</span></span>

<span data-ttu-id="faa99-222">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="faa99-222">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="faa99-223">UTDATA</span><span class="sxs-lookup"><span data-stu-id="faa99-223">OUTPUTS</span></span>

### <span data-ttu-id="faa99-224">Ingen, system. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="faa99-224">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="faa99-225">Denna cmdlet genererar ett **system. Diagnostics. process** -objekt, om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="faa99-225">This cmdlet generates a **System.Diagnostics.Process** object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="faa99-226">Annars returnerar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="faa99-226">Otherwise, this cmdlet does not return any output.</span></span>

## <span data-ttu-id="faa99-227">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="faa99-227">NOTES</span></span>

- <span data-ttu-id="faa99-228">Denna cmdlet implementeras med hjälp av metoden **Start** i klassen **system. Diagnostics. process** .</span><span class="sxs-lookup"><span data-stu-id="faa99-228">This cmdlet is implemented by using the **Start** method of the **System.Diagnostics.Process** class.</span></span> <span data-ttu-id="faa99-229">Mer information om den här metoden finns i [metoden process. start](/dotnet/api/system.diagnostics.process.start#overloads).</span><span class="sxs-lookup"><span data-stu-id="faa99-229">For more information about this method, see [Process.Start Method](/dotnet/api/system.diagnostics.process.start#overloads).</span></span>

- <span data-ttu-id="faa99-230">När du använder **UseNewEnvironment** i Windows, börjar den nya processen bara att innehålla de standard miljö variabler som definierats för **dator** omfånget.</span><span class="sxs-lookup"><span data-stu-id="faa99-230">On Windows, when you use **UseNewEnvironment** , the new process starts only containing the default environment variables defined for the **Machine** scope.</span></span> <span data-ttu-id="faa99-231">Detta har samma effekt som `$env:USERNAME` är inställd på **system**.</span><span class="sxs-lookup"><span data-stu-id="faa99-231">This has the side affect that the `$env:USERNAME` is set to **SYSTEM**.</span></span> <span data-ttu-id="faa99-232">Ingen av variablerna från **användar** omfånget ingår.</span><span class="sxs-lookup"><span data-stu-id="faa99-232">None of the variables from the **User** scope are included.</span></span>

## <span data-ttu-id="faa99-233">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="faa99-233">RELATED LINKS</span></span>

[<span data-ttu-id="faa99-234">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="faa99-234">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="faa99-235">Fel sökning – process</span><span class="sxs-lookup"><span data-stu-id="faa99-235">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="faa99-236">Hämta process</span><span class="sxs-lookup"><span data-stu-id="faa99-236">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="faa99-237">Start-Service</span><span class="sxs-lookup"><span data-stu-id="faa99-237">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="faa99-238">Stoppa – process</span><span class="sxs-lookup"><span data-stu-id="faa99-238">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="faa99-239">Vänta-process</span><span class="sxs-lookup"><span data-stu-id="faa99-239">Wait-Process</span></span>](Wait-Process.md)
