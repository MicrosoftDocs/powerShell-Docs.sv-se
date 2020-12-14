---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 5630c4d09a2806eb117d005466d4925c1740d3a7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708725"
---
# <span data-ttu-id="be9ef-102">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="be9ef-102">Get-Credential</span></span>

## <span data-ttu-id="be9ef-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="be9ef-103">SYNOPSIS</span></span>
<span data-ttu-id="be9ef-104">Hämtar ett Credential-objekt baserat på ett användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="be9ef-104">Gets a credential object based on a user name and password.</span></span>

## <span data-ttu-id="be9ef-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="be9ef-105">SYNTAX</span></span>

### <span data-ttu-id="be9ef-106">CredentialSet (standard)</span><span class="sxs-lookup"><span data-stu-id="be9ef-106">CredentialSet (Default)</span></span>

```
Get-Credential [[-Credential] <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="be9ef-107">MessageSet</span><span class="sxs-lookup"><span data-stu-id="be9ef-107">MessageSet</span></span>

```
Get-Credential [-Message <String>] [[-UserName] <String>] [-Title <String>] [<CommonParameters>]
```

## <span data-ttu-id="be9ef-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="be9ef-108">DESCRIPTION</span></span>

<span data-ttu-id="be9ef-109">`Get-Credential`Cmdleten skapar ett Credential-objekt för ett angivet användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="be9ef-109">The `Get-Credential` cmdlet creates a credential object for a specified user name and password.</span></span> <span data-ttu-id="be9ef-110">Du kan använda Credential-objektet i säkerhets åtgärder.</span><span class="sxs-lookup"><span data-stu-id="be9ef-110">You can use the credential object in security operations.</span></span>

<span data-ttu-id="be9ef-111">`Get-Credential`Cmdleten uppmanas användaren att ange ett lösen ord eller ett användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="be9ef-111">The `Get-Credential` cmdlet prompts the user for a password or a user name and password.</span></span> <span data-ttu-id="be9ef-112">Du kan använda **meddelande** parametern för att ange ett anpassat meddelande i kommando rads tolken.</span><span class="sxs-lookup"><span data-stu-id="be9ef-112">You can use the **Message** parameter to specify a customized message in the command line prompt.</span></span>

## <span data-ttu-id="be9ef-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="be9ef-113">EXAMPLES</span></span>

### <span data-ttu-id="be9ef-114">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="be9ef-114">Example 1</span></span>

```powershell
$c = Get-Credential
```

<span data-ttu-id="be9ef-115">Det här kommandot hämtar ett Credential-objekt och sparar det i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="be9ef-115">This command gets a credential object and saves it in the `$c` variable.</span></span>

<span data-ttu-id="be9ef-116">När du anger kommandot uppmanas du att ange ett användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="be9ef-116">When you enter the command, you are prompted for a user name and password.</span></span> <span data-ttu-id="be9ef-117">När du anger den begärda informationen skapar cmdleten ett **PSCredential** -objekt som representerar användarens autentiseringsuppgifter och sparar det i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="be9ef-117">When you enter the requested information, the cmdlet creates a **PSCredential** object representing the credentials of the user and saves it in the `$c` variable.</span></span>

<span data-ttu-id="be9ef-118">Du kan använda objektet som indata för cmdletar som begär användarautentisering, till exempel de med en **Credential** -parameter.</span><span class="sxs-lookup"><span data-stu-id="be9ef-118">You can use the object as input to cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span> <span data-ttu-id="be9ef-119">Vissa leverantörer som installeras med PowerShell stöder dock inte parametern för **autentiseringsuppgifter** .</span><span class="sxs-lookup"><span data-stu-id="be9ef-119">However, some providers that are installed with PowerShell do not support the **Credential** parameter.</span></span>

### <span data-ttu-id="be9ef-120">Exempel 2</span><span class="sxs-lookup"><span data-stu-id="be9ef-120">Example 2</span></span>

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

<span data-ttu-id="be9ef-121">Dessa kommandon använder ett Credential-objekt som `Get-Credential` cmdleten returnerar för att autentisera en användare på en fjärrdator så att de kan använda Windows Management Instrumentation (WMI) för att hantera datorn.</span><span class="sxs-lookup"><span data-stu-id="be9ef-121">These commands use a credential object that the `Get-Credential` cmdlet returns to authenticate a user on a remote computer so they can use Windows Management Instrumentation (WMI) to manage the computer.</span></span>

<span data-ttu-id="be9ef-122">Det första kommandot hämtar ett Credential-objekt och sparar det i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="be9ef-122">The first command gets a credential object and saves it in the `$c` variable.</span></span> <span data-ttu-id="be9ef-123">Det andra kommandot använder Credential-objektet i ett `Get-CimInstance` kommando.</span><span class="sxs-lookup"><span data-stu-id="be9ef-123">The second command uses the credential object in a `Get-CimInstance` command.</span></span> <span data-ttu-id="be9ef-124">Det här kommandot hämtar information om disk enheterna på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="be9ef-124">This command gets information about the disk drives on the Server01 computer.</span></span>

### <span data-ttu-id="be9ef-125">Exempel 3</span><span class="sxs-lookup"><span data-stu-id="be9ef-125">Example 3</span></span>

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

<span data-ttu-id="be9ef-126">Det här kommandot visar hur du lägger till ett `Get-Credential` kommando i ett  `Get-CimInstance` kommando.</span><span class="sxs-lookup"><span data-stu-id="be9ef-126">This command shows how to include a `Get-Credential` command in a  `Get-CimInstance` command.</span></span>

<span data-ttu-id="be9ef-127">Det här kommandot använder `Get-CimInstance` cmdleten för att hämta information om BIOS på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="be9ef-127">This command uses the `Get-CimInstance` cmdlet to get information about the BIOS on the Server01 computer.</span></span> <span data-ttu-id="be9ef-128">Den använder parametern **Credential** för att autentisera användaren, Domain01\User01 och ett `Get-Credential` kommando som värde för parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="be9ef-128">It uses the **Credential** parameter to authenticate the user, Domain01\User01, and a `Get-Credential` command as the value of the **Credential** parameter.</span></span>

### <span data-ttu-id="be9ef-129">Exempel 4</span><span class="sxs-lookup"><span data-stu-id="be9ef-129">Example 4</span></span>

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

<span data-ttu-id="be9ef-130">I det här exemplet skapas en autentiseringsuppgift som innehåller ett användar namn utan ett domän namn.</span><span class="sxs-lookup"><span data-stu-id="be9ef-130">This example creates a credential that includes a user name without a domain name.</span></span>

<span data-ttu-id="be9ef-131">Det första kommandot hämtar en autentiseringsuppgift med användar namnet user01 och lagrar det i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="be9ef-131">The first command gets a credential with the user name User01 and stores it in the `$c` variable.</span></span>
<span data-ttu-id="be9ef-132">Det andra kommandot visar värdet för egenskapen **username** för objektet som resulterande autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="be9ef-132">The second command displays the value of the **Username** property of the resulting credential object.</span></span>

### <span data-ttu-id="be9ef-133">Exempel 5</span><span class="sxs-lookup"><span data-stu-id="be9ef-133">Example 5</span></span>

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

<span data-ttu-id="be9ef-134">Det här kommandot använder **PromptForCredential** -metoden för att uppmana användaren att ange användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="be9ef-134">This command uses the **PromptForCredential** method to prompt the user for their user name and password.</span></span> <span data-ttu-id="be9ef-135">Kommandot sparar de resulterande autentiseringsuppgifterna i `$Credential` variabeln.</span><span class="sxs-lookup"><span data-stu-id="be9ef-135">The command saves the resulting credentials in the `$Credential` variable.</span></span>

<span data-ttu-id="be9ef-136">Metoden **PromptForCredential** är ett alternativ till att använda `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="be9ef-136">The **PromptForCredential** method is an alternative to using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="be9ef-137">När du använder **PromptForCredential** kan du ange rubriken, meddelandena och användar namnet som visas i prompten.</span><span class="sxs-lookup"><span data-stu-id="be9ef-137">When you use **PromptForCredential**, you can specify the caption, messages, and user name that appear in the prompt.</span></span>

