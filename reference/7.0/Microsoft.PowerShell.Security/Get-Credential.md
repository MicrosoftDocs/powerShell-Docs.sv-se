---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 2ff87c8d4b714be3b5be3bfe8f384b4c89c25272
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "93273452"
---
# <span data-ttu-id="f09dd-103">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="f09dd-103">Get-Credential</span></span>

## <span data-ttu-id="f09dd-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f09dd-104">SYNOPSIS</span></span>
<span data-ttu-id="f09dd-105">Hämtar ett Credential-objekt baserat på ett användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="f09dd-105">Gets a credential object based on a user name and password.</span></span>

## <span data-ttu-id="f09dd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f09dd-106">SYNTAX</span></span>

### <span data-ttu-id="f09dd-107">CredentialSet (standard)</span><span class="sxs-lookup"><span data-stu-id="f09dd-107">CredentialSet (Default)</span></span>

```
Get-Credential [[-Credential] <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="f09dd-108">MessageSet</span><span class="sxs-lookup"><span data-stu-id="f09dd-108">MessageSet</span></span>

```
Get-Credential [-Message <String>] [[-UserName] <String>] [-Title <String>] [<CommonParameters>]
```

## <span data-ttu-id="f09dd-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f09dd-109">DESCRIPTION</span></span>

<span data-ttu-id="f09dd-110">`Get-Credential`Cmdleten skapar ett Credential-objekt för ett angivet användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="f09dd-110">The `Get-Credential` cmdlet creates a credential object for a specified user name and password.</span></span> <span data-ttu-id="f09dd-111">Du kan använda Credential-objektet i säkerhets åtgärder.</span><span class="sxs-lookup"><span data-stu-id="f09dd-111">You can use the credential object in security operations.</span></span>

<span data-ttu-id="f09dd-112">`Get-Credential`Cmdleten uppmanas användaren att ange ett lösen ord eller ett användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="f09dd-112">The `Get-Credential` cmdlet prompts the user for a password or a user name and password.</span></span> <span data-ttu-id="f09dd-113">Du kan använda **meddelande** parametern för att ange ett anpassat meddelande i kommando rads tolken.</span><span class="sxs-lookup"><span data-stu-id="f09dd-113">You can use the **Message** parameter to specify a customized message in the command line prompt.</span></span>

## <span data-ttu-id="f09dd-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f09dd-114">EXAMPLES</span></span>

### <span data-ttu-id="f09dd-115">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="f09dd-115">Example 1</span></span>

```powershell
$c = Get-Credential
```

<span data-ttu-id="f09dd-116">Det här kommandot hämtar ett Credential-objekt och sparar det i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f09dd-116">This command gets a credential object and saves it in the `$c` variable.</span></span>

<span data-ttu-id="f09dd-117">När du anger kommandot uppmanas du att ange ett användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="f09dd-117">When you enter the command, you are prompted for a user name and password.</span></span> <span data-ttu-id="f09dd-118">När du anger den begärda informationen skapar cmdleten ett **PSCredential** -objekt som representerar användarens autentiseringsuppgifter och sparar det i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f09dd-118">When you enter the requested information, the cmdlet creates a **PSCredential** object representing the credentials of the user and saves it in the `$c` variable.</span></span>

<span data-ttu-id="f09dd-119">Du kan använda objektet som indata för cmdletar som begär användarautentisering, till exempel de med en **Credential** -parameter.</span><span class="sxs-lookup"><span data-stu-id="f09dd-119">You can use the object as input to cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span> <span data-ttu-id="f09dd-120">Vissa leverantörer som installeras med PowerShell stöder dock inte parametern för **autentiseringsuppgifter** .</span><span class="sxs-lookup"><span data-stu-id="f09dd-120">However, some providers that are installed with PowerShell do not support the **Credential** parameter.</span></span>

### <span data-ttu-id="f09dd-121">Exempel 2</span><span class="sxs-lookup"><span data-stu-id="f09dd-121">Example 2</span></span>

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

<span data-ttu-id="f09dd-122">Dessa kommandon använder ett Credential-objekt som `Get-Credential` cmdleten returnerar för att autentisera en användare på en fjärrdator så att de kan använda Windows Management Instrumentation (WMI) för att hantera datorn.</span><span class="sxs-lookup"><span data-stu-id="f09dd-122">These commands use a credential object that the `Get-Credential` cmdlet returns to authenticate a user on a remote computer so they can use Windows Management Instrumentation (WMI) to manage the computer.</span></span>

<span data-ttu-id="f09dd-123">Det första kommandot hämtar ett Credential-objekt och sparar det i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f09dd-123">The first command gets a credential object and saves it in the `$c` variable.</span></span> <span data-ttu-id="f09dd-124">Det andra kommandot använder Credential-objektet i ett `Get-CimInstance` kommando.</span><span class="sxs-lookup"><span data-stu-id="f09dd-124">The second command uses the credential object in a `Get-CimInstance` command.</span></span> <span data-ttu-id="f09dd-125">Det här kommandot hämtar information om disk enheterna på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="f09dd-125">This command gets information about the disk drives on the Server01 computer.</span></span>

### <span data-ttu-id="f09dd-126">Exempel 3</span><span class="sxs-lookup"><span data-stu-id="f09dd-126">Example 3</span></span>

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

<span data-ttu-id="f09dd-127">Det här kommandot visar hur du lägger till ett `Get-Credential` kommando i ett  `Get-CimInstance` kommando.</span><span class="sxs-lookup"><span data-stu-id="f09dd-127">This command shows how to include a `Get-Credential` command in a  `Get-CimInstance` command.</span></span>

<span data-ttu-id="f09dd-128">Det här kommandot använder `Get-CimInstance` cmdleten för att hämta information om BIOS på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="f09dd-128">This command uses the `Get-CimInstance` cmdlet to get information about the BIOS on the Server01 computer.</span></span> <span data-ttu-id="f09dd-129">Den använder parametern **Credential** för att autentisera användaren, Domain01\User01 och ett `Get-Credential` kommando som värde för parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="f09dd-129">It uses the **Credential** parameter to authenticate the user, Domain01\User01, and a `Get-Credential` command as the value of the **Credential** parameter.</span></span>

### <span data-ttu-id="f09dd-130">Exempel 4</span><span class="sxs-lookup"><span data-stu-id="f09dd-130">Example 4</span></span>

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

<span data-ttu-id="f09dd-131">I det här exemplet skapas en autentiseringsuppgift som innehåller ett användar namn utan ett domän namn.</span><span class="sxs-lookup"><span data-stu-id="f09dd-131">This example creates a credential that includes a user name without a domain name.</span></span>

<span data-ttu-id="f09dd-132">Det första kommandot hämtar en autentiseringsuppgift med användar namnet user01 och lagrar det i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f09dd-132">The first command gets a credential with the user name User01 and stores it in the `$c` variable.</span></span>
<span data-ttu-id="f09dd-133">Det andra kommandot visar värdet för egenskapen **username** för objektet som resulterande autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="f09dd-133">The second command displays the value of the **Username** property of the resulting credential object.</span></span>

### <span data-ttu-id="f09dd-134">Exempel 5</span><span class="sxs-lookup"><span data-stu-id="f09dd-134">Example 5</span></span>

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

<span data-ttu-id="f09dd-135">Det här kommandot använder **PromptForCredential** -metoden för att uppmana användaren att ange användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="f09dd-135">This command uses the **PromptForCredential** method to prompt the user for their user name and password.</span></span> <span data-ttu-id="f09dd-136">Kommandot sparar de resulterande autentiseringsuppgifterna i `$Credential` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f09dd-136">The command saves the resulting credentials in the `$Credential` variable.</span></span>

<span data-ttu-id="f09dd-137">Metoden **PromptForCredential** är ett alternativ till att använda `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f09dd-137">The **PromptForCredential** method is an alternative to using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="f09dd-138">När du använder **PromptForCredential** kan du ange rubriken, meddelandena och användar namnet som visas i prompten.</span><span class="sxs-lookup"><span data-stu-id="f09dd-138">When you use **PromptForCredential** , you can specify the caption, messages, and user name that appear in the prompt.</span></span>

