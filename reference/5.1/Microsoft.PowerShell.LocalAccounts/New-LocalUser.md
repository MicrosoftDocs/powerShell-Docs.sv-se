---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalUser
ms.openlocfilehash: d83f3ad12481df0849ff2fe3f61d553a9ffdcdde
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265569"
---
# <span data-ttu-id="91268-103">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="91268-103">New-LocalUser</span></span>

## <span data-ttu-id="91268-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="91268-104">SYNOPSIS</span></span>

<span data-ttu-id="91268-105">Skapar ett lokalt användar konto.</span><span class="sxs-lookup"><span data-stu-id="91268-105">Creates a local user account.</span></span>

## <span data-ttu-id="91268-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="91268-106">SYNTAX</span></span>

### <span data-ttu-id="91268-107">Lösen ord (standard)</span><span class="sxs-lookup"><span data-stu-id="91268-107">Password (Default)</span></span>

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> -Password <SecureString> [-PasswordNeverExpires]
 [-UserMayNotChangePassword] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="91268-108">NOPassword</span><span class="sxs-lookup"><span data-stu-id="91268-108">NoPassword</span></span>

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> [-NoPassword] [-UserMayNotChangePassword] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="91268-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="91268-109">DESCRIPTION</span></span>

<span data-ttu-id="91268-110">`New-LocalUser`Cmdleten skapar ett lokalt användar konto.</span><span class="sxs-lookup"><span data-stu-id="91268-110">The `New-LocalUser` cmdlet creates a local user account.</span></span> <span data-ttu-id="91268-111">Denna cmdlet skapar ett lokalt användar konto eller ett lokalt användar konto som är anslutet till en Microsoft-konto.</span><span class="sxs-lookup"><span data-stu-id="91268-111">This cmdlet creates a local user account or a local user account that is connected to a Microsoft account.</span></span>

> [!NOTE]
> <span data-ttu-id="91268-112">Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.</span><span class="sxs-lookup"><span data-stu-id="91268-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="91268-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="91268-113">EXAMPLES</span></span>

### <span data-ttu-id="91268-114">Exempel 1: skapa ett användar konto</span><span class="sxs-lookup"><span data-stu-id="91268-114">Example 1: Create a user account</span></span>

```
PS C:\> New-LocalUser -Name "User02" -Description "Description of this account." -NoPassword
Name    Enabled  Description
----    -------  -----------
User02  True     Description of this account.
```

<span data-ttu-id="91268-115">Det här kommandot skapar ett lokalt användar konto och anger inte parametrarna **AccountExpires** eller **Password** .</span><span class="sxs-lookup"><span data-stu-id="91268-115">This command creates a local user account and does not specify the **AccountExpires** or **Password** parameters.</span></span> <span data-ttu-id="91268-116">Det innebär att kontot inte upphör att gälla eller har ett lösen ord som standard.</span><span class="sxs-lookup"><span data-stu-id="91268-116">Therefore, the account doesn't expire or have a password by default.</span></span>

### <span data-ttu-id="91268-117">Exempel 2: skapa ett användar konto som har ett lösen ord</span><span class="sxs-lookup"><span data-stu-id="91268-117">Example 2: Create a user account that has a password</span></span>

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> New-LocalUser "User03" -Password $Password -FullName "Third User" -Description "Description of this account."
Name    Enabled  Description
----    -------  -----------
User03  True     Description of this account.
```

<span data-ttu-id="91268-118">I det första kommandot uppmanas du att ange ett lösen ord med hjälp av `Read-Host` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="91268-118">The first command prompts you for a password by using the `Read-Host` cmdlet.</span></span> <span data-ttu-id="91268-119">Kommandot lagrar lösen ordet som en säker sträng i `$Password` variabeln.</span><span class="sxs-lookup"><span data-stu-id="91268-119">The command stores the password as a secure string in the `$Password` variable.</span></span>

<span data-ttu-id="91268-120">Det andra kommandot skapar ett lokalt användar konto med hjälp av det lösen ord som lagras i `$Password` .</span><span class="sxs-lookup"><span data-stu-id="91268-120">The second command creates a local user account by using the password stored in `$Password`.</span></span> <span data-ttu-id="91268-121">Kommandot anger ett användar namn, ett fullständigt namn och en beskrivning för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="91268-121">The command specifies a user name, full name, and description for the user account.</span></span>

## <span data-ttu-id="91268-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="91268-122">PARAMETERS</span></span>

### <span data-ttu-id="91268-123">-AccountExpires</span><span class="sxs-lookup"><span data-stu-id="91268-123">-AccountExpires</span></span>

<span data-ttu-id="91268-124">Anger när användar kontot upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="91268-124">Specifies when the user account expires.</span></span> <span data-ttu-id="91268-125">Använd cmdleten för att hämta ett **datetime** -objekt `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="91268-125">To obtain a **DateTime** object, use the `Get-Date` cmdlet.</span></span>
<span data-ttu-id="91268-126">Om du inte anger den här parametern upphör inte kontot att gälla.</span><span class="sxs-lookup"><span data-stu-id="91268-126">If you do not specify this parameter, the account does not expire.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="91268-127">-AccountNeverExpires</span><span class="sxs-lookup"><span data-stu-id="91268-127">-AccountNeverExpires</span></span>

