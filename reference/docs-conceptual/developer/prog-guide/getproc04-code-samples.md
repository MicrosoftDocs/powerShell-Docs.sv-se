---
title: GetProc04-kod exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b90b7e96c1454e57df93863b526758f25d9be690
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771965"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="42776-102">GetProc04 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="42776-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="42776-103">Här är kod exemplen för GetProc04-exempel-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="42776-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="42776-104">Detta är det `Get-Process` cmdlet-exempel som beskrivs i [lägga till fel rapportering som inte avslutas till din cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="42776-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="42776-105">Den här `Get-Process` cmdleten anropar metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) när ett ogiltigt åtgärds undantag genereras vid hämtning av process information.</span><span class="sxs-lookup"><span data-stu-id="42776-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="42776-106">Du kan hämta C#-källfilen (getprov04.cs) för den här get-proc-cmdleten med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="42776-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="42776-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="42776-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="42776-108">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="42776-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="42776-109">Fullständig exempel kod finns i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="42776-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="42776-110">Språk</span><span class="sxs-lookup"><span data-stu-id="42776-110">Language</span></span>|<span data-ttu-id="42776-111">Avsnitt</span><span class="sxs-lookup"><span data-stu-id="42776-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="42776-112">C#</span><span class="sxs-lookup"><span data-stu-id="42776-112">C#</span></span>|[<span data-ttu-id="42776-113">GetProc04 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="42776-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="42776-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="42776-114">VB.NET</span></span>|[<span data-ttu-id="42776-115">GetProc04 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="42776-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="42776-116">Se även</span><span class="sxs-lookup"><span data-stu-id="42776-116">See Also</span></span>

[<span data-ttu-id="42776-117">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="42776-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="42776-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="42776-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
