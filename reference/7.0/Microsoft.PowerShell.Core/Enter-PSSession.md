---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: f5b8d82b2f2a30c176ab01be42201434842a0454
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/24/2020
ms.locfileid: "93268748"
---
# <span data-ttu-id="eb161-103">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="eb161-103">Enter-PSSession</span></span>

## <span data-ttu-id="eb161-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="eb161-104">SYNOPSIS</span></span>
<span data-ttu-id="eb161-105">Startar en interaktiv session med en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="eb161-105">Starts an interactive session with a remote computer.</span></span>

## <span data-ttu-id="eb161-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eb161-106">SYNTAX</span></span>

### <span data-ttu-id="eb161-107">ComputerName (standard)</span><span class="sxs-lookup"><span data-stu-id="eb161-107">ComputerName (Default)</span></span>

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="eb161-108">SSHHost</span><span class="sxs-lookup"><span data-stu-id="eb161-108">SSHHost</span></span>

```
Enter-PSSession [-HostName] <String> [-Port <Int32>] [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [<CommonParameters>]
```

### <span data-ttu-id="eb161-109">Session</span><span class="sxs-lookup"><span data-stu-id="eb161-109">Session</span></span>

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="eb161-110">URI</span><span class="sxs-lookup"><span data-stu-id="eb161-110">Uri</span></span>

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="eb161-111">InstanceId</span><span class="sxs-lookup"><span data-stu-id="eb161-111">InstanceId</span></span>

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### <span data-ttu-id="eb161-112">Id</span><span class="sxs-lookup"><span data-stu-id="eb161-112">Id</span></span>

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="eb161-113">Name</span><span class="sxs-lookup"><span data-stu-id="eb161-113">Name</span></span>

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### <span data-ttu-id="eb161-114">VMId</span><span class="sxs-lookup"><span data-stu-id="eb161-114">VMId</span></span>

```
Enter-PSSession [-VMId] <Guid> [-Credential] <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### <span data-ttu-id="eb161-115">VMName</span><span class="sxs-lookup"><span data-stu-id="eb161-115">VMName</span></span>

```
Enter-PSSession [-VMName] <String> [-Credential] <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="eb161-116">Hålla</span><span class="sxs-lookup"><span data-stu-id="eb161-116">ContainerId</span></span>

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## <span data-ttu-id="eb161-117">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="eb161-117">DESCRIPTION</span></span>

<span data-ttu-id="eb161-118">`Enter-PSSession`Cmdleten startar en interaktiv session med en enda fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="eb161-118">The `Enter-PSSession` cmdlet starts an interactive session with a single remote computer.</span></span>
<span data-ttu-id="eb161-119">Under sessionen, de kommandon som du skriver körs på fjärrdatorn, precis som om du skrev direkt på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-119">During the session, the commands that you type run on the remote computer, just as if you were typing directly on the remote computer.</span></span> <span data-ttu-id="eb161-120">Du kan bara ha en interaktiv session åt gången.</span><span class="sxs-lookup"><span data-stu-id="eb161-120">You can have only one interactive session at a time.</span></span>

<span data-ttu-id="eb161-121">Normalt använder du parametern **computername** för att ange namnet på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-121">Typically, you use the **ComputerName** parameter to specify the name of the remote computer.</span></span>
<span data-ttu-id="eb161-122">Du kan dock även använda en session som du skapar med hjälp av `New-PSSession` cmdleten för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-122">However, you can also use a session that you create by using the `New-PSSession` cmdlet for the interactive session.</span></span> <span data-ttu-id="eb161-123">Du kan dock inte använda `Disconnect-PSSession` `Connect-PSSession` cmdletarna, eller `Receive-PSSession` för att koppla från eller återansluta till en interaktiv session.</span><span class="sxs-lookup"><span data-stu-id="eb161-123">However, you cannot use the `Disconnect-PSSession`, `Connect-PSSession`, or `Receive-PSSession` cmdlets to disconnect from or re-connect to an interactive session.</span></span>

