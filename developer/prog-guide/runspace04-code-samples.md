---
title: RunSpace04 kodexempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb6fcc47-cf89-43e7-b686-3d60934ce3e7
caps.latest.revision: 6
ms.openlocfilehash: 2a3e7598c433027fdd96343829c0606fc7b1c37c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081367"
---
# <a name="runspace04-code-samples"></a><span data-ttu-id="2303b-102">RunSpace04 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="2303b-102">RunSpace04 Code Samples</span></span>

<span data-ttu-id="2303b-103">Här är ett kodexempel på för ett körningsutrymme som använder den [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) klassen för att köra ett skript som genererar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="2303b-103">Here is a code sample for a runspace that uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="2303b-104">Värdprogrammet är ansvarig för att fånga felet och tolka en Felpost.</span><span class="sxs-lookup"><span data-stu-id="2303b-104">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="2303b-105">Du kan hämta källfilen VB.NET (Runspace04.vb) för den här körningsutrymme med hjälp av Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3.0-körtidskomponenter.</span><span class="sxs-lookup"><span data-stu-id="2303b-105">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2303b-106">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2303b-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="2303b-107">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="2303b-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="2303b-108">Fullständig exempelkod finns i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="2303b-108">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="2303b-109">Språk</span><span class="sxs-lookup"><span data-stu-id="2303b-109">Language</span></span>|<span data-ttu-id="2303b-110">Ämne</span><span class="sxs-lookup"><span data-stu-id="2303b-110">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="2303b-111">VB.NET</span><span class="sxs-lookup"><span data-stu-id="2303b-111">VB.NET</span></span>|[<span data-ttu-id="2303b-112">Runspace01 (VB.NET)-kodexempel</span><span class="sxs-lookup"><span data-stu-id="2303b-112">Runspace01 (VB.NET) Code Sample</span></span>](./runspace01-vb-net-code-sample.md)|

## <a name="see-also"></a><span data-ttu-id="2303b-113">Se även</span><span class="sxs-lookup"><span data-stu-id="2303b-113">See Also</span></span>

[<span data-ttu-id="2303b-114">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2303b-114">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2303b-115">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2303b-115">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)