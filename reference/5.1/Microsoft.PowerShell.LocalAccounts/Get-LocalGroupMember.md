---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroupMember
ms.openlocfilehash: 200368c5d13bd027302ad824533e6c187906ed0f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263510"
---
# <span data-ttu-id="07b35-103">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="07b35-103">Get-LocalGroupMember</span></span>

## <span data-ttu-id="07b35-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="07b35-104">SYNOPSIS</span></span>
<span data-ttu-id="07b35-105">Hämtar medlemmar från en lokal grupp.</span><span class="sxs-lookup"><span data-stu-id="07b35-105">Gets members from a local group.</span></span>

## <span data-ttu-id="07b35-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="07b35-106">SYNTAX</span></span>

### <span data-ttu-id="07b35-107">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="07b35-107">Default (Default)</span></span>

```
Get-LocalGroupMember [[-Member] <String>] [-Name] <String> [<CommonParameters>]
```

### <span data-ttu-id="07b35-108">Group</span><span class="sxs-lookup"><span data-stu-id="07b35-108">Group</span></span>

```
Get-LocalGroupMember [-Group] <LocalGroup> [[-Member] <String>] [<CommonParameters>]
```

### <span data-ttu-id="07b35-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="07b35-109">SecurityIdentifier</span></span>

```
Get-LocalGroupMember [[-Member] <String>] [-SID] <SecurityIdentifier> [<CommonParameters>]
```

## <span data-ttu-id="07b35-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="07b35-110">DESCRIPTION</span></span>
<span data-ttu-id="07b35-111">**Get-LocalGroupMember** -cmdlet: en hämtar medlemmar från en lokal grupp.</span><span class="sxs-lookup"><span data-stu-id="07b35-111">The **Get-LocalGroupMember** cmdlet gets members from a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="07b35-112">Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.</span><span class="sxs-lookup"><span data-stu-id="07b35-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="07b35-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="07b35-113">EXAMPLES</span></span>

### <span data-ttu-id="07b35-114">Exempel 1: Hämta alla medlemmar i gruppen Administratörer</span><span class="sxs-lookup"><span data-stu-id="07b35-114">Example 1: Get all members of the Administrators group</span></span>

```
PS C:\> Get-LocalGroupMember -Group "Administrators"
ObjectClass Name                    PrincipalSource
----------- ----                    ---------------
User        CONTOSOPC\Administrator Local
User        CONTOSOPC\LocalAdmin    Local
```

<span data-ttu-id="07b35-115">Det här kommandot hämtar alla medlemmar i den lokala administratörs gruppen.</span><span class="sxs-lookup"><span data-stu-id="07b35-115">This command gets all the members of the local Administrators group.</span></span>

## <span data-ttu-id="07b35-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="07b35-116">PARAMETERS</span></span>

### <span data-ttu-id="07b35-117">– Grupp</span><span class="sxs-lookup"><span data-stu-id="07b35-117">-Group</span></span>
<span data-ttu-id="07b35-118">Anger den säkerhets grupp från vilken denna cmdlet hämtar medlemmar.</span><span class="sxs-lookup"><span data-stu-id="07b35-118">Specifies the security group from which this cmdlet gets members.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="07b35-119">– Medlem</span><span class="sxs-lookup"><span data-stu-id="07b35-119">-Member</span></span>
<span data-ttu-id="07b35-120">Anger en användare eller grupp som denna cmdlet hämtar från en säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="07b35-120">Specifies a user or group that this cmdlet gets from a security group.</span></span>
<span data-ttu-id="07b35-121">Du kan ange användare eller grupper efter namn eller säkerhets-ID (SID).</span><span class="sxs-lookup"><span data-stu-id="07b35-121">You can specify users or groups by name or security ID (SID).</span></span>
<span data-ttu-id="07b35-122">Ange SID-strängar i S-R-I-S-S.</span><span class="sxs-lookup"><span data-stu-id="07b35-122">Specify SID strings in S-R-I-S-S .</span></span>
<span data-ttu-id="07b35-123">.</span><span class="sxs-lookup"><span data-stu-id="07b35-123">.</span></span> <span data-ttu-id="07b35-124">.</span><span class="sxs-lookup"><span data-stu-id="07b35-124">.</span></span>
<span data-ttu-id="07b35-125">.</span><span class="sxs-lookup"><span data-stu-id="07b35-125">format.</span></span>
<span data-ttu-id="07b35-126">Du kan använda jokertecken.</span><span class="sxs-lookup"><span data-stu-id="07b35-126">You can use wildcard characters.</span></span>
<span data-ttu-id="07b35-127">Om du inte anger den här parametern, hämtar cmdleten alla medlemmar i gruppen.</span><span class="sxs-lookup"><span data-stu-id="07b35-127">If you do not specify this parameter, the cmdlet gets all members of the group.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="07b35-128">-Name</span><span class="sxs-lookup"><span data-stu-id="07b35-128">-Name</span></span>
<span data-ttu-id="07b35-129">Anger namnet på den säkerhets grupp från vilken denna cmdlet hämtar medlemmar.</span><span class="sxs-lookup"><span data-stu-id="07b35-129">Specifies the name of the security group from which this cmdlet gets members.</span></span>

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

