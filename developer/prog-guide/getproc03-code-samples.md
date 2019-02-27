---
title: GetProc03 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad39c7d-2f64-49d1-9be0-d2295e4302b3
caps.latest.revision: 5
ms.openlocfilehash: 8cb02b9f2510b90f405651deaf551e9622f5a298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847728"
---
# <a name="getproc03-code-samples"></a><span data-ttu-id="c83be-102">GetProc03 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="c83be-102">GetProc03 Code Samples</span></span>

<span data-ttu-id="c83be-103">Här följer kodexempel för GetProc03 exempel-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c83be-103">Here are the code samples for the GetProc03 sample cmdlet.</span></span> <span data-ttu-id="c83be-104">Det här är den `Get-Process` cmdlet-exemplet som beskrivs i [att lägga till parametrar som indata från Pipeline processen](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="c83be-104">This is the `Get-Process` cmdlet sample described in [Adding Parameters that Process Pipeline Input](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="c83be-105">Detta `Get-Process` cmdlet: en använder en `Name` parameter som godkänner indata från ett pipeline-objekt, hämtar information om från den lokala datorn baserat på angivna namnen och visar information om processerna på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="c83be-105">This `Get-Process` cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="c83be-106">Du kan ladda ned den C# källfilen (getprov03.cs) för denna cmdlet för Get-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="c83be-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c83be-107">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="c83be-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="c83be-108">Du kan ladda ned den C# källfilen (getprov03.cs) för denna cmdlet för Get-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="c83be-108">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c83be-109">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="c83be-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c83be-110">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="c83be-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="c83be-111">Fullständig exempelkod finns i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="c83be-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="c83be-112">Språk</span><span class="sxs-lookup"><span data-stu-id="c83be-112">Language</span></span>|<span data-ttu-id="c83be-113">Ämne</span><span class="sxs-lookup"><span data-stu-id="c83be-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="c83be-114">C#</span><span class="sxs-lookup"><span data-stu-id="c83be-114">C#</span></span>|[<span data-ttu-id="c83be-115">GetProc03 (C#) exempelkoden</span><span class="sxs-lookup"><span data-stu-id="c83be-115">GetProc03 (C#) Sample Code</span></span>](./getproc03-csharp-sample-code.md)|
|<span data-ttu-id="c83be-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="c83be-116">VB.NET</span></span>|[<span data-ttu-id="c83be-117">GetProc03 (VB.NET) exempelkod</span><span class="sxs-lookup"><span data-stu-id="c83be-117">GetProc03 (VB.NET) Sample Code</span></span>](./getproc03-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="c83be-118">Se även</span><span class="sxs-lookup"><span data-stu-id="c83be-118">See Also</span></span>

[<span data-ttu-id="c83be-119">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c83be-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c83be-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c83be-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)