---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Command
ms.openlocfilehash: 652ff321ea1c6507915be9748715604166207200
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268214"
---
# <span data-ttu-id="e7ee8-103">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="e7ee8-103">Invoke-Command</span></span>

## <span data-ttu-id="e7ee8-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e7ee8-104">SYNOPSIS</span></span>
<span data-ttu-id="e7ee8-105">Kör kommandon på lokala datorer och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-105">Runs commands on local and remote computers.</span></span>

## <span data-ttu-id="e7ee8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e7ee8-106">SYNTAX</span></span>

### <span data-ttu-id="e7ee8-107">InProcess (standard)</span><span class="sxs-lookup"><span data-stu-id="e7ee8-107">InProcess (Default)</span></span>

```
Invoke-Command [-ScriptBlock] <ScriptBlock> [-NoNewScope] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="e7ee8-108">Session</span><span class="sxs-lookup"><span data-stu-id="e7ee8-108">Session</span></span>

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="e7ee8-109">FilePathRunspace</span><span class="sxs-lookup"><span data-stu-id="e7ee8-109">FilePathRunspace</span></span>

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="e7ee8-110">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="e7ee8-110">FilePathComputerName</span></span>

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-FilePath] <String> [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="e7ee8-111">ComputerName</span><span class="sxs-lookup"><span data-stu-id="e7ee8-111">ComputerName</span></span>

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="e7ee8-112">URI</span><span class="sxs-lookup"><span data-stu-id="e7ee8-112">Uri</span></span>

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="e7ee8-113">FilePathUri</span><span class="sxs-lookup"><span data-stu-id="e7ee8-113">FilePathUri</span></span>

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="e7ee8-114">VMId</span><span class="sxs-lookup"><span data-stu-id="e7ee8-114">VMId</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="e7ee8-115">VMName</span><span class="sxs-lookup"><span data-stu-id="e7ee8-115">VMName</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="e7ee8-116">FilePathVMId</span><span class="sxs-lookup"><span data-stu-id="e7ee8-116">FilePathVMId</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="e7ee8-117">FilePathVMName</span><span class="sxs-lookup"><span data-stu-id="e7ee8-117">FilePathVMName</span></span>

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="e7ee8-118">Hålla</span><span class="sxs-lookup"><span data-stu-id="e7ee8-118">ContainerId</span></span>

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RunAsAdministrator] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="e7ee8-119">FilePathContainerId</span><span class="sxs-lookup"><span data-stu-id="e7ee8-119">FilePathContainerId</span></span>

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RunAsAdministrator] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

## <span data-ttu-id="e7ee8-120">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e7ee8-120">DESCRIPTION</span></span>

<span data-ttu-id="e7ee8-121">`Invoke-Command`Cmdleten kör kommandon på en lokal eller fjärran sluten dator och returnerar alla utdata från kommandona, inklusive fel.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-121">The `Invoke-Command` cmdlet runs commands on a local or remote computer and returns all output from the commands, including errors.</span></span> <span data-ttu-id="e7ee8-122">Med ett enda `Invoke-Command` kommando kan du köra kommandon på flera datorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-122">Using a single `Invoke-Command` command, you can run commands on multiple computers.</span></span>

<span data-ttu-id="e7ee8-123">Om du vill köra ett enda kommando på en fjärrdator använder du parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-123">To run a single command on a remote computer, use the **ComputerName** parameter.</span></span> <span data-ttu-id="e7ee8-124">Om du vill köra en serie relaterade kommandon som delar data använder du `New-PSSession` cmdleten för att skapa en **PSSession** (en permanent anslutning) på fjärrdatorn och använder sedan parametern **session** för `Invoke-Command` att köra kommandot i **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-124">To run a series of related commands that share data, use the `New-PSSession` cmdlet to create a **PSSession** (a persistent connection) on the remote computer, and then use the **Session** parameter of `Invoke-Command` to run the command in the **PSSession**.</span></span> <span data-ttu-id="e7ee8-125">Om du vill köra ett kommando i en frånkopplad session använder du parametern **InDisconnectedSession** .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-125">To run a command in a disconnected session, use the **InDisconnectedSession** parameter.</span></span> <span data-ttu-id="e7ee8-126">Om du vill köra ett kommando i ett bakgrunds jobb använder du parametern **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-126">To run a command in a background job, use the **AsJob** parameter.</span></span>

<span data-ttu-id="e7ee8-127">Du kan också använda `Invoke-Command` på en lokal dator till ett-skript block som ett kommando.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-127">You can also use `Invoke-Command` on a local computer to a script block as a command.</span></span> <span data-ttu-id="e7ee8-128">PowerShell kör skript blocket direkt i en underordnad omfattning för det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-128">PowerShell runs the script block immediately in a child scope of the current scope.</span></span>

<span data-ttu-id="e7ee8-129">Innan `Invoke-Command` du använder för att köra kommandon på en fjärrdator läser du [about_Remote](./About/about_Remote.md).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-129">Before using `Invoke-Command` to run commands on a remote computer, read [about_Remote](./About/about_Remote.md).</span></span>

<span data-ttu-id="e7ee8-130">I vissa kod exempel används ihopbuntning för att minska linje längden.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-130">Some code samples use splatting to reduce the line length.</span></span> <span data-ttu-id="e7ee8-131">Mer information finns i [about_Splatting](./About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-131">For more information, see [about_Splatting](./About/about_Splatting.md).</span></span>

## <span data-ttu-id="e7ee8-132">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e7ee8-132">EXAMPLES</span></span>

### <span data-ttu-id="e7ee8-133">Exempel 1: kör ett skript på en server</span><span class="sxs-lookup"><span data-stu-id="e7ee8-133">Example 1: Run a script on a server</span></span>

<span data-ttu-id="e7ee8-134">I det här exemplet körs `Test.ps1` skriptet på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-134">This example runs the `Test.ps1` script on the Server01 computer.</span></span>

```powershell
Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
```

<span data-ttu-id="e7ee8-135">Parametern **sökväg** anger ett skript som finns på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-135">The **FilePath** parameter specifies a script that is located on the local computer.</span></span> <span data-ttu-id="e7ee8-136">Skriptet körs på fjärrdatorn och resultatet returneras till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-136">The script runs on the remote computer and the results are returned to the local computer.</span></span>

### <span data-ttu-id="e7ee8-137">Exempel 2: köra ett kommando på en fjärrserver</span><span class="sxs-lookup"><span data-stu-id="e7ee8-137">Example 2: Run a command on a remote server</span></span>

<span data-ttu-id="e7ee8-138">I det här exemplet körs ett `Get-Culture` kommando på Server01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-138">This example runs a `Get-Culture` command on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
```

<span data-ttu-id="e7ee8-139">Parametern **computername** anger namnet på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-139">The **ComputerName** parameter specifies the name of the remote computer.</span></span> <span data-ttu-id="e7ee8-140">Parametern **Credential** används för att köra kommandot i säkerhets kontexten för Domain01\User01, en användare som har behörighet att köra kommandon.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-140">The **Credential** parameter is used to run the command in the security context of Domain01\User01, a user who has permission to run commands.</span></span> <span data-ttu-id="e7ee8-141">Parametern **script block** anger kommandot som ska köras på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-141">The **ScriptBlock** parameter specifies the command to be run on the remote computer.</span></span>

<span data-ttu-id="e7ee8-142">Som svar begär PowerShell lösen ordet och en autentiseringsmetod för user01-kontot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-142">In response, PowerShell requests the password and an authentication method for the User01 account.</span></span>
<span data-ttu-id="e7ee8-143">Den kör sedan kommandot på Server01-datorn och returnerar resultatet.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-143">It then runs the command on the Server01 computer and returns the result.</span></span>

### <span data-ttu-id="e7ee8-144">Exempel 3: köra ett kommando i en permanent anslutning</span><span class="sxs-lookup"><span data-stu-id="e7ee8-144">Example 3: Run a command in a persistent connection</span></span>

<span data-ttu-id="e7ee8-145">I det här exemplet körs samma `Get-Culture` kommando i en session med en beständig anslutning på fjärrdatorn med namnet Server02.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-145">This example runs the same `Get-Culture` command in a session, using a persistent connection, on the remote computer named Server02.</span></span>

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

<span data-ttu-id="e7ee8-146">`New-PSSession`Cmdleten skapar en session på Server02-fjärrdatorn och sparar den i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-146">The `New-PSSession` cmdlet creates a session on the Server02 remote computer and saves it in the `$s` variable.</span></span> <span data-ttu-id="e7ee8-147">Normalt skapar du bara en session när du kör en serie kommandon på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-147">Typically, you create a session only when you run a series of commands on the remote computer.</span></span>

<span data-ttu-id="e7ee8-148">`Invoke-Command`Cmdleten kör `Get-Culture` kommandot på Server02.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-148">The `Invoke-Command` cmdlet runs the `Get-Culture` command on Server02.</span></span> <span data-ttu-id="e7ee8-149">Parametern **session** anger sessionen som sparats i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-149">The **Session** parameter specifies the session saved in the `$s` variable.</span></span>

<span data-ttu-id="e7ee8-150">Som svar kör PowerShell kommandot i sessionen på den Server02 datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-150">In response, PowerShell runs the command in the session on the Server02 computer.</span></span>

### <span data-ttu-id="e7ee8-151">Exempel 4: Använd en session för att köra en serie kommandon som delar data</span><span class="sxs-lookup"><span data-stu-id="e7ee8-151">Example 4: Use a session to run a series of commands that share data</span></span>

