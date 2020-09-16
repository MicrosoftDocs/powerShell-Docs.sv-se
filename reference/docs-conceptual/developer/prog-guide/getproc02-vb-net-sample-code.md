---
title: GetProc02 (VB.NET) exempel kod | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 98261f2d6678e24bb8e8df6d2c8a405b25203364
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787180"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="616f9-102">GetProc02 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="616f9-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="616f9-103">Följande kod visar implementeringen av en `Get-Process` cmdlet som accepterar kommando rads ingångar.</span><span class="sxs-lookup"><span data-stu-id="616f9-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="616f9-104">Observera att den här implementeringen definierar en `Name` parameter för att tillåta kommando rads indata och använder metoden [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) som utmatnings funktion för att skicka utdata till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="616f9-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="616f9-105">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="616f9-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="616f9-106">Se även</span><span class="sxs-lookup"><span data-stu-id="616f9-106">See Also</span></span>

[<span data-ttu-id="616f9-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="616f9-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
