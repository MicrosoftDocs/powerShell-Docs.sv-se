---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Moduler som kräver godkännande av licensen
ms.openlocfilehash: 369e32d5278a2e1bf1d3f2ae67f670c524b9f878
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71329206"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="17e10-103">Moduler som kräver godkännande av licensen</span><span class="sxs-lookup"><span data-stu-id="17e10-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="17e10-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="17e10-104">SYNOPSIS</span></span>

<span data-ttu-id="17e10-105">Juridiska avdelningar för vissa module-utgivare kräver att kunderna uttryckligen accepterar licensen innan de installerar sin modul från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="17e10-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="17e10-106">Om en användare installerar, uppdaterar eller sparar en modul med PowerShellGet, oavsett om det är direkt eller som ett beroende för ett annat paket, och den modulen kräver att användaren godkänner en licens, måste användaren ange att den accepterar licensen eller att åtgärden Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="17e10-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another package, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="17e10-107">Publicera krav för moduler</span><span class="sxs-lookup"><span data-stu-id="17e10-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="17e10-108">Moduler som vill kräva att användare accepterar licens bör uppfylla följande krav:</span><span class="sxs-lookup"><span data-stu-id="17e10-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="17e10-109">PSData-avsnittet av modulens manifest bör innehålla RequireLicenseAcceptance = $True.</span><span class="sxs-lookup"><span data-stu-id="17e10-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="17e10-110">Modulen bör innehålla filen License. txt i rot katalogen.</span><span class="sxs-lookup"><span data-stu-id="17e10-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="17e10-111">Module-manifestet ska innehålla licens-URI.</span><span class="sxs-lookup"><span data-stu-id="17e10-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="17e10-112">Modulen bör publiceras med PowerShellGet-format version 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="17e10-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="17e10-113">Inverkan på installation/Spara/uppdatera-modul</span><span class="sxs-lookup"><span data-stu-id="17e10-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="17e10-114">Installera/Spara/uppdatera cmdletar har stöd för en ny parameter – AcceptLicense som kommer att fungera som om användaren såg licensen.</span><span class="sxs-lookup"><span data-stu-id="17e10-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="17e10-115">Om RequiredLicenseAcceptance är sant och – AcceptLicense inte har angetts visas License. txt i användaren och du uppmanas att göra följande: &quot;godkänner du licens villkoren (Ja/Nej/YesToAll/NoToAll)&quot;.</span><span class="sxs-lookup"><span data-stu-id="17e10-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="17e10-116">Om licensen accepteras</span><span class="sxs-lookup"><span data-stu-id="17e10-116">If the license is accepted</span></span>
    - <span data-ttu-id="17e10-117">**Spara-modul:** modulen kommer att kopieras till användarens&#39;system</span><span class="sxs-lookup"><span data-stu-id="17e10-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="17e10-118">**Installera-modul:** modulen kommer att kopieras till användarens&#39;system till rätt mapp (baserat på omfång)</span><span class="sxs-lookup"><span data-stu-id="17e10-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="17e10-119">**Update-modul:** modulen kommer att uppdateras.</span><span class="sxs-lookup"><span data-stu-id="17e10-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="17e10-120">Om licensen nekas.</span><span class="sxs-lookup"><span data-stu-id="17e10-120">If the license is declined.</span></span>
    - <span data-ttu-id="17e10-121">Åtgärden avbryts.</span><span class="sxs-lookup"><span data-stu-id="17e10-121">Operation will be cancelled.</span></span>
    - <span data-ttu-id="17e10-122">Alla cmdletar söker efter de metadata (requireLicenseAcceptance och format version) som säger att ett licens godkännande krävs</span><span class="sxs-lookup"><span data-stu-id="17e10-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
    - <span data-ttu-id="17e10-123">Om format versionen av klienten är äldre än 2,0 Miss söker åtgärden och ber användaren att uppdatera klienten.</span><span class="sxs-lookup"><span data-stu-id="17e10-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
    - <span data-ttu-id="17e10-124">Om modulen publicerades med format version som är äldre än 2,0 ignoreras flaggan requireLicenseAcceptance.</span><span class="sxs-lookup"><span data-stu-id="17e10-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>

## <a name="module-dependencies"></a><span data-ttu-id="17e10-125">Modul-beroenden</span><span class="sxs-lookup"><span data-stu-id="17e10-125">Module Dependencies</span></span>

- <span data-ttu-id="17e10-126">Om en beroende modul (något annat är beroende av modulen) krävs för att installera/Spara/uppdatera, krävs licens godkännande, vilket innebär att licens godkännande beteendet (ovan) krävs.</span><span class="sxs-lookup"><span data-stu-id="17e10-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="17e10-127">Om modulnamnet redan visas i den lokala katalogen som installeras i systemet skulle vi kringgå licens kontrollen.</span><span class="sxs-lookup"><span data-stu-id="17e10-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="17e10-128">Vid installation/sparande/uppdatering, om en beroende modul kräver en licens, och licens godkännandet inte inträffar, kommer åtgärden att Miss lyckas och följa vanliga processer för paketet det gick inte att installera/Spara/uppdatera.</span><span class="sxs-lookup"><span data-stu-id="17e10-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the package failed to install/save/update.</span></span>

