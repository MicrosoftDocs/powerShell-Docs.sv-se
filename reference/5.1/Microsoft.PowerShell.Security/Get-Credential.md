---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 26c4f8c8dcc1fbd56e29f55a6a8c2e6aa37a2842
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "93273428"
---
# <span data-ttu-id="2ed26-103">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="2ed26-103">Get-Credential</span></span>

## <span data-ttu-id="2ed26-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2ed26-104">SYNOPSIS</span></span>
<span data-ttu-id="2ed26-105">Hämtar ett Credential-objekt baserat på ett användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="2ed26-105">Gets a credential object based on a user name and password.</span></span>

## <span data-ttu-id="2ed26-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2ed26-106">SYNTAX</span></span>

### <span data-ttu-id="2ed26-107">CredentialSet (standard)</span><span class="sxs-lookup"><span data-stu-id="2ed26-107">CredentialSet (Default)</span></span>

```
Get-Credential [-Credential] <PSCredential> [<CommonParameters>]
```

### <span data-ttu-id="2ed26-108">MessageSet</span><span class="sxs-lookup"><span data-stu-id="2ed26-108">MessageSet</span></span>

```
Get-Credential -Message <String> [[-UserName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="2ed26-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2ed26-109">DESCRIPTION</span></span>

<span data-ttu-id="2ed26-110">`Get-Credential`Cmdleten skapar ett Credential-objekt för ett angivet användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="2ed26-110">The `Get-Credential` cmdlet creates a credential object for a specified user name and password.</span></span> <span data-ttu-id="2ed26-111">Du kan använda Credential-objektet i säkerhets åtgärder.</span><span class="sxs-lookup"><span data-stu-id="2ed26-111">You can use the credential object in security operations.</span></span>

<span data-ttu-id="2ed26-112">Från och med PowerShell 3,0 kan du använda **meddelande** parametern för att ange ett anpassat meddelande i dialog rutan där användaren uppmanas att ange namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="2ed26-112">Beginning in PowerShell 3.0, you can use the **Message** parameter to specify a customized message on the dialog box that prompts the user for their name and password.</span></span>

<span data-ttu-id="2ed26-113">`Get-Credential`Cmdleten uppmanas användaren att ange ett lösen ord eller ett användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="2ed26-113">The `Get-Credential` cmdlet prompts the user for a password or a user name and password.</span></span> <span data-ttu-id="2ed26-114">Som standard visas en dialog ruta för autentisering där användaren uppmanas att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="2ed26-114">By default, an authentication dialog box appears to prompt the user.</span></span> <span data-ttu-id="2ed26-115">I vissa värd program, t. ex. PowerShell-konsolen, kan du dock bli ombedd att ange användaren på kommando raden genom att ändra en register post.</span><span class="sxs-lookup"><span data-stu-id="2ed26-115">However, in some host programs, such as the PowerShell console, you can prompt the user at the command line by changing a registry entry.</span></span> <span data-ttu-id="2ed26-116">Mer information om den här register posten finns i anteckningar och exempel.</span><span class="sxs-lookup"><span data-stu-id="2ed26-116">For more information about this registry entry, see the notes and examples.</span></span>

## <span data-ttu-id="2ed26-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2ed26-117">EXAMPLES</span></span>

### <span data-ttu-id="2ed26-118">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="2ed26-118">Example 1</span></span>

```powershell
$c = Get-Credential
```

<span data-ttu-id="2ed26-119">Det här kommandot hämtar ett Credential-objekt och sparar det i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ed26-119">This command gets a credential object and saves it in the `$c` variable.</span></span>

<span data-ttu-id="2ed26-120">När du anger kommandot visas en dialog ruta som efterfrågar ett användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="2ed26-120">When you enter the command, a dialog box appears requesting a user name and password.</span></span> <span data-ttu-id="2ed26-121">När du anger den begärda informationen skapar cmdleten ett **PSCredential** -objekt som representerar användarens autentiseringsuppgifter och sparar det i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ed26-121">When you enter the requested information, the cmdlet creates a **PSCredential** object representing the credentials of the user and saves it in the `$c` variable.</span></span>

<span data-ttu-id="2ed26-122">Du kan använda objektet som indata för cmdletar som begär användarautentisering, till exempel de med en **Credential** -parameter.</span><span class="sxs-lookup"><span data-stu-id="2ed26-122">You can use the object as input to cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span> <span data-ttu-id="2ed26-123">Vissa leverantörer som installeras med PowerShell stöder dock inte parametern för **autentiseringsuppgifter** .</span><span class="sxs-lookup"><span data-stu-id="2ed26-123">However, some providers that are installed with PowerShell do not support the **Credential** parameter.</span></span>

### <span data-ttu-id="2ed26-124">Exempel 2</span><span class="sxs-lookup"><span data-stu-id="2ed26-124">Example 2</span></span>

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

<span data-ttu-id="2ed26-125">Dessa kommandon använder ett Credential-objekt som `Get-Credential` cmdleten returnerar för att autentisera en användare på en fjärrdator så att de kan använda Windows Management Instrumentation (WMI) för att hantera datorn.</span><span class="sxs-lookup"><span data-stu-id="2ed26-125">These commands use a credential object that the `Get-Credential` cmdlet returns to authenticate a user on a remote computer so they can use Windows Management Instrumentation (WMI) to manage the computer.</span></span>

<span data-ttu-id="2ed26-126">Det första kommandot hämtar ett Credential-objekt och sparar det i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ed26-126">The first command gets a credential object and saves it in the `$c` variable.</span></span> <span data-ttu-id="2ed26-127">Det andra kommandot använder Credential-objektet i ett `Get-CimInstance` kommando.</span><span class="sxs-lookup"><span data-stu-id="2ed26-127">The second command uses the credential object in a `Get-CimInstance` command.</span></span> <span data-ttu-id="2ed26-128">Det här kommandot hämtar information om disk enheterna på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="2ed26-128">This command gets information about the disk drives on the Server01 computer.</span></span>

### <span data-ttu-id="2ed26-129">Exempel 3</span><span class="sxs-lookup"><span data-stu-id="2ed26-129">Example 3</span></span>

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

<span data-ttu-id="2ed26-130">Det här kommandot visar hur du lägger till ett `Get-Credential` kommando i ett  `Get-CimInstance` kommando.</span><span class="sxs-lookup"><span data-stu-id="2ed26-130">This command shows how to include a `Get-Credential` command in a  `Get-CimInstance` command.</span></span>

<span data-ttu-id="2ed26-131">Det här kommandot använder `Get-CimInstance` cmdleten för att hämta information om BIOS på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="2ed26-131">This command uses the `Get-CimInstance` cmdlet to get information about the BIOS on the Server01 computer.</span></span> <span data-ttu-id="2ed26-132">Den använder parametern **Credential** för att autentisera användaren, Domain01\User01 och ett `Get-Credential` kommando som värde för parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="2ed26-132">It uses the **Credential** parameter to authenticate the user, Domain01\User01, and a `Get-Credential` command as the value of the **Credential** parameter.</span></span>

### <span data-ttu-id="2ed26-133">Exempel 4</span><span class="sxs-lookup"><span data-stu-id="2ed26-133">Example 4</span></span>

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

<span data-ttu-id="2ed26-134">I det här exemplet skapas en autentiseringsuppgift som innehåller ett användar namn utan ett domän namn.</span><span class="sxs-lookup"><span data-stu-id="2ed26-134">This example creates a credential that includes a user name without a domain name.</span></span>

<span data-ttu-id="2ed26-135">Det första kommandot hämtar en autentiseringsuppgift med användar namnet user01 och lagrar det i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ed26-135">The first command gets a credential with the user name User01 and stores it in the `$c` variable.</span></span>
<span data-ttu-id="2ed26-136">Det andra kommandot visar värdet för egenskapen **username** för objektet som resulterande autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="2ed26-136">The second command displays the value of the **Username** property of the resulting credential object.</span></span>

### <span data-ttu-id="2ed26-137">Exempel 5</span><span class="sxs-lookup"><span data-stu-id="2ed26-137">Example 5</span></span>

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

<span data-ttu-id="2ed26-138">Det här kommandot använder **PromptForCredential** -metoden för att uppmana användaren att ange användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="2ed26-138">This command uses the **PromptForCredential** method to prompt the user for their user name and password.</span></span> <span data-ttu-id="2ed26-139">Kommandot sparar de resulterande autentiseringsuppgifterna i `$Credential` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ed26-139">The command saves the resulting credentials in the `$Credential` variable.</span></span>

<span data-ttu-id="2ed26-140">Metoden **PromptForCredential** är ett alternativ till att använda `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2ed26-140">The **PromptForCredential** method is an alternative to using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="2ed26-141">När du använder **PromptForCredential** kan du ange rubriken, meddelandena och användar namnet som visas i meddelande rutan.</span><span class="sxs-lookup"><span data-stu-id="2ed26-141">When you use **PromptForCredential** , you can specify the caption, messages, and user name that appear in the message box.</span></span>

