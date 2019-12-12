---
title: GetProc04 (VB.NET) exempel kod | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: f2164b97e4f3b3346e66d00834aa299659b62b33
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416102"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="3bdae-102">GetProc04 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="3bdae-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="3bdae-103">Följande kod visar implementeringen av en `Get-Process`-cmdlet som rapporterar att det inte går att avsluta fel.</span><span class="sxs-lookup"><span data-stu-id="3bdae-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="3bdae-104">Den här implementeringen anropar metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) för att rapportera att det inte går att avsluta fel.</span><span class="sxs-lookup"><span data-stu-id="3bdae-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="3bdae-105">Du kan ladda ned C# käll filen (getprov04.CS) för den här get-proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="3bdae-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3bdae-106">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="3bdae-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="3bdae-107">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="3bdae-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3bdae-108">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="3bdae-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="3bdae-109">Se även</span><span class="sxs-lookup"><span data-stu-id="3bdae-109">See Also</span></span>

[<span data-ttu-id="3bdae-110">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="3bdae-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3bdae-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3bdae-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
