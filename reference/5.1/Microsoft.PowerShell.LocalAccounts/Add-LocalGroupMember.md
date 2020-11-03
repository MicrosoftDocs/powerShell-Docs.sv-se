---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-LocalGroupMember
ms.openlocfilehash: 06993c8f6618472f4809e37fbf83d298d13ae515
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263535"
---
# <span data-ttu-id="a6a32-103">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="a6a32-103">Add-LocalGroupMember</span></span>

## <span data-ttu-id="a6a32-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a6a32-104">SYNOPSIS</span></span>
<span data-ttu-id="a6a32-105">Lägger till medlemmar i en lokal grupp.</span><span class="sxs-lookup"><span data-stu-id="a6a32-105">Adds members to a local group.</span></span>

## <span data-ttu-id="a6a32-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a6a32-106">SYNTAX</span></span>

### <span data-ttu-id="a6a32-107">Group</span><span class="sxs-lookup"><span data-stu-id="a6a32-107">Group</span></span>

```
Add-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="a6a32-108">Default</span><span class="sxs-lookup"><span data-stu-id="a6a32-108">Default</span></span>

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a6a32-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="a6a32-109">SecurityIdentifier</span></span>

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="a6a32-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a6a32-110">DESCRIPTION</span></span>

<span data-ttu-id="a6a32-111">`Add-LocalGroupMember`Cmdleten lägger till användare eller grupper i en lokal säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="a6a32-111">The `Add-LocalGroupMember` cmdlet adds users or groups to a local security group.</span></span> <span data-ttu-id="a6a32-112">Alla rättigheter och behörigheter som tilldelas en grupp tilldelas till alla medlemmar i gruppen.</span><span class="sxs-lookup"><span data-stu-id="a6a32-112">All the rights and permissions that are assigned to a group are assigned to all members of that group.</span></span>

<span data-ttu-id="a6a32-113">Medlemmar i gruppen Administratörer på en lokal dator har fullständig behörighet på den datorn.</span><span class="sxs-lookup"><span data-stu-id="a6a32-113">Members of the Administrators group on a local computer have Full Control permissions on that computer.</span></span> <span data-ttu-id="a6a32-114">Begränsa antalet användare i gruppen Administratörer.</span><span class="sxs-lookup"><span data-stu-id="a6a32-114">Limit the number of users in the Administrators group.</span></span>

<span data-ttu-id="a6a32-115">Om datorn är ansluten till en domän kan du lägga till användar konton, dator konton och grupp konton från domänen och från betrodda domäner till en lokal grupp.</span><span class="sxs-lookup"><span data-stu-id="a6a32-115">If the computer is joined to a domain, you can add user accounts, computer accounts, and group accounts from that domain and from trusted domains to a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="a6a32-116">Om datorn är ansluten till en domän och du försöker lägga till en lokal användare som har samma namn som en medlem i domänen läggs domän medlemmen till.</span><span class="sxs-lookup"><span data-stu-id="a6a32-116">If the computer is joined to a domain and you try to add a local user that has the same name as a member of the domain it adds the domain member.</span></span>

## <span data-ttu-id="a6a32-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a6a32-117">EXAMPLES</span></span>

### <span data-ttu-id="a6a32-118">Exempel 1: Lägg till medlemmar i gruppen Administratörer</span><span class="sxs-lookup"><span data-stu-id="a6a32-118">Example 1: Add members to the Administrators group</span></span>

<span data-ttu-id="a6a32-119">Det här kommandot lägger till flera medlemmar i den lokala gruppen Administratörer.</span><span class="sxs-lookup"><span data-stu-id="a6a32-119">This command adds several members to the local Administrators group.</span></span> <span data-ttu-id="a6a32-120">De nya medlemmarna inkluderar ett lokalt användar konto, ett Microsoft-konto, ett Azure Active Directory konto och en domän grupp.</span><span class="sxs-lookup"><span data-stu-id="a6a32-120">The new members include a local user account, a Microsoft account, an Azure Active Directory account, and a domain group.</span></span> <span data-ttu-id="a6a32-121">I det här exemplet används ett plats hållare-värde för användar namnet för ett konto på Outlook.com.</span><span class="sxs-lookup"><span data-stu-id="a6a32-121">This example uses a placeholder value for the user name of an account at Outlook.com.</span></span>

```powershell
Add-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

## <span data-ttu-id="a6a32-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a6a32-122">PARAMETERS</span></span>

### <span data-ttu-id="a6a32-123">– Grupp</span><span class="sxs-lookup"><span data-stu-id="a6a32-123">-Group</span></span>

