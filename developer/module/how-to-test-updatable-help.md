---
title: Så här testar du uppdateringsbar hjälp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: f2f319a3cab4b4bd91e9b634dda57d58a6476b62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845929"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="c6cb4-102">Testa uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="c6cb4-102">How to Test Updatable Help</span></span>

<span data-ttu-id="c6cb4-103">Det här avsnittet beskrivs metoder för att testa uppdateringsbar hjälp för en modul.</span><span class="sxs-lookup"><span data-stu-id="c6cb4-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="c6cb4-104">Med hjälp av utförlig identifiera fel</span><span class="sxs-lookup"><span data-stu-id="c6cb4-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="c6cb4-105">När du har överfört HelpInfo XML-filen och CAB-filer för att testa filerna genom att köra en [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) med den **utförlig** parametern.</span><span class="sxs-lookup"><span data-stu-id="c6cb4-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="c6cb4-106">Den **utförlig** parametern leder `Update-Help` att rapportera kritisk stegen i dess åtgärder, läser den **HelpInfoUri** nyckeln i modulmanifestet att validera filtyper i uppackat CAB-filen och placera filerna i modulkatalogen språkspecifika.</span><span class="sxs-lookup"><span data-stu-id="c6cb4-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>
<span data-ttu-id="c6cb4-107">När du har överfört HelpInfo XML-filen och CAB-filer för att testa filerna genom att köra en [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) med den **utförlig** parametern.</span><span class="sxs-lookup"><span data-stu-id="c6cb4-107">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="c6cb4-108">Den **utförlig** parametern leder `Update-Help` att rapportera kritisk stegen i dess åtgärder, läser den **HelpInfoUri** nyckeln i modulmanifestet att validera filtyper i uppackat CAB-filen och placera filerna i modulkatalogen språkspecifika.</span><span class="sxs-lookup"><span data-stu-id="c6cb4-108">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="c6cb4-109">När alla utförliga meddelanden är löst kör en `Update-Help` med den **felsöka** parametern.</span><span class="sxs-lookup"><span data-stu-id="c6cb4-109">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="c6cb4-110">Den här parametern ska identifiera eventuella återstående problem med uppdateringsbar hjälp-filer.</span><span class="sxs-lookup"><span data-stu-id="c6cb4-110">This parameter should detect any remaining problems with the Updatable Help files.</span></span>