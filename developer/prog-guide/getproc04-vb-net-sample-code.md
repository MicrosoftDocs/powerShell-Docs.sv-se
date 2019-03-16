---
title: GetProc04 (VB.NET) exempelkoden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: 0d0d1a3f82bc2cee025139d69fee02eb601fa563
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055469"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="deb72-102">GetProc04 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="deb72-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="deb72-103">Följande kod visar implementeringen av en `Get-Process` cmdlet som rapporterar oändliga fel.</span><span class="sxs-lookup"><span data-stu-id="deb72-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="deb72-104">Den här implementeringen anropar den [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod för att rapportera oändliga fel.</span><span class="sxs-lookup"><span data-stu-id="deb72-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="deb72-105">Du kan ladda ned den C# källfilen (getprov04.cs) för denna cmdlet för Get-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="deb72-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="deb72-106">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="deb72-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="deb72-107">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="deb72-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="deb72-108">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="deb72-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="deb72-109">Se även</span><span class="sxs-lookup"><span data-stu-id="deb72-109">See Also</span></span>

[<span data-ttu-id="deb72-110">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="deb72-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="deb72-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="deb72-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)