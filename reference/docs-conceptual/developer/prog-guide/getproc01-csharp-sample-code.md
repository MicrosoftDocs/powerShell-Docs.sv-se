---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc01 (C#) – kodexempel
description: GetProc01 (C#) – kodexempel
ms.openlocfilehash: 79509ff12afb32c907058f4ddb0c707f3823857a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654477"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="b17d4-103">GetProc01 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="b17d4-103">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="b17d4-104">Följande kod visar implementeringen av GetProc01-exempel-cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="b17d4-104">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="b17d4-105">Observera att cmdleten är förenklad genom att lämna det faktiska arbetet med process hämtning till metoden [system. Diagnostics. process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) .</span><span class="sxs-lookup"><span data-stu-id="b17d4-105">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="b17d4-106">Du kan hämta C#-källfilen (getproc01.cs) för den här Get-Proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0-komponenter för körning.</span><span class="sxs-lookup"><span data-stu-id="b17d4-106">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="b17d4-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="b17d4-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="b17d4-108">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="b17d4-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b17d4-109">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="b17d4-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a><span data-ttu-id="b17d4-110">Se även</span><span class="sxs-lookup"><span data-stu-id="b17d4-110">See Also</span></span>

[<span data-ttu-id="b17d4-111">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b17d4-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="b17d4-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b17d4-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