<span data-ttu-id="e7ee8-152">I det här exemplet jämförs effekterna av att använda **computername** och **sessionscookies** för `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-152">This example compares the effects of using **ComputerName** and **Session** parameters of `Invoke-Command`.</span></span> <span data-ttu-id="e7ee8-153">Det visar hur du använder en session för att köra en serie kommandon som delar samma data.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-153">It shows how to use a session to run a series of commands that share the same data.</span></span>

```powershell
Invoke-Command -ComputerName Server02 -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -ComputerName Server02 -ScriptBlock {$p.VirtualMemorySize}
$s = New-PSSession -ComputerName Server02
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -Session $s -ScriptBlock {$p.VirtualMemorySize}
```

```Output
17930240
```

<span data-ttu-id="e7ee8-154">De två första kommandona använder parametern **computername** för `Invoke-Command` att köra kommandon på Server02-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-154">The first two commands use the **ComputerName** parameter of `Invoke-Command` to run commands on the Server02 remote computer.</span></span> <span data-ttu-id="e7ee8-155">Det första kommandot använder `Get-Process` cmdleten för att hämta PowerShell-processen på fjärrdatorn och spara den i `$p` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-155">The first command uses the `Get-Process` cmdlet to get the PowerShell process on the remote computer and to save it in the `$p` variable.</span></span> <span data-ttu-id="e7ee8-156">Det andra kommandot hämtar värdet för **VirtualMemorySize** -egenskapen för PowerShell-processen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-156">The second command gets the value of the **VirtualMemorySize** property of the PowerShell process.</span></span>

<span data-ttu-id="e7ee8-157">När du använder parametern **computername** skapar PowerShell en ny session för att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-157">When you use the **ComputerName** parameter, PowerShell creates a new session to run the command.</span></span>
<span data-ttu-id="e7ee8-158">Sessionen stängs när kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-158">The session is closed when the command completes.</span></span> <span data-ttu-id="e7ee8-159">`$p`Variabeln skapades i en anslutning, men den finns inte i anslutningen som skapats för det andra kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-159">The `$p` variable was created in one connection, but it doesn't exist in the connection created for the second command.</span></span>

<span data-ttu-id="e7ee8-160">Problemet löses genom att skapa en beständig session på fjärrdatorn och köra båda kommandona i samma session.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-160">The problem is solved by creating a persistent session on the remote computer, then running both of the commands in the same session.</span></span>

<span data-ttu-id="e7ee8-161">`New-PSSession`Cmdleten skapar en beständig session på datorn Server02 och sparar sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-161">The `New-PSSession` cmdlet creates a persistent session on the computer Server02 and saves the session in the `$s` variable.</span></span> <span data-ttu-id="e7ee8-162">De `Invoke-Command` rader som följer använder parametern **session** för att köra båda kommandona i samma session.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-162">The `Invoke-Command` lines that follow use the **Session** parameter to run both of the commands in the same session.</span></span> <span data-ttu-id="e7ee8-163">Eftersom båda kommandona körs i samma session `$p` är värdet fortfarande aktivt.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-163">Since both commands run in the same session, the `$p` value remains active.</span></span>

### <span data-ttu-id="e7ee8-164">Exempel 5: Ange ett kommando som lagras i en lokal variabel</span><span class="sxs-lookup"><span data-stu-id="e7ee8-164">Example 5: Enter a command stored in a local variable</span></span>

<span data-ttu-id="e7ee8-165">Det här exemplet visar hur du skapar ett kommando som lagras som ett skript block i en lokal variabel.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-165">This example shows how to create a command that is stored as a script block in a local variable.</span></span>
<span data-ttu-id="e7ee8-166">När skript blocket sparas i en lokal variabel kan du ange variabeln som värde för parametern **script block** .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-166">When the script block is saved in a local variable, you can specify the variable as the value of the **ScriptBlock** parameter.</span></span>

```powershell
$command = { Get-EventLog -LogName "Windows PowerShell" |
  Where-Object {$_.Message -like "*certificate*"} }
Invoke-Command -ComputerName S1, S2 -ScriptBlock $command
```

<span data-ttu-id="e7ee8-167">`$command`Variabeln lagrar `Get-EventLog` kommandot som är formaterat som ett skript block.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-167">The `$command` variable stores the `Get-EventLog` command that's formatted as a script block.</span></span> <span data-ttu-id="e7ee8-168">`Invoke-Command`Kör kommandot som lagras på `$command` på datorerna S1 och S2.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-168">The `Invoke-Command` runs the command stored in `$command` on the S1 and S2 remote computers.</span></span>

### <span data-ttu-id="e7ee8-169">Exempel 6: kör ett enda kommando på flera datorer</span><span class="sxs-lookup"><span data-stu-id="e7ee8-169">Example 6: Run a single command on several computers</span></span>

<span data-ttu-id="e7ee8-170">Det här exemplet visar hur du kan använda `Invoke-Command` för att köra ett enda kommando på flera datorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-170">This example demonstrates how to use `Invoke-Command` to run a single command on multiple computers.</span></span>

```powershell
$parameters = @{
  ComputerName = "Server01", "Server02", "TST-0143", "localhost"
  ConfigurationName = 'MySession.PowerShell'
  ScriptBlock = { Get-EventLog "Windows PowerShell" }
}
Invoke-Command @parameters
```

<span data-ttu-id="e7ee8-171">Parametern **computername** anger en kommaavgränsad lista med dator namn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-171">The **ComputerName** parameter specifies a comma-separated list of computer names.</span></span> <span data-ttu-id="e7ee8-172">Listan med datorer innehåller värdet localhost, som representerar den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-172">The list of computers includes the localhost value, which represents the local computer.</span></span> <span data-ttu-id="e7ee8-173">Parametern **ConfigurationName** anger en alternativ konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-173">The **ConfigurationName** parameter specifies an alternate session configuration.</span></span> <span data-ttu-id="e7ee8-174">Parametern **script block** körs `Get-EventLog` för att hämta Windows PowerShell-händelseloggen från varje dator.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-174">The **ScriptBlock** parameter runs `Get-EventLog` to get the Windows PowerShell event logs from each computer.</span></span>

### <span data-ttu-id="e7ee8-175">Exempel 7: Hämta versionen av värd programmet på flera datorer</span><span class="sxs-lookup"><span data-stu-id="e7ee8-175">Example 7: Get the version of the host program on multiple computers</span></span>

<span data-ttu-id="e7ee8-176">I det här exemplet hämtas versionen av PowerShell-värd programmet som körs på 200-fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-176">This example gets the version of the PowerShell host program running on 200 remote computers.</span></span>

```powershell
$version = Invoke-Command -ComputerName (Get-Content Machines.txt) -ScriptBlock {(Get-Host).Version}
```

<span data-ttu-id="e7ee8-177">Eftersom endast ett kommando körs behöver du inte skapa beständiga anslutningar till var och en av datorerna.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-177">Because only one command is run, you don't have to create persistent connections to each of the computers.</span></span> <span data-ttu-id="e7ee8-178">I stället använder kommandot **computername** -parametern för att ange datorerna.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-178">Instead, the command uses the **ComputerName** parameter to indicate the computers.</span></span> <span data-ttu-id="e7ee8-179">För att ange datorer använder den `Get-Content` cmdleten för att hämta innehållet i Machine.txt-filen, en fil med dator namn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-179">To specify the computers, it uses the `Get-Content` cmdlet to get the contents of the Machine.txt file, a file of computer names.</span></span>

<span data-ttu-id="e7ee8-180">`Invoke-Command`Cmdleten kör ett `Get-Host` kommando på fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-180">The `Invoke-Command` cmdlet runs a `Get-Host` command on the remote computers.</span></span> <span data-ttu-id="e7ee8-181">Den använder punkt notation för att hämta **versions** egenskapen för PowerShell-värden.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-181">It uses dot notation to get the **Version** property of the PowerShell host.</span></span>

<span data-ttu-id="e7ee8-182">Kommandona körs en i taget.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-182">These commands run one at a time.</span></span> <span data-ttu-id="e7ee8-183">När kommandona har slutförts sparas utdata från alla datorer i `$version` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-183">When the commands complete, the output of the commands from all of the computers is saved in the `$version` variable.</span></span> <span data-ttu-id="e7ee8-184">Utdata innehåller namnet på den dator från vilken data kommer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-184">The output includes the name of the computer from which the data originated.</span></span>

### <span data-ttu-id="e7ee8-185">Exempel 8: köra ett bakgrunds jobb på flera fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="e7ee8-185">Example 8: Run a background job on several remote computers</span></span>

<span data-ttu-id="e7ee8-186">I det här exemplet körs ett kommando på två fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-186">This example runs a command on two remote computers.</span></span> <span data-ttu-id="e7ee8-187">`Invoke-Command`Kommandot använder parametern **AsJob** så att kommandot körs som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-187">The `Invoke-Command` command uses the **AsJob** parameter so that the command runs as a background job.</span></span> <span data-ttu-id="e7ee8-188">Kommandona körs på fjärrdatorerna, men jobbet finns på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-188">The commands run on the remote computers, but the job exists on the local computer.</span></span> <span data-ttu-id="e7ee8-189">Resultaten överförs till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-189">The results are transmitted to the local computer.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
Invoke-Command -Session $s -ScriptBlock {Get-EventLog system} -AsJob
```

```Output
Id   Name    State      HasMoreData   Location           Command
---  ----    -----      -----         -----------        ---------------
1    Job1    Running    True          Server01,Server02  Get-EventLog system
```

```powershell
$j = Get-Job
$j | Format-List -Property *
```

```Output
HasMoreData   : True
StatusMessage :
Location      : Server01,Server02
Command       : Get-EventLog system
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : e124bb59-8cb2-498b-a0d2-2e07d4e030ca
Id            : 1
Name          : Job1
ChildJobs     : {Job2, Job3}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :
```

```powershell
$results = $j | Receive-Job
```

<span data-ttu-id="e7ee8-190">`New-PSSession`Cmdleten skapar sessioner på fjärrdatorerna Server01 och Server02.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-190">The `New-PSSession` cmdlet creates sessions on the Server01 and Server02 remote computers.</span></span> <span data-ttu-id="e7ee8-191">`Invoke-Command`Cmdleten kör ett bakgrunds jobb i varje session.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-191">The `Invoke-Command` cmdlet runs a background job in each of the sessions.</span></span> <span data-ttu-id="e7ee8-192">Kommandot använder parametern **AsJob** för att köra kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-192">The command uses the **AsJob** parameter to run the command as a background job.</span></span> <span data-ttu-id="e7ee8-193">Det här kommandot returnerar ett jobb objekt som innehåller två underordnade jobb objekt, ett för varje jobb som körs på de två fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-193">This command returns a job object that contains two child job objects, one for each of the jobs run on the two remote computers.</span></span>

<span data-ttu-id="e7ee8-194">`Get-Job`Kommandot sparar jobbobjektet i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-194">The `Get-Job` command saves the job object in the `$j` variable.</span></span> <span data-ttu-id="e7ee8-195">`$j`Variabeln skickas sedan till `Format-List` cmdleten för att visa alla egenskaper för jobbobjektet i en lista.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-195">The `$j` variable is then piped to the `Format-List` cmdlet to display all properties of the job object in a list.</span></span> <span data-ttu-id="e7ee8-196">Det sista kommandot hämtar resultatet av jobben.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-196">The last command gets the results of the jobs.</span></span> <span data-ttu-id="e7ee8-197">Det rör jobbobjektet i- `$j` `Receive-Job` cmdleten och lagrar resultatet i `$results` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-197">It pipes the job object in `$j` to the `Receive-Job` cmdlet and stores the results in the `$results` variable.</span></span>

### <span data-ttu-id="e7ee8-198">Exempel 9: inkludera lokala variabler i en kommando körning på en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="e7ee8-198">Example 9: Include local variables in a command run on a remote computer</span></span>

<span data-ttu-id="e7ee8-199">Det här exemplet visar hur du tar med värdena för lokala variabler i en kommando körning på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-199">This example shows how to include the values of local variables in a command run on a remote computer.</span></span> <span data-ttu-id="e7ee8-200">Kommandot använder `Using` omfångs modifieraren för att identifiera en lokal variabel i ett fjärran slutet kommando.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-200">The command uses the `Using` scope modifier to identify a local variable in a remote command.</span></span> <span data-ttu-id="e7ee8-201">Som standard antas alla variabler definieras i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-201">By default, all variables are assumed to be defined in the remote session.</span></span> <span data-ttu-id="e7ee8-202">`Using`Omfångs modifieraren introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-202">The `Using` scope modifier was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="e7ee8-203">Mer information om `Using` omfångs modifieraren finns i [about_Remote_Variables](./About/about_Remote_Variables.md) och [about_Scopes](./about/about_scopes.md).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-203">For more information about the `Using` scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md) and [about_Scopes](./about/about_scopes.md).</span></span>

