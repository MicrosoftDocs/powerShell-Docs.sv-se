---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/enable-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-LocalUser
ms.openlocfilehash: 80d062578e7114b69e5cb5f3367b56da3871b9df
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263528"
---
# <span data-ttu-id="45363-103">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="45363-103">Enable-LocalUser</span></span>

## <span data-ttu-id="45363-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="45363-104">SYNOPSIS</span></span>
<span data-ttu-id="45363-105">Aktiverar ett lokalt användar konto.</span><span class="sxs-lookup"><span data-stu-id="45363-105">Enables a local user account.</span></span>

## <span data-ttu-id="45363-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="45363-106">SYNTAX</span></span>

### <span data-ttu-id="45363-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="45363-107">InputObject</span></span>

```
Enable-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="45363-108">Default</span><span class="sxs-lookup"><span data-stu-id="45363-108">Default</span></span>

```
Enable-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="45363-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="45363-109">SecurityIdentifier</span></span>

```
Enable-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="45363-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="45363-110">DESCRIPTION</span></span>
<span data-ttu-id="45363-111">Cmdlet **: en Enable-lokal användare** aktiverar lokala användar konton.</span><span class="sxs-lookup"><span data-stu-id="45363-111">The **Enable-LocalUser** cmdlet enables local user accounts.</span></span>
<span data-ttu-id="45363-112">När ett användar konto har inaktiverats kan användaren inte logga in.</span><span class="sxs-lookup"><span data-stu-id="45363-112">When a user account is disabled, the user cannot log on.</span></span>
<span data-ttu-id="45363-113">När ett användar konto är aktiverat kan användaren logga in.</span><span class="sxs-lookup"><span data-stu-id="45363-113">When a user account is enabled, the user can log on.</span></span>

> [!NOTE]
> <span data-ttu-id="45363-114">Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.</span><span class="sxs-lookup"><span data-stu-id="45363-114">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="45363-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="45363-115">EXAMPLES</span></span>

### <span data-ttu-id="45363-116">Exempel 1: aktivera ett konto genom att ange ett namn</span><span class="sxs-lookup"><span data-stu-id="45363-116">Example 1: Enable an account by specifying a name</span></span>

```
PS C:\> Enable-LocalUser -Name "Admin02"
```

<span data-ttu-id="45363-117">Det här kommandot aktiverar det användar konto som heter Admin02.</span><span class="sxs-lookup"><span data-stu-id="45363-117">This command enables the user account named Admin02.</span></span>

### <span data-ttu-id="45363-118">Exempel 2: aktivera ett konto med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="45363-118">Example 2: Enable an account by using the pipeline</span></span>

```
PS C:\> Get-LocalUser -Name "Administrator" | Enable-LocalUser
```

<span data-ttu-id="45363-119">Det här kommandot hämtar det inbyggda administratörs kontot med hjälp av **Get-lokal användare** och skickar det sedan till den aktuella cmdleten med hjälp av pipeline-operatorn.</span><span class="sxs-lookup"><span data-stu-id="45363-119">This command gets the built-in Administrator account by using **Get-LocalUser** , and then passes it to the current cmdlet by using the pipeline operator.</span></span>
<span data-ttu-id="45363-120">Denna cmdlet aktiverar det kontot.</span><span class="sxs-lookup"><span data-stu-id="45363-120">That cmdlet enables that account.</span></span>

## <span data-ttu-id="45363-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="45363-121">PARAMETERS</span></span>

### <span data-ttu-id="45363-122">– InputObject</span><span class="sxs-lookup"><span data-stu-id="45363-122">-InputObject</span></span>
<span data-ttu-id="45363-123">Anger en matris med användar konton som denna cmdlet aktiverar.</span><span class="sxs-lookup"><span data-stu-id="45363-123">Specifies an array of user accounts that this cmdlet enables.</span></span>
<span data-ttu-id="45363-124">Använd Get-LocalUser-cmdleten om du vill skaffa ett användar konto.</span><span class="sxs-lookup"><span data-stu-id="45363-124">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="45363-125">-Name</span><span class="sxs-lookup"><span data-stu-id="45363-125">-Name</span></span>
<span data-ttu-id="45363-126">Anger en matris med namn på de användar konton som denna cmdlet aktiverar.</span><span class="sxs-lookup"><span data-stu-id="45363-126">Specifies an array of names of the user accounts that this cmdlet enables.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="45363-127">-SID</span><span class="sxs-lookup"><span data-stu-id="45363-127">-SID</span></span>
<span data-ttu-id="45363-128">Anger en matris med användar konton som denna cmdlet aktiverar.</span><span class="sxs-lookup"><span data-stu-id="45363-128">Specifies an array of user accounts that this cmdlet enables.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="45363-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="45363-129">-Confirm</span></span>
<span data-ttu-id="45363-130">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="45363-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="45363-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="45363-131">-WhatIf</span></span>
<span data-ttu-id="45363-132">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="45363-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="45363-133">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="45363-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="45363-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="45363-134">CommonParameters</span></span>
<span data-ttu-id="45363-135">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="45363-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="45363-136">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="45363-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="45363-137">INDATA</span><span class="sxs-lookup"><span data-stu-id="45363-137">INPUTS</span></span>

### <span data-ttu-id="45363-138">System. Management. Automation. SecurityAccountsManager. lokal användare, system. String, system. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="45363-138">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="45363-139">Du kan skicka vidare en lokal användare, en sträng eller ett SID till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="45363-139">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="45363-140">UTDATA</span><span class="sxs-lookup"><span data-stu-id="45363-140">OUTPUTS</span></span>

### <span data-ttu-id="45363-141">Inget</span><span class="sxs-lookup"><span data-stu-id="45363-141">None</span></span>
<span data-ttu-id="45363-142">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="45363-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="45363-143">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="45363-143">NOTES</span></span>

* <span data-ttu-id="45363-144">Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa.</span><span class="sxs-lookup"><span data-stu-id="45363-144">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="45363-145">De möjliga källorna är följande:</span><span class="sxs-lookup"><span data-stu-id="45363-145">The possible sources are as follows:</span></span>

- <span data-ttu-id="45363-146">Lokal</span><span class="sxs-lookup"><span data-stu-id="45363-146">Local</span></span>
- <span data-ttu-id="45363-147">Active Directory</span><span class="sxs-lookup"><span data-stu-id="45363-147">Active Directory</span></span>
- <span data-ttu-id="45363-148">Azure Active Directory grupp</span><span class="sxs-lookup"><span data-stu-id="45363-148">Azure Active Directory group</span></span>
- <span data-ttu-id="45363-149">Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="45363-149">Microsoft Account</span></span>

<span data-ttu-id="45363-150">**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="45363-150">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="45363-151">För tidigare versioner är egenskapen tom.</span><span class="sxs-lookup"><span data-stu-id="45363-151">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="45363-152">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="45363-152">RELATED LINKS</span></span>

[<span data-ttu-id="45363-153">Disable-lokal användare</span><span class="sxs-lookup"><span data-stu-id="45363-153">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="45363-154">Get-lokal användare</span><span class="sxs-lookup"><span data-stu-id="45363-154">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="45363-155">New-lokal användare</span><span class="sxs-lookup"><span data-stu-id="45363-155">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="45363-156">Remove-lokal användare</span><span class="sxs-lookup"><span data-stu-id="45363-156">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="45363-157">Byt namn – lokal användare</span><span class="sxs-lookup"><span data-stu-id="45363-157">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="45363-158">Set-lokal användare</span><span class="sxs-lookup"><span data-stu-id="45363-158">Set-LocalUser</span></span>](Set-LocalUser.md)
