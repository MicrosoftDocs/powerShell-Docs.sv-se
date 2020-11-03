---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: 1835d0bd4294161f83728a63e8da8fc64c2bf9e0
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268179"
---
# <span data-ttu-id="c8bca-103">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="c8bca-103">New-PSSession</span></span>

## <span data-ttu-id="c8bca-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c8bca-104">SYNOPSIS</span></span>
<span data-ttu-id="c8bca-105">Skapar en permanent anslutning till en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="c8bca-105">Creates a persistent connection to a local or remote computer.</span></span>

## <span data-ttu-id="c8bca-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c8bca-106">SYNTAX</span></span>

### <span data-ttu-id="c8bca-107">ComputerName (standard)</span><span class="sxs-lookup"><span data-stu-id="c8bca-107">ComputerName (Default)</span></span>

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="c8bca-108">URI</span><span class="sxs-lookup"><span data-stu-id="c8bca-108">Uri</span></span>

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="c8bca-109">VMId</span><span class="sxs-lookup"><span data-stu-id="c8bca-109">VMId</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c8bca-110">VMName</span><span class="sxs-lookup"><span data-stu-id="c8bca-110">VMName</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c8bca-111">Session</span><span class="sxs-lookup"><span data-stu-id="c8bca-111">Session</span></span>

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c8bca-112">Hålla</span><span class="sxs-lookup"><span data-stu-id="c8bca-112">ContainerId</span></span>

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="c8bca-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c8bca-113">DESCRIPTION</span></span>

<span data-ttu-id="c8bca-114">`New-PSSession`Cmdleten skapar en PowerShell-session ( **PSSession** ) på en lokal eller fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="c8bca-114">The `New-PSSession` cmdlet creates a PowerShell session ( **PSSession** ) on a local or remote computer.</span></span> <span data-ttu-id="c8bca-115">När du skapar en **PSSession** upprättar PowerShell en permanent anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-115">When you create a **PSSession** , PowerShell establishes a persistent connection to the remote computer.</span></span>

