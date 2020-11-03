---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: 90bd1d539bb6bc071df6bfcf326adc57e24fff8f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268364"
---
# <span data-ttu-id="35f5e-103">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="35f5e-103">New-PSSession</span></span>

## <span data-ttu-id="35f5e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="35f5e-104">SYNOPSIS</span></span>
<span data-ttu-id="35f5e-105">Skapar en permanent anslutning till en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="35f5e-105">Creates a persistent connection to a local or remote computer.</span></span>

## <span data-ttu-id="35f5e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="35f5e-106">SYNTAX</span></span>

### <span data-ttu-id="35f5e-107">ComputerName (standard)</span><span class="sxs-lookup"><span data-stu-id="35f5e-107">ComputerName (Default)</span></span>

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="35f5e-108">VMId</span><span class="sxs-lookup"><span data-stu-id="35f5e-108">VMId</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="35f5e-109">URI</span><span class="sxs-lookup"><span data-stu-id="35f5e-109">Uri</span></span>

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="35f5e-110">VMName</span><span class="sxs-lookup"><span data-stu-id="35f5e-110">VMName</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="35f5e-111">Session</span><span class="sxs-lookup"><span data-stu-id="35f5e-111">Session</span></span>

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="35f5e-112">Hålla</span><span class="sxs-lookup"><span data-stu-id="35f5e-112">ContainerId</span></span>

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="35f5e-113">SSHHost</span><span class="sxs-lookup"><span data-stu-id="35f5e-113">SSHHost</span></span>

```
New-PSSession [-Name <String[]>] [-Port <Int32>] [-HostName] <String[]> [-UserName <String>]
 [-KeyFilePath <String>] [-SSHTransport] [-Subsystem <String>] [<CommonParameters>]
```

### <span data-ttu-id="35f5e-114">SSHHostHashParam</span><span class="sxs-lookup"><span data-stu-id="35f5e-114">SSHHostHashParam</span></span>

```
New-PSSession [-Name <String[]>] -SSHConnection <Hashtable[]> [<CommonParameters>]
```

## <span data-ttu-id="35f5e-115">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="35f5e-115">DESCRIPTION</span></span>

<span data-ttu-id="35f5e-116">`New-PSSession`Cmdleten skapar en PowerShell-session ( **PSSession** ) på en lokal eller fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="35f5e-116">The `New-PSSession` cmdlet creates a PowerShell session ( **PSSession** ) on a local or remote computer.</span></span> <span data-ttu-id="35f5e-117">När du skapar en **PSSession** upprättar PowerShell en permanent anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-117">When you create a **PSSession** , PowerShell establishes a persistent connection to the remote computer.</span></span>

