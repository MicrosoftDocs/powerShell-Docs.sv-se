---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/set-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LocalUser
ms.openlocfilehash: a6352611b757dae828a2efef07f9ce65abaa5e2e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266271"
---
# <span data-ttu-id="851d0-103">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="851d0-103">Set-LocalUser</span></span>

## <span data-ttu-id="851d0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="851d0-104">SYNOPSIS</span></span>
<span data-ttu-id="851d0-105">Ändrar ett lokalt användar konto.</span><span class="sxs-lookup"><span data-stu-id="851d0-105">Modifies a local user account.</span></span>

## <span data-ttu-id="851d0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="851d0-106">SYNTAX</span></span>

### <span data-ttu-id="851d0-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="851d0-107">Name (Default)</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Name] <String> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="851d0-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="851d0-108">InputObject</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-InputObject] <LocalUser> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="851d0-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="851d0-109">SecurityIdentifier</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Password <SecureString>] [-PasswordNeverExpires <Boolean>] [-SID] <SecurityIdentifier>
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="851d0-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="851d0-110">DESCRIPTION</span></span>
<span data-ttu-id="851d0-111">Cmdlet: en **set-lokal användare** ändrar ett lokalt användar konto.</span><span class="sxs-lookup"><span data-stu-id="851d0-111">The **Set-LocalUser** cmdlet modifies a local user account.</span></span>
<span data-ttu-id="851d0-112">Denna cmdlet kan återställa lösen ordet för ett lokalt användar konto.</span><span class="sxs-lookup"><span data-stu-id="851d0-112">This cmdlet can reset the password of a local user account.</span></span>

> [!NOTE]
> <span data-ttu-id="851d0-113">Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.</span><span class="sxs-lookup"><span data-stu-id="851d0-113">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="851d0-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="851d0-114">EXAMPLES</span></span>

### <span data-ttu-id="851d0-115">Exempel 1: ändra en beskrivning av ett användar konto</span><span class="sxs-lookup"><span data-stu-id="851d0-115">Example 1: Change a description of a user account</span></span>

```
PS C:\> Set-LocalUser -Name "Admin07" -Description "Description of this account."
```

<span data-ttu-id="851d0-116">Det här kommandot ändrar beskrivningen av ett användar konto med namnet Admin07.</span><span class="sxs-lookup"><span data-stu-id="851d0-116">This command changes the description of a user account named Admin07.</span></span>

