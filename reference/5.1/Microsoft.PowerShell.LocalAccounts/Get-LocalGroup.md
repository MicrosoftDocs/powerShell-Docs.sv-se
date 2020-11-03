---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroup
ms.openlocfilehash: 2cd77c2766840527825b0ccf68abaac3c2ea6c16
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263517"
---
# <span data-ttu-id="3d2ce-103">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="3d2ce-103">Get-LocalGroup</span></span>

## <span data-ttu-id="3d2ce-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3d2ce-104">SYNOPSIS</span></span>
<span data-ttu-id="3d2ce-105">Hämtar de lokala säkerhets grupperna.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-105">Gets the local security groups.</span></span>

## <span data-ttu-id="3d2ce-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3d2ce-106">SYNTAX</span></span>

### <span data-ttu-id="3d2ce-107">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="3d2ce-107">Default (Default)</span></span>

```
Get-LocalGroup [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="3d2ce-108">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="3d2ce-108">SecurityIdentifier</span></span>

```
Get-LocalGroup [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## <span data-ttu-id="3d2ce-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3d2ce-109">DESCRIPTION</span></span>
<span data-ttu-id="3d2ce-110">Cmdlet: en **Get-localgroup** hämtar lokala säkerhets grupper i Security Account Manager.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-110">The **Get-LocalGroup** cmdlet gets local security groups in Security Account Manager.</span></span>
<span data-ttu-id="3d2ce-111">Den här cmdleten hämtar inbyggda standard grupper och lokala säkerhets grupper som du skapar.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-111">This cmdlet gets default built-in groups and local security groups that you create.</span></span>

> [!NOTE]
> <span data-ttu-id="3d2ce-112">Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="3d2ce-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3d2ce-113">EXAMPLES</span></span>

### <span data-ttu-id="3d2ce-114">Exempel 1: Hämta gruppen Administratörer</span><span class="sxs-lookup"><span data-stu-id="3d2ce-114">Example 1: Get the Administrators group</span></span>

```
PS C:\> Get-LocalGroup -Name "Administrators"
Name           Description
----           -----------
Administrators Administrators have complete and unrestricted access to the computer/domain
```

<span data-ttu-id="3d2ce-115">Det här kommandot hämtar den lokala gruppen Administratörer.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-115">This command gets the local Administrators group.</span></span>
<span data-ttu-id="3d2ce-116">Kommandot visar egenskaper för gruppen i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-116">The command displays properties of the group in the console.</span></span>

## <span data-ttu-id="3d2ce-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3d2ce-117">PARAMETERS</span></span>

### <span data-ttu-id="3d2ce-118">-Name</span><span class="sxs-lookup"><span data-stu-id="3d2ce-118">-Name</span></span>
<span data-ttu-id="3d2ce-119">Anger en matris med namn på de säkerhets grupper som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-119">Specifies an array of names of security groups that this cmdlet gets.</span></span>
<span data-ttu-id="3d2ce-120">Du kan använda jokertecknet.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-120">You can use the wildcard character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3d2ce-121">-SID</span><span class="sxs-lookup"><span data-stu-id="3d2ce-121">-SID</span></span>
<span data-ttu-id="3d2ce-122">Anger en matris med säkerhets-ID: n (sid) för de säkerhets grupper som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-122">Specifies an array of security IDs (SIDs) of security groups that this cmdlet gets.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3d2ce-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3d2ce-123">CommonParameters</span></span>
<span data-ttu-id="3d2ce-124">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3d2ce-125">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3d2ce-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3d2ce-126">INDATA</span><span class="sxs-lookup"><span data-stu-id="3d2ce-126">INPUTS</span></span>

### <span data-ttu-id="3d2ce-127">System. String, system. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="3d2ce-127">System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="3d2ce-128">Du kan skicka en sträng eller en SID till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-128">You can pipe a string or a SID to this cmdlet.</span></span>

## <span data-ttu-id="3d2ce-129">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3d2ce-129">OUTPUTS</span></span>

### <span data-ttu-id="3d2ce-130">System. Management. Automation. SecurityAccountsManager. LocalGroup</span><span class="sxs-lookup"><span data-stu-id="3d2ce-130">System.Management.Automation.SecurityAccountsManager.LocalGroup</span></span>
<span data-ttu-id="3d2ce-131">Den här cmdleten returnerar en lokal grupp.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-131">This cmdlet returns a local group.</span></span>

## <span data-ttu-id="3d2ce-132">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3d2ce-132">NOTES</span></span>

* <span data-ttu-id="3d2ce-133">Egenskapen **PrincipalSource** är en egenskap för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekt som beskriver objektets källa.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-133">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="3d2ce-134">De möjliga källorna är följande:</span><span class="sxs-lookup"><span data-stu-id="3d2ce-134">The possible sources are as follows:</span></span>

- <span data-ttu-id="3d2ce-135">Lokal</span><span class="sxs-lookup"><span data-stu-id="3d2ce-135">Local</span></span>
- <span data-ttu-id="3d2ce-136">Active Directory</span><span class="sxs-lookup"><span data-stu-id="3d2ce-136">Active Directory</span></span>
- <span data-ttu-id="3d2ce-137">Azure Active Directory grupp</span><span class="sxs-lookup"><span data-stu-id="3d2ce-137">Azure Active Directory group</span></span>
- <span data-ttu-id="3d2ce-138">Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="3d2ce-138">Microsoft Account</span></span>

<span data-ttu-id="3d2ce-139">**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-139">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="3d2ce-140">För tidigare versioner är egenskapen tom.</span><span class="sxs-lookup"><span data-stu-id="3d2ce-140">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="3d2ce-141">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3d2ce-141">RELATED LINKS</span></span>

[<span data-ttu-id="3d2ce-142">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="3d2ce-142">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="3d2ce-143">Ta bort-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="3d2ce-143">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="3d2ce-144">Byt namn – lokal</span><span class="sxs-lookup"><span data-stu-id="3d2ce-144">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="3d2ce-145">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="3d2ce-145">Set-LocalGroup</span></span>](Set-LocalGroup.md)
