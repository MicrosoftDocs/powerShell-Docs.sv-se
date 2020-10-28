---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc04 (VB.NET) – kodexempel
description: GetProc04 (VB.NET) – kodexempel
ms.openlocfilehash: c46a374ab9d77f343b5ac6f45be1711eaec6dd75
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659226"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="57477-103">GetProc04 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="57477-103">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="57477-104">Följande kod visar implementeringen av en `Get-Process` cmdlet som rapporterar att det inte går att avsluta fel.</span><span class="sxs-lookup"><span data-stu-id="57477-104">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="57477-105">Den här implementeringen anropar metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) för att rapportera att det inte går att avsluta fel.</span><span class="sxs-lookup"><span data-stu-id="57477-105">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="57477-106">Du kan hämta C#-källfilen (getprov04.cs) för den här Get-Proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0-komponenter för körning.</span><span class="sxs-lookup"><span data-stu-id="57477-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="57477-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="57477-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="57477-108">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="57477-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="57477-109">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="57477-109">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="57477-110">Se även</span><span class="sxs-lookup"><span data-stu-id="57477-110">See Also</span></span>

[<span data-ttu-id="57477-111">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="57477-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="57477-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="57477-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
