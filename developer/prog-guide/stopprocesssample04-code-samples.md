---
title: StopProcessSample04 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc68af2b-f622-47c4-964f-b07f3d5bdf14
caps.latest.revision: 5
ms.openlocfilehash: fdb78ac93befba66041c4e45834f8a857e3670b6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851095"
---
# <a name="stopprocesssample04-code-samples"></a><span data-ttu-id="72ffb-102">StopProcessSample04 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="72ffb-102">StopProcessSample04 Code Samples</span></span>

<span data-ttu-id="72ffb-103">Här följer kodexempel för StopProc00 exempel-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72ffb-103">Here are the code samples for the StopProc00 sample cmdlet.</span></span> <span data-ttu-id="72ffb-104">Det här är den `Stop-Process` cmdlet-exemplet som beskrivs i [att lägga till parametern anger att en Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="72ffb-104">This is the `Stop-Process` cmdlet sample described in [Adding Parameter Sets to a Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span></span> <span data-ttu-id="72ffb-105">Den `Stop-Process` cmdlet har utformats för att stoppa processer som hämtas med hjälp av cmdleten Get-processen (beskrivs i [skapa din första cmdleten](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="72ffb-105">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="72ffb-106">Du kan ladda ned den C# (stopprocesssample04.cs) och VB.NET (stopprocesssample04.vb) för denna cmdlet för Stop-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="72ffb-106">You can download the C# (stopprocesssample04.cs) and VB.NET (stopprocesssample04.vb) for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="72ffb-107">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="72ffb-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="72ffb-108">Du kan ladda ned den C# (stopprocesssample04.cs) och VB.NET (stopprocesssample04.vb) för denna cmdlet för Stop-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="72ffb-108">You can download the C# (stopprocesssample04.cs) and VB.NET (stopprocesssample04.vb) for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="72ffb-109">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="72ffb-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="72ffb-110">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="72ffb-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="72ffb-111">Fullständig exempelkod finns i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="72ffb-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="72ffb-112">Språk</span><span class="sxs-lookup"><span data-stu-id="72ffb-112">Language</span></span>|<span data-ttu-id="72ffb-113">Ämne</span><span class="sxs-lookup"><span data-stu-id="72ffb-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="72ffb-114">C#</span><span class="sxs-lookup"><span data-stu-id="72ffb-114">C#</span></span>|[<span data-ttu-id="72ffb-115">StopProc04 (C#) exempelkoden</span><span class="sxs-lookup"><span data-stu-id="72ffb-115">StopProc04 (C#) Sample Code</span></span>](./stopprocesssample04-csharp-sample-code.md)|
|<span data-ttu-id="72ffb-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="72ffb-116">VB.NET</span></span>|[<span data-ttu-id="72ffb-117">StopProc04 (VB.NET) exempelkod</span><span class="sxs-lookup"><span data-stu-id="72ffb-117">StopProc04 (VB.NET) Sample Code</span></span>](./stopprocesssample04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="72ffb-118">Se även</span><span class="sxs-lookup"><span data-stu-id="72ffb-118">See Also</span></span>

[<span data-ttu-id="72ffb-119">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="72ffb-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="72ffb-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="72ffb-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)