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
ms.openlocfilehash: 116a116a5ba5b81a77b4432a81f001cc999fe46d
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301358"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="30966-102">GetProc03 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="30966-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="30966-103">Följande kod visar implementeringen av en `Get-Process` cmdlet som kan acceptera pipelined indata.</span><span class="sxs-lookup"><span data-stu-id="30966-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="30966-104">Den här implementeringen definierar en `Name` parameter som accepterar pipeline-indata, hämtar information om från den lokala datorn baserat på angivna namnen och använder sedan den [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)metod som utdata-mekanism för att skicka objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="30966-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="30966-105">Du kan ladda ned den C# källfilen (getprov03.cs) för denna cmdlet för Get-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="30966-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="30966-106">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="30966-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="30966-107">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="30966-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="30966-108">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="30966-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="30966-109">Se även</span><span class="sxs-lookup"><span data-stu-id="30966-109">See Also</span></span>

[<span data-ttu-id="30966-110">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="30966-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="30966-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="30966-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
