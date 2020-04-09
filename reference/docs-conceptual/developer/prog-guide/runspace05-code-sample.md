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
ms.openlocfilehash: 4d9a2db76fe69a8509d33a22124f5f952b1d3c80
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978312"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="1af1a-102">RunSpace05 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="1af1a-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="1af1a-103">Här är käll koden för Runspace05-exemplet som beskrivs i [Konfigurera en körnings utrymme med hjälp av RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="1af1a-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span></span>
<span data-ttu-id="1af1a-104">Det här exemplet visar hur du skapar konfigurations informationen för körnings utrymme, skapar en körnings utrymme, skapar en pipeline med ett enda kommando och sedan kör pipelinen.</span><span class="sxs-lookup"><span data-stu-id="1af1a-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="1af1a-105">Kommandot som körs är `Get-Process`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1af1a-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="1af1a-106">Du kan ladda ned C# käll filen (runspace05.CS) med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="1af1a-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1af1a-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="1af1a-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="1af1a-108">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="1af1a-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1af1a-109">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="1af1a-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="1af1a-110">Se även</span><span class="sxs-lookup"><span data-stu-id="1af1a-110">See Also</span></span>

[<span data-ttu-id="1af1a-111">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="1af1a-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1af1a-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1af1a-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
