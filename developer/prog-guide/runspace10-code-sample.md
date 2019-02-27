---
title: RunSpace10 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: 95b25746a8e99deb871905734700aba51cd7765e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845838"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="ab19b-102">RunSpace10 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="ab19b-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="ab19b-103">Här är källkoden för Runspace10-exemplet.</span><span class="sxs-lookup"><span data-stu-id="ab19b-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="ab19b-104">Det här exempelprogrammet lägger till en cmdlet för att [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) och använder sedan den ändrade konfigurationsinformationen för att skapa körningsutrymmet.</span><span class="sxs-lookup"><span data-stu-id="ab19b-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="ab19b-105">Du kan ladda ned den C# källfilen (runspace10.cs) med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="ab19b-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ab19b-106">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="ab19b-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="ab19b-107">Du kan ladda ned den C# källfilen (runspace10.cs) med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="ab19b-107">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ab19b-108">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="ab19b-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="ab19b-109">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="ab19b-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ab19b-110">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="ab19b-110">Code Sample</span></span>

[!code-csharp[Runspace10.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a><span data-ttu-id="ab19b-111">Se även</span><span class="sxs-lookup"><span data-stu-id="ab19b-111">See Also</span></span>

[<span data-ttu-id="ab19b-112">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab19b-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ab19b-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ab19b-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)