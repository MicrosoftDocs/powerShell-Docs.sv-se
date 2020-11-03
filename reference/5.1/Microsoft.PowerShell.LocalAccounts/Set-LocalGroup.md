---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/set-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LocalGroup
ms.openlocfilehash: 471c3c7bc01bf26dfe9d8eec26e4414464cae02e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266282"
---
# <span data-ttu-id="aa99c-103">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="aa99c-103">Set-LocalGroup</span></span>

## <span data-ttu-id="aa99c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="aa99c-104">SYNOPSIS</span></span>
<span data-ttu-id="aa99c-105">Ändrar en lokal säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="aa99c-105">Changes a local security group.</span></span>

## <span data-ttu-id="aa99c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aa99c-106">SYNTAX</span></span>

### <span data-ttu-id="aa99c-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="aa99c-107">InputObject</span></span>

```
Set-LocalGroup -Description <String> [-InputObject] <LocalGroup> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="aa99c-108">Default</span><span class="sxs-lookup"><span data-stu-id="aa99c-108">Default</span></span>

```
Set-LocalGroup -Description <String> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="aa99c-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="aa99c-109">SecurityIdentifier</span></span>

```
Set-LocalGroup -Description <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="aa99c-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="aa99c-110">DESCRIPTION</span></span>
<span data-ttu-id="aa99c-111">Cmdleten **set-localgroup** ändrar en lokal säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="aa99c-111">The **Set-LocalGroup** cmdlet changes a local security group.</span></span>

## <span data-ttu-id="aa99c-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="aa99c-112">EXAMPLES</span></span>

### <span data-ttu-id="aa99c-113">Exempel 1: ändra en grupp Beskrivning</span><span class="sxs-lookup"><span data-stu-id="aa99c-113">Example 1: Change a group description</span></span>

```
PS C:\> Set-LocalGroup -Name "SecurityGroup04" -Description "This is a sample description."
```

<span data-ttu-id="aa99c-114">Det här kommandot ändrar beskrivningen av en lokal grupp.</span><span class="sxs-lookup"><span data-stu-id="aa99c-114">This command changes the description of a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="aa99c-115">Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.</span><span class="sxs-lookup"><span data-stu-id="aa99c-115">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="aa99c-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="aa99c-116">PARAMETERS</span></span>

### <span data-ttu-id="aa99c-117">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="aa99c-117">-Description</span></span>
<span data-ttu-id="aa99c-118">Anger en kommentar för gruppen.</span><span class="sxs-lookup"><span data-stu-id="aa99c-118">Specifies a comment for the group.</span></span>
<span data-ttu-id="aa99c-119">Den maximala längden är 48 tecken.</span><span class="sxs-lookup"><span data-stu-id="aa99c-119">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aa99c-120">– InputObject</span><span class="sxs-lookup"><span data-stu-id="aa99c-120">-InputObject</span></span>
<span data-ttu-id="aa99c-121">Anger säkerhets gruppen som denna cmdlet ändrar.</span><span class="sxs-lookup"><span data-stu-id="aa99c-121">Specifies the security group that this cmdlet changes.</span></span>
<span data-ttu-id="aa99c-122">Använd Get-LocalGroup-cmdleten för att hämta en säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="aa99c-122">To obtain a security group, use the Get-LocalGroup cmdlet.</span></span>

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

### <span data-ttu-id="aa99c-123">-Name</span><span class="sxs-lookup"><span data-stu-id="aa99c-123">-Name</span></span>
<span data-ttu-id="aa99c-124">Anger namnet på den säkerhets grupp som denna cmdlet ändrar.</span><span class="sxs-lookup"><span data-stu-id="aa99c-124">Specifies the name of the security group that this cmdlet changes.</span></span>

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

### <span data-ttu-id="aa99c-125">-SID</span><span class="sxs-lookup"><span data-stu-id="aa99c-125">-SID</span></span>
<span data-ttu-id="aa99c-126">Anger säkerhets-ID: t (SID) för den säkerhets grupp som denna cmdlet ändrar.</span><span class="sxs-lookup"><span data-stu-id="aa99c-126">Specifies the security ID (SID) of the security group that this cmdlet changes.</span></span>

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

### <span data-ttu-id="aa99c-127">-Confirm</span><span class="sxs-lookup"><span data-stu-id="aa99c-127">-Confirm</span></span>
<span data-ttu-id="aa99c-128">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aa99c-128">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="aa99c-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="aa99c-129">-WhatIf</span></span>
<span data-ttu-id="aa99c-130">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="aa99c-130">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="aa99c-131">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="aa99c-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="aa99c-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aa99c-132">CommonParameters</span></span>
<span data-ttu-id="aa99c-133">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aa99c-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aa99c-134">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="aa99c-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aa99c-135">INDATA</span><span class="sxs-lookup"><span data-stu-id="aa99c-135">INPUTS</span></span>

### <span data-ttu-id="aa99c-136">System. Management. Automation. SecurityAccountsManager. LocalGroup, system. String, system. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="aa99c-136">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="aa99c-137">Du kan skicka vidare en säkerhets grupp, en sträng eller ett SID till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aa99c-137">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="aa99c-138">UTDATA</span><span class="sxs-lookup"><span data-stu-id="aa99c-138">OUTPUTS</span></span>

### <span data-ttu-id="aa99c-139">Inget</span><span class="sxs-lookup"><span data-stu-id="aa99c-139">None</span></span>
<span data-ttu-id="aa99c-140">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="aa99c-140">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="aa99c-141">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="aa99c-141">NOTES</span></span>

* <span data-ttu-id="aa99c-142">Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa.</span><span class="sxs-lookup"><span data-stu-id="aa99c-142">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="aa99c-143">De möjliga källorna är följande:</span><span class="sxs-lookup"><span data-stu-id="aa99c-143">The possible sources are as follows:</span></span>

- <span data-ttu-id="aa99c-144">Lokal</span><span class="sxs-lookup"><span data-stu-id="aa99c-144">Local</span></span>
- <span data-ttu-id="aa99c-145">Active Directory</span><span class="sxs-lookup"><span data-stu-id="aa99c-145">Active Directory</span></span>
- <span data-ttu-id="aa99c-146">Azure Active Directory grupp</span><span class="sxs-lookup"><span data-stu-id="aa99c-146">Azure Active Directory group</span></span>
- <span data-ttu-id="aa99c-147">Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="aa99c-147">Microsoft Account</span></span>

<span data-ttu-id="aa99c-148">**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="aa99c-148">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="aa99c-149">För tidigare versioner är egenskapen tom.</span><span class="sxs-lookup"><span data-stu-id="aa99c-149">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="aa99c-150">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="aa99c-150">RELATED LINKS</span></span>

[<span data-ttu-id="aa99c-151">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="aa99c-151">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="aa99c-152">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="aa99c-152">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="aa99c-153">Ta bort-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="aa99c-153">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="aa99c-154">Byt namn – lokal</span><span class="sxs-lookup"><span data-stu-id="aa99c-154">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)