<span data-ttu-id="91268-128">Anger att kontot inte upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="91268-128">Indicates that the account does not expire.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="91268-129">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="91268-129">-Description</span></span>

<span data-ttu-id="91268-130">Anger en kommentar för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="91268-130">Specifies a comment for the user account.</span></span>
<span data-ttu-id="91268-131">Den maximala längden är 48 tecken.</span><span class="sxs-lookup"><span data-stu-id="91268-131">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="91268-132">-Inaktive rad</span><span class="sxs-lookup"><span data-stu-id="91268-132">-Disabled</span></span>

<span data-ttu-id="91268-133">Anger att den här cmdleten skapar användar kontot som inaktiverat.</span><span class="sxs-lookup"><span data-stu-id="91268-133">Indicates that this cmdlet creates the user account as disabled.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="91268-134">-FullName</span><span class="sxs-lookup"><span data-stu-id="91268-134">-FullName</span></span>

<span data-ttu-id="91268-135">Anger det fullständiga namnet på användar kontot.</span><span class="sxs-lookup"><span data-stu-id="91268-135">Specifies the full name for the user account.</span></span> <span data-ttu-id="91268-136">Det fullständiga namnet skiljer sig från användar kontots användar namn.</span><span class="sxs-lookup"><span data-stu-id="91268-136">The full name differs from the user name of the user account.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="91268-137">-Name</span><span class="sxs-lookup"><span data-stu-id="91268-137">-Name</span></span>

<span data-ttu-id="91268-138">Anger användar namnet för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="91268-138">Specifies the user name for the user account.</span></span>

<span data-ttu-id="91268-139">Om du skapar ett lokalt användar konto för det lokala systemet kan användar namnet innehålla upp till 20 versaler eller gemener.</span><span class="sxs-lookup"><span data-stu-id="91268-139">If you create a local user account for the local system, the user name can contain up to 20 uppercase characters or lowercase characters.</span></span> <span data-ttu-id="91268-140">Ett användar namn får inte innehålla följande tecken:</span><span class="sxs-lookup"><span data-stu-id="91268-140">A user name cannot contain the following characters:</span></span>

<span data-ttu-id="91268-141">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span><span class="sxs-lookup"><span data-stu-id="91268-141">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span></span>

<span data-ttu-id="91268-142">Ett användar namn får inte bestå av bara punkter `.` eller blank steg.</span><span class="sxs-lookup"><span data-stu-id="91268-142">A user name cannot consist only of periods `.` or spaces.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="91268-143">-NOPassword</span><span class="sxs-lookup"><span data-stu-id="91268-143">-NoPassword</span></span>

<span data-ttu-id="91268-144">Anger att användar kontot saknar lösen ord.</span><span class="sxs-lookup"><span data-stu-id="91268-144">Indicates that the user account does not have a password.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoPassword
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="91268-145">-Password</span><span class="sxs-lookup"><span data-stu-id="91268-145">-Password</span></span>

<span data-ttu-id="91268-146">Anger ett lösen ord för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="91268-146">Specifies a password for the user account.</span></span> <span data-ttu-id="91268-147">Du kan använda `Read-Host -GetCredential` , `Get-Credential` eller `ConvertTo-SecureString` för att skapa ett **SecureString** -objekt för lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="91268-147">You can use `Read-Host -GetCredential`, `Get-Credential`, or `ConvertTo-SecureString` to create a **SecureString** object for the password.</span></span>

<span data-ttu-id="91268-148">Om du utelämnar parametrarna för **lösen ord** och **NOPassword** , `New-LocalUser` uppmanas du att ange lösen ordet för den nya användaren.</span><span class="sxs-lookup"><span data-stu-id="91268-148">If you omit the **Password** and **NoPassword** parameters, `New-LocalUser` prompts you for the new user's password.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: Password
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="91268-149">-PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="91268-149">-PasswordNeverExpires</span></span>

<span data-ttu-id="91268-150">Anger om lösen ordet upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="91268-150">Indicates whether the password expires.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Password
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="91268-151">-UserMayNotChangePassword</span><span class="sxs-lookup"><span data-stu-id="91268-151">-UserMayNotChangePassword</span></span>

<span data-ttu-id="91268-152">Anger att användaren inte kan ändra lösen ordet för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="91268-152">Indicates that the user cannot change the password on the user account.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="91268-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="91268-153">-Confirm</span></span>

<span data-ttu-id="91268-154">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="91268-154">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91268-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="91268-155">-WhatIf</span></span>

