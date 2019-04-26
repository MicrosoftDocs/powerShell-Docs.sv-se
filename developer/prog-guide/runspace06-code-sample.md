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
ms.openlocfilehash: d0330f082262b68486a582ed95c7a520be1e184c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081316"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="bdf7c-102">RunSpace06 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="bdf7c-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="bdf7c-103">Här är källkoden för Runspace06-exemplet som beskrivs i [konfigurerar ett Körningsutrymme som en Windows PowerShell snapin-modulen](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="bdf7c-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span> <span data-ttu-id="bdf7c-104">Det här exempelprogrammet skapar ett körningsutrymme baserat på en Windows PowerShell snapin-modul, som sedan används för att köra en pipeline med ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="bdf7c-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="bdf7c-105">Då programmet skapar runspace konfigurationsinformation, skapar ett körningsutrymme, skapas en pipeline med ett enda kommando och sedan körs pipelinen.</span><span class="sxs-lookup"><span data-stu-id="bdf7c-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="bdf7c-106">Du kan ladda ned den C# källfilen (runspace06.cs) med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="bdf7c-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="bdf7c-107">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="bdf7c-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="bdf7c-108">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="bdf7c-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="bdf7c-109">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="bdf7c-109">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="bdf7c-110">Se även</span><span class="sxs-lookup"><span data-stu-id="bdf7c-110">See Also</span></span>

[<span data-ttu-id="bdf7c-111">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bdf7c-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="bdf7c-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="bdf7c-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)