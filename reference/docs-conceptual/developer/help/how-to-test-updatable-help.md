---
title: Testa uppdateringsbar hjälp
ms.date: 09/12/2016
ms.openlocfilehash: 0602349f853fddd0cadae545eaf0302c150e3a28
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892973"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="7cf98-102">Testa uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="7cf98-102">How to Test Updatable Help</span></span>

<span data-ttu-id="7cf98-103">I det här avsnittet beskrivs metoder för att testa uppdaterings bara hjälp för en modul.</span><span class="sxs-lookup"><span data-stu-id="7cf98-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="7cf98-104">Använda utförlig för att identifiera fel</span><span class="sxs-lookup"><span data-stu-id="7cf98-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="7cf98-105">När du har laddat upp XML-HelpInfo och CAB-filerna för modulen testar du filerna genom att köra ett [Update-Help-](/powershell/module/Microsoft.PowerShell.Core/Update-Help) kommando med **utförlig** parameter.</span><span class="sxs-lookup"><span data-stu-id="7cf98-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="7cf98-106">Den **utförliga** parametern styrs `Update-Help` för att rapportera de viktiga stegen i sina åtgärder, från att läsa **HelpInfoUri** -nyckeln i modulen manifest för att validera filtyper i den uppackade CAB-filen och placera filerna i den språkspecifika modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="7cf98-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="7cf98-107">När alla utförliga meddelanden har åtgärd ATS kan du köra ett `Update-Help` kommando med **fel söknings** parametern.</span><span class="sxs-lookup"><span data-stu-id="7cf98-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span>
<span data-ttu-id="7cf98-108">Den här parametern ska identifiera eventuella återstående problem med de uppdateringsfiler som kan uppdateras.</span><span class="sxs-lookup"><span data-stu-id="7cf98-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>