```powershell
$Log = "Windows PowerShell"
Invoke-Command -ComputerName Server01 -ScriptBlock { Get-EventLog -LogName $Using:Log -Newest 10 }
```

<span data-ttu-id="e7ee8-204">`$Log`Variabeln lagrar namnet på händelse loggen, Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-204">The `$Log` variable stores the name of the event log, Windows PowerShell.</span></span> <span data-ttu-id="e7ee8-205">`Invoke-Command`Cmdleten körs `Get-EventLog` på Server01 för att hämta de tio senaste händelserna från händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-205">The `Invoke-Command` cmdlet runs `Get-EventLog` on Server01 to get the ten newest events from the event log.</span></span> <span data-ttu-id="e7ee8-206">Värdet för parametern **LogName** är `$Log` variabeln, som föregås av `Using` omfångs modifieraren för att ange att den skapades i den lokala sessionen, inte i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-206">The value of the **LogName** parameter is the `$Log` variable, which is prefixed by the `Using` scope modifier to indicate that it was created in the local session, not in the remote session.</span></span>

### <span data-ttu-id="e7ee8-207">Exempel 10: Dölj dator namnet</span><span class="sxs-lookup"><span data-stu-id="e7ee8-207">Example 10: Hide the computer name</span></span>

<span data-ttu-id="e7ee8-208">I det här exemplet visas effekterna av att använda **HideComputerName** -parametern i `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-208">This example shows the effect of using the **HideComputerName** parameter of `Invoke-Command`.</span></span>
<span data-ttu-id="e7ee8-209">**HideComputerName** ändrar inte objektet som denna cmdlet returnerar.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-209">**HideComputerName** doesn't change the object that this cmdlet returns.</span></span> <span data-ttu-id="e7ee8-210">Den ändrar bara visningen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-210">It changes only the display.</span></span> <span data-ttu-id="e7ee8-211">Du kan fortfarande använda **format** -cmdletar för att visa egenskapen **PsComputerName** för något av de påverkade objekten.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-211">You can still use the **Format** cmdlets to display the **PsComputerName** property of any of the affected objects.</span></span>

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell}
```

```Output
PSComputerName    Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
--------------    -------  ------    -----      ----- -----   ------     --   -----------
S1                575      15        45100      40988   200     4.68     1392 PowerShell
S2                777      14        35100      30988   150     3.68     67   PowerShell
```

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell} -HideComputerName
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
575      15        45100      40988   200     4.68     1392 PowerShell
777      14        35100      30988   150     3.68     67   PowerShell
```

<span data-ttu-id="e7ee8-212">De två första kommandona använder `Invoke-Command` för att köra ett `Get-Process` kommando för PowerShell-processen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-212">The first two commands use `Invoke-Command` to run a `Get-Process` command for the PowerShell process.</span></span> <span data-ttu-id="e7ee8-213">Utdata från det första kommandot innehåller egenskapen **PsComputerName** som innehåller namnet på den dator där kommandot kördes.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-213">The output of the first command includes the **PsComputerName** property, which contains the name of the computer on which the command ran.</span></span> <span data-ttu-id="e7ee8-214">Utdata från det andra kommandot, som använder **HideComputerName** , inkluderar inte kolumnen **PsComputerName** .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-214">The output of the second command, which uses **HideComputerName** , doesn't include the **PsComputerName** column.</span></span>

### <span data-ttu-id="e7ee8-215">Exempel 11: Använd nyckelordet param i ett skript block</span><span class="sxs-lookup"><span data-stu-id="e7ee8-215">Example 11: Use the Param keyword in a script block</span></span>

<span data-ttu-id="e7ee8-216">`Param`Nyckelordet och parametern **argument List** används för att skicka variabel värden till namngivna parametrar i ett-skript block.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-216">The `Param` keyword and the **ArgumentList** parameter are used to pass variable values to named parameters in a script block.</span></span> <span data-ttu-id="e7ee8-217">I det här exemplet visas fil namn som börjar med bokstaven `a` och har `.pdf` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-217">This example displays filenames that begin with the letter `a` and have the `.pdf` extension.</span></span>

<span data-ttu-id="e7ee8-218">Mer information om `Param` nyckelordet finns [about_Language_Keywords](./about/about_language_keywords.md#param).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-218">For more information about the `Param` keyword, see [about_Language_Keywords](./about/about_language_keywords.md#param).</span></span>

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Param ($param1,$param2) Get-ChildItem -Name $param1 -Include $param2 }
    ArgumentList = "a*", "*.pdf"
}
Invoke-Command @parameters
```

```Output
aa.pdf
ab.pdf
ac.pdf
az.pdf
```

<span data-ttu-id="e7ee8-219">`Invoke-Command` använder parametern **script block** som definierar två variabler `$param1` och `$param2` .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-219">`Invoke-Command` uses the **ScriptBlock** parameter that defines two variables, `$param1` and `$param2`.</span></span> <span data-ttu-id="e7ee8-220">`Get-ChildItem` använder namngivna parametrar, **namn** och **Inkludera** med variabel namn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-220">`Get-ChildItem` uses the named parameters, **Name** and **Include** with the variable names.</span></span> <span data-ttu-id="e7ee8-221">**Argument List** skickar värdena till variablerna.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-221">The **ArgumentList** passes the values to the variables.</span></span>

### <span data-ttu-id="e7ee8-222">Exempel 12: Använd $args automatiska variabeln i ett skript block</span><span class="sxs-lookup"><span data-stu-id="e7ee8-222">Example 12: Use the $args automatic variable in a script block</span></span>

<span data-ttu-id="e7ee8-223">Den `$args` automatiska variabeln och parametern **argument List** används för att skicka mat ris värden till parameter positioner i ett-skript block.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-223">The `$args` automatic variable and the **ArgumentList** parameter are used to pass array values to parameter positions in a script block.</span></span> <span data-ttu-id="e7ee8-224">I det här exemplet visas en servers katalog innehåll för `.txt` filer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-224">This example displays a server's directory contents of `.txt` files.</span></span> <span data-ttu-id="e7ee8-225">Parametern `Get-ChildItem` **Path** är position 0 och **filter** parametern är position</span><span class="sxs-lookup"><span data-stu-id="e7ee8-225">The `Get-ChildItem` **Path** parameter is position 0 and the **Filter** parameter is position</span></span>
1.

<span data-ttu-id="e7ee8-226">Mer information om `$args` variabeln finns i [about_Automatic_Variables](./about/about_automatic_variables.md#args)</span><span class="sxs-lookup"><span data-stu-id="e7ee8-226">For more information about the `$args` variable, see [about_Automatic_Variables](./about/about_automatic_variables.md#args)</span></span>

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Get-ChildItem $args[0] $args[1] }
    ArgumentList = "C:\Test", "*.txt*"
}
Invoke-Command @parameters
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           6/12/2019    15:15            128 alog.txt
-a---           7/27/2019    15:16            256 blog.txt
-a---           9/28/2019    17:10             64 zlog.txt
```

<span data-ttu-id="e7ee8-227">`Invoke-Command` använder en **script block** -parameter och `Get-ChildItem` anger `$args[0]` `$args[1]` mat ris värden och.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-227">`Invoke-Command` uses a **ScriptBlock** parameter and `Get-ChildItem` specifies the `$args[0]` and `$args[1]` array values.</span></span> <span data-ttu-id="e7ee8-228">**Argument List** skickar `$args` mat ris värdena till `Get-ChildItem` parameter positionerna för **sökväg** och **filter**.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-228">The **ArgumentList** passes the `$args` array values to the `Get-ChildItem` parameter positions for **Path** and **Filter**.</span></span>

### <span data-ttu-id="e7ee8-229">Exempel 13: kör ett skript på alla datorer som anges i en textfil</span><span class="sxs-lookup"><span data-stu-id="e7ee8-229">Example 13: Run a script on all the computers listed in a text file</span></span>

<span data-ttu-id="e7ee8-230">I det här exemplet används `Invoke-Command` cmdleten för att köra `Sample.ps1` skriptet på alla datorer som anges i `Servers.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-230">This example uses the `Invoke-Command` cmdlet to run the `Sample.ps1` script on all the computers listed in the `Servers.txt` file.</span></span> <span data-ttu-id="e7ee8-231">Kommandot använder parametern **sökväg** för att ange skript filen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-231">The command uses the **FilePath** parameter to specify the script file.</span></span> <span data-ttu-id="e7ee8-232">Med det här kommandot kan du köra skriptet på fjärrdatorer, även om skript filen inte är tillgänglig för fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-232">This command lets you run the script on the remote computers, even if the script file isn't accessible to the remote computers.</span></span>

```powershell
Invoke-Command -ComputerName (Get-Content Servers.txt) -FilePath C:\Scripts\Sample.ps1 -ArgumentList Process, Service
```

<span data-ttu-id="e7ee8-233">När du skickar kommandot kopieras innehållet i `Sample.ps1` filen till ett-skript block och skript blocket körs på varje fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-233">When you submit the command, the content of the `Sample.ps1` file is copied into a script block and the script block is run on each of the remote computers.</span></span> <span data-ttu-id="e7ee8-234">Den här proceduren motsvarar att använda parametern **script block** för att skicka innehållet i skriptet.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-234">This procedure is equivalent to using the **ScriptBlock** parameter to submit the contents of the script.</span></span>

### <span data-ttu-id="e7ee8-235">Exempel 14: köra ett kommando på en fjärrdator med en URI</span><span class="sxs-lookup"><span data-stu-id="e7ee8-235">Example 14: Run a command on a remote computer using a URI</span></span>

<span data-ttu-id="e7ee8-236">Det här exemplet visar hur du kör ett kommando på en fjärrdator som identifieras av en Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-236">This example shows how to run a command on a remote computer that's identified by a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="e7ee8-237">Det här exemplet kör ett `Set-Mailbox` kommando på en fjärran sluten Exchange-Server.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-237">This particular example runs a `Set-Mailbox` command on a remote Exchange server.</span></span>

```powershell
$LiveCred = Get-Credential
$parameters = @{
  ConfigurationName = 'Microsoft.Exchange'
  ConnectionUri = 'https://ps.exchangelabs.com/PowerShell'
  Credential = $LiveCred
  Authentication = 'Basic'
  ScriptBlock = {Set-Mailbox Dan -DisplayName "Dan Park"}
}
Invoke-Command @parameters
```

<span data-ttu-id="e7ee8-238">Den första raden använder `Get-Credential` cmdleten för att lagra Windows Live ID-autentiseringsuppgifter i `$LiveCred` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-238">The first line uses the `Get-Credential` cmdlet to store Windows Live ID credentials in the `$LiveCred` variable.</span></span> <span data-ttu-id="e7ee8-239">PowerShell efterfrågar användaren att ange Windows Live ID-autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-239">PowerShell prompts the user to enter Windows Live ID credentials.</span></span>