<span data-ttu-id="2ed26-142">Mer information finns i dokumentationen för [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) i SDK.</span><span class="sxs-lookup"><span data-stu-id="2ed26-142">For more information, see the [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) documentation in the SDK.</span></span>

### <span data-ttu-id="2ed26-143">Exempel 6</span><span class="sxs-lookup"><span data-stu-id="2ed26-143">Example 6</span></span>

```powershell
Set-ItemProperty "HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds" -Name ConsolePrompting -Value $true
```

<span data-ttu-id="2ed26-144">Det här exemplet visar hur du ändrar registret så att användaren uppmanas på kommando raden, i stället för att använda en dialog ruta.</span><span class="sxs-lookup"><span data-stu-id="2ed26-144">This example shows how to modify the registry so that the user is prompted at the command line, instead of by using a dialog box.</span></span>

<span data-ttu-id="2ed26-145">Kommandot skapar register posten **ConsolePrompting** och anger värdet true.</span><span class="sxs-lookup"><span data-stu-id="2ed26-145">The command creates the **ConsolePrompting** registry entry and sets its value to True.</span></span> <span data-ttu-id="2ed26-146">Starta PowerShell med alternativet "kör som administratör" för att köra det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="2ed26-146">To run this command, start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="2ed26-147">Om du vill använda en dialog ruta för att ställa frågan ställer du in värdet för ConsolePrompting på falskt ($false) eller använder `Remove-ItemProperty` cmdleten för att ta bort den.</span><span class="sxs-lookup"><span data-stu-id="2ed26-147">To use a dialog box for prompting, set the value of the ConsolePrompting to false ($false) or use the `Remove-ItemProperty` cmdlet to delete it.</span></span>

