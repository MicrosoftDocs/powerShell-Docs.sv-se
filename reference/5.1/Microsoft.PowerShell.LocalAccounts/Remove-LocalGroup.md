---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroup
ms.openlocfilehash: 6a2f921972fef1794581b301df6e7439e56c7f47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265574"
---
# <span data-ttu-id="2eca9-103">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="2eca9-103">Remove-LocalGroup</span></span>

## <span data-ttu-id="2eca9-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2eca9-104">SYNOPSIS</span></span>
<span data-ttu-id="2eca9-105">Tar bort lokala säkerhets grupper.</span><span class="sxs-lookup"><span data-stu-id="2eca9-105">Deletes local security groups.</span></span>

## <span data-ttu-id="2eca9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2eca9-106">SYNTAX</span></span>

### <span data-ttu-id="2eca9-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="2eca9-107">InputObject</span></span>

```
Remove-LocalGroup [-InputObject] <LocalGroup[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2eca9-108">Default</span><span class="sxs-lookup"><span data-stu-id="2eca9-108">Default</span></span>

```
Remove-LocalGroup [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2eca9-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="2eca9-109">SecurityIdentifier</span></span>

```
Remove-LocalGroup [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2eca9-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2eca9-110">DESCRIPTION</span></span>
<span data-ttu-id="2eca9-111">Cmdlet: en **Remove-localgroup** tar bort lokala säkerhets grupper.</span><span class="sxs-lookup"><span data-stu-id="2eca9-111">The **Remove-LocalGroup** cmdlet deletes local security groups.</span></span>
<span data-ttu-id="2eca9-112">Den här cmdleten tar bara bort en lokal grupp.</span><span class="sxs-lookup"><span data-stu-id="2eca9-112">This cmdlet deletes only a local group.</span></span>
<span data-ttu-id="2eca9-113">De användar konton, dator konton eller grupp konton som tillhör gruppen tas inte bort.</span><span class="sxs-lookup"><span data-stu-id="2eca9-113">It does not delete the user accounts, computer accounts, or group accounts that belong to that group.</span></span>
<span data-ttu-id="2eca9-114">Det går inte att återställa en borttagen grupp.</span><span class="sxs-lookup"><span data-stu-id="2eca9-114">You cannot recover a deleted group.</span></span>

<span data-ttu-id="2eca9-115">Om du tar bort en grupp och sedan skapar en annan grupp som har samma grupp namn, måste du ange nya behörigheter för den nya gruppen.</span><span class="sxs-lookup"><span data-stu-id="2eca9-115">If you delete a group and then create another group that has the same group name, you must set new permissions for the new group.</span></span>
<span data-ttu-id="2eca9-116">Den nya gruppen ärver inte de behörigheter som har tilldelats gruppen.</span><span class="sxs-lookup"><span data-stu-id="2eca9-116">The new group does not inherit the permissions that were assigned to the group.</span></span>

> [!NOTE]
> <span data-ttu-id="2eca9-117">Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.</span><span class="sxs-lookup"><span data-stu-id="2eca9-117">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="2eca9-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2eca9-118">EXAMPLES</span></span>

### <span data-ttu-id="2eca9-119">Exempel 1: ta bort en säkerhets grupp</span><span class="sxs-lookup"><span data-stu-id="2eca9-119">Example 1: Delete a security group</span></span>

```
PS C:\> Remove-LocalGroup -Name "SecurityGroup04"
```

<span data-ttu-id="2eca9-120">Det här kommandot tar bort gruppen med namnet SecurityGroup04.</span><span class="sxs-lookup"><span data-stu-id="2eca9-120">This command deletes the group named SecurityGroup04.</span></span>

## <span data-ttu-id="2eca9-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2eca9-121">PARAMETERS</span></span>

### <span data-ttu-id="2eca9-122">– InputObject</span><span class="sxs-lookup"><span data-stu-id="2eca9-122">-InputObject</span></span>
<span data-ttu-id="2eca9-123">Anger en matris med säkerhets grupper som denna cmdlet tar bort.</span><span class="sxs-lookup"><span data-stu-id="2eca9-123">Specifies an array of security groups that this cmdlet deletes.</span></span>
<span data-ttu-id="2eca9-124">Använd Get-LocalGroup-cmdleten för att hämta grupper.</span><span class="sxs-lookup"><span data-stu-id="2eca9-124">To obtain groups, use the Get-LocalGroup cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2eca9-125">-Name</span><span class="sxs-lookup"><span data-stu-id="2eca9-125">-Name</span></span>
<span data-ttu-id="2eca9-126">Anger en matris med namn på de säkerhets grupper som denna cmdlet tar bort.</span><span class="sxs-lookup"><span data-stu-id="2eca9-126">Specifies an array of names of the security groups that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="2eca9-127">-SID</span><span class="sxs-lookup"><span data-stu-id="2eca9-127">-SID</span></span>
<span data-ttu-id="2eca9-128">Anger en matris med säkerhets-ID: n (sid) för de säkerhets grupper som denna cmdlet tar bort.</span><span class="sxs-lookup"><span data-stu-id="2eca9-128">Specifies an array of security IDs (SIDs) of security groups that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="2eca9-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2eca9-129">-Confirm</span></span>
<span data-ttu-id="2eca9-130">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2eca9-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2eca9-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2eca9-131">-WhatIf</span></span>
<span data-ttu-id="2eca9-132">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="2eca9-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2eca9-133">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="2eca9-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2eca9-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2eca9-134">CommonParameters</span></span>
<span data-ttu-id="2eca9-135">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2eca9-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2eca9-136">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2eca9-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2eca9-137">INDATA</span><span class="sxs-lookup"><span data-stu-id="2eca9-137">INPUTS</span></span>

### <span data-ttu-id="2eca9-138">System. Management. Automation. SecurityAccountsManager. LocalGroup, system. String, system. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="2eca9-138">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="2eca9-139">Du kan skicka vidare en säkerhets grupp, en sträng eller ett SID till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2eca9-139">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="2eca9-140">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2eca9-140">OUTPUTS</span></span>

### <span data-ttu-id="2eca9-141">Inget</span><span class="sxs-lookup"><span data-stu-id="2eca9-141">None</span></span>
<span data-ttu-id="2eca9-142">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="2eca9-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2eca9-143">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2eca9-143">NOTES</span></span>

* <span data-ttu-id="2eca9-144">Denna cmdlet kan inte ta bort följande standard grupper:</span><span class="sxs-lookup"><span data-stu-id="2eca9-144">This cmdlet cannot delete the following default groups:</span></span>

- <span data-ttu-id="2eca9-145">Administratörer</span><span class="sxs-lookup"><span data-stu-id="2eca9-145">Administrators</span></span>
- <span data-ttu-id="2eca9-146">Ansvariga för säkerhetskopiering</span><span class="sxs-lookup"><span data-stu-id="2eca9-146">Backup Operators</span></span>
- <span data-ttu-id="2eca9-147">Ansvariga för kryptering</span><span class="sxs-lookup"><span data-stu-id="2eca9-147">Cryptographic Operators</span></span>
- <span data-ttu-id="2eca9-148">Distribuerade COM-användare</span><span class="sxs-lookup"><span data-stu-id="2eca9-148">Distributed COM Users</span></span>
- <span data-ttu-id="2eca9-149">Händelseloggläsare</span><span class="sxs-lookup"><span data-stu-id="2eca9-149">Event Log Readers</span></span>
- <span data-ttu-id="2eca9-150">Gäster</span><span class="sxs-lookup"><span data-stu-id="2eca9-150">Guests</span></span>
- <span data-ttu-id="2eca9-151">Hyper-V-administratörer</span><span class="sxs-lookup"><span data-stu-id="2eca9-151">Hyper-V Administrators</span></span>
- <span data-ttu-id="2eca9-152">IIS_IUSRS</span><span class="sxs-lookup"><span data-stu-id="2eca9-152">IIS_IUSRS</span></span>
- <span data-ttu-id="2eca9-153">Ansvariga för nätverkskonfigurering</span><span class="sxs-lookup"><span data-stu-id="2eca9-153">Network Configuration Operators</span></span>
- <span data-ttu-id="2eca9-154">Användare av prestandaloggar</span><span class="sxs-lookup"><span data-stu-id="2eca9-154">Performance Log Users</span></span>
- <span data-ttu-id="2eca9-155">Användare av prestanda övervakning</span><span class="sxs-lookup"><span data-stu-id="2eca9-155">Performance Monitor Users</span></span>
- <span data-ttu-id="2eca9-156">Privilegierade användare</span><span class="sxs-lookup"><span data-stu-id="2eca9-156">Power Users</span></span>
- <span data-ttu-id="2eca9-157">Användare av fjärrskrivbord</span><span class="sxs-lookup"><span data-stu-id="2eca9-157">Remote Desktop Users</span></span>
- <span data-ttu-id="2eca9-158">Fjärrhanteringsanvändare</span><span class="sxs-lookup"><span data-stu-id="2eca9-158">Remote Management Users</span></span>
- <span data-ttu-id="2eca9-159">Ansvariga för replikering</span><span class="sxs-lookup"><span data-stu-id="2eca9-159">Replicator</span></span>
- <span data-ttu-id="2eca9-160">Användare</span><span class="sxs-lookup"><span data-stu-id="2eca9-160">Users</span></span>
- <span data-ttu-id="2eca9-161">WinRMRemoteWMIUsers__</span><span class="sxs-lookup"><span data-stu-id="2eca9-161">WinRMRemoteWMIUsers__</span></span>

* <span data-ttu-id="2eca9-162">Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa.</span><span class="sxs-lookup"><span data-stu-id="2eca9-162">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="2eca9-163">De möjliga källorna är följande:</span><span class="sxs-lookup"><span data-stu-id="2eca9-163">The possible sources are as follows:</span></span>

- <span data-ttu-id="2eca9-164">Lokal</span><span class="sxs-lookup"><span data-stu-id="2eca9-164">Local</span></span>
- <span data-ttu-id="2eca9-165">Active Directory</span><span class="sxs-lookup"><span data-stu-id="2eca9-165">Active Directory</span></span>
- <span data-ttu-id="2eca9-166">Azure Active Directory grupp</span><span class="sxs-lookup"><span data-stu-id="2eca9-166">Azure Active Directory group</span></span>
- <span data-ttu-id="2eca9-167">Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="2eca9-167">Microsoft Account</span></span>

<span data-ttu-id="2eca9-168">**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="2eca9-168">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="2eca9-169">För tidigare versioner är egenskapen tom.</span><span class="sxs-lookup"><span data-stu-id="2eca9-169">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="2eca9-170">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2eca9-170">RELATED LINKS</span></span>

[<span data-ttu-id="2eca9-171">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="2eca9-171">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="2eca9-172">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="2eca9-172">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="2eca9-173">Byt namn – lokal</span><span class="sxs-lookup"><span data-stu-id="2eca9-173">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="2eca9-174">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="2eca9-174">Set-LocalGroup</span></span>](Set-LocalGroup.md)