### <span data-ttu-id="851d0-117">Exempel 2: ändra lösen ordet för ett konto</span><span class="sxs-lookup"><span data-stu-id="851d0-117">Example 2: Change the password on an account</span></span>

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> $UserAccount = Get-LocalUser -Name "User02"
PS C:\> $UserAccount | Set-LocalUser -Password $Password
```

<span data-ttu-id="851d0-118">I det första kommandot uppmanas du att ange ett lösen ord med hjälp av Read-Host-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="851d0-118">The first command prompts you for a password by using the Read-Host cmdlet.</span></span>
<span data-ttu-id="851d0-119">Kommandot lagrar lösen ordet som en säker sträng i variabeln $Password.</span><span class="sxs-lookup"><span data-stu-id="851d0-119">The command stores the password as a secure string in the $Password variable.</span></span>

<span data-ttu-id="851d0-120">Det andra kommandot hämtar ett användar konto med namnet User02 med hjälp av **Get-lokal användare**.</span><span class="sxs-lookup"><span data-stu-id="851d0-120">The second command gets a user account named User02 by using **Get-LocalUser**.</span></span>
<span data-ttu-id="851d0-121">Kommandot lagrar kontot i variabeln $UserAccount.</span><span class="sxs-lookup"><span data-stu-id="851d0-121">The command stores the account in the $UserAccount variable.</span></span>

<span data-ttu-id="851d0-122">Det tredje kommandot anger det nya lösen ordet för det användar konto som lagras i $UserAccount.</span><span class="sxs-lookup"><span data-stu-id="851d0-122">The third command sets the new password on the user account stored in $UserAccount.</span></span>

## <span data-ttu-id="851d0-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="851d0-123">PARAMETERS</span></span>

### <span data-ttu-id="851d0-124">-AccountExpires</span><span class="sxs-lookup"><span data-stu-id="851d0-124">-AccountExpires</span></span>
<span data-ttu-id="851d0-125">Anger när användar kontot upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="851d0-125">Specifies when the user account expires.</span></span>
<span data-ttu-id="851d0-126">Använd Get-Date-cmdleten för att hämta ett **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="851d0-126">To obtain a **DateTime** object, use the Get-Date cmdlet.</span></span>

<span data-ttu-id="851d0-127">Om du inte vill att kontot ska upphöra att gälla anger du parametern *AccountNeverExpires* .</span><span class="sxs-lookup"><span data-stu-id="851d0-127">If you do not want the account to expire, specify the *AccountNeverExpires* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="851d0-128">-AccountNeverExpires</span><span class="sxs-lookup"><span data-stu-id="851d0-128">-AccountNeverExpires</span></span>
<span data-ttu-id="851d0-129">Anger att kontot inte upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="851d0-129">Indicates that the account does not expire.</span></span>

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

### <span data-ttu-id="851d0-130">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="851d0-130">-Description</span></span>
<span data-ttu-id="851d0-131">Anger en kommentar för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="851d0-131">Specifies a comment for the user account.</span></span>
<span data-ttu-id="851d0-132">Den maximala längden är 48 tecken.</span><span class="sxs-lookup"><span data-stu-id="851d0-132">The maximum length is 48 characters.</span></span>

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

### <span data-ttu-id="851d0-133">-FullName</span><span class="sxs-lookup"><span data-stu-id="851d0-133">-FullName</span></span>
<span data-ttu-id="851d0-134">Anger det fullständiga namnet på användar kontot.</span><span class="sxs-lookup"><span data-stu-id="851d0-134">Specifies the full name for the user account.</span></span>
<span data-ttu-id="851d0-135">Det fullständiga namnet skiljer sig från användar kontots användar namn.</span><span class="sxs-lookup"><span data-stu-id="851d0-135">The full name differs from the user name of the user account.</span></span>

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

### <span data-ttu-id="851d0-136">– InputObject</span><span class="sxs-lookup"><span data-stu-id="851d0-136">-InputObject</span></span>
<span data-ttu-id="851d0-137">Anger det användar konto som denna cmdlet ändrar.</span><span class="sxs-lookup"><span data-stu-id="851d0-137">Specifies the user account that this cmdlet changes.</span></span>
<span data-ttu-id="851d0-138">Använd Get-LocalUser-cmdleten om du vill skaffa ett användar konto.</span><span class="sxs-lookup"><span data-stu-id="851d0-138">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="851d0-139">-Name</span><span class="sxs-lookup"><span data-stu-id="851d0-139">-Name</span></span>
<span data-ttu-id="851d0-140">Anger namnet på det användar konto som denna cmdlet ändrar.</span><span class="sxs-lookup"><span data-stu-id="851d0-140">Specifies the name of the user account that this cmdlet changes.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="851d0-141">-Password</span><span class="sxs-lookup"><span data-stu-id="851d0-141">-Password</span></span>
<span data-ttu-id="851d0-142">Anger ett lösen ord för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="851d0-142">Specifies a password for the user account.</span></span>
<span data-ttu-id="851d0-143">Ange inget lösen ord om användar kontot är anslutet till ett Microsoft-konto.</span><span class="sxs-lookup"><span data-stu-id="851d0-143">If the user account is connected to a Microsoft account, do not set a password.</span></span>

<span data-ttu-id="851d0-144">Du kan använda `Read-Host -GetCredential` , Hämta autentiseringsuppgifter eller ConvertTo-SecureString för att skapa ett **SecureString** -objekt för lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="851d0-144">You can use `Read-Host -GetCredential`, Get-Credential, or ConvertTo-SecureString to create a **SecureString** object for the password.</span></span>

<span data-ttu-id="851d0-145">Om du utelämnar parametrarna för *lösen ord* och *NOPassword* , uppmanas du att ange användarens lösen ord i **set-lokal användare** .</span><span class="sxs-lookup"><span data-stu-id="851d0-145">If you omit the *Password* and *NoPassword* parameters, **Set-LocalUser** prompts you for the user's password.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="851d0-146">-PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="851d0-146">-PasswordNeverExpires</span></span>
<span data-ttu-id="851d0-147">Anger om lösen ordet upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="851d0-147">Indicates whether the password expires.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="851d0-148">-SID</span><span class="sxs-lookup"><span data-stu-id="851d0-148">-SID</span></span>
<span data-ttu-id="851d0-149">Anger säkerhets-ID: t (SID) för det användar konto som denna cmdlet ändrar.</span><span class="sxs-lookup"><span data-stu-id="851d0-149">Specifies the security ID (SID) of the user account that this cmdlet changes.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="851d0-150">-UserMayChangePassword</span><span class="sxs-lookup"><span data-stu-id="851d0-150">-UserMayChangePassword</span></span>
<span data-ttu-id="851d0-151">Anger att användaren kan ändra lösen ordet för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="851d0-151">Indicates that the user can change the password on the user account.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="851d0-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="851d0-152">-Confirm</span></span>
<span data-ttu-id="851d0-153">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="851d0-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="851d0-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="851d0-154">-WhatIf</span></span>
<span data-ttu-id="851d0-155">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="851d0-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="851d0-156">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="851d0-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="851d0-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="851d0-157">CommonParameters</span></span>
<span data-ttu-id="851d0-158">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="851d0-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="851d0-159">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="851d0-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="851d0-160">INDATA</span><span class="sxs-lookup"><span data-stu-id="851d0-160">INPUTS</span></span>

### <span data-ttu-id="851d0-161">System. Management. Automation. SecurityAccountsManager. lokal användare, system. String, system. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="851d0-161">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="851d0-162">Du kan skicka vidare en lokal användare, en sträng eller ett SID till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="851d0-162">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="851d0-163">UTDATA</span><span class="sxs-lookup"><span data-stu-id="851d0-163">OUTPUTS</span></span>

### <span data-ttu-id="851d0-164">Inget</span><span class="sxs-lookup"><span data-stu-id="851d0-164">None</span></span>
<span data-ttu-id="851d0-165">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="851d0-165">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="851d0-166">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="851d0-166">NOTES</span></span>

* <span data-ttu-id="851d0-167">Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa.</span><span class="sxs-lookup"><span data-stu-id="851d0-167">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="851d0-168">De möjliga källorna är följande:</span><span class="sxs-lookup"><span data-stu-id="851d0-168">The possible sources are as follows:</span></span>

- <span data-ttu-id="851d0-169">Lokal</span><span class="sxs-lookup"><span data-stu-id="851d0-169">Local</span></span>
- <span data-ttu-id="851d0-170">Active Directory</span><span class="sxs-lookup"><span data-stu-id="851d0-170">Active Directory</span></span>
- <span data-ttu-id="851d0-171">Azure Active Directory grupp</span><span class="sxs-lookup"><span data-stu-id="851d0-171">Azure Active Directory group</span></span>
- <span data-ttu-id="851d0-172">Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="851d0-172">Microsoft Account</span></span>

<span data-ttu-id="851d0-173">**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="851d0-173">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="851d0-174">För tidigare versioner är egenskapen tom.</span><span class="sxs-lookup"><span data-stu-id="851d0-174">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="851d0-175">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="851d0-175">RELATED LINKS</span></span>

[<span data-ttu-id="851d0-176">Disable-lokal användare</span><span class="sxs-lookup"><span data-stu-id="851d0-176">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="851d0-177">Aktivera – lokal användare</span><span class="sxs-lookup"><span data-stu-id="851d0-177">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="851d0-178">Get-lokal användare</span><span class="sxs-lookup"><span data-stu-id="851d0-178">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="851d0-179">New-lokal användare</span><span class="sxs-lookup"><span data-stu-id="851d0-179">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="851d0-180">Remove-lokal användare</span><span class="sxs-lookup"><span data-stu-id="851d0-180">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="851d0-181">Byt namn – lokal användare</span><span class="sxs-lookup"><span data-stu-id="851d0-181">Rename-LocalUser</span></span>](Rename-LocalUser.md)