<span data-ttu-id="91268-156">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="91268-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="91268-157">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="91268-157">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91268-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="91268-158">CommonParameters</span></span>

<span data-ttu-id="91268-159">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="91268-159">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="91268-160">Mer information finns i [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="91268-160">For more information, see [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="91268-161">INDATA</span><span class="sxs-lookup"><span data-stu-id="91268-161">INPUTS</span></span>

### <span data-ttu-id="91268-162">System. String, system. DateTime, system. Boolean, system. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="91268-162">System.String, System.DateTime, System.Boolean, System.Security.SecureString</span></span>

<span data-ttu-id="91268-163">Du kan skicka en sträng, ett **datetime** -objekt, ett booleskt värde eller en säker sträng till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91268-163">You can pipe a string, a **DateTime** object, a boolean value, or a secure string to this cmdlet.</span></span>

## <span data-ttu-id="91268-164">UTDATA</span><span class="sxs-lookup"><span data-stu-id="91268-164">OUTPUTS</span></span>

### <span data-ttu-id="91268-165">System. Management. Automation. SecurityAccountsManager. lokal användare</span><span class="sxs-lookup"><span data-stu-id="91268-165">System.Management.Automation.SecurityAccountsManager.LocalUser</span></span>

<span data-ttu-id="91268-166">Denna cmdlet returnerar ett **lokal användare** -objekt.</span><span class="sxs-lookup"><span data-stu-id="91268-166">This cmdlet returns a **LocalUser** object.</span></span>
<span data-ttu-id="91268-167">Det här objektet innehåller information om användar kontot.</span><span class="sxs-lookup"><span data-stu-id="91268-167">This object provides information about the user account.</span></span>

## <span data-ttu-id="91268-168">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="91268-168">NOTES</span></span>

- <span data-ttu-id="91268-169">Ett användar namn får inte vara identiskt med andra användar namn eller grupp namn på datorn.</span><span class="sxs-lookup"><span data-stu-id="91268-169">A user name cannot be identical to any other user name or group name on the computer.</span></span> <span data-ttu-id="91268-170">Ett användar namn får inte bestå av bara punkter `.` eller blank steg.</span><span class="sxs-lookup"><span data-stu-id="91268-170">A user name cannot consist only of periods `.` or spaces.</span></span> <span data-ttu-id="91268-171">Ett användar namn kan innehålla upp till 20 versaler eller gemener.</span><span class="sxs-lookup"><span data-stu-id="91268-171">A user name can contain up to 20 uppercase characters or lowercase characters.</span></span> <span data-ttu-id="91268-172">Ett användar namn får inte innehålla följande tecken:</span><span class="sxs-lookup"><span data-stu-id="91268-172">A user name cannot contain the following characters:</span></span>

<span data-ttu-id="91268-173">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span><span class="sxs-lookup"><span data-stu-id="91268-173">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span></span>

- <span data-ttu-id="91268-174">Ett lösen ord kan innehålla upp till 127 tecken.</span><span class="sxs-lookup"><span data-stu-id="91268-174">A password can contain up to 127 characters.</span></span>
- <span data-ttu-id="91268-175">Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa.</span><span class="sxs-lookup"><span data-stu-id="91268-175">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="91268-176">De möjliga källorna är följande:</span><span class="sxs-lookup"><span data-stu-id="91268-176">The possible sources are as follows:</span></span>

  - <span data-ttu-id="91268-177">Lokal</span><span class="sxs-lookup"><span data-stu-id="91268-177">Local</span></span>
  - <span data-ttu-id="91268-178">Active Directory</span><span class="sxs-lookup"><span data-stu-id="91268-178">Active Directory</span></span>
  - <span data-ttu-id="91268-179">Azure Active Directory grupp</span><span class="sxs-lookup"><span data-stu-id="91268-179">Azure Active Directory group</span></span>
  - <span data-ttu-id="91268-180">Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="91268-180">Microsoft Account</span></span>

> [!NOTE]
> <span data-ttu-id="91268-181">**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="91268-181">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="91268-182">För tidigare versioner är egenskapen tom.</span><span class="sxs-lookup"><span data-stu-id="91268-182">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="91268-183">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="91268-183">RELATED LINKS</span></span>

[<span data-ttu-id="91268-184">Disable-lokal användare</span><span class="sxs-lookup"><span data-stu-id="91268-184">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="91268-185">Aktivera – lokal användare</span><span class="sxs-lookup"><span data-stu-id="91268-185">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="91268-186">Get-lokal användare</span><span class="sxs-lookup"><span data-stu-id="91268-186">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="91268-187">Remove-lokal användare</span><span class="sxs-lookup"><span data-stu-id="91268-187">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="91268-188">Byt namn – lokal användare</span><span class="sxs-lookup"><span data-stu-id="91268-188">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="91268-189">Set-lokal användare</span><span class="sxs-lookup"><span data-stu-id="91268-189">Set-LocalUser</span></span>](Set-LocalUser.md)
