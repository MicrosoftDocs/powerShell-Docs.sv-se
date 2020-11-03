---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 02/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedmodule?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledModule
ms.openlocfilehash: 199c257633a6d85a305a5155fdb4e61debcdf322
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266558"
---
# <span data-ttu-id="ffc29-103">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="ffc29-103">Get-InstalledModule</span></span>

## <span data-ttu-id="ffc29-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ffc29-104">SYNOPSIS</span></span>
<span data-ttu-id="ffc29-105">Hämtar en lista över moduler på den dator som har installerats av PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="ffc29-105">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

## <span data-ttu-id="ffc29-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ffc29-106">SYNTAX</span></span>

```
Get-InstalledModule [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="ffc29-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ffc29-107">DESCRIPTION</span></span>

<span data-ttu-id="ffc29-108">`Get-InstalledModule`Cmdlet: en hämtar PowerShell-moduler som är installerade på en dator med hjälp av PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="ffc29-108">The `Get-InstalledModule` cmdlet gets PowerShell modules that are installed on a computer using PowerShellGet.</span></span> <span data-ttu-id="ffc29-109">Om du vill se alla moduler som är installerade i systemet använder du `Get-Module -ListAvailable` kommandot.</span><span class="sxs-lookup"><span data-stu-id="ffc29-109">To see all modules installed on the system, use the `Get-Module -ListAvailable` command.</span></span>

## <span data-ttu-id="ffc29-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ffc29-110">EXAMPLES</span></span>

### <span data-ttu-id="ffc29-111">Exempel 1: Hämta alla installerade moduler</span><span class="sxs-lookup"><span data-stu-id="ffc29-111">Example 1: Get all installed modules</span></span>

```powershell
Get-InstalledModule
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
2.0.0      PSGTEST-UploadMultipleVersionOfP... Module     GalleryINT     Module for DAC functionality
1.3.5      AzureAutomationDebug                Module     PSGallery      Module for debugging Azure Automation runbooks, emulating AA native cmdlets
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="ffc29-112">Det här kommandot hämtar alla installerade moduler.</span><span class="sxs-lookup"><span data-stu-id="ffc29-112">This command gets all installed modules.</span></span>

### <span data-ttu-id="ffc29-113">Exempel 2: hämta vissa versioner av en modul</span><span class="sxs-lookup"><span data-stu-id="ffc29-113">Example 2: Get specific versions of a module</span></span>

```powershell
Get-InstalledModule -Name "AzureRM.Automation" -MinimumVersion 1.0 -MaximumVersion 2.0
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="ffc29-114">Detta kommando hämtar versioner av modulen AzureRM. Automation från version 1,0 till version 2,0.</span><span class="sxs-lookup"><span data-stu-id="ffc29-114">This command gets versions of the AzureRM.Automation module from version 1.0 through version 2.0.</span></span>

## <span data-ttu-id="ffc29-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ffc29-115">PARAMETERS</span></span>

### <span data-ttu-id="ffc29-116">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="ffc29-116">-AllowPrerelease</span></span>

<span data-ttu-id="ffc29-117">Innehåller i de resultat moduler som marker ATS som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="ffc29-117">Includes in the results modules marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ffc29-118">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="ffc29-118">-AllVersions</span></span>

<span data-ttu-id="ffc29-119">Anger att du vill hämta alla tillgängliga versioner av en modul.</span><span class="sxs-lookup"><span data-stu-id="ffc29-119">Indicates that you want to get all available versions of a module.</span></span>
<span data-ttu-id="ffc29-120">Du kan inte använda parametern **AllVersions** med parametrarna **MinimumVersion** , **MaximumVersion** eller **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="ffc29-120">You cannot use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ffc29-121">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="ffc29-121">-MaximumVersion</span></span>

<span data-ttu-id="ffc29-122">Anger den maximala eller nyaste versionen av en modul som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="ffc29-122">Specifies the maximum, or newest, version of a module to get.</span></span> <span data-ttu-id="ffc29-123">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="ffc29-123">The **MaximumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="ffc29-124">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="ffc29-124">-MinimumVersion</span></span>

<span data-ttu-id="ffc29-125">Anger den lägsta version av en enskild modul som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="ffc29-125">Specifies the minimum version of a single module to get.</span></span> <span data-ttu-id="ffc29-126">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="ffc29-126">The **MinimumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="ffc29-127">-Name</span><span class="sxs-lookup"><span data-stu-id="ffc29-127">-Name</span></span>

<span data-ttu-id="ffc29-128">Anger en matris med namn på moduler som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="ffc29-128">Specifies an array of names of modules to get.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ffc29-129">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="ffc29-129">-RequiredVersion</span></span>

<span data-ttu-id="ffc29-130">Anger den exakta version av en modul som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="ffc29-130">Specifies the exact version of a module to get.</span></span>

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

### <span data-ttu-id="ffc29-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ffc29-131">CommonParameters</span></span>

<span data-ttu-id="ffc29-132">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ffc29-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ffc29-133">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="ffc29-133">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ffc29-134">INDATA</span><span class="sxs-lookup"><span data-stu-id="ffc29-134">INPUTS</span></span>

### <span data-ttu-id="ffc29-135">System.String[]</span><span class="sxs-lookup"><span data-stu-id="ffc29-135">System.String[]</span></span>

### <span data-ttu-id="ffc29-136">System. String</span><span class="sxs-lookup"><span data-stu-id="ffc29-136">System.String</span></span>

## <span data-ttu-id="ffc29-137">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ffc29-137">OUTPUTS</span></span>

### <span data-ttu-id="ffc29-138">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="ffc29-138">System.Management.Automation.PSCustomObject</span></span>

## <span data-ttu-id="ffc29-139">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ffc29-139">NOTES</span></span>

## <span data-ttu-id="ffc29-140">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ffc29-140">RELATED LINKS</span></span>