<span data-ttu-id="2ed26-148">Register posten ConsolePrompting fungerar i vissa värd program, till exempel PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="2ed26-148">The ConsolePrompting registry entry works in some host programs, such as the PowerShell console.</span></span> <span data-ttu-id="2ed26-149">Det kanske inte fungerar i alla värd program.</span><span class="sxs-lookup"><span data-stu-id="2ed26-149">It might not work in all host programs.</span></span>

### <span data-ttu-id="2ed26-150">Exempel 7</span><span class="sxs-lookup"><span data-stu-id="2ed26-150">Example 7</span></span>

<span data-ttu-id="2ed26-151">Det här exemplet visar hur du skapar ett Credential-objekt som är identiskt med det objekt som `Get-Credential` returneras utan att användaren tillkommer.</span><span class="sxs-lookup"><span data-stu-id="2ed26-151">This example shows how to create a credential object that is identical to the object that `Get-Credential` returns without prompting the user.</span></span> <span data-ttu-id="2ed26-152">Den här metoden kräver ett lösen ord för oformaterad text, vilket kan strida mot säkerhets standarder i vissa företag.</span><span class="sxs-lookup"><span data-stu-id="2ed26-152">This method requires a plain text password, which might violate the security standards in some enterprises.</span></span>

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

<span data-ttu-id="2ed26-153">Det första kommandot sparar användar konto namnet i `$User` parametern.</span><span class="sxs-lookup"><span data-stu-id="2ed26-153">The first command saves the user account name in the `$User` parameter.</span></span> <span data-ttu-id="2ed26-154">Värdet måste ha formatet "domän \ användare" eller "ComputerName\User".</span><span class="sxs-lookup"><span data-stu-id="2ed26-154">The value must have the "Domain\User" or "ComputerName\User" format.</span></span>

