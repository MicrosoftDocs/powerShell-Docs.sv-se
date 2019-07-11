---
title: RunSpace03 (C#)-kodexemplet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: e1fc91174a959d6acc306330afb8d5c2e7a9a860
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735002"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="122ca-102">RunSpace03 (C#) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="122ca-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="122ca-103">Här är den C# källkoden för konsolprogrammet som beskrivs i [och skapa en konsolen program som använder ett skript som angetts](fd).</span><span class="sxs-lookup"><span data-stu-id="122ca-103">Here is the C# source code for the console application described in [Creating a Console Application That Runs a Specified Script](fd).</span></span> <span data-ttu-id="122ca-104">Det här exemplet används den [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) klassen för att köra ett skript som hämtar bearbeta information med hjälp av listan över processnamn som skickades till skriptet.</span><span class="sxs-lookup"><span data-stu-id="122ca-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="122ca-105">Den visar hur du skickar in objekt till ett skript och hur du hämtar felobjekt samt utdata-objekt.</span><span class="sxs-lookup"><span data-stu-id="122ca-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="122ca-106">Du kan ladda ned den C# källfilen (runspace03.cs) för det här exemplet med hjälp av Microsoft Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="122ca-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="122ca-107">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="122ca-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="122ca-108">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="122ca-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="122ca-109">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="122ca-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="122ca-110">Se även</span><span class="sxs-lookup"><span data-stu-id="122ca-110">See Also</span></span>

[<span data-ttu-id="122ca-111">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="122ca-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="122ca-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="122ca-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)