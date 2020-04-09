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
ms.openlocfilehash: 0978880a4294edb96fc6edb00f420cd0a9ad197b
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977989"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="15b62-102">Runspace01 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="15b62-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="15b62-103">Här är kod exemplen för körnings utrymme som beskrivs i [skapa ett konsol program som kör ett angivet kommando](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="15b62-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span>
<span data-ttu-id="15b62-104">För att göra detta anropar programmet en körnings utrymme och anropar sedan ett kommando.</span><span class="sxs-lookup"><span data-stu-id="15b62-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="15b62-105">(Observera att det här programmet inte anger körnings utrymme konfigurations information eller inte uttryckligen skapar en pipeline).</span><span class="sxs-lookup"><span data-stu-id="15b62-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="15b62-106">Kommandot som anropas är `Get-Process`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="15b62-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="15b62-107">Du kan ladda ned C# käll filen (runspace01.CS) för den här körnings utrymme med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="15b62-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span>
> <span data-ttu-id="15b62-108">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="15b62-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="15b62-109">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="15b62-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="15b62-110">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="15b62-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a><span data-ttu-id="15b62-111">Se även</span><span class="sxs-lookup"><span data-stu-id="15b62-111">See Also</span></span>

[<span data-ttu-id="15b62-112">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="15b62-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="15b62-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="15b62-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
