---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/rename-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-LocalGroup
ms.openlocfilehash: 566d33bdeb52323cca41fa9757d36334b40f1654
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266277"
---
# <span data-ttu-id="0416b-103">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="0416b-103">Rename-LocalGroup</span></span>

## <span data-ttu-id="0416b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0416b-104">SYNOPSIS</span></span>
<span data-ttu-id="0416b-105">Byter namn på en lokal säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="0416b-105">Renames a local security group.</span></span>

## <span data-ttu-id="0416b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0416b-106">SYNTAX</span></span>

### <span data-ttu-id="0416b-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="0416b-107">InputObject</span></span>

```
Rename-LocalGroup [-InputObject] <LocalGroup> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0416b-108">Default</span><span class="sxs-lookup"><span data-stu-id="0416b-108">Default</span></span>

```
Rename-LocalGroup [-Name] <String> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0416b-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="0416b-109">SecurityIdentifier</span></span>

```
Rename-LocalGroup [-NewName] <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0416b-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0416b-110">DESCRIPTION</span></span>
<span data-ttu-id="0416b-111">Cmdleten **rename-localgroup** byter namn på en lokal säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="0416b-111">The **Rename-LocalGroup** cmdlet renames a local security group.</span></span>

> [!NOTE]
> <span data-ttu-id="0416b-112">Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.</span><span class="sxs-lookup"><span data-stu-id="0416b-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="0416b-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0416b-113">EXAMPLES</span></span>

### <span data-ttu-id="0416b-114">Exempel 1: ändra namnet på en grupp</span><span class="sxs-lookup"><span data-stu-id="0416b-114">Example 1: Change the name of a group</span></span>

```
PS C:\> Rename-LocalGroup -Name "SecurityGroup" -NewName "SecurityGroup04"
```

<span data-ttu-id="0416b-115">Med det här kommandot byter du namn på en säkerhets grupp med namnet SecurityGroup.</span><span class="sxs-lookup"><span data-stu-id="0416b-115">This command renames a security group named SecurityGroup.</span></span>

## <span data-ttu-id="0416b-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0416b-116">PARAMETERS</span></span>

### <span data-ttu-id="0416b-117">– InputObject</span><span class="sxs-lookup"><span data-stu-id="0416b-117">-InputObject</span></span>
<span data-ttu-id="0416b-118">Anger säkerhets gruppen som den här cmdleten byter namn på.</span><span class="sxs-lookup"><span data-stu-id="0416b-118">Specifies the security group that this cmdlet renames.</span></span>
<span data-ttu-id="0416b-119">Använd Get-LocalGroup-cmdleten för att hämta en säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="0416b-119">To obtain a security group, use the Get-LocalGroup cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0416b-120">-Name</span><span class="sxs-lookup"><span data-stu-id="0416b-120">-Name</span></span>
<span data-ttu-id="0416b-121">Anger namnet på den säkerhets grupp som denna cmdlet byter namn på.</span><span class="sxs-lookup"><span data-stu-id="0416b-121">Specifies the name of the security group that this cmdlet renames.</span></span>

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

### <span data-ttu-id="0416b-122">-Nyttnamn</span><span class="sxs-lookup"><span data-stu-id="0416b-122">-NewName</span></span>
<span data-ttu-id="0416b-123">Anger ett nytt namn på säkerhets gruppen.</span><span class="sxs-lookup"><span data-stu-id="0416b-123">Specifies a new name for the security group.</span></span>

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

### <span data-ttu-id="0416b-124">-SID</span><span class="sxs-lookup"><span data-stu-id="0416b-124">-SID</span></span>
<span data-ttu-id="0416b-125">Anger säkerhets-ID: t (SID) för en säkerhets grupp som denna cmdlet byter namn på.</span><span class="sxs-lookup"><span data-stu-id="0416b-125">Specifies the security ID (SID) of a security group that this cmdlet renames.</span></span>

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

### <span data-ttu-id="0416b-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0416b-126">-Confirm</span></span>
<span data-ttu-id="0416b-127">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0416b-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0416b-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0416b-128">-WhatIf</span></span>
<span data-ttu-id="0416b-129">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="0416b-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="0416b-130">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="0416b-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0416b-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0416b-131">CommonParameters</span></span>
<span data-ttu-id="0416b-132">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0416b-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0416b-133">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0416b-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0416b-134">INDATA</span><span class="sxs-lookup"><span data-stu-id="0416b-134">INPUTS</span></span>

### <span data-ttu-id="0416b-135">System. Management. Automation. SecurityAccountsManager. LocalGroup, system. String, system. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="0416b-135">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="0416b-136">Du kan skicka vidare en säkerhets grupp, en sträng eller ett SID till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0416b-136">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="0416b-137">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0416b-137">OUTPUTS</span></span>

### <span data-ttu-id="0416b-138">Inget</span><span class="sxs-lookup"><span data-stu-id="0416b-138">None</span></span>
<span data-ttu-id="0416b-139">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="0416b-139">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="0416b-140">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0416b-140">NOTES</span></span>

* <span data-ttu-id="0416b-141">Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa.</span><span class="sxs-lookup"><span data-stu-id="0416b-141">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="0416b-142">De möjliga källorna är följande:</span><span class="sxs-lookup"><span data-stu-id="0416b-142">The possible sources are as follows:</span></span>

- <span data-ttu-id="0416b-143">Lokal</span><span class="sxs-lookup"><span data-stu-id="0416b-143">Local</span></span>
- <span data-ttu-id="0416b-144">Active Directory</span><span class="sxs-lookup"><span data-stu-id="0416b-144">Active Directory</span></span>
- <span data-ttu-id="0416b-145">Azure Active Directory grupp</span><span class="sxs-lookup"><span data-stu-id="0416b-145">Azure Active Directory group</span></span>
- <span data-ttu-id="0416b-146">Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="0416b-146">Microsoft Account</span></span>

<span data-ttu-id="0416b-147">**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="0416b-147">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="0416b-148">För tidigare versioner är egenskapen tom.</span><span class="sxs-lookup"><span data-stu-id="0416b-148">For earlier  versions, the property is blank.</span></span>

## <span data-ttu-id="0416b-149">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0416b-149">RELATED LINKS</span></span>

[<span data-ttu-id="0416b-150">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="0416b-150">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="0416b-151">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="0416b-151">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="0416b-152">Ta bort-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="0416b-152">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="0416b-153">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="0416b-153">Set-LocalGroup</span></span>](Set-LocalGroup.md)
