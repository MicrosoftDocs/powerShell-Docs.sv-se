---
ms.date: 2017-06-09
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptance
ms.openlocfilehash: 260ccc1ee52d09a640e88203c5644f20f9723d6f
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/11/2017
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="256fc-103">Moduler som kräver godkännande av licens</span><span class="sxs-lookup"><span data-stu-id="256fc-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="256fc-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="256fc-104">SYNOPSIS</span></span>
<span data-ttu-id="256fc-105">Juridiska avdelningar för vissa modulen utgivare kräva att kunder uttryckligen måste acceptera licensvillkoren innan du installerar sina modul från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="256fc-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="256fc-106">Om en användare installerar uppdateringar eller sparar en modul med PowerShellGet, direkt eller som ett beroende för ett annat objekt, och att modulen kräver att användaren godkänner du en licens, måste användaren ange de godkänner licensvillkoren, annars misslyckas åtgärden.</span><span class="sxs-lookup"><span data-stu-id="256fc-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another item, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="256fc-107">Publicera krav för moduler</span><span class="sxs-lookup"><span data-stu-id="256fc-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="256fc-108">Moduler som användarna ska acceptera licens ska uppfylla följande krav:</span><span class="sxs-lookup"><span data-stu-id="256fc-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>
    
- <span data-ttu-id="256fc-109">PSData avsnitt i modulmanifestet bör innehålla RequireLicenseAcceptance = $True.</span><span class="sxs-lookup"><span data-stu-id="256fc-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="256fc-110">Modulen bör innehålla filen license.txt i rotkatalogen.</span><span class="sxs-lookup"><span data-stu-id="256fc-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="256fc-111">Modulmanifestet bör innehålla licens Uri.</span><span class="sxs-lookup"><span data-stu-id="256fc-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="256fc-112">Modulen måste publiceras med PowerShellGet Format Version 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="256fc-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="256fc-113">Påverkan på Installera/Save/Update-modul</span><span class="sxs-lookup"><span data-stu-id="256fc-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="256fc-114">Cmdlets för installation-spara-uppdateringen stöder en ny parameter – AcceptLicense som fungerar som om användaren såg licensen.</span><span class="sxs-lookup"><span data-stu-id="256fc-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="256fc-115">Om RequiredLicenseAcceptance är True och – AcceptLicense har inte angetts, användaren ska visas license.txt och du får: &quot;godkänner du licensvillkoren (Ja/Nej/YesToAll/NoToAll)&quot;.</span><span class="sxs-lookup"><span data-stu-id="256fc-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="256fc-116">Om licensen godkänns</span><span class="sxs-lookup"><span data-stu-id="256fc-116">If the license is accepted</span></span>
    - <span data-ttu-id="256fc-117">**Spara-modul:** modulen ska kopieras till användaren &#39; s system</span><span class="sxs-lookup"><span data-stu-id="256fc-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="256fc-118">**Installera-modul:** modulen ska kopieras till användaren &#39; s system till rätt mapp (baserat på omfattningen)</span><span class="sxs-lookup"><span data-stu-id="256fc-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="256fc-119">**Update-modul:** modulen kommer att uppdateras.</span><span class="sxs-lookup"><span data-stu-id="256fc-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="256fc-120">Om licensen har nekats.</span><span class="sxs-lookup"><span data-stu-id="256fc-120">If the license is declined.</span></span> 
    - <span data-ttu-id="256fc-121">Åtgärden kommer att avbrytas.</span><span class="sxs-lookup"><span data-stu-id="256fc-121">Operation will be cancelled.</span></span>
- <span data-ttu-id="256fc-122">Alla cmdletar kommer att söka efter metadata (requireLicenseAcceptance och Format Version) där det står att ett godkännande av licens krävs</span><span class="sxs-lookup"><span data-stu-id="256fc-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
  - <span data-ttu-id="256fc-123">Om formatet för version av klienten är äldre än 2.0, misslyckas åtgärden och be användaren att uppdatera klienten.</span><span class="sxs-lookup"><span data-stu-id="256fc-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
  - <span data-ttu-id="256fc-124">Om modulen har publicerats med formatversion som är äldre än 2.0 ignoreras requireLicenseAcceptance flaggan.</span><span class="sxs-lookup"><span data-stu-id="256fc-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>

    
 ## <a name="module-dependencies"></a><span data-ttu-id="256fc-125">Modulen beroenden</span><span class="sxs-lookup"><span data-stu-id="256fc-125">Module Dependencies</span></span>
- <span data-ttu-id="256fc-126">Under installationen-spara-uppdateringen kommer igen om en beroende-modul (något annat beror på modulen) kräver godkännande av licens och sedan licens godkännande beteendet (ovan) att krävas.</span><span class="sxs-lookup"><span data-stu-id="256fc-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="256fc-127">Om modulversionen finns redan i den lokala katalogen som är installerad på systemet, skulle vi kringgå Licenskontroll.</span><span class="sxs-lookup"><span data-stu-id="256fc-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="256fc-128">Under installationen-spara-uppdateringen igen om en beroende modul kräver en licens och godkännande av licens inte genomförs åtgärden misslyckas och följa normala processer för objektet kunde inte installera-spara-uppdateringen.</span><span class="sxs-lookup"><span data-stu-id="256fc-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the item failed to install/save/update.</span></span>

 ## <a name="impact-on--force"></a><span data-ttu-id="256fc-129">Påverkan på - Force</span><span class="sxs-lookup"><span data-stu-id="256fc-129">Impact on -Force</span></span>