<span data-ttu-id="e7ee8-240">`$parameters`Variabeln är en hash-tabell som innehåller de parametrar som ska skickas till `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-240">The `$parameters` variable is a hash table containing the parameters to be passed to the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="e7ee8-241">`Invoke-Command`Cmdleten kör ett `Set-Mailbox` kommando med hjälp av konfigurationen för **Microsoft. Exchange** -sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-241">The `Invoke-Command` cmdlet runs a `Set-Mailbox` command using the **Microsoft.Exchange** session configuration.</span></span> <span data-ttu-id="e7ee8-242">Parametern **ConnectionURI** anger URL: en för Exchange Server-slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-242">The **ConnectionURI** parameter specifies the URL of the Exchange server endpoint.</span></span> <span data-ttu-id="e7ee8-243">Parametern **Credential** anger de autentiseringsuppgifter som lagras i `$LiveCred` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-243">The **Credential** parameter specifies the credentials stored in the `$LiveCred` variable.</span></span> <span data-ttu-id="e7ee8-244">Parametern **AuthenticationMechanism** anger användningen av grundläggande autentisering.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-244">The **AuthenticationMechanism** parameter specifies the use of basic authentication.</span></span> <span data-ttu-id="e7ee8-245">Parametern **script block** anger ett skript block som innehåller kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-245">The **ScriptBlock** parameter specifies a script block that contains the command.</span></span>

### <span data-ttu-id="e7ee8-246">Exempel 15: Använd ett session-alternativ</span><span class="sxs-lookup"><span data-stu-id="e7ee8-246">Example 15: Use a session option</span></span>

<span data-ttu-id="e7ee8-247">Det här exemplet visar hur du skapar och använder en **SessionOption** -parameter.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-247">This example shows how to create and use a **SessionOption** parameter.</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
Invoke-Command -ComputerName server01 -UseSSL -ScriptBlock { Get-HotFix } -SessionOption $so -Credential server01\user01
```

<span data-ttu-id="e7ee8-248">`New-PSSessionOption`Cmdleten skapar ett sessionsobjekt som gör att Fjärrslutpunkten inte verifierar certifikat utfärdaren, kanoniskt namn och återkallnings listor vid utvärdering av inkommande https-anslutningen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-248">The `New-PSSessionOption` cmdlet creates a session option object that causes the remote end not to verify the Certificate Authority, Canonical Name, and Revocation Lists while evaluating the incoming HTTPS connection.</span></span> <span data-ttu-id="e7ee8-249">**SessionOption** -objektet sparas i `$so` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-249">The **SessionOption** object is saved in the `$so` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="e7ee8-250">Att inaktivera de här kontrollerna är användbart för fel sökning, men uppenbarligen inte säkert.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-250">Disabling these checks is convenient for troubleshooting, but obviously not secure.</span></span>

<span data-ttu-id="e7ee8-251">`Invoke-Command`Cmdlet: en kör ett `Get-HotFix` kommando via fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-251">The `Invoke-Command` cmdlet runs a `Get-HotFix` command remotely.</span></span> <span data-ttu-id="e7ee8-252">**SessionOption** -parametern har fått `$so` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-252">The **SessionOption** parameter is given the `$so` variable.</span></span>

### <span data-ttu-id="e7ee8-253">Exempel 16: hantera omdirigering av URI i ett fjärran slutet kommando</span><span class="sxs-lookup"><span data-stu-id="e7ee8-253">Example 16: Manage URI redirection in a remote command</span></span>

<span data-ttu-id="e7ee8-254">Det här exemplet visar hur du använder parametrarna **AllowRedirection** och **SessionOption** för att hantera omdirigering av URI i ett fjärrkommando.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-254">This example shows how to use the **AllowRedirection** and **SessionOption** parameters to manage URI redirection in a remote command.</span></span>

```powershell
$max = New-PSSessionOption -MaximumRedirection 1
$parameters = @{
  ConnectionUri = "https://ps.exchangelabs.com/PowerShell"
  ScriptBlock = { Get-Mailbox dan }
  AllowRedirection = $true
  SessionOption = $max
}
Invoke-Command @parameters
```

<span data-ttu-id="e7ee8-255">`New-PSSessionOption`Cmdleten skapar ett **PSSessionOption** -objekt som sparas i `$max` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-255">The `New-PSSessionOption` cmdlet creates a **PSSessionOption** object that is saved in the `$max` variable.</span></span> <span data-ttu-id="e7ee8-256">Kommandot använder parametern **MaximumRedirection** för att ange egenskapen **MaximumConnectionRedirectionCount** för **PSSessionOption** -objektet till 1.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-256">The command uses the **MaximumRedirection** parameter to set the **MaximumConnectionRedirectionCount** property of the **PSSessionOption** object to 1.</span></span>

<span data-ttu-id="e7ee8-257">`Invoke-Command`Cmdleten kör ett `Get-Mailbox` kommando på en fjärran sluten Microsoft Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-257">The `Invoke-Command` cmdlet runs a `Get-Mailbox` command on a remote Microsoft Exchange Server.</span></span> <span data-ttu-id="e7ee8-258">Parametern **AllowRedirection** ger uttrycklig behörighet att omdirigera anslutningen till en annan slut punkt.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-258">The **AllowRedirection** parameter provides explicit permission to redirect the connection to an alternate endpoint.</span></span> <span data-ttu-id="e7ee8-259">Parametern **SessionOption** använder det sessionsobjekt som lagras i `$max` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-259">The **SessionOption** parameter uses the session object stored in the `$max` variable.</span></span>

<span data-ttu-id="e7ee8-260">Det innebär att om den fjärranslutna datorn som anges av **ConnectionURI** returnerar ett omdirigerings meddelande, omdirigerar PowerShell anslutningen, men om det nya målet returnerar ett annat omdirigerings meddelande, räknas värdet 1 för omdirigeringen och `Invoke-Command` returnerar ett icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-260">As a result, if the remote computer specified by **ConnectionURI** returns a redirection message, PowerShell redirects the connection, but if the new destination returns another redirection message, the redirection count value of 1 is exceeded, and `Invoke-Command` returns a non-terminating error.</span></span>

### <span data-ttu-id="e7ee8-261">Exempel 17: få åtkomst till en nätverks resurs i en fjärran sluten session</span><span class="sxs-lookup"><span data-stu-id="e7ee8-261">Example 17: Access a network share in a remote session</span></span>

<span data-ttu-id="e7ee8-262">Det här exemplet visar hur du kommer åt en nätverks resurs från en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-262">This example shows how to access a network share from a remote session.</span></span> <span data-ttu-id="e7ee8-263">Tre datorer används för att demonstrera exemplet.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-263">Three computers are used to demonstrate the example.</span></span> <span data-ttu-id="e7ee8-264">Server01 är den lokala datorn, Server02 är den fjärranslutna datorn och Net03 innehåller nätverks resursen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-264">Server01 is the local computer, Server02 is the remote computer, and Net03 contains the network share.</span></span> <span data-ttu-id="e7ee8-265">Server01 ansluter till Server02 och Server02 gör sedan ett andra hopp till Net03 för att få åtkomst till nätverks resursen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-265">Server01 connects to Server02, and then Server02 does a second hop to Net03 to access the network share.</span></span> <span data-ttu-id="e7ee8-266">Mer information om hur PowerShell-fjärrkommunikation stöder hopp mellan datorer finns i [göra det andra hoppet i PowerShell-fjärrkommunikation](/powershell/scripting/learn/remoting/ps-remoting-second-hop).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-266">For more information about how PowerShell Remoting supports hops between computers, see [Making the second hop in PowerShell Remoting](/powershell/scripting/learn/remoting/ps-remoting-second-hop).</span></span>

