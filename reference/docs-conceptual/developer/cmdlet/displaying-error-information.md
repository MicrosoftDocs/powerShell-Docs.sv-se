---
ms.date: 09/13/2016
ms.topic: reference
title: Visa felinformation
description: Visa felinformation
ms.openlocfilehash: 37a3adb91d0e616a5c7f27bcab866f8da139f969
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653062"
---
# <a name="displaying-error-information"></a><span data-ttu-id="1ca6c-103">Visa felinformation</span><span class="sxs-lookup"><span data-stu-id="1ca6c-103">Displaying Error Information</span></span>

<span data-ttu-id="1ca6c-104">I det här avsnittet beskrivs hur användare kan visa fel information.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-104">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="1ca6c-105">När cmdleten påträffar ett fel, ser presentationen av fel informationen som standard ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="1ca6c-105">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="1ca6c-106">Användare kan dock visa fel efter kategori genom `$ErrorView` att ange variabeln till `"CategoryView"` .</span><span class="sxs-lookup"><span data-stu-id="1ca6c-106">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="1ca6c-107">I vyn kategori visas viss information från fel posten i stället för en kostnads fri text Beskrivning av felet.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-107">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="1ca6c-108">Den här vyn kan vara användbar om du har en lång lista med fel som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-108">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="1ca6c-109">Föregående fel meddelande visas i kategorivyn enligt följande.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-109">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="1ca6c-110">Mer information om fel kategorier finns i [fel poster för Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="1ca6c-110">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ca6c-111">Se även</span><span class="sxs-lookup"><span data-stu-id="1ca6c-111">See Also</span></span>

[<span data-ttu-id="1ca6c-112">Windows PowerShell-felposter</span><span class="sxs-lookup"><span data-stu-id="1ca6c-112">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="1ca6c-113">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="1ca6c-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