<span data-ttu-id="2ed26-155">Det andra kommandot använder `ConvertTo-SecureString` cmdleten för att skapa en säker sträng från ett lösen ord med oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="2ed26-155">The second command uses the `ConvertTo-SecureString` cmdlet to create a secure string from a plain text password.</span></span> <span data-ttu-id="2ed26-156">Kommandot använder parametern **Disklar** text för att ange att strängen är oformaterad text och **Force** -parametern för att bekräfta att du förstår riskerna med att använda oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="2ed26-156">The command uses the **AsPlainText** parameter to indicate that the string is plain text and the **Force** parameter to confirm that you understand the risks of using plain text.</span></span>

<span data-ttu-id="2ed26-157">Det tredje kommandot använder `New-Object` cmdleten för att skapa ett **PSCredential** -objekt från värdena i `$User` `$PWord` variablerna och.</span><span class="sxs-lookup"><span data-stu-id="2ed26-157">The third command uses the `New-Object` cmdlet to create a **PSCredential** object from the values in the `$User` and `$PWord` variables.</span></span>

### <span data-ttu-id="2ed26-158">Exempel 8</span><span class="sxs-lookup"><span data-stu-id="2ed26-158">Example 8</span></span>

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

<span data-ttu-id="2ed26-159">Det här kommandot använder cmdlet: en **meddelande** och **användar namn** `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="2ed26-159">This command uses the **Message** and **UserName** parameters of the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="2ed26-160">Det här kommando formatet är utformat för delade skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="2ed26-160">This command format is designed for shared scripts and functions.</span></span> <span data-ttu-id="2ed26-161">I det här fallet visar meddelandet användaren varför autentiseringsuppgifter krävs och ger dem förtroende för att begäran är giltig.</span><span class="sxs-lookup"><span data-stu-id="2ed26-161">In this case, the message tells the user why credentials are needed and gives them confidence that the request is legitimate.</span></span>

### <span data-ttu-id="2ed26-162">Exempel 9</span><span class="sxs-lookup"><span data-stu-id="2ed26-162">Example 9</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Get-Credential Domain01\User02}
```

```Output
PowerShell Credential Request : PowerShell Credential Request
Warning: This credential is being requested by a script or application on the SERVER01 remote computer. Enter your credentials only if you
 trust the remote computer and the application or script requesting it.

Enter your credentials.
Password for user Domain01\User02: ***************

PSComputerName     : Server01
RunspaceId         : 422bdf52-9886-4ada-ab2f-130497c6777f
PSShowComputerName : True
UserName           : Domain01\User01
Password           : System.Security.SecureString
```

<span data-ttu-id="2ed26-163">Det här kommandot hämtar autentiseringsuppgifter från fjärrdatorn Server01.</span><span class="sxs-lookup"><span data-stu-id="2ed26-163">This command gets a credential from the Server01 remote computer.</span></span> <span data-ttu-id="2ed26-164">Kommandot använder `Invoke-Command` cmdleten för att köra ett `Get-Credential` kommando på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="2ed26-164">The command uses the `Invoke-Command` cmdlet to run a `Get-Credential` command on the remote computer.</span></span> <span data-ttu-id="2ed26-165">Utdata visar det fjärranslutna säkerhets meddelande som `Get-Credential` ingår i verifierings frågan.</span><span class="sxs-lookup"><span data-stu-id="2ed26-165">The output shows the remote security message that `Get-Credential` includes in the authentication prompt.</span></span>

## <span data-ttu-id="2ed26-166">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2ed26-166">PARAMETERS</span></span>

### <span data-ttu-id="2ed26-167">-Credential</span><span class="sxs-lookup"><span data-stu-id="2ed26-167">-Credential</span></span>

