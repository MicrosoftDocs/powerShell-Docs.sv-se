---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalGroup
ms.openlocfilehash: de66ad724d3cfee2d296d3b431618768a9cd38da
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265581"
---
# <span data-ttu-id="109a0-103">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="109a0-103">New-LocalGroup</span></span>

## <span data-ttu-id="109a0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="109a0-104">SYNOPSIS</span></span>
<span data-ttu-id="109a0-105">Skapar en lokal säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="109a0-105">Creates a local security group.</span></span>

## <span data-ttu-id="109a0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="109a0-106">SYNTAX</span></span>

```
New-LocalGroup [-Description <String>] [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="109a0-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="109a0-107">DESCRIPTION</span></span>
<span data-ttu-id="109a0-108">**New-localgroup-** cmdlet: en skapar en lokal säkerhets grupp i Security Account Manager.</span><span class="sxs-lookup"><span data-stu-id="109a0-108">The **New-LocalGroup** cmdlet creates a local security group in the Security Account Manager.</span></span>

> [!NOTE]
> <span data-ttu-id="109a0-109">Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.</span><span class="sxs-lookup"><span data-stu-id="109a0-109">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="109a0-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="109a0-110">EXAMPLES</span></span>

### <span data-ttu-id="109a0-111">Exempel 1: skapa en säkerhets grupp</span><span class="sxs-lookup"><span data-stu-id="109a0-111">Example 1: Create a security group</span></span>

```
PS C:\> New-LocalGroup -Name "SecurityGroup04"
```

<span data-ttu-id="109a0-112">Det här kommandot skapar en grupp med namnet SecurityGroup04.</span><span class="sxs-lookup"><span data-stu-id="109a0-112">This command creates a group named SecurityGroup04.</span></span>

## <span data-ttu-id="109a0-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="109a0-113">PARAMETERS</span></span>

### <span data-ttu-id="109a0-114">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="109a0-114">-Description</span></span>
<span data-ttu-id="109a0-115">Anger en kommentar för gruppen.</span><span class="sxs-lookup"><span data-stu-id="109a0-115">Specifies a comment for the group.</span></span>
<span data-ttu-id="109a0-116">Den maximala längden är 48 tecken.</span><span class="sxs-lookup"><span data-stu-id="109a0-116">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="109a0-117">-Name</span><span class="sxs-lookup"><span data-stu-id="109a0-117">-Name</span></span>
<span data-ttu-id="109a0-118">Anger ett namn för gruppen.</span><span class="sxs-lookup"><span data-stu-id="109a0-118">Specifies a name for the group.</span></span>
<span data-ttu-id="109a0-119">Den maximala längden är 256 tecken.</span><span class="sxs-lookup"><span data-stu-id="109a0-119">The maximum length is 256 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="109a0-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="109a0-120">-Confirm</span></span>
<span data-ttu-id="109a0-121">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="109a0-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="109a0-122">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="109a0-122">-WhatIf</span></span>
<span data-ttu-id="109a0-123">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="109a0-123">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="109a0-124">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="109a0-124">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="109a0-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="109a0-125">CommonParameters</span></span>
<span data-ttu-id="109a0-126">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="109a0-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="109a0-127">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="109a0-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="109a0-128">INDATA</span><span class="sxs-lookup"><span data-stu-id="109a0-128">INPUTS</span></span>

### <span data-ttu-id="109a0-129">System. String</span><span class="sxs-lookup"><span data-stu-id="109a0-129">System.String</span></span>
<span data-ttu-id="109a0-130">Du kan skicka vidare en sträng till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="109a0-130">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="109a0-131">UTDATA</span><span class="sxs-lookup"><span data-stu-id="109a0-131">OUTPUTS</span></span>

### <span data-ttu-id="109a0-132">System. Management. Automation. SecurityAccountsManager. LocalGroup</span><span class="sxs-lookup"><span data-stu-id="109a0-132">System.Management.Automation.SecurityAccountsManager.LocalGroup</span></span>
<span data-ttu-id="109a0-133">Den här cmdleten returnerar en säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="109a0-133">This cmdlet returns a security group.</span></span>

## <span data-ttu-id="109a0-134">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="109a0-134">NOTES</span></span>

* <span data-ttu-id="109a0-135">Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa.</span><span class="sxs-lookup"><span data-stu-id="109a0-135">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="109a0-136">De möjliga källorna är följande:</span><span class="sxs-lookup"><span data-stu-id="109a0-136">The possible sources are as follows:</span></span>

- <span data-ttu-id="109a0-137">Lokal</span><span class="sxs-lookup"><span data-stu-id="109a0-137">Local</span></span>
- <span data-ttu-id="109a0-138">Active Directory</span><span class="sxs-lookup"><span data-stu-id="109a0-138">Active Directory</span></span>
- <span data-ttu-id="109a0-139">Azure Active Directory grupp</span><span class="sxs-lookup"><span data-stu-id="109a0-139">Azure Active Directory group</span></span>
- <span data-ttu-id="109a0-140">Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="109a0-140">Microsoft Account</span></span>

<span data-ttu-id="109a0-141">**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="109a0-141">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="109a0-142">För tidigare versioner är egenskapen tom.</span><span class="sxs-lookup"><span data-stu-id="109a0-142">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="109a0-143">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="109a0-143">RELATED LINKS</span></span>

[<span data-ttu-id="109a0-144">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="109a0-144">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="109a0-145">Ta bort-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="109a0-145">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="109a0-146">Byt namn – lokal</span><span class="sxs-lookup"><span data-stu-id="109a0-146">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="109a0-147">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="109a0-147">Set-LocalGroup</span></span>](Set-LocalGroup.md)
