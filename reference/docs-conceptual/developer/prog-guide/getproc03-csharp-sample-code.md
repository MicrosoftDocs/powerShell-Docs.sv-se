---
title: GetProc03 (C#) exempel kod | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 24f47ab8d99683e6d0024bd8073b6d7bb5dcbd90
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978380"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="5750d-102">GetProc03 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="5750d-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="5750d-103">Följande kod visar implementeringen av en `Get-Process`-cmdlet som kan acceptera pipeline-inmatade.</span><span class="sxs-lookup"><span data-stu-id="5750d-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="5750d-104">Den här implementeringen definierar en `Name` parameter som godkänner pipeline-indata, hämtar process information från den lokala datorn baserat på de angivna namnen och använder sedan metoden [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) som utmatnings funktion för att skicka objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5750d-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="5750d-105">Du kan ladda ned C# käll filen (getprov03.CS) för den här get-proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="5750d-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5750d-106">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="5750d-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="5750d-107">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="5750d-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5750d-108">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="5750d-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a><span data-ttu-id="5750d-109">Se även</span><span class="sxs-lookup"><span data-stu-id="5750d-109">See Also</span></span>

[<span data-ttu-id="5750d-110">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="5750d-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5750d-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5750d-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
