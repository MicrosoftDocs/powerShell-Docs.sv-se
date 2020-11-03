---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroupMember
ms.openlocfilehash: 6e6264a65c343657c2f2f87384d76cc3f1554d3d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265575"
---
# <span data-ttu-id="7f858-103">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="7f858-103">Remove-LocalGroupMember</span></span>

## <span data-ttu-id="7f858-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7f858-104">SYNOPSIS</span></span>
<span data-ttu-id="7f858-105">Tar bort medlemmar från en lokal grupp.</span><span class="sxs-lookup"><span data-stu-id="7f858-105">Removes members from a local group.</span></span>

## <span data-ttu-id="7f858-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7f858-106">SYNTAX</span></span>

### <span data-ttu-id="7f858-107">Group</span><span class="sxs-lookup"><span data-stu-id="7f858-107">Group</span></span>

```
Remove-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="7f858-108">Default</span><span class="sxs-lookup"><span data-stu-id="7f858-108">Default</span></span>

```
Remove-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7f858-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="7f858-109">SecurityIdentifier</span></span>

```
Remove-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="7f858-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7f858-110">DESCRIPTION</span></span>
<span data-ttu-id="7f858-111">Cmdlet: en **Remove-LocalGroupMember** tar bort användare eller grupper från en lokal grupp.</span><span class="sxs-lookup"><span data-stu-id="7f858-111">The **Remove-LocalGroupMember** cmdlet removes users or groups from a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="7f858-112">Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.</span><span class="sxs-lookup"><span data-stu-id="7f858-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="7f858-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7f858-113">EXAMPLES</span></span>

### <span data-ttu-id="7f858-114">Exempel 1: ta bort medlemmar från gruppen Administratörer</span><span class="sxs-lookup"><span data-stu-id="7f858-114">Example 1: Remove members from the Administrators group</span></span>

```
PS C:\> Remove-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

<span data-ttu-id="7f858-115">Det här kommandot tar bort flera medlemmar från den lokala gruppen Administratörer.</span><span class="sxs-lookup"><span data-stu-id="7f858-115">This command removes several members from the local Administrators group.</span></span>
<span data-ttu-id="7f858-116">Medlemmarna som denna cmdlet tar bort inkluderar ett lokalt användar konto, ett Microsoft-konto, ett Azure Active Directory konto och en domän grupp.</span><span class="sxs-lookup"><span data-stu-id="7f858-116">The members that this cmdlet removes include a local user account, a Microsoft account, an Azure Active Directory account, and a domain group.</span></span>
<span data-ttu-id="7f858-117">I det här exemplet används ett plats hållare-värde för användar namnet för ett konto på Outlook.com.</span><span class="sxs-lookup"><span data-stu-id="7f858-117">This example uses a placeholder value for the user name of an account at Outlook.com.</span></span>

## <span data-ttu-id="7f858-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7f858-118">PARAMETERS</span></span>