<span data-ttu-id="c8bca-116">Använd en **PSSession** för att köra flera kommandon som delar data, till exempel en funktion eller värdet för en variabel.</span><span class="sxs-lookup"><span data-stu-id="c8bca-116">Use a **PSSession** to run multiple commands that share data, such as a function or the value of a variable.</span></span> <span data-ttu-id="c8bca-117">Om du vill köra kommandon i en **PSSession** använder du `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c8bca-117">To run commands in a **PSSession** , use the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="c8bca-118">Använd cmdleten om du vill använda **PSSession** för att interagera direkt med en fjärrdator `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="c8bca-118">To use the **PSSession** to interact directly with a remote computer, use the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="c8bca-119">Mer information finns i [about_PSSessions](about/about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="c8bca-119">For more information, see [about_PSSessions](about/about_PSSessions.md).</span></span>

<span data-ttu-id="c8bca-120">Du kan köra kommandon på en fjärrdator utan att skapa en **PSSession** med hjälp av **computername** -parametrarna för `Enter-PSSession` eller `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="c8bca-120">You can run commands on a remote computer without creating a **PSSession** by using the **ComputerName** parameters of `Enter-PSSession` or `Invoke-Command`.</span></span> <span data-ttu-id="c8bca-121">När du använder parametern **computername** skapar PowerShell en tillfällig anslutning som används för kommandot och stängs sedan.</span><span class="sxs-lookup"><span data-stu-id="c8bca-121">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that is used for the command and is then closed.</span></span>

## <span data-ttu-id="c8bca-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c8bca-122">EXAMPLES</span></span>

### <span data-ttu-id="c8bca-123">Exempel 1: skapa en session på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="c8bca-123">Example 1: Create a session on the local computer</span></span>

```powershell
$s = New-PSSession
```

<span data-ttu-id="c8bca-124">Det här kommandot skapar en ny **PSSession** på den lokala datorn och sparar **PSSession** i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8bca-124">This command creates a new **PSSession** on the local computer and saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="c8bca-125">Nu kan du använda den här **PSSession** för att köra kommandon på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-125">You can now use this **PSSession** to run commands on the local computer.</span></span>

### <span data-ttu-id="c8bca-126">Exempel 2: skapa en session på en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="c8bca-126">Example 2: Create a session on a remote computer</span></span>

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

<span data-ttu-id="c8bca-127">Det här kommandot skapar en ny **PSSession** på Server01-datorn och sparar det i `$Server01` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8bca-127">This command creates a new **PSSession** on the Server01 computer and saves it in the `$Server01` variable.</span></span>

<span data-ttu-id="c8bca-128">När du skapar flera **PSSession** -objekt tilldelar du dem till variabler med användbara namn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-128">When creating multiple **PSSession** objects, assign them to variables with useful names.</span></span> <span data-ttu-id="c8bca-129">Detta hjälper dig att hantera **PSSession** -objekt i efterföljande kommandon.</span><span class="sxs-lookup"><span data-stu-id="c8bca-129">This will help you manage the **PSSession** objects in subsequent commands.</span></span>

### <span data-ttu-id="c8bca-130">Exempel 3: skapa sessioner på flera datorer</span><span class="sxs-lookup"><span data-stu-id="c8bca-130">Example 3: Create sessions on multiple computers</span></span>

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

<span data-ttu-id="c8bca-131">Det här kommandot skapar tre **PSSession** -objekt, ett på varje dator som anges av parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="c8bca-131">This command creates three **PSSession** objects, one on each of the computers specified by the **ComputerName** parameter.</span></span>

<span data-ttu-id="c8bca-132">Kommandot använder tilldelnings operatorn (=) för att tilldela de nya **PSSession** -objekten till variabler: `$s1` , `$s2` , `$s3` .</span><span class="sxs-lookup"><span data-stu-id="c8bca-132">The command uses the assignment operator (=) to assign the new **PSSession** objects to variables: `$s1`, `$s2`, `$s3`.</span></span> <span data-ttu-id="c8bca-133">Den tilldelar Server01- **PSSession** till `$s1` , Server02 **PSSession** till `$s2` och Server03 **PSSession** till `$s3` .</span><span class="sxs-lookup"><span data-stu-id="c8bca-133">It assigns the Server01 **PSSession** to `$s1`, the Server02 **PSSession** to `$s2`, and the Server03 **PSSession** to `$s3`.</span></span>

<span data-ttu-id="c8bca-134">När du tilldelar flera objekt till en serie med variabler tilldelar PowerShell varje objekt till en variabel i serien.</span><span class="sxs-lookup"><span data-stu-id="c8bca-134">When you assign multiple objects to a series of variables, PowerShell assigns each object to a variable in the series respectively.</span></span> <span data-ttu-id="c8bca-135">Om det finns fler objekt än variabler tilldelas alla återstående objekt den sista variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8bca-135">If there are more objects than variables, all remaining objects are assigned to the last variable.</span></span> <span data-ttu-id="c8bca-136">Om det finns fler variabler än objekt är de återstående variablerna tomma (null).</span><span class="sxs-lookup"><span data-stu-id="c8bca-136">If there are more variables than objects, the remaining variables are empty (null).</span></span>

### <span data-ttu-id="c8bca-137">Exempel 4: skapa en session med en angiven port</span><span class="sxs-lookup"><span data-stu-id="c8bca-137">Example 4: Create a session with a specified port</span></span>

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

<span data-ttu-id="c8bca-138">Det här kommandot skapar en ny **PSSession** på Server01-datorn som ansluter till server port 8081 och använder SSL-protokollet.</span><span class="sxs-lookup"><span data-stu-id="c8bca-138">This command creates a new **PSSession** on the Server01 computer that connects to server port 8081 and uses the SSL protocol.</span></span> <span data-ttu-id="c8bca-139">Den nya **PSSession** använder en alternativ sessionsinformation med namnet E12.</span><span class="sxs-lookup"><span data-stu-id="c8bca-139">The new **PSSession** uses an alternative session configuration called E12.</span></span>

<span data-ttu-id="c8bca-140">Innan du anger porten måste du konfigurera WinRM-lyssnaren på fjärrdatorn så att den lyssnar på port 8081.</span><span class="sxs-lookup"><span data-stu-id="c8bca-140">Before setting the port, you must configure the WinRM listener on the remote computer to listen on port 8081.</span></span> <span data-ttu-id="c8bca-141">Mer information finns i beskrivningen av **port** parametern.</span><span class="sxs-lookup"><span data-stu-id="c8bca-141">For more information, see the description of the **Port** parameter.</span></span>

### <span data-ttu-id="c8bca-142">Exempel 5: skapa en session baserad på en befintlig session</span><span class="sxs-lookup"><span data-stu-id="c8bca-142">Example 5: Create a session based on an existing session</span></span>

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

<span data-ttu-id="c8bca-143">Det här kommandot skapar en **PSSession** med samma egenskaper som en befintlig **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="c8bca-143">This command creates a **PSSession** with the same properties as an existing **PSSession**.</span></span> <span data-ttu-id="c8bca-144">Du kan använda det här kommando formatet när resurserna för en befintlig **PSSession** är uttömda och en ny **PSSession** krävs för att avlasta en del av behovet.</span><span class="sxs-lookup"><span data-stu-id="c8bca-144">You can use this command format when the resources of an existing **PSSession** are exhausted and a new **PSSession** is needed to offload some of the demand.</span></span>

<span data-ttu-id="c8bca-145">Kommandot använder parametern **session** för `New-PSSession` för att ange **PSSession** som sparats i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8bca-145">The command uses the **Session** parameter of `New-PSSession` to specify the **PSSession** saved in the `$s` variable.</span></span> <span data-ttu-id="c8bca-146">Den använder Domain1\Admin01-användarens autentiseringsuppgifter för att slutföra kommandot.</span><span class="sxs-lookup"><span data-stu-id="c8bca-146">It uses the credentials of the Domain1\Admin01 user to complete the command.</span></span>

### <span data-ttu-id="c8bca-147">Exempel 6: skapa en session med en global omfattning i en annan domän</span><span class="sxs-lookup"><span data-stu-id="c8bca-147">Example 6: Create a session with a global scope in a different domain</span></span>

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

<span data-ttu-id="c8bca-148">Det här exemplet visar hur du skapar en **PSSession** med ett globalt omfång på en dator i en annan domän.</span><span class="sxs-lookup"><span data-stu-id="c8bca-148">This example shows how to create a **PSSession** with a global scope on a computer in a different domain.</span></span>

<span data-ttu-id="c8bca-149">Som standard skapas **PSSession** -objekt som skapas på kommando raden med lokala scope-och **PSSession** -objekt som skapats i ett skript som har skript omfattning.</span><span class="sxs-lookup"><span data-stu-id="c8bca-149">By default, **PSSession** objects created at the command line are created with local scope and **PSSession** objects created in a script have script scope.</span></span>

<span data-ttu-id="c8bca-150">Skapa en **PSSession** med global omfattning genom att skapa en ny **PSSession** och sedan lagra **PSSession** i en variabel som är Cast till en global omfattning.</span><span class="sxs-lookup"><span data-stu-id="c8bca-150">To create a **PSSession** with global scope, create a new **PSSession** and then store the **PSSession** in a variable that is cast to a global scope.</span></span> <span data-ttu-id="c8bca-151">I det här fallet `$s` omvandlas variabeln till en global omfattning.</span><span class="sxs-lookup"><span data-stu-id="c8bca-151">In this case, the `$s` variable is cast to a global scope.</span></span>

<span data-ttu-id="c8bca-152">Kommandot använder parametern **computername** för att ange fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-152">The command uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="c8bca-153">Eftersom datorn finns i en annan domän än användar kontot, anges det fullständiga namnet på datorn tillsammans med autentiseringsuppgifterna för användaren.</span><span class="sxs-lookup"><span data-stu-id="c8bca-153">Because the computer is in a different domain than the user account, the full name of the computer is specified together with the credentials of the user.</span></span>

### <span data-ttu-id="c8bca-154">Exempel 7: skapa sessioner för många datorer</span><span class="sxs-lookup"><span data-stu-id="c8bca-154">Example 7: Create sessions for many computers</span></span>

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

<span data-ttu-id="c8bca-155">Det här kommandot skapar en **PSSession** på var och en av de 200 datorer som anges i Servers.txt-filen och lagrar den resulterande **PSSession** i `$rs` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8bca-155">This command creates a **PSSession** on each of the 200 computers listed in the Servers.txt file and it stores the resulting **PSSession** in the `$rs` variable.</span></span> <span data-ttu-id="c8bca-156">**PSSession** -objekten har en begränsnings gräns på 50.</span><span class="sxs-lookup"><span data-stu-id="c8bca-156">The **PSSession** objects have a throttle limit of 50.</span></span>

<span data-ttu-id="c8bca-157">Du kan använda det här kommando formatet när namnen på datorerna lagras i en databas, ett kalkyl blad, i en textfil eller i ett annat format som kan konverteras.</span><span class="sxs-lookup"><span data-stu-id="c8bca-157">You can use this command format when the names of computers are stored in a database, spreadsheet, text file, or other text-convertible format.</span></span>

### <span data-ttu-id="c8bca-158">Exempel 8: skapa en session med en URI</span><span class="sxs-lookup"><span data-stu-id="c8bca-158">Example 8: Create a session by using a URI</span></span>

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

<span data-ttu-id="c8bca-159">Det här kommandot skapar en **PSSession** på Server01-datorn och lagrar den i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8bca-159">This command creates a **PSSession** on the Server01 computer and stores it in the `$s` variable.</span></span> <span data-ttu-id="c8bca-160">Den använder **URI** -parametern för att ange transport protokollet, fjärrdatorn, porten och en alternativ konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="c8bca-160">It uses the **URI** parameter to specify the transport protocol, the remote computer, the port, and an alternate session configuration.</span></span> <span data-ttu-id="c8bca-161">Den använder också parametern **Credential** för att ange ett användar konto som har behörighet att skapa en session på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-161">It also uses the **Credential** parameter to specify a user account that has permission to create a session on the remote computer.</span></span>

### <span data-ttu-id="c8bca-162">Exempel 9: köra ett bakgrunds jobb i en uppsättning sessioner</span><span class="sxs-lookup"><span data-stu-id="c8bca-162">Example 9: Run a background job in a set of sessions</span></span>

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

<span data-ttu-id="c8bca-163">Dessa kommandon skapar en uppsättning **PSSession** -objekt och kör sedan ett bakgrunds jobb i vart och ett av **PSSession** -objekten.</span><span class="sxs-lookup"><span data-stu-id="c8bca-163">These commands create a set of **PSSession** objects and then run a background job in each of the **PSSession** objects.</span></span>

<span data-ttu-id="c8bca-164">Det första kommandot skapar en ny **PSSession** på var och en av de datorer som anges i Servers.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="c8bca-164">The first command creates a new **PSSession** on each of the computers listed in the Servers.txt file.</span></span> <span data-ttu-id="c8bca-165">Den använder `New-PSSession` cmdleten för att skapa **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="c8bca-165">It uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span> <span data-ttu-id="c8bca-166">Värdet för parametern **computername** är ett kommando som använder `Get-Content` cmdleten för att hämta listan över dator namn Servers.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="c8bca-166">The value of the **ComputerName** parameter is a command that uses the `Get-Content` cmdlet to get the list of computer names the Servers.txt file.</span></span>

<span data-ttu-id="c8bca-167">Kommandot använder parametern **Credential** för att skapa **PSSession** -objekt som har behörighet för en domän administratör och använder parametern **ThrottleLimit** för att begränsa kommandot till 16 samtidiga anslutningar.</span><span class="sxs-lookup"><span data-stu-id="c8bca-167">The command uses the **Credential** parameter to create the **PSSession** objects that have the permission of a domain administrator, and it uses the **ThrottleLimit** parameter to limit the command to 16 concurrent connections.</span></span> <span data-ttu-id="c8bca-168">Kommandot sparar **PSSession** -objekten i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8bca-168">The command saves the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="c8bca-169">Det andra kommandot använder **AsJob** -parametern för `Invoke-Command` cmdleten för att starta ett bakgrunds jobb som kör ett `Get-Process PowerShell` kommando i varje **PSSession** -objekt i `$s` .</span><span class="sxs-lookup"><span data-stu-id="c8bca-169">The second command uses the **AsJob** parameter of the `Invoke-Command` cmdlet to start a background job that runs a `Get-Process PowerShell` command in each of the **PSSession** objects in `$s`.</span></span>

<span data-ttu-id="c8bca-170">Mer information om PowerShell-bakgrunds jobb finns i [about_Jobs](About/about_Jobs.md) och [about_Remote_Jobs](About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="c8bca-170">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

### <span data-ttu-id="c8bca-171">Exempel 10: skapa en session för en dator med hjälp av dess URI</span><span class="sxs-lookup"><span data-stu-id="c8bca-171">Example 10: Create a session for a computer by using its URI</span></span>

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

<span data-ttu-id="c8bca-172">Det här kommandot skapar ett **PSSession** -objekt som ansluter till en dator som anges av en URI i stället för ett dator namn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-172">This command creates a **PSSession** objects that connects to a computer that is specified by a URI instead of a computer name.</span></span>

### <span data-ttu-id="c8bca-173">Exempel 11: skapa ett session-alternativ</span><span class="sxs-lookup"><span data-stu-id="c8bca-173">Example 11: Create a session option</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

<span data-ttu-id="c8bca-174">I det här exemplet visas hur du skapar ett sessionsobjekt-objekt och använder parametern **SessionOption** .</span><span class="sxs-lookup"><span data-stu-id="c8bca-174">This example shows how to create a session option object and use the **SessionOption** parameter.</span></span>

<span data-ttu-id="c8bca-175">Det första kommandot använder `New-PSSessionOption` cmdleten för att skapa ett session-alternativ.</span><span class="sxs-lookup"><span data-stu-id="c8bca-175">The first command uses the `New-PSSessionOption` cmdlet to create a session option.</span></span> <span data-ttu-id="c8bca-176">Det sparar det resulterande **SessionOption** -objektet i `$so` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8bca-176">It saves the resulting **SessionOption** object in the `$so` variable.</span></span>

<span data-ttu-id="c8bca-177">Det andra kommandot använder alternativet i en ny session.</span><span class="sxs-lookup"><span data-stu-id="c8bca-177">The second command uses the option in a new session.</span></span> <span data-ttu-id="c8bca-178">Kommandot använder `New-PSSession` cmdleten för att skapa en ny session.</span><span class="sxs-lookup"><span data-stu-id="c8bca-178">The command uses the `New-PSSession` cmdlet to create a new session.</span></span> <span data-ttu-id="c8bca-179">Värdet för parametern SessionOption är **SessionOption** -objektet i `$so` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8bca-179">The value of the SessionOption parameter is the **SessionOption** object in the `$so` variable.</span></span>

## <span data-ttu-id="c8bca-180">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c8bca-180">PARAMETERS</span></span>

### <span data-ttu-id="c8bca-181">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="c8bca-181">-AllowRedirection</span></span>

<span data-ttu-id="c8bca-182">Anger att denna cmdlet tillåter omdirigering av anslutningen till en alternativ Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="c8bca-182">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="c8bca-183">När du använder **ConnectionURI** -parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI.</span><span class="sxs-lookup"><span data-stu-id="c8bca-183">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="c8bca-184">Som standard omdirigerar PowerShell inte anslutningar, men du kan använda den här parametern för att aktivera den för att omdirigera anslutningen.</span><span class="sxs-lookup"><span data-stu-id="c8bca-184">By default, PowerShell does not redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="c8bca-185">Du kan också begränsa hur många gånger anslutningen omdirigeras genom att ändra värdet för alternativet **MaximumConnectionRedirectionCount** session.</span><span class="sxs-lookup"><span data-stu-id="c8bca-185">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="c8bca-186">Använd parametern **MaximumRedirection** för `New-PSSessionOption` cmdleten eller ange egenskapen **MaximumConnectionRedirectionCount** för variabeln **$PSSessionOption** .</span><span class="sxs-lookup"><span data-stu-id="c8bca-186">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="c8bca-187">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="c8bca-187">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-188">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="c8bca-188">-ApplicationName</span></span>

<span data-ttu-id="c8bca-189">Anger program namns segmentet för anslutnings-URI: n.</span><span class="sxs-lookup"><span data-stu-id="c8bca-189">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="c8bca-190">Använd den här parametern för att ange program namnet när du inte använder parametern **ConnectionURI** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="c8bca-190">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="c8bca-191">Standardvärdet är värdet för Preference- `$PSSessionApplicationName` variabeln på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-191">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="c8bca-192">Om den här preferens variabeln inte definieras är standardvärdet WSMAN.</span><span class="sxs-lookup"><span data-stu-id="c8bca-192">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="c8bca-193">Det här värdet är lämpligt för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="c8bca-193">This value is appropriate for most uses.</span></span> <span data-ttu-id="c8bca-194">Mer information finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="c8bca-194">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="c8bca-195">WinRM-tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran.</span><span class="sxs-lookup"><span data-stu-id="c8bca-195">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="c8bca-196">Värdet för den här parametern ska matcha värdet på egenskapen **URLPrefix** för en lyssnare på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-196">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-197">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="c8bca-197">-Authentication</span></span>

<span data-ttu-id="c8bca-198">Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="c8bca-198">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="c8bca-199">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="c8bca-199">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c8bca-200">Default</span><span class="sxs-lookup"><span data-stu-id="c8bca-200">Default</span></span>
- <span data-ttu-id="c8bca-201">Basic</span><span class="sxs-lookup"><span data-stu-id="c8bca-201">Basic</span></span>
- <span data-ttu-id="c8bca-202">CredSSP</span><span class="sxs-lookup"><span data-stu-id="c8bca-202">Credssp</span></span>
- <span data-ttu-id="c8bca-203">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="c8bca-203">Digest</span></span>
- <span data-ttu-id="c8bca-204">Kerberos</span><span class="sxs-lookup"><span data-stu-id="c8bca-204">Kerberos</span></span>
- <span data-ttu-id="c8bca-205">Negotiate</span><span class="sxs-lookup"><span data-stu-id="c8bca-205">Negotiate</span></span>
- <span data-ttu-id="c8bca-206">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="c8bca-206">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="c8bca-207">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="c8bca-207">The default value is Default.</span></span>

<span data-ttu-id="c8bca-208">Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="c8bca-208">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="c8bca-209">CredSSP-autentisering (Credential Security Support Provider), där användarautentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="c8bca-209">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="c8bca-210">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="c8bca-210">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="c8bca-211">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="c8bca-211">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-212">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="c8bca-212">-CertificateThumbprint</span></span>

<span data-ttu-id="c8bca-213">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c8bca-213">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="c8bca-214">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="c8bca-214">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="c8bca-215">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="c8bca-215">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="c8bca-216">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="c8bca-216">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="c8bca-217">Hämta ett certifikat med hjälp av `Get-Item` kommandot eller `Get-ChildItem` i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="c8bca-217">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="c8bca-218">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="c8bca-218">-ComputerName</span></span>

<span data-ttu-id="c8bca-219">Anger en matris med namn på datorer.</span><span class="sxs-lookup"><span data-stu-id="c8bca-219">Specifies an array of names of computers.</span></span> <span data-ttu-id="c8bca-220">Denna cmdlet skapar en permanent anslutning ( **PSSession** ) till den angivna datorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-220">This cmdlet creates a persistent connection ( **PSSession** ) to the specified computer.</span></span> <span data-ttu-id="c8bca-221">Om du anger flera dator namn `New-PSSession` skapas flera **PSSession** -objekt, ett för varje dator.</span><span class="sxs-lookup"><span data-stu-id="c8bca-221">If you enter multiple computer names, `New-PSSession` creates multiple **PSSession** objects, one for each computer.</span></span> <span data-ttu-id="c8bca-222">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-222">The default is the local computer.</span></span>

<span data-ttu-id="c8bca-223">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="c8bca-223">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="c8bca-224">Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.).</span><span class="sxs-lookup"><span data-stu-id="c8bca-224">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="c8bca-225">När datorn finns i en annan domän än användaren, krävs det fullständigt kvalificerade domän namnet.</span><span class="sxs-lookup"><span data-stu-id="c8bca-225">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="c8bca-226">Du kan också skicka ett dator namn inom citat tecken till `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="c8bca-226">You can also pipe a computer name, in quotation marks, to `New-PSSession`.</span></span>

<span data-ttu-id="c8bca-227">Om du vill använda en IP-adress i värdet för parametern **computername** måste kommandot innehålla parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="c8bca-227">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="c8bca-228">Dessutom måste datorn konfigureras för HTTPS-transport eller fjärrdatorns IP-adress måste ingå i listan WinRM TrustedHosts på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-228">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="c8bca-229">Instruktioner för att lägga till ett dator namn i listan TrustedHosts finns i avsnittet om hur du lägger till en dator i listan över betrodda värdar i [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="c8bca-229">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="c8bca-230">Om du vill inkludera den lokala datorn i värdet för parametern **computername** startar du Windows PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="c8bca-230">To include the local computer in the value of the **ComputerName** parameter, start Windows PowerShell by using the Run as administrator option.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-231">– ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="c8bca-231">-ConfigurationName</span></span>

<span data-ttu-id="c8bca-232">Anger den sessionsinformation som används för den nya **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="c8bca-232">Specifies the session configuration that is used for the new **PSSession**.</span></span>

<span data-ttu-id="c8bca-233">Ange ett konfigurations namn eller den fullständigt kvalificerade resurs-URI: n för en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="c8bca-233">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="c8bca-234">Om du bara anger konfigurations namnet är följande schema-URI anpassningsprefix: `http://schemas.microsoft.com/PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="c8bca-234">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="c8bca-235">Sessionens konfiguration för en session finns på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-235">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="c8bca-236">Om den angivna konfigurationen av sessionen inte finns på fjärrdatorn Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="c8bca-236">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="c8bca-237">Standardvärdet är värdet för Preference- `$PSSessionConfigurationName` variabeln på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-237">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="c8bca-238">Om den här preferens variabeln inte anges är standardvärdet Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8bca-238">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="c8bca-239">Mer information finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="c8bca-239">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-240">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="c8bca-240">-ConnectionUri</span></span>

<span data-ttu-id="c8bca-241">Anger en URI som definierar anslutnings slut punkten för sessionen.</span><span class="sxs-lookup"><span data-stu-id="c8bca-241">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="c8bca-242">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="c8bca-242">The URI must be fully qualified.</span></span> <span data-ttu-id="c8bca-243">Formatet för den här strängen är följande:</span><span class="sxs-lookup"><span data-stu-id="c8bca-243">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="c8bca-244">Standardvärdet är följande:</span><span class="sxs-lookup"><span data-stu-id="c8bca-244">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="c8bca-245">Om du inte anger en **ConnectionURI** kan du använda parametrarna **UseSSL** , **computername** , **port** och **ApplicationName** för att ange **ConnectionURI** -värden.</span><span class="sxs-lookup"><span data-stu-id="c8bca-245">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="c8bca-246">Giltiga värden för URI: n i transport segmentet är HTTP och HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c8bca-246">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="c8bca-247">Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med standard portar: 80 för HTTP och 443 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c8bca-247">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="c8bca-248">Om du vill använda standard portarna för PowerShell-fjärrkommunikation anger du Port 5985 för HTTP eller 5986 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c8bca-248">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="c8bca-249">Om mål datorn omdirigerar anslutningen till en annan URI, förhindrar PowerShell omdirigeringen om du inte använder parametern **AllowRedirection** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="c8bca-249">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: Uri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-250">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="c8bca-250">-ContainerId</span></span>

<span data-ttu-id="c8bca-251">Anger en matris med ID: n för behållare.</span><span class="sxs-lookup"><span data-stu-id="c8bca-251">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="c8bca-252">Den här cmdleten startar en interaktiv session med var och en av de angivna behållarna.</span><span class="sxs-lookup"><span data-stu-id="c8bca-252">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="c8bca-253">Använd `docker ps` kommandot för att hämta en lista över behållar-ID: n.</span><span class="sxs-lookup"><span data-stu-id="c8bca-253">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="c8bca-254">Mer information finns i hjälpen för kommandot [Docker PS](https://docs.docker.com/engine/reference/commandline/ps/) .</span><span class="sxs-lookup"><span data-stu-id="c8bca-254">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-255">-Credential</span><span class="sxs-lookup"><span data-stu-id="c8bca-255">-Credential</span></span>

<span data-ttu-id="c8bca-256">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c8bca-256">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="c8bca-257">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="c8bca-257">The default is the current user.</span></span>

<span data-ttu-id="c8bca-258">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c8bca-258">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="c8bca-259">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="c8bca-259">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="c8bca-260">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="c8bca-260">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="c8bca-261">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="c8bca-261">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-262">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="c8bca-262">-EnableNetworkAccess</span></span>

<span data-ttu-id="c8bca-263">Anger att denna cmdlet lägger till en interaktiv säkerhetstoken till loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="c8bca-263">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="c8bca-264">Med den interaktiva token kan du köra kommandon i loopback-sessionen som hämtar data från andra datorer.</span><span class="sxs-lookup"><span data-stu-id="c8bca-264">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="c8bca-265">Du kan till exempel köra ett kommando i sessionen som kopierar XML-filer från en fjärrdator till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-265">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="c8bca-266">En loopback-session är en **PSSession** som kommer från och slutar på samma dator.</span><span class="sxs-lookup"><span data-stu-id="c8bca-266">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="c8bca-267">Om du vill skapa en loopback-session utelämnar du parametern **computername** eller anger värdet för punkt (.), localhost eller namnet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-267">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (.), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="c8bca-268">Som standard skapar denna cmdlet loopback-sessioner med hjälp av en nätverks-token som kanske inte ger tillräcklig behörighet att autentisera till fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="c8bca-268">By default, this cmdlet creates loopback sessions by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="c8bca-269">Parametern **EnableNetworkAccess** är endast effektiv i loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="c8bca-269">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="c8bca-270">Om du använder **EnableNetworkAccess** när du skapar en-session på en fjärrdator, lyckas kommandot, men parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="c8bca-270">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="c8bca-271">Du kan också aktivera fjärråtkomst i en loopback-session med hjälp av CredSSP-värdet för parametern **Authentication** , som delegerar autentiseringsuppgifterna för sessionen till andra datorer.</span><span class="sxs-lookup"><span data-stu-id="c8bca-271">You can also enable remote access in a loopback session by using the CredSSP value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="c8bca-272">För att skydda datorn från skadlig åtkomst kan frånkopplade loopback-sessioner med interaktiva token, som är de som skapats med hjälp av parametern **EnableNetworkAccess** , bara återanslutas från den dator där sessionen skapades.</span><span class="sxs-lookup"><span data-stu-id="c8bca-272">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="c8bca-273">Frånkopplade sessioner som använder CredSSP-autentisering kan återanslutas från andra datorer.</span><span class="sxs-lookup"><span data-stu-id="c8bca-273">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="c8bca-274">Mer information finns i `Disconnect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="c8bca-274">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="c8bca-275">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c8bca-275">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri, Session
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-276">-Name</span><span class="sxs-lookup"><span data-stu-id="c8bca-276">-Name</span></span>

<span data-ttu-id="c8bca-277">Anger ett eget namn för **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="c8bca-277">Specifies a friendly name for the **PSSession**.</span></span>

<span data-ttu-id="c8bca-278">Du kan använda namnet för att referera till **PSSession** när du använder andra cmdlets, till exempel `Get-PSSession` och `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="c8bca-278">You can use the name to refer to the **PSSession** when you use other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="c8bca-279">Namnet måste inte vara unikt för datorn eller den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c8bca-279">The name is not required to be unique to the computer or the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-280">-Port</span><span class="sxs-lookup"><span data-stu-id="c8bca-280">-Port</span></span>

<span data-ttu-id="c8bca-281">Anger nätverks porten på den fjärrdator som används för den här anslutningen.</span><span class="sxs-lookup"><span data-stu-id="c8bca-281">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="c8bca-282">Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder.</span><span class="sxs-lookup"><span data-stu-id="c8bca-282">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="c8bca-283">Standard portarna är 5985, som är WinRM-porten för HTTP och 5986, som är WinRM-porten för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c8bca-283">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="c8bca-284">Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.</span><span class="sxs-lookup"><span data-stu-id="c8bca-284">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="c8bca-285">Använd följande kommandon för att konfigurera lyssnaren:</span><span class="sxs-lookup"><span data-stu-id="c8bca-285">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="c8bca-286">Använd inte **port** parametern om du inte behöver.</span><span class="sxs-lookup"><span data-stu-id="c8bca-286">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="c8bca-287">Port inställningen i kommandot gäller för alla datorer eller sessioner där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="c8bca-287">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="c8bca-288">En alternativ port inställning kan hindra kommandot från att köras på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="c8bca-288">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-289">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="c8bca-289">-RunAsAdministrator</span></span>

<span data-ttu-id="c8bca-290">Anger att **PSSession** körs som administratör.</span><span class="sxs-lookup"><span data-stu-id="c8bca-290">Indicates that the **PSSession** runs as administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-291">– Session</span><span class="sxs-lookup"><span data-stu-id="c8bca-291">-Session</span></span>

<span data-ttu-id="c8bca-292">Anger en matris med **PSSession** -objekt som denna cmdlet använder som en modell för den nya **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="c8bca-292">Specifies an array of **PSSession** objects that this cmdlet uses as a model for the new **PSSession**.</span></span> <span data-ttu-id="c8bca-293">Den här parametern skapar nya **PSSession** -objekt som har samma egenskaper som de angivna **PSSession** -objekten.</span><span class="sxs-lookup"><span data-stu-id="c8bca-293">This parameter creates new **PSSession** objects that have the same properties as the specified **PSSession** objects.</span></span>

<span data-ttu-id="c8bca-294">Ange en variabel som innehåller **PSSession** -objekt eller ett kommando som skapar eller hämtar **PSSession** -objekt, till exempel ett- `New-PSSession` eller- `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="c8bca-294">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="c8bca-295">De resulterande **PSSession** -objekten har samma dator namn, program namn, ANSLUTNINGS-URI, port, konfigurations namn, begränsnings gräns och Secure SOCKETS Layer (SSL)-värde som original, men de har olika visnings namn, ID och instans-ID (GUID).</span><span class="sxs-lookup"><span data-stu-id="c8bca-295">The resulting **PSSession** objects have the same computer name, application name, connection URI, port, configuration name, throttle limit, and Secure Sockets Layer (SSL) value as the originals, but they have a different display name, ID, and instance ID (GUID).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-296">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="c8bca-296">-SessionOption</span></span>

<span data-ttu-id="c8bca-297">Anger avancerade alternativ för sessionen.</span><span class="sxs-lookup"><span data-stu-id="c8bca-297">Specifies advanced options for the session.</span></span> <span data-ttu-id="c8bca-298">Ange ett **SessionOption** -objekt, t. ex. ett som du skapar med hjälp av `New-PSSessionOption` cmdleten, eller en hash-tabell där nycklarna är namn på sessionstillstånd och värdena är alternativ värden för session.</span><span class="sxs-lookup"><span data-stu-id="c8bca-298">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="c8bca-299">Standardvärdena för alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts.</span><span class="sxs-lookup"><span data-stu-id="c8bca-299">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="c8bca-300">Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="c8bca-300">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="c8bca-301">Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i `$PSSessionOption` variabeln Preference och i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="c8bca-301">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="c8bca-302">De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="c8bca-302">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="c8bca-303">En beskrivning av de sessionsinformation som innehåller standardvärdena finns i `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="c8bca-303">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="c8bca-304">Information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="c8bca-304">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="c8bca-305">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="c8bca-305">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-306">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="c8bca-306">-ThrottleLimit</span></span>

<span data-ttu-id="c8bca-307">Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="c8bca-307">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="c8bca-308">Om du utelämnar den här parametern eller anger värdet 0 (noll) används standardvärdet 32.</span><span class="sxs-lookup"><span data-stu-id="c8bca-308">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span>

<span data-ttu-id="c8bca-309">Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-309">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-310">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="c8bca-310">-UseSSL</span></span>

<span data-ttu-id="c8bca-311">Anger att denna cmdlet använder SSL-protokollet för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c8bca-311">Indicates that this cmdlet uses the SSL protocol to establish a connection to the remote computer.</span></span>
<span data-ttu-id="c8bca-312">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="c8bca-312">By default, SSL is not used.</span></span>

<span data-ttu-id="c8bca-313">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="c8bca-313">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="c8bca-314">Parametern **UseSSL** erbjuder ytterligare ett skydd som skickar data via en HTTPS-anslutning i stället för en HTTP-anslutning.</span><span class="sxs-lookup"><span data-stu-id="c8bca-314">The **UseSSL** parameter offers an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="c8bca-315">Om du använder den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="c8bca-315">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-316">-VMId</span><span class="sxs-lookup"><span data-stu-id="c8bca-316">-VMId</span></span>

<span data-ttu-id="c8bca-317">Anger en matris med ID för virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="c8bca-317">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="c8bca-318">Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna.</span><span class="sxs-lookup"><span data-stu-id="c8bca-318">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="c8bca-319">Använd följande kommando för att se de virtuella datorer som är tillgängliga för dig:</span><span class="sxs-lookup"><span data-stu-id="c8bca-319">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-320">– VMName</span><span class="sxs-lookup"><span data-stu-id="c8bca-320">-VMName</span></span>

<span data-ttu-id="c8bca-321">Anger en matris med namn på virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="c8bca-321">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="c8bca-322">Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna.</span><span class="sxs-lookup"><span data-stu-id="c8bca-322">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="c8bca-323">Använd cmdleten för att se de virtuella datorer som är tillgängliga för dig `Get-VM` .</span><span class="sxs-lookup"><span data-stu-id="c8bca-323">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c8bca-324">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c8bca-324">CommonParameters</span></span>

<span data-ttu-id="c8bca-325">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c8bca-325">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c8bca-326">Mer information finns i about_CommonParameters ( https://go.microsoft.com/fwlink/?LinkID=113216) .</span><span class="sxs-lookup"><span data-stu-id="c8bca-326">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c8bca-327">INDATA</span><span class="sxs-lookup"><span data-stu-id="c8bca-327">INPUTS</span></span>

### <span data-ttu-id="c8bca-328">System. String, system. URI, system. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="c8bca-328">System.String, System.URI, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="c8bca-329">Du kan skicka en sträng, en URI eller ett sessionsobjekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c8bca-329">You can pipe a string, URI, or session object to this cmdlet.</span></span>

## <span data-ttu-id="c8bca-330">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c8bca-330">OUTPUTS</span></span>

### <span data-ttu-id="c8bca-331">System. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="c8bca-331">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="c8bca-332">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c8bca-332">NOTES</span></span>

- <span data-ttu-id="c8bca-333">Denna cmdlet använder PowerShell-infrastrukturen för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="c8bca-333">This cmdlet uses the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="c8bca-334">Om du vill använda den här cmdleten måste den lokala datorn och alla fjärrdatorer konfigureras för PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="c8bca-334">To use this cmdlet, the local computer and any remote computers must be configured for PowerShell remoting.</span></span> <span data-ttu-id="c8bca-335">Mer information finns i [about_Remote_Requirements](About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8bca-335">For more information, see [about_Remote_Requirements](About/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="c8bca-336">Om du vill skapa en **PSSession** på den lokala datorn startar du PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="c8bca-336">To create a **PSSession** on the local computer, start PowerShell with the Run as administrator option.</span></span>
- <span data-ttu-id="c8bca-337">När du är färdig med **PSSession** kan du använda `Remove-PSSession` cmdleten för att ta bort **PSSession** och släppa dess resurser.</span><span class="sxs-lookup"><span data-stu-id="c8bca-337">When you are finished with the **PSSession** , use the `Remove-PSSession` cmdlet to delete the **PSSession** and release its resources.</span></span>

## <span data-ttu-id="c8bca-338">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c8bca-338">RELATED LINKS</span></span>

[<span data-ttu-id="c8bca-339">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="c8bca-339">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="c8bca-340">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="c8bca-340">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="c8bca-341">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="c8bca-341">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="c8bca-342">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="c8bca-342">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="c8bca-343">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="c8bca-343">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="c8bca-344">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="c8bca-344">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="c8bca-345">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="c8bca-345">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="c8bca-346">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="c8bca-346">Remove-PSSession</span></span>](Remove-PSSession.md)