<span data-ttu-id="35f5e-118">Använd en **PSSession** för att köra flera kommandon som delar data, till exempel en funktion eller värdet för en variabel.</span><span class="sxs-lookup"><span data-stu-id="35f5e-118">Use a **PSSession** to run multiple commands that share data, such as a function or the value of a variable.</span></span> <span data-ttu-id="35f5e-119">Om du vill köra kommandon i en **PSSession** använder du `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="35f5e-119">To run commands in a **PSSession** , use the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="35f5e-120">Använd cmdleten om du vill använda **PSSession** för att interagera direkt med en fjärrdator `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="35f5e-120">To use the **PSSession** to interact directly with a remote computer, use the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="35f5e-121">Mer information finns i [about_PSSessions](about/about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="35f5e-121">For more information, see [about_PSSessions](about/about_PSSessions.md).</span></span>

<span data-ttu-id="35f5e-122">Du kan köra kommandon på en fjärrdator utan att skapa en **PSSession** med hjälp av **computername** -parametrarna för `Enter-PSSession` eller `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="35f5e-122">You can run commands on a remote computer without creating a **PSSession** by using the **ComputerName** parameters of `Enter-PSSession` or `Invoke-Command`.</span></span> <span data-ttu-id="35f5e-123">När du använder parametern **computername** skapar PowerShell en tillfällig anslutning som används för kommandot och stängs sedan.</span><span class="sxs-lookup"><span data-stu-id="35f5e-123">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that is used for the command and is then closed.</span></span>

<span data-ttu-id="35f5e-124">Från och med PowerShell 6,0 kan du använda SSH (Secure Shell) för att upprätta en anslutning till och skapa en session på en fjärrdator, om SSH är tillgängligt på den lokala datorn och fjärrdatorn har kon figurer ATS med en PowerShell SSH-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="35f5e-124">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to and create a session on a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="35f5e-125">Fördelen med en SSH-baserad PowerShell-fjärrsession är att den kan fungera på flera plattformar (Windows, Linux och macOS).</span><span class="sxs-lookup"><span data-stu-id="35f5e-125">The benefit of an SSH based PowerShell remote session is that it can work across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="35f5e-126">För SSH-baserade sessioner använder du parametern **hostname** eller **SSHConnection** för att ange fjärrdatorn och relevant anslutnings information.</span><span class="sxs-lookup"><span data-stu-id="35f5e-126">For SSH based sessions you use the **HostName** or **SSHConnection** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="35f5e-127">Mer information om hur du konfigurerar PowerShell SSH-fjärrkommunikation finns i [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="35f5e-127">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="35f5e-128">När du använder WSMan-fjärrkommunikation från en Linux-eller macOS-klient med en HTTPS-slutpunkt där Server certifikatet inte är betrott (t. ex. ett självsignerat certifikat).</span><span class="sxs-lookup"><span data-stu-id="35f5e-128">When using WSMan remoting from a Linux or macOS client with a HTTPS endpoint where the server certificate is not trusted (e.g., a self-signed certificate).</span></span> <span data-ttu-id="35f5e-129">Du måste ange en `PSSessionOption` som inkluderar `-SkipCACheck` och `-SkipCNCheck` för att kunna upprätta anslutningen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-129">You must provide a `PSSessionOption` that includes `-SkipCACheck` and `-SkipCNCheck` to successfully establish the connection.</span></span> <span data-ttu-id="35f5e-130">Gör bara detta om du är i en miljö där du kan vara säker på Server certifikatet och nätverks anslutningen till mål systemet.</span><span class="sxs-lookup"><span data-stu-id="35f5e-130">Only do this if you are in an environment where you can be certain of the server certificate and the network connection to the target system.</span></span>

## <span data-ttu-id="35f5e-131">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="35f5e-131">EXAMPLES</span></span>

### <span data-ttu-id="35f5e-132">Exempel 1: skapa en session på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="35f5e-132">Example 1: Create a session on the local computer</span></span>

```powershell
$s = New-PSSession
```

<span data-ttu-id="35f5e-133">Det här kommandot skapar en ny **PSSession** på den lokala datorn och sparar **PSSession** i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="35f5e-133">This command creates a new **PSSession** on the local computer and saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="35f5e-134">Nu kan du använda den här **PSSession** för att köra kommandon på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-134">You can now use this **PSSession** to run commands on the local computer.</span></span>

### <span data-ttu-id="35f5e-135">Exempel 2: skapa en session på en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="35f5e-135">Example 2: Create a session on a remote computer</span></span>

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

<span data-ttu-id="35f5e-136">Det här kommandot skapar en ny **PSSession** på Server01-datorn och sparar det i `$Server01` variabeln.</span><span class="sxs-lookup"><span data-stu-id="35f5e-136">This command creates a new **PSSession** on the Server01 computer and saves it in the `$Server01` variable.</span></span>

<span data-ttu-id="35f5e-137">När du skapar flera **PSSession** -objekt tilldelar du dem till variabler med användbara namn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-137">When creating multiple **PSSession** objects, assign them to variables with useful names.</span></span> <span data-ttu-id="35f5e-138">Detta hjälper dig att hantera **PSSession** -objekt i efterföljande kommandon.</span><span class="sxs-lookup"><span data-stu-id="35f5e-138">This will help you manage the **PSSession** objects in subsequent commands.</span></span>

### <span data-ttu-id="35f5e-139">Exempel 3: skapa sessioner på flera datorer</span><span class="sxs-lookup"><span data-stu-id="35f5e-139">Example 3: Create sessions on multiple computers</span></span>

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

<span data-ttu-id="35f5e-140">Det här kommandot skapar tre **PSSession** -objekt, ett på varje dator som anges av parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="35f5e-140">This command creates three **PSSession** objects, one on each of the computers specified by the **ComputerName** parameter.</span></span>

<span data-ttu-id="35f5e-141">Kommandot använder tilldelnings operatorn (=) för att tilldela de nya **PSSession** -objekten till variabler: `$s1` , `$s2` , `$s3` .</span><span class="sxs-lookup"><span data-stu-id="35f5e-141">The command uses the assignment operator (=) to assign the new **PSSession** objects to variables: `$s1`, `$s2`, `$s3`.</span></span> <span data-ttu-id="35f5e-142">Den tilldelar Server01- **PSSession** till `$s1` , Server02 **PSSession** till `$s2` och Server03 **PSSession** till `$s3` .</span><span class="sxs-lookup"><span data-stu-id="35f5e-142">It assigns the Server01 **PSSession** to `$s1`, the Server02 **PSSession** to `$s2`, and the Server03 **PSSession** to `$s3`.</span></span>

<span data-ttu-id="35f5e-143">När du tilldelar flera objekt till en serie med variabler tilldelar PowerShell varje objekt till en variabel i serien.</span><span class="sxs-lookup"><span data-stu-id="35f5e-143">When you assign multiple objects to a series of variables, PowerShell assigns each object to a variable in the series respectively.</span></span> <span data-ttu-id="35f5e-144">Om det finns fler objekt än variabler tilldelas alla återstående objekt den sista variabeln.</span><span class="sxs-lookup"><span data-stu-id="35f5e-144">If there are more objects than variables, all remaining objects are assigned to the last variable.</span></span> <span data-ttu-id="35f5e-145">Om det finns fler variabler än objekt är de återstående variablerna tomma (null).</span><span class="sxs-lookup"><span data-stu-id="35f5e-145">If there are more variables than objects, the remaining variables are empty (null).</span></span>

### <span data-ttu-id="35f5e-146">Exempel 4: skapa en session med en angiven port</span><span class="sxs-lookup"><span data-stu-id="35f5e-146">Example 4: Create a session with a specified port</span></span>

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

<span data-ttu-id="35f5e-147">Det här kommandot skapar en ny **PSSession** på Server01-datorn som ansluter till server port 8081 och använder SSL-protokollet.</span><span class="sxs-lookup"><span data-stu-id="35f5e-147">This command creates a new **PSSession** on the Server01 computer that connects to server port 8081 and uses the SSL protocol.</span></span> <span data-ttu-id="35f5e-148">Den nya **PSSession** använder en alternativ sessionsinformation med namnet E12.</span><span class="sxs-lookup"><span data-stu-id="35f5e-148">The new **PSSession** uses an alternative session configuration called E12.</span></span>

<span data-ttu-id="35f5e-149">Innan du anger porten måste du konfigurera WinRM-lyssnaren på fjärrdatorn så att den lyssnar på port 8081.</span><span class="sxs-lookup"><span data-stu-id="35f5e-149">Before setting the port, you must configure the WinRM listener on the remote computer to listen on port 8081.</span></span> <span data-ttu-id="35f5e-150">Mer information finns i beskrivningen av **port** parametern.</span><span class="sxs-lookup"><span data-stu-id="35f5e-150">For more information, see the description of the **Port** parameter.</span></span>

### <span data-ttu-id="35f5e-151">Exempel 5: skapa en session baserad på en befintlig session</span><span class="sxs-lookup"><span data-stu-id="35f5e-151">Example 5: Create a session based on an existing session</span></span>

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

<span data-ttu-id="35f5e-152">Det här kommandot skapar en **PSSession** med samma egenskaper som en befintlig **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="35f5e-152">This command creates a **PSSession** with the same properties as an existing **PSSession**.</span></span> <span data-ttu-id="35f5e-153">Du kan använda det här kommando formatet när resurserna för en befintlig **PSSession** är uttömda och en ny **PSSession** krävs för att avlasta en del av behovet.</span><span class="sxs-lookup"><span data-stu-id="35f5e-153">You can use this command format when the resources of an existing **PSSession** are exhausted and a new **PSSession** is needed to offload some of the demand.</span></span>

<span data-ttu-id="35f5e-154">Kommandot använder parametern **session** för `New-PSSession` för att ange **PSSession** som sparats i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="35f5e-154">The command uses the **Session** parameter of `New-PSSession` to specify the **PSSession** saved in the `$s` variable.</span></span> <span data-ttu-id="35f5e-155">Den använder Domain1\Admin01-användarens autentiseringsuppgifter för att slutföra kommandot.</span><span class="sxs-lookup"><span data-stu-id="35f5e-155">It uses the credentials of the Domain1\Admin01 user to complete the command.</span></span>

### <span data-ttu-id="35f5e-156">Exempel 6: skapa en session med en global omfattning i en annan domän</span><span class="sxs-lookup"><span data-stu-id="35f5e-156">Example 6: Create a session with a global scope in a different domain</span></span>

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

<span data-ttu-id="35f5e-157">Det här exemplet visar hur du skapar en **PSSession** med ett globalt omfång på en dator i en annan domän.</span><span class="sxs-lookup"><span data-stu-id="35f5e-157">This example shows how to create a **PSSession** with a global scope on a computer in a different domain.</span></span>

<span data-ttu-id="35f5e-158">Som standard skapas **PSSession** -objekt som skapas på kommando raden med lokala scope-och **PSSession** -objekt som skapats i ett skript som har skript omfattning.</span><span class="sxs-lookup"><span data-stu-id="35f5e-158">By default, **PSSession** objects created at the command line are created with local scope and **PSSession** objects created in a script have script scope.</span></span>

<span data-ttu-id="35f5e-159">Skapa en **PSSession** med global omfattning genom att skapa en ny **PSSession** och sedan lagra **PSSession** i en variabel som är Cast till en global omfattning.</span><span class="sxs-lookup"><span data-stu-id="35f5e-159">To create a **PSSession** with global scope, create a new **PSSession** and then store the **PSSession** in a variable that is cast to a global scope.</span></span> <span data-ttu-id="35f5e-160">I det här fallet `$s` omvandlas variabeln till en global omfattning.</span><span class="sxs-lookup"><span data-stu-id="35f5e-160">In this case, the `$s` variable is cast to a global scope.</span></span>

<span data-ttu-id="35f5e-161">Kommandot använder parametern **computername** för att ange fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-161">The command uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="35f5e-162">Eftersom datorn finns i en annan domän än användar kontot, anges det fullständiga namnet på datorn tillsammans med autentiseringsuppgifterna för användaren.</span><span class="sxs-lookup"><span data-stu-id="35f5e-162">Because the computer is in a different domain than the user account, the full name of the computer is specified together with the credentials of the user.</span></span>

### <span data-ttu-id="35f5e-163">Exempel 7: skapa sessioner för många datorer</span><span class="sxs-lookup"><span data-stu-id="35f5e-163">Example 7: Create sessions for many computers</span></span>

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

<span data-ttu-id="35f5e-164">Det här kommandot skapar en **PSSession** på var och en av de 200 datorer som anges i Servers.txt-filen och lagrar den resulterande **PSSession** i `$rs` variabeln.</span><span class="sxs-lookup"><span data-stu-id="35f5e-164">This command creates a **PSSession** on each of the 200 computers listed in the Servers.txt file and it stores the resulting **PSSession** in the `$rs` variable.</span></span> <span data-ttu-id="35f5e-165">**PSSession** -objekten har en begränsnings gräns på 50.</span><span class="sxs-lookup"><span data-stu-id="35f5e-165">The **PSSession** objects have a throttle limit of 50.</span></span>

<span data-ttu-id="35f5e-166">Du kan använda det här kommando formatet när namnen på datorerna lagras i en databas, ett kalkyl blad, i en textfil eller i ett annat format som kan konverteras.</span><span class="sxs-lookup"><span data-stu-id="35f5e-166">You can use this command format when the names of computers are stored in a database, spreadsheet, text file, or other text-convertible format.</span></span>

### <span data-ttu-id="35f5e-167">Exempel 8: skapa en session med en URI</span><span class="sxs-lookup"><span data-stu-id="35f5e-167">Example 8: Create a session by using a URI</span></span>

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

<span data-ttu-id="35f5e-168">Det här kommandot skapar en **PSSession** på Server01-datorn och lagrar den i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="35f5e-168">This command creates a **PSSession** on the Server01 computer and stores it in the `$s` variable.</span></span> <span data-ttu-id="35f5e-169">Den använder **URI** -parametern för att ange transport protokollet, fjärrdatorn, porten och en alternativ konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-169">It uses the **URI** parameter to specify the transport protocol, the remote computer, the port, and an alternate session configuration.</span></span> <span data-ttu-id="35f5e-170">Den använder också parametern **Credential** för att ange ett användar konto som har behörighet att skapa en session på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-170">It also uses the **Credential** parameter to specify a user account that has permission to create a session on the remote computer.</span></span>

### <span data-ttu-id="35f5e-171">Exempel 9: köra ett bakgrunds jobb i en uppsättning sessioner</span><span class="sxs-lookup"><span data-stu-id="35f5e-171">Example 9: Run a background job in a set of sessions</span></span>

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

<span data-ttu-id="35f5e-172">Dessa kommandon skapar en uppsättning **PSSession** -objekt och kör sedan ett bakgrunds jobb i vart och ett av **PSSession** -objekten.</span><span class="sxs-lookup"><span data-stu-id="35f5e-172">These commands create a set of **PSSession** objects and then run a background job in each of the **PSSession** objects.</span></span>

<span data-ttu-id="35f5e-173">Det första kommandot skapar en ny **PSSession** på var och en av de datorer som anges i Servers.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-173">The first command creates a new **PSSession** on each of the computers listed in the Servers.txt file.</span></span> <span data-ttu-id="35f5e-174">Den använder `New-PSSession` cmdleten för att skapa **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="35f5e-174">It uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span> <span data-ttu-id="35f5e-175">Värdet för parametern **computername** är ett kommando som använder `Get-Content` cmdleten för att hämta listan över dator namn Servers.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-175">The value of the **ComputerName** parameter is a command that uses the `Get-Content` cmdlet to get the list of computer names the Servers.txt file.</span></span>

<span data-ttu-id="35f5e-176">Kommandot använder parametern **Credential** för att skapa **PSSession** -objekt som har behörighet för en domän administratör och använder parametern **ThrottleLimit** för att begränsa kommandot till 16 samtidiga anslutningar.</span><span class="sxs-lookup"><span data-stu-id="35f5e-176">The command uses the **Credential** parameter to create the **PSSession** objects that have the permission of a domain administrator, and it uses the **ThrottleLimit** parameter to limit the command to 16 concurrent connections.</span></span> <span data-ttu-id="35f5e-177">Kommandot sparar **PSSession** -objekten i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="35f5e-177">The command saves the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="35f5e-178">Det andra kommandot använder **AsJob** -parametern för `Invoke-Command` cmdleten för att starta ett bakgrunds jobb som kör ett `Get-Process PowerShell` kommando i varje **PSSession** -objekt i `$s` .</span><span class="sxs-lookup"><span data-stu-id="35f5e-178">The second command uses the **AsJob** parameter of the `Invoke-Command` cmdlet to start a background job that runs a `Get-Process PowerShell` command in each of the **PSSession** objects in `$s`.</span></span>

<span data-ttu-id="35f5e-179">Mer information om PowerShell-bakgrunds jobb finns i [about_Jobs](About/about_Jobs.md) och [about_Remote_Jobs](About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="35f5e-179">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

### <span data-ttu-id="35f5e-180">Exempel 10: skapa en session för en dator med hjälp av dess URI</span><span class="sxs-lookup"><span data-stu-id="35f5e-180">Example 10: Create a session for a computer by using its URI</span></span>

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

<span data-ttu-id="35f5e-181">Det här kommandot skapar ett **PSSession** -objekt som ansluter till en dator som anges av en URI i stället för ett dator namn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-181">This command creates a **PSSession** objects that connects to a computer that is specified by a URI instead of a computer name.</span></span>

### <span data-ttu-id="35f5e-182">Exempel 11: skapa ett session-alternativ</span><span class="sxs-lookup"><span data-stu-id="35f5e-182">Example 11: Create a session option</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

<span data-ttu-id="35f5e-183">I det här exemplet visas hur du skapar ett sessionsobjekt-objekt och använder parametern **SessionOption** .</span><span class="sxs-lookup"><span data-stu-id="35f5e-183">This example shows how to create a session option object and use the **SessionOption** parameter.</span></span>

<span data-ttu-id="35f5e-184">Det första kommandot använder `New-PSSessionOption` cmdleten för att skapa ett session-alternativ.</span><span class="sxs-lookup"><span data-stu-id="35f5e-184">The first command uses the `New-PSSessionOption` cmdlet to create a session option.</span></span> <span data-ttu-id="35f5e-185">Det sparar det resulterande **SessionOption** -objektet i `$so` variabeln.</span><span class="sxs-lookup"><span data-stu-id="35f5e-185">It saves the resulting **SessionOption** object in the `$so` variable.</span></span>

<span data-ttu-id="35f5e-186">Det andra kommandot använder alternativet i en ny session.</span><span class="sxs-lookup"><span data-stu-id="35f5e-186">The second command uses the option in a new session.</span></span> <span data-ttu-id="35f5e-187">Kommandot använder `New-PSSession` cmdleten för att skapa en ny session.</span><span class="sxs-lookup"><span data-stu-id="35f5e-187">The command uses the `New-PSSession` cmdlet to create a new session.</span></span> <span data-ttu-id="35f5e-188">Värdet för parametern SessionOption är **SessionOption** -objektet i `$so` variabeln.</span><span class="sxs-lookup"><span data-stu-id="35f5e-188">The value of the SessionOption parameter is the **SessionOption** object in the `$so` variable.</span></span>

### <span data-ttu-id="35f5e-189">Exempel 12: skapa en session med SSH</span><span class="sxs-lookup"><span data-stu-id="35f5e-189">Example 12: Create a session using SSH</span></span>

```powershell
New-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="35f5e-190">Det här exemplet visar hur du skapar en ny **PSSession** med hjälp av SSH (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="35f5e-190">This example shows how to create a new **PSSession** using Secure Shell (SSH).</span></span> <span data-ttu-id="35f5e-191">Om SSH har kon figurer ATS på fjärrdatorn för att uppmanas att ange lösen ord får du en prompt.</span><span class="sxs-lookup"><span data-stu-id="35f5e-191">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span> <span data-ttu-id="35f5e-192">Annars kommer du att behöva använda SSH-nyckelbaserad användarautentisering.</span><span class="sxs-lookup"><span data-stu-id="35f5e-192">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="35f5e-193">Exempel 13: skapa en session med SSH och ange nyckel för port och användarautentisering</span><span class="sxs-lookup"><span data-stu-id="35f5e-193">Example 13: Create a session using SSH and specify the port and user authentication key</span></span>

```powershell
New-PSSession -HostName UserA@LinuxServer01:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="35f5e-194">Det här exemplet visar hur du skapar en **PSSession** med hjälp av SSH (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="35f5e-194">This example shows how to create a **PSSession** using Secure Shell (SSH).</span></span> <span data-ttu-id="35f5e-195">Den använder **port** parametern för att ange vilken port som ska användas och parametern för nyckel **Sök** vägar för att ange en RSA-nyckel som används för att identifiera och autentisera användaren på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-195">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to identify and authenticate the user on the remote computer.</span></span>

### <span data-ttu-id="35f5e-196">Exempel 14: skapa flera sessioner med SSH</span><span class="sxs-lookup"><span data-stu-id="35f5e-196">Example 14: Create multiple sessions using SSH</span></span>

```powershell
$sshConnections = @{ HostName="WinServer1"; UserName="domain\userA"; KeyFilePath="c:\users\UserA\id_rsa" }, @{ HostName="UserB@LinuxServer5"; KeyFilePath="c:\UserB\<path>\id_rsa" }
New-PSSession -SSHConnection $sshConnections
```

<span data-ttu-id="35f5e-197">Det här exemplet visar hur du skapar flera sessioner med hjälp av SSH (Secure Shell) och **SSHConnection** -parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-197">This example shows how to create multiple sessions using Secure Shell (SSH) and the **SSHConnection** parameter set.</span></span> <span data-ttu-id="35f5e-198">Parametern **SSHConnection** tar en matris med hash-tabeller som innehåller anslutnings information för varje session.</span><span class="sxs-lookup"><span data-stu-id="35f5e-198">The **SSHConnection** parameter takes an array of hash tables that contain connection information for each session.</span></span> <span data-ttu-id="35f5e-199">Observera att det här exemplet kräver att de mål datorerna har SSH konfigurerat för att stödja nyckelbaserad användarautentisering.</span><span class="sxs-lookup"><span data-stu-id="35f5e-199">Note that this example requires that the target remote computers have SSH configured to support key based user authentication.</span></span>

## <span data-ttu-id="35f5e-200">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="35f5e-200">PARAMETERS</span></span>

### <span data-ttu-id="35f5e-201">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="35f5e-201">-AllowRedirection</span></span>

<span data-ttu-id="35f5e-202">Anger att denna cmdlet tillåter omdirigering av anslutningen till en alternativ Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="35f5e-202">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="35f5e-203">När du använder **ConnectionURI** -parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI.</span><span class="sxs-lookup"><span data-stu-id="35f5e-203">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="35f5e-204">Som standard omdirigerar PowerShell inte anslutningar, men du kan använda den här parametern för att aktivera den för att omdirigera anslutningen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-204">By default, PowerShell does not redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="35f5e-205">Du kan också begränsa hur många gånger anslutningen omdirigeras genom att ändra värdet för alternativet **MaximumConnectionRedirectionCount** session.</span><span class="sxs-lookup"><span data-stu-id="35f5e-205">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="35f5e-206">Använd parametern **MaximumRedirection** för `New-PSSessionOption` cmdleten eller ange egenskapen **MaximumConnectionRedirectionCount** för variabeln **$PSSessionOption** .</span><span class="sxs-lookup"><span data-stu-id="35f5e-206">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="35f5e-207">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="35f5e-207">The default value is 5.</span></span>

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

### <span data-ttu-id="35f5e-208">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="35f5e-208">-ApplicationName</span></span>

<span data-ttu-id="35f5e-209">Anger program namns segmentet för anslutnings-URI: n.</span><span class="sxs-lookup"><span data-stu-id="35f5e-209">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="35f5e-210">Använd den här parametern för att ange program namnet när du inte använder parametern **ConnectionURI** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="35f5e-210">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="35f5e-211">Standardvärdet är värdet för Preference- `$PSSessionApplicationName` variabeln på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-211">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="35f5e-212">Om den här preferens variabeln inte definieras är standardvärdet WSMAN.</span><span class="sxs-lookup"><span data-stu-id="35f5e-212">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="35f5e-213">Det här värdet är lämpligt för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="35f5e-213">This value is appropriate for most uses.</span></span> <span data-ttu-id="35f5e-214">Mer information finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="35f5e-214">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="35f5e-215">WinRM-tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran.</span><span class="sxs-lookup"><span data-stu-id="35f5e-215">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="35f5e-216">Värdet för den här parametern ska matcha värdet på egenskapen **URLPrefix** för en lyssnare på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-216">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

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

### <span data-ttu-id="35f5e-217">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="35f5e-217">-Authentication</span></span>

<span data-ttu-id="35f5e-218">Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="35f5e-218">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="35f5e-219">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="35f5e-219">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="35f5e-220">Default</span><span class="sxs-lookup"><span data-stu-id="35f5e-220">Default</span></span>
- <span data-ttu-id="35f5e-221">Basic</span><span class="sxs-lookup"><span data-stu-id="35f5e-221">Basic</span></span>
- <span data-ttu-id="35f5e-222">CredSSP</span><span class="sxs-lookup"><span data-stu-id="35f5e-222">Credssp</span></span>
- <span data-ttu-id="35f5e-223">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="35f5e-223">Digest</span></span>
- <span data-ttu-id="35f5e-224">Kerberos</span><span class="sxs-lookup"><span data-stu-id="35f5e-224">Kerberos</span></span>
- <span data-ttu-id="35f5e-225">Negotiate</span><span class="sxs-lookup"><span data-stu-id="35f5e-225">Negotiate</span></span>
- <span data-ttu-id="35f5e-226">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="35f5e-226">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="35f5e-227">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="35f5e-227">The default value is Default.</span></span>

<span data-ttu-id="35f5e-228">Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="35f5e-228">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="35f5e-229">CredSSP-autentisering (Credential Security Support Provider), där användarautentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="35f5e-229">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="35f5e-230">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="35f5e-230">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="35f5e-231">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-231">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

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

### <span data-ttu-id="35f5e-232">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="35f5e-232">-CertificateThumbprint</span></span>

<span data-ttu-id="35f5e-233">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="35f5e-233">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="35f5e-234">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="35f5e-234">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="35f5e-235">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="35f5e-235">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="35f5e-236">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="35f5e-236">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="35f5e-237">Hämta ett certifikat med hjälp av `Get-Item` kommandot eller `Get-ChildItem` i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="35f5e-237">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="35f5e-238">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="35f5e-238">-ComputerName</span></span>

<span data-ttu-id="35f5e-239">Anger en matris med namn på datorer.</span><span class="sxs-lookup"><span data-stu-id="35f5e-239">Specifies an array of names of computers.</span></span> <span data-ttu-id="35f5e-240">Denna cmdlet skapar en permanent anslutning ( **PSSession** ) till den angivna datorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-240">This cmdlet creates a persistent connection ( **PSSession** ) to the specified computer.</span></span> <span data-ttu-id="35f5e-241">Om du anger flera dator namn `New-PSSession` skapas flera **PSSession** -objekt, ett för varje dator.</span><span class="sxs-lookup"><span data-stu-id="35f5e-241">If you enter multiple computer names, `New-PSSession` creates multiple **PSSession** objects, one for each computer.</span></span> <span data-ttu-id="35f5e-242">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-242">The default is the local computer.</span></span>

<span data-ttu-id="35f5e-243">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="35f5e-243">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="35f5e-244">Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.).</span><span class="sxs-lookup"><span data-stu-id="35f5e-244">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="35f5e-245">När datorn finns i en annan domän än användaren, krävs det fullständigt kvalificerade domän namnet.</span><span class="sxs-lookup"><span data-stu-id="35f5e-245">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="35f5e-246">Du kan också skicka ett dator namn inom citat tecken till `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="35f5e-246">You can also pipe a computer name, in quotation marks, to `New-PSSession`.</span></span>

<span data-ttu-id="35f5e-247">Om du vill använda en IP-adress i värdet för parametern **computername** måste kommandot innehålla parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="35f5e-247">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="35f5e-248">Dessutom måste datorn konfigureras för HTTPS-transport eller fjärrdatorns IP-adress måste ingå i listan WinRM TrustedHosts på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-248">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="35f5e-249">Instruktioner för att lägga till ett dator namn i listan TrustedHosts finns i avsnittet om hur du lägger till en dator i listan över betrodda värdar i [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="35f5e-249">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="35f5e-250">Om du vill inkludera den lokala datorn i värdet för parametern **computername** startar du Windows PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="35f5e-250">To include the local computer in the value of the **ComputerName** parameter, start Windows PowerShell by using the Run as administrator option.</span></span>

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

### <span data-ttu-id="35f5e-251">– ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="35f5e-251">-ConfigurationName</span></span>

<span data-ttu-id="35f5e-252">Anger den sessionsinformation som används för den nya **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="35f5e-252">Specifies the session configuration that is used for the new **PSSession**.</span></span>

<span data-ttu-id="35f5e-253">Ange ett konfigurations namn eller den fullständigt kvalificerade resurs-URI: n för en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-253">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="35f5e-254">Om du bara anger konfigurations namnet är följande schema-URI anpassningsprefix: `http://schemas.microsoft.com/PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="35f5e-254">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="35f5e-255">Sessionens konfiguration för en session finns på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-255">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="35f5e-256">Om den angivna konfigurationen av sessionen inte finns på fjärrdatorn Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="35f5e-256">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="35f5e-257">Standardvärdet är värdet för Preference- `$PSSessionConfigurationName` variabeln på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-257">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="35f5e-258">Om den här preferens variabeln inte anges är standardvärdet Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35f5e-258">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="35f5e-259">Mer information finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="35f5e-259">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

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

### <span data-ttu-id="35f5e-260">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="35f5e-260">-ConnectionUri</span></span>

<span data-ttu-id="35f5e-261">Anger en URI som definierar anslutnings slut punkten för sessionen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-261">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="35f5e-262">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="35f5e-262">The URI must be fully qualified.</span></span> <span data-ttu-id="35f5e-263">Formatet för den här strängen är följande:</span><span class="sxs-lookup"><span data-stu-id="35f5e-263">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="35f5e-264">Standardvärdet är följande:</span><span class="sxs-lookup"><span data-stu-id="35f5e-264">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="35f5e-265">Om du inte anger en **ConnectionURI** kan du använda parametrarna **UseSSL** , **computername** , **port** och **ApplicationName** för att ange **ConnectionURI** -värden.</span><span class="sxs-lookup"><span data-stu-id="35f5e-265">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="35f5e-266">Giltiga värden för URI: n i transport segmentet är HTTP och HTTPS.</span><span class="sxs-lookup"><span data-stu-id="35f5e-266">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="35f5e-267">Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med standard portar: 80 för HTTP och 443 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="35f5e-267">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="35f5e-268">Om du vill använda standard portarna för PowerShell-fjärrkommunikation anger du Port 5985 för HTTP eller 5986 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="35f5e-268">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="35f5e-269">Om mål datorn omdirigerar anslutningen till en annan URI, förhindrar PowerShell omdirigeringen om du inte använder parametern **AllowRedirection** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="35f5e-269">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

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

### <span data-ttu-id="35f5e-270">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="35f5e-270">-ContainerId</span></span>

<span data-ttu-id="35f5e-271">Anger en matris med ID: n för behållare.</span><span class="sxs-lookup"><span data-stu-id="35f5e-271">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="35f5e-272">Den här cmdleten startar en interaktiv session med var och en av de angivna behållarna.</span><span class="sxs-lookup"><span data-stu-id="35f5e-272">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="35f5e-273">Använd `docker ps` kommandot för att hämta en lista över behållar-ID: n.</span><span class="sxs-lookup"><span data-stu-id="35f5e-273">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="35f5e-274">Mer information finns i hjälpen för kommandot [Docker PS](https://docs.docker.com/engine/reference/commandline/ps/) .</span><span class="sxs-lookup"><span data-stu-id="35f5e-274">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

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

### <span data-ttu-id="35f5e-275">-Credential</span><span class="sxs-lookup"><span data-stu-id="35f5e-275">-Credential</span></span>

<span data-ttu-id="35f5e-276">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="35f5e-276">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="35f5e-277">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="35f5e-277">The default is the current user.</span></span>

<span data-ttu-id="35f5e-278">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="35f5e-278">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="35f5e-279">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="35f5e-279">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="35f5e-280">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="35f5e-280">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="35f5e-281">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="35f5e-281">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="35f5e-282">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="35f5e-282">-EnableNetworkAccess</span></span>

<span data-ttu-id="35f5e-283">Anger att denna cmdlet lägger till en interaktiv säkerhetstoken till loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="35f5e-283">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="35f5e-284">Med den interaktiva token kan du köra kommandon i loopback-sessionen som hämtar data från andra datorer.</span><span class="sxs-lookup"><span data-stu-id="35f5e-284">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="35f5e-285">Du kan till exempel köra ett kommando i sessionen som kopierar XML-filer från en fjärrdator till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-285">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="35f5e-286">En loopback-session är en **PSSession** som kommer från och slutar på samma dator.</span><span class="sxs-lookup"><span data-stu-id="35f5e-286">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="35f5e-287">Om du vill skapa en loopback-session utelämnar du parametern **computername** eller anger värdet för punkt (.), localhost eller namnet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-287">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (.), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="35f5e-288">Som standard skapar denna cmdlet loopback-sessioner med hjälp av en nätverks-token som kanske inte ger tillräcklig behörighet att autentisera till fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="35f5e-288">By default, this cmdlet creates loopback sessions by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="35f5e-289">Parametern **EnableNetworkAccess** är endast effektiv i loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="35f5e-289">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="35f5e-290">Om du använder **EnableNetworkAccess** när du skapar en-session på en fjärrdator, lyckas kommandot, men parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="35f5e-290">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="35f5e-291">Du kan också aktivera fjärråtkomst i en loopback-session med hjälp av CredSSP-värdet för parametern **Authentication** , som delegerar autentiseringsuppgifterna för sessionen till andra datorer.</span><span class="sxs-lookup"><span data-stu-id="35f5e-291">You can also enable remote access in a loopback session by using the CredSSP value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="35f5e-292">För att skydda datorn från skadlig åtkomst kan frånkopplade loopback-sessioner med interaktiva token, som är de som skapats med hjälp av parametern **EnableNetworkAccess** , bara återanslutas från den dator där sessionen skapades.</span><span class="sxs-lookup"><span data-stu-id="35f5e-292">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="35f5e-293">Frånkopplade sessioner som använder CredSSP-autentisering kan återanslutas från andra datorer.</span><span class="sxs-lookup"><span data-stu-id="35f5e-293">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="35f5e-294">Mer information finns i `Disconnect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="35f5e-294">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="35f5e-295">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="35f5e-295">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="35f5e-296">-HostName</span><span class="sxs-lookup"><span data-stu-id="35f5e-296">-HostName</span></span>

<span data-ttu-id="35f5e-297">Anger en matris med dator namn för en SSH-baserad (Secure Shell) anslutning.</span><span class="sxs-lookup"><span data-stu-id="35f5e-297">Specifies an array of computer names for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="35f5e-298">Detta liknar parametern ComputerName, förutom att anslutningen till fjärrdatorn görs med SSH i stället för Windows WinRM.</span><span class="sxs-lookup"><span data-stu-id="35f5e-298">This is similar to the ComputerName parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span>

<span data-ttu-id="35f5e-299">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="35f5e-299">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35f5e-300">-Fil Sök väg</span><span class="sxs-lookup"><span data-stu-id="35f5e-300">-KeyFilePath</span></span>

<span data-ttu-id="35f5e-301">Anger en nyckel fil Sök väg som används av SSH (Secure Shell) för att autentisera en användare på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="35f5e-301">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="35f5e-302">SSH tillåter att användarautentisering utförs via privata/offentliga nycklar som ett alternativ till grundläggande lösenordsautentisering.</span><span class="sxs-lookup"><span data-stu-id="35f5e-302">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="35f5e-303">Om fjärrdatorn har kon figurer ATS för nyckel autentisering kan du använda den här parametern för att ange den nyckel som identifierar användaren.</span><span class="sxs-lookup"><span data-stu-id="35f5e-303">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="35f5e-304">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="35f5e-304">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35f5e-305">-Name</span><span class="sxs-lookup"><span data-stu-id="35f5e-305">-Name</span></span>

<span data-ttu-id="35f5e-306">Anger ett eget namn för **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="35f5e-306">Specifies a friendly name for the **PSSession**.</span></span>

<span data-ttu-id="35f5e-307">Du kan använda namnet för att referera till **PSSession** när du använder andra cmdlets, till exempel `Get-PSSession` och `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="35f5e-307">You can use the name to refer to the **PSSession** when you use other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="35f5e-308">Namnet måste inte vara unikt för datorn eller den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-308">The name is not required to be unique to the computer or the current session.</span></span>

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

### <span data-ttu-id="35f5e-309">-Port</span><span class="sxs-lookup"><span data-stu-id="35f5e-309">-Port</span></span>

<span data-ttu-id="35f5e-310">Anger nätverks porten på den fjärrdator som används för den här anslutningen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-310">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="35f5e-311">Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder.</span><span class="sxs-lookup"><span data-stu-id="35f5e-311">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="35f5e-312">Standard portarna är 5985, som är WinRM-porten för HTTP och 5986, som är WinRM-porten för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="35f5e-312">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="35f5e-313">Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.</span><span class="sxs-lookup"><span data-stu-id="35f5e-313">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="35f5e-314">Använd följande kommandon för att konfigurera lyssnaren:</span><span class="sxs-lookup"><span data-stu-id="35f5e-314">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="35f5e-315">Använd inte **port** parametern om du inte behöver.</span><span class="sxs-lookup"><span data-stu-id="35f5e-315">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="35f5e-316">Port inställningen i kommandot gäller för alla datorer eller sessioner där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="35f5e-316">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="35f5e-317">En alternativ port inställning kan hindra kommandot från att köras på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="35f5e-317">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35f5e-318">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="35f5e-318">-RunAsAdministrator</span></span>

<span data-ttu-id="35f5e-319">Anger att **PSSession** körs som administratör.</span><span class="sxs-lookup"><span data-stu-id="35f5e-319">Indicates that the **PSSession** runs as administrator.</span></span>

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

### <span data-ttu-id="35f5e-320">– Session</span><span class="sxs-lookup"><span data-stu-id="35f5e-320">-Session</span></span>

<span data-ttu-id="35f5e-321">Anger en matris med **PSSession** -objekt som denna cmdlet använder som en modell för den nya **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="35f5e-321">Specifies an array of **PSSession** objects that this cmdlet uses as a model for the new **PSSession**.</span></span> <span data-ttu-id="35f5e-322">Den här parametern skapar nya **PSSession** -objekt som har samma egenskaper som de angivna **PSSession** -objekten.</span><span class="sxs-lookup"><span data-stu-id="35f5e-322">This parameter creates new **PSSession** objects that have the same properties as the specified **PSSession** objects.</span></span>

<span data-ttu-id="35f5e-323">Ange en variabel som innehåller **PSSession** -objekt eller ett kommando som skapar eller hämtar **PSSession** -objekt, till exempel ett- `New-PSSession` eller- `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="35f5e-323">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="35f5e-324">De resulterande **PSSession** -objekten har samma dator namn, program namn, ANSLUTNINGS-URI, port, konfigurations namn, begränsnings gräns och Secure SOCKETS Layer (SSL)-värde som original, men de har olika visnings namn, ID och instans-ID (GUID).</span><span class="sxs-lookup"><span data-stu-id="35f5e-324">The resulting **PSSession** objects have the same computer name, application name, connection URI, port, configuration name, throttle limit, and Secure Sockets Layer (SSL) value as the originals, but they have a different display name, ID, and instance ID (GUID).</span></span>

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

### <span data-ttu-id="35f5e-325">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="35f5e-325">-SessionOption</span></span>

<span data-ttu-id="35f5e-326">Anger avancerade alternativ för sessionen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-326">Specifies advanced options for the session.</span></span> <span data-ttu-id="35f5e-327">Ange ett **SessionOption** -objekt, t. ex. ett som du skapar med hjälp av `New-PSSessionOption` cmdleten, eller en hash-tabell där nycklarna är namn på sessionstillstånd och värdena är alternativ värden för session.</span><span class="sxs-lookup"><span data-stu-id="35f5e-327">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="35f5e-328">Standardvärdena för alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts.</span><span class="sxs-lookup"><span data-stu-id="35f5e-328">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="35f5e-329">Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-329">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="35f5e-330">Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i `$PSSessionOption` variabeln Preference och i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-330">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="35f5e-331">De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-331">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="35f5e-332">En beskrivning av de sessionsinformation som innehåller standardvärdena finns i `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="35f5e-332">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="35f5e-333">Information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="35f5e-333">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="35f5e-334">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="35f5e-334">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

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

### <span data-ttu-id="35f5e-335">-SSHConnection</span><span class="sxs-lookup"><span data-stu-id="35f5e-335">-SSHConnection</span></span>

<span data-ttu-id="35f5e-336">Den här parametern tar en matris med hash där varje hash innehåller en eller flera anslutnings parametrar som behövs för att upprätta en SSH-anslutning (Secure Shell) (värdnamn, port, användar namn, sökväg).</span><span class="sxs-lookup"><span data-stu-id="35f5e-336">This parameter takes an array of hashtables where each hashtable contains one or more connection parameters needed to establish a Secure Shell (SSH) connection (HostName, Port, UserName, KeyFilePath).</span></span>

<span data-ttu-id="35f5e-337">Anslutnings parametrarna för hash-tabellen är desamma som definieras för parametern **hostname** .</span><span class="sxs-lookup"><span data-stu-id="35f5e-337">The hashtable connection parameters are the same as defined for the **HostName** parameter set.</span></span>

<span data-ttu-id="35f5e-338">Parametern **SSHConnection** är användbar för att skapa flera sessioner där varje session kräver annan anslutnings information.</span><span class="sxs-lookup"><span data-stu-id="35f5e-338">The **SSHConnection** parameter is useful for creating multiple sessions where each session requires different connection information.</span></span>

<span data-ttu-id="35f5e-339">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="35f5e-339">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35f5e-340">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="35f5e-340">-SSHTransport</span></span>

<span data-ttu-id="35f5e-341">Anger att fjärr anslutningen upprättas med hjälp av SSH (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="35f5e-341">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="35f5e-342">Som standard använder PowerShell Windows WinRM för att ansluta till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="35f5e-342">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="35f5e-343">Den här växeln tvingar PowerShell att använda HostName-parametern som angetts för att upprätta en SSH-baserad fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="35f5e-343">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="35f5e-344">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="35f5e-344">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35f5e-345">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="35f5e-345">-ThrottleLimit</span></span>

<span data-ttu-id="35f5e-346">Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="35f5e-346">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="35f5e-347">Om du utelämnar den här parametern eller anger värdet 0 (noll) används standardvärdet 32.</span><span class="sxs-lookup"><span data-stu-id="35f5e-347">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span>

<span data-ttu-id="35f5e-348">Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-348">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, Uri, VMId, VMName, Session, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35f5e-349">-UserName</span><span class="sxs-lookup"><span data-stu-id="35f5e-349">-UserName</span></span>

<span data-ttu-id="35f5e-350">Anger användar namnet för det konto som används för att skapa en session på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-350">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="35f5e-351">Metoden för användarautentisering beror på hur Secure Shell (SSH) är konfigurerat på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-351">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="35f5e-352">Om SSH har kon figurer ATS för grundläggande lösenordsautentisering uppmanas du att ange användar lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="35f5e-352">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="35f5e-353">Om SSH har kon figurer ATS för nyckelbaserad användarautentisering kan en nyckel fil Sök väg tillhandahållas via parametern för nyckel Sök väg och inget lösen ord visas.</span><span class="sxs-lookup"><span data-stu-id="35f5e-353">If SSH is configured for key based user authentication then a key file path can be provided via the KeyFilePath parameter and no password prompt will occur.</span></span> <span data-ttu-id="35f5e-354">Observera att om klientens användar nyckel finns på en känd SSH-plats behövs inte parametern för nyckel Sök vägar för nyckelbaserad autentisering, och användarautentisering sker automatiskt baserat på användar namnet.</span><span class="sxs-lookup"><span data-stu-id="35f5e-354">Note that if the client user key file is located in an SSH known location then the KeyFilePath parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="35f5e-355">Mer information finns i SSH-dokumentationen om nyckelbaserad användarautentisering.</span><span class="sxs-lookup"><span data-stu-id="35f5e-355">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="35f5e-356">Detta är inte en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="35f5e-356">This is not a required parameter.</span></span> <span data-ttu-id="35f5e-357">Om ingen användar namns parameter anges används den aktuella inloggnings användar namnet för anslutningen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-357">If no UserName parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="35f5e-358">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="35f5e-358">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35f5e-359">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="35f5e-359">-UseSSL</span></span>

<span data-ttu-id="35f5e-360">Anger att denna cmdlet använder SSL-protokollet för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-360">Indicates that this cmdlet uses the SSL protocol to establish a connection to the remote computer.</span></span>
<span data-ttu-id="35f5e-361">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="35f5e-361">By default, SSL is not used.</span></span>

<span data-ttu-id="35f5e-362">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="35f5e-362">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="35f5e-363">Parametern **UseSSL** erbjuder ytterligare ett skydd som skickar data via en HTTPS-anslutning i stället för en HTTP-anslutning.</span><span class="sxs-lookup"><span data-stu-id="35f5e-363">The **UseSSL** parameter offers an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="35f5e-364">Om du använder den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="35f5e-364">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="35f5e-365">-VMId</span><span class="sxs-lookup"><span data-stu-id="35f5e-365">-VMId</span></span>

<span data-ttu-id="35f5e-366">Anger en matris med ID för virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="35f5e-366">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="35f5e-367">Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna.</span><span class="sxs-lookup"><span data-stu-id="35f5e-367">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="35f5e-368">Använd följande kommando för att se de virtuella datorer som är tillgängliga för dig:</span><span class="sxs-lookup"><span data-stu-id="35f5e-368">To see the virtual machines that are available to you, use the following command:</span></span>

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

### <span data-ttu-id="35f5e-369">– VMName</span><span class="sxs-lookup"><span data-stu-id="35f5e-369">-VMName</span></span>

<span data-ttu-id="35f5e-370">Anger en matris med namn på virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="35f5e-370">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="35f5e-371">Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna.</span><span class="sxs-lookup"><span data-stu-id="35f5e-371">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="35f5e-372">Använd cmdleten för att se de virtuella datorer som är tillgängliga för dig `Get-VM` .</span><span class="sxs-lookup"><span data-stu-id="35f5e-372">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

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

### <span data-ttu-id="35f5e-373">-HostName</span><span class="sxs-lookup"><span data-stu-id="35f5e-373">-HostName</span></span>

<span data-ttu-id="35f5e-374">Anger en matris med dator namn för en SSH-baserad (Secure Shell) anslutning.</span><span class="sxs-lookup"><span data-stu-id="35f5e-374">Specifies an array of computer names for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="35f5e-375">Detta liknar parametern ComputerName, förutom att anslutningen till fjärrdatorn görs med SSH i stället för Windows WinRM.</span><span class="sxs-lookup"><span data-stu-id="35f5e-375">This is similar to the ComputerName parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span>
<span data-ttu-id="35f5e-376">Den här parametern har stöd för att ange användar namnet och/eller porten som en del av värdet för värd namn parametern med hjälp av formuläret `user@hostname:port` .</span><span class="sxs-lookup"><span data-stu-id="35f5e-376">This parameter supports specifying the user name and/or port as part of the host name parameter value using the form `user@hostname:port`.</span></span>
<span data-ttu-id="35f5e-377">Användar namnet och/eller porten som anges som en del av värd namnet har företräde framför `-UserName` `-Port` parametrarna och, om de anges.</span><span class="sxs-lookup"><span data-stu-id="35f5e-377">The user name and/or port specified as part of the host name takes precedence over the `-UserName` and `-Port` parameters, if specified.</span></span>
<span data-ttu-id="35f5e-378">På så sätt kan du skicka flera dator namn till den här parametern där vissa har vissa användar namn och/eller portar, medan andra använder användar namnet och/eller porten från `-UserName` `-Port` parametrarna och.</span><span class="sxs-lookup"><span data-stu-id="35f5e-378">This allows passing multiple computer names to this parameter where some have specific user names and/or ports, while others use the user name and/or port from the `-UserName` and `-Port` parameters.</span></span>

<span data-ttu-id="35f5e-379">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="35f5e-379">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: HostName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35f5e-380">-Fil Sök väg</span><span class="sxs-lookup"><span data-stu-id="35f5e-380">-KeyFilePath</span></span>

<span data-ttu-id="35f5e-381">Anger en nyckel fil Sök väg som används av SSH (Secure Shell) för att autentisera en användare på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="35f5e-381">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="35f5e-382">SSH tillåter att användarautentisering utförs via privata/offentliga nycklar som ett alternativ till grundläggande lösenordsautentisering.</span><span class="sxs-lookup"><span data-stu-id="35f5e-382">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="35f5e-383">Om fjärrdatorn har kon figurer ATS för nyckel autentisering kan du använda den här parametern för att ange den nyckel som identifierar användaren.</span><span class="sxs-lookup"><span data-stu-id="35f5e-383">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="35f5e-384">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="35f5e-384">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: HostName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35f5e-385">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="35f5e-385">-SSHTransport</span></span>

<span data-ttu-id="35f5e-386">Anger att fjärr anslutningen upprättas med hjälp av SSH (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="35f5e-386">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="35f5e-387">Som standard använder PowerShell Windows WinRM för att ansluta till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="35f5e-387">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="35f5e-388">Den här växeln tvingar PowerShell att använda HostName-parametern som angetts för att upprätta en SSH-baserad fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="35f5e-388">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="35f5e-389">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="35f5e-389">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: HostName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35f5e-390">-UserName</span><span class="sxs-lookup"><span data-stu-id="35f5e-390">-UserName</span></span>

<span data-ttu-id="35f5e-391">Anger användar namnet för det konto som används för att skapa en session på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-391">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="35f5e-392">Metoden för användarautentisering beror på hur Secure Shell (SSH) är konfigurerat på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="35f5e-392">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="35f5e-393">Om SSH har kon figurer ATS för grundläggande lösenordsautentisering uppmanas du att ange användar lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="35f5e-393">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="35f5e-394">Om SSH har kon figurer ATS för nyckelbaserad användarautentisering kan en nyckel fil Sök väg tillhandahållas via parametern för nyckel Sök väg och inget lösen ord visas.</span><span class="sxs-lookup"><span data-stu-id="35f5e-394">If SSH is configured for key based user authentication then a key file path can be provided via the KeyFilePath parameter and no password prompt will occur.</span></span> <span data-ttu-id="35f5e-395">Observera att om klientens användar nyckel finns på en känd SSH-plats behövs inte parametern för nyckel Sök vägar för nyckelbaserad autentisering, och användarautentisering sker automatiskt baserat på användar namnet.</span><span class="sxs-lookup"><span data-stu-id="35f5e-395">Note that if the client user key file is located in an SSH known location then the KeyFilePath parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="35f5e-396">Mer information finns i SSH-dokumentationen om nyckelbaserad användarautentisering.</span><span class="sxs-lookup"><span data-stu-id="35f5e-396">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="35f5e-397">Detta är inte en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="35f5e-397">This is not a required parameter.</span></span> <span data-ttu-id="35f5e-398">Om ingen användar namns parameter anges används den aktuella inloggnings användar namnet för anslutningen.</span><span class="sxs-lookup"><span data-stu-id="35f5e-398">If no UserName parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="35f5e-399">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="35f5e-399">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: HostName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35f5e-400">-SSHConnection</span><span class="sxs-lookup"><span data-stu-id="35f5e-400">-SSHConnection</span></span>

<span data-ttu-id="35f5e-401">Den här parametern tar en matris med hash där varje hash innehåller en eller flera anslutnings parametrar som behövs för att upprätta en SSH-anslutning (Secure Shell) (värdnamn, port, användar namn, fil Sök väg, under system).</span><span class="sxs-lookup"><span data-stu-id="35f5e-401">This parameter takes an array of hashtables where each hashtable contains one or more connection parameters needed to establish a Secure Shell (SSH) connection (HostName, Port, UserName, KeyFilePath, Subsystem).</span></span>

<span data-ttu-id="35f5e-402">Anslutnings parametrarna för hash-tabellen är desamma som definieras för parametern **hostname** .</span><span class="sxs-lookup"><span data-stu-id="35f5e-402">The hashtable connection parameters are the same as defined for the **HostName** parameter set.</span></span>
<span data-ttu-id="35f5e-403">Observera att ordningen på nycklarna i hash-tabellen resulterar i att användar namnet och porten används för anslutningen där den sista som angetts används.</span><span class="sxs-lookup"><span data-stu-id="35f5e-403">Note that the order of the keys in the hashtable result in user name and port being used for the connection where the last one specified is used.</span></span>  <span data-ttu-id="35f5e-404">Om du till exempel använder `@{UserName="first";HostName="second@host"}` används användar namnet `second` .</span><span class="sxs-lookup"><span data-stu-id="35f5e-404">For example, if you use `@{UserName="first";HostName="second@host"}`, then the user name `second` will be used.</span></span>  <span data-ttu-id="35f5e-405">Men om du använder `@{HostName="second@host:22";Port=23}` , kommer port 23 att användas.</span><span class="sxs-lookup"><span data-stu-id="35f5e-405">However, if you use `@{HostName="second@host:22";Port=23}`, then port 23 will be used.</span></span>

<span data-ttu-id="35f5e-406">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="35f5e-406">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="35f5e-407">Parametern **SSHConnection** är användbar för att skapa flera sessioner där varje session kräver annan anslutnings information.</span><span class="sxs-lookup"><span data-stu-id="35f5e-407">The **SSHConnection** parameter is useful for creating multiple sessions where each session requires different connection information.</span></span>

```yaml
Type: hashtable
Parameter Sets: SSHConnection
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35f5e-408">-Under system</span><span class="sxs-lookup"><span data-stu-id="35f5e-408">-Subsystem</span></span>

<span data-ttu-id="35f5e-409">Anger det SSH-undersystem som används för den nya **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="35f5e-409">Specifies the SSH subsystem used for the new **PSSession**.</span></span>

<span data-ttu-id="35f5e-410">Detta anger under systemet som ska användas på målet som det definieras i sshd_config.</span><span class="sxs-lookup"><span data-stu-id="35f5e-410">This specifies the subsystem to use on the target as defined in sshd_config.</span></span>
<span data-ttu-id="35f5e-411">Under systemet startar en angiven version av PowerShell med fördefinierade parametrar.</span><span class="sxs-lookup"><span data-stu-id="35f5e-411">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span>
<span data-ttu-id="35f5e-412">Om det angivna under systemet inte finns på fjärrdatorn Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="35f5e-412">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="35f5e-413">Om den här parametern inte används är standard under systemet "PowerShell".</span><span class="sxs-lookup"><span data-stu-id="35f5e-413">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

```yaml
Type: System.String
Parameter Sets: HostName
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="35f5e-414">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="35f5e-414">CommonParameters</span></span>

<span data-ttu-id="35f5e-415">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="35f5e-415">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="35f5e-416">Mer information finns i about_CommonParameters ( https://go.microsoft.com/fwlink/?LinkID=113216) .</span><span class="sxs-lookup"><span data-stu-id="35f5e-416">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="35f5e-417">INDATA</span><span class="sxs-lookup"><span data-stu-id="35f5e-417">INPUTS</span></span>

### <span data-ttu-id="35f5e-418">System. String, system. URI, system. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="35f5e-418">System.String, System.URI, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="35f5e-419">Du kan skicka en sträng, en URI eller ett sessionsobjekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="35f5e-419">You can pipe a string, URI, or session object to this cmdlet.</span></span>

## <span data-ttu-id="35f5e-420">UTDATA</span><span class="sxs-lookup"><span data-stu-id="35f5e-420">OUTPUTS</span></span>

### <span data-ttu-id="35f5e-421">System. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="35f5e-421">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="35f5e-422">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="35f5e-422">NOTES</span></span>

- <span data-ttu-id="35f5e-423">Denna cmdlet använder PowerShell-infrastrukturen för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="35f5e-423">This cmdlet uses the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="35f5e-424">Om du vill använda den här cmdleten måste den lokala datorn och alla fjärrdatorer konfigureras för PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="35f5e-424">To use this cmdlet, the local computer and any remote computers must be configured for PowerShell remoting.</span></span> <span data-ttu-id="35f5e-425">Mer information finns i [about_Remote_Requirements](About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35f5e-425">For more information, see [about_Remote_Requirements](About/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="35f5e-426">Om du vill skapa en **PSSession** på den lokala datorn startar du PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="35f5e-426">To create a **PSSession** on the local computer, start PowerShell with the Run as administrator option.</span></span>
- <span data-ttu-id="35f5e-427">När du är färdig med **PSSession** kan du använda `Remove-PSSession` cmdleten för att ta bort **PSSession** och släppa dess resurser.</span><span class="sxs-lookup"><span data-stu-id="35f5e-427">When you are finished with the **PSSession** , use the `Remove-PSSession` cmdlet to delete the **PSSession** and release its resources.</span></span>
- <span data-ttu-id="35f5e-428">Parameter uppsättningarna **hostname** och **SSHConnection** inkluderades från och med PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="35f5e-428">The **HostName** and **SSHConnection** parameter sets were included starting with PowerShell 6.0.</span></span>
  <span data-ttu-id="35f5e-429">De lades till för att tillhandahålla PowerShell-fjärrkommunikation utifrån SSH (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="35f5e-429">They were added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="35f5e-430">Både SSH och PowerShell stöds på flera plattformar (Windows, Linux, macOS) och PowerShell-fjärrkommunikationen fungerar över dessa plattformar där PowerShell och SSH har installerats och kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="35f5e-430">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="35f5e-431">Detta skiljer sig från den tidigare Windows-fjärrkommunikation som baseras på WinRM och mycket av de särskilda WinRM-funktionerna och begränsningarna gäller inte.</span><span class="sxs-lookup"><span data-stu-id="35f5e-431">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="35f5e-432">Till exempel kan WinRM-baserade kvoter, sessions alternativ, anpassad slut punkts konfiguration och funktionerna för att koppla från/återansluta inte användas för närvarande.</span><span class="sxs-lookup"><span data-stu-id="35f5e-432">For example WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="35f5e-433">Mer information om hur du konfigurerar PowerShell SSH-fjärrkommunikation finns i [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="35f5e-433">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <span data-ttu-id="35f5e-434">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="35f5e-434">RELATED LINKS</span></span>

[<span data-ttu-id="35f5e-435">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="35f5e-435">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="35f5e-436">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="35f5e-436">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="35f5e-437">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="35f5e-437">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="35f5e-438">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="35f5e-438">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="35f5e-439">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="35f5e-439">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="35f5e-440">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="35f5e-440">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="35f5e-441">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="35f5e-441">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="35f5e-442">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="35f5e-442">Remove-PSSession</span></span>](Remove-PSSession.md)