### <span data-ttu-id="7f858-119">– Grupp</span><span class="sxs-lookup"><span data-stu-id="7f858-119">-Group</span></span>
<span data-ttu-id="7f858-120">Anger den säkerhets grupp från vilken denna cmdlet tar bort medlemmar.</span><span class="sxs-lookup"><span data-stu-id="7f858-120">Specifies the security group from which this cmdlet removes members.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7f858-121">– Medlem</span><span class="sxs-lookup"><span data-stu-id="7f858-121">-Member</span></span>
<span data-ttu-id="7f858-122">Anger en matris med användare eller grupper som denna cmdlet tar bort från en säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="7f858-122">Specifies an array of users or groups that this cmdlet removes from a security group.</span></span>
<span data-ttu-id="7f858-123">Du kan ange användare eller grupper efter namn, säkerhets-ID (SID) eller **LocalPrincipal** -objekt.</span><span class="sxs-lookup"><span data-stu-id="7f858-123">You can specify users or groups by name, security ID (SID), or **LocalPrincipal** objects.</span></span>
<span data-ttu-id="7f858-124">Ange SID-strängar i S-R-I-S-S.</span><span class="sxs-lookup"><span data-stu-id="7f858-124">Specify SID strings in S-R-I-S-S .</span></span>
<span data-ttu-id="7f858-125">.</span><span class="sxs-lookup"><span data-stu-id="7f858-125">.</span></span> <span data-ttu-id="7f858-126">.</span><span class="sxs-lookup"><span data-stu-id="7f858-126">.</span></span>
<span data-ttu-id="7f858-127">.</span><span class="sxs-lookup"><span data-stu-id="7f858-127">format.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalPrincipal[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7f858-128">-Name</span><span class="sxs-lookup"><span data-stu-id="7f858-128">-Name</span></span>
<span data-ttu-id="7f858-129">Anger namnet på den säkerhets grupp från vilken denna cmdlet tar bort medlemmar.</span><span class="sxs-lookup"><span data-stu-id="7f858-129">Specifies the name of the security group from which this cmdlet removes members.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7f858-130">-SID</span><span class="sxs-lookup"><span data-stu-id="7f858-130">-SID</span></span>
<span data-ttu-id="7f858-131">Anger säkerhets-ID: t för den säkerhets grupp från vilken denna cmdlet tar bort medlemmar.</span><span class="sxs-lookup"><span data-stu-id="7f858-131">Specifies the security ID of the security group from which this cmdlet removes members.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7f858-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7f858-132">-Confirm</span></span>
<span data-ttu-id="7f858-133">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7f858-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7f858-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7f858-134">-WhatIf</span></span>
<span data-ttu-id="7f858-135">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="7f858-135">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7f858-136">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="7f858-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7f858-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7f858-137">CommonParameters</span></span>
<span data-ttu-id="7f858-138">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7f858-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7f858-139">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7f858-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7f858-140">INDATA</span><span class="sxs-lookup"><span data-stu-id="7f858-140">INPUTS</span></span>

### <span data-ttu-id="7f858-141">System. Management. Automation. SecurityAccountsManager. LocalPrincipal, system. String, system. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="7f858-141">System.Management.Automation.SecurityAccountsManager.LocalPrincipal, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="7f858-142">Du kan skicka vidare ett lokalt huvud namn, en sträng eller ett SID till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7f858-142">You can pipe a local principal, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="7f858-143">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7f858-143">OUTPUTS</span></span>

### <span data-ttu-id="7f858-144">Inget</span><span class="sxs-lookup"><span data-stu-id="7f858-144">None</span></span>
<span data-ttu-id="7f858-145">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="7f858-145">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7f858-146">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7f858-146">NOTES</span></span>

* <span data-ttu-id="7f858-147">Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa.</span><span class="sxs-lookup"><span data-stu-id="7f858-147">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="7f858-148">De möjliga källorna är följande:</span><span class="sxs-lookup"><span data-stu-id="7f858-148">The possible sources are as follows:</span></span>

- <span data-ttu-id="7f858-149">Lokal</span><span class="sxs-lookup"><span data-stu-id="7f858-149">Local</span></span>
- <span data-ttu-id="7f858-150">Active Directory</span><span class="sxs-lookup"><span data-stu-id="7f858-150">Active Directory</span></span>
- <span data-ttu-id="7f858-151">Azure Active Directory grupp</span><span class="sxs-lookup"><span data-stu-id="7f858-151">Azure Active Directory group</span></span>
- <span data-ttu-id="7f858-152">Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="7f858-152">Microsoft Account</span></span>

<span data-ttu-id="7f858-153">**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="7f858-153">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="7f858-154">För tidigare versioner är egenskapen tom.</span><span class="sxs-lookup"><span data-stu-id="7f858-154">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="7f858-155">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7f858-155">RELATED LINKS</span></span>

[<span data-ttu-id="7f858-156">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="7f858-156">Add-LocalGroupMember</span></span>](Add-LocalGroupMember.md)

[<span data-ttu-id="7f858-157">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="7f858-157">Get-LocalGroupMember</span></span>](Get-LocalGroupMember.md)

[<span data-ttu-id="7f858-158">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="7f858-158">New-LocalGroup</span></span>](New-LocalGroup.md)
