---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace07 – kodexempel
description: RunSpace07 – kodexempel
ms.openlocfilehash: 6e8c9f48a6e9c5a642ecf93bca8a85003b3cfbf8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647398"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="10b50-103">RunSpace07 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="10b50-103">RunSpace07 Code Sample</span></span>

<span data-ttu-id="10b50-104">Här är käll koden för Runspace07-exemplet som beskrivs i [skapa ett konsol program som lägger till kommandon i en pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="10b50-104">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span>
<span data-ttu-id="10b50-105">Det här exempel programmet skapar en körnings utrymme, skapar en pipeline, lägger till två kommandon i pipelinen och kör sedan pipelinen.</span><span class="sxs-lookup"><span data-stu-id="10b50-105">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="10b50-106">Kommandona som läggs till i pipelinen är `Get-Process` `Measure-Object` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="10b50-106">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="10b50-107">Du kan hämta C#-källfilen (runspace07.cs) med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="10b50-107">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="10b50-108">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="10b50-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="10b50-109">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="10b50-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="10b50-110">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="10b50-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs" range="11-108":::

## <a name="see-also"></a><span data-ttu-id="10b50-111">Se även</span><span class="sxs-lookup"><span data-stu-id="10b50-111">See Also</span></span>

[<span data-ttu-id="10b50-112">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="10b50-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="10b50-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="10b50-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
