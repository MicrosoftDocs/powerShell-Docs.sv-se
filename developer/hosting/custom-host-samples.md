---
title: Anpassade Host-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794152"
---
# <a name="custom-host-samples"></a><span data-ttu-id="189d3-102">Exempel på anpassad värd</span><span class="sxs-lookup"><span data-stu-id="189d3-102">Custom Host Samples</span></span>

<span data-ttu-id="189d3-103">Det här avsnittet innehåller exempelkod för att skriva en egen värd.</span><span class="sxs-lookup"><span data-stu-id="189d3-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="189d3-104">Du kan använda Microsoft Visual Studio för att skapa ett konsolprogram och sedan kopiera koden från avsnitten i det här avsnittet i din värdapp.</span><span class="sxs-lookup"><span data-stu-id="189d3-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="189d3-105">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="189d3-105">In This Section</span></span>

 <span data-ttu-id="189d3-106">[Host01 exempel](./host01-sample.md) det här exemplet visas hur du implementerar ett program som använder en grundläggande anpassad värd.</span><span class="sxs-lookup"><span data-stu-id="189d3-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="189d3-107">[Host02 exempel](./host02-sample.md) det här exemplet visas hur du skriver ett program som använder Windows PowerShell-runtime tillsammans med implementering av anpassade värden.</span><span class="sxs-lookup"><span data-stu-id="189d3-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="189d3-108">Värdprogrammet anger kulturen värden till tyska, körs den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet och visar resultat som du ser dem med hjälp av pwrsh.exe och sedan visar du aktuella datum och tidpunkt på tyska.</span><span class="sxs-lookup"><span data-stu-id="189d3-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="189d3-109">[Host03 exempel](./host03-sample.md) i det här exemplet visar hur du skapar en interaktiv konsol-baserad värd-program som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen.</span><span class="sxs-lookup"><span data-stu-id="189d3-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="189d3-110">[Host04 exempel](./host04-sample.md) i det här exemplet visar hur du skapar en interaktiv konsol-baserad värd-program som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen.</span><span class="sxs-lookup"><span data-stu-id="189d3-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="189d3-111">Den här värdprogrammet stöder också med frågor som används att ange flera val.</span><span class="sxs-lookup"><span data-stu-id="189d3-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="189d3-112">[Host05 exempel](./host05-sample.md) i det här exemplet visar hur du skapar en interaktiv konsol-baserad värd-program som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen.</span><span class="sxs-lookup"><span data-stu-id="189d3-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="189d3-113">Den här värdprogrammet stöder också anrop till fjärrdatorer med hjälp av den [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) och [avsluta-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="189d3-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="189d3-114">[Host06 exempel](./host06-sample.md) i det här exemplet visar hur du skapar en interaktiv konsol-baserad värd-program som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen.</span><span class="sxs-lookup"><span data-stu-id="189d3-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="189d3-115">Det här exemplet använder dessutom Tokenizer-API: er för att ange färgen på texten som anges av användaren.</span><span class="sxs-lookup"><span data-stu-id="189d3-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="189d3-116">Se även</span><span class="sxs-lookup"><span data-stu-id="189d3-116">See Also</span></span>
