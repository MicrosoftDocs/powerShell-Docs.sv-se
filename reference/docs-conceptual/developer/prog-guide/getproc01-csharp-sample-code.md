---
title: GetProc01 (C#) exempel kod | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 883beb9dd1328a1897b9b61656a98cf515a21be7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778901"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="e0cf6-102">GetProc01 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="e0cf6-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="e0cf6-103">Följande kod visar implementeringen av GetProc01-exempel-cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="e0cf6-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="e0cf6-104">Observera att cmdleten är förenklad genom att lämna det faktiska arbetet med process hämtning till metoden [system. Diagnostics. process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) .</span><span class="sxs-lookup"><span data-stu-id="e0cf6-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="e0cf6-105">Du kan hämta C#-källfilen (getproc01.cs) för den här get-proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="e0cf6-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e0cf6-106">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e0cf6-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="e0cf6-107">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="e0cf6-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e0cf6-108">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="e0cf6-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a><span data-ttu-id="e0cf6-109">Se även</span><span class="sxs-lookup"><span data-stu-id="e0cf6-109">See Also</span></span>

[<span data-ttu-id="e0cf6-110">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0cf6-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e0cf6-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e0cf6-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
