---
title: Kod exempelC#för RunSpace03 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 06b5a06ae20a4bbb2c58eaa1776700aa8f80555c
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416059"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="29fcc-102">RunSpace03 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="29fcc-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="29fcc-103">Här är C# käll koden för konsol programmet som beskrivs i avsnittet "skapa ett konsol program som kör ett angivet skript".</span><span class="sxs-lookup"><span data-stu-id="29fcc-103">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="29fcc-104">I det här exemplet används klassen [system. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) för att köra ett skript som hämtar process information med hjälp av listan över process namn som skickas till skriptet.</span><span class="sxs-lookup"><span data-stu-id="29fcc-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="29fcc-105">Den visar hur du skickar indata-objekt till ett skript och hur du hämtar fel objekt samt utgående objekt.</span><span class="sxs-lookup"><span data-stu-id="29fcc-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="29fcc-106">Du kan ladda ned C# käll filen (runspace03.CS) för det här exemplet med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="29fcc-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="29fcc-107">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="29fcc-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="29fcc-108">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="29fcc-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="29fcc-109">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="29fcc-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="29fcc-110">Se även</span><span class="sxs-lookup"><span data-stu-id="29fcc-110">See Also</span></span>

[<span data-ttu-id="29fcc-111">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="29fcc-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="29fcc-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="29fcc-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