<span data-ttu-id="2ed26-168">Anger ett användar namn för autentiseringsuppgiften, till exempel **user01** eller **Domain01\User01**.</span><span class="sxs-lookup"><span data-stu-id="2ed26-168">Specifies a user name for the credential, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="2ed26-169">Parameter namnet, `-Credential` , är valfritt.</span><span class="sxs-lookup"><span data-stu-id="2ed26-169">The parameter name, `-Credential`, is optional.</span></span>

<span data-ttu-id="2ed26-170">När du skickar kommandot och anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="2ed26-170">When you submit the command and specify a user name, you're prompted for a password.</span></span> <span data-ttu-id="2ed26-171">Om du utelämnar den här parametern uppmanas du att ange ett användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="2ed26-171">If you omit this parameter, you're prompted for a user name and a password.</span></span>

<span data-ttu-id="2ed26-172">Från och med PowerShell 3,0, om du anger ett användar namn utan en domän, `Get-Credential` infogar inte längre ett omvänt snedstreck före namnet.</span><span class="sxs-lookup"><span data-stu-id="2ed26-172">Starting in PowerShell 3.0, if you enter a user name without a domain, `Get-Credential` no longer inserts a backslash before the name.</span></span>

<span data-ttu-id="2ed26-173">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="2ed26-173">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="2ed26-174">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="2ed26-174">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2ed26-175">– Meddelande</span><span class="sxs-lookup"><span data-stu-id="2ed26-175">-Message</span></span>

<span data-ttu-id="2ed26-176">Anger ett meddelande som visas i autentiserings-prompten.</span><span class="sxs-lookup"><span data-stu-id="2ed26-176">Specifies a message that appears in the authentication prompt.</span></span> <span data-ttu-id="2ed26-177">Den här parametern är avsedd att användas i en funktion eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="2ed26-177">This parameter is designed for use in a function or script.</span></span> <span data-ttu-id="2ed26-178">Du kan använda meddelandet för att förklara för användaren varför du begär autentiseringsuppgifter och hur de ska användas.</span><span class="sxs-lookup"><span data-stu-id="2ed26-178">You can use the message to explain to the user why you are requesting credentials and how they will be used.</span></span>

<span data-ttu-id="2ed26-179">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2ed26-179">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2ed26-180">-UserName</span><span class="sxs-lookup"><span data-stu-id="2ed26-180">-UserName</span></span>

<span data-ttu-id="2ed26-181">Anger ett användar namn.</span><span class="sxs-lookup"><span data-stu-id="2ed26-181">Specifies a user name.</span></span> <span data-ttu-id="2ed26-182">Autentiserings-prompten begär ett lösen ord för användar namnet.</span><span class="sxs-lookup"><span data-stu-id="2ed26-182">The authentication prompt requests a password for the user name.</span></span> <span data-ttu-id="2ed26-183">Som standard är användar namnet tomt och autentiserings-prompten begär både ett användar namn och ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="2ed26-183">By default, the user name is blank and the authentication prompt requests both a user name and password.</span></span>

<span data-ttu-id="2ed26-184">När frågan om autentisering visas i en dialog ruta kan användaren redigera det angivna användar namnet.</span><span class="sxs-lookup"><span data-stu-id="2ed26-184">When the authentication prompt appears in a dialog box, the user can edit the specified user name.</span></span>
<span data-ttu-id="2ed26-185">Användaren kan dock inte ändra användar namnet när prompten visas på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="2ed26-185">However, the user cannot change the user name when the prompt appears at the command line.</span></span> <span data-ttu-id="2ed26-186">När du använder den här parametern i en delad funktion eller ett skript, bör du ta hänsyn till alla möjliga presentationer.</span><span class="sxs-lookup"><span data-stu-id="2ed26-186">When using this parameter in a shared function or script, consider all possible presentations.</span></span>

<span data-ttu-id="2ed26-187">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2ed26-187">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: 1
Default value: None (blank)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2ed26-188">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2ed26-188">CommonParameters</span></span>

