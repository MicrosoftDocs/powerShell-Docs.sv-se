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
ms.openlocfilehash: 8dd3770a60ca56634ad1eb1ac8cf89d96c975c90
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810829"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="0d66a-102">Testa uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="0d66a-102">How to Test Updatable Help</span></span>

<span data-ttu-id="0d66a-103">I det här avsnittet beskrivs metoder för att testa uppdaterings bara hjälp för en modul.</span><span class="sxs-lookup"><span data-stu-id="0d66a-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="0d66a-104">Använda utförlig för att identifiera fel</span><span class="sxs-lookup"><span data-stu-id="0d66a-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="0d66a-105">När du har laddat upp XML-HelpInfo och CAB-filerna för modulen testar du filerna genom att köra ett [Update-Help-](/powershell/module/Microsoft.PowerShell.Core/Update-Help) kommando med **utförlig** parameter.</span><span class="sxs-lookup"><span data-stu-id="0d66a-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="0d66a-106">Den **utförliga** parametern styrs `Update-Help` för att rapportera de viktiga stegen i sina åtgärder, från att läsa **HelpInfoUri** -nyckeln i modulen manifest för att validera filtyper i den uppackade CAB-filen och placera filerna i den språkspecifika modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="0d66a-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="0d66a-107">När alla utförliga meddelanden har åtgärd ATS kan du köra ett `Update-Help` kommando med **fel söknings** parametern.</span><span class="sxs-lookup"><span data-stu-id="0d66a-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="0d66a-108">Den här parametern ska identifiera eventuella återstående problem med de uppdateringsfiler som kan uppdateras.</span><span class="sxs-lookup"><span data-stu-id="0d66a-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>
