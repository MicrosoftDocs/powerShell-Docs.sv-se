---
title: GetProc04 (C#) exempel kod | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: d17a67019b7451f2da5595b3258457a01cc86b0b
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978363"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="32965-102">GetProc04 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="32965-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="32965-103">Följande kod visar implementeringen av en `Get-Process`-cmdlet som rapporterar att det inte går att avsluta fel.</span><span class="sxs-lookup"><span data-stu-id="32965-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="32965-104">Den här implementeringen anropar metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) för att rapportera att det inte går att avsluta fel.</span><span class="sxs-lookup"><span data-stu-id="32965-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="32965-105">Du kan ladda ned C# käll filen (getprov04.CS) för den här get-proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="32965-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="32965-106">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="32965-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="32965-107">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="32965-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="32965-108">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="32965-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs" range="11-98":::

## <a name="see-also"></a><span data-ttu-id="32965-109">Se även</span><span class="sxs-lookup"><span data-stu-id="32965-109">See Also</span></span>

[<span data-ttu-id="32965-110">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="32965-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="32965-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="32965-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
