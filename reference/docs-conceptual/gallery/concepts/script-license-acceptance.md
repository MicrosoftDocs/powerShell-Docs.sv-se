---
ms.date: 06/09/2017
title: Kräver godkännande av licens för skript
description: Artikeln förklarar hur du arbetar med skript som publicerats i PowerShell-galleriet som kräver godkännande av en slut användar licens.
ms.openlocfilehash: d82974810fd1e73ef8d9e5771fc430d0f7964e87
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656085"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="80ae8-103">Kräver godkännande av licens för skript</span><span class="sxs-lookup"><span data-stu-id="80ae8-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="80ae8-104">Licens godkännande stöds inte för skript.</span><span class="sxs-lookup"><span data-stu-id="80ae8-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="80ae8-105">Scenariot där ett skript är beroende av en modul som kräver godkännande av licenser stöds dock.</span><span class="sxs-lookup"><span data-stu-id="80ae8-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="80ae8-106">Skript kommandona PowerShellGet stöder parametern **AcceptLicense** som beter sig som om användaren såg licensen.</span><span class="sxs-lookup"><span data-stu-id="80ae8-106">The PowerShellGet script commands support the parameter **AcceptLicense** that behaves as though user saw the license.</span></span> <span data-ttu-id="80ae8-107">Om **AcceptLicense** inte anges visas `license.txt` filen för en beroende modul och du uppmanas att godkänna licensen.</span><span class="sxs-lookup"><span data-stu-id="80ae8-107">If **AcceptLicense** is not specified the user is shown the `license.txt` file for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="80ae8-108">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="80ae8-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="80ae8-109">Exempel 1: installera skript med beroenden som kräver licens godkännande</span><span class="sxs-lookup"><span data-stu-id="80ae8-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="80ae8-110">Skriptet ' ScriptRequireLicenseAcceptance ' är beroende av modulen ' ModuleRequireLicenseAcceptance '.</span><span class="sxs-lookup"><span data-stu-id="80ae8-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="80ae8-111">Användaren uppmanas att godkänna licens.</span><span class="sxs-lookup"><span data-stu-id="80ae8-111">User is prompted to Accept License.</span></span>

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="80ae8-112">Exempel 2: installera skript med beroenden som kräver licens godkännande och-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="80ae8-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="80ae8-113">Skriptet ' ScriptRequireLicenseAcceptance ' är beroende av modulen ' ModuleRequireLicenseAcceptance '.</span><span class="sxs-lookup"><span data-stu-id="80ae8-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="80ae8-114">Användaren uppmanas inte att godkänna licensen eftersom-AcceptLicense har angetts.</span><span class="sxs-lookup"><span data-stu-id="80ae8-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="80ae8-115">Mer information</span><span class="sxs-lookup"><span data-stu-id="80ae8-115">More details</span></span>

- [<span data-ttu-id="80ae8-116">Kräv support för licens godkännande för moduler</span><span class="sxs-lookup"><span data-stu-id="80ae8-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="80ae8-117">Kräv support för licens godkännande på PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="80ae8-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [<span data-ttu-id="80ae8-118">Kräv godkännande av licensen vid distribuera till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="80ae8-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
