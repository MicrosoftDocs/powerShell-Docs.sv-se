---
title: RunSpace07 kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 55005a254ef50a2230121095770899cb3b9b70f1
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978239"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="5369f-102">RunSpace07 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="5369f-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="5369f-103">Här är käll koden för Runspace07-exemplet som beskrivs i [skapa ett konsol program som lägger till kommandon i en pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="5369f-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span>
<span data-ttu-id="5369f-104">Det här exempel programmet skapar en körnings utrymme, skapar en pipeline, lägger till två kommandon i pipelinen och kör sedan pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5369f-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="5369f-105">Kommandona som läggs till i pipelinen är `Get-Process`-och `Measure-Object`-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="5369f-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="5369f-106">Du kan ladda ned C# käll filen (runspace07.CS) med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="5369f-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5369f-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="5369f-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="5369f-108">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="5369f-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5369f-109">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="5369f-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs" range="11-108":::

## <a name="see-also"></a><span data-ttu-id="5369f-110">Se även</span><span class="sxs-lookup"><span data-stu-id="5369f-110">See Also</span></span>

[<span data-ttu-id="5369f-111">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="5369f-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5369f-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5369f-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
