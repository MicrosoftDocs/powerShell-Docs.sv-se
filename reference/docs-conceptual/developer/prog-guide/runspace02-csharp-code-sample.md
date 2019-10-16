---
title: Kod exempelC#för Runspace02 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59a7b8b9-f72e-43fd-9a10-77404441a3f2
caps.latest.revision: 6
ms.openlocfilehash: abf539bc29bd9ccac59bd5957397fbe68951f266
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357059"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="ca57f-102">Runspace02 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="ca57f-102">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="ca57f-103">Här är C# käll koden för Runspace02-exemplet.</span><span class="sxs-lookup"><span data-stu-id="ca57f-103">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="ca57f-104">I det här exemplet används klassen [system. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) för att köra cmdleten `Get-Process` synkront.</span><span class="sxs-lookup"><span data-stu-id="ca57f-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="ca57f-105">Windows Forms och data bindning används sedan för att visa resultaten i en DataGridView-kontroll</span><span class="sxs-lookup"><span data-stu-id="ca57f-105">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="ca57f-106">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="ca57f-106">Code Sample</span></span>

[!code-csharp[Runspace02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs#L11-L82 "Runspace02.cs")]

## <a name="see-also"></a><span data-ttu-id="ca57f-107">Se även</span><span class="sxs-lookup"><span data-stu-id="ca57f-107">See Also</span></span>

[<span data-ttu-id="ca57f-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ca57f-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