<span data-ttu-id="eb161-124">Från och med PowerShell 6,0 kan du använda SSH (Secure Shell) för att upprätta en anslutning till en fjärrdator, om SSH är tillgängligt på den lokala datorn och fjärrdatorn har kon figurer ATS med en PowerShell SSH-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="eb161-124">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="eb161-125">Fördelen med en SSH-baserad PowerShell-fjärrsession är att den fungerar på flera plattformar (Windows, Linux, macOS).</span><span class="sxs-lookup"><span data-stu-id="eb161-125">The benefit an SSH based PowerShell remote session is that it works across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="eb161-126">För SSH-baserad fjärr kommunikation använder du parametern **hostname** för att ange fjärrdatorn och relevant anslutnings information.</span><span class="sxs-lookup"><span data-stu-id="eb161-126">For SSH based remoting you use the **HostName** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="eb161-127">Mer information om hur du konfigurerar PowerShell SSH-fjärrkommunikation finns i [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="eb161-127">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="eb161-128">Om du vill avsluta den interaktiva sessionen och koppla från fjärrdatorn använder du `Exit-PSSession` cmdleten eller typen `exit` .</span><span class="sxs-lookup"><span data-stu-id="eb161-128">To end the interactive session and disconnect from the remote computer, use the `Exit-PSSession` cmdlet, or type `exit`.</span></span>

## <span data-ttu-id="eb161-129">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="eb161-129">EXAMPLES</span></span>

### <span data-ttu-id="eb161-130">Exempel 1: starta en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="eb161-130">Example 1: Start an interactive session</span></span>

```
PS> Enter-PSSession
[localhost]: PS>
```

<span data-ttu-id="eb161-131">Det här kommandot startar en interaktiv session på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-131">This command starts an interactive session on the local computer.</span></span> <span data-ttu-id="eb161-132">Kommando tolken ändras för att visa att du nu kör kommandon i en annan session.</span><span class="sxs-lookup"><span data-stu-id="eb161-132">The command prompt changes to indicate that you are now running commands in a different session.</span></span>

<span data-ttu-id="eb161-133">De kommandon som du anger körs i den nya sessionen och resultatet returneras till Standardsessionen som text.</span><span class="sxs-lookup"><span data-stu-id="eb161-133">The commands that you enter run in the new session, and the results are returned to the default session as text.</span></span>

### <span data-ttu-id="eb161-134">Exempel 2: arbeta med en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="eb161-134">Example 2: Work with an interactive session</span></span>

<span data-ttu-id="eb161-135">Det första kommandot använder `Enter-PSSession` cmdleten för att starta en interaktiv session med Server01, en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="eb161-135">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with Server01, a remote computer.</span></span> <span data-ttu-id="eb161-136">När sessionen startar ändras kommando tolken så att den inkluderar dator namnet.</span><span class="sxs-lookup"><span data-stu-id="eb161-136">When the session starts, the command prompt changes to include the computer name.</span></span>

<span data-ttu-id="eb161-137">Det andra kommandot hämtar PowerShell-processen och dirigerar om utdata till Process.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="eb161-137">The second command gets the PowerShell process and redirects the output to the Process.txt file.</span></span> <span data-ttu-id="eb161-138">Kommandot skickas till fjärrdatorn och filen sparas på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-138">The command is submitted to the remote computer, and the file is saved on the remote computer.</span></span>

<span data-ttu-id="eb161-139">Det tredje kommandot använder nyckelordet **exit** för att avsluta den interaktiva sessionen och stänga anslutningen.</span><span class="sxs-lookup"><span data-stu-id="eb161-139">The third command uses the **Exit** keyword to end the interactive session and close the connection.</span></span>
<span data-ttu-id="eb161-140">Det fjärde kommandot bekräftar att Process.txt-filen finns på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-140">The fourth command confirms that the Process.txt file is on the remote computer.</span></span> <span data-ttu-id="eb161-141">Ett `Get-ChildItem` ("dir")-kommando på den lokala datorn kan inte hitta filen.</span><span class="sxs-lookup"><span data-stu-id="eb161-141">A `Get-ChildItem` ("dir") command on the local computer cannot find the file.</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

<span data-ttu-id="eb161-142">Det här kommandot visar hur du arbetar i en interaktiv session med en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="eb161-142">This command shows how to work in an interactive session with a remote computer.</span></span>

### <span data-ttu-id="eb161-143">Exempel 3: Använd parametern session</span><span class="sxs-lookup"><span data-stu-id="eb161-143">Example 3: Use the Session parameter</span></span>

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
[Server01]: PS>
```

<span data-ttu-id="eb161-144">Dessa kommandon använder parametern **session** för `Enter-PSSession` för att köra den interaktiva sessionen i en befintlig PowerShell-session ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="eb161-144">These commands use the **Session** parameter of `Enter-PSSession` to run the interactive session in an existing PowerShell session ( **PSSession** ).</span></span>

### <span data-ttu-id="eb161-145">Exempel 4: starta en interaktiv session och ange port-och Credential-parametrarna</span><span class="sxs-lookup"><span data-stu-id="eb161-145">Example 4: Start an interactive session and specify the Port and Credential parameters</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS>
```

<span data-ttu-id="eb161-146">Det här kommandot startar en interaktiv session med Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-146">This command starts an interactive session with the Server01 computer.</span></span> <span data-ttu-id="eb161-147">Den använder **port** parametern för att ange porten och parametern **Credential** för att ange kontot för en användare som har behörighet att ansluta till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-147">It uses the **Port** parameter to specify the port and the **Credential** parameter to specify the account of a user who has permission to connect to the remote computer.</span></span>

### <span data-ttu-id="eb161-148">Exempel 5: stoppa en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="eb161-148">Example 5: Stop an interactive session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
[Server01]: PS> Exit-PSSession
PS>
```

<span data-ttu-id="eb161-149">Det här exemplet visar hur du startar och stoppar en interaktiv session.</span><span class="sxs-lookup"><span data-stu-id="eb161-149">This example shows how to start and stop an interactive session.</span></span> <span data-ttu-id="eb161-150">Det första kommandot använder `Enter-PSSession` cmdleten för att starta en interaktiv session med Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-150">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

<span data-ttu-id="eb161-151">Det andra kommandot använder `Exit-PSSession` cmdleten för att avsluta sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-151">The second command uses the `Exit-PSSession` cmdlet to end the session.</span></span> <span data-ttu-id="eb161-152">Du kan också använda nyckelordet **exit** för att avsluta den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-152">You can also use the **Exit** keyword to end the interactive session.</span></span> <span data-ttu-id="eb161-153">`Exit-PSSession` och **Avsluta** har samma resultat.</span><span class="sxs-lookup"><span data-stu-id="eb161-153">`Exit-PSSession` and **Exit** have the same effect.</span></span>

### <span data-ttu-id="eb161-154">Exempel 6: starta en interaktiv session med SSH</span><span class="sxs-lookup"><span data-stu-id="eb161-154">Example 6: Start an interactive session using SSH</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="eb161-155">Det här exemplet visar hur du startar en interaktiv session med hjälp av SSH (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="eb161-155">This example shows how to start an interactive session using Secure Shell (SSH).</span></span> <span data-ttu-id="eb161-156">Om SSH har kon figurer ATS på fjärrdatorn för att uppmanas att ange lösen ord får du en prompt.</span><span class="sxs-lookup"><span data-stu-id="eb161-156">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span>
<span data-ttu-id="eb161-157">Annars kommer du att behöva använda SSH-nyckelbaserad användarautentisering.</span><span class="sxs-lookup"><span data-stu-id="eb161-157">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="eb161-158">Exempel 7: starta en interaktiv session med SSH och ange nyckel för port och användarautentisering</span><span class="sxs-lookup"><span data-stu-id="eb161-158">Example 7: Start an interactive session using SSH and specify the Port and user authentication key</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer02:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="eb161-159">Det här exemplet visar hur du startar en interaktiv session med SSH.</span><span class="sxs-lookup"><span data-stu-id="eb161-159">This example shows how to start an interactive session using SSH.</span></span> <span data-ttu-id="eb161-160">Den använder **port** parametern för att ange vilken port som ska användas och parametern för nyckel **Sök** vägar för att ange en RSA-nyckel som används för att autentisera användaren på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-160">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to authenticate the user on the remote computer.</span></span>

## <span data-ttu-id="eb161-161">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="eb161-161">PARAMETERS</span></span>

### <span data-ttu-id="eb161-162">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="eb161-162">-AllowRedirection</span></span>

<span data-ttu-id="eb161-163">Tillåter omdirigering av anslutningen till en alternativ Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="eb161-163">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="eb161-164">Omdirigering tillåts inte som standard.</span><span class="sxs-lookup"><span data-stu-id="eb161-164">By default, redirection is not allowed.</span></span>

<span data-ttu-id="eb161-165">När du använder **ConnectionURI** -parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI.</span><span class="sxs-lookup"><span data-stu-id="eb161-165">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="eb161-166">Som standard omdirigerar PowerShell inte anslutningar, men du kan använda den här parametern om du vill att den ska kunna omdirigera anslutningen.</span><span class="sxs-lookup"><span data-stu-id="eb161-166">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="eb161-167">Du kan också begränsa hur många gånger anslutningen omdirigeras genom att ändra värdet för alternativet **MaximumConnectionRedirectionCount** session.</span><span class="sxs-lookup"><span data-stu-id="eb161-167">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="eb161-168">Använd parametern **MaximumRedirection** för `New-PSSessionOption` cmdleten eller ange egenskapen **MaximumConnectionRedirectionCount** för `$PSSessionOption` Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="eb161-168">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="eb161-169">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="eb161-169">The default value is 5.</span></span>

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

### <span data-ttu-id="eb161-170">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="eb161-170">-ApplicationName</span></span>

<span data-ttu-id="eb161-171">Anger program namns segmentet för anslutnings-URI: n.</span><span class="sxs-lookup"><span data-stu-id="eb161-171">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="eb161-172">Använd den här parametern för att ange program namnet när du inte använder parametern **ConnectionURI** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="eb161-172">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="eb161-173">Standardvärdet är värdet för Preference- `$PSSessionApplicationName` variabeln på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-173">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="eb161-174">Om den här preferens variabeln inte definieras är standardvärdet WSMAN.</span><span class="sxs-lookup"><span data-stu-id="eb161-174">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="eb161-175">Det här värdet är lämpligt för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="eb161-175">This value is appropriate for most uses.</span></span> <span data-ttu-id="eb161-176">Mer information finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="eb161-176">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="eb161-177">**WinRM** -tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran.</span><span class="sxs-lookup"><span data-stu-id="eb161-177">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="eb161-178">Värdet för den här parametern ska matcha värdet på egenskapen **URLPrefix** för en lyssnare på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-178">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

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

### <span data-ttu-id="eb161-179">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="eb161-179">-Authentication</span></span>

<span data-ttu-id="eb161-180">Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="eb161-180">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="eb161-181">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="eb161-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="eb161-182">Default</span><span class="sxs-lookup"><span data-stu-id="eb161-182">Default</span></span>
- <span data-ttu-id="eb161-183">Basic</span><span class="sxs-lookup"><span data-stu-id="eb161-183">Basic</span></span>
- <span data-ttu-id="eb161-184">CredSSP</span><span class="sxs-lookup"><span data-stu-id="eb161-184">Credssp</span></span>
- <span data-ttu-id="eb161-185">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="eb161-185">Digest</span></span>
- <span data-ttu-id="eb161-186">Kerberos</span><span class="sxs-lookup"><span data-stu-id="eb161-186">Kerberos</span></span>
- <span data-ttu-id="eb161-187">Negotiate</span><span class="sxs-lookup"><span data-stu-id="eb161-187">Negotiate</span></span>
- <span data-ttu-id="eb161-188">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="eb161-188">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="eb161-189">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="eb161-189">The default value is Default.</span></span>

<span data-ttu-id="eb161-190">CredSSP-autentisering är endast tillgängligt i Windows Vista, Windows Server 2008 och senare versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="eb161-190">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="eb161-191">Mer information om värdena för den här parametern finns i [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="eb161-191">For more information about the values of this parameter, see [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="eb161-192">Varning! CredSSP-autentisering (Credential Security Support Provider), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="eb161-192">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="eb161-193">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="eb161-193">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="eb161-194">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-194">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

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

### <span data-ttu-id="eb161-195">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="eb161-195">-CertificateThumbprint</span></span>

<span data-ttu-id="eb161-196">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="eb161-196">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="eb161-197">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="eb161-197">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="eb161-198">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="eb161-198">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="eb161-199">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="eb161-199">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="eb161-200">Hämta ett certifikat med hjälp av `Get-Item` kommandot eller `Get-ChildItem` i PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="eb161-200">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="eb161-201">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="eb161-201">-ComputerName</span></span>

<span data-ttu-id="eb161-202">Anger ett dator namn.</span><span class="sxs-lookup"><span data-stu-id="eb161-202">Specifies a computer name.</span></span> <span data-ttu-id="eb161-203">Den här cmdleten startar en interaktiv session med den angivna fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-203">This cmdlet starts an interactive session with the specified remote computer.</span></span> <span data-ttu-id="eb161-204">Ange bara ett dator namn.</span><span class="sxs-lookup"><span data-stu-id="eb161-204">Enter only one computer name.</span></span> <span data-ttu-id="eb161-205">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-205">The default is the local computer.</span></span>

<span data-ttu-id="eb161-206">Ange NetBIOS-namnet, IP-adressen eller det fullständigt kvalificerade domän namnet för datorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-206">Type the NetBIOS name, the IP address, or the fully qualified domain name of the computer.</span></span> <span data-ttu-id="eb161-207">Du kan också skicka ett dator namn till `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="eb161-207">You can also pipe a computer name to `Enter-PSSession`.</span></span>

<span data-ttu-id="eb161-208">Om du vill använda en IP-adress i värdet för parametern **computername** måste kommandot innehålla parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="eb161-208">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="eb161-209">Dessutom måste datorn konfigureras för HTTPS-transport eller fjärrdatorns IP-adress måste ingå i listan WinRM TrustedHosts på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-209">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="eb161-210">Instruktioner för att lägga till ett dator namn i listan TrustedHosts finns i avsnittet om hur du lägger till en dator i listan över betrodda värdar i [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="eb161-210">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="eb161-211">Obs! i Windows Vista och senare versioner av operativ systemet Windows, för att inkludera den lokala datorn i värdet för parametern **computername** , måste du starta PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="eb161-211">Note: In Windows Vista and later versions of the Windows operating system, to include the local computer in the value of the **ComputerName** parameter, you must start PowerShell with the Run as administrator option.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="eb161-212">– ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="eb161-212">-ConfigurationName</span></span>

<span data-ttu-id="eb161-213">Anger den sessionsinformation som används för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-213">Specifies the session configuration that is used for the interactive session.</span></span>

<span data-ttu-id="eb161-214">Ange ett konfigurations namn eller den fullständigt kvalificerade resurs-URI: n för en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-214">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="eb161-215">Om du bara anger konfigurations namnet är följande schema-URI anpassningsprefix: `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="eb161-215">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="eb161-216">När det används med SSH anger detta det under system som ska användas på målet som det definieras i sshd_config.</span><span class="sxs-lookup"><span data-stu-id="eb161-216">When used with SSH, this specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="eb161-217">Standardvärdet för SSH är under `powershell` systemet.</span><span class="sxs-lookup"><span data-stu-id="eb161-217">The default value for SSH is the `powershell` subsystem.</span></span>

<span data-ttu-id="eb161-218">Sessionens konfiguration för en session finns på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-218">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="eb161-219">Om den angivna konfigurationen av sessionen inte finns på fjärrdatorn Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="eb161-219">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="eb161-220">Standardvärdet är värdet för Preference- `$PSSessionConfigurationName` variabeln på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-220">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="eb161-221">Om den här preferens variabeln inte anges är standardvärdet Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb161-221">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="eb161-222">Mer information finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="eb161-222">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

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

### <span data-ttu-id="eb161-223">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="eb161-223">-ConnectionUri</span></span>

<span data-ttu-id="eb161-224">Anger en URI som definierar anslutnings slut punkten för sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-224">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="eb161-225">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="eb161-225">The URI must be fully qualified.</span></span> <span data-ttu-id="eb161-226">Formatet för den här strängen är följande:</span><span class="sxs-lookup"><span data-stu-id="eb161-226">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="eb161-227">Standardvärdet är följande:</span><span class="sxs-lookup"><span data-stu-id="eb161-227">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="eb161-228">Om du inte anger en **ConnectionURI** kan du använda parametrarna **UseSSL** , **computername** , **port** och **ApplicationName** för att ange **ConnectionURI** -värden.</span><span class="sxs-lookup"><span data-stu-id="eb161-228">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="eb161-229">Giltiga värden för URI: n i transport segmentet är HTTP och HTTPS.</span><span class="sxs-lookup"><span data-stu-id="eb161-229">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="eb161-230">Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med hjälp av standard portar: 80 för HTTP och 443 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="eb161-230">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created by using standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="eb161-231">Om du vill använda standard portarna för PowerShell-fjärrkommunikation anger du Port 5985 för HTTP eller 5986 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="eb161-231">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="eb161-232">Om mål datorn omdirigerar anslutningen till en annan URI, förhindrar PowerShell omdirigeringen om du inte använder parametern **AllowRedirection** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="eb161-232">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri
Parameter Sets: Uri
Aliases: URI, CU

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="eb161-233">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="eb161-233">-ContainerId</span></span>

<span data-ttu-id="eb161-234">Anger ID för en behållare.</span><span class="sxs-lookup"><span data-stu-id="eb161-234">Specifies the ID of a container.</span></span>

```yaml
Type: System.String
Parameter Sets: ContainerId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="eb161-235">-Credential</span><span class="sxs-lookup"><span data-stu-id="eb161-235">-Credential</span></span>

<span data-ttu-id="eb161-236">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="eb161-236">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="eb161-237">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="eb161-237">The default is the current user.</span></span>

<span data-ttu-id="eb161-238">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eb161-238">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="eb161-239">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="eb161-239">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="eb161-240">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="eb161-240">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="eb161-241">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="eb161-241">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: 1
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="eb161-242">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="eb161-242">-EnableNetworkAccess</span></span>

<span data-ttu-id="eb161-243">Anger att denna cmdlet lägger till en interaktiv säkerhetstoken till loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="eb161-243">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="eb161-244">Med den interaktiva token kan du köra kommandon i loopback-sessionen som hämtar data från andra datorer.</span><span class="sxs-lookup"><span data-stu-id="eb161-244">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="eb161-245">Du kan till exempel köra ett kommando i sessionen som kopierar XML-filer från en fjärrdator till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-245">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="eb161-246">En loopback-session är en **PSSession** som kommer från och slutar på samma dator.</span><span class="sxs-lookup"><span data-stu-id="eb161-246">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="eb161-247">Om du vill skapa en loopback-session utelämnar du parametern **computername** eller anger värdet till.</span><span class="sxs-lookup"><span data-stu-id="eb161-247">To create a loopback session, omit the **ComputerName** parameter or set its value to .</span></span> <span data-ttu-id="eb161-248">(punkt), localhost eller namnet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-248">(dot), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="eb161-249">Som standard skapas loopback-sessioner med hjälp av en nätverks-token som kanske inte ger behörighet att autentisera till fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="eb161-249">By default, loopback sessions are created by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="eb161-250">Parametern **EnableNetworkAccess** är endast effektiv i loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="eb161-250">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="eb161-251">Om du använder **EnableNetworkAccess** när du skapar en-session på en fjärrdator, lyckas kommandot, men parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="eb161-251">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="eb161-252">Du kan också tillåta fjärråtkomst i en loopback-session med hjälp av **CredSSP** -värdet för parametern **Authentication** , som delegerar autentiseringsuppgifterna för sessionen till andra datorer.</span><span class="sxs-lookup"><span data-stu-id="eb161-252">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="eb161-253">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="eb161-253">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eb161-254">-HostName</span><span class="sxs-lookup"><span data-stu-id="eb161-254">-HostName</span></span>

<span data-ttu-id="eb161-255">Anger ett dator namn för en SSH-baserad (Secure Shell) anslutning.</span><span class="sxs-lookup"><span data-stu-id="eb161-255">Specifies a computer name for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="eb161-256">Detta liknar parametern **computername** , förutom att anslutningen till fjärrdatorn görs med SSH i stället för Windows WinRM.</span><span class="sxs-lookup"><span data-stu-id="eb161-256">This is similar to the **ComputerName** parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span> <span data-ttu-id="eb161-257">Den här parametern har stöd för att ange användar namnet och/eller porten som en del av värdet för värd namn parametern med hjälp av formuläret `user@hostname:port` .</span><span class="sxs-lookup"><span data-stu-id="eb161-257">This parameter supports specifying the user name and/or port as part of the host name parameter value using the form `user@hostname:port`.</span></span> <span data-ttu-id="eb161-258">Användar namnet och/eller porten som anges som en del av värd namnet har företräde framför `-UserName` `-Port` parametrarna och, om de anges.</span><span class="sxs-lookup"><span data-stu-id="eb161-258">The user name and/or port specified as part of the host name takes precedence over the `-UserName` and `-Port` parameters, if specified.</span></span> <span data-ttu-id="eb161-259">På så sätt kan du skicka flera dator namn till den här parametern där vissa har vissa användar namn och/eller portar, medan andra använder användar namnet och/eller porten från `-UserName` `-Port` parametrarna och.</span><span class="sxs-lookup"><span data-stu-id="eb161-259">This allows passing multiple computer names to this parameter where some have specific user names and/or ports, while others use the user name and/or port from the `-UserName` and `-Port` parameters.</span></span>

<span data-ttu-id="eb161-260">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="eb161-260">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="eb161-261">-ID</span><span class="sxs-lookup"><span data-stu-id="eb161-261">-Id</span></span>

<span data-ttu-id="eb161-262">Anger ID för en befintlig session.</span><span class="sxs-lookup"><span data-stu-id="eb161-262">Specifies the ID of an existing session.</span></span> <span data-ttu-id="eb161-263">`Enter-PSSession` använder den angivna sessionen för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-263">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="eb161-264">Använd cmdleten för att hitta ID: t för en session `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="eb161-264">To find the ID of a session, use the `Get-PSSession` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="eb161-265">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="eb161-265">-InstanceId</span></span>

<span data-ttu-id="eb161-266">Anger instans-ID för en befintlig session.</span><span class="sxs-lookup"><span data-stu-id="eb161-266">Specifies the instance ID of an existing session.</span></span> <span data-ttu-id="eb161-267">`Enter-PSSession` använder den angivna sessionen för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-267">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="eb161-268">Instans-ID: t är ett GUID.</span><span class="sxs-lookup"><span data-stu-id="eb161-268">The instance ID is a GUID.</span></span> <span data-ttu-id="eb161-269">Använd cmdleten för att hitta instans-ID för en session `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="eb161-269">To find the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="eb161-270">Du kan också använda parametrarna **session** , **Name** eller **ID** för att ange en befintlig session.</span><span class="sxs-lookup"><span data-stu-id="eb161-270">You can also use the **Session** , **Name** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="eb161-271">Du kan också använda parametern **computername** för att starta en tillfällig session.</span><span class="sxs-lookup"><span data-stu-id="eb161-271">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

```yaml
Type: System.Guid
Parameter Sets: InstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="eb161-272">-Fil Sök väg</span><span class="sxs-lookup"><span data-stu-id="eb161-272">-KeyFilePath</span></span>

<span data-ttu-id="eb161-273">Anger en nyckel fil Sök väg som används av SSH (Secure Shell) för att autentisera en användare på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="eb161-273">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="eb161-274">SSH tillåter att användarautentisering utförs via privata/offentliga nycklar som ett alternativ till grundläggande lösenordsautentisering.</span><span class="sxs-lookup"><span data-stu-id="eb161-274">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="eb161-275">Om fjärrdatorn har kon figurer ATS för nyckel autentisering kan du använda den här parametern för att ange den nyckel som identifierar användaren.</span><span class="sxs-lookup"><span data-stu-id="eb161-275">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="eb161-276">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="eb161-276">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="eb161-277">-Name</span><span class="sxs-lookup"><span data-stu-id="eb161-277">-Name</span></span>

<span data-ttu-id="eb161-278">Anger det egna namnet på en befintlig session.</span><span class="sxs-lookup"><span data-stu-id="eb161-278">Specifies the friendly name of an existing session.</span></span> <span data-ttu-id="eb161-279">`Enter-PSSession` använder den angivna sessionen för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-279">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="eb161-280">Kommandot Miss lyckas om det namn som du anger matchar mer än en session.</span><span class="sxs-lookup"><span data-stu-id="eb161-280">If the name that you specify matches more than one session, the command fails.</span></span> <span data-ttu-id="eb161-281">Du kan också använda parametrarna **session** , **InstanceID** eller **ID** för att ange en befintlig session.</span><span class="sxs-lookup"><span data-stu-id="eb161-281">You can also use the **Session** , **InstanceID** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="eb161-282">Du kan också använda parametern **computername** för att starta en tillfällig session.</span><span class="sxs-lookup"><span data-stu-id="eb161-282">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

<span data-ttu-id="eb161-283">Om du vill skapa ett eget namn för en session använder du parametern **Name** i `New-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eb161-283">To establish a friendly name for a session, use the **Name** parameter of the `New-PSSession` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="eb161-284">-Port</span><span class="sxs-lookup"><span data-stu-id="eb161-284">-Port</span></span>

<span data-ttu-id="eb161-285">Anger nätverks porten på den fjärrdator som används för det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="eb161-285">Specifies the network port on the remote computer that is used for this command.</span></span>

<span data-ttu-id="eb161-286">I PowerShell 6,0 var den här parametern inlcuded i parametern **hostname** som stöder SSH-anslutningar (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="eb161-286">In PowerShell 6.0 this parameter was inlcuded in the **HostName** parameter set which supports Secure Shell (SSH) connections.</span></span>

<span data-ttu-id="eb161-287">**WinRM (ComputerName-parameter uppsättning)**</span><span class="sxs-lookup"><span data-stu-id="eb161-287">**WinRM (ComputerName parameter set)**</span></span>

<span data-ttu-id="eb161-288">Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder.</span><span class="sxs-lookup"><span data-stu-id="eb161-288">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="eb161-289">Standard portarna är 5985, som är WinRM-porten för HTTP och 5986, som är WinRM-porten för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="eb161-289">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="eb161-290">Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.</span><span class="sxs-lookup"><span data-stu-id="eb161-290">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="eb161-291">Använd följande kommandon för att konfigurera lyssnaren:</span><span class="sxs-lookup"><span data-stu-id="eb161-291">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="eb161-292">Använd inte **port** parametern om du inte behöver.</span><span class="sxs-lookup"><span data-stu-id="eb161-292">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="eb161-293">Port inställningen i kommandot gäller för alla datorer eller sessioner där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="eb161-293">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="eb161-294">En alternativ port inställning kan hindra kommandot från att köras på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="eb161-294">An alternate port setting might prevent the command from running on all computers.</span></span>

<span data-ttu-id="eb161-295">**SSH (HostName parameter uppsättning)**</span><span class="sxs-lookup"><span data-stu-id="eb161-295">**SSH (HostName parameter set)**</span></span>

<span data-ttu-id="eb161-296">Om du vill ansluta till en fjärrdator måste fjärrdatorn konfigureras med SSH-tjänsten (SSHD) och måste lyssna på den port som anslutningen använder.</span><span class="sxs-lookup"><span data-stu-id="eb161-296">To connect to a remote computer, the remote computer must be configured with the SSH service (SSHD) and must be listening on the port that the connection uses.</span></span> <span data-ttu-id="eb161-297">Standard porten för SSH är 22.</span><span class="sxs-lookup"><span data-stu-id="eb161-297">The default port for SSH is 22.</span></span>

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

### <span data-ttu-id="eb161-298">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="eb161-298">-RunAsAdministrator</span></span>

<span data-ttu-id="eb161-299">Anger att **PSSession** körs som administratör.</span><span class="sxs-lookup"><span data-stu-id="eb161-299">Indicates that the **PSSession** runs as administrator.</span></span>

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

### <span data-ttu-id="eb161-300">– Session</span><span class="sxs-lookup"><span data-stu-id="eb161-300">-Session</span></span>

<span data-ttu-id="eb161-301">Anger en PowerShell-session ( **PSSession** ) som ska användas för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-301">Specifies a PowerShell session ( **PSSession** ) to use for the interactive session.</span></span> <span data-ttu-id="eb161-302">Den här parametern tar ett sessionsobjekt.</span><span class="sxs-lookup"><span data-stu-id="eb161-302">This parameter takes a session object.</span></span> <span data-ttu-id="eb161-303">Du kan också använda parametrarna **Name** , **InstanceID** eller **ID** för att ange en **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="eb161-303">You can also use the **Name** , **InstanceID** , or **ID** parameters to specify a **PSSession**.</span></span>

<span data-ttu-id="eb161-304">Ange en variabel som innehåller ett session-objekt eller ett kommando som skapar eller hämtar ett sessionsobjekt, till exempel ett `New-PSSession` eller- `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="eb161-304">Enter a variable that contains a session object or a command that creates or gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="eb161-305">Du kan också skicka ett sessionsobjekt till `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="eb161-305">You can also pipe a session object to `Enter-PSSession`.</span></span> <span data-ttu-id="eb161-306">Du kan bara skicka en **PSSession** med hjälp av den här parametern.</span><span class="sxs-lookup"><span data-stu-id="eb161-306">You can submit only one **PSSession** by using this parameter.</span></span> <span data-ttu-id="eb161-307">Om du anger en variabel som innehåller mer än en **PSSession** Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="eb161-307">If you enter a variable that contains more than one **PSSession** , the command fails.</span></span>

<span data-ttu-id="eb161-308">När du använder `Exit-PSSession` eller **avslutar** -nyckelordet avslutas den interaktiva sessionen, men **PSSession** som du skapade förblir öppen och tillgänglig för användning.</span><span class="sxs-lookup"><span data-stu-id="eb161-308">When you use `Exit-PSSession` or the **EXIT** keyword, the interactive session ends, but the **PSSession** that you created remains open and available for use.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="eb161-309">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="eb161-309">-SessionOption</span></span>

<span data-ttu-id="eb161-310">Ställer in avancerade alternativ för sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-310">Sets advanced options for the session.</span></span> <span data-ttu-id="eb161-311">Ange ett **SessionOption** -objekt, t. ex. ett som du skapar med hjälp av `New-PSSessionOption` cmdleten, eller en hash-tabell där nycklarna är namn på sessionstillstånd och värdena är alternativ värden för session.</span><span class="sxs-lookup"><span data-stu-id="eb161-311">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="eb161-312">Standardvärdena för alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts.</span><span class="sxs-lookup"><span data-stu-id="eb161-312">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="eb161-313">Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-313">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="eb161-314">Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i `$PSSessionOption` variabeln Preference och i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-314">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="eb161-315">De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-315">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="eb161-316">En beskrivning av sessions alternativen, inklusive standardvärdena, finns i `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="eb161-316">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="eb161-317">Information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="eb161-317">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="eb161-318">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="eb161-318">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

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

### <span data-ttu-id="eb161-319">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="eb161-319">-SSHTransport</span></span>

<span data-ttu-id="eb161-320">Anger att fjärr anslutningen upprättas med hjälp av SSH (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="eb161-320">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="eb161-321">Som standard använder PowerShell Windows WinRM för att ansluta till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="eb161-321">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="eb161-322">Den här växeln tvingar PowerShell att använda HostName-parametern som angetts för att upprätta en SSH-baserad fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="eb161-322">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="eb161-323">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="eb161-323">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="eb161-324">-Under system</span><span class="sxs-lookup"><span data-stu-id="eb161-324">-Subsystem</span></span>

<span data-ttu-id="eb161-325">Anger det SSH-undersystem som används för den nya **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="eb161-325">Specifies the SSH subsystem used for the new **PSSession**.</span></span>

<span data-ttu-id="eb161-326">Detta anger under systemet som ska användas på målet som det definieras i sshd_config.</span><span class="sxs-lookup"><span data-stu-id="eb161-326">This specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="eb161-327">Under systemet startar en angiven version av PowerShell med fördefinierade parametrar.</span><span class="sxs-lookup"><span data-stu-id="eb161-327">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span> <span data-ttu-id="eb161-328">Om det angivna under systemet inte finns på fjärrdatorn Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="eb161-328">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="eb161-329">Om den här parametern inte används är standard under systemet "PowerShell".</span><span class="sxs-lookup"><span data-stu-id="eb161-329">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="eb161-330">-UserName</span><span class="sxs-lookup"><span data-stu-id="eb161-330">-UserName</span></span>

<span data-ttu-id="eb161-331">Anger användar namnet för det konto som används för att skapa en session på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-331">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="eb161-332">Metoden för användarautentisering beror på hur Secure Shell (SSH) är konfigurerat på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-332">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="eb161-333">Om SSH har kon figurer ATS för grundläggande lösenordsautentisering uppmanas du att ange användar lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="eb161-333">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="eb161-334">Om SSH har kon figurer ATS för nyckelbaserad användarautentisering kan en nyckel fil Sök väg tillhandahållas via parametern för nyckel **Sök väg** och inget lösen ord visas.</span><span class="sxs-lookup"><span data-stu-id="eb161-334">If SSH is configured for key based user authentication then a key file path can be provided via the **KeyFilePath** parameter and no password prompt will occur.</span></span> <span data-ttu-id="eb161-335">Observera att om klientens användar nyckel finns på en känd SSH-plats behövs inte parametern för nyckel **Sök** vägar för nyckelbaserad autentisering, och användarautentisering sker automatiskt baserat på användar namnet.</span><span class="sxs-lookup"><span data-stu-id="eb161-335">Note that if the client user key file is located in an SSH known location then the **KeyFilePath** parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="eb161-336">Mer information finns i SSH-dokumentationen om nyckelbaserad användarautentisering.</span><span class="sxs-lookup"><span data-stu-id="eb161-336">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="eb161-337">Detta är inte en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="eb161-337">This is not a required parameter.</span></span> <span data-ttu-id="eb161-338">Om ingen **användar namns** parameter anges används den aktuella inloggnings användar namnet för anslutningen.</span><span class="sxs-lookup"><span data-stu-id="eb161-338">If no **UserName** parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="eb161-339">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="eb161-339">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="eb161-340">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="eb161-340">-UseSSL</span></span>

<span data-ttu-id="eb161-341">Anger att denna cmdlet använder Secure Sockets Layer-protokollet (SSL) för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-341">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="eb161-342">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="eb161-342">By default, SSL is not used.</span></span>

<span data-ttu-id="eb161-343">WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="eb161-343">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="eb161-344">Parametern **UseSSL** är ett ytterligare skydd som skickar data via en HTTPS-anslutning i stället för en HTTP-anslutning.</span><span class="sxs-lookup"><span data-stu-id="eb161-344">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="eb161-345">Om du använder den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="eb161-345">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="eb161-346">-VMId</span><span class="sxs-lookup"><span data-stu-id="eb161-346">-VMId</span></span>

<span data-ttu-id="eb161-347">Anger ID för en virtuell dator.</span><span class="sxs-lookup"><span data-stu-id="eb161-347">Specifies the ID of a virtual machine.</span></span>

```yaml
Type: System.Guid
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="eb161-348">– VMName</span><span class="sxs-lookup"><span data-stu-id="eb161-348">-VMName</span></span>

<span data-ttu-id="eb161-349">Anger namnet på en virtuell dator.</span><span class="sxs-lookup"><span data-stu-id="eb161-349">Specifies the name of a virtual machine.</span></span>

```yaml
Type: System.String
Parameter Sets: VMName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="eb161-350">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eb161-350">CommonParameters</span></span>

<span data-ttu-id="eb161-351">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eb161-351">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eb161-352">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="eb161-352">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eb161-353">INDATA</span><span class="sxs-lookup"><span data-stu-id="eb161-353">INPUTS</span></span>

### <span data-ttu-id="eb161-354">System. String, system. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="eb161-354">System.String, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="eb161-355">Du kan skicka vidare ett dator namn, som en sträng eller ett sessionsobjekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb161-355">You can pipe a computer name, as a string, or a session object to this cmdlet.</span></span>

## <span data-ttu-id="eb161-356">UTDATA</span><span class="sxs-lookup"><span data-stu-id="eb161-356">OUTPUTS</span></span>

### <span data-ttu-id="eb161-357">Inget</span><span class="sxs-lookup"><span data-stu-id="eb161-357">None</span></span>

<span data-ttu-id="eb161-358">Cmdleten returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="eb161-358">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="eb161-359">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="eb161-359">NOTES</span></span>

<span data-ttu-id="eb161-360">Om du vill ansluta till en fjärrdator måste du vara medlem i gruppen Administratörer på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="eb161-360">To connect to a remote computer, you must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="eb161-361">Om du vill starta en interaktiv session på den lokala datorn måste du starta PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="eb161-361">To start an interactive session on the local computer, you must start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="eb161-362">När du använder `Enter-PSSession` används din användar profil på fjärrdatorn för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-362">When you use `Enter-PSSession`, your user profile on the remote computer is used for the interactive session.</span></span> <span data-ttu-id="eb161-363">Kommandona i fjärran sluten användar profil, inklusive kommandon för att lägga till PowerShell-moduler och ändra kommando tolken, körs innan fjärrprompten visas.</span><span class="sxs-lookup"><span data-stu-id="eb161-363">The commands in the remote user profile, including commands to add PowerShell modules and to change the command prompt, run before the remote prompt is displayed.</span></span>

<span data-ttu-id="eb161-364">`Enter-PSSession` använder inställningen för användar gränssnitts kulturen på den lokala datorn för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="eb161-364">`Enter-PSSession` uses the UI culture setting on the local computer for the interactive session.</span></span> <span data-ttu-id="eb161-365">Använd den automatiska variabeln för att hitta den lokala användar gränssnitts kulturen `$UICulture` .</span><span class="sxs-lookup"><span data-stu-id="eb161-365">To find the local UI culture, use the `$UICulture` automatic variable.</span></span>

<span data-ttu-id="eb161-366">`Enter-PSSession` kräver `Get-Command` `Out-Default` cmdletarna,, och `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="eb161-366">`Enter-PSSession` requires the `Get-Command`, `Out-Default`, and `Exit-PSSession` cmdlets.</span></span> <span data-ttu-id="eb161-367">Om dessa cmdletar inte ingår i konfigurationen av sessionen på fjärrdatorn `Enter-PSSession` Miss lyckas kommandona.</span><span class="sxs-lookup"><span data-stu-id="eb161-367">If these cmdlets are not included in the session configuration on the remote computer, the `Enter-PSSession` commands fails.</span></span>

<span data-ttu-id="eb161-368">Till skillnad från `Invoke-Command` , som tolkar och tolkar kommandon innan de skickar dem till fjärrdatorn, `Enter-PSSession` skickar kommandona direkt till fjärrdatorn utan tolkning.</span><span class="sxs-lookup"><span data-stu-id="eb161-368">Unlike `Invoke-Command`, which parses and interprets the commands before it sends them to the remote computer, `Enter-PSSession` sends the commands directly to the remote computer without interpretation.</span></span>

<span data-ttu-id="eb161-369">Om sessionen som du vill ange är upptagen med bearbetningen av ett kommando kan det uppstå en fördröjning innan PowerShell svarar på `Enter-PSSession` kommandot.</span><span class="sxs-lookup"><span data-stu-id="eb161-369">If the session you want to enter is busy processing a command, there might be a delay before PowerShell responds to the `Enter-PSSession` command.</span></span> <span data-ttu-id="eb161-370">Du är ansluten så snart sessionen är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="eb161-370">You are connected as soon as the session is available.</span></span> <span data-ttu-id="eb161-371">`Enter-PSSession`Tryck på <kbd>CTRL</kbd> + <kbd>C</kbd>om du vill avbryta kommandot.</span><span class="sxs-lookup"><span data-stu-id="eb161-371">To cancel the `Enter-PSSession` command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="eb161-372">Parameter uppsättningen **hostname** ingick från och med PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="eb161-372">The **HostName** parameter set was included starting with PowerShell 6.0.</span></span> <span data-ttu-id="eb161-373">Den har lagts till för att tillhandahålla PowerShell-fjärrkommunikation baserat på Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="eb161-373">It was added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="eb161-374">Både SSH och PowerShell stöds på flera plattformar (Windows, Linux, macOS) och PowerShell-fjärrkommunikationen fungerar över dessa plattformar där PowerShell och SSH har installerats och kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="eb161-374">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="eb161-375">Detta skiljer sig från den tidigare Windows-fjärrkommunikation som baseras på WinRM och mycket av de särskilda WinRM-funktionerna och begränsningarna gäller inte.</span><span class="sxs-lookup"><span data-stu-id="eb161-375">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="eb161-376">Till exempel stöds inte WinRM-baserade kvoter, sessions alternativ, anpassad slut punkts konfiguration och funktionerna för att koppla från/återansluta.</span><span class="sxs-lookup"><span data-stu-id="eb161-376">For example, WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="eb161-377">Mer information om hur du konfigurerar PowerShell SSH-fjärrkommunikation finns i [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="eb161-377">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="eb161-378">Före PowerShell 7,1 har fjärr kommunikation via SSH inte stöd för andra hopp-fjärrsessioner.</span><span class="sxs-lookup"><span data-stu-id="eb161-378">Prior to PowerShell 7.1, remoting over SSH did not support second-hop remote sessions.</span></span> <span data-ttu-id="eb161-379">Den här funktionen var begränsad till sessioner som använder WinRM.</span><span class="sxs-lookup"><span data-stu-id="eb161-379">This capability was limited to sessions using WinRM.</span></span> <span data-ttu-id="eb161-380">PowerShell 7,1 tillåter `Enter-PSSession` och `Enter-PSHostProcess` fungerar inifrån en interaktiv fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="eb161-380">PowerShell 7.1 allows `Enter-PSSession` and `Enter-PSHostProcess` to work from within any interactive remote session.</span></span>

## <span data-ttu-id="eb161-381">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="eb161-381">RELATED LINKS</span></span>

[<span data-ttu-id="eb161-382">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="eb161-382">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="eb161-383">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="eb161-383">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="eb161-384">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="eb161-384">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="eb161-385">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="eb161-385">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="eb161-386">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="eb161-386">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="eb161-387">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="eb161-387">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="eb161-388">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="eb161-388">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="eb161-389">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="eb161-389">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="eb161-390">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="eb161-390">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="eb161-391">about_Remote</span><span class="sxs-lookup"><span data-stu-id="eb161-391">about_Remote</span></span>](About/about_Remote.md)
