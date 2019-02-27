---
title: GetProc03 (C#) exempelkoden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: c24d18a2b80f8f9b62b5418fed35f54f7c7da23c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846398"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="6dca7-102">GetProc03 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="6dca7-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="6dca7-103">Följande kod visar implementeringen av en `Get-Process` cmdlet som kan acceptera pipelined indata.</span><span class="sxs-lookup"><span data-stu-id="6dca7-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="6dca7-104">Den här implementeringen definierar en `Name` parameter som accepterar pipeline-indata, hämtar information om från den lokala datorn baserat på angivna namnen och använder sedan den [System.Management.Automation.Cmdlet.Writeobject% 28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) metod som utdata-mekanism för att skicka objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="6dca7-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="6dca7-105">Du kan ladda ned den C# källfilen (getprov03.cs) för denna cmdlet för Get-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="6dca7-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6dca7-106">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6dca7-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="6dca7-107">Du kan ladda ned den C# källfilen (getprov03.cs) för denna cmdlet för Get-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="6dca7-107">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6dca7-108">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6dca7-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="6dca7-109">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="6dca7-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6dca7-110">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="6dca7-110">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="6dca7-111">Se även</span><span class="sxs-lookup"><span data-stu-id="6dca7-111">See Also</span></span>

[<span data-ttu-id="6dca7-112">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6dca7-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="6dca7-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6dca7-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)