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
ms.openlocfilehash: 833ff1c37ee025e9cd9d2760bc63695534dd69ff
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429456"
---
# <a name="getproc03-code-samples"></a><span data-ttu-id="1db82-102">GetProc03 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="1db82-102">GetProc03 Code Samples</span></span>

<span data-ttu-id="1db82-103">Här följer kodexempel för GetProc03 exempel-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1db82-103">Here are the code samples for the GetProc03 sample cmdlet.</span></span> <span data-ttu-id="1db82-104">Det här är den `Get-Process` cmdlet-exemplet som beskrivs i [att lägga till parametrar som indata från Pipeline processen](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="1db82-104">This is the `Get-Process` cmdlet sample described in [Adding Parameters that Process Pipeline Input](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="1db82-105">Detta `Get-Process` cmdlet: en använder en `Name` parameter som godkänner indata från ett pipeline-objekt, hämtar information om från den lokala datorn baserat på angivna namnen och visar information om processerna på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="1db82-105">This `Get-Process` cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="1db82-106">Du kan ladda ned den C# källfilen (getprov03.cs) för denna cmdlet för Get-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="1db82-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1db82-107">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="1db82-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="1db82-108">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="1db82-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="1db82-109">Fullständig exempelkod finns i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="1db82-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="1db82-110">Språk</span><span class="sxs-lookup"><span data-stu-id="1db82-110">Language</span></span>|<span data-ttu-id="1db82-111">Ämne</span><span class="sxs-lookup"><span data-stu-id="1db82-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="1db82-112">C#</span><span class="sxs-lookup"><span data-stu-id="1db82-112">C#</span></span>|[<span data-ttu-id="1db82-113">GetProc03 (C#) exempelkoden</span><span class="sxs-lookup"><span data-stu-id="1db82-113">GetProc03 (C#) Sample Code</span></span>](./getproc03-csharp-sample-code.md)|
|<span data-ttu-id="1db82-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="1db82-114">VB.NET</span></span>|[<span data-ttu-id="1db82-115">GetProc03 (VB.NET) exempelkod</span><span class="sxs-lookup"><span data-stu-id="1db82-115">GetProc03 (VB.NET) Sample Code</span></span>](./getproc03-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="1db82-116">Se även</span><span class="sxs-lookup"><span data-stu-id="1db82-116">See Also</span></span>

[<span data-ttu-id="1db82-117">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1db82-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1db82-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1db82-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)