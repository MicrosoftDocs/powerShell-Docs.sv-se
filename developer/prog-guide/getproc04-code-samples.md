---
title: GetProc04 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: d679bc8cbdb026e072628d3e0c5704de2eec7af9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846426"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="3135f-102">GetProc04 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="3135f-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="3135f-103">Här följer kodexempel för GetProc04 exempel-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3135f-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="3135f-104">Det här är den `Get-Process` cmdlet-exemplet som beskrivs i [att lägga till oändliga felrapportering om du till din Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="3135f-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="3135f-105">Detta `Get-Process` cmdlet-anrop i [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod när genereras ett ogiltig åtgärdsundantag vid hämtning av processinformation.</span><span class="sxs-lookup"><span data-stu-id="3135f-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="3135f-106">Du kan ladda ned den C# källfilen (getprov04.cs) för denna cmdlet för Get-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="3135f-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3135f-107">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="3135f-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="3135f-108">Du kan ladda ned den C# källfilen (getprov04.cs) för denna cmdlet för Get-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="3135f-108">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3135f-109">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="3135f-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="3135f-110">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="3135f-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="3135f-111">Fullständig exempelkod finns i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="3135f-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="3135f-112">Språk</span><span class="sxs-lookup"><span data-stu-id="3135f-112">Language</span></span>|<span data-ttu-id="3135f-113">Ämne</span><span class="sxs-lookup"><span data-stu-id="3135f-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="3135f-114">C#</span><span class="sxs-lookup"><span data-stu-id="3135f-114">C#</span></span>|[<span data-ttu-id="3135f-115">GetProc04 (C#) exempelkoden</span><span class="sxs-lookup"><span data-stu-id="3135f-115">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="3135f-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="3135f-116">VB.NET</span></span>|[<span data-ttu-id="3135f-117">GetProc04 (VB.NET) exempelkod</span><span class="sxs-lookup"><span data-stu-id="3135f-117">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="3135f-118">Se även</span><span class="sxs-lookup"><span data-stu-id="3135f-118">See Also</span></span>

[<span data-ttu-id="3135f-119">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3135f-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3135f-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3135f-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)