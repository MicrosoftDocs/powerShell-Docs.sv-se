---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc02 (VB.NET) – kodexempel
description: GetProc02 (VB.NET) – kodexempel
ms.openlocfilehash: e13da4689b7f4ba4878e83cd826076a6394d9fb2
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654371"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="ef7ab-103">GetProc02 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="ef7ab-103">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="ef7ab-104">Följande kod visar implementeringen av en `Get-Process` cmdlet som accepterar kommando rads ingångar.</span><span class="sxs-lookup"><span data-stu-id="ef7ab-104">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="ef7ab-105">Observera att den här implementeringen definierar en `Name` parameter för att tillåta kommando rads indata och använder metoden [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) som utmatnings funktion för att skicka utdata till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="ef7ab-105">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ef7ab-106">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="ef7ab-106">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="ef7ab-107">Se även</span><span class="sxs-lookup"><span data-stu-id="ef7ab-107">See Also</span></span>

[<span data-ttu-id="ef7ab-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ef7ab-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