<span data-ttu-id="e7ee8-267">Den obligatoriska CredSSP-delegeringen (Security Support Provider) för autentiseringsuppgifter är aktive rad i klient inställningarna på den lokala datorn och i tjänst inställningarna på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-267">The required Credential Security Support Provider (CredSSP) delegation is enabled in the client settings on the local computer, and in the service settings on the remote computer.</span></span> <span data-ttu-id="e7ee8-268">Om du vill köra kommandona i det här exemplet måste du vara medlem i gruppen **Administratörer** på den lokala datorn och fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-268">To run the commands in this example, you must be a member of the **Administrators** group on the local computer and the remote computer.</span></span>

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer Server02
$s = New-PSSession Server02
Invoke-Command -Session $s -ScriptBlock {Enable-WSManCredSSP -Role Server -Force}
$parameters = @{
  Session = $s
  ScriptBlock = { Get-Item \\Net03\Scripts\LogFiles.ps1 }
  Authentication = "CredSSP"
  Credential = "Domain01\Admin01"
}
Invoke-Command @parameters
```

<span data-ttu-id="e7ee8-269">`Enable-WSManCredSSP`Cmdlet: en aktiverar CredSSP-delegering från den lokala Server01-datorn till Server02-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-269">The `Enable-WSManCredSSP` cmdlet enables CredSSP delegation from the Server01 local computer to the Server02 remote computer.</span></span> <span data-ttu-id="e7ee8-270">**Roll** parametern anger **klienten** för att konfigurera CredSSP-klient inställningen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-270">The **Role** parameter specifies **Client** to configure the CredSSP client setting on the local computer.</span></span>

<span data-ttu-id="e7ee8-271">`New-PSSession` skapar ett **PSSession** -objekt för Server02 och lagrar objektet i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-271">`New-PSSession` creates a **PSSession** object for Server02 and stores the object in the `$s` variable.</span></span>

<span data-ttu-id="e7ee8-272">`Invoke-Command`Cmdlet: en använder `$s` variabeln för att ansluta till fjärrdatorn, Server02.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-272">The `Invoke-Command` cmdlet uses the `$s` variable to connect to the remote computer, Server02.</span></span> <span data-ttu-id="e7ee8-273">Parametern **script block** körs `Enable-WSManCredSSP` på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-273">The **ScriptBlock** parameter runs `Enable-WSManCredSSP` on the remote computer.</span></span> <span data-ttu-id="e7ee8-274">**Roll** parametern anger **servern** för att konfigurera CredSSP-Server inställningen på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-274">The **Role** parameter specifies **Server** to configure the CredSSP server setting on the remote computer.</span></span>

<span data-ttu-id="e7ee8-275">`$parameters`Variabeln innehåller de parameter värden som ska anslutas till nätverks resursen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-275">The `$parameters` variable contains the parameter values to connect to the network share.</span></span> <span data-ttu-id="e7ee8-276">`Invoke-Command`Cmdleten kör ett `Get-Item` kommando i sessionen i `$s` .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-276">The `Invoke-Command` cmdlet runs a `Get-Item` command in the session in `$s`.</span></span> <span data-ttu-id="e7ee8-277">Det här kommandot hämtar ett skript från `\\Net03\Scripts` nätverks resursen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-277">This command gets a script from the `\\Net03\Scripts` network share.</span></span> <span data-ttu-id="e7ee8-278">Kommandot använder parametern **Authentication** med värdet **CredSSP** och parametern **Credential** med värdet **Domain01\Admin01**.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-278">The command uses the **Authentication** parameter with a value of **CredSSP** and the **Credential** parameter with a value of **Domain01\Admin01**.</span></span>

### <span data-ttu-id="e7ee8-279">Exempel 18: starta skript på många fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="e7ee8-279">Example 18: Start scripts on many remote computers</span></span>

<span data-ttu-id="e7ee8-280">I det här exemplet körs ett skript på fler än hundra datorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-280">This example runs a script on more than a hundred computers.</span></span> <span data-ttu-id="e7ee8-281">För att minimera påverkan på den lokala datorn ansluter den till varje dator, startar skriptet och kopplar sedan från varje dator.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-281">To minimize the impact on the local computer, it connects to each computer, starts the script, and then disconnects from each computer.</span></span>
<span data-ttu-id="e7ee8-282">Skriptet fortsätter att köras i de frånkopplade sessionerna.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-282">The script continues to run in the disconnected sessions.</span></span>

```powershell
$parameters = @{
  ComputerName = (Get-Content -Path C:\Test\Servers.txt)
  InDisconnectedSession = $true
  FilePath = "\\Scripts\Public\ConfigInventory.ps1"
  SessionOption = @{OutputBufferingMode="Drop";IdleTimeout=43200000}
}
Invoke-Command @parameters
```

<span data-ttu-id="e7ee8-283">Kommandot använder `Invoke-Command` för att köra skriptet.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-283">The command uses `Invoke-Command` to run the script.</span></span> <span data-ttu-id="e7ee8-284">Värdet för parametern **computername** är ett `Get-Content` kommando som hämtar namnen på fjärrdatorerna från en textfil.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-284">The value of the **ComputerName** parameter is a `Get-Content` command that gets the names of the remote computers from a text file.</span></span> <span data-ttu-id="e7ee8-285">Parametern **InDisconnectedSession** kopplar från sessionerna så snart den startar kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-285">The **InDisconnectedSession** parameter disconnects the sessions as soon as it starts the command.</span></span> <span data-ttu-id="e7ee8-286">Värdet för parametern **sökväg** är det skript som `Invoke-Command` körs på varje dator.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-286">The value of the **FilePath** parameter is the script that `Invoke-Command` runs on each computer.</span></span>

<span data-ttu-id="e7ee8-287">Värdet för **SessionOption** är en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-287">The value of **SessionOption** is a hash table.</span></span> <span data-ttu-id="e7ee8-288">**OutputBufferingMode** -värdet är inställt på **Drop** och **idleTimeout** -värdet är inställt på **43200000** millisekunder (12 timmar).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-288">The **OutputBufferingMode** value is set to **Drop** and the **IdleTimeout** value is set to **43200000** milliseconds (12 hours).</span></span>

<span data-ttu-id="e7ee8-289">Använd cmdleten för att hämta resultatet av kommandon och skript som körs i frånkopplade sessioner `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-289">To get the results of commands and scripts that run in disconnected sessions, use the `Receive-PSSession` cmdlet.</span></span>

## <span data-ttu-id="e7ee8-290">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e7ee8-290">PARAMETERS</span></span>

### <span data-ttu-id="e7ee8-291">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="e7ee8-291">-AllowRedirection</span></span>

<span data-ttu-id="e7ee8-292">Tillåter omdirigering av anslutningen till en alternativ Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-292">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="e7ee8-293">När du använder **ConnectionURI** -parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-293">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="e7ee8-294">Som standard omdirigerar PowerShell inte anslutningar, men du kan använda den här parametern om du vill att den ska kunna omdirigera anslutningen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-294">By default, PowerShell doesn't redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="e7ee8-295">Du kan också begränsa hur många gånger anslutningen omdirigeras genom att ändra värdet för alternativet **MaximumConnectionRedirectionCount** session.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-295">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="e7ee8-296">Använd parametern **MaximumRedirection** för `New-PSSessionOption` cmdleten eller ange egenskapen **MaximumConnectionRedirectionCount** för `$PSSessionOption` Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-296">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="e7ee8-297">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-297">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-298">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="e7ee8-298">-ApplicationName</span></span>

