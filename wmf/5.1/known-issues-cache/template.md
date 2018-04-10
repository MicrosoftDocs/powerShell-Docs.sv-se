---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
title: exempelmall av ett känt problem eller begränsning uppskrivning
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="a6a48-103">Obs: ge en föreslagna beskrivande rubrik och en kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="a6a48-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="a6a48-104">Exempel: Felaktiga ExecutionPolicy fel</span><span class="sxs-lookup"><span data-stu-id="a6a48-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="a6a48-105">Användningen av PowerShell-moduler och DSC-resurser kan resultera i fel som rapporteras om körningsprincipen på Windows 7.</span><span class="sxs-lookup"><span data-stu-id="a6a48-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="a6a48-106">Lösning</span><span class="sxs-lookup"><span data-stu-id="a6a48-106">Resolution</span></span>

<span data-ttu-id="a6a48-107">Lös problemet genom att ange den **ExecutionPolicy** till **RemoteSigned** genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):</span><span class="sxs-lookup"><span data-stu-id="a6a48-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```