<span data-ttu-id="f09dd-139">Mer information finns i dokumentationen för [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) i SDK.</span><span class="sxs-lookup"><span data-stu-id="f09dd-139">For more information, see the [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) documentation in the SDK.</span></span>

### <span data-ttu-id="f09dd-140">Exempel 6</span><span class="sxs-lookup"><span data-stu-id="f09dd-140">Example 6</span></span>

<span data-ttu-id="f09dd-141">Det här exemplet visar hur du skapar ett Credential-objekt som är identiskt med det objekt som `Get-Credential` returneras utan att användaren tillkommer.</span><span class="sxs-lookup"><span data-stu-id="f09dd-141">This example shows how to create a credential object that is identical to the object that `Get-Credential` returns without prompting the user.</span></span> <span data-ttu-id="f09dd-142">Den här metoden kräver ett lösen ord för oformaterad text, vilket kan strida mot säkerhets standarder i vissa företag.</span><span class="sxs-lookup"><span data-stu-id="f09dd-142">This method requires a plain text password, which might violate the security standards in some enterprises.</span></span>

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

<span data-ttu-id="f09dd-143">Det första kommandot sparar användar konto namnet i `$User` parametern.</span><span class="sxs-lookup"><span data-stu-id="f09dd-143">The first command saves the user account name in the `$User` parameter.</span></span> <span data-ttu-id="f09dd-144">Värdet måste ha formatet "domän \ användare" eller "ComputerName\User".</span><span class="sxs-lookup"><span data-stu-id="f09dd-144">The value must have the "Domain\User" or "ComputerName\User" format.</span></span>

