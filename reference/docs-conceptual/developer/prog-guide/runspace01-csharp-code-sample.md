---
title: Kod exempelC#för Runspace01 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 39e7d49b51942da51a581ab33dbe46ab848ca1c3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357073"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="00708-102">Runspace01 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="00708-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="00708-103">Här är kod exemplen för körnings utrymme som beskrivs i [skapa ett konsol program som kör ett angivet kommando](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="00708-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="00708-104">För att göra detta anropar programmet en körnings utrymme och anropar sedan ett kommando.</span><span class="sxs-lookup"><span data-stu-id="00708-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="00708-105">(Observera att det här programmet inte anger körnings utrymme konfigurations information eller inte uttryckligen skapar en pipeline).</span><span class="sxs-lookup"><span data-stu-id="00708-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="00708-106">Kommandot som anropas är cmdleten `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="00708-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="00708-107">Du kan ladda ned C# käll filen (runspace01.CS) för den här körnings utrymme med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="00708-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="00708-108">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="00708-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="00708-109">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="00708-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="00708-110">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="00708-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="00708-111">Se även</span><span class="sxs-lookup"><span data-stu-id="00708-111">See Also</span></span>

[<span data-ttu-id="00708-112">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="00708-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="00708-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="00708-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
