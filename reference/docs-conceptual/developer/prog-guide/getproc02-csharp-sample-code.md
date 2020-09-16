---
title: GetProc02 (C#) exempel kod | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d9afa8fff23d99661987c067e8082a9294c12717
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787163"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="64e5d-102">GetProc02 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="64e5d-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="64e5d-103">Följande kod visar implementeringen av en `Get-Process` cmdlet som accepterar kommando rads ingångar.</span><span class="sxs-lookup"><span data-stu-id="64e5d-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="64e5d-104">Observera att den här implementeringen definierar en `Name` parameter för att tillåta kommando rads indata och använder metoden [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) som utmatnings funktion för att skicka utdata till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="64e5d-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="64e5d-105">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="64e5d-105">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a><span data-ttu-id="64e5d-106">Se även</span><span class="sxs-lookup"><span data-stu-id="64e5d-106">See Also</span></span>

[<span data-ttu-id="64e5d-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="64e5d-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