<span data-ttu-id="be9ef-138">Mer information finns i dokumentationen för [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) i SDK.</span><span class="sxs-lookup"><span data-stu-id="be9ef-138">For more information, see the [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) documentation in the SDK.</span></span>

### <span data-ttu-id="be9ef-139">Exempel 6</span><span class="sxs-lookup"><span data-stu-id="be9ef-139">Example 6</span></span>

<span data-ttu-id="be9ef-140">Det här exemplet visar hur du skapar ett Credential-objekt som är identiskt med det objekt som `Get-Credential` returneras utan att användaren tillkommer.</span><span class="sxs-lookup"><span data-stu-id="be9ef-140">This example shows how to create a credential object that is identical to the object that `Get-Credential` returns without prompting the user.</span></span> <span data-ttu-id="be9ef-141">Den här metoden kräver ett lösen ord för oformaterad text, vilket kan strida mot säkerhets standarder i vissa företag.</span><span class="sxs-lookup"><span data-stu-id="be9ef-141">This method requires a plain text password, which might violate the security standards in some enterprises.</span></span>

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

<span data-ttu-id="be9ef-142">Det första kommandot sparar användar konto namnet i `$User` parametern.</span><span class="sxs-lookup"><span data-stu-id="be9ef-142">The first command saves the user account name in the `$User` parameter.</span></span> <span data-ttu-id="be9ef-143">Värdet måste ha formatet "domän \ användare" eller "ComputerName\User".</span><span class="sxs-lookup"><span data-stu-id="be9ef-143">The value must have the "Domain\User" or "ComputerName\User" format.</span></span>

