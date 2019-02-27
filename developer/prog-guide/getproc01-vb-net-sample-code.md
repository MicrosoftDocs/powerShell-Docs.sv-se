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
ms.openlocfilehash: 1f11c89f60aef44905cbce3fe669def26119d12e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846860"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="4a407-102">GetProc01 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="4a407-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="4a407-103">Följande kod visar implementeringen av GetProc01 exempel-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4a407-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="4a407-104">Observera att cmdleten förenklas genom att låta det faktiska arbetet i processen för hämtning av filer till den [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) metod.</span><span class="sxs-lookup"><span data-stu-id="4a407-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="4a407-105">Du kan ladda ned den C# källfilen (getproc01.cs) för denna cmdlet för Get-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="4a407-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4a407-106">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="4a407-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="4a407-107">Du kan ladda ned den C# källfilen (getproc01.cs) för denna cmdlet för Get-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="4a407-107">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4a407-108">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="4a407-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="4a407-109">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="4a407-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4a407-110">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="4a407-110">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="4a407-111">Se även</span><span class="sxs-lookup"><span data-stu-id="4a407-111">See Also</span></span>

[<span data-ttu-id="4a407-112">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a407-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4a407-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4a407-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)