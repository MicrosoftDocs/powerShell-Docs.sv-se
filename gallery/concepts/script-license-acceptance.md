---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Att kräva godkännande av licens för skript
ms.openlocfilehash: 6374c8c8536dd0c8f27580a5b8895b8db18424f9
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34049015"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="72a1a-103">Att kräva godkännande av licens för skript</span><span class="sxs-lookup"><span data-stu-id="72a1a-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="72a1a-104">Godkännande av licens stöds inte för skript.</span><span class="sxs-lookup"><span data-stu-id="72a1a-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="72a1a-105">Ett scenario där ett skript som är beroende av en modul som kräver godkännande av licens stöds dock.</span><span class="sxs-lookup"><span data-stu-id="72a1a-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="72a1a-106">Skriptet commands(Install-Script/Save-Script/Update-Script) stöder en ny parameter - AcceptLicense som fungerar som om användaren såg licensen.</span><span class="sxs-lookup"><span data-stu-id="72a1a-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="72a1a-107">Om - AcceptLicense anges; användaren ska visas license.txt för beroende modulen och du uppmanas att acceptera licensvillkoren.</span><span class="sxs-lookup"><span data-stu-id="72a1a-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="72a1a-108">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="72a1a-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="72a1a-109">Exempel 1: Installationsskriptet med beroenden som kräver godkännande av licens</span><span class="sxs-lookup"><span data-stu-id="72a1a-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="72a1a-110">Skriptet ScriptRequireLicenseAcceptance beror på modulen 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="72a1a-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="72a1a-111">Användaren uppmanas att godkänna licens.</span><span class="sxs-lookup"><span data-stu-id="72a1a-111">User is prompted to Accept License.</span></span>

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="72a1a-112">Exempel 2: Installationsskriptet med beroenden som kräver godkännande av licens och -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="72a1a-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="72a1a-113">Skriptet ScriptRequireLicenseAcceptance beror på modulen 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="72a1a-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="72a1a-114">Användaren uppmanas inte att godkänna licens eftersom - AcceptLicense har angetts.</span><span class="sxs-lookup"><span data-stu-id="72a1a-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="72a1a-115">Mer information</span><span class="sxs-lookup"><span data-stu-id="72a1a-115">More details</span></span>

- [<span data-ttu-id="72a1a-116">Kräv godkännande av licens-stöd för moduler</span><span class="sxs-lookup"><span data-stu-id="72a1a-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="72a1a-117">Kräv godkännande av licens-stöd på PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="72a1a-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-items/items-that-require-license-acceptance.md)
- [<span data-ttu-id="72a1a-118">Kräv godkännande av licensen vid distribuera till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="72a1a-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-items/deploy-to-azure-automation.md)