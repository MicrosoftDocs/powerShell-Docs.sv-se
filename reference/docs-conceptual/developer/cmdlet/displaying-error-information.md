---
title: Visar fel information | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359369"
---
# <a name="displaying-error-information"></a><span data-ttu-id="dd581-102">Visa felinformation</span><span class="sxs-lookup"><span data-stu-id="dd581-102">Displaying Error Information</span></span>

<span data-ttu-id="dd581-103">I det här avsnittet beskrivs hur användare kan visa fel information.</span><span class="sxs-lookup"><span data-stu-id="dd581-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="dd581-104">När cmdleten påträffar ett fel, ser presentationen av fel informationen som standard ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="dd581-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="dd581-105">Användare kan dock visa fel efter kategori genom att ange `$ErrorView` variabeln till `"CategoryView"`.</span><span class="sxs-lookup"><span data-stu-id="dd581-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="dd581-106">I vyn kategori visas viss information från fel posten i stället för en kostnads fri text Beskrivning av felet.</span><span class="sxs-lookup"><span data-stu-id="dd581-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="dd581-107">Den här vyn kan vara användbar om du har en lång lista med fel som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="dd581-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="dd581-108">Föregående fel meddelande visas i kategorivyn enligt följande.</span><span class="sxs-lookup"><span data-stu-id="dd581-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="dd581-109">Mer information om fel kategorier finns i [fel poster för Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="dd581-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd581-110">Se även</span><span class="sxs-lookup"><span data-stu-id="dd581-110">See Also</span></span>

[<span data-ttu-id="dd581-111">Windows PowerShell-felposter</span><span class="sxs-lookup"><span data-stu-id="dd581-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="dd581-112">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="dd581-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
