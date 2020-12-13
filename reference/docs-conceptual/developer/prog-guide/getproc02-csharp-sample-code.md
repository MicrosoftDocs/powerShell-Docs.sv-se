---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc02 (C#) – kodexempel
description: GetProc02 (C#) – kodexempel
ms.openlocfilehash: 17fd0d0c0829ed21ef955fd2e62e9ee089d62190
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355620"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="bbe43-103">GetProc02 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="bbe43-103">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="bbe43-104">Följande kod visar implementeringen av en `Get-Process` cmdlet som accepterar kommando rads ingångar.</span><span class="sxs-lookup"><span data-stu-id="bbe43-104">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="bbe43-105">Observera att den här implementeringen definierar en `Name` parameter för att tillåta kommando rads indata och använder metoden [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) som utmatnings funktion för att skicka utdata till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="bbe43-105">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="bbe43-106">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="bbe43-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a><span data-ttu-id="bbe43-107">Se även</span><span class="sxs-lookup"><span data-stu-id="bbe43-107">See Also</span></span>

[<span data-ttu-id="bbe43-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="bbe43-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
