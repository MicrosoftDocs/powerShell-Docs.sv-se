---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace02 (C#) – kodexempel
description: Runspace02 (C#) – kodexempel
ms.openlocfilehash: 9e2c0cf37d1bf12a92f4fbf781928c0241202915
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647452"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="b398d-103">Runspace02 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="b398d-103">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="b398d-104">Här är C#-käll koden för Runspace02-exemplet.</span><span class="sxs-lookup"><span data-stu-id="b398d-104">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="b398d-105">I det här exemplet används klassen [system. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) för att köra `Get-Process` cmdleten synkront.</span><span class="sxs-lookup"><span data-stu-id="b398d-105">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="b398d-106">Windows Forms och data bindning används sedan för att visa resultaten i en DataGridView-kontroll</span><span class="sxs-lookup"><span data-stu-id="b398d-106">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="b398d-107">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="b398d-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs" range="11-82":::

## <a name="see-also"></a><span data-ttu-id="b398d-108">Se även</span><span class="sxs-lookup"><span data-stu-id="b398d-108">See Also</span></span>

[<span data-ttu-id="b398d-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b398d-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
