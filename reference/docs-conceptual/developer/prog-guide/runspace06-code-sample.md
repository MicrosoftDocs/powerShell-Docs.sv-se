---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace06 – kodexempel
description: RunSpace06 – kodexempel
ms.openlocfilehash: 627fa2be51721dd8bfdd63fabdd2e6f286d593be
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667493"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="c875d-103">RunSpace06 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="c875d-103">RunSpace06 Code Sample</span></span>

<span data-ttu-id="c875d-104">Här är käll koden för Runspace06-exemplet som beskrivs i [Konfigurera en körnings utrymme med hjälp av en Windows PowerShell-snapin-modul](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="c875d-104">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span>
<span data-ttu-id="c875d-105">Det här exempel programmet skapar en körnings utrymme baserat på en Windows PowerShell-snapin-modul, som sedan används för att köra en pipeline med ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="c875d-105">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="c875d-106">För att göra detta skapar programmet körnings utrymme konfigurations information, skapar en körnings utrymme, skapar en pipeline med ett enda kommando och kör sedan pipelinen.</span><span class="sxs-lookup"><span data-stu-id="c875d-106">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="c875d-107">Du kan ladda ned C#-käll filen (runspace06.cs) med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="c875d-107">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c875d-108">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="c875d-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="c875d-109">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="c875d-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c875d-110">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="c875d-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs" range="11-85":::

## <a name="see-also"></a><span data-ttu-id="c875d-111">Se även</span><span class="sxs-lookup"><span data-stu-id="c875d-111">See Also</span></span>

[<span data-ttu-id="c875d-112">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c875d-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c875d-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c875d-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
