---
title: RunSpace07 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 3e016b0e98234797afc8f303a55919228eaf8829
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848162"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="2011d-102">RunSpace07 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="2011d-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="2011d-103">Här är källkoden för Runspace07-exemplet som beskrivs i [skapar ett program som lägger till konsolkommandon för en Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="2011d-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="2011d-104">Det här exempelprogrammet skapar ett körningsutrymme, skapas en pipeline, lägger till två kommandon i pipelinen och sedan körs pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2011d-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="2011d-105">Kommandona läggs till i pipeline är den `Get-Process` och `Measure-Object` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="2011d-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="2011d-106">Du kan ladda ned den C# källfilen (runspace07.cs) med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="2011d-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2011d-107">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2011d-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="2011d-108">Du kan ladda ned den C# källfilen (runspace07.cs) med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="2011d-108">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2011d-109">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2011d-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="2011d-110">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="2011d-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="2011d-111">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="2011d-111">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="2011d-112">Se även</span><span class="sxs-lookup"><span data-stu-id="2011d-112">See Also</span></span>

[<span data-ttu-id="2011d-113">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2011d-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2011d-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2011d-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)