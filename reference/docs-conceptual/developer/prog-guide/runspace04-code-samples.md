---
title: RunSpace04-kod exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb6fcc47-cf89-43e7-b686-3d60934ce3e7
caps.latest.revision: 6
ms.openlocfilehash: 2a3e7598c433027fdd96343829c0606fc7b1c37c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352530"
---
# <a name="runspace04-code-samples"></a><span data-ttu-id="0b02a-102">RunSpace04 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="0b02a-102">RunSpace04 Code Samples</span></span>

<span data-ttu-id="0b02a-103">Här är ett kod exempel för en körnings utrymme som använder klassen [system. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) för att köra ett skript som genererar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="0b02a-103">Here is a code sample for a runspace that uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="0b02a-104">Värd programmet ansvarar för att fånga upp felet och tolka fel posten.</span><span class="sxs-lookup"><span data-stu-id="0b02a-104">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="0b02a-105">Du kan ladda ned VB.NET-källfilen (Runspace04. VB) för den här körnings utrymme med Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="0b02a-105">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0b02a-106">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="0b02a-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="0b02a-107">De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** .</span><span class="sxs-lookup"><span data-stu-id="0b02a-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="0b02a-108">Fullständig exempel kod finns i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="0b02a-108">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="0b02a-109">Språk</span><span class="sxs-lookup"><span data-stu-id="0b02a-109">Language</span></span>|<span data-ttu-id="0b02a-110">Ämne</span><span class="sxs-lookup"><span data-stu-id="0b02a-110">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="0b02a-111">VB.NET</span><span class="sxs-lookup"><span data-stu-id="0b02a-111">VB.NET</span></span>|[<span data-ttu-id="0b02a-112">Kod exempel för Runspace01 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="0b02a-112">Runspace01 (VB.NET) Code Sample</span></span>](./runspace01-vb-net-code-sample.md)|

## <a name="see-also"></a><span data-ttu-id="0b02a-113">Se även</span><span class="sxs-lookup"><span data-stu-id="0b02a-113">See Also</span></span>

[<span data-ttu-id="0b02a-114">Windows PowerShell Programmer ' s guide</span><span class="sxs-lookup"><span data-stu-id="0b02a-114">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0b02a-115">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0b02a-115">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)