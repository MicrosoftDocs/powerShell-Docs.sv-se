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
ms.openlocfilehash: 59320365c4a35c3d71af10273eb21b1ce01e5c0c
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429711"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="36723-102">Runspace01 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="36723-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="36723-103">Här följer kodexempel för körningsutrymmet som beskrivs i [och skapa en konsolen programmet som kör ett kommando som angetts](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span><span class="sxs-lookup"><span data-stu-id="36723-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="36723-104">Om du vill göra detta måste programmet anropar ett körningsutrymme och anropar sedan ett kommando.</span><span class="sxs-lookup"><span data-stu-id="36723-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="36723-105">(Observera att det här programmet inte anger konfigurationsinformation för körningsutrymme eller gör det uttryckligen skapa en pipeline).</span><span class="sxs-lookup"><span data-stu-id="36723-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="36723-106">Kommandot som anropas är den `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36723-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="36723-107">Du kan ladda ned den C# källfilen (runspace01.cs) för den här körningsutrymme med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="36723-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="36723-108">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="36723-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="36723-109">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="36723-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="36723-110">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="36723-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="36723-111">Se även</span><span class="sxs-lookup"><span data-stu-id="36723-111">See Also</span></span>

[<span data-ttu-id="36723-112">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="36723-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="36723-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="36723-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)