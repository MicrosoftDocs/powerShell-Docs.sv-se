---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalUser
ms.openlocfilehash: de1054971dab19f8cfae654208488ca9ce5e17e4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266288"
---
# <span data-ttu-id="7718e-103">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="7718e-103">Remove-LocalUser</span></span>

## <span data-ttu-id="7718e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7718e-104">SYNOPSIS</span></span>
<span data-ttu-id="7718e-105">Tar bort lokala användar konton.</span><span class="sxs-lookup"><span data-stu-id="7718e-105">Deletes local user accounts.</span></span>

## <span data-ttu-id="7718e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7718e-106">SYNTAX</span></span>

### <span data-ttu-id="7718e-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="7718e-107">InputObject</span></span>

```
Remove-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7718e-108">Default</span><span class="sxs-lookup"><span data-stu-id="7718e-108">Default</span></span>

```
Remove-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7718e-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="7718e-109">SecurityIdentifier</span></span>

```
Remove-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7718e-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7718e-110">DESCRIPTION</span></span>
<span data-ttu-id="7718e-111">Cmdlet: en **Remove-lokal användare** tar bort lokala användar konton.</span><span class="sxs-lookup"><span data-stu-id="7718e-111">The **Remove-LocalUser** cmdlet deletes local user accounts.</span></span>

## <span data-ttu-id="7718e-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7718e-112">EXAMPLES</span></span>

### <span data-ttu-id="7718e-113">Exempel 1: ta bort ett användar konto</span><span class="sxs-lookup"><span data-stu-id="7718e-113">Example 1: Delete a user account</span></span>

```
PS C:\> Remove-LocalUser -Name "AdminContoso02"
```

<span data-ttu-id="7718e-114">Det här kommandot tar bort användar kontot med namnet AdminContoso02.</span><span class="sxs-lookup"><span data-stu-id="7718e-114">This command deletes the user account named AdminContoso02.</span></span>

> [!NOTE]
> <span data-ttu-id="7718e-115">Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.</span><span class="sxs-lookup"><span data-stu-id="7718e-115">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="7718e-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7718e-116">PARAMETERS</span></span>

### <span data-ttu-id="7718e-117">– InputObject</span><span class="sxs-lookup"><span data-stu-id="7718e-117">-InputObject</span></span>
<span data-ttu-id="7718e-118">Anger en matris med användar konton som denna cmdlet tar bort.</span><span class="sxs-lookup"><span data-stu-id="7718e-118">Specifies an array of user accounts that this cmdlet deletes.</span></span>
<span data-ttu-id="7718e-119">Använd Get-LocalUser-cmdleten om du vill skaffa ett användar konto.</span><span class="sxs-lookup"><span data-stu-id="7718e-119">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

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

### <span data-ttu-id="7718e-120">-Name</span><span class="sxs-lookup"><span data-stu-id="7718e-120">-Name</span></span>
<span data-ttu-id="7718e-121">Anger en matris med namn på de användar konton som denna cmdlet tar bort.</span><span class="sxs-lookup"><span data-stu-id="7718e-121">Specifies an array of names of the user accounts that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="7718e-122">-SID</span><span class="sxs-lookup"><span data-stu-id="7718e-122">-SID</span></span>
<span data-ttu-id="7718e-123">Anger en matris med säkerhets-ID: n (sid) för de användar konton som denna cmdlet tar bort.</span><span class="sxs-lookup"><span data-stu-id="7718e-123">Specifies an array of security IDs (SIDs) of user accounts that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="7718e-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7718e-124">-Confirm</span></span>
<span data-ttu-id="7718e-125">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7718e-125">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7718e-126">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7718e-126">-WhatIf</span></span>
<span data-ttu-id="7718e-127">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="7718e-127">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7718e-128">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="7718e-128">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7718e-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7718e-129">CommonParameters</span></span>
<span data-ttu-id="7718e-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7718e-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7718e-131">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7718e-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7718e-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="7718e-132">INPUTS</span></span>

### <span data-ttu-id="7718e-133">System. Management. Automation. SecurityAccountsManager. lokal användare, system. String, system. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="7718e-133">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="7718e-134">Du kan skicka vidare en lokal användare, en sträng eller ett SID till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7718e-134">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="7718e-135">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7718e-135">OUTPUTS</span></span>

### <span data-ttu-id="7718e-136">Inget</span><span class="sxs-lookup"><span data-stu-id="7718e-136">None</span></span>
<span data-ttu-id="7718e-137">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="7718e-137">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7718e-138">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7718e-138">NOTES</span></span>

* <span data-ttu-id="7718e-139">Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa.</span><span class="sxs-lookup"><span data-stu-id="7718e-139">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="7718e-140">De möjliga källorna är följande:</span><span class="sxs-lookup"><span data-stu-id="7718e-140">The possible sources are as follows:</span></span>

- <span data-ttu-id="7718e-141">Lokal</span><span class="sxs-lookup"><span data-stu-id="7718e-141">Local</span></span>
- <span data-ttu-id="7718e-142">Active Directory</span><span class="sxs-lookup"><span data-stu-id="7718e-142">Active Directory</span></span>
- <span data-ttu-id="7718e-143">Azure Active Directory grupp</span><span class="sxs-lookup"><span data-stu-id="7718e-143">Azure Active Directory group</span></span>
- <span data-ttu-id="7718e-144">Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="7718e-144">Microsoft Account</span></span>

<span data-ttu-id="7718e-145">**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="7718e-145">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="7718e-146">För tidigare versioner är egenskapen tom.</span><span class="sxs-lookup"><span data-stu-id="7718e-146">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="7718e-147">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7718e-147">RELATED LINKS</span></span>

[<span data-ttu-id="7718e-148">Disable-lokal användare</span><span class="sxs-lookup"><span data-stu-id="7718e-148">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="7718e-149">Aktivera – lokal användare</span><span class="sxs-lookup"><span data-stu-id="7718e-149">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="7718e-150">Get-lokal användare</span><span class="sxs-lookup"><span data-stu-id="7718e-150">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="7718e-151">New-lokal användare</span><span class="sxs-lookup"><span data-stu-id="7718e-151">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="7718e-152">Byt namn – lokal användare</span><span class="sxs-lookup"><span data-stu-id="7718e-152">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="7718e-153">Set-lokal användare</span><span class="sxs-lookup"><span data-stu-id="7718e-153">Set-LocalUser</span></span>](Set-LocalUser.md)
