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
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a>Logik för att förbereda modulen beroenden under publiceringen
1.  Moduler som anges som en del av RequiredModules anses vara beroenden.
2.  Moduler som anges som en del av NestedModules, vars bas som modulen inte är under den angivna modulen bas, betraktas som beroenden.

3.  Ovanstående beroenden måste finnas på samma måldatabasen, annars publicera åtgärden resulterar i ett fel.
    Exempel: om 'SnippetPx' inte är tillgänglig på databasen, nedan fel genereras.
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  Vissa modulen beroenden kan hanteras externt, i så fall de ska läggas till posten ExternalModuleDependencies i avsnittet PSData i modulmanifestet.
    Under en del i ovanstående felmeddelande
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

*Under installationen av principmodulen ovan förberedda beroenden används listan för att installera beroenden.*

*Se till att din modulen beroenden är tillgängliga under $env: PSModulePath på datorn under publicera igen.*