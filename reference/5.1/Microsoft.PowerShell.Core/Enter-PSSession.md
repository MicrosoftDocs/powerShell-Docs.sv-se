---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: 40d9da7d2e7e3233608b893b026c2b89c7155ab1
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/24/2020
ms.locfileid: "93268737"
---
# <span data-ttu-id="017b5-103">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="017b5-103">Enter-PSSession</span></span>

## <span data-ttu-id="017b5-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="017b5-104">SYNOPSIS</span></span>
<span data-ttu-id="017b5-105">Startar en interaktiv session med en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="017b5-105">Starts an interactive session with a remote computer.</span></span>

## <span data-ttu-id="017b5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="017b5-106">SYNTAX</span></span>

### <span data-ttu-id="017b5-107">ComputerName (standard)</span><span class="sxs-lookup"><span data-stu-id="017b5-107">ComputerName (Default)</span></span>

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [-Credential <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="017b5-108">Session</span><span class="sxs-lookup"><span data-stu-id="017b5-108">Session</span></span>

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="017b5-109">URI</span><span class="sxs-lookup"><span data-stu-id="017b5-109">Uri</span></span>

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [-Credential <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="017b5-110">InstanceId</span><span class="sxs-lookup"><span data-stu-id="017b5-110">InstanceId</span></span>

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### <span data-ttu-id="017b5-111">Id</span><span class="sxs-lookup"><span data-stu-id="017b5-111">Id</span></span>

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="017b5-112">Name</span><span class="sxs-lookup"><span data-stu-id="017b5-112">Name</span></span>

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### <span data-ttu-id="017b5-113">VMId</span><span class="sxs-lookup"><span data-stu-id="017b5-113">VMId</span></span>

```
Enter-PSSession [-VMId] <Guid> -Credential <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### <span data-ttu-id="017b5-114">VMName</span><span class="sxs-lookup"><span data-stu-id="017b5-114">VMName</span></span>

```
Enter-PSSession [-VMName] <String> -Credential <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="017b5-115">Hålla</span><span class="sxs-lookup"><span data-stu-id="017b5-115">ContainerId</span></span>

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## <span data-ttu-id="017b5-116">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="017b5-116">DESCRIPTION</span></span>

<span data-ttu-id="017b5-117">`Enter-PSSession`Cmdleten startar en interaktiv session med en enda fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="017b5-117">The `Enter-PSSession` cmdlet starts an interactive session with a single remote computer.</span></span> <span data-ttu-id="017b5-118">Under sessionen, de kommandon som du skriver körs på fjärrdatorn, precis som om du skrev direkt på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-118">During the session, the commands that you type run on the remote computer, just as if you were typing directly on the remote computer.</span></span> <span data-ttu-id="017b5-119">Du kan bara ha en interaktiv session åt gången.</span><span class="sxs-lookup"><span data-stu-id="017b5-119">You can have only one interactive session at a time.</span></span>

<span data-ttu-id="017b5-120">Normalt använder du parametern **computername** för att ange namnet på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-120">Typically, you use the **ComputerName** parameter to specify the name of the remote computer.</span></span>
<span data-ttu-id="017b5-121">Du kan dock även använda en session som du skapar med hjälp av `New-PSSession` cmdleten för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-121">However, you can also use a session that you create by using the `New-PSSession` cmdlet for the interactive session.</span></span> <span data-ttu-id="017b5-122">Du kan dock inte använda `Disconnect-PSSession` `Connect-PSSession` cmdletarna, eller `Receive-PSSession` för att koppla från eller återansluta till en interaktiv session.</span><span class="sxs-lookup"><span data-stu-id="017b5-122">However, you cannot use the `Disconnect-PSSession`, `Connect-PSSession`, or `Receive-PSSession` cmdlets to disconnect from or re-connect to an interactive session.</span></span>

<span data-ttu-id="017b5-123">Om du vill avsluta den interaktiva sessionen och koppla från fjärrdatorn använder du `Exit-PSSession` cmdleten eller typen `exit` .</span><span class="sxs-lookup"><span data-stu-id="017b5-123">To end the interactive session and disconnect from the remote computer, use the `Exit-PSSession` cmdlet, or type `exit`.</span></span>

## <span data-ttu-id="017b5-124">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="017b5-124">EXAMPLES</span></span>

### <span data-ttu-id="017b5-125">Exempel 1: starta en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="017b5-125">Example 1: Start an interactive session</span></span>

```
PS C:\> Enter-PSSession
[localhost]: PS C:\>
```

<span data-ttu-id="017b5-126">Det här kommandot startar en interaktiv session på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-126">This command starts an interactive session on the local computer.</span></span> <span data-ttu-id="017b5-127">Kommando tolken ändras för att visa att du nu kör kommandon i en annan session.</span><span class="sxs-lookup"><span data-stu-id="017b5-127">The command prompt changes to indicate that you are now running commands in a different session.</span></span>

<span data-ttu-id="017b5-128">De kommandon som du anger körs i den nya sessionen och resultatet returneras till Standardsessionen som text.</span><span class="sxs-lookup"><span data-stu-id="017b5-128">The commands that you enter run in the new session, and the results are returned to the default session as text.</span></span>

### <span data-ttu-id="017b5-129">Exempel 2: arbeta med en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="017b5-129">Example 2: Work with an interactive session</span></span>

<span data-ttu-id="017b5-130">Det första kommandot använder `Enter-PSSession` cmdleten för att starta en interaktiv session med Server01, en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="017b5-130">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with Server01, a remote computer.</span></span> <span data-ttu-id="017b5-131">När sessionen startar ändras kommando tolken så att den inkluderar dator namnet.</span><span class="sxs-lookup"><span data-stu-id="017b5-131">When the session starts, the command prompt changes to include the computer name.</span></span>
<span data-ttu-id="017b5-132">Det andra kommandot hämtar Windows PowerShell-processen och dirigerar om utdata till Process.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="017b5-132">The second command gets the Windows PowerShell process and redirects the output to the Process.txt file.</span></span> <span data-ttu-id="017b5-133">Kommandot skickas till fjärrdatorn och filen sparas på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-133">The command is submitted to the remote computer, and the file is saved on the remote computer.</span></span>
<span data-ttu-id="017b5-134">Det tredje kommandot använder nyckelordet **exit** för att avsluta den interaktiva sessionen och stänga anslutningen.</span><span class="sxs-lookup"><span data-stu-id="017b5-134">The third command uses the **Exit** keyword to end the interactive session and close the connection.</span></span>
<span data-ttu-id="017b5-135">Det fjärde kommandot bekräftar att Process.txt-filen finns på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-135">The fourth command confirms that the Process.txt file is on the remote computer.</span></span> <span data-ttu-id="017b5-136">Ett `Get-ChildItem` ("dir")-kommando på den lokala datorn kan inte hitta filen.</span><span class="sxs-lookup"><span data-stu-id="017b5-136">A `Get-ChildItem` ("dir") command on the local computer cannot find the file.</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS C:\>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

<span data-ttu-id="017b5-137">Det här kommandot visar hur du arbetar i en interaktiv session med en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="017b5-137">This command shows how to work in an interactive session with a remote computer.</span></span>

### <span data-ttu-id="017b5-138">Exempel 3: Använd parametern session</span><span class="sxs-lookup"><span data-stu-id="017b5-138">Example 3: Use the Session parameter</span></span>

```powershell
PS C:\> $s = New-PSSession -ComputerName Server01
PS C:\> Enter-PSSession -Session $s
[Server01]: PS C:\>
```

<span data-ttu-id="017b5-139">Dessa kommandon använder parametern **session** för `Enter-PSSession` för att köra den interaktiva sessionen i en befintlig Windows PowerShell-session ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="017b5-139">These commands use the **Session** parameter of `Enter-PSSession` to run the interactive session in an existing Windows PowerShell session ( **PSSession** ).</span></span>

### <span data-ttu-id="017b5-140">Exempel 4: starta en interaktiv session och ange port-och Credential-parametrarna</span><span class="sxs-lookup"><span data-stu-id="017b5-140">Example 4: Start an interactive session and specify the Port and Credential parameters</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS C:\>
```

<span data-ttu-id="017b5-141">Det här kommandot startar en interaktiv session med Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-141">This command starts an interactive session with the Server01 computer.</span></span> <span data-ttu-id="017b5-142">Den använder **port** parametern för att ange porten och parametern **Credential** för att ange kontot för en användare som har behörighet att ansluta till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-142">It uses the **Port** parameter to specify the port and the **Credential** parameter to specify the account of a user who has permission to connect to the remote computer.</span></span>

### <span data-ttu-id="017b5-143">Exempel 5: stoppa en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="017b5-143">Example 5: Stop an interactive session</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS C:\> Exit-PSSession
PS C:\>
```

<span data-ttu-id="017b5-144">Det här exemplet visar hur du startar och stoppar en interaktiv session.</span><span class="sxs-lookup"><span data-stu-id="017b5-144">This example shows how to start and stop an interactive session.</span></span> <span data-ttu-id="017b5-145">Det första kommandot använder `Enter-PSSession` cmdleten för att starta en interaktiv session med Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-145">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

<span data-ttu-id="017b5-146">Det andra kommandot använder `Exit-PSSession` cmdleten för att avsluta sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-146">The second command uses the `Exit-PSSession` cmdlet to end the session.</span></span> <span data-ttu-id="017b5-147">Du kan också använda nyckelordet **exit** för att avsluta den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-147">You can also use the **Exit** keyword to end the interactive session.</span></span> <span data-ttu-id="017b5-148">`Exit-PSSession` och **Avsluta** har samma resultat.</span><span class="sxs-lookup"><span data-stu-id="017b5-148">`Exit-PSSession` and **Exit** have the same effect.</span></span>

## <span data-ttu-id="017b5-149">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="017b5-149">PARAMETERS</span></span>

### <span data-ttu-id="017b5-150">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="017b5-150">-AllowRedirection</span></span>

<span data-ttu-id="017b5-151">Tillåter omdirigering av anslutningen till en alternativ Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="017b5-151">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="017b5-152">Omdirigering tillåts inte som standard.</span><span class="sxs-lookup"><span data-stu-id="017b5-152">By default, redirection is not allowed.</span></span>

<span data-ttu-id="017b5-153">När du använder **ConnectionURI** -parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI.</span><span class="sxs-lookup"><span data-stu-id="017b5-153">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="017b5-154">Som standard omdirigerar Windows PowerShell inte anslutningar, men du kan använda den här parametern om du vill att den ska kunna omdirigera anslutningen.</span><span class="sxs-lookup"><span data-stu-id="017b5-154">By default, Windows PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="017b5-155">Du kan också begränsa hur många gånger anslutningen omdirigeras genom att ändra värdet för alternativet **MaximumConnectionRedirectionCount** session.</span><span class="sxs-lookup"><span data-stu-id="017b5-155">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="017b5-156">Använd parametern **MaximumRedirection** för `New-PSSessionOption` cmdleten eller ange egenskapen **MaximumConnectionRedirectionCount** för `$PSSessionOption` Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="017b5-156">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="017b5-157">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="017b5-157">The default value is 5.</span></span>

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

### <span data-ttu-id="017b5-158">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="017b5-158">-ApplicationName</span></span>

<span data-ttu-id="017b5-159">Anger program namns segmentet för anslutnings-URI: n.</span><span class="sxs-lookup"><span data-stu-id="017b5-159">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="017b5-160">Använd den här parametern för att ange program namnet när du inte använder parametern **ConnectionURI** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="017b5-160">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="017b5-161">Standardvärdet är värdet för Preference- `$PSSessionApplicationName` variabeln på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-161">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="017b5-162">Om den här preferens variabeln inte definieras är standardvärdet WSMAN.</span><span class="sxs-lookup"><span data-stu-id="017b5-162">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="017b5-163">Det här värdet är lämpligt för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="017b5-163">This value is appropriate for most uses.</span></span> <span data-ttu-id="017b5-164">Mer information finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="017b5-164">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="017b5-165">**WinRM** -tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran.</span><span class="sxs-lookup"><span data-stu-id="017b5-165">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="017b5-166">Värdet för den här parametern ska matcha värdet på egenskapen **URLPrefix** för en lyssnare på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-166">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

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

### <span data-ttu-id="017b5-167">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="017b5-167">-Authentication</span></span>

<span data-ttu-id="017b5-168">Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="017b5-168">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="017b5-169">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="017b5-169">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="017b5-170">Default</span><span class="sxs-lookup"><span data-stu-id="017b5-170">Default</span></span>
- <span data-ttu-id="017b5-171">Basic</span><span class="sxs-lookup"><span data-stu-id="017b5-171">Basic</span></span>
- <span data-ttu-id="017b5-172">CredSSP</span><span class="sxs-lookup"><span data-stu-id="017b5-172">Credssp</span></span>
- <span data-ttu-id="017b5-173">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="017b5-173">Digest</span></span>
- <span data-ttu-id="017b5-174">Kerberos</span><span class="sxs-lookup"><span data-stu-id="017b5-174">Kerberos</span></span>
- <span data-ttu-id="017b5-175">Negotiate</span><span class="sxs-lookup"><span data-stu-id="017b5-175">Negotiate</span></span>
- <span data-ttu-id="017b5-176">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="017b5-176">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="017b5-177">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="017b5-177">The default value is Default.</span></span>

<span data-ttu-id="017b5-178">CredSSP-autentisering är endast tillgängligt i Windows Vista, Windows Server 2008 och senare versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="017b5-178">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="017b5-179">Mer information om värdena för den här parametern finns i [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="017b5-179">For more information about the values of this parameter, see [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="017b5-180">Varning! CredSSP-autentisering (Credential Security Support Provider), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="017b5-180">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="017b5-181">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="017b5-181">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="017b5-182">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-182">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

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

### <span data-ttu-id="017b5-183">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="017b5-183">-CertificateThumbprint</span></span>

<span data-ttu-id="017b5-184">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="017b5-184">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="017b5-185">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="017b5-185">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="017b5-186">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="017b5-186">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="017b5-187">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="017b5-187">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="017b5-188">Hämta ett certifikat med hjälp av `Get-Item` kommandot eller `Get-ChildItem` i Windows PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="017b5-188">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the Windows PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="017b5-189">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="017b5-189">-ComputerName</span></span>

<span data-ttu-id="017b5-190">Anger ett dator namn.</span><span class="sxs-lookup"><span data-stu-id="017b5-190">Specifies a computer name.</span></span> <span data-ttu-id="017b5-191">Den här cmdleten startar en interaktiv session med den angivna fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-191">This cmdlet starts an interactive session with the specified remote computer.</span></span> <span data-ttu-id="017b5-192">Ange bara ett dator namn.</span><span class="sxs-lookup"><span data-stu-id="017b5-192">Enter only one computer name.</span></span> <span data-ttu-id="017b5-193">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-193">The default is the local computer.</span></span>

<span data-ttu-id="017b5-194">Ange NetBIOS-namnet, IP-adressen eller det fullständigt kvalificerade domän namnet för datorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-194">Type the NetBIOS name, the IP address, or the fully qualified domain name of the computer.</span></span> <span data-ttu-id="017b5-195">Du kan också skicka ett dator namn till `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="017b5-195">You can also pipe a computer name to `Enter-PSSession`.</span></span>

<span data-ttu-id="017b5-196">Om du vill använda en IP-adress i värdet för parametern **computername** måste kommandot innehålla parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="017b5-196">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="017b5-197">Dessutom måste datorn konfigureras för HTTPS-transport eller fjärrdatorns IP-adress måste ingå i listan WinRM TrustedHosts på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-197">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="017b5-198">Instruktioner för att lägga till ett dator namn i listan TrustedHosts finns i avsnittet om hur du lägger till en dator i listan över betrodda värdar i [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="017b5-198">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="017b5-199">Obs! i Windows Vista och senare versioner av operativ systemet Windows, för att inkludera den lokala datorn i värdet för parametern **computername** , måste du starta Windows PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="017b5-199">Note: In Windows Vista and later versions of the Windows operating system, to include the local computer in the value of the **ComputerName** parameter, you must start Windows PowerShell with the Run as administrator option.</span></span>

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

### <span data-ttu-id="017b5-200">– ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="017b5-200">-ConfigurationName</span></span>

<span data-ttu-id="017b5-201">Anger den sessionsinformation som används för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-201">Specifies the session configuration that is used for the interactive session.</span></span>

<span data-ttu-id="017b5-202">Ange ett konfigurations namn eller den fullständigt kvalificerade resurs-URI: n för en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-202">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="017b5-203">Om du bara anger konfigurations namnet är följande schema-URI anpassningsprefix: `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="017b5-203">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="017b5-204">Sessionens konfiguration för en session finns på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-204">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="017b5-205">Om den angivna konfigurationen av sessionen inte finns på fjärrdatorn Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="017b5-205">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="017b5-206">Standardvärdet är värdet för Preference- `$PSSessionConfigurationName` variabeln på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-206">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="017b5-207">Om den här preferens variabeln inte anges är standardvärdet Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="017b5-207">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="017b5-208">Mer information finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="017b5-208">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

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

### <span data-ttu-id="017b5-209">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="017b5-209">-ConnectionUri</span></span>

<span data-ttu-id="017b5-210">Anger en URI som definierar anslutnings slut punkten för sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-210">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="017b5-211">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="017b5-211">The URI must be fully qualified.</span></span> <span data-ttu-id="017b5-212">Formatet för den här strängen är följande:</span><span class="sxs-lookup"><span data-stu-id="017b5-212">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="017b5-213">Standardvärdet är följande:</span><span class="sxs-lookup"><span data-stu-id="017b5-213">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="017b5-214">Om du inte anger en **ConnectionURI** kan du använda parametrarna **UseSSL** , **computername** , **port** och **ApplicationName** för att ange **ConnectionURI** -värden.</span><span class="sxs-lookup"><span data-stu-id="017b5-214">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="017b5-215">Giltiga värden för URI: n i transport segmentet är HTTP och HTTPS.</span><span class="sxs-lookup"><span data-stu-id="017b5-215">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="017b5-216">Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med hjälp av standard portar: 80 för HTTP och 443 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="017b5-216">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created by using standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="017b5-217">Om du vill använda standard portarna för Windows PowerShell-fjärrkommunikation, anger du Port 5985 för HTTP eller 5986 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="017b5-217">To use the default ports for Windows PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="017b5-218">Om mål datorn omdirigerar anslutningen till en annan URI, förhindrar Windows PowerShell omdirigeringen om du inte använder parametern **AllowRedirection** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="017b5-218">If the destination computer redirects the connection to a different URI, Windows PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

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

### <span data-ttu-id="017b5-219">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="017b5-219">-ContainerId</span></span>

<span data-ttu-id="017b5-220">Anger ID för en behållare.</span><span class="sxs-lookup"><span data-stu-id="017b5-220">Specifies the ID of a container.</span></span>

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

### <span data-ttu-id="017b5-221">-Credential</span><span class="sxs-lookup"><span data-stu-id="017b5-221">-Credential</span></span>

<span data-ttu-id="017b5-222">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="017b5-222">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="017b5-223">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="017b5-223">The default is the current user.</span></span>

<span data-ttu-id="017b5-224">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="017b5-224">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="017b5-225">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="017b5-225">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="017b5-226">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="017b5-226">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="017b5-227">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="017b5-227">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="017b5-228">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="017b5-228">-EnableNetworkAccess</span></span>

<span data-ttu-id="017b5-229">Anger att denna cmdlet lägger till en interaktiv säkerhetstoken till loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="017b5-229">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="017b5-230">Med den interaktiva token kan du köra kommandon i loopback-sessionen som hämtar data från andra datorer.</span><span class="sxs-lookup"><span data-stu-id="017b5-230">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="017b5-231">Du kan till exempel köra ett kommando i sessionen som kopierar XML-filer från en fjärrdator till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-231">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="017b5-232">En loopback-session är en **PSSession** som kommer från och slutar på samma dator.</span><span class="sxs-lookup"><span data-stu-id="017b5-232">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="017b5-233">Om du vill skapa en loopback-session utelämnar du parametern **computername** eller anger värdet till.</span><span class="sxs-lookup"><span data-stu-id="017b5-233">To create a loopback session, omit the **ComputerName** parameter or set its value to .</span></span> <span data-ttu-id="017b5-234">(punkt), localhost eller namnet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-234">(dot), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="017b5-235">Som standard skapas loopback-sessioner med hjälp av en nätverks-token som kanske inte ger behörighet att autentisera till fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="017b5-235">By default, loopback sessions are created by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="017b5-236">Parametern **EnableNetworkAccess** är endast effektiv i loopback-sessioner.</span><span class="sxs-lookup"><span data-stu-id="017b5-236">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="017b5-237">Om du använder **EnableNetworkAccess** när du skapar en-session på en fjärrdator, lyckas kommandot, men parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="017b5-237">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="017b5-238">Du kan också tillåta fjärråtkomst i en loopback-session med hjälp av **CredSSP** -värdet för parametern **Authentication** , som delegerar autentiseringsuppgifterna för sessionen till andra datorer.</span><span class="sxs-lookup"><span data-stu-id="017b5-238">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="017b5-239">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="017b5-239">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="017b5-240">-ID</span><span class="sxs-lookup"><span data-stu-id="017b5-240">-Id</span></span>

<span data-ttu-id="017b5-241">Anger ID för en befintlig session.</span><span class="sxs-lookup"><span data-stu-id="017b5-241">Specifies the ID of an existing session.</span></span> <span data-ttu-id="017b5-242">`Enter-PSSession` använder den angivna sessionen för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-242">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="017b5-243">Använd cmdleten för att hitta ID: t för en session `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="017b5-243">To find the ID of a session, use the `Get-PSSession` cmdlet.</span></span>

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

### <span data-ttu-id="017b5-244">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="017b5-244">-InstanceId</span></span>

<span data-ttu-id="017b5-245">Anger instans-ID för en befintlig session.</span><span class="sxs-lookup"><span data-stu-id="017b5-245">Specifies the instance ID of an existing session.</span></span> <span data-ttu-id="017b5-246">`Enter-PSSession` använder den angivna sessionen för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-246">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="017b5-247">Instans-ID: t är ett GUID.</span><span class="sxs-lookup"><span data-stu-id="017b5-247">The instance ID is a GUID.</span></span> <span data-ttu-id="017b5-248">Använd cmdleten för att hitta instans-ID för en session `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="017b5-248">To find the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="017b5-249">Du kan också använda parametrarna **session** , **Name** eller **ID** för att ange en befintlig session.</span><span class="sxs-lookup"><span data-stu-id="017b5-249">You can also use the **Session** , **Name** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="017b5-250">Du kan också använda parametern **computername** för att starta en tillfällig session.</span><span class="sxs-lookup"><span data-stu-id="017b5-250">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

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

### <span data-ttu-id="017b5-251">-Name</span><span class="sxs-lookup"><span data-stu-id="017b5-251">-Name</span></span>

<span data-ttu-id="017b5-252">Anger det egna namnet på en befintlig session.</span><span class="sxs-lookup"><span data-stu-id="017b5-252">Specifies the friendly name of an existing session.</span></span> <span data-ttu-id="017b5-253">`Enter-PSSession` använder den angivna sessionen för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-253">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="017b5-254">Kommandot Miss lyckas om det namn som du anger matchar mer än en session.</span><span class="sxs-lookup"><span data-stu-id="017b5-254">If the name that you specify matches more than one session, the command fails.</span></span> <span data-ttu-id="017b5-255">Du kan också använda parametrarna **session** , **InstanceID** eller **ID** för att ange en befintlig session.</span><span class="sxs-lookup"><span data-stu-id="017b5-255">You can also use the **Session** , **InstanceID** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="017b5-256">Du kan också använda parametern **computername** för att starta en tillfällig session.</span><span class="sxs-lookup"><span data-stu-id="017b5-256">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

<span data-ttu-id="017b5-257">Om du vill skapa ett eget namn för en session använder du parametern **Name** i `New-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="017b5-257">To establish a friendly name for a session, use the **Name** parameter of the `New-PSSession` cmdlet.</span></span>

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

### <span data-ttu-id="017b5-258">-Port</span><span class="sxs-lookup"><span data-stu-id="017b5-258">-Port</span></span>

<span data-ttu-id="017b5-259">Anger nätverks porten på den fjärrdator som används för det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="017b5-259">Specifies the network port on the remote computer that is used for this command.</span></span> <span data-ttu-id="017b5-260">Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder.</span><span class="sxs-lookup"><span data-stu-id="017b5-260">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="017b5-261">Standard portarna är 5985, som är WinRM-porten för HTTP och 5986, som är WinRM-porten för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="017b5-261">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="017b5-262">Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.</span><span class="sxs-lookup"><span data-stu-id="017b5-262">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="017b5-263">Använd följande kommandon för att konfigurera lyssnaren:</span><span class="sxs-lookup"><span data-stu-id="017b5-263">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="017b5-264">Använd inte **port** parametern om du inte behöver.</span><span class="sxs-lookup"><span data-stu-id="017b5-264">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="017b5-265">Port inställningen i kommandot gäller för alla datorer eller sessioner där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="017b5-265">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="017b5-266">En alternativ port inställning kan hindra kommandot från att köras på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="017b5-266">An alternate port setting might prevent the command from running on all computers.</span></span>

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

### <span data-ttu-id="017b5-267">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="017b5-267">-RunAsAdministrator</span></span>

<span data-ttu-id="017b5-268">Anger att **PSSession** körs som administratör.</span><span class="sxs-lookup"><span data-stu-id="017b5-268">Indicates that the **PSSession** runs as administrator.</span></span>

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

### <span data-ttu-id="017b5-269">– Session</span><span class="sxs-lookup"><span data-stu-id="017b5-269">-Session</span></span>

<span data-ttu-id="017b5-270">Anger en Windows PowerShell-session ( **PSSession** ) som ska användas för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-270">Specifies a Windows PowerShell session ( **PSSession** ) to use for the interactive session.</span></span> <span data-ttu-id="017b5-271">Den här parametern tar ett sessionsobjekt.</span><span class="sxs-lookup"><span data-stu-id="017b5-271">This parameter takes a session object.</span></span> <span data-ttu-id="017b5-272">Du kan också använda parametrarna **Name** , **InstanceID** eller **ID** för att ange en **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="017b5-272">You can also use the **Name** , **InstanceID** , or **ID** parameters to specify a **PSSession**.</span></span>

<span data-ttu-id="017b5-273">Ange en variabel som innehåller ett session-objekt eller ett kommando som skapar eller hämtar ett sessionsobjekt, till exempel ett `New-PSSession` eller- `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="017b5-273">Enter a variable that contains a session object or a command that creates or gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="017b5-274">Du kan också skicka ett sessionsobjekt till `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="017b5-274">You can also pipe a session object to `Enter-PSSession`.</span></span> <span data-ttu-id="017b5-275">Du kan bara skicka en **PSSession** med hjälp av den här parametern.</span><span class="sxs-lookup"><span data-stu-id="017b5-275">You can submit only one **PSSession** by using this parameter.</span></span> <span data-ttu-id="017b5-276">Om du anger en variabel som innehåller mer än en **PSSession** Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="017b5-276">If you enter a variable that contains more than one **PSSession** , the command fails.</span></span>

<span data-ttu-id="017b5-277">När du använder `Exit-PSSession` eller **avslutar** -nyckelordet avslutas den interaktiva sessionen, men **PSSession** som du skapade förblir öppen och tillgänglig för användning.</span><span class="sxs-lookup"><span data-stu-id="017b5-277">When you use `Exit-PSSession` or the **EXIT** keyword, the interactive session ends, but the **PSSession** that you created remains open and available for use.</span></span>

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

### <span data-ttu-id="017b5-278">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="017b5-278">-SessionOption</span></span>

<span data-ttu-id="017b5-279">Ställer in avancerade alternativ för sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-279">Sets advanced options for the session.</span></span> <span data-ttu-id="017b5-280">Ange ett **SessionOption** -objekt, t. ex. ett som du skapar med hjälp av `New-PSSessionOption` cmdleten, eller en hash-tabell där nycklarna är namn på sessionstillstånd och värdena är alternativ värden för session.</span><span class="sxs-lookup"><span data-stu-id="017b5-280">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="017b5-281">Standardvärdena för alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts.</span><span class="sxs-lookup"><span data-stu-id="017b5-281">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="017b5-282">Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-282">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="017b5-283">Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i `$PSSessionOption` variabeln Preference och i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-283">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="017b5-284">De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-284">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="017b5-285">En beskrivning av sessions alternativen, inklusive standardvärdena, finns i `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="017b5-285">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="017b5-286">Information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="017b5-286">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="017b5-287">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="017b5-287">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

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

### <span data-ttu-id="017b5-288">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="017b5-288">-UseSSL</span></span>

<span data-ttu-id="017b5-289">Anger att denna cmdlet använder Secure Sockets Layer-protokollet (SSL) för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-289">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="017b5-290">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="017b5-290">By default, SSL is not used.</span></span>

<span data-ttu-id="017b5-291">WS-Management krypterar allt Windows PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="017b5-291">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="017b5-292">Parametern **UseSSL** är ett ytterligare skydd som skickar data via en HTTPS-anslutning i stället för en HTTP-anslutning.</span><span class="sxs-lookup"><span data-stu-id="017b5-292">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="017b5-293">Om du använder den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="017b5-293">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="017b5-294">-VMId</span><span class="sxs-lookup"><span data-stu-id="017b5-294">-VMId</span></span>

<span data-ttu-id="017b5-295">Anger ID för en virtuell dator.</span><span class="sxs-lookup"><span data-stu-id="017b5-295">Specifies the ID of a virtual machine.</span></span>

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

### <span data-ttu-id="017b5-296">– VMName</span><span class="sxs-lookup"><span data-stu-id="017b5-296">-VMName</span></span>

<span data-ttu-id="017b5-297">Anger namnet på en virtuell dator.</span><span class="sxs-lookup"><span data-stu-id="017b5-297">Specifies the name of a virtual machine.</span></span>

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

### <span data-ttu-id="017b5-298">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="017b5-298">CommonParameters</span></span>

<span data-ttu-id="017b5-299">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="017b5-299">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="017b5-300">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="017b5-300">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="017b5-301">INDATA</span><span class="sxs-lookup"><span data-stu-id="017b5-301">INPUTS</span></span>

### <span data-ttu-id="017b5-302">System. String, system. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="017b5-302">System.String, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="017b5-303">Du kan skicka vidare ett dator namn, som en sträng eller ett sessionsobjekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="017b5-303">You can pipe a computer name, as a string, or a session object to this cmdlet.</span></span>

## <span data-ttu-id="017b5-304">UTDATA</span><span class="sxs-lookup"><span data-stu-id="017b5-304">OUTPUTS</span></span>

### <span data-ttu-id="017b5-305">Inget</span><span class="sxs-lookup"><span data-stu-id="017b5-305">None</span></span>

<span data-ttu-id="017b5-306">Cmdleten returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="017b5-306">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="017b5-307">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="017b5-307">NOTES</span></span>

<span data-ttu-id="017b5-308">Om du vill ansluta till en fjärrdator måste du vara medlem i gruppen Administratörer på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="017b5-308">To connect to a remote computer, you must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="017b5-309">Om du vill starta en interaktiv session på den lokala datorn måste du starta PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="017b5-309">To start an interactive session on the local computer, you must start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="017b5-310">När du använder `Enter-PSSession` används din användar profil på fjärrdatorn för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-310">When you use `Enter-PSSession`, your user profile on the remote computer is used for the interactive session.</span></span> <span data-ttu-id="017b5-311">Kommandona i fjärran sluten användar profil, inklusive kommandon för att lägga till PowerShell-moduler och ändra kommando tolken, körs innan fjärrprompten visas.</span><span class="sxs-lookup"><span data-stu-id="017b5-311">The commands in the remote user profile, including commands to add PowerShell modules and to change the command prompt, run before the remote prompt is displayed.</span></span>

<span data-ttu-id="017b5-312">`Enter-PSSession` använder inställningen för användar gränssnitts kulturen på den lokala datorn för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="017b5-312">`Enter-PSSession` uses the UI culture setting on the local computer for the interactive session.</span></span> <span data-ttu-id="017b5-313">Använd den automatiska variabeln för att hitta den lokala användar gränssnitts kulturen `$UICulture` .</span><span class="sxs-lookup"><span data-stu-id="017b5-313">To find the local UI culture, use the `$UICulture` automatic variable.</span></span>

<span data-ttu-id="017b5-314">`Enter-PSSession` kräver `Get-Command` `Out-Default` cmdletarna,, och `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="017b5-314">`Enter-PSSession` requires the `Get-Command`, `Out-Default`, and `Exit-PSSession` cmdlets.</span></span> <span data-ttu-id="017b5-315">Om dessa cmdletar inte ingår i konfigurationen av sessionen på fjärrdatorn `Enter-PSSession` Miss lyckas kommandona.</span><span class="sxs-lookup"><span data-stu-id="017b5-315">If these cmdlets are not included in the session configuration on the remote computer, the `Enter-PSSession` commands fails.</span></span>

<span data-ttu-id="017b5-316">Till skillnad från `Invoke-Command` , som tolkar och tolkar kommandon innan de skickar dem till fjärrdatorn, `Enter-PSSession` skickar kommandona direkt till fjärrdatorn utan tolkning.</span><span class="sxs-lookup"><span data-stu-id="017b5-316">Unlike `Invoke-Command`, which parses and interprets the commands before it sends them to the remote computer, `Enter-PSSession` sends the commands directly to the remote computer without interpretation.</span></span>

<span data-ttu-id="017b5-317">Om sessionen som du vill ange är upptagen med bearbetningen av ett kommando kan det uppstå en fördröjning innan PowerShell svarar på `Enter-PSSession` kommandot.</span><span class="sxs-lookup"><span data-stu-id="017b5-317">If the session you want to enter is busy processing a command, there might be a delay before PowerShell responds to the `Enter-PSSession` command.</span></span> <span data-ttu-id="017b5-318">Du är ansluten så snart sessionen är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="017b5-318">You are connected as soon as the session is available.</span></span> <span data-ttu-id="017b5-319">`Enter-PSSession`Tryck på <kbd>CTRL</kbd> + <kbd>C</kbd>om du vill avbryta kommandot.</span><span class="sxs-lookup"><span data-stu-id="017b5-319">To cancel the `Enter-PSSession` command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

## <span data-ttu-id="017b5-320">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="017b5-320">RELATED LINKS</span></span>

[<span data-ttu-id="017b5-321">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="017b5-321">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="017b5-322">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="017b5-322">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="017b5-323">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="017b5-323">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="017b5-324">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="017b5-324">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="017b5-325">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="017b5-325">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="017b5-326">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="017b5-326">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="017b5-327">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="017b5-327">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="017b5-328">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="017b5-328">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="017b5-329">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="017b5-329">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="017b5-330">about_Remote</span><span class="sxs-lookup"><span data-stu-id="017b5-330">about_Remote</span></span>](About/about_Remote.md)
