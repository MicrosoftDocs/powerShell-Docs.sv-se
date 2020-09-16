---
title: RunSpace07 kod exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 615bb237d26bf3a314ea7fb21e983ba2b000d105
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784715"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="5a6af-102">RunSpace07 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="5a6af-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="5a6af-103">Här är käll koden för Runspace07-exemplet som beskrivs i [skapa ett konsol program som lägger till kommandon i en pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="5a6af-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span>
<span data-ttu-id="5a6af-104">Det här exempel programmet skapar en körnings utrymme, skapar en pipeline, lägger till två kommandon i pipelinen och kör sedan pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5a6af-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="5a6af-105">Kommandona som läggs till i pipelinen är `Get-Process` `Measure-Object` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="5a6af-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="5a6af-106">Du kan hämta C#-källfilen (runspace07.cs) med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="5a6af-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5a6af-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="5a6af-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="5a6af-108">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="5a6af-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5a6af-109">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="5a6af-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs" range="11-108":::

## <a name="see-also"></a><span data-ttu-id="5a6af-110">Se även</span><span class="sxs-lookup"><span data-stu-id="5a6af-110">See Also</span></span>

[<span data-ttu-id="5a6af-111">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a6af-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5a6af-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5a6af-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
