---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc04 – kodexempel
description: GetProc04 – kodexempel
ms.openlocfilehash: db94eda2b3aa5fc88a3054df66f54628e1482f56
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659241"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="b4148-103">GetProc04 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="b4148-103">GetProc04 Code Samples</span></span>

<span data-ttu-id="b4148-104">Här är kod exemplen för GetProc04-exempel-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b4148-104">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="b4148-105">Detta är det `Get-Process` cmdlet-exempel som beskrivs i [lägga till fel rapportering som inte avslutas till din cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="b4148-105">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="b4148-106">Den här `Get-Process` cmdleten anropar metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) när ett ogiltigt åtgärds undantag genereras vid hämtning av process information.</span><span class="sxs-lookup"><span data-stu-id="b4148-106">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="b4148-107">Du kan hämta C#-källfilen (getprov04.cs) för den här Get-Proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0-komponenter för körning.</span><span class="sxs-lookup"><span data-stu-id="b4148-107">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="b4148-108">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="b4148-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="b4148-109">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="b4148-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="b4148-110">Fullständig exempel kod finns i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="b4148-110">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="b4148-111">Språk</span><span class="sxs-lookup"><span data-stu-id="b4148-111">Language</span></span>|<span data-ttu-id="b4148-112">Avsnitt</span><span class="sxs-lookup"><span data-stu-id="b4148-112">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="b4148-113">C#</span><span class="sxs-lookup"><span data-stu-id="b4148-113">C#</span></span>|[<span data-ttu-id="b4148-114">GetProc04 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="b4148-114">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="b4148-115">VB.NET</span><span class="sxs-lookup"><span data-stu-id="b4148-115">VB.NET</span></span>|[<span data-ttu-id="b4148-116">GetProc04 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="b4148-116">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="b4148-117">Se även</span><span class="sxs-lookup"><span data-stu-id="b4148-117">See Also</span></span>

[<span data-ttu-id="b4148-118">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b4148-118">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="b4148-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b4148-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