### <span data-ttu-id="07b35-130">-SID</span><span class="sxs-lookup"><span data-stu-id="07b35-130">-SID</span></span>
<span data-ttu-id="07b35-131">Anger säkerhets-ID: t för den säkerhets grupp som den här cmdlet: en hämtar medlemmar från.</span><span class="sxs-lookup"><span data-stu-id="07b35-131">Specifies the security ID of the security group from which this cmdlet gets members.</span></span>

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

### <span data-ttu-id="07b35-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="07b35-132">CommonParameters</span></span>
<span data-ttu-id="07b35-133">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="07b35-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="07b35-134">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="07b35-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="07b35-135">INDATA</span><span class="sxs-lookup"><span data-stu-id="07b35-135">INPUTS</span></span>

### <span data-ttu-id="07b35-136">System. Management. Automation. SecurityAccountsManager. LocalGroup, system. String, system. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="07b35-136">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="07b35-137">Du kan skicka vidare en lokal grupp, en sträng eller ett SID till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="07b35-137">You can pipe a local group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="07b35-138">UTDATA</span><span class="sxs-lookup"><span data-stu-id="07b35-138">OUTPUTS</span></span>

### <span data-ttu-id="07b35-139">Microsoft. SecurityAccountsManager. LocalPrincipal</span><span class="sxs-lookup"><span data-stu-id="07b35-139">Microsoft.SecurityAccountsManager.LocalPrincipal</span></span>
<span data-ttu-id="07b35-140">Denna cmdlet returnerar lokala huvud namn.</span><span class="sxs-lookup"><span data-stu-id="07b35-140">This cmdlet returns local principals.</span></span>

## <span data-ttu-id="07b35-141">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="07b35-141">NOTES</span></span>

* <span data-ttu-id="07b35-142">Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa.</span><span class="sxs-lookup"><span data-stu-id="07b35-142">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="07b35-143">De möjliga källorna är följande:</span><span class="sxs-lookup"><span data-stu-id="07b35-143">The possible sources are as follows:</span></span>

- <span data-ttu-id="07b35-144">Lokal</span><span class="sxs-lookup"><span data-stu-id="07b35-144">Local</span></span>
- <span data-ttu-id="07b35-145">Active Directory</span><span class="sxs-lookup"><span data-stu-id="07b35-145">Active Directory</span></span>
- <span data-ttu-id="07b35-146">Azure Active Directory grupp</span><span class="sxs-lookup"><span data-stu-id="07b35-146">Azure Active Directory group</span></span>
- <span data-ttu-id="07b35-147">Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="07b35-147">Microsoft Account</span></span>

<span data-ttu-id="07b35-148">**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="07b35-148">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="07b35-149">För tidigare versioner är egenskapen tom.</span><span class="sxs-lookup"><span data-stu-id="07b35-149">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="07b35-150">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="07b35-150">RELATED LINKS</span></span>

[<span data-ttu-id="07b35-151">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="07b35-151">Add-LocalGroupMember</span></span>](Add-LocalGroupMember.md)

[<span data-ttu-id="07b35-152">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="07b35-152">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="07b35-153">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="07b35-153">Remove-LocalGroupMember</span></span>](Remove-LocalGroupMember.md)
