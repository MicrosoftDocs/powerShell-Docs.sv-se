---
title: Visar fel information | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e542110e9c35a74c5d4c112b0a831f7f8ad9242e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774583"
---
# <a name="displaying-error-information"></a><span data-ttu-id="c32e0-102">Visa felinformation</span><span class="sxs-lookup"><span data-stu-id="c32e0-102">Displaying Error Information</span></span>

<span data-ttu-id="c32e0-103">I det här avsnittet beskrivs hur användare kan visa fel information.</span><span class="sxs-lookup"><span data-stu-id="c32e0-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="c32e0-104">När cmdleten påträffar ett fel, ser presentationen av fel informationen som standard ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="c32e0-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="c32e0-105">Användare kan dock visa fel efter kategori genom `$ErrorView` att ange variabeln till `"CategoryView"` .</span><span class="sxs-lookup"><span data-stu-id="c32e0-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="c32e0-106">I vyn kategori visas viss information från fel posten i stället för en kostnads fri text Beskrivning av felet.</span><span class="sxs-lookup"><span data-stu-id="c32e0-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="c32e0-107">Den här vyn kan vara användbar om du har en lång lista med fel som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="c32e0-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="c32e0-108">Föregående fel meddelande visas i kategorivyn enligt följande.</span><span class="sxs-lookup"><span data-stu-id="c32e0-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="c32e0-109">Mer information om fel kategorier finns i [fel poster för Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="c32e0-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c32e0-110">Se även</span><span class="sxs-lookup"><span data-stu-id="c32e0-110">See Also</span></span>

[<span data-ttu-id="c32e0-111">Windows PowerShell-felposter</span><span class="sxs-lookup"><span data-stu-id="c32e0-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="c32e0-112">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="c32e0-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
