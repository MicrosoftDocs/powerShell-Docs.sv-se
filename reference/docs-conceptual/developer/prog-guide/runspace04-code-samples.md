---
title: RunSpace04-kod exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9a9b7e02358cdf9018199046c938c699aff8681c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787077"
---
# <a name="runspace04-code-samples"></a><span data-ttu-id="fbf70-102">RunSpace04 – kodexempel</span><span class="sxs-lookup"><span data-stu-id="fbf70-102">RunSpace04 Code Samples</span></span>

<span data-ttu-id="fbf70-103">Här är ett kod exempel för en körnings utrymme som använder klassen [system. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) för att köra ett skript som genererar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="fbf70-103">Here is a code sample for a runspace that uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="fbf70-104">Värd programmet ansvarar för att fånga upp felet och tolka fel posten.</span><span class="sxs-lookup"><span data-stu-id="fbf70-104">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="fbf70-105">Du kan ladda ned VB.NET-källfilen (Runspace04. VB) för den här körnings utrymme med Windows Software Development Kit för Windows Vista och Microsoft .NET Framework 3,0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="fbf70-105">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="fbf70-106">Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="fbf70-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="fbf70-107">De hämtade källfilerna är tillgängliga i **\<PowerShell Samples>** katalogen.</span><span class="sxs-lookup"><span data-stu-id="fbf70-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="fbf70-108">Fullständig exempel kod finns i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="fbf70-108">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="fbf70-109">Språk</span><span class="sxs-lookup"><span data-stu-id="fbf70-109">Language</span></span>|<span data-ttu-id="fbf70-110">Avsnitt</span><span class="sxs-lookup"><span data-stu-id="fbf70-110">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="fbf70-111">VB.NET</span><span class="sxs-lookup"><span data-stu-id="fbf70-111">VB.NET</span></span>|[<span data-ttu-id="fbf70-112">Runspace01 (VB.NET) – kodexempel</span><span class="sxs-lookup"><span data-stu-id="fbf70-112">Runspace01 (VB.NET) Code Sample</span></span>](./runspace01-vb-net-code-sample.md)|

## <a name="see-also"></a><span data-ttu-id="fbf70-113">Se även</span><span class="sxs-lookup"><span data-stu-id="fbf70-113">See Also</span></span>

[<span data-ttu-id="fbf70-114">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fbf70-114">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="fbf70-115">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fbf70-115">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
