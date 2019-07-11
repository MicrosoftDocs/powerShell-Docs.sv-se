---
title: Runspace01 (C#)-kodexemplet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: ab067485d70523a16493eb57170615ab300eaa98
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735049"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="70501-102">Runspace01 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="70501-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="70501-103">Här följer kodexempel för körningsutrymmet som beskrivs i [och skapa en konsolen programmet som kör ett kommando som angetts](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="70501-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="70501-104">Om du vill göra detta måste programmet anropar ett körningsutrymme och anropar sedan ett kommando.</span><span class="sxs-lookup"><span data-stu-id="70501-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="70501-105">(Observera att det här programmet inte anger konfigurationsinformation för körningsutrymme eller gör det uttryckligen skapa en pipeline).</span><span class="sxs-lookup"><span data-stu-id="70501-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="70501-106">Kommandot som anropas är den `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70501-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="70501-107">Du kan ladda ned den C# källfilen (runspace01.cs) för den här körningsutrymme med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="70501-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="70501-108">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="70501-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="70501-109">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="70501-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="70501-110">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="70501-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="70501-111">Se även</span><span class="sxs-lookup"><span data-stu-id="70501-111">See Also</span></span>

[<span data-ttu-id="70501-112">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="70501-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="70501-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="70501-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)