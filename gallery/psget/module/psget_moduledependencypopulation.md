---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: psget_moduledependencypopulation
ms.openlocfilehash: c4c9f203e9c526ff532c2388acb6334515d66934
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a><span data-ttu-id="d4cfb-103">Logik för att förbereda modulen beroenden under publiceringen</span><span class="sxs-lookup"><span data-stu-id="d4cfb-103">Logic for preparing the module dependencies during Publish operation</span></span>
1.  <span data-ttu-id="d4cfb-104">Moduler som anges som en del av RequiredModules anses vara beroenden.</span><span class="sxs-lookup"><span data-stu-id="d4cfb-104">Modules listed as part of RequiredModules are considered as dependencies.</span></span>
2.  <span data-ttu-id="d4cfb-105">Moduler som anges som en del av NestedModules, vars bas som modulen inte är under den angivna modulen bas, betraktas som beroenden.</span><span class="sxs-lookup"><span data-stu-id="d4cfb-105">Modules listed as part of NestedModules, whose module base is not under the specified module base, are considered as dependencies.</span></span>

3.  <span data-ttu-id="d4cfb-106">Ovanstående beroenden måste finnas på samma måldatabasen, annars publicera åtgärden resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="d4cfb-106">Above dependencies should be available on the same target repository, otherwise publish operation will result in an error.</span></span>
    <span data-ttu-id="d4cfb-107">Exempel: om 'SnippetPx' inte är tillgänglig på databasen, nedan fel genereras.</span><span class="sxs-lookup"><span data-stu-id="d4cfb-107">For example: If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  <span data-ttu-id="d4cfb-108">Vissa modulen beroenden kan hanteras externt, i så fall de ska läggas till posten ExternalModuleDependencies i avsnittet PSData i modulmanifestet.</span><span class="sxs-lookup"><span data-stu-id="d4cfb-108">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>
    <span data-ttu-id="d4cfb-109">Under en del i ovanstående felmeddelande</span><span class="sxs-lookup"><span data-stu-id="d4cfb-109">Below part in the above error message</span></span>
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

<span data-ttu-id="d4cfb-110">*Under installationen av principmodulen ovan förberedda beroenden används listan för att installera beroenden.*</span><span class="sxs-lookup"><span data-stu-id="d4cfb-110">*During the module installation, above prepared dependencies list is used for installing the dependencies.*</span></span>

<span data-ttu-id="d4cfb-111">*Se till att din modulen beroenden är tillgängliga under $env: PSModulePath på datorn under publicera igen.*</span><span class="sxs-lookup"><span data-stu-id="d4cfb-111">*Please ensure that your module’s dependencies are available under $env:PSModulePath on your system during publish operation.*</span></span>