<span data-ttu-id="f09dd-145">Det andra kommandot använder `ConvertTo-SecureString` cmdleten för att skapa en säker sträng från ett lösen ord med oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="f09dd-145">The second command uses the `ConvertTo-SecureString` cmdlet to create a secure string from a plain text password.</span></span> <span data-ttu-id="f09dd-146">Kommandot använder parametern **Disklar** text för att ange att strängen är oformaterad text och **Force** -parametern för att bekräfta att du förstår riskerna med att använda oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="f09dd-146">The command uses the **AsPlainText** parameter to indicate that the string is plain text and the **Force** parameter to confirm that you understand the risks of using plain text.</span></span>

<span data-ttu-id="f09dd-147">Det tredje kommandot använder `New-Object` cmdleten för att skapa ett **PSCredential** -objekt från värdena i `$User` `$PWord` variablerna och.</span><span class="sxs-lookup"><span data-stu-id="f09dd-147">The third command uses the `New-Object` cmdlet to create a **PSCredential** object from the values in the `$User` and `$PWord` variables.</span></span>

### <span data-ttu-id="f09dd-148">Exempel 7</span><span class="sxs-lookup"><span data-stu-id="f09dd-148">Example 7</span></span>

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

<span data-ttu-id="f09dd-149">Det här kommandot använder cmdlet: en **meddelande** och **användar namn** `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="f09dd-149">This command uses the **Message** and **UserName** parameters of the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="f09dd-150">Det här kommando formatet är utformat för delade skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="f09dd-150">This command format is designed for shared scripts and functions.</span></span> <span data-ttu-id="f09dd-151">I det här fallet visar meddelandet användaren varför autentiseringsuppgifter krävs och ger dem förtroende för att begäran är giltig.</span><span class="sxs-lookup"><span data-stu-id="f09dd-151">In this case, the message tells the user why credentials are needed and gives them confidence that the request is legitimate.</span></span>

### <span data-ttu-id="f09dd-152">Exempel 8</span><span class="sxs-lookup"><span data-stu-id="f09dd-152">Example 8</span></span>

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

<span data-ttu-id="f09dd-153">Det här kommandot hämtar autentiseringsuppgifter från fjärrdatorn Server01.</span><span class="sxs-lookup"><span data-stu-id="f09dd-153">This command gets a credential from the Server01 remote computer.</span></span> <span data-ttu-id="f09dd-154">Kommandot använder `Invoke-Command` cmdleten för att köra ett `Get-Credential` kommando på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="f09dd-154">The command uses the `Invoke-Command` cmdlet to run a `Get-Credential` command on the remote computer.</span></span> <span data-ttu-id="f09dd-155">Utdata visar det fjärranslutna säkerhets meddelande som `Get-Credential` ingår i verifierings frågan.</span><span class="sxs-lookup"><span data-stu-id="f09dd-155">The output shows the remote security message that `Get-Credential` includes in the authentication prompt.</span></span>

## <span data-ttu-id="f09dd-156">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f09dd-156">PARAMETERS</span></span>

### <span data-ttu-id="f09dd-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="f09dd-157">-Credential</span></span>

<span data-ttu-id="f09dd-158">Anger ett användar namn för autentiseringsuppgiften, till exempel **user01** eller **Domain01\User01**.</span><span class="sxs-lookup"><span data-stu-id="f09dd-158">Specifies a user name for the credential, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="f09dd-159">Parameter namnet, `-Credential` , är valfritt.</span><span class="sxs-lookup"><span data-stu-id="f09dd-159">The parameter name, `-Credential`, is optional.</span></span>

<span data-ttu-id="f09dd-160">När du skickar kommandot och anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="f09dd-160">When you submit the command and specify a user name, you're prompted for a password.</span></span> <span data-ttu-id="f09dd-161">Om du utelämnar den här parametern uppmanas du att ange ett användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="f09dd-161">If you omit this parameter, you're prompted for a user name and a password.</span></span>

<span data-ttu-id="f09dd-162">Från och med PowerShell 3,0, om du anger ett användar namn utan en domän, `Get-Credential` infogar inte längre ett omvänt snedstreck före namnet.</span><span class="sxs-lookup"><span data-stu-id="f09dd-162">Starting in PowerShell 3.0, if you enter a user name without a domain, `Get-Credential` no longer inserts a backslash before the name.</span></span>

<span data-ttu-id="f09dd-163">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="f09dd-163">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="f09dd-164">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="f09dd-164">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="f09dd-165">– Meddelande</span><span class="sxs-lookup"><span data-stu-id="f09dd-165">-Message</span></span>

<span data-ttu-id="f09dd-166">Anger ett meddelande som visas i autentiserings-prompten.</span><span class="sxs-lookup"><span data-stu-id="f09dd-166">Specifies a message that appears in the authentication prompt.</span></span> <span data-ttu-id="f09dd-167">Den här parametern är avsedd att användas i en funktion eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="f09dd-167">This parameter is designed for use in a function or script.</span></span> <span data-ttu-id="f09dd-168">Du kan använda meddelandet för att förklara för användaren varför du begär autentiseringsuppgifter och hur de ska användas.</span><span class="sxs-lookup"><span data-stu-id="f09dd-168">You can use the message to explain to the user why you are requesting credentials and how they will be used.</span></span>

<span data-ttu-id="f09dd-169">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f09dd-169">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f09dd-170">– Rubrik</span><span class="sxs-lookup"><span data-stu-id="f09dd-170">-Title</span></span>

<span data-ttu-id="f09dd-171">Anger texten på rubrik raden för autentiserings-prompten i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="f09dd-171">Sets the text of the title line for the authentication prompt in the console.</span></span>

<span data-ttu-id="f09dd-172">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="f09dd-172">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="f09dd-173">-UserName</span><span class="sxs-lookup"><span data-stu-id="f09dd-173">-UserName</span></span>

<span data-ttu-id="f09dd-174">Anger ett användar namn.</span><span class="sxs-lookup"><span data-stu-id="f09dd-174">Specifies a user name.</span></span> <span data-ttu-id="f09dd-175">Autentiserings-prompten begär ett lösen ord för användar namnet.</span><span class="sxs-lookup"><span data-stu-id="f09dd-175">The authentication prompt requests a password for the user name.</span></span> <span data-ttu-id="f09dd-176">Som standard är användar namnet tomt och autentiserings-prompten begär både ett användar namn och ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="f09dd-176">By default, the user name is blank and the authentication prompt requests both a user name and password.</span></span>

<span data-ttu-id="f09dd-177">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f09dd-177">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f09dd-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f09dd-178">CommonParameters</span></span>

<span data-ttu-id="f09dd-179">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f09dd-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f09dd-180">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f09dd-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f09dd-181">INDATA</span><span class="sxs-lookup"><span data-stu-id="f09dd-181">INPUTS</span></span>

### <span data-ttu-id="f09dd-182">Inget</span><span class="sxs-lookup"><span data-stu-id="f09dd-182">None</span></span>

<span data-ttu-id="f09dd-183">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f09dd-183">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f09dd-184">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f09dd-184">OUTPUTS</span></span>

### <span data-ttu-id="f09dd-185">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="f09dd-185">System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="f09dd-186">`Get-Credential` Returnerar ett Credential-objekt.</span><span class="sxs-lookup"><span data-stu-id="f09dd-186">`Get-Credential` returns a credential object.</span></span>

## <span data-ttu-id="f09dd-187">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f09dd-187">NOTES</span></span>

<span data-ttu-id="f09dd-188">Du kan använda **PSCredential** -objektet som `Get-Credential` skapar i-cmdletar som begär användarautentisering, till exempel de med en **Credential** -parameter.</span><span class="sxs-lookup"><span data-stu-id="f09dd-188">You can use the **PSCredential** object that `Get-Credential` creates in cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span>

<span data-ttu-id="f09dd-189">Parametern **Credential** stöds inte av alla providers som är installerade med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f09dd-189">The **Credential** parameter is not supported by all providers that are installed with PowerShell.</span></span>
<span data-ttu-id="f09dd-190">Från och med PowerShell 3,0 stöds det på utvalda cmdlets, till exempel `Get-Content` `New-PSDrive` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="f09dd-190">Beginning in PowerShell 3.0, it is supported on select cmdlets, such as the `Get-Content` and `New-PSDrive` cmdlets.</span></span>

## <span data-ttu-id="f09dd-191">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f09dd-191">RELATED LINKS</span></span>

[<span data-ttu-id="f09dd-192">PromptForCredential</span><span class="sxs-lookup"><span data-stu-id="f09dd-192">PromptForCredential</span></span>](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