<span data-ttu-id="2ed26-189">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2ed26-189">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2ed26-190">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2ed26-190">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2ed26-191">INDATA</span><span class="sxs-lookup"><span data-stu-id="2ed26-191">INPUTS</span></span>

### <span data-ttu-id="2ed26-192">Inget</span><span class="sxs-lookup"><span data-stu-id="2ed26-192">None</span></span>

<span data-ttu-id="2ed26-193">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2ed26-193">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="2ed26-194">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2ed26-194">OUTPUTS</span></span>

### <span data-ttu-id="2ed26-195">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="2ed26-195">System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="2ed26-196">`Get-Credential` Returnerar ett Credential-objekt.</span><span class="sxs-lookup"><span data-stu-id="2ed26-196">`Get-Credential` returns a credential object.</span></span>

## <span data-ttu-id="2ed26-197">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2ed26-197">NOTES</span></span>

<span data-ttu-id="2ed26-198">Du kan använda **PSCredential** -objektet som `Get-Credential` skapar i-cmdletar som begär användarautentisering, till exempel de med en **Credential** -parameter.</span><span class="sxs-lookup"><span data-stu-id="2ed26-198">You can use the **PSCredential** object that `Get-Credential` creates in cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span>

<span data-ttu-id="2ed26-199">Som standard visas verifierings frågan i en dialog ruta.</span><span class="sxs-lookup"><span data-stu-id="2ed26-199">By default, the authentication prompt appears in a dialog box.</span></span> <span data-ttu-id="2ed26-200">Om du vill visa verifierings frågan på kommando raden lägger du till register posten **ConsolePrompting** ( `HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\ConsolePrompting` ) och anger värdet till **Sant**.</span><span class="sxs-lookup"><span data-stu-id="2ed26-200">To display the authentication prompt at the command line, add the **ConsolePrompting** registry entry (`HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\ConsolePrompting`) and set its value to **True**.</span></span>
<span data-ttu-id="2ed26-201">Om register posten **ConsolePrompting** inte finns eller om värdet är false visas autentiseringen i en dialog ruta.</span><span class="sxs-lookup"><span data-stu-id="2ed26-201">If the **ConsolePrompting** registry entry does not exist or if its value is False, the authentication prompt appears in a dialog box.</span></span> <span data-ttu-id="2ed26-202">Anvisningar finns i exemplen.</span><span class="sxs-lookup"><span data-stu-id="2ed26-202">For instructions, see the examples.</span></span>

<span data-ttu-id="2ed26-203">Register posten **ConsolePrompting** fungerar i PowerShell-konsolen, men fungerar inte i alla värd program.</span><span class="sxs-lookup"><span data-stu-id="2ed26-203">The **ConsolePrompting** registry entry works in the PowerShell console, but it does not work in all host programs.</span></span>

<span data-ttu-id="2ed26-204">Den har till exempel ingen inverkan i PowerShell-miljön (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="2ed26-204">For example, it has no effect in the PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="2ed26-205">Information om effekterna av register posten **ConsolePrompting** finns i hjälp avsnitten för värd programmet.</span><span class="sxs-lookup"><span data-stu-id="2ed26-205">For information about the effect of the **ConsolePrompting** registry entry, see the help topics for the host program.</span></span>

<span data-ttu-id="2ed26-206">Parametern **Credential** stöds inte av alla providers som är installerade med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ed26-206">The **Credential** parameter is not supported by all providers that are installed with PowerShell.</span></span>
<span data-ttu-id="2ed26-207">Från och med PowerShell 3,0 stöds det på utvalda cmdlets, till exempel `Get-Content` `New-PSDrive` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="2ed26-207">Beginning in PowerShell 3.0, it is supported on select cmdlets, such as the `Get-Content` and `New-PSDrive` cmdlets.</span></span>

## <span data-ttu-id="2ed26-208">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2ed26-208">RELATED LINKS</span></span>

[<span data-ttu-id="2ed26-209">PromptForCredential</span><span class="sxs-lookup"><span data-stu-id="2ed26-209">PromptForCredential</span></span>](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
