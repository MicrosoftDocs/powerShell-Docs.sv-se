---
title: RunSpace06 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: b6fdad90f7339e941d77646936b1b5952cd65500
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734930"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="917c5-102">RunSpace06 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="917c5-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="917c5-103">Här är källkoden för Runspace06-exemplet som beskrivs i [konfigurerar ett Körningsutrymme som en Windows PowerShell snapin-modulen](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="917c5-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span> <span data-ttu-id="917c5-104">Det här exempelprogrammet skapar ett körningsutrymme baserat på en Windows PowerShell snapin-modul, som sedan används för att köra en pipeline med ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="917c5-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="917c5-105">Då programmet skapar runspace konfigurationsinformation, skapar ett körningsutrymme, skapas en pipeline med ett enda kommando och sedan körs pipelinen.</span><span class="sxs-lookup"><span data-stu-id="917c5-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="917c5-106">Du kan ladda ned den C# källfilen (runspace06.cs) med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="917c5-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="917c5-107">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="917c5-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="917c5-108">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="917c5-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="917c5-109">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="917c5-109">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="917c5-110">Se även</span><span class="sxs-lookup"><span data-stu-id="917c5-110">See Also</span></span>

[<span data-ttu-id="917c5-111">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="917c5-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="917c5-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="917c5-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)