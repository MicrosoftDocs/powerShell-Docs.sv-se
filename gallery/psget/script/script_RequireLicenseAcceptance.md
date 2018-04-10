---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 4a2dc39c2b6c380fb4ca94f9fd071ed9cdb35049
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="52cda-103">Att kräva godkännande av licens för skript</span><span class="sxs-lookup"><span data-stu-id="52cda-103">Requiring License Acceptance for Scripts</span></span>

<span data-ttu-id="52cda-104">Godkännande av licens stöds inte för skript.</span><span class="sxs-lookup"><span data-stu-id="52cda-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="52cda-105">Ett scenario där ett skript som är beroende av en modul som kräver godkännande av licens stöds dock.</span><span class="sxs-lookup"><span data-stu-id="52cda-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="52cda-106">Skriptet commands(Install-Script/Save-Script/Update-Script) stöder en ny parameter - AcceptLicense som fungerar som om användaren såg licensen.</span><span class="sxs-lookup"><span data-stu-id="52cda-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="52cda-107">Om - AcceptLicense anges; användaren ska visas license.txt för beroende modulen och du uppmanas att acceptera licensvillkoren.</span><span class="sxs-lookup"><span data-stu-id="52cda-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="52cda-108">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="52cda-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="52cda-109">Exempel 1: Installationsskriptet med beroenden som kräver godkännande av licens</span><span class="sxs-lookup"><span data-stu-id="52cda-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>
<span data-ttu-id="52cda-110">Skriptet ScriptRequireLicenseAcceptance beror på modulen 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="52cda-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="52cda-111">Användaren uppmanas att godkänna licens.</span><span class="sxs-lookup"><span data-stu-id="52cda-111">User is prompted to Accept License.</span></span>
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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="52cda-112">Exempel 2: Installationsskriptet med beroenden som kräver godkännande av licens och -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="52cda-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="52cda-113">Skriptet ScriptRequireLicenseAcceptance beror på modulen 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="52cda-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="52cda-114">Användaren uppmanas inte att godkänna licens eftersom - AcceptLicense har angetts.</span><span class="sxs-lookup"><span data-stu-id="52cda-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="52cda-115">Mer information</span><span class="sxs-lookup"><span data-stu-id="52cda-115">More details</span></span>
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[<span data-ttu-id="52cda-116">Kräv godkännande av licens-stöd för moduler</span><span class="sxs-lookup"><span data-stu-id="52cda-116">Require License Acceptance support for Modules</span></span>](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="52cda-117">Kräv godkännande av licens-stöd på PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="52cda-117">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="52cda-118">Kräv godkännande av licensen vid distribuera till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="52cda-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)