---
title: Testa uppdaterbar hjälp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357430"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="637dc-102">Testa uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="637dc-102">How to Test Updatable Help</span></span>

<span data-ttu-id="637dc-103">I det här avsnittet beskrivs metoder för att testa uppdaterings bara hjälp för en modul.</span><span class="sxs-lookup"><span data-stu-id="637dc-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="637dc-104">Använda utförlig för att identifiera fel</span><span class="sxs-lookup"><span data-stu-id="637dc-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="637dc-105">När du har laddat upp XML-HelpInfo och CAB-filerna för modulen testar du filerna genom att köra ett [Update-Help-](/powershell/module/Microsoft.PowerShell.Core/Update-Help) kommando med **utförlig** parameter.</span><span class="sxs-lookup"><span data-stu-id="637dc-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="637dc-106">Den **utförliga** parametern dirigerar `Update-Help` för att rapportera de viktiga stegen i sina åtgärder, från att läsa nyckeln **HelpInfoUri** i modulen manifest för att validera filtyper i den uppackade CAB-filen och placera filerna i språkspecifika modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="637dc-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="637dc-107">När alla utförliga meddelanden har åtgärd ATS kör du ett `Update-Help`-kommando med **fel söknings** parametern.</span><span class="sxs-lookup"><span data-stu-id="637dc-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="637dc-108">Den här parametern ska identifiera eventuella återstående problem med de uppdateringsfiler som kan uppdateras.</span><span class="sxs-lookup"><span data-stu-id="637dc-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>