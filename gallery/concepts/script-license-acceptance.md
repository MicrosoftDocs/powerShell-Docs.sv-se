---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Kräver godkännande av licensen för skript
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002590"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="ed188-103">Kräver godkännande av licensen för skript</span><span class="sxs-lookup"><span data-stu-id="ed188-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="ed188-104">Godkännande av licensen finns inte stöd för skript.</span><span class="sxs-lookup"><span data-stu-id="ed188-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="ed188-105">Ett scenario där ett skript beror på en modul som kräver godkännande av licensen stöds dock.</span><span class="sxs-lookup"><span data-stu-id="ed188-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="ed188-106">Skriptet commands(Install-Script/Save-Script/Update-Script) stöd för en ny parameter - AcceptLicense som fungerar som om användaren såg licensen.</span><span class="sxs-lookup"><span data-stu-id="ed188-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="ed188-107">Om inte anges - AcceptLicense; användaren ska visas license.txt för beroende modulen och du uppmanas att acceptera licensen.</span><span class="sxs-lookup"><span data-stu-id="ed188-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="ed188-108">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ed188-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="ed188-109">Exempel 1: Installationsskriptet med beroenden som kräver godkännande av licensen</span><span class="sxs-lookup"><span data-stu-id="ed188-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="ed188-110">Skriptet ScriptRequireLicenseAcceptance är beroende av modulen ”ModuleRequireLicenseAcceptance”.</span><span class="sxs-lookup"><span data-stu-id="ed188-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="ed188-111">Användaren uppmanas att acceptera licensen.</span><span class="sxs-lookup"><span data-stu-id="ed188-111">User is prompted to Accept License.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="ed188-112">Exempel 2: Installationsskriptet med beroenden som kräver godkännande av licensen och -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="ed188-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="ed188-113">Skriptet ScriptRequireLicenseAcceptance är beroende av modulen ”ModuleRequireLicenseAcceptance”.</span><span class="sxs-lookup"><span data-stu-id="ed188-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="ed188-114">Användaren behöver inte ange att acceptera licensen eftersom - AcceptLicense har angetts.</span><span class="sxs-lookup"><span data-stu-id="ed188-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="ed188-115">Mer information</span><span class="sxs-lookup"><span data-stu-id="ed188-115">More details</span></span>

- [<span data-ttu-id="ed188-116">Kräv godkännande av licensen stöd för moduler</span><span class="sxs-lookup"><span data-stu-id="ed188-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="ed188-117">Kräv godkännande av licensen stöd på PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="ed188-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [<span data-ttu-id="ed188-118">Kräv godkännande av licensen vid distribuera till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="ed188-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
