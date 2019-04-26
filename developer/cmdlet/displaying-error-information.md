---
title: Visa felinformation | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068291"
---
# <a name="displaying-error-information"></a><span data-ttu-id="51e77-102">Visa felinformation</span><span class="sxs-lookup"><span data-stu-id="51e77-102">Displaying Error Information</span></span>

<span data-ttu-id="51e77-103">Det här avsnittet beskrivs hur där användare kan visa information om felet.</span><span class="sxs-lookup"><span data-stu-id="51e77-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="51e77-104">När din cmdlet påträffar ett fel, kommer, presentation av felinformationen som standard likna följande utdata om felet.</span><span class="sxs-lookup"><span data-stu-id="51e77-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="51e77-105">Användare kan dock visa fel efter kategori genom att ange den `$ErrorView` variabeln `"CategoryView"`.</span><span class="sxs-lookup"><span data-stu-id="51e77-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="51e77-106">Kategorivyn visas viss information från en Felpost snarare än en fri text beskrivning av felet.</span><span class="sxs-lookup"><span data-stu-id="51e77-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="51e77-107">Den här vyn kan vara användbart om du har en lång lista med fel att skanna.</span><span class="sxs-lookup"><span data-stu-id="51e77-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="51e77-108">Vyn kategori visas föregående felmeddelande på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="51e77-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="51e77-109">Läs mer om felkategorier [Windows PowerShell-felposter](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="51e77-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="51e77-110">Se även</span><span class="sxs-lookup"><span data-stu-id="51e77-110">See Also</span></span>

[<span data-ttu-id="51e77-111">Windows PowerShell-felposter</span><span class="sxs-lookup"><span data-stu-id="51e77-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="51e77-112">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="51e77-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
