---
ms.date: 09/12/2016
ms.topic: reference
title: GetProc03 (VB.NET) – kodexempel
description: GetProc03 (VB.NET) – kodexempel
ms.openlocfilehash: fc70496178c85e101b380e68aacd64c8d1f350e9
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355569"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="2fa37-103">GetProc03 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="2fa37-103">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="2fa37-104">Följande kod visar implementeringen av en `Get-Process` cmdlet som kan acceptera pipeline-inmatade.</span><span class="sxs-lookup"><span data-stu-id="2fa37-104">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="2fa37-105">Den här implementeringen definierar en `Name` parameter som accepterar pipeline-indata, hämtar process information från den lokala datorn baserat på de angivna namnen och använder sedan metoden [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) som utmatnings funktion för att skicka objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2fa37-105">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="2fa37-106">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="2fa37-106">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
