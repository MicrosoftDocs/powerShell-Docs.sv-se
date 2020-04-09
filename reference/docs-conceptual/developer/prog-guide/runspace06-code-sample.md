---
title: RunSpace06 kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: d1d5e7f4096288ed09dada8eb8a61773921dc1ce
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978244"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="5feeb-102">RunSpace06 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="5feeb-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="5feeb-103">Här är käll koden för Runspace06-exemplet som beskrivs i [Konfigurera en körnings utrymme med hjälp av en Windows PowerShell-snapin-modul](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="5feeb-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span>
<span data-ttu-id="5feeb-104">Det här exempel programmet skapar en körnings utrymme baserat på en Windows PowerShell-snapin-modul, som sedan används för att köra en pipeline med ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="5feeb-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="5feeb-105">För att göra detta skapar programmet körnings utrymme konfigurations information, skapar en körnings utrymme, skapar en pipeline med ett enda kommando och kör sedan pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5feeb-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="5feeb-106">Du kan ladda ned C# käll filen (runspace06.CS) med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="5feeb-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5feeb-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="5feeb-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="5feeb-108">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="5feeb-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5feeb-109">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="5feeb-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs" range="11-85":::

## <a name="see-also"></a><span data-ttu-id="5feeb-110">Se även</span><span class="sxs-lookup"><span data-stu-id="5feeb-110">See Also</span></span>

[<span data-ttu-id="5feeb-111">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="5feeb-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5feeb-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5feeb-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
