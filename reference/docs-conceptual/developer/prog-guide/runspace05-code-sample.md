---
title: RunSpace05 kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 8802e308712be93992ead5ef77b97d8c21b137f7
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870650"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="e9b4e-102">RunSpace05 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="e9b4e-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="e9b4e-103">Här är käll koden för Runspace05-exemplet som beskrivs i [Konfigurera en körnings utrymme med hjälp av RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="e9b4e-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span></span>
<span data-ttu-id="e9b4e-104">Det här exemplet visar hur du skapar konfigurations informationen för körnings utrymme, skapar en körnings utrymme, skapar en pipeline med ett enda kommando och sedan kör pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e9b4e-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="e9b4e-105">Kommandot som körs är `Get-Process`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e9b4e-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="e9b4e-106">Du kan ladda ned C# käll filen (runspace05.CS) med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="e9b4e-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e9b4e-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e9b4e-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="e9b4e-108">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="e9b4e-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e9b4e-109">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="e9b4e-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="e9b4e-110">Se även</span><span class="sxs-lookup"><span data-stu-id="e9b4e-110">See Also</span></span>

[<span data-ttu-id="e9b4e-111">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="e9b4e-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e9b4e-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e9b4e-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