<span data-ttu-id="be9ef-144">Det andra kommandot använder `ConvertTo-SecureString` cmdleten för att skapa en säker sträng från ett lösen ord med oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="be9ef-144">The second command uses the `ConvertTo-SecureString` cmdlet to create a secure string from a plain text password.</span></span> <span data-ttu-id="be9ef-145">Kommandot använder parametern **Disklar** text för att ange att strängen är oformaterad text och **Force** -parametern för att bekräfta att du förstår riskerna med att använda oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="be9ef-145">The command uses the **AsPlainText** parameter to indicate that the string is plain text and the **Force** parameter to confirm that you understand the risks of using plain text.</span></span>

<span data-ttu-id="be9ef-146">Det tredje kommandot använder `New-Object` cmdleten för att skapa ett **PSCredential** -objekt från värdena i `$User` `$PWord` variablerna och.</span><span class="sxs-lookup"><span data-stu-id="be9ef-146">The third command uses the `New-Object` cmdlet to create a **PSCredential** object from the values in the `$User` and `$PWord` variables.</span></span>

### <span data-ttu-id="be9ef-147">Exempel 7</span><span class="sxs-lookup"><span data-stu-id="be9ef-147">Example 7</span></span>

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

<span data-ttu-id="be9ef-148">Det här kommandot använder cmdlet: en **meddelande** och **användar namn** `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="be9ef-148">This command uses the **Message** and **UserName** parameters of the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="be9ef-149">Det här kommando formatet är utformat för delade skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="be9ef-149">This command format is designed for shared scripts and functions.</span></span> <span data-ttu-id="be9ef-150">I det här fallet visar meddelandet användaren varför autentiseringsuppgifter krävs och ger dem förtroende för att begäran är giltig.</span><span class="sxs-lookup"><span data-stu-id="be9ef-150">In this case, the message tells the user why credentials are needed and gives them confidence that the request is legitimate.</span></span>

### <span data-ttu-id="be9ef-151">Exempel 8</span><span class="sxs-lookup"><span data-stu-id="be9ef-151">Example 8</span></span>

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

<span data-ttu-id="be9ef-152">Det här kommandot hämtar autentiseringsuppgifter från fjärrdatorn Server01.</span><span class="sxs-lookup"><span data-stu-id="be9ef-152">This command gets a credential from the Server01 remote computer.</span></span> <span data-ttu-id="be9ef-153">Kommandot använder `Invoke-Command` cmdleten för att köra ett `Get-Credential` kommando på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="be9ef-153">The command uses the `Invoke-Command` cmdlet to run a `Get-Credential` command on the remote computer.</span></span> <span data-ttu-id="be9ef-154">Utdata visar det fjärranslutna säkerhets meddelande som `Get-Credential` ingår i verifierings frågan.</span><span class="sxs-lookup"><span data-stu-id="be9ef-154">The output shows the remote security message that `Get-Credential` includes in the authentication prompt.</span></span>

## <span data-ttu-id="be9ef-155">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="be9ef-155">PARAMETERS</span></span>

### <span data-ttu-id="be9ef-156">-Credential</span><span class="sxs-lookup"><span data-stu-id="be9ef-156">-Credential</span></span>

<span data-ttu-id="be9ef-157">Anger ett användar namn för autentiseringsuppgiften, till exempel **user01** eller **Domain01\User01**.</span><span class="sxs-lookup"><span data-stu-id="be9ef-157">Specifies a user name for the credential, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="be9ef-158">Parameter namnet, `-Credential` , är valfritt.</span><span class="sxs-lookup"><span data-stu-id="be9ef-158">The parameter name, `-Credential`, is optional.</span></span>

<span data-ttu-id="be9ef-159">När du skickar kommandot och anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="be9ef-159">When you submit the command and specify a user name, you're prompted for a password.</span></span> <span data-ttu-id="be9ef-160">Om du utelämnar den här parametern uppmanas du att ange ett användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="be9ef-160">If you omit this parameter, you're prompted for a user name and a password.</span></span>

<span data-ttu-id="be9ef-161">Från och med PowerShell 3,0, om du anger ett användar namn utan en domän, `Get-Credential` infogar inte längre ett omvänt snedstreck före namnet.</span><span class="sxs-lookup"><span data-stu-id="be9ef-161">Starting in PowerShell 3.0, if you enter a user name without a domain, `Get-Credential` no longer inserts a backslash before the name.</span></span>

<span data-ttu-id="be9ef-162">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="be9ef-162">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="be9ef-163">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="be9ef-163">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be9ef-164">– Meddelande</span><span class="sxs-lookup"><span data-stu-id="be9ef-164">-Message</span></span>

<span data-ttu-id="be9ef-165">Anger ett meddelande som visas i autentiserings-prompten.</span><span class="sxs-lookup"><span data-stu-id="be9ef-165">Specifies a message that appears in the authentication prompt.</span></span> <span data-ttu-id="be9ef-166">Den här parametern är avsedd att användas i en funktion eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="be9ef-166">This parameter is designed for use in a function or script.</span></span> <span data-ttu-id="be9ef-167">Du kan använda meddelandet för att förklara för användaren varför du begär autentiseringsuppgifter och hur de ska användas.</span><span class="sxs-lookup"><span data-stu-id="be9ef-167">You can use the message to explain to the user why you are requesting credentials and how they will be used.</span></span>

<span data-ttu-id="be9ef-168">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="be9ef-168">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be9ef-169">– Rubrik</span><span class="sxs-lookup"><span data-stu-id="be9ef-169">-Title</span></span>

<span data-ttu-id="be9ef-170">Anger texten på rubrik raden för autentiserings-prompten i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="be9ef-170">Sets the text of the title line for the authentication prompt in the console.</span></span>

<span data-ttu-id="be9ef-171">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="be9ef-171">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be9ef-172">-UserName</span><span class="sxs-lookup"><span data-stu-id="be9ef-172">-UserName</span></span>

<span data-ttu-id="be9ef-173">Anger ett användar namn.</span><span class="sxs-lookup"><span data-stu-id="be9ef-173">Specifies a user name.</span></span> <span data-ttu-id="be9ef-174">Autentiserings-prompten begär ett lösen ord för användar namnet.</span><span class="sxs-lookup"><span data-stu-id="be9ef-174">The authentication prompt requests a password for the user name.</span></span> <span data-ttu-id="be9ef-175">Som standard är användar namnet tomt och autentiserings-prompten begär både ett användar namn och ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="be9ef-175">By default, the user name is blank and the authentication prompt requests both a user name and password.</span></span>

<span data-ttu-id="be9ef-176">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="be9ef-176">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="be9ef-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="be9ef-177">CommonParameters</span></span>

<span data-ttu-id="be9ef-178">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="be9ef-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="be9ef-179">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="be9ef-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="be9ef-180">INDATA</span><span class="sxs-lookup"><span data-stu-id="be9ef-180">INPUTS</span></span>

### <span data-ttu-id="be9ef-181">Inga</span><span class="sxs-lookup"><span data-stu-id="be9ef-181">None</span></span>

<span data-ttu-id="be9ef-182">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be9ef-182">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="be9ef-183">UTDATA</span><span class="sxs-lookup"><span data-stu-id="be9ef-183">OUTPUTS</span></span>

### <span data-ttu-id="be9ef-184">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="be9ef-184">System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="be9ef-185">`Get-Credential` Returnerar ett Credential-objekt.</span><span class="sxs-lookup"><span data-stu-id="be9ef-185">`Get-Credential` returns a credential object.</span></span>

## <span data-ttu-id="be9ef-186">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="be9ef-186">NOTES</span></span>

<span data-ttu-id="be9ef-187">Du kan använda **PSCredential** -objektet som `Get-Credential` skapar i-cmdletar som begär användarautentisering, till exempel de med en **Credential** -parameter.</span><span class="sxs-lookup"><span data-stu-id="be9ef-187">You can use the **PSCredential** object that `Get-Credential` creates in cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span>

<span data-ttu-id="be9ef-188">Parametern **Credential** stöds inte av alla providers som är installerade med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="be9ef-188">The **Credential** parameter is not supported by all providers that are installed with PowerShell.</span></span>
<span data-ttu-id="be9ef-189">Från och med PowerShell 3,0 stöds det på utvalda cmdlets, till exempel `Get-Content` `New-PSDrive` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="be9ef-189">Beginning in PowerShell 3.0, it is supported on select cmdlets, such as the `Get-Content` and `New-PSDrive` cmdlets.</span></span>

## <span data-ttu-id="be9ef-190">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="be9ef-190">RELATED LINKS</span></span>

[<span data-ttu-id="be9ef-191">PromptForCredential</span><span class="sxs-lookup"><span data-stu-id="be9ef-191">PromptForCredential</span></span>](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
