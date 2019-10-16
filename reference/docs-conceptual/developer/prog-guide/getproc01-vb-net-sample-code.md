---
title: GetProc01 (VB.NET) exempel kod | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ee87f67-6d2c-48cc-b300-3ae917c6dc88
caps.latest.revision: 5
ms.openlocfilehash: 2411642c39737e7dc03bd0bb4ea753ed27783732
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352726"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="5a3ac-102">GetProc01 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="5a3ac-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="5a3ac-103">Följande kod visar implementeringen av GetProc01-exempel-cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="5a3ac-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="5a3ac-104">Observera att cmdleten är förenklad genom att lämna det faktiska arbetet med process hämtning till metoden [system. Diagnostics. process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) .</span><span class="sxs-lookup"><span data-stu-id="5a3ac-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="5a3ac-105">Du kan ladda ned C# käll filen (getproc01.CS) för den här get-proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="5a3ac-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5a3ac-106">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="5a3ac-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="5a3ac-107">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="5a3ac-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5a3ac-108">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="5a3ac-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="5a3ac-109">Se även</span><span class="sxs-lookup"><span data-stu-id="5a3ac-109">See Also</span></span>

[<span data-ttu-id="5a3ac-110">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="5a3ac-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5a3ac-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5a3ac-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)