<span data-ttu-id="256fc-130">Ange – Force inte är tillräckliga för att godkänna en licens.</span><span class="sxs-lookup"><span data-stu-id="256fc-130">Specifying –Force is NOT sufficient to accept a license.</span></span> <span data-ttu-id="256fc-131">– AcceptLicense krävs för behörighet att installera.</span><span class="sxs-lookup"><span data-stu-id="256fc-131">–AcceptLicense is required for permission to install.</span></span> <span data-ttu-id="256fc-132">Om – Force anges RequiredLicenseAcceptance är True, och – AcceptLicense har inte angetts, misslyckas åtgärden.</span><span class="sxs-lookup"><span data-stu-id="256fc-132">If –Force is specified, RequiredLicenseAcceptance is True, and –AcceptLicense is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="256fc-133">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="256fc-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="256fc-134">Exempel 1: Uppdatera modulen Manifest att kräva godkännande av licens</span><span class="sxs-lookup"><span data-stu-id="256fc-134">Example 1: Update Module Manifest to require license acceptance</span></span>
```PowerShell
PS C:\> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable
    
 } # End of PrivateData hashtable
```
<span data-ttu-id="256fc-135">Det här kommandot uppdaterar manifestfilen och ställer in flaggan RequireLicenseAcceptance till true.</span><span class="sxs-lookup"><span data-stu-id="256fc-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>
### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="256fc-136">Exempel 2: Installera modulen som kräver godkännande av licens</span><span class="sxs-lookup"><span data-stu-id="256fc-136">Example 2: Install Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance

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
<span data-ttu-id="256fc-137">Det här kommandot visar licens från filen license.txt och uppmanar användaren att acceptera licensvillkoren.</span><span class="sxs-lookup"><span data-stu-id="256fc-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="256fc-138">Exempel 3: Installera modulen som kräver godkännande av licens med - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="256fc-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
<span data-ttu-id="256fc-139">Modulen installeras utan prompten att acceptera licens.</span><span class="sxs-lookup"><span data-stu-id="256fc-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="256fc-140">Exempel 4: Installera modulen som kräver godkännande av licens med - Force</span><span class="sxs-lookup"><span data-stu-id="256fc-140">Example 4: Install Module requiring license acceptance with -Force</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="256fc-141">Exempel 5: Installera modulen med beroenden som kräver godkännande av licens</span><span class="sxs-lookup"><span data-stu-id="256fc-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>
<span data-ttu-id="256fc-142">Modulen ModuleWithDependency beror på modulen 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="256fc-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="256fc-143">Användaren uppmanas att godkänna licens.</span><span class="sxs-lookup"><span data-stu-id="256fc-143">User is prompted to Accept License.</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleWithDependency

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="256fc-144">Exempel 6: Installera modulen med beroenden som kräver godkännande av licens och -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="256fc-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="256fc-145">Modulen ModuleWithDependency beror på modulen 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="256fc-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="256fc-146">Användaren uppmanas inte att godkänna licens eftersom - AcceptLicense har angetts.</span><span class="sxs-lookup"><span data-stu-id="256fc-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\>  Install-Module -Name ModuleWithDependency -AcceptLicense
```
### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="256fc-147">Exempel 7: Installera modulen som kräver godkännande av licens på en klient som är äldre än PSGetFormatVersion 2.0</span><span class="sxs-lookup"><span data-stu-id="256fc-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>
```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```
### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="256fc-148">Exempel 8: Spara modulen som kräver godkännande av licens</span><span class="sxs-lookup"><span data-stu-id="256fc-148">Example 8: Save Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

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
<span data-ttu-id="256fc-149">Det här kommandot visar licens från filen license.txt och uppmanar användaren att acceptera licensvillkoren.</span><span class="sxs-lookup"><span data-stu-id="256fc-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="256fc-150">Exempel 9: Spara modulen som kräver godkännande av licens med - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="256fc-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```
<span data-ttu-id="256fc-151">Modulen sparas utan någon tillfrågas om du vill acceptera licens.</span><span class="sxs-lookup"><span data-stu-id="256fc-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="256fc-152">Exempel 10: Uppdatera modulen som kräver godkännande av licens</span><span class="sxs-lookup"><span data-stu-id="256fc-152">Example 10: Update Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance

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
<span data-ttu-id="256fc-153">Det här kommandot visar licens från filen license.txt och uppmanar användaren att acceptera licensvillkoren.</span><span class="sxs-lookup"><span data-stu-id="256fc-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="256fc-154">Exempel 11: Uppdatera modulen som kräver godkännande av licens med - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="256fc-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
<span data-ttu-id="256fc-155">Modulen uppdateras utan någon tillfrågas om du vill acceptera licens.</span><span class="sxs-lookup"><span data-stu-id="256fc-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="256fc-156">Mer information</span><span class="sxs-lookup"><span data-stu-id="256fc-156">More details</span></span>
### <a name="require-license-acceptance-for-scriptsscriptscriptrequirelicenseacceptancemd"></a>[<span data-ttu-id="256fc-157">Kräv godkännande av licens för skript</span><span class="sxs-lookup"><span data-stu-id="256fc-157">Require License Acceptance for Scripts</span></span>](../script/script_RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="256fc-158">Kräv godkännande av licens-stöd på PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="256fc-158">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="256fc-159">Kräv godkännande av licens på Distribuera till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="256fc-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)
