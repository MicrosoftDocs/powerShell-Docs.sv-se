---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc03 (C#) – kodexempel
description: GetProc03 (C#) – kodexempel
ms.openlocfilehash: 2784cd9bea3e8849f35dc37877930670d3faff4c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661909"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="35417-103">GetProc03 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="35417-103">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="35417-104">Följande kod visar implementeringen av en `Get-Process` cmdlet som kan acceptera pipeline-inmatade.</span><span class="sxs-lookup"><span data-stu-id="35417-104">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="35417-105">Den här implementeringen definierar en `Name` parameter som accepterar pipeline-indata, hämtar process information från den lokala datorn baserat på de angivna namnen och använder sedan metoden [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) som utmatnings funktion för att skicka objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="35417-105">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="35417-106">Du kan hämta C#-källfilen (getprov03.cs) för den här Get-Proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0-komponenter för körning.</span><span class="sxs-lookup"><span data-stu-id="35417-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="35417-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="35417-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="35417-108">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="35417-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="35417-109">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="35417-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a><span data-ttu-id="35417-110">Se även</span><span class="sxs-lookup"><span data-stu-id="35417-110">See Also</span></span>

[<span data-ttu-id="35417-111">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="35417-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="35417-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="35417-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
