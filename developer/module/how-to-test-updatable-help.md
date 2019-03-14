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
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794271"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="e9bfd-102">Testa uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="e9bfd-102">How to Test Updatable Help</span></span>

<span data-ttu-id="e9bfd-103">Det här avsnittet beskrivs metoder för att testa uppdateringsbar hjälp för en modul.</span><span class="sxs-lookup"><span data-stu-id="e9bfd-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="e9bfd-104">Med hjälp av utförlig identifiera fel</span><span class="sxs-lookup"><span data-stu-id="e9bfd-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="e9bfd-105">När du har överfört HelpInfo XML-filen och CAB-filer för att testa filerna genom att köra en [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) med den **utförlig** parametern.</span><span class="sxs-lookup"><span data-stu-id="e9bfd-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="e9bfd-106">Den **utförlig** parametern leder `Update-Help` att rapportera kritisk stegen i dess åtgärder, läser den **HelpInfoUri** nyckeln i modulmanifestet att validera filtyper i uppackat CAB-filen och placera filerna i modulkatalogen språkspecifika.</span><span class="sxs-lookup"><span data-stu-id="e9bfd-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="e9bfd-107">När alla utförliga meddelanden är löst kör en `Update-Help` med den **felsöka** parametern.</span><span class="sxs-lookup"><span data-stu-id="e9bfd-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="e9bfd-108">Den här parametern ska identifiera eventuella återstående problem med uppdateringsbar hjälp-filer.</span><span class="sxs-lookup"><span data-stu-id="e9bfd-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>