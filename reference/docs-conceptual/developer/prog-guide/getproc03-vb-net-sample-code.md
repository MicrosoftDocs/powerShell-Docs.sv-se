---
ms.date: 09/12/2016
ms.topic: reference
title: GetProc03 (VB.NET) – kodexempel
description: GetProc03 (VB.NET) – kodexempel
ms.openlocfilehash: 6d51c3bf65ccb37811acce0ab5f59daaac91118b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657209"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="d1dae-103">GetProc03 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="d1dae-103">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="d1dae-104">Följande kod visar implementeringen av en `Get-Process` cmdlet som kan acceptera pipeline-inmatade.</span><span class="sxs-lookup"><span data-stu-id="d1dae-104">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="d1dae-105">Den här implementeringen definierar en `Name` parameter som accepterar pipeline-indata, hämtar process information från den lokala datorn baserat på de angivna namnen och använder sedan metoden [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) som utmatnings funktion för att skicka objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="d1dae-105">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d1dae-106">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="d1dae-106">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
