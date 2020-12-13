---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc04 (VB.NET) – kodexempel
description: GetProc04 (VB.NET) – kodexempel
ms.openlocfilehash: c46a374ab9d77f343b5ac6f45be1711eaec6dd75
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659226"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="36608-103">GetProc04 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="36608-103">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="36608-104">Följande kod visar implementeringen av en `Get-Process` cmdlet som rapporterar att det inte går att avsluta fel.</span><span class="sxs-lookup"><span data-stu-id="36608-104">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="36608-105">Den här implementeringen anropar metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) för att rapportera att det inte går att avsluta fel.</span><span class="sxs-lookup"><span data-stu-id="36608-105">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="36608-106">Du kan hämta C#-källfilen (getprov04.cs) för den här Get-Proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0-komponenter för körning.</span><span class="sxs-lookup"><span data-stu-id="36608-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="36608-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="36608-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="36608-108">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="36608-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="36608-109">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="36608-109">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="36608-110">Se även</span><span class="sxs-lookup"><span data-stu-id="36608-110">See Also</span></span>

[<span data-ttu-id="36608-111">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="36608-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="36608-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="36608-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
