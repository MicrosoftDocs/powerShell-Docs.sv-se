---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/rename-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-LocalUser
ms.openlocfilehash: fc5740e52e08ad2146981799a4e1659cd420b321
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266283"
---
# <span data-ttu-id="3dbbc-103">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="3dbbc-103">Rename-LocalUser</span></span>

## <span data-ttu-id="3dbbc-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3dbbc-104">SYNOPSIS</span></span>
<span data-ttu-id="3dbbc-105">Byter namn på ett lokalt användar konto.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-105">Renames a local user account.</span></span>

## <span data-ttu-id="3dbbc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3dbbc-106">SYNTAX</span></span>

### <span data-ttu-id="3dbbc-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="3dbbc-107">InputObject</span></span>

```
Rename-LocalUser [-InputObject] <LocalUser> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3dbbc-108">Default</span><span class="sxs-lookup"><span data-stu-id="3dbbc-108">Default</span></span>

```
Rename-LocalUser [-Name] <String> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3dbbc-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="3dbbc-109">SecurityIdentifier</span></span>

```
Rename-LocalUser [-NewName] <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3dbbc-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3dbbc-110">DESCRIPTION</span></span>
<span data-ttu-id="3dbbc-111">Cmdleten **rename-lokal användare** byter namn på ett lokalt användar konto.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-111">The **Rename-LocalUser** cmdlet renames a local user account.</span></span>

> [!NOTE]
> <span data-ttu-id="3dbbc-112">Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="3dbbc-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3dbbc-113">EXAMPLES</span></span>

### <span data-ttu-id="3dbbc-114">Exempel 1: Byt namn på ett användar konto</span><span class="sxs-lookup"><span data-stu-id="3dbbc-114">Example 1: Rename a user account</span></span>

```
PS C:\> Rename-LocalUser -Name "Admin02" -NewName "AdminContoso02"
```

<span data-ttu-id="3dbbc-115">Det här kommandot byter namn på användar kontot med namnet Admin02.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-115">This command renames the user account named Admin02.</span></span>

## <span data-ttu-id="3dbbc-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3dbbc-116">PARAMETERS</span></span>

### <span data-ttu-id="3dbbc-117">– InputObject</span><span class="sxs-lookup"><span data-stu-id="3dbbc-117">-InputObject</span></span>
<span data-ttu-id="3dbbc-118">Anger det användar konto som den här cmdleten byter namn på.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-118">Specifies the user account that this cmdlet renames.</span></span>
<span data-ttu-id="3dbbc-119">Använd Get-LocalUser-cmdleten om du vill skaffa ett användar konto.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-119">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

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

### <span data-ttu-id="3dbbc-120">-Name</span><span class="sxs-lookup"><span data-stu-id="3dbbc-120">-Name</span></span>
<span data-ttu-id="3dbbc-121">Anger namnet på det användar konto som denna cmdlet byter namn på.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-121">Specifies the name of the user account that this cmdlet renames.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3dbbc-122">-Nyttnamn</span><span class="sxs-lookup"><span data-stu-id="3dbbc-122">-NewName</span></span>
<span data-ttu-id="3dbbc-123">Anger ett nytt namn för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-123">Specifies a new name for the user account.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3dbbc-124">-SID</span><span class="sxs-lookup"><span data-stu-id="3dbbc-124">-SID</span></span>
<span data-ttu-id="3dbbc-125">Anger säkerhets-ID: t (SID) för ett användar konto som denna cmdlet byter namn på.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-125">Specifies the security ID (SID) of a user accounts that this cmdlet renames.</span></span>

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

### <span data-ttu-id="3dbbc-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3dbbc-126">-Confirm</span></span>
<span data-ttu-id="3dbbc-127">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3dbbc-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3dbbc-128">-WhatIf</span></span>
<span data-ttu-id="3dbbc-129">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="3dbbc-130">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3dbbc-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3dbbc-131">CommonParameters</span></span>
<span data-ttu-id="3dbbc-132">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3dbbc-133">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3dbbc-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3dbbc-134">INDATA</span><span class="sxs-lookup"><span data-stu-id="3dbbc-134">INPUTS</span></span>

### <span data-ttu-id="3dbbc-135">System. Management. Automation. SecurityAccountsManager. lokal användare, system. String, system. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="3dbbc-135">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="3dbbc-136">Du kan skicka vidare en lokal användare, en sträng eller ett SID till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-136">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="3dbbc-137">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3dbbc-137">OUTPUTS</span></span>

### <span data-ttu-id="3dbbc-138">Inget</span><span class="sxs-lookup"><span data-stu-id="3dbbc-138">None</span></span>
<span data-ttu-id="3dbbc-139">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-139">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3dbbc-140">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3dbbc-140">NOTES</span></span>

* <span data-ttu-id="3dbbc-141">Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-141">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="3dbbc-142">De möjliga källorna är följande:</span><span class="sxs-lookup"><span data-stu-id="3dbbc-142">The possible sources are as follows:</span></span>

- <span data-ttu-id="3dbbc-143">Lokal</span><span class="sxs-lookup"><span data-stu-id="3dbbc-143">Local</span></span>
- <span data-ttu-id="3dbbc-144">Active Directory</span><span class="sxs-lookup"><span data-stu-id="3dbbc-144">Active Directory</span></span>
- <span data-ttu-id="3dbbc-145">Azure Active Directory grupp</span><span class="sxs-lookup"><span data-stu-id="3dbbc-145">Azure Active Directory group</span></span>
- <span data-ttu-id="3dbbc-146">Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="3dbbc-146">Microsoft Account</span></span>

<span data-ttu-id="3dbbc-147">**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-147">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="3dbbc-148">För tidigare versioner är egenskapen tom.</span><span class="sxs-lookup"><span data-stu-id="3dbbc-148">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="3dbbc-149">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3dbbc-149">RELATED LINKS</span></span>

[<span data-ttu-id="3dbbc-150">Disable-lokal användare</span><span class="sxs-lookup"><span data-stu-id="3dbbc-150">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="3dbbc-151">Aktivera – lokal användare</span><span class="sxs-lookup"><span data-stu-id="3dbbc-151">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="3dbbc-152">Get-lokal användare</span><span class="sxs-lookup"><span data-stu-id="3dbbc-152">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="3dbbc-153">New-lokal användare</span><span class="sxs-lookup"><span data-stu-id="3dbbc-153">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="3dbbc-154">Remove-lokal användare</span><span class="sxs-lookup"><span data-stu-id="3dbbc-154">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="3dbbc-155">Set-lokal användare</span><span class="sxs-lookup"><span data-stu-id="3dbbc-155">Set-LocalUser</span></span>](Set-LocalUser.md)