## <a name="impact-on--force"></a><span data-ttu-id="17e10-129">Påverkan på Force</span><span class="sxs-lookup"><span data-stu-id="17e10-129">Impact on -Force</span></span>

<span data-ttu-id="17e10-130">Det räcker inte att ange `–Force` för att godkänna en licens.</span><span class="sxs-lookup"><span data-stu-id="17e10-130">Specifying `–Force` is NOT sufficient to accept a license.</span></span> <span data-ttu-id="17e10-131">`–AcceptLicense` krävs för att du ska kunna installera.</span><span class="sxs-lookup"><span data-stu-id="17e10-131">`–AcceptLicense` is required for permission to install.</span></span> <span data-ttu-id="17e10-132">Om `–Force` anges är RequiredLicenseAcceptance sant och `–AcceptLicense` inte har angetts, kommer åtgärden att Miss läge.</span><span class="sxs-lookup"><span data-stu-id="17e10-132">If `–Force` is specified, RequiredLicenseAcceptance is True, and `–AcceptLicense` is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="17e10-133">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="17e10-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="17e10-134">Exempel 1: uppdatera modul manifest för att kräva licens godkännande</span><span class="sxs-lookup"><span data-stu-id="17e10-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="17e10-135">Detta kommando uppdaterar manifest filen och anger flaggan RequireLicenseAcceptance till true.</span><span class="sxs-lookup"><span data-stu-id="17e10-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="17e10-136">Exempel 2: installera modul som kräver licens godkännande</span><span class="sxs-lookup"><span data-stu-id="17e10-136">Example 2: Install Module requiring license acceptance</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="17e10-137">Det här kommandot visar licensen från filen License. txt och användaren måste godkänna licensen.</span><span class="sxs-lookup"><span data-stu-id="17e10-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="17e10-138">Exempel 3: installera modul som kräver licens godkännande med-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="17e10-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="17e10-139">Modulen installeras utan att du behöver ange en licens för att godkänna licens.</span><span class="sxs-lookup"><span data-stu-id="17e10-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="17e10-140">Exempel 4: installera modul som kräver licens godkännande med-force</span><span class="sxs-lookup"><span data-stu-id="17e10-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="17e10-141">Exempel 5: installera modulen med beroenden som kräver licens godkännande</span><span class="sxs-lookup"><span data-stu-id="17e10-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="17e10-142">Modulen ' ModuleWithDependency ' är beroende av modulen ' ModuleRequireLicenseAcceptance '.</span><span class="sxs-lookup"><span data-stu-id="17e10-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="17e10-143">Användaren uppmanas att godkänna licens.</span><span class="sxs-lookup"><span data-stu-id="17e10-143">User is prompted to Accept License.</span></span>

```powershell
Install-Module -Name ModuleWithDependency
```

```output
License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="17e10-144">Exempel 6: installera modulen med beroenden som kräver licens godkännande och-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="17e10-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="17e10-145">Modulen ' ModuleWithDependency ' är beroende av modulen ' ModuleRequireLicenseAcceptance '.</span><span class="sxs-lookup"><span data-stu-id="17e10-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="17e10-146">Användaren uppmanas inte att godkänna licensen eftersom-AcceptLicense har angetts.</span><span class="sxs-lookup"><span data-stu-id="17e10-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="17e10-147">Exempel 7: installera modul som kräver licens godkännande på en klient som är äldre än PSGetFormatVersion 2,0</span><span class="sxs-lookup"><span data-stu-id="17e10-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="17e10-148">Exempel 8: Spara modul som kräver licens godkännande</span><span class="sxs-lookup"><span data-stu-id="17e10-148">Example 8: Save Module requiring license acceptance</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="17e10-149">Det här kommandot visar licensen från filen License. txt och användaren måste godkänna licensen.</span><span class="sxs-lookup"><span data-stu-id="17e10-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="17e10-150">Exempel 9: Spara modul som kräver licens godkännande med-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="17e10-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="17e10-151">Modulen sparas utan att du behöver ange en licens för att godkänna licensen.</span><span class="sxs-lookup"><span data-stu-id="17e10-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="17e10-152">Exempel 10: Update-modulen som kräver licens godkännande</span><span class="sxs-lookup"><span data-stu-id="17e10-152">Example 10: Update Module requiring license acceptance</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="17e10-153">Det här kommandot visar licensen från filen License. txt och användaren måste godkänna licensen.</span><span class="sxs-lookup"><span data-stu-id="17e10-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="17e10-154">Exempel 11: Update-modulen som kräver licens godkännande med-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="17e10-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="17e10-155">Modulen uppdateras utan att du behöver ange en licens för att godkänna licens.</span><span class="sxs-lookup"><span data-stu-id="17e10-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="17e10-156">Mer information</span><span class="sxs-lookup"><span data-stu-id="17e10-156">More details</span></span>

[<span data-ttu-id="17e10-157">Kräv godkännande av licensen för skript</span><span class="sxs-lookup"><span data-stu-id="17e10-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

[<span data-ttu-id="17e10-158">Kräv support för licens godkännande på PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="17e10-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[<span data-ttu-id="17e10-159">Kräv godkännande av licensen vid distribuera till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="17e10-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
