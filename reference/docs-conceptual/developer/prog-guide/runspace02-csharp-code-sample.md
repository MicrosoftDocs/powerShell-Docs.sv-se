---
title: Kod exempel för Runspace02 (C#) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1e58f035f20baa7443d9031499062a45beae01b9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778459"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="e6965-102">Runspace02 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="e6965-102">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="e6965-103">Här är C#-käll koden för Runspace02-exemplet.</span><span class="sxs-lookup"><span data-stu-id="e6965-103">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="e6965-104">I det här exemplet används klassen [system. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) för att köra `Get-Process` cmdleten synkront.</span><span class="sxs-lookup"><span data-stu-id="e6965-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="e6965-105">Windows Forms och data bindning används sedan för att visa resultaten i en DataGridView-kontroll</span><span class="sxs-lookup"><span data-stu-id="e6965-105">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="e6965-106">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="e6965-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs" range="11-82":::

## <a name="see-also"></a><span data-ttu-id="e6965-107">Se även</span><span class="sxs-lookup"><span data-stu-id="e6965-107">See Also</span></span>

[<span data-ttu-id="e6965-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e6965-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
