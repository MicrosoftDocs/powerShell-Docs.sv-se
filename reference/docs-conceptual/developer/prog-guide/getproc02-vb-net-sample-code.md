---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc02 (VB.NET) – kodexempel
description: GetProc02 (VB.NET) – kodexempel
ms.openlocfilehash: aefc3a4df5e0f29120916648ecdca41931a4c1c6
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354549"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="5af23-103">GetProc02 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="5af23-103">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="5af23-104">Följande kod visar implementeringen av en `Get-Process` cmdlet som accepterar kommando rads ingångar.</span><span class="sxs-lookup"><span data-stu-id="5af23-104">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="5af23-105">Observera att den här implementeringen definierar en `Name` parameter för att tillåta kommando rads indata och använder metoden [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) som utmatnings funktion för att skicka utdata till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5af23-105">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5af23-106">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="5af23-106">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="5af23-107">Se även</span><span class="sxs-lookup"><span data-stu-id="5af23-107">See Also</span></span>

[<span data-ttu-id="5af23-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5af23-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
