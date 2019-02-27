---
title: StopProc01 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 60873d0f-c5f1-4d5b-ade1-49ad0df43245
caps.latest.revision: 5
ms.openlocfilehash: 406e40065d95f657e41ecac994eee02e281744c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847224"
---
# <a name="stopproc01-code-samples"></a><span data-ttu-id="1e4f0-102">StopProc01 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="1e4f0-102">StopProc01 Code Samples</span></span>

<span data-ttu-id="1e4f0-103">Här är exempelkod för StopProc01 exempel-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e4f0-103">Here is the code sample for the StopProc01 sample cmdlet.</span></span> <span data-ttu-id="1e4f0-104">Det här är den `Stop-Process` cmdlet-exemplet som beskrivs i [skapa en Cmdlet som ändrar systemet](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="1e4f0-104">This is the `Stop-Process` cmdlet sample described in [Creating a Cmdlet that Modifies the System](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).</span></span> <span data-ttu-id="1e4f0-105">Den `Stop-Process` cmdlet har utformats för att stoppa processer som hämtas med hjälp av cmdleten Get-processen (beskrivs i [skapa din första cmdleten](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="1e4f0-105">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="1e4f0-106">Du kan ladda ned den C# (stopproc01.cs) källfilen för cmdleten Stop-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="1e4f0-106">You can download the C# (stopproc01.cs) source file for the Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1e4f0-107">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="1e4f0-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="1e4f0-108">Du kan ladda ned den C# (stopproc01.cs) källfilen för cmdleten Stop-processen med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="1e4f0-108">You can download the C# (stopproc01.cs) source file for the Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1e4f0-109">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="1e4f0-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="1e4f0-110">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="1e4f0-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

|<span data-ttu-id="1e4f0-111">Språk</span><span class="sxs-lookup"><span data-stu-id="1e4f0-111">Language</span></span>|<span data-ttu-id="1e4f0-112">Ämne</span><span class="sxs-lookup"><span data-stu-id="1e4f0-112">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="1e4f0-113">C#</span><span class="sxs-lookup"><span data-stu-id="1e4f0-113">C#</span></span>|[<span data-ttu-id="1e4f0-114">StopProc01 (C#) exempelkoden</span><span class="sxs-lookup"><span data-stu-id="1e4f0-114">StopProc01 (C#) Sample Code</span></span>](./stopproc01-csharp-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="1e4f0-115">Se även</span><span class="sxs-lookup"><span data-stu-id="1e4f0-115">See Also</span></span>

[<span data-ttu-id="1e4f0-116">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e4f0-116">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1e4f0-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1e4f0-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)