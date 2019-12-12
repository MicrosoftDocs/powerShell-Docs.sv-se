---
title: Anpassade värd exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357682"
---
# <a name="custom-host-samples"></a><span data-ttu-id="4f9b3-102">Exempel på anpassad värd</span><span class="sxs-lookup"><span data-stu-id="4f9b3-102">Custom Host Samples</span></span>

<span data-ttu-id="4f9b3-103">Det här avsnittet innehåller exempel kod för att skriva en anpassad värd.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="4f9b3-104">Du kan använda Microsoft Visual Studio för att skapa ett konsol program och sedan kopiera koden från ämnena i det här avsnittet till värd programmet.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4f9b3-105">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="4f9b3-105">In This Section</span></span>

 <span data-ttu-id="4f9b3-106">[Host01-exempel](./host01-sample.md) Det här exemplet visar hur du implementerar ett värd program som använder en grundläggande anpassad värd.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="4f9b3-107">[Host02-exempel](./host02-sample.md) Det här exemplet visar hur du skriver ett värd program som använder Windows PowerShell-körningsmiljön tillsammans med en anpassad värd implementering.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="4f9b3-108">Värd programmet ställer in värd kulturen på tyska, kör cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) och visar resultatet som du ser dem med hjälp av pwrsh. exe, och skriver sedan ut aktuella data och tid på tyska.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="4f9b3-109">[Host03-exempel](./host03-sample.md) Det här exemplet visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="4f9b3-110">[Host04-exempel](./host04-sample.md) Det här exemplet visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="4f9b3-111">Detta värd program har även stöd för att Visa prompter som gör att användaren kan ange flera alternativ.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="4f9b3-112">[Host05-exempel](./host05-sample.md) Det här exemplet visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="4f9b3-113">Detta värd program stöder även anrop till fjärrdatorer med hjälp av cmdletarna [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) och [exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession)</span><span class="sxs-lookup"><span data-stu-id="4f9b3-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="4f9b3-114">[Host06-exempel](./host06-sample.md) Det här exemplet visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="4f9b3-115">I det här exemplet används dessutom Tokenizer-API: er för att ange färgen på texten som anges av användaren.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f9b3-116">Se även</span><span class="sxs-lookup"><span data-stu-id="4f9b3-116">See Also</span></span>
