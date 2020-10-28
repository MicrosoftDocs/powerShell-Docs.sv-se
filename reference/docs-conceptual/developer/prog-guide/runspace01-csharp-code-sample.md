---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace01 (C#) – kodexempel
description: Runspace01 (C#) – kodexempel
ms.openlocfilehash: e6121c144e1a4c1a1d9460d01119f44ee5835821
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657149"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="8cb45-103">Runspace01 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="8cb45-103">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="8cb45-104">Här är kod exemplen för körnings utrymme som beskrivs i [skapa ett konsol program som kör ett angivet kommando](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="8cb45-104">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span>
<span data-ttu-id="8cb45-105">För att göra detta anropar programmet en körnings utrymme och anropar sedan ett kommando.</span><span class="sxs-lookup"><span data-stu-id="8cb45-105">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="8cb45-106">(Observera att det här programmet inte anger körnings utrymme konfigurations information eller inte uttryckligen skapar en pipeline).</span><span class="sxs-lookup"><span data-stu-id="8cb45-106">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="8cb45-107">Kommandot som anropas är `Get-Process` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8cb45-107">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="8cb45-108">Du kan hämta C#-källfilen (runspace01.cs) för den här körnings utrymme med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="8cb45-108">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span>
> <span data-ttu-id="8cb45-109">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="8cb45-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="8cb45-110">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="8cb45-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8cb45-111">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="8cb45-111">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a><span data-ttu-id="8cb45-112">Se även</span><span class="sxs-lookup"><span data-stu-id="8cb45-112">See Also</span></span>

[<span data-ttu-id="8cb45-113">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8cb45-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="8cb45-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8cb45-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
