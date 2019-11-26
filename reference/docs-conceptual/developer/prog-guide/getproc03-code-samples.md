---
title: GetProc03-kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad39c7d-2f64-49d1-9be0-d2295e4302b3
caps.latest.revision: 5
ms.openlocfilehash: bd6d26cb830bcd6706c88548956e5358b2fddf41
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416147"
---
# <a name="getproc03-code-samples"></a><span data-ttu-id="c8ea4-102">GetProc03 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="c8ea4-102">GetProc03 Code Samples</span></span>

<span data-ttu-id="c8ea4-103">Här är kod exemplen för GetProc03-exempel-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c8ea4-103">Here are the code samples for the GetProc03 sample cmdlet.</span></span> <span data-ttu-id="c8ea4-104">Detta är `Get-Process` cmdlet-exemplet som beskrivs i [lägga till parametrar som bearbetar pipeline-inflöden](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="c8ea4-104">This is the `Get-Process` cmdlet sample described in [Adding Parameters that Process Pipeline Input](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="c8ea4-105">Denna `Get-Process`-cmdlet använder en `Name` parameter som accepterar indata från ett pipeline-objekt, hämtar process information från den lokala datorn baserat på de angivna namnen och visar sedan information om processerna på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="c8ea4-105">This `Get-Process` cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="c8ea4-106">Du kan ladda ned C# käll filen (getprov03.CS) för den här get-proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="c8ea4-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c8ea4-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="c8ea4-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c8ea4-108">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="c8ea4-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="c8ea4-109">Fullständig exempel kod finns i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="c8ea4-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="c8ea4-110">Språk</span><span class="sxs-lookup"><span data-stu-id="c8ea4-110">Language</span></span>|<span data-ttu-id="c8ea4-111">Avsnitt</span><span class="sxs-lookup"><span data-stu-id="c8ea4-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="c8ea4-112">C#</span><span class="sxs-lookup"><span data-stu-id="c8ea4-112">C#</span></span>|[<span data-ttu-id="c8ea4-113">GetProc03 (C#) exempel kod</span><span class="sxs-lookup"><span data-stu-id="c8ea4-113">GetProc03 (C#) Sample Code</span></span>](./getproc03-csharp-sample-code.md)|
|<span data-ttu-id="c8ea4-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="c8ea4-114">VB.NET</span></span>|[<span data-ttu-id="c8ea4-115">GetProc03 (VB.NET) exempel kod</span><span class="sxs-lookup"><span data-stu-id="c8ea4-115">GetProc03 (VB.NET) Sample Code</span></span>](./getproc03-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="c8ea4-116">Se även</span><span class="sxs-lookup"><span data-stu-id="c8ea4-116">See Also</span></span>

[<span data-ttu-id="c8ea4-117">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="c8ea4-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c8ea4-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c8ea4-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
