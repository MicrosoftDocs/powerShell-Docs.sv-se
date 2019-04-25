---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.topic: conceptual
title: exempelmall för ett känt problem eller begränsning writeup
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055555"
---
 ><span data-ttu-id="a13ea-103">Obs: Ange en föreslagna beskrivande rubrik och en kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="a13ea-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="a13ea-104">Exempel: Felaktiga ExecutionPolicy-fel</span><span class="sxs-lookup"><span data-stu-id="a13ea-104">Example: Erroneous ExecutionPolicy errors</span></span>
<span data-ttu-id="a13ea-105">Använda PowerShell-moduler och DSC-resurser kan resultera i fel som rapporterats om ExecutionPolicy på Windows 7.</span><span class="sxs-lookup"><span data-stu-id="a13ea-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="a13ea-106">Lösning</span><span class="sxs-lookup"><span data-stu-id="a13ea-106">Resolution</span></span>

<span data-ttu-id="a13ea-107">Att lösa, ange den **ExecutionPolicy** till **RemoteSigned** genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):</span><span class="sxs-lookup"><span data-stu-id="a13ea-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
