---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 02/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedmodule?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledModule
ms.openlocfilehash: e894e2f71e0a76badd05b86b42903d49aab4af0b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264482"
---
# <span data-ttu-id="5b9b8-103">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="5b9b8-103">Get-InstalledModule</span></span>

## <span data-ttu-id="5b9b8-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5b9b8-104">SYNOPSIS</span></span>
<span data-ttu-id="5b9b8-105">Hämtar en lista över moduler på den dator som har installerats av PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-105">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

## <span data-ttu-id="5b9b8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5b9b8-106">SYNTAX</span></span>

```
Get-InstalledModule [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="5b9b8-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5b9b8-107">DESCRIPTION</span></span>

<span data-ttu-id="5b9b8-108">`Get-InstalledModule`Cmdlet: en hämtar PowerShell-moduler som är installerade på en dator med hjälp av PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-108">The `Get-InstalledModule` cmdlet gets PowerShell modules that are installed on a computer using PowerShellGet.</span></span> <span data-ttu-id="5b9b8-109">Om du vill se alla moduler som är installerade i systemet använder du `Get-Module -ListAvailable` kommandot.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-109">To see all modules installed on the system, use the `Get-Module -ListAvailable` command.</span></span>

## <span data-ttu-id="5b9b8-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5b9b8-110">EXAMPLES</span></span>

### <span data-ttu-id="5b9b8-111">Exempel 1: Hämta alla installerade moduler</span><span class="sxs-lookup"><span data-stu-id="5b9b8-111">Example 1: Get all installed modules</span></span>

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

<span data-ttu-id="5b9b8-112">Det här kommandot hämtar alla installerade moduler.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-112">This command gets all installed modules.</span></span>

### <span data-ttu-id="5b9b8-113">Exempel 2: hämta vissa versioner av en modul</span><span class="sxs-lookup"><span data-stu-id="5b9b8-113">Example 2: Get specific versions of a module</span></span>

```powershell
Get-InstalledModule -Name "AzureRM.Automation" -MinimumVersion 1.0 -MaximumVersion 2.0
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="5b9b8-114">Detta kommando hämtar versioner av modulen AzureRM. Automation från version 1,0 till version 2,0.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-114">This command gets versions of the AzureRM.Automation module from version 1.0 through version 2.0.</span></span>

## <span data-ttu-id="5b9b8-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5b9b8-115">PARAMETERS</span></span>

### <span data-ttu-id="5b9b8-116">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="5b9b8-116">-AllowPrerelease</span></span>

<span data-ttu-id="5b9b8-117">Innehåller i de resultat moduler som marker ATS som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-117">Includes in the results modules marked as a prerelease.</span></span>

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

### <span data-ttu-id="5b9b8-118">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="5b9b8-118">-AllVersions</span></span>

<span data-ttu-id="5b9b8-119">Anger att du vill hämta alla tillgängliga versioner av en modul.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-119">Indicates that you want to get all available versions of a module.</span></span>
<span data-ttu-id="5b9b8-120">Du kan inte använda parametern **AllVersions** med parametrarna **MinimumVersion** , **MaximumVersion** eller **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="5b9b8-120">You cannot use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="5b9b8-121">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="5b9b8-121">-MaximumVersion</span></span>

<span data-ttu-id="5b9b8-122">Anger den maximala eller nyaste versionen av en modul som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-122">Specifies the maximum, or newest, version of a module to get.</span></span> <span data-ttu-id="5b9b8-123">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-123">The **MaximumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="5b9b8-124">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="5b9b8-124">-MinimumVersion</span></span>

<span data-ttu-id="5b9b8-125">Anger den lägsta version av en enskild modul som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-125">Specifies the minimum version of a single module to get.</span></span> <span data-ttu-id="5b9b8-126">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-126">The **MinimumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="5b9b8-127">-Name</span><span class="sxs-lookup"><span data-stu-id="5b9b8-127">-Name</span></span>

<span data-ttu-id="5b9b8-128">Anger en matris med namn på moduler som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-128">Specifies an array of names of modules to get.</span></span>

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

### <span data-ttu-id="5b9b8-129">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="5b9b8-129">-RequiredVersion</span></span>

<span data-ttu-id="5b9b8-130">Anger den exakta version av en modul som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-130">Specifies the exact version of a module to get.</span></span>

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

### <span data-ttu-id="5b9b8-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5b9b8-131">CommonParameters</span></span>

<span data-ttu-id="5b9b8-132">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5b9b8-133">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="5b9b8-133">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5b9b8-134">INDATA</span><span class="sxs-lookup"><span data-stu-id="5b9b8-134">INPUTS</span></span>

## <span data-ttu-id="5b9b8-135">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5b9b8-135">OUTPUTS</span></span>

### <span data-ttu-id="5b9b8-136">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="5b9b8-136">System.Management.Automation.PSCustomObject</span></span>

## <span data-ttu-id="5b9b8-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5b9b8-137">NOTES</span></span>

## <span data-ttu-id="5b9b8-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5b9b8-138">RELATED LINKS</span></span>