<span data-ttu-id="e7ee8-299">Anger program namns segmentet för anslutnings-URI: n.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-299">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="e7ee8-300">Använd den här parametern för att ange program namnet när du inte använder parametern **ConnectionURI** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-300">Use this parameter to specify the application name when you aren't using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="e7ee8-301">Standardvärdet är värdet för Preference- `$PSSessionApplicationName` variabeln på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-301">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="e7ee8-302">Om den här preferens variabeln inte har definierats är standardvärdet WSMAN.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-302">If this preference variable isn't defined, the default value is WSMAN.</span></span> <span data-ttu-id="e7ee8-303">Det här värdet är lämpligt för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-303">This value is appropriate for most uses.</span></span> <span data-ttu-id="e7ee8-304">Mer information finns i [about_Preference_Variables](./About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-304">For more information, see [about_Preference_Variables](./About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="e7ee8-305">WinRM-tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-305">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="e7ee8-306">Värdet för den här parametern ska matcha värdet på egenskapen **URLPrefix** för en lyssnare på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-306">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: $PSSessionApplicationName if set on the local computer, otherwise WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-307">– Argument List</span><span class="sxs-lookup"><span data-stu-id="e7ee8-307">-ArgumentList</span></span>

<span data-ttu-id="e7ee8-308">Tillhandahåller värdena för lokala variabler i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-308">Supplies the values of local variables in the command.</span></span> <span data-ttu-id="e7ee8-309">Variablerna i kommandot ersätts av de här värdena innan kommandot körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-309">The variables in the command are replaced by these values before the command is run on the remote computer.</span></span> <span data-ttu-id="e7ee8-310">Ange värdena i en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-310">Enter the values in a comma-separated list.</span></span> <span data-ttu-id="e7ee8-311">Värdena är associerade med variabler i den ordning som de visas.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-311">Values are associated with variables in the order that they're listed.</span></span> <span data-ttu-id="e7ee8-312">Aliaset för **argument List** är argument.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-312">The alias for **ArgumentList** is Args.</span></span>

<span data-ttu-id="e7ee8-313">Värdena i **argument List** -parametern kan vara faktiska värden, till exempel 1024, eller så kan de vara referenser till lokala variabler, till exempel `$max` .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-313">The values in the **ArgumentList** parameter can be actual values, such as 1024, or they can be references to local variables, such as `$max`.</span></span>

<span data-ttu-id="e7ee8-314">Använd följande kommando format om du vill använda lokala variabler i ett kommando:</span><span class="sxs-lookup"><span data-stu-id="e7ee8-314">To use local variables in a command, use the following command format:</span></span>

<span data-ttu-id="e7ee8-315">`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` eller `<local-variable>`</span><span class="sxs-lookup"><span data-stu-id="e7ee8-315">`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` -or- `<local-variable>`</span></span>

<span data-ttu-id="e7ee8-316">Nyckelordet **param** listar de lokala variabler som används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-316">The **param** keyword lists the local variables that are used in the command.</span></span> <span data-ttu-id="e7ee8-317">**Argument List** tillhandahåller värdena för variablerna i den ordning som de visas.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-317">**ArgumentList** supplies the values of the variables, in the order that they're listed.</span></span> <span data-ttu-id="e7ee8-318">Mer information om beteendet för **argument List** finns [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-318">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-319">– AsJob</span><span class="sxs-lookup"><span data-stu-id="e7ee8-319">-AsJob</span></span>

<span data-ttu-id="e7ee8-320">Anger att denna cmdlet kör kommandot som ett bakgrunds jobb på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-320">Indicates that this cmdlet runs the command as a background job on a remote computer.</span></span> <span data-ttu-id="e7ee8-321">Använd den här parametern för att köra kommandon som tar lång tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-321">Use this parameter to run commands that take an extensive time to finish.</span></span>

<span data-ttu-id="e7ee8-322">När du använder parametern **AsJob** , returnerar kommandot ett objekt som representerar jobbet och visar sedan kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-322">When you use the **AsJob** parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span> <span data-ttu-id="e7ee8-323">Du kan fortsätta att arbeta i sessionen medan jobbet är klart.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-323">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="e7ee8-324">Använd cmdletarna för att hantera jobbet `*-Job` .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-324">To manage the job, use the `*-Job` cmdlets.</span></span> <span data-ttu-id="e7ee8-325">Använd cmdleten för att hämta jobb resultatet `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-325">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="e7ee8-326">Parametern **AsJob** påminner om `Invoke-Command` att använda cmdleten för att köra en `Start-Job` cmdlet via en fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-326">The **AsJob** parameter resembles using the `Invoke-Command` cmdlet to run a `Start-Job` cmdlet remotely.</span></span> <span data-ttu-id="e7ee8-327">Men med **AsJob** skapas jobbet på den lokala datorn även om jobbet körs på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-327">However, with **AsJob** , the job is created on the local computer, even though the job runs on a remote computer.</span></span> <span data-ttu-id="e7ee8-328">Resultatet av fjärrjobbet returneras automatiskt till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-328">The results of the remote job are automatically returned to the local computer.</span></span>

<span data-ttu-id="e7ee8-329">Mer information om PowerShell-bakgrunds jobb finns i [about_Jobs](About/about_Jobs.md) och [about_Remote_Jobs](About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-329">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-330">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="e7ee8-330">-Authentication</span></span>

<span data-ttu-id="e7ee8-331">Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-331">Specifies the mechanism that's used to authenticate the user's credentials.</span></span> <span data-ttu-id="e7ee8-332">CredSSP-autentisering är endast tillgängligt i Windows Vista, Windows Server 2008 och senare versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-332">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="e7ee8-333">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="e7ee8-333">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="e7ee8-334">Default</span><span class="sxs-lookup"><span data-stu-id="e7ee8-334">Default</span></span>
- <span data-ttu-id="e7ee8-335">Basic</span><span class="sxs-lookup"><span data-stu-id="e7ee8-335">Basic</span></span>
- <span data-ttu-id="e7ee8-336">CredSSP</span><span class="sxs-lookup"><span data-stu-id="e7ee8-336">Credssp</span></span>
- <span data-ttu-id="e7ee8-337">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="e7ee8-337">Digest</span></span>
- <span data-ttu-id="e7ee8-338">Kerberos</span><span class="sxs-lookup"><span data-stu-id="e7ee8-338">Kerberos</span></span>
- <span data-ttu-id="e7ee8-339">Negotiate</span><span class="sxs-lookup"><span data-stu-id="e7ee8-339">Negotiate</span></span>
- <span data-ttu-id="e7ee8-340">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="e7ee8-340">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="e7ee8-341">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-341">The default value is Default.</span></span>

<span data-ttu-id="e7ee8-342">Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-342">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="e7ee8-343">CredSSP-autentisering (Credential Security Support Provider), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-343">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="e7ee8-344">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-344">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="e7ee8-345">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-345">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span> <span data-ttu-id="e7ee8-346">Mer information finns i [Credential Security Support Provider](/windows/win32/secauthn/credential-security-support-provider).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-346">For more information, see [Credential Security Support Provider](/windows/win32/secauthn/credential-security-support-provider).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-347">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="e7ee8-347">-CertificateThumbprint</span></span>

<span data-ttu-id="e7ee8-348">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att ansluta till den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-348">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="e7ee8-349">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-349">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="e7ee8-350">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-350">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="e7ee8-351">De kan endast mappas till lokala användar konton och de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-351">They can be mapped only to local user accounts and they don't work with domain accounts.</span></span>

<span data-ttu-id="e7ee8-352">Om du vill hämta ett tumavtryck för certifikatet använder du ett `Get-Item` eller- `Get-ChildItem` kommando i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-352">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-353">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="e7ee8-353">-ComputerName</span></span>

<span data-ttu-id="e7ee8-354">Anger de datorer där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-354">Specifies the computers on which the command runs.</span></span> <span data-ttu-id="e7ee8-355">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-355">The default is the local computer.</span></span>

<span data-ttu-id="e7ee8-356">När du använder parametern **computername** skapar PowerShell en tillfällig anslutning som bara används för att köra det angivna kommandot och sedan stängs.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-356">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that's used only to run the specified command and is then closed.</span></span> <span data-ttu-id="e7ee8-357">Om du behöver en permanent anslutning använder du parametern **session** .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-357">If you need a persistent connection, use the **Session** parameter.</span></span>

<span data-ttu-id="e7ee8-358">Ange NETBIOS-namn, IP-adress eller fullständigt kvalificerat domän namn för en eller flera datorer i en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-358">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="e7ee8-359">Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-359">To specify the local computer, type the computer name, localhost, or a dot (`.`).</span></span>

<span data-ttu-id="e7ee8-360">Om du vill använda en IP-adress i värdet för **computername** måste kommandot innehålla parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-360">To use an IP address in the value of **ComputerName** , the command must include the **Credential** parameter.</span></span> <span data-ttu-id="e7ee8-361">Datorn måste vara konfigurerad för HTTPS-transporten eller fjärrdatorns IP-adress måste ingå i den lokala datorns WinRM **TrustedHosts** -lista.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-361">The computer must be configured for the HTTPS transport or the IP address of the remote computer must be included in the local computer's WinRM **TrustedHosts** list.</span></span> <span data-ttu-id="e7ee8-362">Instruktioner för att lägga till ett dator namn i listan **TrustedHosts** finns i [så här lägger du till en dator i listan över betrodda värden](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-362">For instructions to add a computer name to the **TrustedHosts** list, see [How to Add a Computer to the Trusted Host List](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list).</span></span>

<span data-ttu-id="e7ee8-363">I Windows Vista och senare versioner av operativ systemet Windows måste du köra PowerShell med alternativet **Kör som administratör** för att kunna inkludera den lokala datorn i värdet för **computername**.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-363">On Windows Vista and later versions of the Windows operating system, to include the local computer in the value of **ComputerName** , you must run PowerShell using the **Run as administrator** option.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FilePathComputerName, ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-364">– ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="e7ee8-364">-ConfigurationName</span></span>

<span data-ttu-id="e7ee8-365">Anger den sessionsinformation som används för den nya **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-365">Specifies the session configuration that is used for the new **PSSession**.</span></span>

<span data-ttu-id="e7ee8-366">Ange ett konfigurations namn eller den fullständigt kvalificerade resurs-URI: n för en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-366">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="e7ee8-367">Om du bara anger konfigurations namnet är följande schema-URI anpassningsprefix: `http://schemas.microsoft.com/PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-367">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="e7ee8-368">Sessionens konfiguration för en session finns på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-368">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="e7ee8-369">Om den angivna konfigurationen av sessionen inte finns på fjärrdatorn Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-369">If the specified session configuration doesn't exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="e7ee8-370">Standardvärdet är värdet för Preference- `$PSSessionConfigurationName` variabeln på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-370">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="e7ee8-371">Om den här preferens variabeln inte har angetts är standardvärdet **Microsoft. PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-371">If this preference variable isn't set, the default is **Microsoft.PowerShell**.</span></span> <span data-ttu-id="e7ee8-372">Mer information finns i [about_Preference_Variables](about/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-372">For more information, see [about_Preference_Variables](about/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: $PSSessionConfigurationName if set on the local computer, otherwise Microsoft.PowerShell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-373">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="e7ee8-373">-ConnectionUri</span></span>

<span data-ttu-id="e7ee8-374">Anger en Uniform Resource Identifier (URI) som definierar sessionens anslutnings slut punkt.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-374">Specifies a Uniform Resource Identifier (URI) that defines the connection endpoint of the session.</span></span>
<span data-ttu-id="e7ee8-375">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-375">The URI must be fully qualified.</span></span>

<span data-ttu-id="e7ee8-376">Formatet för den här strängen är följande:</span><span class="sxs-lookup"><span data-stu-id="e7ee8-376">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="e7ee8-377">Standardvärdet är följande:</span><span class="sxs-lookup"><span data-stu-id="e7ee8-377">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="e7ee8-378">Om du inte anger en anslutnings-URI kan du använda parametrarna **UseSSL** och **port** för att ange anslutnings-URI-värden.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-378">If you don't specify a connection URI, you can use the **UseSSL** and **Port** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="e7ee8-379">Giltiga värden för URI: n i **transport** segmentet är http och https.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-379">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="e7ee8-380">Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med standard portarna: 80 för HTTP och 443 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-380">If you specify a connection URI with a Transport segment, but don't specify a port, the session is created with the standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="e7ee8-381">Om du vill använda standard portarna för PowerShell-fjärrkommunikation anger du Port 5985 för HTTP eller 5986 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-381">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="e7ee8-382">Om mål datorn omdirigerar anslutningen till en annan URI, förhindrar PowerShell omdirigeringen om du inte använder parametern **AllowRedirection** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-382">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: Uri, FilePathUri
Aliases: URI, CU

Required: False
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-383">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="e7ee8-383">-ContainerId</span></span>

<span data-ttu-id="e7ee8-384">Anger en matris med container-ID: n.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-384">Specifies an array of container IDs.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-385">-Credential</span><span class="sxs-lookup"><span data-stu-id="e7ee8-385">-Credential</span></span>

<span data-ttu-id="e7ee8-386">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-386">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="e7ee8-387">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-387">The default is the current user.</span></span>

<span data-ttu-id="e7ee8-388">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-388">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="e7ee8-389">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-389">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="e7ee8-390">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-390">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="e7ee8-391">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-391">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName
Aliases:

Required: True (VMId, VMName, FilePathVMId, FilePathVMName), False (ComputerName, FilePathComputerName, Uri, FilePathUri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-392">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="e7ee8-392">-EnableNetworkAccess</span></span>

<span data-ttu-id="e7ee8-393">Anger att denna cmdlet lägger till en interaktiv säkerhetstoken till loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-393">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="e7ee8-394">Med den interaktiva token kan du köra kommandon i loopback-sessionen som hämtar data från andra datorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-394">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="e7ee8-395">Du kan till exempel köra ett kommando i sessionen som kopierar XML-filer från en fjärrdator till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-395">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="e7ee8-396">En loopback-session är en **PSSession** som kommer från och slutar på samma dator.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-396">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="e7ee8-397">Om du vill skapa en loopback-session utelämnar du parametern **computername** eller anger värdet till punkt ( `.` ), localhost eller namnet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-397">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (`.`), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="e7ee8-398">Som standard skapas loopback-sessioner med en nätverks-token som kanske inte ger behörighet att autentisera till fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-398">By default, loopback sessions are created using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="e7ee8-399">Parametern **EnableNetworkAccess** är endast effektiv i loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-399">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="e7ee8-400">Om du använder **EnableNetworkAccess** när du skapar en-session på en fjärrdator, lyckas kommandot, men parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-400">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="e7ee8-401">Du kan tillåta fjärråtkomst i en loopback-session med hjälp av **CredSSP** -värdet för parametern **Authentication** , som delegerar autentiseringsuppgifterna för sessionen till andra datorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-401">You can allow remote access in a loopback session using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="e7ee8-402">För att skydda datorn från skadlig åtkomst kan frånkopplade loopback-sessioner som har interaktiva tokens, som är de som skapats med **EnableNetworkAccess** , bara återanslutas från den dator där sessionen skapades.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-402">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created using **EnableNetworkAccess** , can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="e7ee8-403">Frånkopplade sessioner som använder CredSSP-autentisering kan återanslutas från andra datorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-403">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="e7ee8-404">Mer information finns i `Disconnect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-404">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="e7ee8-405">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-405">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-406">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="e7ee8-406">-FilePath</span></span>

<span data-ttu-id="e7ee8-407">Anger ett lokalt skript som denna cmdlet körs på en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-407">Specifies a local script that this cmdlet runs on one or more remote computers.</span></span> <span data-ttu-id="e7ee8-408">Ange sökvägen och fil namnet för skriptet eller skicka en sökväg till en skript Sök väg till `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-408">Enter the path and filename of the script, or pipe a script path to `Invoke-Command`.</span></span> <span data-ttu-id="e7ee8-409">Skriptet måste finnas på den lokala datorn eller i en katalog som den lokala datorn kan komma åt.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-409">The script must exist on the local computer or in a directory that the local computer can access.</span></span> <span data-ttu-id="e7ee8-410">Använd **argument List** för att ange värden för parametrarna i skriptet.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-410">Use **ArgumentList** to specify the values of parameters in the script.</span></span>

<span data-ttu-id="e7ee8-411">När du använder den här parametern konverterar PowerShell innehållet i den angivna skript filen till ett-skript block, skickar skript blocket till fjärrdatorn och kör det på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-411">When you use this parameter, PowerShell converts the contents of the specified script file to a script block, transmits the script block to the remote computer, and runs it on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, FilePathComputerName, FilePathUri, FilePathVMId, FilePathVMName, FilePathContainerId
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-412">-HideComputerName</span><span class="sxs-lookup"><span data-stu-id="e7ee8-412">-HideComputerName</span></span>

<span data-ttu-id="e7ee8-413">Anger att denna cmdlet utelämnar dator namnet för varje objekt från visningen av utdata.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-413">Indicates that this cmdlet omits the computer name of each object from the output display.</span></span> <span data-ttu-id="e7ee8-414">Som standard visas namnet på den dator som skapade objektet i visningen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-414">By default, the name of the computer that generated the object appears in the display.</span></span>

<span data-ttu-id="e7ee8-415">Den här parametern påverkar endast visningen av utdata.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-415">This parameter affects only the output display.</span></span> <span data-ttu-id="e7ee8-416">Objektet ändras inte.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-416">It doesn't change the object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases: HCN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-417">-InDisconnectedSession</span><span class="sxs-lookup"><span data-stu-id="e7ee8-417">-InDisconnectedSession</span></span>

<span data-ttu-id="e7ee8-418">Anger att denna cmdlet kör ett kommando eller skript i en frånkopplad session.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-418">Indicates that this cmdlet runs a command or script in a disconnected session.</span></span>

<span data-ttu-id="e7ee8-419">När du använder parametern **InDisconnectedSession** `Invoke-Command` skapar en beständig session på varje fjärrdator, startar kommandot som anges av parametern **script block** eller **sökväg** och kopplar sedan från sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-419">When you use the **InDisconnectedSession** parameter, `Invoke-Command` creates a persistent session on each remote computer, starts the command specified by the **ScriptBlock** or **FilePath** parameter, and then disconnects from the session.</span></span> <span data-ttu-id="e7ee8-420">Kommandona fortsätter att köras i de frånkopplade sessionerna.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-420">The commands continue to run in the disconnected sessions.</span></span> <span data-ttu-id="e7ee8-421">Med **InDisconnectedSession** kan du köra kommandon utan att ha en anslutning till fjärrsessionerna.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-421">**InDisconnectedSession** enables you to run commands without maintaining a connection to the remote sessions.</span></span> <span data-ttu-id="e7ee8-422">Eftersom sessionen kopplas bort innan ett resultat returneras, ser **InDisconnectedSession** till att alla kommando resultat returneras till den återanslutna sessionen, i stället för att delas mellan sessioner.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-422">And, because the session is disconnected before any results are returned, **InDisconnectedSession** makes sure that all command results are returned to the reconnected session, instead of being split between sessions.</span></span>

<span data-ttu-id="e7ee8-423">Du kan inte använda **InDisconnectedSession** med parametern **session** eller parametern **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-423">You can't use **InDisconnectedSession** with the **Session** parameter or the **AsJob** parameter.</span></span>

<span data-ttu-id="e7ee8-424">Kommandon som använder **InDisconnectedSession** returnerar ett **PSSession** -objekt som representerar den frånkopplade sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-424">Commands that use **InDisconnectedSession** return a **PSSession** object that represents the disconnected session.</span></span> <span data-ttu-id="e7ee8-425">De returnerar inte kommandoutdata.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-425">They don't return the command output.</span></span> <span data-ttu-id="e7ee8-426">Använd cmdletarna eller för att ansluta till den frånkopplade `Connect-PSSession` sessionen `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-426">To connect to the disconnected session, use the `Connect-PSSession` or `Receive-PSSession` cmdlets.</span></span> <span data-ttu-id="e7ee8-427">Använd cmdleten för att hämta resultatet av de kommandon som kördes i sessionen `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-427">To get the results of commands that ran in the session, use the `Receive-PSSession` cmdlet.</span></span> <span data-ttu-id="e7ee8-428">Om du vill köra kommandon som genererar utdata i en frånkopplad session anger du värdet för alternativet **OutputBufferingMode** session som du vill **ta bort**.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-428">To run commands that generate output in a disconnected session, set the value of the **OutputBufferingMode** session option to **Drop**.</span></span> <span data-ttu-id="e7ee8-429">Om du vill ansluta till den frånkopplade sessionen ställer du in tids gränsen för inaktivitet i sessionen så att den ger tillräckligt med tid för att ansluta innan sessionen tas bort.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-429">If you intend to connect to the disconnected session, set the idle time-out in the session so that it provides sufficient time for you to connect before deleting the session.</span></span>

<span data-ttu-id="e7ee8-430">Du kan ställa in buffrings läget för utdata och tids gränsen för inaktivitet i parametern **SessionOption** eller i `$PSSessionOption` variabeln Preference.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-430">You can set the output buffering mode and idle time-out in the **SessionOption** parameter or in the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="e7ee8-431">Mer information om sessions alternativ finns i `New-PSSessionOption` och [about_Preference_Variables](./about/about_preference_variables.md).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-431">For more information about session options, see `New-PSSessionOption` and [about_Preference_Variables](./about/about_preference_variables.md).</span></span>

<span data-ttu-id="e7ee8-432">Mer information om funktionen frånkopplade sessioner finns [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-432">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="e7ee8-433">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-433">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases: Disconnected

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-434">– InputObject</span><span class="sxs-lookup"><span data-stu-id="e7ee8-434">-InputObject</span></span>

<span data-ttu-id="e7ee8-435">Anger ininformation till kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-435">Specifies input to the command.</span></span> <span data-ttu-id="e7ee8-436">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-436">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="e7ee8-437">När du använder **InputObject** -parametern använder du den `$Input` automatiska variabeln i värdet för parametern **script block** för att representera de ingående objekten.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-437">When using the **InputObject** parameter, use the `$Input` automatic variable in the value of the **ScriptBlock** parameter to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-438">– JobName</span><span class="sxs-lookup"><span data-stu-id="e7ee8-438">-JobName</span></span>

<span data-ttu-id="e7ee8-439">Anger ett eget namn för bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-439">Specifies a friendly name for the background job.</span></span> <span data-ttu-id="e7ee8-440">Som standard namnges jobb `Job<n>` , där `<n>` är ett ordnings tal.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-440">By default, jobs are named `Job<n>`, where `<n>` is an ordinal number.</span></span>

<span data-ttu-id="e7ee8-441">Om du använder parametern **JobName** i ett kommando körs kommandot som ett jobb och `Invoke-Command` returnerar ett jobb objekt, även om du inte inkluderar **AsJob** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-441">If you use the **JobName** parameter in a command, the command is run as a job, and `Invoke-Command` returns a job object, even if you don't include **AsJob** in the command.</span></span>

<span data-ttu-id="e7ee8-442">Mer information om PowerShell-bakgrunds jobb finns [about_Jobs](./About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-442">For more information about PowerShell background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

```yaml
Type: System.String
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: Job<n>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-443">-NoNewScope</span><span class="sxs-lookup"><span data-stu-id="e7ee8-443">-NoNewScope</span></span>

<span data-ttu-id="e7ee8-444">Anger att denna cmdlet kör det angivna kommandot i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-444">Indicates that this cmdlet runs the specified command in the current scope.</span></span> <span data-ttu-id="e7ee8-445">Som standard `Invoke-Command` Kör kommandon i deras egna omfång.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-445">By default, `Invoke-Command` runs commands in their own scope.</span></span>

<span data-ttu-id="e7ee8-446">Den här parametern är endast giltig i kommandon som körs i den aktuella sessionen, det vill säga kommandon som utelämnar både **computername** -och **session** -parametrarna.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-446">This parameter is valid only in commands that are run in the current session, that is, commands that omit both the **ComputerName** and **Session** parameters.</span></span>

<span data-ttu-id="e7ee8-447">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-447">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InProcess
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-448">-Port</span><span class="sxs-lookup"><span data-stu-id="e7ee8-448">-Port</span></span>

<span data-ttu-id="e7ee8-449">Anger nätverks porten på den fjärrdator som används för det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-449">Specifies the network port on the remote computer that is used for this command.</span></span> <span data-ttu-id="e7ee8-450">Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-450">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="e7ee8-451">Standard portarna är 5985 (WinRM-port för HTTP) och 5986 (WinRM-port för HTTPS).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-451">The default ports are 5985 (WinRM port for HTTP) and 5986 (WinRM port for HTTPS).</span></span>

<span data-ttu-id="e7ee8-452">Innan du använder en alternativ port konfigurerar du WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-452">Before using an alternate port, configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="e7ee8-453">Konfigurera lyssnaren genom att skriva följande två kommandon i PowerShell-prompten:</span><span class="sxs-lookup"><span data-stu-id="e7ee8-453">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="e7ee8-454">Använd inte **port** parametern om du inte behöver det.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-454">Don't use the **Port** parameter unless you must.</span></span> <span data-ttu-id="e7ee8-455">Porten som anges i kommandot gäller för alla datorer eller sessioner där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-455">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="e7ee8-456">En alternativ port inställning kan hindra kommandot från att köras på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-456">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-457">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="e7ee8-457">-RunAsAdministrator</span></span>

<span data-ttu-id="e7ee8-458">Anger att denna cmdlet anropar ett kommando som administratör.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-458">Indicates that this cmdlet invokes a command as an Administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-459">– Script block</span><span class="sxs-lookup"><span data-stu-id="e7ee8-459">-ScriptBlock</span></span>

<span data-ttu-id="e7ee8-460">Anger vilka kommandon som ska köras.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-460">Specifies the commands to run.</span></span> <span data-ttu-id="e7ee8-461">Sätt i kommandona inom klammerparenteser `{ }` för att skapa ett skript block.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-461">Enclose the commands in curly braces `{ }` to create a script block.</span></span>
<span data-ttu-id="e7ee8-462">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-462">This parameter is required.</span></span>

<span data-ttu-id="e7ee8-463">Som standard utvärderas alla variabler i kommandot på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-463">By default, any variables in the command are evaluated on the remote computer.</span></span> <span data-ttu-id="e7ee8-464">Använd **argument List** om du vill inkludera lokala variabler i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-464">To include local variables in the command, use **ArgumentList**.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: InProcess, Session, ComputerName, Uri, VMId, VMName, ContainerId
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-465">– Session</span><span class="sxs-lookup"><span data-stu-id="e7ee8-465">-Session</span></span>

<span data-ttu-id="e7ee8-466">Anger en matris med sessioner där denna cmdlet kör kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-466">Specifies an array of sessions in which this cmdlet runs the command.</span></span> <span data-ttu-id="e7ee8-467">Ange en variabel som innehåller **PSSession** -objekt eller ett kommando som skapar eller hämtar **PSSession** -objekt, till exempel ett `New-PSSession` eller- `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-467">Enter a variable that contains **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="e7ee8-468">När du skapar en **PSSession** upprättar PowerShell en permanent anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-468">When you create a **PSSession** , PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="e7ee8-469">Använd en **PSSession** för att köra en serie relaterade kommandon som delar data.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-469">Use a **PSSession** to run a series of related commands that share data.</span></span> <span data-ttu-id="e7ee8-470">Om du vill köra ett enda kommando eller en serie med orelaterade kommandon använder du parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-470">To run a single command or a series of unrelated commands, use the **ComputerName** parameter.</span></span> <span data-ttu-id="e7ee8-471">Mer information finns i [about_PSSessions](./About/about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-471">For more information, see [about_PSSessions](./About/about_PSSessions.md).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session, FilePathRunspace
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-472">-Sessionsnamn</span><span class="sxs-lookup"><span data-stu-id="e7ee8-472">-SessionName</span></span>

<span data-ttu-id="e7ee8-473">Anger ett eget namn för en frånkopplad session.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-473">Specifies a friendly name for a disconnected session.</span></span> <span data-ttu-id="e7ee8-474">Du kan använda namnet för att referera till sessionen i efterföljande kommandon, till exempel ett `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-474">You can use the name to refer to the session in subsequent commands, such as a `Get-PSSession` command.</span></span> <span data-ttu-id="e7ee8-475">Den här parametern är endast giltig med parametern **InDisconnectedSession** .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-475">This parameter is valid only with the **InDisconnectedSession** parameter.</span></span>

<span data-ttu-id="e7ee8-476">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-476">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-477">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="e7ee8-477">-SessionOption</span></span>

<span data-ttu-id="e7ee8-478">Anger avancerade alternativ för sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-478">Specifies advanced options for the session.</span></span> <span data-ttu-id="e7ee8-479">Ange ett **SessionOption** -objekt, t. ex. ett som du skapar med hjälp av `New-PSSessionOption` cmdleten, eller en hash-tabell där nycklarna är namn på sessionstillstånd och värdena är alternativ värden för session.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-479">Enter a **SessionOption** object, such as one that you create using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="e7ee8-480">Standardvärdena för alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-480">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it's set.</span></span> <span data-ttu-id="e7ee8-481">Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-481">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="e7ee8-482">Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i `$PSSessionOption` variabeln Preference och i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-482">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="e7ee8-483">De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-483">However, they don't take precedence over maximum values, quotas, or limits set in the session configuration.</span></span>

<span data-ttu-id="e7ee8-484">En beskrivning av de sessionsinformation som innehåller standardvärdena finns i `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-484">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="e7ee8-485">Information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-485">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="e7ee8-486">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-486">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: FilePathComputerName, ComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-487">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="e7ee8-487">-ThrottleLimit</span></span>

<span data-ttu-id="e7ee8-488">Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-488">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="e7ee8-489">Om du utelämnar den här parametern eller anger värdet 0, används standardvärdet 32.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-489">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="e7ee8-490">Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-490">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Session, FilePathRunspace, FilePathComputerName, ComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-491">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="e7ee8-491">-UseSSL</span></span>

<span data-ttu-id="e7ee8-492">Anger att denna cmdlet använder Secure Sockets Layer-protokollet (SSL) för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-492">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="e7ee8-493">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-493">By default, SSL isn't used.</span></span>

<span data-ttu-id="e7ee8-494">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-494">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="e7ee8-495">Parametern **UseSSL** är ett ytterligare skydd som skickar data via https i stället för http.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-495">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS, instead of HTTP.</span></span>

<span data-ttu-id="e7ee8-496">Om du använder den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-496">If you use this parameter, but SSL isn't available on the port that's used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathComputerName, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-497">-VMId</span><span class="sxs-lookup"><span data-stu-id="e7ee8-497">-VMId</span></span>

<span data-ttu-id="e7ee8-498">Anger en matris med ID: n för virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-498">Specifies an array of IDs of virtual machines.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: VMId, FilePathVMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-499">– VMName</span><span class="sxs-lookup"><span data-stu-id="e7ee8-499">-VMName</span></span>

<span data-ttu-id="e7ee8-500">Anger en matris med namn på virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-500">Specifies an array of names of virtual machines.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName, FilePathVMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e7ee8-501">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e7ee8-501">CommonParameters</span></span>

<span data-ttu-id="e7ee8-502">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-502">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e7ee8-503">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-503">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e7ee8-504">INDATA</span><span class="sxs-lookup"><span data-stu-id="e7ee8-504">INPUTS</span></span>

### <span data-ttu-id="e7ee8-505">System. Management. Automation. script block</span><span class="sxs-lookup"><span data-stu-id="e7ee8-505">System.Management.Automation.ScriptBlock</span></span>

<span data-ttu-id="e7ee8-506">Du kan skicka vidare ett kommando i ett skript block till `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-506">You can pipe a command in a script block to `Invoke-Command`.</span></span> <span data-ttu-id="e7ee8-507">Använd den `$Input` automatiska variabeln för att representera inobjekten i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-507">Use the `$Input` automatic variable to represent the input objects in the command.</span></span>

## <span data-ttu-id="e7ee8-508">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e7ee8-508">OUTPUTS</span></span>

### <span data-ttu-id="e7ee8-509">System. Management. Automation. PSRemotingJob, system. Management. Automation. körnings utrymmen. PSSession eller utdata från det anropade kommandot</span><span class="sxs-lookup"><span data-stu-id="e7ee8-509">System.Management.Automation.PSRemotingJob, System.Management.Automation.Runspaces.PSSession, or the output of the invoked command</span></span>

<span data-ttu-id="e7ee8-510">Den här cmdleten returnerar ett jobb objekt, om du använder parametern **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-510">This cmdlet returns a job object, if you use the **AsJob** parameter.</span></span> <span data-ttu-id="e7ee8-511">Om du anger parametern **InDisconnectedSession** `Invoke-Command` returnerar ett **PSSession** -objekt.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-511">If you specify the **InDisconnectedSession** parameter, `Invoke-Command` returns a **PSSession** object.</span></span> <span data-ttu-id="e7ee8-512">Annars returnerar den utdata från kommandot som anropades, vilket är värdet för parametern **script block** .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-512">Otherwise, it returns the output of the invoked command, which is the value of the **ScriptBlock** parameter.</span></span>

## <span data-ttu-id="e7ee8-513">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e7ee8-513">NOTES</span></span>

<span data-ttu-id="e7ee8-514">I Windows Vista och senare versioner av operativ systemet Windows, för att använda parametern **computername** för `Invoke-Command` för att köra ett kommando på den lokala datorn, måste du köra PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="e7ee8-514">On Windows Vista, and later versions of the Windows operating system, to use the **ComputerName** parameter of `Invoke-Command` to run a command on the local computer, you must run PowerShell using the **Run as administrator** option.</span></span>

<span data-ttu-id="e7ee8-515">När du kör kommandon på flera datorer ansluter PowerShell till datorerna i den ordning som de visas i listan.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-515">When you run commands on multiple computers, PowerShell connects to the computers in the order in which they appear in the list.</span></span> <span data-ttu-id="e7ee8-516">Men kommandots utdata visas i den ordning som den tas emot från fjärrdatorer, vilket kan vara olika.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-516">However, the command output is displayed in the order that it's received from the remote computers, which might be different.</span></span>

<span data-ttu-id="e7ee8-517">Fel som orsakas av kommandot som `Invoke-Command` körs ingår i kommando resultatet.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-517">Errors that result from the command that `Invoke-Command` runs are included in the command results.</span></span>
<span data-ttu-id="e7ee8-518">Fel som avslutar fel i ett lokalt kommando behandlas som icke-avslutande fel i ett fjärrkommando.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-518">Errors that would be terminating errors in a local command are treated as non-terminating errors in a remote command.</span></span> <span data-ttu-id="e7ee8-519">Den här strategin ser till att avslutande fel på en dator inte stänger kommandot på alla datorer där den körs.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-519">This strategy makes sure that terminating errors on one computer don't close the command on all computers on which it's run.</span></span> <span data-ttu-id="e7ee8-520">Den här metoden används även när ett fjärrkommando körs på en enda dator.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-520">This practice is used even when a remote command is run on a single computer.</span></span>

<span data-ttu-id="e7ee8-521">Om fjärrdatorn inte finns i en domän som den lokala datorn litar på, kanske datorn inte kan autentisera användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-521">If the remote computer isn't in a domain that the local computer trusts, the computer might not be able to authenticate the user's credentials.</span></span> <span data-ttu-id="e7ee8-522">Om du vill lägga till fjärrdatorn i listan över betrodda värdar i WS-Management använder du följande kommando i `WSMAN` providern, där `<Remote-Computer-Name>` är namnet på fjärrdatorn:</span><span class="sxs-lookup"><span data-stu-id="e7ee8-522">To add the remote computer to the list of trusted hosts in WS-Management, use the following command in the `WSMAN` provider, where `<Remote-Computer-Name>` is the name of the remote computer:</span></span>

`Set-Item -Path WSMan:\Localhost\Client\TrustedHosts -Value \<Remote-Computer-Name\>`

<span data-ttu-id="e7ee8-523">När du kopplar från en **PSSession** med hjälp av **InDisconnectedSession** -parametern är sessionstillståndet **frånkopplat** och tillgängligheten är **ingen**.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-523">When you disconnect a **PSSession** using the **InDisconnectedSession** parameter, the session state is **Disconnected** and the availability is **None**.</span></span> <span data-ttu-id="e7ee8-524">Värdet för egenskapen **State** är i förhållande till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-524">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="e7ee8-525">Värdet **frånkopplat** innebär att **PSSession** inte är ansluten till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-525">A value of **Disconnected** means that the **PSSession** isn't connected to the current session.</span></span> <span data-ttu-id="e7ee8-526">Det innebär dock inte att **PSSession** är frånkopplad från alla sessioner.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-526">However, it doesn't mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="e7ee8-527">Den kan vara ansluten till en annan session.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-527">It might be connected to a different session.</span></span> <span data-ttu-id="e7ee8-528">Använd egenskapen **tillgänglighet** för att avgöra om du kan ansluta eller återansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-528">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

<span data-ttu-id="e7ee8-529">**Tillgänglighet** svärdet **none** anger att du kan ansluta till sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-529">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="e7ee8-530">Värdet **upptagen** anger att du inte kan ansluta till **PSSession** eftersom det är anslutet till en annan session.</span><span class="sxs-lookup"><span data-stu-id="e7ee8-530">A value of **Busy** indicates that you can't connect to the **PSSession** because it's connected to another session.</span></span> <span data-ttu-id="e7ee8-531">Mer information om värdena för egenskapen **State** för sessioner finns i [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-531">For more information about the values of the **State** property of sessions, see [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span> <span data-ttu-id="e7ee8-532">Mer information om värdena för egenskapen **Availability** för sessioner finns i [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span><span class="sxs-lookup"><span data-stu-id="e7ee8-532">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="e7ee8-533">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e7ee8-533">RELATED LINKS</span></span>

[<span data-ttu-id="e7ee8-534">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="e7ee8-534">about_PSSessions</span></span>](./About/about_PSSessions.md)

[<span data-ttu-id="e7ee8-535">about_Remote</span><span class="sxs-lookup"><span data-stu-id="e7ee8-535">about_Remote</span></span>](./About/about_Remote.md)

[<span data-ttu-id="e7ee8-536">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="e7ee8-536">about_Remote_Disconnected_Sessions</span></span>](./About/about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="e7ee8-537">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="e7ee8-537">about_Remote_Troubleshooting</span></span>](./About/about_remote_troubleshooting.md)

[<span data-ttu-id="e7ee8-538">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="e7ee8-538">about_Remote_Variables</span></span>](./About/about_Remote_Variables.md)

[<span data-ttu-id="e7ee8-539">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="e7ee8-539">about_Scopes</span></span>](./About/about_scopes.md)

[<span data-ttu-id="e7ee8-540">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="e7ee8-540">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="e7ee8-541">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="e7ee8-541">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="e7ee8-542">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="e7ee8-542">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="e7ee8-543">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="e7ee8-543">Invoke-Item</span></span>](../Microsoft.PowerShell.Management/Invoke-Item.md)

[<span data-ttu-id="e7ee8-544">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e7ee8-544">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="e7ee8-545">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="e7ee8-545">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="e7ee8-546">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="e7ee8-546">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
