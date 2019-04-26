---
title: GetProc04 (C#) exempelkoden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: 936fb355be40b98136719ea929cf50b06705b687
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081639"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="65b4f-102">GetProc04 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="65b4f-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="65b4f-103">Följande kod visar implementeringen av en `Get-Process` cmdlet som rapporterar oändliga fel.</span><span class="sxs-lookup"><span data-stu-id="65b4f-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="65b4f-104">Den här implementeringen anropar den [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod för att rapportera oändliga fel.</span><span class="sxs-lookup"><span data-stu-id="65b4f-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="65b4f-105">Du kan ladda ned den C# källfilen (getprov04.cs) för denna cmdlet för Get-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="65b4f-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="65b4f-106">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="65b4f-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="65b4f-107">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="65b4f-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="65b4f-108">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="65b4f-108">Code Sample</span></span>

[!code-csharp[GetProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="65b4f-109">Se även</span><span class="sxs-lookup"><span data-stu-id="65b4f-109">See Also</span></span>

[<span data-ttu-id="65b4f-110">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="65b4f-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="65b4f-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="65b4f-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)