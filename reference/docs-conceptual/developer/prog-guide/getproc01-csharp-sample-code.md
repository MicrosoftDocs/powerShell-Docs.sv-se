---
title: GetProc01 (C#) exempel kod | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 71ba68521ed8d26d0c85169d2b0d547cc6d2d5e3
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978432"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="0cbc8-102">GetProc01 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="0cbc8-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="0cbc8-103">Följande kod visar implementeringen av GetProc01-exempel-cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="0cbc8-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="0cbc8-104">Observera att cmdleten är förenklad genom att lämna det faktiska arbetet med process hämtning till metoden [system. Diagnostics. process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) .</span><span class="sxs-lookup"><span data-stu-id="0cbc8-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="0cbc8-105">Du kan ladda ned C# käll filen (getproc01.CS) för den här get-proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="0cbc8-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0cbc8-106">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="0cbc8-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="0cbc8-107">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="0cbc8-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0cbc8-108">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="0cbc8-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a><span data-ttu-id="0cbc8-109">Se även</span><span class="sxs-lookup"><span data-stu-id="0cbc8-109">See Also</span></span>

[<span data-ttu-id="0cbc8-110">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="0cbc8-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0cbc8-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0cbc8-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
