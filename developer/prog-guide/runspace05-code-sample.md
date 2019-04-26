---
title: RunSpace05 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: b16ee45383059c52ce3433699c6b8d2120992431
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081350"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="240e6-102">RunSpace05 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="240e6-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="240e6-103">Här är källkoden för Runspace05-exemplet som beskrivs i [konfigurerar en Körningsutrymme med RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="240e6-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="240e6-104">Detta exempel visar hur du skapar körningsutrymme konfigurationsinformation, skapa ett körningsutrymme, skapa en pipeline med ett enda kommando och sedan köra pipelinen.</span><span class="sxs-lookup"><span data-stu-id="240e6-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="240e6-105">Kommandot som körs är den `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="240e6-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="240e6-106">Du kan ladda ned den C# källfilen (runspace05.cs) med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="240e6-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="240e6-107">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="240e6-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="240e6-108">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="240e6-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="240e6-109">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="240e6-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="240e6-110">Se även</span><span class="sxs-lookup"><span data-stu-id="240e6-110">See Also</span></span>

[<span data-ttu-id="240e6-111">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="240e6-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="240e6-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="240e6-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)