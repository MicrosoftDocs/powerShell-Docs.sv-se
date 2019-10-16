---
title: GetProc04-kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352642"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="66fde-102">GetProc04 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="66fde-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="66fde-103">Här är kod exemplen för GetProc04-exempel-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="66fde-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="66fde-104">Detta är `Get-Process`-cmdlet-exemplet som beskrivs i [lägga till ej avslutande fel rapportering till din cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="66fde-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="66fde-105">Denna `Get-Process`-cmdlet anropar metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) när ett ogiltigt åtgärds undantag genereras vid hämtning av process information.</span><span class="sxs-lookup"><span data-stu-id="66fde-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="66fde-106">Du kan ladda ned C# käll filen (getprov04.CS) för den här get-proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="66fde-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="66fde-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="66fde-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="66fde-108">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="66fde-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="66fde-109">Fullständig exempel kod finns i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="66fde-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="66fde-110">Språk</span><span class="sxs-lookup"><span data-stu-id="66fde-110">Language</span></span>|<span data-ttu-id="66fde-111">Ämne</span><span class="sxs-lookup"><span data-stu-id="66fde-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="66fde-112">C#</span><span class="sxs-lookup"><span data-stu-id="66fde-112">C#</span></span>|[<span data-ttu-id="66fde-113">GetProc04 (C#) exempel kod</span><span class="sxs-lookup"><span data-stu-id="66fde-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="66fde-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="66fde-114">VB.NET</span></span>|[<span data-ttu-id="66fde-115">GetProc04 (VB.NET) exempel kod</span><span class="sxs-lookup"><span data-stu-id="66fde-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="66fde-116">Se även</span><span class="sxs-lookup"><span data-stu-id="66fde-116">See Also</span></span>

[<span data-ttu-id="66fde-117">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="66fde-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="66fde-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="66fde-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)