<span data-ttu-id="a6a32-124">Anger den säkerhets grupp som denna cmdlet lägger till medlemmar i.</span><span class="sxs-lookup"><span data-stu-id="a6a32-124">Specifies the security group to which this cmdlet adds members.</span></span>

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

### <span data-ttu-id="a6a32-125">– Medlem</span><span class="sxs-lookup"><span data-stu-id="a6a32-125">-Member</span></span>

<span data-ttu-id="a6a32-126">Anger en matris med användare eller grupper som denna cmdlet lägger till i en säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="a6a32-126">Specifies an array of users or groups that this cmdlet adds to a security group.</span></span> <span data-ttu-id="a6a32-127">Du kan ange användare eller grupper efter namn, säkerhets-ID (SID) eller **LocalPrincipal** -objekt.</span><span class="sxs-lookup"><span data-stu-id="a6a32-127">You can specify users or groups by name, security ID (SID), or **LocalPrincipal** objects.</span></span>

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

### <span data-ttu-id="a6a32-128">-Name</span><span class="sxs-lookup"><span data-stu-id="a6a32-128">-Name</span></span>

<span data-ttu-id="a6a32-129">Anger namnet på den säkerhets grupp som denna cmdlet lägger till medlemmar i.</span><span class="sxs-lookup"><span data-stu-id="a6a32-129">Specifies the name of the security group to which this cmdlet adds members.</span></span>

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

### <span data-ttu-id="a6a32-130">-SID</span><span class="sxs-lookup"><span data-stu-id="a6a32-130">-SID</span></span>

<span data-ttu-id="a6a32-131">Anger säkerhets-ID: t för den säkerhets grupp som denna cmdlet lägger till medlemmar i.</span><span class="sxs-lookup"><span data-stu-id="a6a32-131">Specifies the security ID of the security group to which this cmdlet adds members.</span></span>

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

### <span data-ttu-id="a6a32-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a6a32-132">-Confirm</span></span>

<span data-ttu-id="a6a32-133">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a6a32-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a6a32-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a6a32-134">-WhatIf</span></span>

<span data-ttu-id="a6a32-135">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="a6a32-135">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a6a32-136">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="a6a32-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a6a32-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a6a32-137">CommonParameters</span></span>

<span data-ttu-id="a6a32-138">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a6a32-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a6a32-139">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a6a32-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a6a32-140">INDATA</span><span class="sxs-lookup"><span data-stu-id="a6a32-140">INPUTS</span></span>

### <span data-ttu-id="a6a32-141">System. Management. Automation. SecurityAccountsManager. LocalGroup, system. String, system. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="a6a32-141">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>

<span data-ttu-id="a6a32-142">Du kan skicka vidare ett lokalt huvud namn, en sträng eller ett SID till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a6a32-142">You can pipe a local principal, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="a6a32-143">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a6a32-143">OUTPUTS</span></span>

### <span data-ttu-id="a6a32-144">Inget</span><span class="sxs-lookup"><span data-stu-id="a6a32-144">None</span></span>

<span data-ttu-id="a6a32-145">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="a6a32-145">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a6a32-146">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a6a32-146">NOTES</span></span>

<span data-ttu-id="a6a32-147">Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.</span><span class="sxs-lookup"><span data-stu-id="a6a32-147">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

<span data-ttu-id="a6a32-148">Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa.</span><span class="sxs-lookup"><span data-stu-id="a6a32-148">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="a6a32-149">De möjliga källorna är följande:</span><span class="sxs-lookup"><span data-stu-id="a6a32-149">The possible sources are as follows:</span></span>

- <span data-ttu-id="a6a32-150">Lokal</span><span class="sxs-lookup"><span data-stu-id="a6a32-150">Local</span></span>
- <span data-ttu-id="a6a32-151">Active Directory</span><span class="sxs-lookup"><span data-stu-id="a6a32-151">Active Directory</span></span>
- <span data-ttu-id="a6a32-152">Azure Active Directory grupp</span><span class="sxs-lookup"><span data-stu-id="a6a32-152">Azure Active Directory group</span></span>
- <span data-ttu-id="a6a32-153">Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="a6a32-153">Microsoft Account</span></span>

<span data-ttu-id="a6a32-154">**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="a6a32-154">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="a6a32-155">För tidigare versioner är egenskapen tom.</span><span class="sxs-lookup"><span data-stu-id="a6a32-155">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="a6a32-156">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a6a32-156">RELATED LINKS</span></span>

[<span data-ttu-id="a6a32-157">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="a6a32-157">Get-LocalGroupMember</span></span>](Get-LocalGroupMember.md)

[<span data-ttu-id="a6a32-158">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="a6a32-158">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="a6a32-159">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="a6a32-159">Remove-LocalGroupMember</span></span>](Remove-LocalGroupMember.md)
