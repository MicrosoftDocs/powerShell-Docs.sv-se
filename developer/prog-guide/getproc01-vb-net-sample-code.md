---
title: GetProc01 (VB.NET) exempelkoden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ee87f67-6d2c-48cc-b300-3ae917c6dc88
caps.latest.revision: 5
ms.openlocfilehash: 2411642c39737e7dc03bd0bb4ea753ed27783732
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081809"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="b7d67-102">GetProc01 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="b7d67-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="b7d67-103">Följande kod visar implementeringen av GetProc01 exempel-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b7d67-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="b7d67-104">Observera att cmdleten förenklas genom att låta det faktiska arbetet i processen för hämtning av filer till den [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) metod.</span><span class="sxs-lookup"><span data-stu-id="b7d67-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="b7d67-105">Du kan ladda ned den C# källfilen (getproc01.cs) för denna cmdlet för Get-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="b7d67-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="b7d67-106">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="b7d67-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="b7d67-107">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="b7d67-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b7d67-108">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="b7d67-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="b7d67-109">Se även</span><span class="sxs-lookup"><span data-stu-id="b7d67-109">See Also</span></span>

[<span data-ttu-id="b7d67-110">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7d67-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="b7d67-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b7d67-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)