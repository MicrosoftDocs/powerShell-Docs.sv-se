---
ms.date: 2017-06-09
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 7092fb2e63b9e2b1eca59cd418317631bff8b172
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/11/2017
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="8d8d7-103">Att kräva godkännande av licens för skript</span><span class="sxs-lookup"><span data-stu-id="8d8d7-103">Requiring License Acceptance for Scripts</span></span>

<span data-ttu-id="8d8d7-104">Godkännande av licens stöds inte för skript.</span><span class="sxs-lookup"><span data-stu-id="8d8d7-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="8d8d7-105">Ett scenario där ett skript som är beroende av en modul som kräver godkännande av licens stöds dock.</span><span class="sxs-lookup"><span data-stu-id="8d8d7-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="8d8d7-106">Skriptet commands(Install-Script/Save-Script/Update-Script) stöder en ny parameter - AcceptLicense som fungerar som om användaren såg licensen.</span><span class="sxs-lookup"><span data-stu-id="8d8d7-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="8d8d7-107">Om - AcceptLicense anges; användaren ska visas license.txt för beroende modulen och du uppmanas att acceptera licensvillkoren.</span><span class="sxs-lookup"><span data-stu-id="8d8d7-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="8d8d7-108">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8d8d7-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="8d8d7-109">Exempel 1: Installationsskriptet med beroenden som kräver godkännande av licens</span><span class="sxs-lookup"><span data-stu-id="8d8d7-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>
<span data-ttu-id="8d8d7-110">Skriptet ScriptRequireLicenseAcceptance beror på modulen 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="8d8d7-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="8d8d7-111">Användaren uppmanas att godkänna licens.</span><span class="sxs-lookup"><span data-stu-id="8d8d7-111">User is prompted to Accept License.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="8d8d7-112">Exempel 2: Installationsskriptet med beroenden som kräver godkännande av licens och -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="8d8d7-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="8d8d7-113">Skriptet ScriptRequireLicenseAcceptance beror på modulen 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="8d8d7-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="8d8d7-114">Användaren uppmanas inte att godkänna licens eftersom - AcceptLicense har angetts.</span><span class="sxs-lookup"><span data-stu-id="8d8d7-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="8d8d7-115">Mer information</span><span class="sxs-lookup"><span data-stu-id="8d8d7-115">More details</span></span>
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[<span data-ttu-id="8d8d7-116">Kräv godkännande av licens-stöd för moduler</span><span class="sxs-lookup"><span data-stu-id="8d8d7-116">Require License Acceptance support for Modules</span></span>](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="8d8d7-117">Kräv godkännande av licens-stöd på PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="8d8d7-117">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="8d8d7-118">Kräv godkännande av licens på Distribuera till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="8d8d7-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)
